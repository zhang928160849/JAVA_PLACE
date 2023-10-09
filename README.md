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
- use Lombok annotation to reduce boilerplate code
- use transient keyword to exclude an attribute during seralization
- Runnable can be called via Thread interface, Callable can be called only via ExecutorService.
