# UAA How To

## Installation

- Get source code for UAA

      # In the oauth-experiments root dir
      git submodule update --init

- Install the UAA CLI (optional, but very useful for experimenting)

      sudo gem install cf-uaac

## Configuration

- Create a config dir for your `uaa.yml` file.

- Add your config dir to your environment:

      export UUA_CONFIG_PATH=<path-to-your-config-dir>

  For example:

      export UAA_CONFIG_PATH=$(pwd)/cf-config

- In your config dir, create a `uaa.yml` file.

- In your `uaa.yml` file, configure the groups, users, and clients.

## Running the UAA Server

- Set `JAVA_HOME` (UAA requires Java 11)

      # On MacOS
      export JAVA_HOME=$(/usr/libexec/java_home -v 11)

- Build the UAA server

      # In the uaa dir
      ./gradlew assemble
      # or
      ./gradlew clean assemble

- Launch the UAA server

      # In the uaa dir
      ./gradlew run

  This launches UAA at `http://localhost:8080/uaa`
  as a Gradle task.
  To stop the server,
  stop the Gradle task
  using `CTRL-C`.

  It is possible to configure a different port,
  but I have not tried that.

## Admin (the UAA CLI)

- Connect the UAA CLI to UAA:

      uaac target http://localhost:8080/uaa

  This stores information about the target
  in your `~/.uaac.yml` file.

- Log into the CLI as admin

      uaac token client get admin -s adminsecret

  This does several things:

  - Adds an `admin` context
    to your `~/.uaac.yml` file
    (if that context doesn't already exist).
  - Stores the token and other information
    in the `admin` context.
  - Sets `admin` as the current context
    (the one currently in use by the CLI).

  Note that this command is an example of the Client Credentials flow.

## Client (e.g. Pulse)

- Add a client (TBD)

- View a client

      uaac client get CLIENTNAME

- View all clients

      uaac clients

## Group

A group represents a permission.

- Create a group

      uaac group add GROUPNAME

- View a group

      uaac group get GROUPNAME

- View all groups

      uaac groups

## User

- Create a user

      uaac user add USERNAME -p PASSWORD --emails EMAIL

- Add a user to a group

      uaac member add GROUPNAME MEMBERNAMES...

  This gives the user the permission represented by that group.

- View a user

      uaac user get USERNAME

- View all users

      uaac users

- Get an access token

      uaac token owner get CLIENTNAME USERNAME -s CLIENTSECRET -p PASSWORD

  Or you can omit anything after `get`, and the UAA CLI will prompt you for
  whatever is missing:

      uaac token owner get CLIENTNAME USERNAME

  This commend (in either form) does several things:
  - Adds a "user" context
    to your `~/.uaac.yml` file,
    with the same name as the user
    (if that context doesn't already exist).
  - Stores the token and other information
    in the user context.
  - Sets the user context as the current context
    (the one currently in use by the CLI).

  Note that this command is an example of the Password flow.

## Tokens

Decode a token

    uaac token decode TOKEN

## Contexts

A context is a set of tokens and other information
currently active in the UAA CLI.

- Switch to a different context

      uaac context CONTEXT

- View the current context

      uaac context

- View all contexts

      uaac contexts
