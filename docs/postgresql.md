# PostgreSQL

→ [postgresql.org](https://www.postgresql.org/)

## Getting Started

### Local installation

#### Docker

[GitHub](https://github.com/docker-library/postgres)

```bash
# Alpine
docker run --name postgres -p 5432:5432 -e POSTGRES_PASSWORD=mysecretpassword -d postgres:alpine
# Official
docker run --name postgres966 -p 5432:5432 -e POSTGRES_PASSWORD=mysecretpassword -d postgres:9.6.6
```

## Tools

### pgAdmin

#### pgAdmin 3

- With Docker (see [hub.docker.com](https://hub.docker.com/r/dpage/pgadmin4/))

```bash
docker pull dpage/pgadmin4
docker run -p 80:80 -e "PGADMIN_DEFAULT_EMAIL=user@domain.com" -e "PGADMIN_DEFAULT_PASSWORD=SuperSecret" --name pgadmin4 -d dpage/pgadmin4
# open http://localhost and login
```

## Recipes

### Backup / restore

- Backup can be done with pgAdmin (personally I prefer plain format to have human readble sql content)
- Restore can be done with Docker: `cat D:\Temp\dump.sql | docker exec -i postgres966 psql -U postgres` (you may have to add the missing roles entries, which are not exported such as `CREATE ROLE mycompany SUPERUSER;`)

## Queries

### SQL

#### Update a user password

```sql
ALTER USER user WITH PASSWORD 'newpassword';
```

#### Get all databases

```sql
SELECT * FROM pg_catalog.pg_database;
```

#### Get all tables

```sql
SELECT
    table_schema || '.' || table_name
FROM
    information_schema.tables
WHERE
    table_type = 'BASE TABLE'
AND
    table_schema NOT IN ('pg_catalog', 'information_schema');

SELECT * FROM pg_catalog.pg_tables WHERE schemaname = 'gracethd';
```

#### Get all columns of a table

```sql
SELECT *
FROM information_schema.columns
WHERE table_schema = 'gracethd'
  AND table_name   = 'adresse';
```
