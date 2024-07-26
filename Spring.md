[Spring Boot Offical Guideline](https://docs.spring.io/spring-boot/docs/2.0.0.M4/reference/html/index.html)

- how to create own auto-configuration,Auto-configuration classes can be bundled in external jars and still be picked-up by Spring Boot.
  brief: spring.factories under META-INF [link](https://docs.spring.io/spring-boot/docs/2.0.0.M4/reference/html/boot-features-developing-auto-configuration.html)
  *tips:* the target bean better be a class @Configuration and @ComponentScan to get all beans

- spring-boot-devtools automatic restart whenever changes are made
