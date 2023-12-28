# JAVA_PLACE

- import & import static, can use import static to import static method without reference to class
- use @RestController and @RequestMapping("/api/v1/books") to define a spring mvc controller, use @GetMapping to annotate the method to handle specific request
- Test class annotated with @SpringBootTest should has the same package path with application class that annotated with @SpringBootApplication
  > src/main/java/com.your.package/applicationClass   src/test/java/com.your.package/testClass
- in order to simulate the application shut down, use this @DirtiesContext(classMode = DirtiesContext.ClassMode.AFTER_EACH_TEST_METHOD) in class signature to kill spring context between each test methods
- use @repository to mark a repository to use Spring JPA to manage data.
- spring的原理 [link](https://github.wdf.sap.corp/d022051/SpringTutorial/wiki/SpringContext)
- @SpringBootApplication annotation is combination of @SpringBootConfiguration annotation, @EnableAutoConfiguration annotation and @ComponentScan annotation.
  
> SpringBootConfiguration
@SpringBootApplication annotation is an alternatevice to spring Configuration annotation. it is used to tell application that this class is Spring Boot Configuration.
@ComponentScan
ComponentScan annotation is used to scan directories for configuraiton class. it is annotation is equivalent to Spring XML's element. it provides basePackageClasses or basePackages or its alias value which specify which packages to scan. If packages are not defined,then package of the configuration class anotated with ComponentScan will be condised ad default package to scan.
@EnableAutoConfiguration
EnableAutoConfiguration annotation is used to enable spring boot automatic configuration of application context. it will find the configured beans in the class path. All the jars or configuration classes added in class path will be included in application context.

- @EnableJpaRepositories to include JPA repository that defined out of class path of @EnableAutoConfiguration
- @EnableConfigurationProperties to import the POJO only annotated with @ConfigurationProperties
- compare integer, you shouldn't use ==, but .equals
- DTO stand for Data Transfet Object, check [DTO](https://martinfowler.com/eaaCatalog/dataTransferObject.html) , dto object need getter and setter
- use Lombok annotation to reduce boilerplate code [offical document](https://projectlombok.org/features/)
- use transient keyword to exclude an attribute during seralization
- Runnable can be called via Thread interface, Callable can be called only via ExecutorService.
- generic type on method   public <T> T somemethod(T t), when call it, don't need to specify the T explicility, just somemethod("XXX")
- .equal won't trigger type conversion Long C = 3L, 3L.equal(1+2) false
- Autoboxing and unBoxing in JAVA
- _Character_ object contains helper method to assert the type of character
- when no constructor explicitly declared, there will be default constructor, when a contructor with parameter is defined, the dafult is surpressed.
- you find jar is not executable after mvn packaging, you may check this [Spring Boot Maven Plugin](https://www.baeldung.com/spring-boot-fix-the-no-main-manifest-attribute)
set is not ordered measn the order of element in set doesn't follow the order elements added, but set would sort elemenet with it's own sort algorithm.
- a way to build relation between parent table and child table is create a foreign key in child table that point to the primary key of parent table, code below
  ```java
  public class Parent {
      @Id
      private Long id;
  
      @OneToMany(mappedBy = "parent", cascade = CascadeType.ALL)
      private List<Child> children = new ArrayList<>();
  
      //Other fields, getters and setters
  }
  
  @Entity
  public class Child {
      @Id
      private Long id;
  
      @ManyToOne(fetch = FetchType.LAZY)
      @JoinColumn(name = "parent_id")
      private Parent parent;
  
      //Other fields, getters and setters
  }
  ```

- there are two ways to send http request

WebClient:

WebClient is a non-blocking, reactive web client introduced in Spring 5.
It's part of Spring WebFlux module and is suitable for event-loop style processing that can scale with a small number of threads.
WebClient can work efficiently in high load scenarios and can handle streaming scenarios better due to its non-blocking nature.
It also supports Server-Sent Events (SSE) and WebSockets.
WebClient is recommended for new Spring projects.

RestTemplate:

RestTemplate is a blocking, non-reactive client which was the main way to do HTTP client-side operations in Spring 3.x and 4.x versions.
It's part of Spring Web MVC module and is not suitable for handling many concurrent connections because one thread is used for one request/response.
RestTemplate does not support SSE and WebSockets.
As of Spring 5, RestTemplate is in maintenance mode and the Spring team suggests WebClient as its replacement.
high precision should use BigDecimal class, instead of float or double, Big decimal would take more memory and slower.
