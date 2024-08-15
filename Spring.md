[Spring Boot Offical Guideline](https://docs.spring.io/spring-boot/docs/2.0.0.M4/reference/html/index.html)

- how to create own auto-configuration,Auto-configuration classes can be bundled in external jars and still be picked-up by Spring Boot.
  brief: spring.factories under META-INF [link](https://docs.spring.io/spring-boot/docs/2.0.0.M4/reference/html/boot-features-developing-auto-configuration.html)
  *tips:* the target bean better be a class @Configuration and @ComponentScan to get all beans

- IoC and ApplicationContext,
   @Component is generic stereotype
   @Service
   @Repository
   @Controller
   @Bean
   @Configuration

With @Configuration + @Bean we could produced the bean, !

- spring-boot-devtools automatic restart whenever changes are made
- Secutity Context store the authentication object and authority

- @PostConstruct There's no hard and fast rule against using `@PostConstruct` for that purpose.

Using `@PostConstruct` to initialize data during startup can be beneficial, especially if the data doesn't change frequently and will be used across the application, as it reduces the need for repeated database calls.

However, there are a few things to consider:

1. **Application Startup Time:** If reading the data from the database and initializing the list takes too long, it can prolong the startup time of your application. This could be a problem if you need your application to start quickly.

2. **Error Handling:** If there is a problem reading the data from the DB during startup (e.g., DB is down or there is a network issue), you need to handle this in your `@PostConstruct` method in order to prevent your application from failing during startup. 

3. **Data Freshness:** Depending on when and how often the underlying data changes, you might serve stale data. If the data is changing constantly and the accuracy of real-time data is essential, then pre-loading data might not be the best strategy.

4. **Memory Usage:** Depending on the amount of data being pulled in, this might consume significant memory, which might bring down your application if the size of the list is huge.

So, the use of `@PostConstruct` for database reading and data initialization really depends on the use case, and it might be worthwhile to evaluate these points before going ahead with this approach.

