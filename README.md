# JAVA_PLACE

- import & import static, can use import static to import static method withour reference to class
- use @RestController and @RequestMapping("/api/v1/books") to define a spring mvc controller, use @GetMapping to annotate the method to handle specific request
- Test class annotated with @SpringBootTest should has the same package path with application class that annotated with @SpringBootApplication
  > src/main/java/com.your.package/applicationClass   src/test/java/com.your.package/testClass
- in order to simulate the application shut down, use this @DirtiesContext(classMode = DirtiesContext.ClassMode.AFTER_EACH_TEST_METHOD) in class signature to kill spring context between each test methods
