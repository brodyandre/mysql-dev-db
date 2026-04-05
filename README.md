# MySQL para Desenvolvimento com Docker

Este repositorio padroniza o setup de MySQL local para desenvolvimento usando Docker Compose, com configuracao via arquivo de ambiente e sem expor senha no comando.

## Objetivo

Subir um banco MySQL local para desenvolvimento pontual com os seguintes requisitos:

- Banco de dados: `docker_db`
- Usuario de aplicacao: `docker_usr`
- Senha de aplicacao: `docker_pwd`

## Pre-requisitos

- Docker Desktop (ou Docker Engine + Compose) instalado
- Porta `3306` disponivel na maquina local

## Subir o banco (fluxo recomendado)

1. Copie o arquivo de exemplo:

```bash
cp .env.example .env.mysql.dev
```

2. Suba o servico:

```bash
docker compose --env-file .env.mysql.dev up -d mysql
```

3. Verifique status:

```bash
docker compose --env-file .env.mysql.dev ps
```

## String de conexao para aplicacoes

```txt
mysql://docker_usr:docker_pwd@localhost:3306/docker_db
```

## Parar e remover o ambiente

```bash
docker compose --env-file .env.mysql.dev down
```

## Comando unico (alternativa sem compose)

Se o time preferir manter um comando unico:

```bash
docker run --name docker_mysql_dev --rm -d -p 127.0.0.1:3306:3306 --env-file .env.mysql.dev mysql:8.4
```

## Padrao profissional aplicado neste repositorio

- Segredos fora da linha de comando (`--env-file`)
- Porta publicada apenas em `localhost` (`127.0.0.1`)
- Healthcheck configurado no Compose
- Arquivo de ambiente local ignorado no Git

## Escopo

Este setup e focado em desenvolvimento local. Para producao, recomenda-se adicionar persistencia duravel, backup/restore validado, monitoramento, TLS e gerenciador de segredos.
