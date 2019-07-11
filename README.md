## Navigation
- [Navigation](#Navigation)
- [Instructions](#Instructions)
- [Hibernate FAQs](#Hibernate-FAQs)
- [Spring FAQs](#Spring-FAQs)


## Instructions
- For best viewing experience on your phone switch to Desktop Mode
- To view the entire page on phone click on **View all of README.md**
- Best viewed on PC
- Please cross-check ambigous/confusing content

* * *

## Hibernate FAQs

1. __`hibernate.cfg.xml` file__<br>
   `hibernate.cfg.xml` file is used to configure various properties for Hibernate framework
    - `connection.driver_class` ➜ The JDBC driver class
    - `connection.url` ➜ JDBC connection String
    - `connection.username`, `connection.password` ➜ Username and Password for DB
    - `dialect` ➜ This property makes Hibernate generate the appropriate SQL for the chosen database
    - `show_sql` ➜ used to show the generated SQL on console
    - `hbm2ddl.auto` ➜ creates the table automatically
      - create
      - update
      - create-drop
      - validate

2. __Persistent Object__<br>
   Persistent Object : <br>
   > Persistent objects are instances of POJO classes that you create that represent rows in the table in the database.
   > According to hibernate-doc an instance of POJO class representing table in database goes through 3 states of which persistent is one of them.

3. __Bag Collection__<br>
   A Bag is a java collection that stores elements without caring about the sequencing, but allow duplicate elements in the list. A bag is a random grouping of the objects in the list. A Collection is mapped with a `<bag>` element in the mapping table and initialized with `java.util.ArrayList`.

4. __In which state object is not associated with Session__<br>
   Transient & Detached

5. __Different `@Annotations` in Hibernate__<br>
   - `@Entity`
   - `@Column`
   - `@Id`
   - `@GeneratedValue`

6. __Different types of Association Mapping in Hibernate__<br>
   - OneToOne
   - OneToMany
   - ManyToOne
   - ManyToMany

7. __`get()` v/s `load()`__<br>
    <table>
        <tr>
            <th><samp>get()</samp></th>
            <td><samp>load()</samp></th>
        </tr>
        <tr>
            <td>Returns null if an object is not found.</td>
            <td>Throws ObjectNotFoundException if an object is not found.</td>
        </tr>
        <tr>
            <td><samp>get()</samp> method always hit the database.</td>
            <td><samp>load()</samp> method doesn't hit the database.</td>
        </tr>
        <tr>
            <td><samp>get()</samp> returns the real object, not the proxy.</td>
            <td><samp>load()</samp> returns proxy object.</td>
        </tr>
        <tr>
            <td><samp>get()</samp> should be used if you are not sure about the existence of instance.</td>
            <td><samp>load()</samp> should be used if you are sure that instance exists.</td>
        </tr>
    </table>

8. __Different Hibernate Inheritence Strategies__<br>
    - Table Per Hierarchy
      - `@Inheritance(strategy=InheritanceType.SINGLE_TABLE) `
    - Table Per Concrete class
      - `@Inheritance(strategy = InheritanceType.TABLE_PER_CLASS)`
    - Table Per Subclass
      - `@Inheritance(strategy=InheritanceType.JOINED)`

9.  __First Level Cache & Second Level Cache__<br>
    First Level Cache:
    > First level is maintained at the Session level and accessible only to the Session.
    > Can use the first level cache to store local data i.e. the data which is needed by the Session

    Second Level Cache:
    > Second level cache is maintained at the SessionFactory level and available to all Sessions.
    > Can use the second level cache to store global data i.e. something which can be shared across sessions.

10. __Hibernate Architecture Layers__<br>
    3 Main Layers
    - Java Application Layer
    - Hibernate Framework Layer
    - Backend API Layer _(Optional)_
    - DB Layer

11. __What is Hibernate?__<br>
    Hibernate is a Java framework that simplifies the development of Java application to interact with the database. It is an open source, lightweight, ORM (Object Relational Mapping) tool. Hibernate implements the specifications of JPA (Java Persistence API) for data persistence.

12. __Configuration in Hibernate__<br>
    - Combination of Configuration XML and Mapping XML file
    - Annotations

13. __Advantages and Jobs of ORM__<br>
    ORM stands for Object/Relational mapping. It is the programmed and translucent perseverance of objects in a Java application in to the tables of a relational database using the metadata that describes the mapping between the objects and the database. It works by transforming the data from one representation to another.

    _Advantages:_
    - Speeds-up Development - eliminates the need for repetitive SQL code.
    - Overcomes vendor specific SQL differences - the ORM knows how to write vendor specific SQL so you don't have to.

14. __Criteria Query & How to create it__<br>
    Hibernate provides alternate ways of manipulating objects and in turn data available in RDBMS tables. One of the methods is Criteria API, which allows you to build up a criteria query object programmatically where you can apply filtration rules and logical conditions.

    The Hibernate `Session` interface provides `createCriteria()` method, which can be used to create a `Criteria` object that returns instances of the persistence object's class when your application executes a criteria query.

15. __Significance of `hbm2ddl.auto`__<br>
    `hibernate.hbm2ddl.auto` Automatically validates or exports schema DDL to the database when the SessionFactory is created. With create-drop, the database schema will be dropped when the SessionFactory is closed explicitly.
    - *validate*: validate the schema, makes no changes to the database.
    - *update*: update the schema.
    - *create*: creates the schema, destroying previous data.
    - *create-drop*: drop the schema when the SessionFactory is closed explicitly, typically when the application is stopped.

16. __Significance of Session object in Hibernate__<br>
    A Session is used to get a physical connection with a database. The Session object is lightweight and designed to be instantiated each time an interaction is needed with the database. Persistent objects are saved and retrieved through a Session object.

17. __Methods of Session object__<br>
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

18. __EAGER v/s LAZY loading__<br>
    Lazy loading:
    > Lazy Loading. It is the default behavior of an Entity Framework, where a child entity is loaded only when it is accessed for the first time. 
    > It simply delays the loading of the related data, until you ask for it.

    EAGER loading:
    > Eager Loading helps you to load all your needed entities at once; i.e., all your child entities will be loaded at single database call. 
    > This can be achieved, using the Include method, which returs the related entities as a part of the query and a large amount of data is loaded at once.

19. __Significance of HQL__<br>
    It is more beneficial to use HQL instead of native SQ retrieve data from databases. The following are some of the reasons why HQL is preferred over SQL:
    - Provides full support for relational operations.
    - Return results as objects.
    - Supports polymorphic queries.
    - Easy to learn and use.
    - Supports many advanced features as compared to SQL, such as pagination, fetch join etc.
    - Provides database independency.

20. __Important components in Hibernate Architecture__<br>
    - Configuration Object
    - SessionFactory Object
    - Session Object
    - Transaction Object
    - Query Object
    - Criteria Object

21. __LifeCycle states of an object in Hibernate__<br>
    - Transient State
      > A transient state is one where hibernate session is not associated with the object instance and does not represent a row in the database table.
    - Persistent State
      > A persistent state is one where hibernate session is associated with the object instance and does represent a row in the database table with a valid primary key identifier.
    - Detached State
      > In this state, the persistent object still exists after the closure of the active session. In other words, the changes to the pojo object will not be reflected in the database and vice-versa.
    - Removed State
      > When the persistent object is deleted from the database, it is passed to the session’s `delete(obj)` method. At this state, java instance exists but any changes made to the object are not saved to the database.
      <![Object LifeCycle in Hibernate](/objectLifeCycle.jpeg)>

22. __Different annotations used in `@ManyToMany` Association__<br>
    - `@JoinTable`
    - `@JoinColumn`

23. __Properties in `HBM XML` file__<br>
    - The mapping document is an XML document having `<hibernate-mapping>` as the root element, which contains all the `<class>` elements.

    - The `<class>` elements are used to define specific mappings from a Java classes to the database tables. The Java class name is specified using the name attribute of the class element and the database table name is specified using the table attribute.

    - The `<meta>` element is optional element and can be used to create the class description.

    - The `<id>` element maps the unique ID attribute in class to the primary key of the database table. The name attribute of the id element refers to the property in the class and the column attribute refers to the column in the database table. The type attribute holds the hibernate mapping type, this mapping types will convert from Java to SQL data type.

    - The `<generator>` element within the id element is used to generate the primary key values automatically. The class attribute of the generator element is set to native to let hibernate pick up either identity, sequence, or hilo algorithm to create primary key depending upon the capabilities of the underlying database.

    - The `<property>` element is used to map a Java class property to a column in the database table. The name attribute of the element refers to the property in the class and the column attribute refers to the column in the database table. The type attribute holds the hibernate mapping type, this mapping types will convert from Java to SQL data type.

24. __Named Query & Criteria Query__<br>
    - Named Query:
      > A named query is a statically defined query with a predefined unchangeable query string. They're validated when the session factory is created, thus making the application to fail fast in case of an error.
    - Criteria Query:
      > The Hibernate Criteria Query Language (HCQL) is used to fetch the records based on the specific criteria. The Criteria interface provides methods to apply criteria such as retreiving all the records of table whose salary is greater than 50000 etc.

25. __Pagination in Hibernate__<br>
    The idea behind Pagination Hibernate is to divide the large result set into a number of pages and fetching one page at a time. We can programmatically declare how many records should contain each page and from what record. For example, the page may contain 5 records staring from 3rd record.

    The code is simple to do the job of Pagination Hibernate.
    ```java
    Query q = session.createQuery("select * from Student"); // you can use order by also 
    q.setFirstResult(3); // starting position of the record (first record is 0, that is, 0, 1, 2, 3)
    q.setMaxResults(5); // size of page; each page displays 5 records (3, 4, 5, 6, 7)
    List list1 = q.list(); // iterate the list to get each page with Iterator or for loop
    ```

26. __Named Parameter/Dynamic Parameter (`=:`)__<br>
    Named parameters are as name itself suggests, the query string will be using the parameters in the variable name. That can be replaced at runtime and one advantage of using named parameter is, the same named parameter can be used many times in the same query.
    ```java
    String queryStr = "from Student s where s.name like :searchName";
    List result = session.createQuery(queryStr)
                .setString("searchName",searchNameValue)
                .list;
    ```

27. __JPA Annotations__<br>
    Package : `javax.persistence`
    - `@Entity`
    - `@Table`
    - `@Column`
      - `@Id`
    - `@GeneratedValue`
    - `@OrderBy`
    - `@Transient`
    - Mapping Annotations:
      - `@OneToOne`
      - `@OneToMany`
      - `@ManyToMany`
    - `@PrimaryKeyJoinColumn`
    - `@JoinColumn`
      - `@JoinColumn`

28. __`MappedBy` & `@JoinColumn` usage__<br>
    JPA Relationships can be either unidirectional or bidirectional. It simply means we can model them as an attribute on exactly one of the associated entities or both.

    Defining the direction of the relationship between entities has no impact on the database mapping. It only defines the directions in which we use that relationship in our domain model.

    For a bidirectional relationship, we usually define:
    - the owning side
    - inverse or the referencing side

    The `@JoinColumn` annotation helps us specify the column we’ll use for joining an entity association or element collection. On the other hand, the `mappedBy` attribute is used to define the referencing side (non-owning side) of the relationship.



<hr>
 

## Spring FAQs

1. __BeanFactory v/s ApplicationContext__<br>
    <table>
        <tr>
            <th>BeanFactory</th>
            <td>ApplicationContext</th>
        </tr>
        <tr>
            <td>This is the root interface for accessing the Spring container.</td>
            <td>The ApplicationContext is the central interface within a Spring application that is used for providing configuration information to the application.</td>
        </tr>
        <tr>
            <td>Provides object when <code>getBean()</code> is called.</td>
            <td>Provides a singleton object as soon as the instance of ApplicationContext IOC is created.</td>
        </tr>
        <tr>
            <td><code>XMLBeanFactory</code></td>
            <td><code>ClassPathXmlApplicationContext</code></td>
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

6. __`@PathVariable` & `@RequestParam`__<br>
   - `@PathVariable`
     > It is used to pass parameter along with the url, sometimes we need to pass parameters along with the url to get the data. Spring MVC provides support for customizing the URL in order to get data. To achieving this purpose `@PathVariable` annotation is used in Spring mvc framework.
   - `@RequestParam`
     > In Spring MVC, the `@RequestParam` annotation is used to read the form data and bind it automatically to the parameter present in the provided method.

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
     Spring Component annotation is used to denote a class as Component. It means that Spring framework will autodetect these classes for dependency injection when annotation-based configuration and classpath scanning is used.
     - `@Controller`: Mostly used with web applications or REST web services to specify that the class is a front controller and responsible to handle user request and return appropriate response.
     - `@Service`: Denotes that the class provides some services. Our utility classes can be marked as Service classes.
     - `@Repository`: This annotation indicates that the class deals with CRUD operations, usually it’s used with DAO implementations that deal with database tables.

9.  __Role of Controller in Spring__<br>
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

16. __Autowiring Collection Types__<br>
    1. *autowire byName* – For this type of autowiring, setter method is used for dependency injection. Also the variable name should be same in the class where we will inject the dependency and in the spring bean configuration file.
    2. *autowire byType* – For this type of autowiring, class type is used. So there should be only one bean configured for this type in the spring bean configuration file.
    3. *autowire by constructor* – This is almost similar to autowire byType, the only difference is that constructor is used to inject the dependency.
    4. *autowire by autodetect* – If you are on Spring 3.0 or older versions, this is one of the autowire options available. This option was used for autowire by constructor or byType, as determined by Spring container. 
    5. *`@Autowired` annotation* – We can use Spring `@Autowired` annotation for spring bean autowiring. `@Autowired` annotation can be applied on variables and methods for autowiring byType. We can also use `@Autowired` annotation on constructor for constructor based spring autowiring.
    6. *`@Qualifier`annotation* – This annotation is used to avoid conflicts in bean mapping and we need to provide the bean name that will be used for autowiring. This way we can avoid issues where multiple beans are defined for same type. This annotation usually works with the `@Autowired` annotation. For constructors with multiple arguments, we can use this annotation with the argument names in the method.

17. __What is `ModelAndView`?__<br>
    `ModelAndView` is an object that holds both the model and view. The handler returns the `ModelAndView` object and `DispatcherServlet` resolves the view using View Resolvers and View. The View is an object which contains view name in the form of the String and model is a map to add multiple objects.

18. __View Resolvers__<br>
    - Spring MVC Framework provides the ViewResolver interface, that maps view names to actual views.
    - It also provides the View interface, which addresses the request of a view to the view technology. So when a ModelAndView instance is returned by a Controller, the view resolver will resolve the view according to the view name.
    - *Types*:
      - `AbstractCachingViewResolver`
      - `XmlViewResolver`
      - `ResourceBundleViewResolver`
      - `UrlBasedViewResolver`
      - `InternalResourceViewResolver`
      - `ContentNegotiatingViewResolver`

19. __`@ModelAttribute` Annotation__<br>
    - Firstly, it can be used to inject data objects to the model before a JSP loads. This makes it particularly useful in ensuring that a JSP has all the data is needs to display itself. The injection is achieved by binding a method return value to the model.
    - Secondly, it can be used to read data from an existing model assigning it to handler method parameters.

20. __Locating `hibernate.cfg.xml` file__<br>
    To ask Hibernate look for your `hibernate.cfg.xml` file in other directory, you can modify the default Hibernate’s SessionFactory class by passing your `hibernate.cfg.xml` file path as an argument into the `configure()` method:
    ```java
    SessionFactory sessionFactory = new Configuration()
    .configure("/com/mkyong/persistence/hibernate.cfg.xml")
    .buildSessionFactory();

    return sessionFactory;
    ```

21. __About `InternalResourceViewResolver`__<br>
    The `InternalResourceViewResolver` is an implementation of `ViewResolver` in Spring MVC framework which resolves logical view name e.g. "hello" to internal physical resources e.g. Servlet and JSP files e.g. jsp files placed under WEB-INF folder. It is a subclass of `UrlBasedViewResolver`, which uses "prefix" and "suffix" to convert a logical view name returned from Spring controller to map to actual, physical views.<br>
    *Important Points*:
    1. When chaining ViewResolvers, an `InternalResourceViewResolver` always needs to be last, as it will attempt to resolve any view name, no matter whether the underlying resource actually exists.
    2. The `InternalResourceViewResolver` is also the default view resolver of `DispatcherServlet` class, which acts as the front controller in Spring MVC framework.
    3. By default, `InternalResourceViewResolver` returns `InternalResourceView` (i.e. Servlets and JSP) but it can be configured to return JstlView by using the `viewClass` attribute.

22. __`@Resource` Annotation__<br>
    `@Resource` is the annotaion that will help to extract beans from the container.<br>
    There are several lookup options to extract beans:
    - Match by Name
    - Match by Type
    - Match by Qualifier
    <br>
    Using @Resource without any parameters will trigger Match by Type lookup type.

23. __Attributes of `<bean>` tag__<br>
    - *name / id*: This attribute specifies the bean unique identifier.
    - *class*: This attribute is mandatory and specify the bean class to be used to create the bean.
    - *scope*: This attribute specifies the scope of the objects created from a particular bean definition.
    - *constructor-arg*: This is used to inject the dependencies through bean constructor.
    - *properties*: This attribute is used to inject the dependencies through setter method.
    - *autowiring mode*: This is used to inject the dependencies.
    - *init-method (initialization method)*: A callback to be called just after all necessary properties on the bean have been set by the container. This is part of bean lifecycle.
    - *destroy-method (destruction method)*: A callback to be used when the container containing the bean is destroyed. This is part of bean lifecycle.



<br>
<br>
<br>
<br>
<p align="center">Made with ❤ by <a href="https://abhinavsharma.dev/">Abhinav Sharma</a></p>
<p align="center">Keep updating the page! More content maybe up!</p>