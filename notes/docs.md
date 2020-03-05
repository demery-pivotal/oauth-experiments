# UAA Documentation

- [UAA Repository](https://github.com/cloudfoundry/uaa)
- [UAA Docs](https://github.com/cloudfoundry/uaa/tree/develop/docs)
  (in the UAA repository).
- [UAA API](http://docs.cloudfoundry.org/api/uaa/version/74.14.0/index.html)
- [UAA "Spec"](https://github.com/cloudfoundry/uaa-release/blob/develop/jobs/uaa/spec)
- [UAA CLI Repository](https://github.com/cloudfoundry/cf-uaac)
- [System for Cross-domain Identity Management (SCIM)](http://www.simplecloud.info/)

## User Groups and Client Scopes

**Groups**

- UAA represents permissions as _groups._
- Each group has an identifier and a description.
- Each user is in a set of groups
  that define the user's permissions.
- To give a user a new permission,
  add the user to the group that represents the permission.

**Client Scopes**

- Each client has a list of _scopes._
- A scope is a permission that
  the client knows how to use on a user's behalf.

**Relevant Permissions**

When a client requests permissions via the Authorization Code flow
(and perhaps via other flows):

- It shows a web page
  that includes a list of relevant permissions for the user to select from.
- The relevant permissions are those in the _intersection_ of:
  - The user's groups (i.e. the permissions that the user has).
  - The client's scopes (i.e. the permissions that the client knows how to use).

Note that "relevant permission" is my term.
I don't know whether UAA has a term for this.
