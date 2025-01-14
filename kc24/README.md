# Keycloak v24

## Configuração

1. **Clone o repositório:**

   ```bash
   git clone https://github.com/varantes/keycloak-docker.git
   cd keycloak-docker
   ```

2. **Configure as variáveis de ambiente:**

   Crie um arquivo `.env` na raiz do projeto com o seguinte conteúdo:

   ```env
   KEYCLOAK_ADMIN=admin
   KEYCLOAK_ADMIN_PASSWORD=admin
   ```

   *Nota:* Altere as credenciais conforme necessário.

3. **Configure o arquivo `docker-compose.yml`:**

   Certifique-se de que o arquivo `docker-compose.yml` esteja configurado corretamente para suas necessidades.

   ```yaml
   version: '3.8'

   services:
     keycloak:
       image: quay.io/keycloak/keycloak:latest
       environment:
         KEYCLOAK_ADMIN: ${KEYCLOAK_ADMIN}
         KEYCLOAK_ADMIN_PASSWORD: ${KEYCLOAK_ADMIN_PASSWORD}
       ports:
         - "8080:8080"
       command:
         - start-dev
   ```

   *Nota:* Este é um exemplo básico. Para configurações mais avançadas, consulte a [documentação oficial do Keycloak](https://www.keycloak.org/documentation).

## Uso

1. **Inicie os serviços:**

   ```bash
   docker-compose up -d
   ```

O KC 24 pode ser colocado no ar tanto utilizando o docker-compose.yml quanto utilizando o comando:

```
docker run --rm --name kc24 -p 8080:8080 -e KEYCLOAK_ADMIN=admin -e KEYCLOAK_ADMIN_PASSWORD=admin quay.io/keycloak/keycloak:24.0 start-dev
```

O H2 é utilizado como banco de dados nos dois cases acima.

2. **Acesse o Keycloak:**

   Após a inicialização, o Keycloak estará acessível em `http://localhost:8080`. Utilize as credenciais definidas no arquivo `.env` para fazer login.

## Personalização

Para personalizar o Keycloak, você pode adicionar temas, configurações de realm e outros recursos no diretório `kc24/`.

## Referências

- [Documentação Oficial do Keycloak](https://www.keycloak.org/documentation)
- [Keycloak Docker Image](https://hub.docker.com/r/jboss/keycloak/)
- [Docker Compose](https://docs.docker.com/compose/)
- docker-compose.yml original foi obtido [neste repo git](https://github.com/viniciusfinger/keycloak-docker-compose/blob/main/docker-compose.yaml).

*Nota:* Este repositório é destinado para fins de teste e desenvolvimento. Para ambientes de produção, consulte as melhores práticas na documentação oficial do Keycloak. 
