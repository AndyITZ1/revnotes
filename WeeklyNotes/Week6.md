# Week 6 Spring

### What is Spring?
- **Spring** is loosely, loaded term, in what it can refer to in different contexts. 
- **Spring** can refer to:
    - Spring Framework
    - Spring Projects
    - Spring Beans
    - Spring Boot
    - and more...
- However most of the time without being given a context, **Spring** refers to the overall **Spring Framework**. 

### What is Spring Framework?
- **Spring Framework** is a popular application **framework** and **inversion of control** container for the Java platform. It is a core part of the Spring Tools Suite with Spring Boot. Spring Framework can be used as a standalone open-source framework to support the development of enterprise scale applications. 

### What are benefits to using the Spring Framework?
- The ability to use POJOs when developing enterprise-class applications.
    - POJOs (Plain Old Java Objects) are basically types that have no references to any particular frameworks and that mainly a POJO has no naming convention for properties/methods. 
        - Furthermore there isn't any real convention for constructing/accessing/modifying the class's state. Which overall creates issues in terms limiting a framework's ability to **favor convention over configuration**, understand how to use the class and augment its functionality. 
    - With the Spring Framework we can convert our POJOs into Beans (Spring Beans), these are still POJOs but with more strict sets of rules that are followed in implementation
        - Access levels – our properties are private and we expose getters and setters
        - Method names – our getters and setters follow the getX and setX convention (in the case of a boolean, isX can be used for a getter)
        - Default Constructor – a no-argument constructor must be present so an instance can be created without providing arguments, for example during deserialization
- Testing with Spring applications is simple, because of features like **Dependency Injection**, which allows us to have application classes be independent of each other for class reusability and for unit testing. **Dependency Injection (DI)** basically helps fill in the gap of having to manage a dependency part of a class. 
    - If class A is dependent on class B, meaning that it has property of type Class B, then we need to make sure that property of type Class B is filled in to meet testing needs of Class A.
    - With DI, Spring IoC will handle that process of *injecting* class B into class A. Which can be done when passing parameters to constructor or by post-construction using setter methods.

### What is a framework? How is this different from a library?
- A **framework** is simply a structure that you can build software on. It is written code that has already been to extent designed and tested by other software developers and engineers. A framwork acts similar to a template/foundation for you to avoid writing code to setup non-specific feature code and focus more on the core software development of your application. 
- The difference between frameworks and libraries is the **inversion of control**. Similar to how we might have a framework for a house that supports and frames how we do everything else when building the house. A **software framework** does the same for having setup code that only now needs the **everything else**. 
- However this has the effect of **requiring you to specify your own code for what the framework needs** to setup for your project. A **library** does not necessarily do that in that you are calling code that has been written fully so that you can use it immediately when building the application and choose when you want to use such pre-written code. 

### What is Inversion of Control (IoC)?
- **Inversion of Control (IoC)** is self-defined, in that we are changing/reversing/inverting the flow of control over something. To be more specific, **IoC** is a design principle that inverts or transfer control of some part of application development from the developer to a container/framework. 
- An example of this is a **framework** like Spring, where rather you (the developer), even though you are writing your own code, **you have to follow the pattern of a framework**, what this means is that everytime you use a framework it has stuff implemented/framed a certain way and you cannot change how that is framed/implemented. The only thing you are allow to do is provide your code to fill in missing pieces to have the framework to build your application. By doing this, the framework is **in control** of how your application is developed skeleton/frame-wise. 
- A more in depth example of **IoC** is that with Spring IoC, the controlling of Java objects and their lifecycle is managed/done by Spring IoC and not by the developer. We can see this with Spring IoC creating objects for us, managing our objects, managing dependencies, and more. 
- IoC in short is that the flow of control switches/inverts from one thing to another. In the example, you aren't necessarily in control of how to write code as you are "dictated" in how you can write code by the framework.
- Libraries are not IoC in that, you are provided with a **set of previously-written code** this is usually functions. And you are given the "freedom" to pick and choose what code you want to use when developing your application as you are in charge of how your functions/classes/values are determined and setup.  
- Below Example: IoC is demonstrated that with the Spring IoC container we are getting an instance of an object through the ApplicationContext which refers to an XML config file to get a bean/instance created by Spring IoC. 
    - **So instead of calling the direct constructor to make the object we want would only need to getBean() to get the object instance we need and Spring IoC handles the creation of the Score class/object.**
    - NOTE: This example is not an example dependency injection which is a form IoC but Spring IoC can be demonstrated like below without dependency injections.
    - The XML config file is used by us developers to inform the IoC container of various Beans being used in the application and that in general for this example that Spring needs:
        - to manage instance of a class Score
        - Programs in the application will refer to this instance as "thescore" for its name.
