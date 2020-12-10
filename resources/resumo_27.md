# Spring Boot 2 Essentials 27 - RestTemplate exchange

Quando fazemos a requisição em alguma API que retorna mais de um elemento, o interessante é armazenar essa resposta em uma List. 

### Usando Array

Podemos pensar em retornar em um Array, mas nos dias atuais isso não é tão legal.

```java
import academy.devdojo.springboot2.domain.Anime;
import lombok.extern.log4j.Log4j2;
import org.springframework.core.ParameterizedTypeReference;
import org.springframework.http.HttpMethod;
import org.springframework.http.ResponseEntity;
import org.springframework.web.client.RestTemplate;

import java.util.List;

@Log4j2
public class SpringClient {
    public static void main(String[] args) {
        
        Anime[] animes = new RestTemplate().getForObject("http://localhost:8080/animes/all", Anime[].class);
        log.info(Arrays.toString(animes));
    }
}
```

### exchange()

O ideal é fazer essa conversão utilizando o método exchange() conforme exemplo:

```java
import academy.devdojo.springboot2.domain.Anime;
import lombok.extern.log4j.Log4j2;
import org.springframework.core.ParameterizedTypeReference;
import org.springframework.http.HttpMethod;
import org.springframework.http.ResponseEntity;
import org.springframework.web.client.RestTemplate;

import java.util.List;

@Log4j2
public class SpringClient {
    public static void main(String[] args) {

        ResponseEntity<List<Anime>> exchange = new RestTemplate().exchange("http://localhost:8080/animes/all",
                HttpMethod.GET,
                null,
                new ParameterizedTypeReference<>() {
                }
        );
        log.info(exchange.getBody());
    }
}
```

Video no Youtube: [https://youtu.be/f93kYkmIyPo](https://youtu.be/f93kYkmIyPo)

---

[Volte ao início](https://github.com/rafaneng/spring-boot-essentials#spring-boot-essentials-2---devdojo)