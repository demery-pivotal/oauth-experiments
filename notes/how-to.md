# UAA How To

## Configuration

Create a config dir for your `uaa.yml` file.

Add your config dir to your environment:

    export UUA_CONFIG_PATH=<path-to-your-config-dir>

In your config dir, create a `uaa.yml` file.

In your `uaa.yml` file, configure the users:

```
scim:
  users:
    - pulse|pulse|scim.write,scim.read,openid
```

## Running UAA

Launch UAA:

    # In the UAA repository directory
    ./gradlew run

Connect the CLI to UAA:

    uaac target http://localhost:8080/uaa

This stores information about the target
in the `~/.uaac.yml` file.

Log in as admin:

    uaac token client get ADMIN-CLIENT-ID -s ADMIN-CLIENT-SECRET

This stores the token and other information
in the `~/.uaac.yml` file
in a context named after the client.
It also sets this context as the current context.

## Client (e.g. Pulse)

Add

View


## Group

A group represents a permission.

Create a group:

    uaac group add GROUPNAME

View a group:

    uaac group get GROUPNAME

## User

Create a user:

    uaac user add USERNAME -p PASSWORD --emails EMAIL

Add the user to a group (to give the user a permission):

    uaac member add GROUPNAME MEMBERNAMES...

View a user:

    uaac user get USERNAME

Get an access token (via the Password flow):

    uaac token owner get CLIENTNAME USERNAME

This stores the token and other information
in the `~/.uaac.yml` file
in a context named after the user.
It also sets this context as the current context.

## Tokens

Decode a token:

    uaac token decode TOKEN
