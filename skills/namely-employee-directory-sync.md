---
name: namely-employee-directory-sync
description: >-
  Read the full employee directory out of a Namely HRIS tenant, resolving job titles, groups and
  teams through Namely's JSON API sideload, while respecting the one rate limit Namely publishes
  and the pagination it requires.
api: Namely API
version: v1
generated: '2026-08-26'
method: generated
source: >-
  openapi/namely-api-openapi.json (operationIds verified against the published contract) plus
  developers.namely.com introduction and linked-objects articles.
operations:
  - GET_companies-info
  - GET_profiles
  - GET_profiles-id
  - GET_job_titles
  - GET_groups
  - GET_teams
consequence: read-only
---

# Sync the Namely employee directory

Read-only. Nothing in this skill writes.

## Before you start

- **Base URL is tenant-specific.** `https://{company}.namely.com/api/v1`. There is no shared
  Namely API host — substitute the customer's own subdomain. The published contract declares no
  `host`, so a generated client will not have one.
- **Auth.** Send `Authorization: Bearer <token>` on every request, where the token is either an
  OAuth 2.0 access token (15-minute lifetime) or a Personal Access Token (2-year lifetime). The
  contract defines the scheme but applies it to no operation, so do not rely on a generated client
  to attach it.
- **This data is sensitive.** `Profile` carries `ssn`, `dob`, `ethnicity`, `gender` and
  `marital_status` alongside compensation. A PAT inherits the permissions of the person who
  created it, so an administrator's token reads every employee's SSN. Only request the fields the
  task needs, and never log a whole profile object.

## Steps

1. **Confirm connectivity.** `GET_companies-info` (`GET /companies/info`). It returns tenant
   metadata and is the lightest call in the API. A 401 here means the token is wrong before you
   have touched any employee data.

2. **Page the directory.** `GET_profiles` (`GET /profiles`).
   - Pagination is **mandatory**. Since 2017-09-20 Namely no longer allows retrieving all profiles
     in one call, and unpaginated requests time out.
   - Read `meta.count` for the number of records on this page and `meta.total_count` for the full
     total. These mean different things — do not use `count` as the total.
   - **Stay under 100 requests per minute.** This is the only rate limit Namely publishes and it
     applies to exactly this endpoint.
   - **Exhaustion returns HTTP 406, not 429**, and carries no `Retry-After`. Treat a 406 from this
     endpoint as throttling, sleep, and resume. A generic HTTP client will read 406 as a content
     negotiation failure and give up.

3. **Resolve relationships from the sideload, not from extra calls.** Each profile carries
   `links` with ids for `profiles.job_title`, `profiles.image`, `profiles.groups` and
   `profiles.teams`. The top-level `links` hash tells you the *type* of each relationship, and the
   top-level `linked` hash carries the resolved objects. Join by id in memory. Refetching each
   related object individually is what will push you into the rate limit.

4. **Fetch reference data once.** `GET_job_titles` (`GET /job_titles`), `GET_groups`
   (`GET /groups`) and `GET_teams` (`GET /teams`) are small and stable. Cache them for the run
   rather than resolving per employee.

5. **Build the org chart from `reports_to`.** Profile carries a self-referential `reports_to`
   manager reference. That field, not the group or team edges, is the reporting hierarchy.

6. **Fetch individuals only when needed.** `GET_profiles-id` (`GET /profiles/{id}`) for a single
   record; `GET_profiles-me` for the token owner's own profile.

## Things that will surprise you

- **Custom fields appear as extra top-level keys** on every profile, so the runtime shape is a
  superset of the published schema. Do not use strict schema validation on a profile response.
- **Field keys are frozen.** Renaming a field in the Namely UI does not rename its API key —
  `favorite_film` stays `favorite_film` after the label becomes "Favorite Song". This is
  deliberate, and it means the API key is the stable identifier, not the label.
- **`user_status` has more than two values.** Since 2018-05-22 it returns every status the UI
  shows, including `pending`. Code written against the older active/inactive assumption will
  mis-handle it.
- **Groups and Teams overlap.** `Group` carries an `is_team` boolean and there is also a separate
  `/teams` surface, so the same real-world team can be reached two ways.
- **A 403 may not be your fault.** If the Namely user who minted the PAT is deactivated or
  deleted, every call with that token returns 403. Escalate to a human — this is an HR event, not
  a code change.