```Java

public static void main(String[] args) {

    // Example of IoC in Spring 

    // This first line we the developer use the new keyword and Score constructor to make an instance of a Score object.
    // Here we are creating the object ourselves
    // Score thescore = new Score();

    // Here Spring and using ApplicationContext instance, we are getting an instance of an object that has been created and managed by Spring.
    Score score = context.getBean("thescore", Score.class);
}
```

### What is Dependency Injection?
- Dependency injection (DI) is main functionality in Spring IoC. DI is a *flavor* of IoC, where it helps with loose-coupling of classes, which in general is just keeping classes in Java independent of each other. 
- We can see DI in action when class A needs an object of class B to utilize or use class B's methods. This relationship is class B being a dependency for class A or class A is dependent on class B.
    - This relationship is okay in idea, but could lead to issues where if the dependencies are really needed to make something work and aren't provided then ultimately it may cause the "system to fail" (*system failure*).
- With DI, we resolves such dependencies through which the Spring IoC container handles the instantiation of objects required for implementation and this is also according to configurations specified by the developer. 

### What are the two types of Spring Dependency Injection used?
- The two types of of Spring DI used are **Constructor Injection/Constructor Dependency Injection (CDI)** and **Setter Injection/Setter Dependency Injection (SDI)**.
- Constructor injection is done by using the constructor of the bean (Spring Bean) to instantiate a bean where each argument of the constructor represents a dependency. And DI is handled by Spring IoC to ensure those dependencies are implemented at the time of the current class instantiation.
- Setter injection is Spring IoC creating an instance of the dependency and providing it to the class having the dependency by its setter method.
- In Spring, we can use the `@Autowired` annotation to perform either injection, it should be noted that all the classes should be a Java/Spring Bean, so that Spring can manage them. 
```Java
@Service // This is one way to make a class be a bean.
public class DatabaseAccountService implements AccountService {

	private final RiskAssessor riskAssessor;

	@Autowired // constructor injection
	public DatabaseAccountService(RiskAssessor riskAssessor) {
		this.riskAssessor = riskAssessor;
	}

    /*
    @Autowired // setter injection
    public setRiskAssessor(RiskAssessor riskAssessor) {
        this.riskAssessor = riskAssessor;
    }
    */
	// ...

}
```

### What are Spring Beans?
- **Spring beans** are objects that essentially form the backbone of your application and are managed by the Spring IoC container. A bean is an object that is instantiated, assembled and managed by a Spring IoC container. The Spring IoC container simplifies or help makes beans work by handling processes like of not just creating them but also making sure their dependencies are fulfilled. Which overall means the Spring IoC is the one with the control over not just instantiating/creating a bean but also has other roles like performing DIs vs compared to us (the developers) usually doing all that work.
- Just to reiterate Spring beans get the benefit of having DIs perform on them for necessary dependencies. Regular Java objects will not have this benefit of being managed by the Spring IoC container unless they are declared/configured as Spring Beans.

### How do we create Spring Beans?
- We can define/create Spring Beans using 3 different ways.
- **XML Configuration** is one way to define beans,  in which we utilize an XML configuration file to provide all the necessary configuration metadata for Spring container to know what beans are beind defined. 
```XML
<?xml version = "1.0" encoding = "UTF-8"?>

<beans xmlns = "http://www.springframework.org/schema/beans"
   xmlns:xsi = "http://www.w3.org/2001/XMLSchema-instance"
   xsi:schemaLocation = "http://www.springframework.org/schema/beans
   http://www.springframework.org/schema/beans/spring-beans-3.0.xsd">

   <!-- A simple bean definition -->
   <bean id = "..." class = "...">
      <!-- collaborators and configuration for this bean go here -->
   </bean>

   <!-- A bean definition with lazy init set on -->
   <bean id = "..." class = "..." lazy-init = "true">
      <!-- collaborators and configuration for this bean go here -->
   </bean>

   <!-- A bean definition with initialization method -->
   <bean id = "..." class = "..." init-method = "...">
      <!-- collaborators and configuration for this bean go here -->
   </bean>

   <!-- A bean definition with destruction method -->
   <bean id = "..." class = "..." destroy-method = "...">
      <!-- collaborators and configuration for this bean go here -->
   </bean>

   <!-- more bean definitions go here -->
   
</beans>
```
- **Java Annotation Configuration** is another way to define beans. Similar to XML Configuration, we declarae a bean giving an ID and also the class type object that it will provide an instance of. 
- So we use configuration classes instead of the XML config file and we use `@Bean` instead of the `<bean>` tag.
- It should be noted that this changes from needing to write configurations to just using Java Annotations when specifying the bean we want to create. However annotations in this way are not the same way used in the last method for creating beans. 
- **Annotation Driven (stereotype annotations)** are a final way an automatic way to create Spring Beans in the application context. So instead of specifying some name/id and technically the class to create a Bean instance. Here we just specify what classes are going to be beans and utilized as Beans.

