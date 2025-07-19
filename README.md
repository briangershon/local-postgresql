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
- `CREATE DATABASE abc;` and `DROP DATABASE abc;` - create and drop a database
- `\c database-name-here` - connect to a database
- `\dt` - list tables
- `\d table-name` to describe a table
- `exit` - exit `psql`

## Example connection string

`postgres://postgres:postgres@localhost:5432/mydatabase`

## Export and Import a PostgreSQL table

Here's how to export and import data from tables via CSV files using `psql`:

`psql DATABASE_URL`

To export:

```
postgres=> \copy my_table TO 'my_table.csv' WITH CSV HEADER;
```

To import:

```
postgres=> \copy my_table FROM 'my_table.csv' WITH CSV HEADER;
```

## Backup and Restore a PostgreSQL table

```bash
pg_dump --data-only --table=company sourcedb > company.pg
```

```bash
psql sourcedb < company.pg
```
