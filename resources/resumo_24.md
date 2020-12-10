# Spring Boot 2 Essentials 24 - WebMvcConfigurer

Como podemos trocar o tamanho padrão das páginas

1. Criar novo pacote chamado "configurer"
2. Criar nova classe "DevDojoWebMvcConfigurer"
3. Inserir anotação @Configuration e implementar WebMvcConfigurer na classe
4. Sobrescrever o método "addArgumentResolvers"

```java
import org.springframework.context.annotation.Configuration;
import org.springframework.data.domain.PageRequest;
import org.springframework.data.web.PageableHandlerMethodArgumentResolver;
import org.springframework.web.method.support.HandlerMethodArgumentResolver;
import org.springframework.web.servlet.config.annotation.WebMvcConfigurer;

import java.util.List;

@Configuration
public class DevDojoWebMvcConfigurer implements WebMvcConfigurer {
    @Override
    public void addArgumentResolvers(List<HandlerMethodArgumentResolver> resolvers) {
        PageableHandlerMethodArgumentResolver pageHandler = new PageableHandlerMethodArgumentResolver();
        pageHandler.setFallbackPageable(PageRequest.of(0,10));
        resolvers.add(pageHandler);
    }
}
```

Video no Youtube: [https://youtu.be/1_Bp3JFZ4Cs](https://youtu.be/1_Bp3JFZ4Cs)

---

[Volte ao início](https://github.com/rafaneng/spring-boot-essentials#spring-boot-essentials-2---devdojo)