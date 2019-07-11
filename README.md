## Hibernate FAQs

1. __`hibernate.cfg.xml` file__<br>
   `hibernate.cfg.xml` file is used to configure various properties for Hibernate framework
    - `connection.driver_class`
    - `connection.url`
    - `connection.username`, `connection.password`
    - `dialect` ➜
    - `show_sql` ➜ used to show the generated SQL on console
    - `hbm2ddl.auto` ➜ creates the table automatically
      - create
      - update
      - create-drop
      - validate

2. __Persistent Object & Collection Object__<br>
   Persistent Object : <br>
   > Persistent objects are instances of POJO classes that you create that represent rows in the table in the database.
   > According to hibernate-doc an instance of POJO class representing table in database goes through 3 states of which persistent is one of them.

   Collection Object : <br>

3. __Bag Collection__<br>
   A Bag is a java collection that stores elements without caring about the sequencing, but allow duplicate elements in the list. A bag is a random grouping of the objects in the list. A Collection is mapped with a `<bag>` element in the mapping table and initialized with `java.util.ArrayList`.

4. __Collection Mapping in Hibernate using XML__<br>
5. __In which state object is not associated with Session__<br>
   Transient & Detached

6. __Different `@Annotations` in Hibernate__<br>
   - `@Entity`
   - `@Column`
   - `@Id`
   - `@GeneratedValue`

7. __Different types of Association Mapping in Hibernate__<br>
   - OneToOne
   - OneToMany
   - ManyToOne
   - ManyToMany

8. __`get()` v/s `load()`__<br>
   `get()`|`load()`
   ----------|----------
   Returns null if an object is not found. | Throws ObjectNotFoundException if an object is not found.
   get() method always hit the database. | load() method doesn't hit the database.
   get() returns the real object, not the proxy. | load() returns proxy object.
   get() should be used if you are not sure about the existence of instance. | load() should be used if you are sure that instance exists.

9. __Different Hibernate Inheritence Strategies__<br>
    - Table Per Hierarchy
      - `@Inheritance(strategy=InheritanceType.SINGLE_TABLE) `
    - Table Per Concrete class
      - `@Inheritance(strategy = InheritanceType.TABLE_PER_CLASS)`
    - Table Per Subclass
      - `@Inheritance(strategy=InheritanceType.JOINED)`

10. __First Level Cache & Second Level Cache__<br>
    First Level Cache:
    > First level is maintained at the Session level and accessible only to the Session.
    > Can use the first level cache to store local data i.e. the data which is needed by the Session

    Second Level Cache:
    > Second level cache is maintained at the SessionFactory level and available to all Sessions.
    > Can use the second level cache to store global data i.e. something which can be shared across sessions.

11. __Hibernate Architecture Layers__<br>
    3 Main Layers
    - Java Application Layer
    - Hibernate Framework Layer
    - Backend API Layer _(Optional)_
    - DB Layer

12. __What is Hibernate?__<br>
    Hibernate is a Java framework that simplifies the development of Java application to interact with the database. It is an open source, lightweight, ORM (Object Relational Mapping) tool. Hibernate implements the specifications of JPA (Java Persistence API) for data persistence.

14. __Configuration in Hibernate__<br>
    - Combination of Configuration XML and Mapping XML file
    - Annotations

15. __Advantages and Jobs of ORM__<br>
    ORM stands for Object/Relational mapping. It is the programmed and translucent perseverance of objects in a Java application in to the tables of a relational database using the metadata that describes the mapping between the objects and the database. It works by transforming the data from one representation to another.

    _Advantages:_
    - Speeds-up Development - eliminates the need for repetitive SQL code.
    - Overcomes vendor specific SQL differences - the ORM knows how to write vendor specific SQL so you don't have to.

16. __Criteria Query & How to create it__<br>
    Hibernate provides alternate ways of manipulating objects and in turn data available in RDBMS tables. One of the methods is Criteria API, which allows you to build up a criteria query object programmatically where you can apply filtration rules and logical conditions.

    The Hibernate `Session` interface provides `createCriteria()` method, which can be used to create a `Criteria` object that returns instances of the persistence object's class when your application executes a criteria query.

