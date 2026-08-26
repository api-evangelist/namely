---
name: namely-profile-schema-management
description: >-
  Inspect and extend the profile SCHEMA in a Namely tenant — the custom fields and sections that
  define what an employee record contains. Contains an irreversible write; read the consequences
  section before acting.
api: Namely API
version: v1
generated: '2026-08-26'
method: generated
source: >-
  openapi/namely-api-openapi.json (operationIds verified against the published contract) plus
  developers.namely.com profile-fields and introduction articles.
operations:
  - GET_profiles-fields
  - GET_profiles-fields-id
  - GET_profiles-fields-sections
  - GET_profiles-fields-sections-id
  - POST_profiles-fields
  - PUT_profiles-fields-id
  - PUT_profiles-fields-sections-id
consequence: high
---

# Manage the Namely profile schema

Namely separates profile **content** (an employee's data) from profile **schema** (which fields
exist at all). This skill is about the schema. Everything here changes what every employee record
in the tenant looks like.

## Stop and read this first

`POST /profiles/fields` is **irreversible through the API**. Namely publishes no delete operation
for a profile field. Once you create one:

- it materialises as a key on **every** employee profile in the tenant;
- there is **no** `DELETE /profiles/fields/{id}` and **no** restore, archive or undo;
- there is **no** dry-run or validate-only mode, so you cannot rehearse it;
- `PUT /profiles/fields/{id}` only changes the **label**, not the key — so you cannot rename your
  way out of a mistake either. The API key is frozen at creation, deliberately, to protect live
  integrations.

Get explicit human confirmation before calling `POST_profiles-fields`. Undoing it requires a
Namely administrator working in the UI, or Namely support.

## Read the current schema

1. `GET_profiles-fields-sections` (`GET /profiles/fields/sections`) — the sections a profile is
   divided into, each with its `block_titles`.
2. `GET_profiles-fields` (`GET /profiles/fields`) — every API-transferable field. Each carries
   `name`, `label`, `type`, `default`, `deletable` and `valid_format_info`, and links to its
   section.
3. `GET_profiles-fields-id` / `GET_profiles-fields-sections-id` for a single field or section.

Check `deletable` before you assume anything about a field's permanence, and check whether a field
with the semantics you need **already exists** — this is the step that prevents the irreversible
write.

## Change labels (safe, reversible by repeating)

- `PUT_profiles-fields-id` (`PUT /profiles/fields/{id}`) changes a field's label.
- `PUT_profiles-fields-sections-id` (`PUT /profiles/fields/sections/{id}`) changes a section's
  label.

Both are idempotent by HTTP semantics and can be re-applied with the previous value to revert.
Neither changes the underlying API key, so no integration breaks.

## Create a field (irreversible)

`POST_profiles-fields` (`POST /profiles/fields`) with a `Create Profile Field` body.

- There is **no** `Idempotency-Key` header on this operation, or on any Namely operation. A
  retried request creates a **second** field. If the call times out, do **not** blindly retry —
  re-read `GET /profiles/fields` and check whether it landed.
- Namely's docs describe a `POST /profiles/fields/section` for creating a section; it does not
  appear in the published Swagger contract, so treat section creation as undocumented at the
  contract level and verify before relying on it.

## Downstream effect on SCIM

Custom fields created here surface to identity providers through Namely's SCIM 2.0 endpoint at
`https://{company}.namely.com/api/scim/v2/Users.json`, under the extension namespace
`urn:ietf:params:scim:schemas:extension:custom:2.0:User`. If the customer syncs to Okta, the
variable name is case-sensitive and must match the field name exactly as it appears in that SCIM
document — not as it appears in the Namely UI.

## Errors

The published contract declares **no** 4xx or 5xx responses on any operation, so there is nothing
to pattern-match against. The failure modes Namely documents anywhere are:

- **403** — the profile that created your Personal Access Token was deactivated or deleted.
- **406** — rate limit, but only on `GET /profiles`, not on these endpoints.

Anything else is undocumented. Surface the raw status and body to a human rather than guessing.
