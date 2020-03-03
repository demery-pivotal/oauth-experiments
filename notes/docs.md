# Pulse and UAA Docs


- [UAA Repository](https://github.com/cloudfoundry/uaa)
- [UAA Repository Docs](https://github.com/cloudfoundry/uaa/tree/develop/docs)
- [UAA "Spec"](https://github.com/cloudfoundry/uaa-release/blob/develop/jobs/uaa/spec)
- [UAA CLI Repository](https://github.com/cloudfoundry/cf-uaac)
- [UAA API](http://docs.cloudfoundry.org/api/uaa/version/74.14.0/index.html)
- [System for Cross-domain Identity Management (SCIM)](http://www.simplecloud.info/)

## UAA Terminology

- Access token parameters:
  - scope
    - permission or role for a client
    - when the client is acting on behalf of a user
  - authorities:
    - permission or role for a client
    - when the client acting on its own behalf

- Scopes
  - Scope names are meaningful only to the resource server.
  - The "base name" of a scope is everything before the last dot.


- Groups
  - A user belongs to one or more groups.
  - A group represents a scope.

### UAA Access Token Fields (JWT)

- scope: Array of permissions
- aud: Array of audiences?
  - UAA adds the base name of every scope to the aud field?