### What are the 4 types of Stereotype Annotations?
- There is `@Component` which is the main Stereotype Annotation used to create a Spring Bean automatically. We use `@Component` to mark the beans as Spring managed components. All remaining types are derived from the `@Component`
- `@Service` is used to mark Service classes to indicate that they hold business logic as the service layer.
- `@Repository` is used to indicate that this bean will deal with CRUD operations (working w/ databases), therefore this is used often with DAOs or Repository Implementations (implements JPA Repository)
- `@Controller` used to specify a class that it is a front controller handling user requests and returning responses. This is used often with REST Web Services.
```Java
```

### What is the difference between Java Annotation Configurations and using just Stereotype Annotations to create/define bean?
- While both methods are valid for creating beans the nuances of how each work differs in the way Spring container interacts or perceives them.
- First Stereotype Annotations are really reliant on the fact that the Spring container has to auto detect "beans" using the classpath. With that this why we use `@ComponentScan` to detect them (classes that are beans) if they are scatter in different base packages. And note that this doesn't make them beans in they are outside the package scan range.
    - We cannot create a bean of a class using `@Component`, if the class is outside Spring container whereas we can create a bean of a class using `@Bean` even if the class is present outside the Spring container.
- With that `@Bean` explicitly declares a single bean, 


### What is a Spring IoC container?
- A Spring Container is an object that instantiates/creates and holds your Spring Beans, then injects them wherever they are being called in the application. The container itself manages the lifecycle of the Spring Beans. There are types of containers in Spring, the BeanFactory and the ApplicationContext, which is a sub-interface of BeanFactory. 

### What is the difference between BeanFactory and ApplicationContext?
- BeanFactory is historical meaning its older than the ApplicationContext and it provides for the basic functionalities of managing and providing the configuration framework for it. And the ApplicationContext is rather a superset of the BeanFactory in that it does all of that and expands with other additional functionalities and features. The ApplicationContext makes it easier to integrate with Spring's AOP features; message resource handling; event publication; and application layer specific contexts. So basically more enterprise-specific functionalities. 
- For the most part, there isn't a huge reason to not just use the ApplicationContext as it does all the same things as BeanFactory and more.  

### What are bean scopes?
- Bean scopes refer to how many instances of a Bean are/can be created and where they are used. There are 6 beans scopes, 2 universal scopes and 4 for specifically web-aware projects.
- **Singleton** is the default value for scopes and when a bean is created in a container, only a single instance of that bean is created. All requests to that bean name will return the same object, which is cached. Which also means any modifications to that object is reflected in all references to that bean. 
- **Prototype**, is the scope where when a bean is requested from a container it will return a new/different instance each time. 
- Web-Aware Application Context Scopes:
    - **Request** scope creates a bean instance for a single HTTP request, each request has a different bean instance that is returned.
    - **Session** scope creates a bean instance for an HTTP session, the same bean instance is returned with any persisted changes made to it for each request in the session. 
    - **Application** scope creates the bean instance for the lifecycle of a ServletContext.
        - Similar to Singleton scope, it creates a bean instance that is shared across mutliple servlet-based applications running the same ServletContext. The difference between Singleton, is that Singleton scoped beans are scoped to a single application context only.
        - Similar to Session scoped beans the data in the instance once set is retained for all subsequent requests, sessions, and for different servlet applications that are running the same ServletContext.
    - **WebSocket** scope creates a bean for a particular WebSocket session.
        - WebSocket scoped bean is the same instance return for the entire WebSocket session and is stored in the WebSocket session attributes. Again only exists in a WebSocket session.


### How do we wire beans (dependency injections)?
- **Bean wiring** is how we connect our beans as dependencies of one another and this is also known as **dependency injection**. 
- There are three types of **Bean Wiring**:
    - Constructor injection
    - Setter injection
    - Field injection (This is bad practice and not used)
- **Autowiring** is the **automagically** effect of Spring IoC container determining the dependencies for you and then injecting them as needed. 
    - This utilizes the **@Autowired** annotation to denote the constructor or setter method to inject the dependency via. **Autowiring** abstracts away the process of dependency injection.


