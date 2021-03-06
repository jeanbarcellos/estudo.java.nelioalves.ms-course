_Repositório apenas para estudo_

# Curso: Microsserviços Java com Spring Boot e Spring Cloud

Códigos gerado a partir do curso '**Microsserviços Java com Spring Boot e Spring Cloud**'

<br>

**Descrição:**

Aprenda a estruturar um sistema de microsserviços Java com Spring Boot e Spring Cloud.

Você vai aprender a criar, passo a passo e do absoluto zero, um sistema composto por vários microsserviços que comunicam entre si de forma **transparente**, **escalável** e com **balanceamento de carga**.

Os microsserviços são registrados em um "Discovery Server" (Eureka), de modo que a comunicação entre eles é feita pelo nome do microsserviço. Além disso, as requisições são feitas em um **API Gateway** (Zuul), responsável por rotear e autorizar as requisições.

Você vai aprender a trabalhar com **autenticação e autorização**, usando **OAuth** e tokens **JWT**. Além disso, vai aprender como gerar e testar os containers **Docker** para deixar os microsserviços e as bases de dados aptos para implantação.

O objetivo deste curso não é esgotar todos recursos do ecossistema Spring, mas sim apresentar uma introdução, de forma bem didática, de algumas das principais ferramentas do Spring Cloud, de modo que o desenvolvedor se familiarize com o processo básico de construção dos microsserviços, sua configuração e comunicação, e possa depois seguir se especializando se assim desejar.

Os conteúdos do curso incluem:

- **Feign** para requisições de API entre microsserviços
- **Ribbon** para balanceamento de carga
- _Servidor_ **Eureka** para registro dos microsserviços
- _API Gateway_ **Zuul** para roteamento e autorização
- **Hystrix** para tolerância a falhas
- **OAuth** e **JWT** para autenticação e autorização
- Servidor de configuração centralizada com dados em repositório Git
- Geração de containers **Docker** para os microsserviços e bases de dados

Este curso é de **nível iniciante** do ponto de vista de microsserviços e do ferramental Spring Cloud, mas vale ressaltar que **não é para iniciantes em Java ou Spring Boot**. É preciso já ter pelo menos conhecimento básico de construção de API's REST com Spring Boot e Java.

Estou muito feliz em apresentar este curso para você, e desejo que ele possa contribuir para você dar mais um passo na sua carreia. Um grande abraço e te vejo nas aulas.

<br>

**O que será aprendido:**

- Uma introdução a algumas das principais ferramentas do Spring Cloud para estruturação de um sistema em microsserviços
- Chamadas de API entre microsserviços por meio de clientes Feign
- Criar microsserviços escaláveis, com resolução de nomes e balanceamento de carga de forma transparente, usando servidor Eureka
- Roteamento transparente de microsserviços com Zuul API Gateway
- Configuração centralizada por meio de um servidor de configuração
- Autenticação e autorização compartilhada por meio do API Gateway, usando Oauth e JWT

<br>

**Instrutor:**

