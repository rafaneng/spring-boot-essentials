# Spring Boot 2 Essentials 25 - Sorting, Log SQL

Ao adicionar o Pageable, temos o Sort, para utilizar basta inserir na URL o parametro sort, exemplo:

sort=name,asc

sort=name,desc

Por padrão, o show-sql do application.yml, imprime o sql fora do padrao do Spring, ele simplesmente imprime sem nenhum tipo de appender. O Spring usa o logback. (Isso pode influenciar a performance)

Para trocar, para inserir o logging no application.yml e remover o show-sql

```yaml
spring:
  datasource:
    url: jdbc:mysql://localhost:3306/anime?createDatabaseIfNotExist=true
    username: root
    password: root
  jpa:
    hibernate:
      ddl-auto: update
    ~~show-sql: true~~
logging:
  level:
    org:
      hibernate:
        SQL: DEBUG
```

Video no Youtube: [https://youtu.be/mg8zkaPQPxs](https://youtu.be/mg8zkaPQPxs)

---

[Volte ao início](https://github.com/rafaneng/spring-boot-essentials#spring-boot-essentials-2---devdojo)