### What are Spring Modules?
- **Spring Modules** are pieces of the Spring Framework that each provide different functionalities to developing enterprise applications.
- Required modules that are utilized to an extent by all Spring applications are:
- **Core** module, which is the one that contains the core functionality of Spring and has the BeanFactory interface which is one of two IoC containers we can use to manage beans.
- The **Bean** module contains Bean configuration and functionality implementation. 
- The **Context** module provides the ApplicationContext interface which is the other IoC container that we can use to manage our beans.
- Modules that we can add on to create different types of projects include:
- **Spring Web MVC** which provides functionality for Spring use functionality for managing requests and resposnes with annotations for controllers 
- **Spring AOP** (Aspect Oriented Programming) provides functionality to handle "cross cutting concerns" such as logging (which occur/involve multiple classes)


### What is Spring Boot?
- **Spring Boot** is a Spring Project used to create standalone Spring-based application that you can **just run**. **Spring Boot** takes on an **opinionated view** of the Spring platform and third-party libraries to allow developers to get started with their applications with minimal and simple build configuration decisions. So in layman's term Spring Boot will decide which packages to install and which default values to use rahter than requiring you to do those configurations. And how it provides the standalone aspect is through providing the necessary stuff like an embedded web server to launch your application on any platform without relying on external web servers. 
- **Spring Boot** also follows the mindset of **Convention over Configuration**, this is a design philosophy which focuses on utilizing reasonable defaults/standards/most working use case in terms how something is setup or conventions basically over the need to manage thingss like configurations and decisions that are rather specific to something. Overall the goal of Spring Boot is to minimize the amount of decisions and work a developer needs to perform to build an application as it will handle and decide for most of what configurations to use and it will apply conventions for the developer just to follow simple-mindedly while being able to focus on the actual more core parts to their applications functionality rather than stressing over configuration details. 

### What are benefits of using Spring Boot?
- With Spring Boot, we don't need to use external web server to run our application, but rather Spring Boot provides an embedded Tomcat Server for us to run and start the Spring Boot application. 
- With Spring Boot, we can choose from "starter" dependencies that will cover typical use cases and will be setup by Spring Boot with default configurations and this also means the pom.xml file will be setup with all the necessary dependencies.
- With how Spring Boot decides/handles default configurations for aspects of the application and dependencies, we no longer need to write/setup as the developer an XML configuration to setup our application. Any at least configuration that Spring Boot won't handle can be done in the application.properties file.
- Spring Boot also provides tools like Spring Boot Actuator and Spring Boot DevTools to help monitor project metrics/information and setup development easily. 

### What is Spring Boot DevTools?
- Spring Boot applications can include a set of tools use to ease development more. With DevTools we are offered 2 major features that improve development workflow:
    - Disabled caching
    - Automatic restarts
- Disabled caching refers to disable the caching features of that some Spring modules utilized to improve performance in their functionalities. However caching at times can hinder development so Spring Boot DevTools automatically disables caching with these modules. 
- Automatic restarts refer to how we may perform manual restarts of application often to utilize/apply any changes that were made regardless of the size of the change. With DevTools it provides the feature of being able to restart the application automatically based on when a file changes in the classpath. 
- Like any other dependency to use Spring Boot DevTools we have to include the appropriate dependency configuration in the config file for Maven or Gradle (Maven config file is the pom.xml)

### What is Spring Boot Actuator?
- Spring Boot Actuator is a Spring library that can be provided in Spring Boot applications to expose tools for monitoring and gathering metrics about a running application.  How it does this is through predefined endpoints that are used to utilize any of its operational feature.
- It should be noted that endpoints can be enabled and disabled and for security should be only enabled in a security chain or excluded to prevent from others beside the developer from accessing it. 
- For routing to a metric use `/actuator/<endpoint-id>`
- Actuator is used to handle many management and monitoring production operations. 
### How does a Spring Boot application work/run?
- For Spring Boot applications, you need to create a "new Spring Starter Project" and to run it we simply need a `@SpringBootApplication` annotation above the main method class and just run the app with `SpringApplication.run(<MainClassName>.class, args);`
- Spring Boot does this all for us as in we don't have to manually set this up. It's already written for us just gotta run the main method to boot the application. 

### What is Spring Web MVC?
- Spring Web MVC is a Spring module that works as a framework that follows the Model-View-Controller design pattern and is used to develop web applications.
- Spring Web MVC is designed around a DispatcherServlet that handles all the HTTP requests and responeses. The DispatcherServlet also dispatches requests to handlers. By using the `@Controller`,  we can defined controller classes that take in requests and handle the sending of responses. We can use `@RequestMapping` to map what requests through a certain URI goes to what controllers to be facilitated. 
- Core parts to Spring Web MVC include:
    - **DispatchServlet**
    - **HandlerMapping** - this is the interface that is **responsible for sending requests to the proper controller**, this is what the `@RequestMapping` annotation does inside a controller class.
    - **@Controller**, is a stereotype annotation but also identifies the class that will handle HTTP Requests from the DispatchServlet. 
    - **ContextLoaderListener** is a Servlet listener which listens for server startup and shutdown events to manage spring beans that will be created during server startup and destroyed during shutodown. Spring Web MVC applications do not need to have a Context Loader Listener as rather it doesn't manage any web-specific beans like the DispatcherServlet. However it does provide a root application context for whcih 
    used to create the root context in Spring web application and this context is shared by different contexts loaded by each DispatcherServlet. The ContextLoaderListener manages the unloading and loading of Spring-managed beans based on reading configuration files and listening for server startup and shutdown. While it provides a root context and handles generic beans that aren't like the ones managed by the DispatcherServlet it is optional 