17. __Significance of `hbm2ddl.auto`__<br>
    `hibernate.hbm2ddl.auto` Automatically validates or exports schema DDL to the database when the SessionFactory is created. With create-drop, the database schema will be dropped when the SessionFactory is closed explicitly.
    - *validate*: validate the schema, makes no changes to the database.
    - *update*: update the schema.
    - *create*: creates the schema, destroying previous data.
    - *create-drop*: drop the schema when the SessionFactory is closed explicitly, typically when the application is stopped.

18. __Significance of Session object in Hibernate__<br>
    A Session is used to get a physical connection with a database. The Session object is lightweight and designed to be instantiated each time an interaction is needed with the database. Persistent objects are saved and retrieved through a Session object.

19. __Methods of Session object__<br>
    - `beginTransaction()`
    - `save()`
    - `update()`
    - `saveOrUpdate()`
    - `createQuery()`
    - `createSQLQuery()`
    - `merge()`
    - `persist()`
    - `flush()`
    - `delete()`

20. __EAGER v/s LAZY loading__<br>
    Lazy loading:
    > Lazy Loading. It is the default behavior of an Entity Framework, where a child entity is loaded only when it is accessed for the first time. 
    > It simply delays the loading of the related data, until you ask for it.

    EAGER loading:
    > Eager Loading helps you to load all your needed entities at once; i.e., all your child entities will be loaded at single database call. 
    > This can be achieved, using the Include method, which returs the related entities as a part of the query and a large amount of data is loaded at once.

21. __Significance of HQL__<br>
    It is more beneficial to use HQL instead of native SQ retrieve data from databases. The following are some of the reasons why HQL is preferred over SQL:
    - Provides full support for relational operations.
    - Return results as objects.
    - Supports polymorphic queries.
    - Easy to learn and use.
    - Supports many advanced features as compared to SQL, such as pagination, fetch join etc.
    - Provides database independency.

22. __Important components in Hibernate Architecture__<br>
    - Configuration Object
    - SessionFactory Object
    - Session Object
    - Transaction Object
    - Query Object
    - Criteria Object

23. __LifeCycle states of an object in Hibernate__<br>
    - Transient State
      > A transient state is one where hibernate session is not associated with the object instance and does not represent a row in the database table.
    - Persistent State
      > A persistent state is one where hibernate session is associated with the object instance and does represent a row in the database table with a valid primary key identifier.
    - Detached State
      > In this state, the persistent object still exists after the closure of the active session. In other words, the changes to the pojo object will not be reflected in the database and vice-versa.
    - Removed State
      > When the persistent object is deleted from the database, it is passed to the session’s `delete(obj)` method. At this state, java instance exists but any changes made to the object are not saved to the database. 

24. __Different annotations used in `@ManyToMany` Association__<br>
    - `@JoinTable`
    - `@JoinColumn`


<hr>


## Spring FAQs

1. __BeanFactory v/s ApplicationContext__<br>
    <table>
        <th>
            <td>`BeanFactory`</td>
            <td>`ApplicationContext`</td>
        </th>
        <tr>
            <td>This is the root interface for accessing the Spring container.</td>
            <td>The ApplicationContext is the central interface within a Spring application that is used for providing configuration information to the application.</td>
        </tr>
        <tr>
            <td>Provides object when `getBean()` is called.</td>
            <td>Provides a singleton object as soon as the instance of ApplicationContext IOC is created.</td>
        </tr>
        <tr>
            <td>`XMLBeanFactory`</td>
            <td>`ClassPathXmlApplicationContext`</td>
        </tr>
    </table>

2. __Basic Spring Configuration File__<br>
   Spring configuration file is a file with `.xml` extension and the file contains information about the classes and interfaces and their dependencies. Using this file the spring container controls the life cycle of a spring bean and also Dependency Injection is achieved.

3. __Configuring constructor DI using XML__<br>
   Assume these 3 files:
   `IndexApp.java` - Calling Class
   ```java
    public class IndexApp {
        private IService service;
        // constructor will get the service reference
        // standard constructors/getters/setters
    }
   ```
   `IService.java` - Service interface
   ```java
    public interface IService {
        public String serve();
    }
   ```

   `Service.java` - Service implementing class
   ```java
    public class IndexService implements IService {
        @Override
        public String serve() {
            return "Hello World";
        }
    }
   ```

   Constructor DI:
   ```xml
    <bean
    id="indexApp"
    class="com.lti.di.spring.IndexApp">
        <constructor-arg ref="service" />
    </bean>    
   ```

