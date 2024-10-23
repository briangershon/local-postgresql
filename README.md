# local-postgresql

Run PostgreSQL locally via Docker Desktop on MacOS.

## Setup

Start up Docker Desktop.

Run Postgresql container. Optionally use `--detach` to run in the background.

```shell
docker compose -f docker-compose.yml up --detach
```

Check connectivity with `psql`, which you can download on MacOS via `brew install libpq`. Or use your favorite PostgreSQL client. Default password is `postgres`.

```shell
psql --host localhost --port 5432 --username postgres
```

or to a specific database via:

```shell
psql --host localhost --port 5432 --username postgres --dbname postgres
```

Some common `psql` commands:

- `\l` - list databases
- `\c database-name-here` - connect to a database
- `\dt` - list tables
- `exit` - exit `psql`
