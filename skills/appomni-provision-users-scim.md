---
name: appomni-provision-users-scim
description: Provision and manage AppOmni platform users — over SCIM 2.0 from an identity provider, or directly through the AppOmni core user and RBAC routes, including emergency breakglass access.
api: appomni:appomni-scim-api
openapi: openapi/appomni-scim-api-openapi.yml
operations:
  - allUsers
  - user
  - userWithFilter
  - updateUsers
  - listGroups
  - listUsers
  - addUser
  - getUserDetailsAndRoles
  - deactivateOrActivateUser
  - listRBACRoles
  - enableBreakglassAccessForEmergencies
  - disableBreakglassAccessForEmergencies
generated: '2026-09-04'
method: generated
source: openapi/appomni-scim-api-openapi.yml + openapi/appomni-identity-api-openapi.yml
---

# Provision AppOmni users

AppOmni exposes two user surfaces. Pick the right one.

- **SCIM 2.0** at `/scim/v2/` — for an identity provider syncing users and groups into AppOmni.
- **Core user routes** at `/api/v1/core/user/` — for direct administration from a script or agent.

Do not confuse either with `/api/v1/identity/user/`, which describes users detected *inside* the
monitored SaaS applications, not people who log into AppOmni.

## SCIM 2.0

AppOmni implements SCIM 2.0 properly — bodies carry
`"schemas": ["urn:ietf:params:scim:schemas:core:2.0:User"]` and list responses carry
`urn:ietf:params:scim:api:messages:2.0:ListResponse` with `totalResults`, `itemsPerPage` and `startIndex`.

1. `allUsers` — `GET /scim/v2/Users`
2. `userWithFilter` — `GET /scim/v2/Users/?filter=userName sw "<prefix>"` (SCIM filter grammar)
3. `user` — `GET /scim/v2/Users/{user_id}`
4. `updateUsers` — `PUT /scim/v2/Users/{user_id}`. This is a **replace**, not a merge: send the full
   resource — `userName`, `name.givenName`, `name.familyName`, `externalId`, `locale`, `active`,
   `emails[]` — or you will blank the fields you leave out.
5. `listGroups` — `GET /scim/v2/Groups`. Members come back as `{value, $ref, display}`.

Setting `"active": false` deactivates rather than deletes. That is the reversible path; use it.

## Core routes

- `listUsers` / `addUser` — `GET`/`POST /api/v1/core/user/`
- `getUserDetailsAndRoles` — `GET /api/v1/core/user/{id}/`
- `deactivateOrActivateUser` — `PATCH /api/v1/core/user/{id}/`. One operation toggles both directions,
  so deactivation is directly reversible.
- `listRBACRoles` — `GET /api/v1/core/group/`
- `listUsersForRolesWithLimitedPermissions` — `GET /api/v1/core/limited-user/` is the projection to use
  when the caller's own role cannot see full user records.

## Breakglass

`enableBreakglassAccessForEmergencies` — `PUT /api/v1/core/user/{user_id}/enable_breakglass` grants
emergency access, and `disableBreakglassAccessForEmergencies` revokes it. This pair is reversible but it
is a genuine privilege escalation: require human authorisation to enable, and always pair an enable with
a scheduled disable. AppOmni publishes no automatic expiry.

## Conventions

Bearer token auth. Core routes use `?limit=`/`?offset=`; SCIM uses `startIndex`/`itemsPerPage`. Errors
are `{"detail": "..."}`. No idempotency keys — a retried `POST /api/v1/core/user/` may create a second user.