4. __Spring Scopes__<br>
   - *singleton*: This scopes the bean definition to a single instance per Spring IoC container (default).
   - *prototype*: This scopes a single bean definition to have any number of object instances.
   - *request*: This scopes a bean definition to an HTTP request. Only valid in the context of a web-aware Spring ApplicationContext.
   - *session*: This scopes a bean definition to an HTTP session. Only valid in the context of a web-aware Spring ApplicationContext.
   - *global-session*: This scopes a bean definition to a global HTTP session. Only valid in the context of a web-aware Spring ApplicationContext.

5. __`@RequestMapping` Annotation__<br>
   - This annotation maps HTTP requests to handler methods of MVC and REST controllers.
   - The `@RequestMapping` annotation can be applied to class-level and/or method-level in a controller.

6. __`@Path` Variable__<br>
   It is used to pass parameter along with the url, sometimes we need to pass parameters along with the url to get the data. Spring MVC provides support for customizing the URL in order to get data. To achieving this purpose @PathVariable annotation is used in Spring mvc framework.

7. __Declarative Transaction Management in Spring__<br>
   Declarative transaction management approach allows you to manage the transaction with the help of configuration instead of hard coding in your source code. This means that you can separate transaction management from the business code. You only use annotations or XML based configuration to manage the transactions. The bean configuration will specify the methods to be transactional.

   Steps:
   1. Define a transaction manager in `spring.xml`
      ```xml
      <bean class="org.springframework.jdbc.datasource.DataSourceTransactionManager" id="txManager"/>
      ```  
   2. Turn on support for transaction annotations, add to `spring.xml`
      ```xml
      <tx:annotation-driven transaction-manager="txManager"/>
      ``` 
   3. Add the `@Transactional` annotation to the desired method
      ```java
        @Transactional
        public int desiredMethod(Param paramObj) {...}
      ```

8. __Configuring a bean through Annotations__<br>
   - `@Component`
     - `@Controller`
     - `@Service`
     - `@Repository`

9. __Role of Controller in Spring__<br>
    - A controller contains the business logic of an application. Here, the @Controller annotation is used to mark the class as the controller.
    - A front controller is defined as a controller that handles all requests for a Web Application. DispatcherServlet servlet is the front controller in Spring MVC that intercepts every request and then dispatches requests to an appropriate controller.

10. __Important Bean LifeCycle Methods__<br>
    - `InitializingBean`
      - `afterPropertiesSet()`
    - `DisposableBean`
      - `destroy()`

11. __Role of `ContextLoadListener`__<br>
    The ApplicationContext is where your Spring beans live. The purpose of the ContextLoaderListener is two-fold:
    - to tie the lifecycle of the ApplicationContext to the lifecycle of the ServletContext and
    - to automate the creation of the ApplicationContext, so you don't have to write explicit code to do create it - it's a convenience function.

12. __Which method invokes GRACEFUL shutdown?__<br>
    `registerShutdownHook()`

13. __@Configuration & @Bean__<br>
    - `@Configuration`
        > Spring @Configuration annotation is part of the spring core framework. Spring Configuration annotation indicates that the class has @Bean definition methods. So Spring container can process the class and generate Spring Beans to be used in the application.
    - `@Bean`
        > Spring @Bean Annotation is applied on a method to specify that it returns a bean to be managed by Spring context. Spring Bean annotation is usually declared in Configuration classes methods. In this case, bean methods may reference other @Bean methods in the same class by calling them directly.

14. __What is AOP and DI?__<br>
    - AOP:
        > Aspect-Oriented Programming (AOP) is a programming paradigm that aims to increase modularity by allowing the separation of cross-cutting concerns.
    - DI:
        > Dependency Injection (DI) is a design pattern used to implement IoC. It allows the creation of dependent objects outside of a class and provides those objects to a class through different ways. Using DI, we move the creation and binding of the dependent objects outside of the class that depends on them.

15. __Basic Spring Modules__ <br>
    - Spring Core Module
    - Spring Context Module
    - Spring DAO Module
    - Spring ORM Module
    - Spring AOP Module
    - Spring WEB-MVC Module

16. 















### Working on more content! Check soon (of course before exam)