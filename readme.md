# Developer Environment 1

Setup files for the development environment using all the services

1. Go to the `/local` folder

2. Run following command
```docker compose --env-file ../.env up -d```

### docker-compose-default [optional]

This is the alternative docker-compose setup for running services without explicit IP addresses.
There is also two separate instances of postgres for running the main DB and the one for Keycloak.
Using this does not require you to manually interact with the database. 

1. Fill .env with the content of `.env.local.default.example`
2. Run following command:

``` bash
docker-compose -f local/docker-compose-default.yml --env-file .env up
```

After that you can run services in VSCode's devcontainers using config

```json
	"runArgs": [
		"--network=eil"
	]
```

and connect to the services by their container name, e.g. `postgres_db:5432`, `postgres_kc:5432`, `database-api:80` etc.