- [Nélio Alves](https://www.udemy.com/user/nelio-alves/)

**Referências:**

- https://www.udemy.com/course/microsservicos-java-spring-cloud/
- https://github.com/acenelio/ms-course

## Conteúdo do curso

- Seção 01: Introdução
- Seção 02: Fase 1: Comunicação simples, Feign, Ribbon
- Seção 03: Fase 2: Eureka, Hystrix, Zuul
- Seção 04: Fase 3: Configuração centralizada
- Seção 05: Fase 4: Autenticação e autorização
- Seção 06: Criando e testando containers Docker

<br>

## Visão geral do sistema

![Visão geral do sistema](https://raw.githubusercontent.com/jeanbarcellos/estudo.java.nelioalves.ms-course/master/docs/01.JPG)

## Anotações

- **RestTemplate**

  - Cliente síncrono para executar solicitações HTTP, expondo uma API de método de modelo simples sobre bibliotecas cliente HTTP subjacentes
  - [Documentação](https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/web/client/RestTemplate.html)

- **Feign client**

  - Cliente de serviço da Web declarativo. Facilita a escrita de clientes de serviço da web.
  - Requisições de API entre microsserviços
  - [Documentação](https://docs.spring.io/spring-cloud-openfeign/docs/current/reference/html/)

- **Ribbon**

  - Biblioteca Inter Process Communication (IPC) do lado do cliente que é testada em nuvem. Frnece recursos como:
    - Balanceamento de carga
    - Tolerância ao erro
    - Suporte a múltiplos protocolos (HTTP, TCP, UDP) em um modelo assíncrono e reativo
    - Cache e batching
  - Fornece algoritmos de balanceamento de carga do lado do cliente
  - [Documentação](https://github.com/Netflix/ribbon)

- **JAXB**

  - Fornece suporte à manipulação de objetos Java e XML. Sua principal característica é a capacidade de vincular XML a objetos Java e vice-versa
  - [Documentação](https://javaee.github.io/jaxb-v2/)

- **Spring Cloud**

  - Responsável por integrar todas as soluções em aplicações Spring Boot, onde toda configuração é feita através de anotações e propriedades do `application.properties`;
  - [Documentação](https://spring.io/projects/spring-cloud)

- **Eureka, Discovery Server**

  - Comunicação e descoberta de serviços em uma arquitetura de microservices
  - Resolução de nomes e balanceamento de carga de forma transparente
  - Permite com que serviços sejam registrados através do _Eureka Server_ e descobertos através do _Eureka Client_, facilitando esse controle de aplicação distribuída
  - [Documentação](https://spring.io/projects/spring-cloud-netflix)
  - [Artigo: Michelli Brito](https://medium.com/@michellibrito/netflix-eureka-comunica%C3%A7%C3%A3o-entre-microservices-383d32d39506)

- **Hystrix**

  - É uma biblioteca de latência e tolerância a falhas projetada para isolar pontos de acesso a sistemas remotos, serviços e bibliotecas de terceiros, interromper a falha em cascata e permitir a resiliência em sistemas distribuídos complexos onde a falha é inevitável
  - [Documentação](https://github.com/Netflix/Hystrix)

- **Zuul, API Gateway**

  - Solução de roteamento dinâmico que possibilita monitoramento, resiliência e segurança para aplicações, que também pode ser encontrada no sub-projeto spring-cloud-netflix.
  - [Documentação](https://github.com/Netflix/zuul)

- **Actuator**

  - Monitorar nosso aplicativo, reunir métricas, entender o tráfego ou o estado de nosso banco de dados torna-se trivial com essa dependência
  - Disponibiliza série de recursos adicionais para ajudá-lo a monitorar e gerenciar seu aplicativo ao colocá-lo em produção
  - [Documentação](https://docs.spring.io/spring-boot/docs/current/reference/html/actuator.html)

- **OAuth**

  - É um protocolo de autorização que permite que uma aplicação se autentique em outra. Para que isso aconteça, uma aplicação pede permissão de acesso para um usuário, sem que para isso ela tenha acesso a alguma senha dele. O usuário pode conceder ou não o acesso à aplicação. Depois da permissão ser aceita, caso o usuário precise alterar a senha de acesso, a permissão continuará válida para a aplicação e, caso necessário, a permissão dada à aplicação pode ser revogada a qualquer momento também.
  - [Documentação](https://oauth.net/2/)

- **Spring Cloud Security**

  - Fornece um conjunto de princípios básicos para a construção de aplicativos e serviços seguros com o mínimo de confusão
  - [Documentação](https://spring.io/projects/spring-cloud-security)

<br>

## Bugs encontratos + Soluções

- **Geral**

  Ao criar os projetos, copiar o pom.xml do mesmo projeto do repositório do curso:

  ```
  https://github.com/acenelio/ms-course
  ```

- **Aula 21 - Histrix para tolerância de falhas**

  Projeto para de funcionar pois o pacote `com.netflix.hystrix.contrib` não é encontrato

  - Bug:

    `import com.netflix.hystrix.contrib.javanica.annotation.HystrixCommand;` não é encontrado

  - Solução:

    Em todos os projetos, no arquivo `pom.xml` trocar a versão do `Hoxton` da `8` para a `9`.

    Antes:

    ```xml
    <version>Hoxton.SR9</version>
    ```

    Depois:

    ```xml
    <version>Hoxton.SR8</version>
    ```

- **Aula 30 - Repositório Git privativo**

  - Bug:

    Github não autoriza o acesso ao diretório privado, mesmo com o login e senha corretos.

  - Solução:

    O Github só autoria acesso a diretório privado, usando o protocolo HTTP, através de um token de acesso. Então ao invés de informar a senha, deve-se informar o token gerado.

    - Deve-se gerar um token para acesso http no `Github`

      Tutotial: https://docs.github.com/pt/github/authenticating-to-github/creating-a-personal-access-token

    - Colocar o token gerado na variável de ambiente `GITHUB_PASS`

- **Aula 41 - Login e token JWT PARTE 2/2**

  - Bug:

    Projeto `hr-oauth` não sobre.

  - Solução:

    Adicionar a seguinte dependência no arquivo `pom.xml` do projeto `hr-oauth`

    ```xml
    <dependency>
      <groupId>com.sun.xml.bind</groupId>
      <artifactId>jaxb-impl</artifactId>
      <version>2.3.4</version>
    </dependency>
    ```

    ATENÇÃO: A Versão deve ser a mesma que está no início do arquivo `pom.xml`

    ```xml
      <parent>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-starter-parent</artifactId>
      <version>2.3.4.RELEASE</version>
      <relativePath /> <!-- lookup parent from repository -->
    </parent>
    ```

- **Aula 42 - Autorização pelo Zuul**

  - Bug:

    Projeto `hr-api-gateway-zuul` não sobre.

  - Solução:

    Mesma solução encontrada para o bug da aula 41

    Adicionar a seguinte dependência no arquivo `pom.xml` do projeto `hr-api-gateway-zuul`

    ```xml
    <dependency>
      <groupId>com.sun.xml.bind</groupId>
      <artifactId>jaxb-impl</artifactId>
      <version>2.3.4</version>
    </dependency>
    ```

    ATENÇÃO: A Versão deve ser a mesma que está no início do arquivo `pom.xml`

    ```xml
      <parent>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-starter-parent</artifactId>
      <version>2.3.4.RELEASE</version>
      <relativePath /> <!-- lookup parent from repository -->
    </parent>
    ```

## Mapa e resumo dos microserviços e seus containers

![Mapa de contaniers](https://raw.githubusercontent.com/jeanbarcellos/estudo.java.nelioalves.ms-course/master/docs/02.JPG)

- **hr-worker** - Manipulação dos trabaladores - **_Porta Diâmica_**

  - Eureka Client
  - Config Client _(configuraçãoes de acesso ao banco de dados)_
  - Banco de Dados Postgres
    - **_Porta 5432_**

- **hr-payroll** - Serviço para calcular a folha de pagamento - **_Porta Diâmica_**

  - Eureka Client
  - Fegin Clients _(comunicação com o microsserviço hr-worker)_
  - Circuit breaker - Hystrix _(tolerância a falhas)_
  - Load Balance - Ribbon _(balanceamento de carga)_

- **hr-user** - Manipulação dos usuários - **_Porta Diâmica_**

  - Eureka Client
  - Config Client _(configuraçãoes de acesso ao banco de dados)_
  - Banco de Dados Postgres
    - **_Porta 5433_**

- **hr-oauth** - Serviço de autenticação - **_Porta Diâmica_**

  - Eureka Client
  - Config Client _(configurações de autenticação)_
  - Fegin Clients _(comunicação com o microsserviço hr-user)_

- **hr-config-server** - Servidor de configurações - **_Porta 8888_**

  - Config Server

- **hr-eureka-server** - Servidor de registro dos microsserviços - **_Porta 8761_**

  - Eureka Server

- **hr-api-gateway-zuul** - API Gateway para roteamento e autorização - **_Porta 8765_**

  - Zuul Server
  - Eureka Client
  - Config Client _(configuraçãoes para autorização)_

## TO-DO / Trabalhos Futuros

### **Upgrade dos serviços**

- Criar um novo repostório com a atualização dos serviços que foram descontinuados:
  - **Anteriormente** --> **Hoje**
  - Hystrix --> **Resliience4J**
  - Ribbon --> **Spring Cloud Load Balancer**
  - Zuul --> **Spring Cloud Gateway**
