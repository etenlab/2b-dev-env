# Developer Environment 1

[Docs](https://docs.dev.lab.eten.bible/docs/Support/dev-env)

Setup files for the development environment using all the services

1. Go to the `/local` folder

2. Run following command
```docker-compose --env-file ../.env up -d```

## How to dump database to ./local/postgres/dump-eil-eildb1.sql (need root rights do see files at ./local/postgres)
example (`local-postgres-1` here is name of the container)
``` bash
docker exec -i local-postgres-1 /bin/bash -c "pg_dump --verbose --host=dev-aurora-cluster.cluster-ro-cpxhfog2q80o.us-east-2.rds.amazonaws.com --port=5432 --username=postgres --format=plain --file /var/lib/postgresql/data/dump-eil-eildb1.sql eildb1"
```

## How to dump local SSO database (after making Keycloak Admin changes) to ./local/sql/keycloak_db.sql
example (`local-postgres-sso-1` here is name of the container)
``` bash
docker exec -i local-postgres-sso-1 /bin/bash -c "PGPASSWORD=example pg_dump --verbose --username=postgres --format=plain --file /docker-entrypoint-initdb.d/keycloak_db.sql keycloak_db"
```
