O KC 24 pode ser colocado no ar tanto utilizando o docker-compose.yml quanto utilizando o comando:

```
docker run --rm --name kc24 -p 8080:8080 -e KEYCLOAK_ADMIN=admin -e KEYCLOAK_ADMIN_PASSWORD=admin quay.io/keycloak/keycloak:24.0 start-dev
```

O H2 é utilizado como banco de dados nos dois cases acima.

O docker-compose foi obtido em https://github.com/viniciusfinger/keycloak-docker-compose/blob/main/docker-compose.yaml.
