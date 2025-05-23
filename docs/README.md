# Java 

- Spring API Rest
  - https://spring.io/guides/tutorials/rest
- Spring Initializr - https://start.spring.io/
- Controller
  - @RestController
  - @RequestMapping("/ping")
- Endpoints (rotas)
  - GET @GetMapping
  - GET @GetMapping("/rota1")
  - GET @GetMapping("/rota2")
- OpenAPI 
  - Spring Doc - https://springdoc.org/
  - Swagger - https://swagger.io/specification/
  - application.properties
  ```
  springdoc.swagger-ui.path=/
  ```
- Endpoints (rotas)
  - GET @GetMapping 
  - POST @PostMapping - @RequestBody
  - GET @GetMapping("{id}") - @PathVariable
  - PUT @PutMapping("{id}") - @PathVariable + @RequestBody
  - DELETE @DeleteMapping("{id}") - @PathVariable
- Http Status Code - https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Status
  - ResponseEntity.status(201)
  - ResponseEntity.status(200)
  - ResponseEntity.status(204)
  - ResponseEntity.status(404)
- ResponseEntity
  - ResponseEntity.ok
  - ResponseEntity.notFound
  - ResponseEntity.noContent
- Service
- Database
  - application.properties
  ```
  spring.datasource.url=jdbc:mysql://localhost:3306/api?createDatabaseIfNotExist=true
  spring.datasource.username=root
  spring.datasource.password=root_pwd
  spring.jpa.hibernate.ddl-auto=update
  spring.jpa.show-sql=true
  spring.jpa.open-in-view=true
  spring.jpa.database-platform=org.hibernate.dialect.MySQLDialect
   ```
- @Entity @Id @GeneratedValue
- Spring Data Repository
- Optional
- List<?> Stream
  - filter
  - map
  - collect(Collectors.toList())
  - orElseExcept
- Spring Data Repository
  - https://www.baeldung.com/spring-data-derived-queries
  - query findBy*()
- DTO Mapper
  - toDto() & toModel()
  - https://www.baeldung.com/java-modelmapper
  - https://modelmapper.org/
- Spring Data Relationships
  - https://www.baeldung.com/spring-data-rest-relationships
  - @ManyToOne
  - @Cascade(value = CascadeType.ALL)
  - @JoinColumn(name = "entity_id")
  - @OneToMany
  - @OneToMany(mappedBy = "attr", cascade = CascadeType.ALL, orphanRemoval = true)   
  - @OneToOne
- Spring Data Projections
  - https://docs.spring.io/spring-data/jpa/reference/repositories/projections.html
  - https://www.baeldung.com/spring-data-jpa-projections
- Spring Framework Profiles
  - https://docs.spring.io/spring-boot/docs/1.2.0.M1/reference/html/boot-features-profiles.html 
  - https://www.baeldung.com/spring-profiles
- Spring Environment Variable
  - https://docs.spring.io/spring-boot/docs/1.2.0.M1/reference/html/boot-features-profiles.html
- Docker
  - https://docs.docker.com/reference/dockerfile/
  - https://docs.docker.com/get-started/docker_cheatsheet.pdf
- Docker Composer
  - https://docs.docker.com/compose/
- Deploy Manual to Cloud
- Lombok
  - https://projectlombok.org/
- Exception Handler
  - https://www.baeldung.com/exception-handling-for-rest-with-spring
- Unit Tests
  - https://www.baeldung.com/spring-boot-testing
- Spring List Of Values
  - https://www.baeldung.com/hibernate-inheritance
- Validation
  - https://www.baeldung.com/spring-boot-bean-validation
  - @Valid
  - @NotBlank(message = "Name is mandatory")
- Security
  - https://www.baeldung.com/security-spring
- API Versioning
  - 
- Code Quality - Checkstyle 
- Docker Composer
- Continuous Integration
- Continuous Delivery
- Continuous Deployment
- Cache
- Migrations
- Integration WebWook
- Integration Kafka
