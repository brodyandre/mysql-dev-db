# MySQL para Desenvolvimento com Docker

Este repositório disponibiliza um comando único para subir um MySQL local em container para desenvolvimento pontual.

## Comando oficial

```bash
docker run --name docker_mysql_dev --rm -d -p 3306:3306 -e MYSQL_DATABASE=docker_db -e MYSQL_USER=docker_usr -e MYSQL_PASSWORD=docker_pwd -e MYSQL_ROOT_PASSWORD=docker_root_pwd mysql:8.4
```

## Configuração criada

- Banco de dados: `docker_db`
- Usuário de aplicação: `docker_usr`
- Senha de aplicação: `docker_pwd`
- Porta local: `3306`

## Parar o container

```bash
docker stop docker_mysql_dev
```