### What is MVC?
- Model-View-Controller is a design pattern used to define user interfaces, data and controlling. The idea behind is to "separate concerns" of a software's business logic from what is displayed to the end user, and this overall provides better maintenance in terms of what is being spearated. 
- In terms of how MVC is being used in Spring Web MVC, we are using it to divide the structure of how we want to handle certain responsiblities or tasks.
    - The Model is the data being sent back and forth
    - The View is what the user sees, which can change depending on requests sent to the server by the user. 
    - The Controller is the controller classes that takes in the requests and handles them accordingly in terms of responses.

### What is the flow of a Spring MVC Application?
- When a Tomcat server receives a HTTP Request, it gets passed to the DispatcherServlet (Front Controller)
- THe DispatcherServlet consults with the HandleMapping with the URI of the request and sending and determining the controller to send the request to. 
- The controller layer upon receiving the request communicates with the service/business logic layer to process the request
- The controller upon processing the rquest will build the response and hands it back to the DispatcherServlet
- The DispatcherServlet then consults with the ViewResolver if necessary to process a view (this isn't used since we can have our own frontend views)
- The response is then sent back to the Tomcat server which send it to the frontend (where the request came from).
- The HTTP lifecycle continues

### What are annotations used in Spring MVC?
- **@Controller** stereotype annotation used for MVC controllers, makes controller class a bean, and allows class to use specific annotations relevant to Spring MVC. This also makes the class noticeable to the DispatcherServlet
- **@RequestMapping** - specifies the path URI (endpoint) that will be delegated to the controller class and/or its methods. 
    - There are annotations corresponding to each type of request (@GetMapping, @PostMapping)
- **@CrossOrigin** set ups CORS filtering so that we can get requests from the front end and send back responses.
- **@ResponseBody** - Converts the body of our response to JSON automatically
- **@PathVariable** allows for getting a path variable out of the URI and used in the parameter section of the controller method taking in that request
- **@RequestBody** Parses the JSON body of the request to object specified in the parameters of the controller method
- **@RestController** annotation that combines the functionality of both `@Controller` and `@ResponseBody`

### What are Spring Projects?
- **Spring Projects** are similar to add-ons in which we can use them to help build our own application projects. They are built on Spring modules and provide solutions to issues faced by industry-level applications. 
- There are many and all are open source, some examples are Spring Boot and Spring Data.

### What is Spring ORM and Spring Data?
- Spring ORM and **Spring Data** are modules that will handle the application's object relational mapping and the database connection

### What is Spring Data JPA/Spring Data?
- Spring Data JPA is a Spring Project that allows us to easily implement JPA based repositories and enhances support for JPA based data access layers. The goal of Spring Data JPA is to abstract away the effort needed to to implement data access layers. This can be seen with developers being allow to write repository interfaces with custom finder methods, and Spring providing that implementation automatically. 
- JPA stands Java Persistence API, which is utilize to reduce the burden of interacting with databases via Java by forming a "bridge" between object models in Java and relational models in database. In short helps reduce the burden of writing code relational object maangment and allowing for easy interaction with a database instance.

- Spring Data JPA is a Spring Project that we can utilize to implement JPA-based repositories for our data access layers. In terms the goal is for developers to write repository interfaces that have custom finder methods to search/querying in a DB instance from Java, but how these methods are implemented is done automatically by Spring Data JPA.
- JPA stands for Java Persistence API, which is utilize to reduce the burden of interacting with databases from Java, by handling the code for relating Java objects and DB models.

### What does JPA use and do specifically?
- JPA utilizes the **EntityManager interface** to create, read, update and delete DB entities and their data in the database. **This interface is what lets us query/manipulate our database from our Java Server.**
- JPA has standardized annotations for performing object relational mapping and Spring Data uses these data to directly map our Java models to Database tables. In short our DB tables get created by our Java models.

### What are advantages to using Spring Data compared to JDBC?
- JDBC can be more complex especially in larger applications 
- Changing database dialect or flavor would likely lead to editing JDBC statements to match the dialect's syntax. With Spring Data, we don't have to worry as changing a dialect is just a change in the configuration file.
- Spring Data will automatically convert ResultSets into Java objects for us, whereas in JDBC we had to manually conver ResultSets to POJOs
- JDBC requires the developer to specifically know about the database such as table and column names. While Spring Data does not required this because we can create tables as soon as we're done with our Java code. 
- Spring Data requires much less lines of connection code and DAO code and saves us time if we know what we are doing for our CRUD operations. 


### What does the Spring Data Interface hierarchy look like?
- Spring Data's interfaces are what is used to make our DAO classes.
- Hierarchy:
    - **Repository** - Most generic repository
        - **CrudRepository** - used to create a basic repo just from implementing it
            - **PagingAndSortingRepository** -
                - **JpaRepository** - contains most of the basic DAO methods we'll want to use, we can also have saving and flushing methods
                    - **Custom Interface (DAO interfaces)** All repositories should extend from JpaRepository.
- Note: There is class implementation of JpaRepository 

### What are fundamental JPA Annotations?
- **@Entity** is used to indicate a class meant to be mapped to a database table
- **@Table** is used for setting DB table options such as the name of the table (THIS DOES NOT MAKE A CLASS A TABLE, @Entity does that)
- **@Column** defines a Java variable as the column in the DB table. While Hibernate wil turn all of a class's fields into DB columns by default, we can still use @Column to specify things like column names, or constraints (not null, unique...)
- **@Id** declares a variable as the primary key in a table
    - **@GeneratedValue** give us controls over the options for how Hibernate will auto-generate the primary key (GenerationType.IDENTITY for serial values)

### What annotations in JPA are used to define relationships?
- **@ManyToOne**/**@OneToMany**/**@ManyToMany** are used to defined the relationship between model classes in Java.
- To set up the relationship correctly, the relationship is defined from the perspective of the Class in which the annotation sits in. So if a field is on the "Many" side for a many-to-one relationship then it would have the `@ManyToOne` annotation. And vice versa we would put the `@OneToMany` on the field on the "One" side. However only one annotation is needed to represented that relationship and usually thats `@ManyToOne`.
    - For these annotations, you can specify attributes like CascadeType and FetchType
    - CascadeType is used to specify the cascading on the database when removing/updating items
        - and this is also we maintain **referential integrity** in Hibernate
    - FetchType determines if the related objects are called from the database immediately (EAGER) or if called, waits until they are needed (LAZY)
        - EAGER is more memory intensive, but less error prone
- **@JoinColumn** is used to specify the column at which establishes the relationship on. This is usually the foreign key pointing to the primary key. The name attribute specify should match the name of the field in the referred to class.
- **@JoinTable** is used for situations of @ManyToMany as we are determining which tables to link in order to make the relationship and this is also how join tables in Spring Data

### What are some Spring Data Annotations (Above were Annotations standard in JPA)?
- Spring Data focuses on abstracting away the code required for data storage, allowing for developers to focus more on the business logic.
- Spring Data annotations allows use to configure how queries execute and usually these are used mostly in DAO and model classes. 
- All of following annotations are **case sensitive**:
- **@Transactional** is used to configure how database transactions behave
- **@NoRepositoryBean** used to create an interface taht provides common methods for child repositories 
- **@param** allows for parameters to be passed to queries that are defined with `@query`
- **@transient** marks a field as transient, **to be ignored** by the data store ending during reads/writes
- **@CreatedBy/@LastModifiedBy** are auditing annotations that will automatically be filled with the current author
- **@CreatedDate/@LastModifiedDate** are auditing annotations that will automatically be filled with the current date

### What are transactions?
- A **transaction** is a group of one or more SQL statements typically DML statements that execute together as a unit of work following the **ACID properties**
- Transactions are important for **data integrity** or when you just need a group of SQL statements to succeed together or fail together.

### What are the ACID properties?
- The ACID properties are used to describe the concept of transactions.
- **Atomicity** defines that a transaction should be treated as a single unit of operation, which implies that either the sequence of SQL statements is successful together or not and get rollbacked.
    - Atomic means also that we can't break a transaction down any further as we cannot just have a piece of a transaction succeed alone, a transaction should succeed as a whole.
- **Consistency** represents the consistency of the referential integrity of the database and also that transactions cannot ignore rules like constraints 
- **Isolation**  refers to that transactions should be isolated in terms that while we can have many statements executing the on the same data at the same time, they should be isolated to avoid inconsistency of the database state. **This can be done with transactions being ran independently without interference and that a particular transaction's changes will not be visible to any other transaction unless that change is commited to the main memory**.
- **Durability** refers to the fact that transactions must be durable in that when a transaction successfully completes, it changes are to the database (basically the data) is saved forever/persists after that transaction. 
    - This also implies that the changes made a in a transaction can be losable in the sense of a rollback if the transaction fails.

### What is RestTemplate?
- **RestTemplate** can be used in Spring MVC to receive JSON information from an external Restful API (a different server). This allows our Java server to send requests to other servers.
    - We just instantiate a RequestTemplate object to use its methods
- For the methods, requests are are just `___ForObject(url, body(requested/sent))`
    - `getForObject()`
    - `postForObject()`
    - Two parameters: URL where request is going to and the type of object being requested/sent

### What is the Bean lifecycle?
- Beans are managed by Spring IoC containers which is either the BeanFactory or the ApplicationContext. This management invovles instantiation of the bean, configuration and destruction/removal fo the bean. 
- The lifecycle can be visualized as 12 different steps and that not all steps apply to every bean in terms how a bean is setup. 
    - 0 - Bean is called for or instantiated
    - 1 - The Bean's name is set using the setBeanName() method that is implemented and inherited from the BeanNameAware interface.
    - 2 - The bean's is made aware of the class loader for that bean using the setBeanClassLoader() method. The class loader is the object responsible for loading class
        - and similarly this method comes from the BeanClassLoaderAware interface
    - 3 - The bean is made aware of the Bean Factory that owns it and manages it, through the setBeanFactory() method. This like the last 2 steps comes from an interface called the BeanFactoryAware interface.
    - Step 4 - 8 are not necessary to know, but are used when beans are used in application context
    - 4 - *ResourceLoaderAware's setResourceLoader (only applicable when running in an application context)*
    - 5 - *ApplicationEventPublisherAware's setApplicationEventPublisher (only applicable when running in an application context)*
    - 6 - *MessageSourceAware's setMessageSource (only applicable when running in an application context)*
    - 7 - *ApplicationContextAware's setApplicationContext (only applicable when running in an application context)*
    - 8 - *ServletContextAware's setServletContext (only applicable when running in a web application context)*
    - Step 9 - 12 resumes what any bean would have as part of its lifecycle and follows after a bean is made aware of the related interfaces
    - 9 - After the bean has been populated with property values, a BeanPostProcessor's postProcessBeforeInitialization() method(s) are called before a bean initialization callback methods are invoked.
        - what this means really refers to is that a BeanPostProcessor is a special bean/object that applies its own post processor to customly modify new bean instances.
        - so in this case if a post processor is needed to be applied before bean initialization then the BeanPostProcessor should implement the `postProcessBeforeInitialization()` method.
    - 10 - InitializingBean's afterPropertiesSet() is ran by the BeanFactory after all a bean properties have been set and this is to allow the bean instance to **perform validation of its overall configuration and final initialization.** 
        - This is an example of an initialization callback method referred to in step 9
    - 11 - Any custom initialization method is defined with @PostInit and used to initialized the bean.
    - 12 BeanPostProcessor's postProcessAfterInitialization() method is called to customly modify new bean instances after the initializaiton callbacks for a bean. This post processor can be applied to either or both the Factory bean and bean/object created by the FactoryBean (which is a bean that acts a factory for its type of beans)
    - Teardown: What happens to a bean near/at the end of its lifecycle
    - 1 - the DisposableBean's interface destroy() is utilized
    - 2 - Any custom destroy method defined with @PreDestroy
    - 3 - Garbage collection eventually


### What is AOP (Aspect Oriented Programming)?
- **Aspect Oriented Programming (AOP)** is a way of thinking about structuring your program which can be used complementary to Object Oriented Programming. With OOP the key component are classes which are use to represent concrete ideas with states and behaviors and be able to create them as objects. With AOP, the key components are **aspects** which modularizes particular transactional concerns which can be present across multiple classes, these concerns are called **cross cutting concerns**.

### What is concerning or the issue with cross cutting concerns?
- **Cross cutting concerns** are defined in that they are actions that can take place across mulitple classes, regardless of the class's function or structure. This would be considered code redundancy in traditional OOP, as the same code is being called multiple times throughout an application to perform the actions. 
- **AOP** works to eliminate this redundancy by transferring responsibility of these issues to **aspects**

### What are examples of cross cutting concerns?
- Examples of cross cutting concerns include things like error handling and logging system messages. And these are usually sometimes consider generic functionality that is not relative or specific to the business logic of the classes they are implemented in.

### What is Spring AOP?
- Spring AOP is a Spring module that supports the implementation of apsect oriented programming where an **aspect** is a key unit in the modularity of a program and cross-cutting concerns are things that don't necessarily fit the OOP paradigm. 
- While AOP is not crucial or depended on by Spring IoC containers and applications in general, the Spring AOP framework provides a middleware solution for cross cutting concerns.
- **Spring AOP allows us to create Aspect classes to manage cross cutting concerns, basically all the functionality like for example logging is now done in one class that is an aspect called LoggingAspect.**
- **Aspects** are defined as the modularization of **cross-cutting concerns** which is logic or code that "cuts" across multiple types/objects/classess.
- An example of a crosscutting concern is logging where we may log different parts of the program, but in general logging isn't really tied with what it logs so having all this logging logic cutting into many different parts is not logical. 
    - With that we can put all are logging logic in one classed called an **aspect**

### What are aspects?
- **Aspects** are defined as modularizing a concern that cuts across multiple classes.
    - Modularizing in Spring AOP, means that aspects are implemented using regular classes or regular classes are annotated with the `@Aspect` annotation.
    - Modularizing in general is to just divide something like a program into sub-programs that most of the time focuses on a single aspect/concept. Ex: classes in OOP, aspect in AOP.  

### What are other AOP terms?
- **Advice** is the action you are taking at a particular **join point**, what code you're injecting to address the **cross cutting concern**. 
- **JoinPoint** is a point during the execution of a program such as a method execution or handling of an exception. In Spring AOP, join point is always represents a method execution.
    - And these points are potential places where an **advice** may be injected to.
- **PointCut** is the specific JoinPoint that is determined after matching a join point or multiple join points to a criteria/point cut expression to determine your point cut. And PointCuts are the specific joinpoint that you **will** inject your **advice** into

### What is AspectJ and how does it tie in with Spring AOP?
- AspectJ is a fully AOP framework that Spring AOP uses under the hood. However it requires extensive XML configuration to function, which Spring AOP abstracts away from us.
- In essence, Spring AOP adopts AspectJ annotations, but has replaced some functionality and has done away with the XML configuration.
    - This also means that Spring AOP requires the AspectJ dependency to work to an extent.


### What annotations are used in AOP/AspectJ?
- **@Aspect** is used annotate classes in which we want to be considered **aspects** to address a cross cutting concern (CCC). And it has to be a Spring Bean to work with Spring AOP so we would also used `@Component` 
- There are different types of advice annotations to denote when an **advice** should be executed.
    - **@Before** is used to have an **advice** execute before the joinpoint/pointcut
    - **After** is used to have an **advice** execute after the joinpoint/pointcut. This annotation can be more specific in two ways.
        - **@AfterReturning** lets the advice execute after the JoinPoint/PointCut returns successfully
        - **@AfterThrowing** lets the advice execute after the JoinPoint/PointCut throws an error or exception
    - **@Around** used to allow for advice to be injected before/during/after the JoinPoint/PointCut. This can stop the execution of your pointcut. However, it's more complicated and not preferred if you can achieved the same functionality with `@Before` or `@After`

### What are join points and how are they implemented/used in Spring AOP?
- Join points are a **specific part of the application in which an advice can be injected to**. Join points are usually methods.
- JoinPoint is an interface that can be passed to any aspect methods (advices) and this is the access point in the target object where the advice is injected into. 
    - **Overall this allows for Spring AOP to access the JoinPoint's method signature, arguments and etc and modify them**. This is also how we indicate to Spring AOP which JoinPoint we want to inject advice to. 
        - We can use the `jp.getSignature()` method to get the method/joinpoint being called and we can use `jp.getTarget()` to get the actual object we are using.
- **ProceedingJoinPoint** is a sub-interface of JoinPoint which is used with the @Around advice only
    - It's used to achieve the ability to pause/stop a method from running


### What are the different types of PointCut expressions?
- All PointCut expressions are essentially JoinPoints that an advice will utilized to take some action addressing CCC in the method that has the concern.
- To be further clear, pointcut expressions are used to determine which joinpoints will have advice taken in or injected into.
- **Execution**, which is the most common type of point cut expression, refers to the moment a method is executed. We use the method's signature to along with `execution` to be the pointcut expression utilized
- **Within** refers to JoinPoint (basically methods) within a certain package(s)
    - This means the advice will execute for all methods in a class that is within the specified package.
    - We use `within(packages)` as the pointcut expression
- **Args**, is technically an `execution` pointcut expression, but here we can specify the types of the arguments being utilized in a method. As in this pointcut expression will only match methods/JoinPoints where the method signature matches in having the parameters types and count specified in the expression
    - `execution(doSomething(Long))` refers to a doSomething() method that exactly has one parameter that is of type Long.
- **This**, limits the match JP to where bean reference is an instance of a given type (specific class)
- **Target**, limits the match JP to where the target object is an instance of a certain type (this is usually an interface type)
- Pointcut expressions can be combined with logical operators like && and || to further narrow down or increase the criteria needed to match a JP that an advice will be injected into.



