# Spring Boot 2 Essentials 26 - RestTemplate getForObject e getForEntity

Quando estamos desenvolvendo, algum momento precisaremos realizar uma requisição para outro serviço/URL externa mas não queremos fazer essa requisição manualmente. O Spring oferece uma biblioteca que realiza isso automaticamente.

### Criando um RestTemplate

Começamos criando um package client e uma classe SpringClient

```java
import academy.devdojo.springboot2.domain.Anime;
import lombok.extern.log4j.Log4j2;
import org.springframework.http.ResponseEntity;
import org.springframework.web.client.RestTemplate;

@Log4j2
public class SpringClient {
    public static void main(String[] args) {
        ResponseEntity<Anime> entity = new RestTemplate().getForEntity("http://localhost:8080/animes/{id}", Anime.class, 9);
        log.info(entity);

        Anime object = new RestTemplate().getForObject("http://localhost:8080/animes/{id}", Anime.class, 9);
        log.info(object);
    }
}
```

### getForEntity()

Neste caso, convertemos e a armazenamos a resposta em uma Response Entity. Informamos a URL, qual a classe para ele realizar a conversão e utilizamos uma variável chamada id para buscar. Caso seja necessário inserir mais de uma variável, basta inserir virgula e ele fará a inserção na mesma sequencia.

O retorno no terminal virá com todas as informações, exemplo:

```bash
09:15:16.663 [main] DEBUG org.springframework.web.client.RestTemplate - HTTP GET http://localhost:8080/animes/9
09:15:16.754 [main] DEBUG org.springframework.web.client.RestTemplate - Accept=[application/json, application/*+json]
09:15:16.813 [main] DEBUG org.springframework.web.client.RestTemplate - Response 200 OK
09:15:16.820 [main] DEBUG org.springframework.web.client.RestTemplate - Reading to [academy.devdojo.springboot2.domain.Anime]
09:15:16.852 [main] INFO academy.devdojo.springboot2.client.SpringClient - <200,Anime(id=9, name=testee),[Content-Type:"application/json", Transfer-Encoding:"chunked", Date:"Thu, 10 Dec 2020 12:15:16 GMT", Keep-Alive:"timeout=60", Connection:"keep-alive"]>
```

### getForObject()

Aqui, convertetemos diretamente para um objeto, dispensando muitas informações, exemplo:

```bash
09:16:39.688 [main] DEBUG org.springframework.web.client.RestTemplate - HTTP GET http://localhost:8080/animes/9
09:16:39.767 [main] DEBUG org.springframework.web.client.RestTemplate - Accept=[application/json, application/*+json]
09:16:39.823 [main] DEBUG org.springframework.web.client.RestTemplate - Response 200 OK
09:16:39.828 [main] DEBUG org.springframework.web.client.RestTemplate - Reading to [academy.devdojo.springboot2.domain.Anime]
09:16:39.851 [main] INFO academy.devdojo.springboot2.client.SpringClient - Anime(id=9, name=testee)
```

Video no Youtube: [https://youtu.be/Qnxv6ovn3Xc](https://youtu.be/Qnxv6ovn3Xc)

---

[Volte ao início](https://github.com/rafaneng/spring-boot-essentials#spring-boot-essentials-2---devdojo)