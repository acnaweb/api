# Java


## Feature Flag


## Spring API Rest
O Spring Boot permite construir APIs RESTful de forma rápida e simples.

📘 Guia oficial: https://spring.io/guides/tutorials/rest

Exemplo:
```java
@RestController
@RequestMapping("/ping")
public class PingController {
    @GetMapping
    public String ping() {
        return "pong";
    }
}
```

## Spring Initializr
Ferramenta para geração de projetos Spring Boot.

🌐 https://start.spring.io/

Selecione dependências como:
- Spring Web
- Spring Data JPA
- MySQL Driver
- Lombok

## Controller
Define endpoints da aplicação.

```java
@RestController
@RequestMapping("/ping")
public class PingController {
    @GetMapping
    public String ping() {
        return "pong";
    }

    @GetMapping("/rota1")
    public String rota1() {
        return "rota1";
    }

    @GetMapping("/rota2")
    public String rota2() {
        return "rota2";
    }
}
```

## Endpoints (rotas)
- `@GetMapping`: leitura
- `@PostMapping`: criação
- `@PutMapping`: atualização
- `@DeleteMapping`: exclusão

```java
@GetMapping("/{id}")
public Produto findById(@PathVariable Long id) { ... }

@PostMapping
public Produto create(@RequestBody Produto produto) { ... }
```

## OpenAPI
Documentação interativa da API.

- 📘 https://springdoc.org/
- 📘 https://swagger.io/specification/

Configuração:
```properties
springdoc.swagger-ui.path=/
```

Acesse em `http://localhost:8080/`

## Http Status Code
Referência: https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Status

Exemplos:
```java
return ResponseEntity.status(201).body(produto);
return ResponseEntity.ok(produto);
return ResponseEntity.noContent().build();
return ResponseEntity.notFound().build();
```

## ResponseEntity
Classe que representa a resposta HTTP.

```java
ResponseEntity.ok(obj);
ResponseEntity.status(HttpStatus.CREATED).body(obj);
ResponseEntity.notFound().build();
ResponseEntity.noContent().build();
```

## Service
Camada que contém a lógica de negócio da aplicação.

```java
@Service
public class ProdutoService {
    public ProdutoDto findById(Long id) {
        return repository.findById(id)
            .map(this::toDto)
            .orElseThrow(() -> new RuntimeException("Not found"));
    }
}
```

## Database
Configuração do MySQL:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/api?createDatabaseIfNotExist=true
spring.datasource.username=root
spring.datasource.password=root_pwd
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.database-platform=org.hibernate.dialect.MySQLDialect
```

## Spring Data Repository
Interface para persistência:

```java
public interface ProdutoRepository extends JpaRepository<Produto, Long> {
    List<Produto> findByNomeContaining(String nome);
}
```

## Optional
Evita `NullPointerException`:

```java
Optional<Produto> produto = repository.findById(1L);
produto.ifPresent(System.out::println);
```

## List<?> Stream
Manipulação com Java Streams:

```java
List<Produto> ativos = produtos.stream()
    .filter(p -> p.isAtivo())
    .map(this::toDto)
    .collect(Collectors.toList());
```

## DTO Mapper
Conversão entre entidades e DTOs.

```java
public ProdutoDto toDto(Produto model) { ... }
public Produto toModel(ProdutoDto dto) { ... }
```

🔗 https://modelmapper.org/

## Spring Data Relationships
Mapeamento entre entidades:

```java
@OneToMany(mappedBy = "pedido", cascade = CascadeType.ALL, orphanRemoval = true)
private List<Item> items;

@ManyToOne
@JoinColumn(name = "pedido_id")
private Pedido pedido;
```

## Spring Data Projections
Projeções de dados com interfaces:

```java
public interface ProdutoView {
    String getNome();
    BigDecimal getValor();
}
```

🔗 https://www.baeldung.com/spring-data-jpa-projections

## Pagination & Sort
Paginação com Pageable:

```java
@GetMapping
public Page<Produto> listar(Pageable pageable) {
    return repository.findAll(pageable);
}
```

## Spring Framework Profiles
Configuração por ambiente:

```properties
# application-dev.properties
app.feature.enabled=true
```

Execução:
```bash
-Dspring.profiles.active=dev
```

## Spring Environment Variable
Uso de variáveis externas:

```properties
app.url=${APP_URL:http://localhost}
```

## Docker
Empacotando a aplicação:

```dockerfile
FROM openjdk:17
COPY target/api.jar app.jar
ENTRYPOINT ["java", "-jar", "/app.jar"]
```

## Docker Composer
Gerenciando múltiplos containers:

```yaml
version: '3'
services:
  db:
    image: mysql
    environment:
      MYSQL_ROOT_PASSWORD: root_pwd
      MYSQL_DATABASE: api
```

## Deploy Manual to Cloud
Opções:
- Google Cloud Run
- AWS Elastic Beanstalk
- Azure App Service

## Lombok
Simplifica getters, setters, construtores.

```java
@Data
@NoArgsConstructor
@AllArgsConstructor
@Entity
public class Produto { ... }
```

🔗 https://projectlombok.org/

## Exception Handler
Tratamento global:

```java
@ControllerAdvice
public class GlobalExceptionHandler {
    @ExceptionHandler(NotFoundException.class)
    public ResponseEntity<String> handleNotFound(NotFoundException e) {
        return ResponseEntity.status(404).body(e.getMessage());
    }
}
```

## Unit Tests
Teste com MockMvc:

```java
@SpringBootTest
@AutoConfigureMockMvc
class ProdutoControllerTest {
    @Autowired MockMvc mockMvc;

    @Test
    void testPing() throws Exception {
        mockMvc.perform(get("/ping")).andExpect(status().isOk());
    }
}
```

## Spring List Of Values
Uso de herança em entidades:

```java
@Entity
@Inheritance(strategy = InheritanceType.JOINED)
public abstract class Pessoa { ... }
```

## Validation
Validação de entrada:

```java
public record ProdutoDto(
    @NotBlank(message = "Nome é obrigatório")
    String nome
) { }
```

## Security
Exemplo com `httpBasic()`:

```java
@Override
protected void configure(HttpSecurity http) throws Exception {
    http.authorizeRequests().anyRequest().authenticated().and().httpBasic();
}
```

## API Versioning
Controle de versão por rota:

```java
@RequestMapping("/api/v1/produtos")
```

## Code Quality - Checkstyle
Ferramenta de análise estática de código.

🔗 https://checkstyle.sourceforge.io/

## Continuous Integration / Delivery / Deployment
Ferramentas:
- GitHub Actions
- Jenkins
- GitLab CI/CD

## Cache
Anotação `@Cacheable`:

```java
@Cacheable("produtos")
public Produto buscar(Long id) { ... }
```

## Migrations
Usando Flyway:

```sql
-- V1__create_produto.sql
CREATE TABLE produto (...);
```

🔗 https://www.baeldung.com/database-migrations-with-flyway

## Integration WebWook
Envio de eventos:

```java
restTemplate.postForEntity("https://webhook.site", payload, Void.class);
```

## Integration Kafka
Produção de mensagens:

```java
@Autowired
private KafkaTemplate<String, String> kafka;

kafka.send("topico", "mensagem");
```

## Api Gateway
Utilize:
- Spring Cloud Gateway
- Kong
- NGINX

Configuração de roteamento e segurança de entrada.
