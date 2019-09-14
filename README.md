# pg_local

A script for managing multiple local instances of a PostgreSQL server.

For local development, it can be helpful to keep the artifacts associated with
a particular project isolated to a particular directory. Additionally, with
version managers like [asdf-vm](https://asdf-vm.com/#/), it’s possible to have
multiple version of PostgreSQL available on a single machine.

Combined with [direnv][], `pg_local` automates the process of running a
PostgreSQL for each project or client.

## Requirements

- macOS
- [direnv][] — triggers the environment to be loaded
- Ruby — used to dynamically determine free port numbers
- [dot-bash][] - for ANSI color escape codes

## Usage

  1. Place the `pg_local` script somewhere in your `$PATH`.

  2. In each directory where you want an instance of PostgreSQL, run `pg_local
     setup`. This will add a line to your `.envrc` (and allow it to be loaded).

Now, each time you enter this directory, the script will set `PGDATA` and
`PGPORT` to the match the local instance. Update your application
configuration to use these settings when it connects to the database. Commands
like `psql` will read these values automatically, so no additional
configuration is needed there.

## Commands

  - `pg_local init` — initializes a local copy of PostgreSQL
  - `pg_local setup` — hooks `pg_local into the `.envrc` in the current
    directory
  - `pg_local start` — starts the local PostgreSQL server with a dynamic port
    number
  - `pg_local stop` — stops the local PostgreSQL server
  - `pg_local restart` — restarts the local PostgreSQL server
  - `pg_local status` — outputs whether the local server is running or not
  - `pg_local env` — exports the `PGDATA` and `PGPORT` environment variables

## Contributing

  1. Fork it.
  2. Create your feature branch (`git checkout -b my-new-feature`).
  3. Commit your changes (`git commit -am 'Added some feature'`).
  4. Push to the branch (`git push origin my-new-feature`).
  5. Create a new Pull Request.

## Copyright

Copyright © 2019 Tyler Hunt. See LICENSE for details.

[direnv]: https://direnv.net
[dot-bash]: https://github.com/tylerhunt/dot-bash
