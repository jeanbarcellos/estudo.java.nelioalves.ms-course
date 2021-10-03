# Criando e testando containers Docker

## Criar rede docker para sistema hr

```
docker network create hr-net
```

## Testando perfil dev com Postgresql no Docker

```
docker pull postgres:12-alpine

docker run -p 5432:5432 --name hr-worker-pg12 --network hr-net -e POSTGRES_PASSWORD=1234567 -e POSTGRES_DB=db_hr_worker postgres:12-alpine

docker run -p 5433:5432 --name hr-user-pg12 --network hr-net -e POSTGRES_PASSWORD=1234567 -e POSTGRES_DB=db_hr_user postgres:12-alpine
```

## hr-config-server

Acessar o terminal (em modo administrador) na raiz do projeto `hr-config-server`

Gerar a `build` Java, usando o comando:

```
mvnw clean package
```

Criar o arquivo `Dockerfile` com o seguinte conteúdo:

```
FROM openjdk:11
VOLUME /tmp
EXPOSE 8888
ADD ./target/hr-config-server-0.0.1-SNAPSHOT.jar hr-config-server.jar
ENTRYPOINT ["java","-jar","/hr-config-server.jar"]
```

Gerar `imagem` `Docker`, usando o comando:

```
docker build -t hr-config-server:v1 .
```

Levantar um `container` com a `imagem` recém criada, usando o comando:

```
docker run -p 8888:8888 --name hr-config-server --network hr-net -e GITHUB_USER=jeanbarcellos@hotmail.com -e GITHUB_PASS= hr-config-server:v1
```

## hr-eureka-server

Acessar o terminal (em modo administrador) na raiz do projeto `hr-eureka-server`

Gerar a `build` Java, usando o comando:

```
mvnw clean package
```

Criar o arquivo `Dockerfile` com o seguinte conteúdo:

```
FROM openjdk:11
VOLUME /tmp
EXPOSE 8761
ADD ./target/hr-eureka-server-0.0.1-SNAPSHOT.jar hr-eureka-server.jar
ENTRYPOINT ["java","-jar","/hr-eureka-server.jar"]
```

Gerar `imagem` `Docker`, usando o comando:

```
docker build -t hr-eureka-server:v1 .
```

Levantar um `container` com a `imagem` recém criada, usando o comando:

```
docker run -p 8761:8761 --name hr-eureka-server --network hr-net hr-eureka-server:v1
```

## hr-worker

Acessar o terminal (em modo administrador) na raiz do projeto `hr-worker`

Gerar a `build` Java, usando o comando:

```
mvnw clean package -DskipTests
```

- Obs: o argumento `-DskipTests` é para evitar que se faça testes acessando o banco de dados

Criar o arquivo `Dockerfile` com o seguinte conteúdo:

```
FROM openjdk:11
VOLUME /tmp
ADD ./target/hr-worker-0.0.1-SNAPSHOT.jar hr-worker.jar
ENTRYPOINT ["java","-jar","/hr-worker.jar"]
```

Gerar `imagem` `Docker`, usando o comando:

```
docker build -t hr-worker:v1 .
```

Levantar um `container` com a `imagem` recém criada, usando o comando:

```
docker run -P --network hr-net hr-worker:v1
```

- Obs: o argumento `-P` faz o container levantar com uma porta aleatória
- Não é necessário definir o nome e nem a porta do container porque o microservice será autoescalável.

## hr-user

Acessar o terminal (em modo administrador) na raiz do projeto `hr-user`

Gerar a `build` Java, usando o comando:

```
mvnw clean package -DskipTests
```

Criar o arquivo `Dockerfile` com o seguinte conteúdo:

```
FROM openjdk:11
VOLUME /tmp
ADD ./target/hr-user-0.0.1-SNAPSHOT.jar hr-user.jar
ENTRYPOINT ["java","-jar","/hr-user.jar"]
```

Gerar `imagem` `Docker`, usando o comando:

```
docker build -t hr-user:v1 .
```

Levantar um `container` com a `imagem` recém criada, usando o comando:

```
docker run -P --network hr-net hr-user:v1
```

## hr-payroll

Acessar o terminal (em modo administrador) na raiz do projeto `hr-payroll`

Gerar a `build` Java, usando o comando:

```
mvnw clean package -DskipTests
```

Criar o arquivo `Dockerfile` com o seguinte conteúdo:

```
FROM openjdk:11
VOLUME /tmp
ADD ./target/hr-payroll-0.0.1-SNAPSHOT.jar hr-payroll.jar
ENTRYPOINT ["java","-jar","/hr-payroll.jar"]
```

Gerar `imagem` `Docker`, usando o comando:

```
docker build -t hr-payroll:v1 .
```

Levantar um `container` com a `imagem` recém criada, usando o comando:

```
docker run -P --network hr-net hr-payroll:v1

```

## hr-oauth

Acessar o terminal (em modo administrador) na raiz do projeto `hr-oauth`

Gerar a `build` Java, usando o comando:

```
mvnw clean package -DskipTests
```

Criar o arquivo `Dockerfile` com o seguinte conteúdo:

```
FROM openjdk:11
VOLUME /tmp
ADD ./target/hr-oauth-0.0.1-SNAPSHOT.jar hr-oauth.jar
ENTRYPOINT ["java","-jar","/hr-oauth.jar"]
```

Gerar `imagem` `Docker`, usando o comando:

```
docker build -t hr-oauth:v1 .
```

Levantar um `container` com a `imagem` recém criada, usando o comando:

```
docker run -P --network hr-net hr-oauth:v1
```

## hr-api-gateway-zuul

Acessar o terminal (em modo administrador) na raiz do projeto `hr-api-gateway-zuul`

Gerar a `build` Java, usando o comando:

```
mvnw clean package -DskipTests
```

Criar o arquivo `Dockerfile` com o seguinte conteúdo:

```
FROM openjdk:11
VOLUME /tmp
EXPOSE 8765
ADD ./target/hr-api-gateway-zuul-0.0.1-SNAPSHOT.jar hr-api-gateway-zuul.jar
ENTRYPOINT ["java","-jar","/hr-api-gateway-zuul.jar"]
```

Gerar `imagem` `Docker`, usando o comando:

```
docker build -t hr-api-gateway-zuul:v1 .
```

Levantar um `container` com a `imagem` recém criada, usando o comando:

```
docker run -p 8765:8765 --name hr-api-gateway-zuul --network hr-net hr-api-gateway-zuul:v1
```

## Alguns comandos Docker

Criar uma rede Docker

```
docker network create <nome-da-rede>
```

Baixar imagem do Dockerhub

```
docker pull <nome-da-imagem:tag>
```

Ver imagens

```
docker images
```

Criar/rodar um container de uma imagem

```
docker run -p <porta-externa>:<porta-interna> --name <nome-do-container> --network <nome-da-rede> <nome-da-imagem:tag>
```

Listar containers

```
docker ps

docker ps -a
```

Acompanhar logs do container em execução

```
docker logs -f <container-id>
```
