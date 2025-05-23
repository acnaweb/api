# Java 

- Spring Initializr
  - https://start.spring.io/
- Controller
  - @RestController
  - @RequestMapping("/ping")
- Endpoints (rotas)
  - GET @GetMapping
  - GET @GetMapping("/rota1")
  - GET @GetMapping("/rota2")
- OpenAPI 
  - Spring Doc - https://springdoc.org/
  - Swagger https://swagger.io/specification/
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
- Http Status Code
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
  - query findBy*()
- Spring Data Relationships
  - @ManyToOne
  - @Cascade(value = CascadeType.ALL)
  - @JoinColumn(name = "entity_id")
  - @OneToMany
  - @OneToMany(mappedBy = "attr", cascade = CascadeType.ALL, orphanRemoval = true)   
  - @OneToOne
- Spring Data Projections
- Spring Framework Profiles
- Database Environment Variable
- Docker
- Docker Composer
- Deploy Manual to Cloud
- Lombok
- Exception Handler
- Unit Tests
- Spring List Of Values
- Validation
- Security
- API Versioning
- DTO Mapper
- Code Quality - Checkstyle 
- Docker Composer
- Continuous Integration
- Continuous Delivery
- Continuous Deployment
- Cache
- Integration WebWook
- Integration Kafka
