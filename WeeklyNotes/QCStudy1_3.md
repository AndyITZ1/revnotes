# QC Study Guide Week 1-3

## Week 3

### What is a lambda (expression)?
- A lambda expression **creates an unnamed/anonymous method that is of single-use and can be passed as parameters** inside another method. Lambda unlike regular methods **do not need a name and has different syntax** that slightly varies with the number of arguments and number of lines in the body, but all lambda expressions **require the lambda operator** which is a dash with a greater than symbol. `->`

```Java
// Lambda Syntax
/*
    Minor syntactic sugar in lambda expressions are that when there is only one parameter, the list of parameters doesn't need to be in parentheses.
    Also if there is only one line for the body then curly brackets aren't necessary.
*/

// No arguments and one line body
() -> System.out.println("Hello") // prints out Hello


// One argument and one line body
int a -> a * a // takes an integer parameter and returns an int

// Multiple arguments and multiple line body
(String s1, String s2) -> {
    System.out.println(s1);
    System.out.println(s2);
}
```

- Functionalities Lambdas provide:
    - Enable to treat functions/methods as a method argument, or code as data
    - A function that can be created without belonging to any class
    - A lambda expression can be passed around as an object that can be executed on demand.

### What are streams?
- Streams are a sequence of objects/elements that are taken from a source and can be processed via different methods to produce some result that can be used or stored. The modified data in and from a stream doesn't affect the original data in the source which is processed in the stream.

### What are two different types of operations performed on the data in a stream?
- Operations executed on a stream are **Intermediate Operations** and **Terminal Operations**. Intermediate operations, while modifying data in a stream does not return a true result but rather a modified stream. Terminal operations complete the modification of a stream and may or may not return a primitive value or object. Another thing about streams is that multiple intermediate operations can be chained and performed on the same stream, but only one terminal operation can be performed and only at the end of the chain.

### What are examples of intermediate operations and their use?
- Intermediate operations include operations like map(), filter(), and sorted(). 
    - `map()` allows us to modify each element in the stream with a given function and upon the operation being finished the stream now contains modified elements. 
    - `filter()` allows us to provide a criteria in elements of the stream upon passing the criteria are maintained in the resulting stream.
    - `sorted()` allows us to sort the elements of a stream in their natural order which can be numerically, alphabetically or both. 

### What are examples of terminal operations and their use?
- Terminal operations include operations like `collect()`, `forEach()`, and `reduce()`.
    - `collect()` returns the stream as a specified object
    - `forEach()` performs a given function to each element in the stream and terminates the stream (unlike with `map()`)
    - `reduce()` returns a single value after reducing the elements via some binary operator

### What are queues?
- Queues are a data structure that stores a collection of elements. Queues are designed to follow a principle of the first object add in a queue is also the first object to be removed when removing elements from the queue.
- Due to this principle queues are inherently ordered and can only be truly traversed by removing one element at a time from one end. 
- Queues in Java can vary as some may not allowed null elements, but some do. 

### What methods does a queue provide?
- In Java, we can use methods inherited by the Queue from the Collection interface such as `add()` and `remove()` otherwise queue specific methods include `offer()`,`poll()`, and `peek()`

### What classes implement the Queue Interface?
- In Java, the Queue Interface is implemented by multiple classes but most common classes used are the LinkedList and PriorityQueue classes.
- Unlike normal queues, PriorityQueues order their elements based on their natural ordering or given some comparator object.

### What are Maps?
- Maps are not a part of the Collection API but are considered a collection as they store key/value pairs. So rather than most collections storing just single elements. A key-value pair in a Map is basically 1 object associated with another object. 

### What methods can we use with Maps?
- Maps have methods like `containsKey()` and `containsValue()` to allow us to find a certain object if it has been stored in a pair(s) in a map. To insert a new key/value pair into a map, the `put()` is used. For removing a pair, the `remove()` method is used with a given key. For a list of all the keys in the map use the `keySet()` method. To retrieve a value for a key, the `get()` method can be used.

### What are implementations of the Map Interface?
- HashMap is one implementation of a map in Java, they are not ordered can have at max one null key and any amount of null values.
- HashTables are another implementation that are also not ordered, however they cannot have any null keys or null values.

### What are Comparables and Comparators? Similarities? Differences?
- Both `Comparable` and `Comparator`are Interfaces that have a method which allows for implementing classes to compare two objects. This comparison can be helpful when sorting objects as they may not have an obvious way be naturally ordered unlike primitive values. 
- Comparable Interface allows implementing classes to implement the compareTo() method which compares the current instance of a class with another instance of the same class. 
- This provides a way of sorting elements in a collection based on a single element otherwise known as **single ordering sequence**. 
- The Comparator Interface provides a method, but rather than being implemented by the class of the objects being compared and external class implements the Comparator Interface and one can use the `compare()` method once implemented by this external class.
- Unlike the `compareTo()` method, rather than comparing the object calling it with another object. The `compare()` method passes in both objects of the same class to be compared. This also means that the object calling the compare() method is not necessarily of the same class of the objects it is compariing.
- Both the `compareTo()` (Comparable) and `compare()` methods have similar implementations in that the value they return is an integer, where `0` represents equal objects, positive values meaning an object is greater than another object and negative integers meaning an object is lesser than another object.
- Another feature of using comparators is that comparators can be implemented in different ways to sort differently based on attributes inside a class.  
- With using the comparable interface, we can only implement it using the class with the instances that are to be compared. And the one method implementation is the only implementation usable unless it is changed. 

---

### What is REST?
- REST (Representational State Transfer) is an architectural style/convention for web services that represent a server (backend) as a collection of resources that can be accessed by specific endpoints (frontend). This can be seen over the Internet as a client-server architecture where clients can use HTTP Requests to request fetching of resources from the server and the server responses with HTTP Responses with the data fetched. 

### What are endpoints?
- Endpoints are usually deterimined by URI or URL which identify a single or multiple resources. Endpoints are simply access points to the resources.

### What are the 6 guiding principles/constraints of a RESTful API?
- There is the client-server architecture which separates the user interfaces from data storage, allowing for portability across multiple platforms and abstraction in general
- Layered architecture, in which the server should designed layered so that the client is not aware of how the server is designed beyond the layer that interacts directly with requests
- Stateless is when each request from a client to the server must contain all relevant information for the server to complete the request. However the server should not store any context information about the client. Meaning that requests have no knowledge of past and future requests.
- Cacheable, responses should be saveable for the client, as responses are resources at particular endpoints and so to reduce redundant requests to the server the data should be able to be saved by the client.
- Uniform Interface, the system architecture should be designed efficiently in a way that makes finding resources highly logical. This means for endpoints the URIs should proceed from being general to the collective to the specific resources.
- Code on demand (Optional), allows for client functionality to be expanded to downloading applets or scripts to execute code to use with the resources. This is not well defined or agreed upon by the software development community. 

### What are different HTTP verbs/methods used in REST?
- GET - used to request information
- POST - used to create a new object or add entirely new information which is contained in the body.
- PUT - used to update a complete resource.
- PATCH - used to update a specific part of a resource
- DELETE - used to remove resources
- HEAD - returns the header of the request
- TRACE - Traces the path a request takes on its way to the server.

### What exactly is a REST resource?
- A REST resource is any information or data that can be retrieved, stored or manipulated by a user through HTTP Requests sent to certain endpoints.
- A resource is usually identified by the URI path given to label the resource and we can expose REST API endpoints by creating handlers for endpoints to allow for fetching of these resources by traversing through controllers, dao, all layers up to the server.

### What is a web service?
- A **web service** is a software system designed to support interchangeable machine-to-machine interaction over a network. A web service is a collection of open protocols and standards used for various programming languages and running on various platforms. 
- We use web services to let our frontend and back end communicate in order to exchange data over a web network using a universal data transfer format.
- When creating web services there are two types of web services REST and SOAP. REST is generally preferred due to using less bandwidth, being flexible for internet usage and unlike SOAP it allows for more formats beyond XML like JSON and YAML formats for responses provided to the client requests. 

### What is a session?
- A session stores client request history/information and it is stateful as when receiving client requests and sending responses to the client, the identity of the user on the client side is revealed unlike HTTP Requests which do not keep track of previous requests. 
- Session stores user information on the server as key/value pairs and in doing this violates the REST principle of being stateless, where the server should not store any information about the client sending a request.

### What is a cookie?
- A cookie is a small piece of data that is sent from the server and stored on the end. A cookie is also what is used by sessions to identify users sending requests. 

---

### What is logging?
- Logging is the process of recording events that occur during a program's or software's execution. By logging information, users can track or monitor an application's performance, use logs to debug, and observe potential security risks.

### What is Logback?
- Logback is reliable, fast, flexible logging framework for Java supported by Apache. Logback is commonly used to record application events, log debugging information for developers and write exception events to files. Logback also allows users to determine which messages will be recorded in the log files using various logging levels for different messages. 

### What are logging levels?
- Logging levels are classifications used on logging messages to determine their level of severity and importance. In Logback there are 7 different levels, each define what kind of message can be logged at that level. With that a logger, can be assigned a threshold level, which determined or limits what log messages below a certain logging level are ignored and basically not logged into the files. Logback like other Maven dependencies can be found in Maven repositories and to use it we need to get the dependency tag lines from the repository to put in the pom.xml file of the project. 

### What is Test Driven Development (TDD)?
- Test Driven Development is the practice of writing unit tests first prior to writing the source code for the actual application. Usually the process involves writing all the unit tests that each test a functionality or feature that will be implemented into the application. Upon all tests are written all should fail when run as we have yet to implement the features that are being tested for. Then we implement each feature or functionality and run the tests to see if the feature meets/passes the test written for it and that if it doesn't it should be modified and refactored until the application code passes the test. 
- The benefits of following this process is to ensure that we have valid unit tests for testing a wide range of features in an application and that if the code does need refactoring despite passing the test, we can ensure that if the refactor code fails then most likely the new code has an error and the bug is not within the old code.

### What is unit testing?
- Unit testing is the testing of smalllest testable parts of an application in general. In Java, this can be the methods utilized to perform an application's functionality. The premise for testing such small parts is that we can ensure that methods are running as expected. Generally, tests when written can be positive or negative in that they test for an expected result that is a valid response for a valid input or invalid input.

### What is JUnit?
- JUnit is a testing framework that provides annotations and methods for creating unit tests in Java. Annotations in JUnit include ones like BeforeClass and AfterClass which can specify a method to run before or after any tests for a class to run. Overall annotations kind of specify what to do with a method during the execution of testing in JUnit. JUnit has methods like assertEquals() which can be used in a testing method to assert that a testing method or method in general output is valid as expected. 

### What is Mockito?
- Mockito is a testing framework thath allows us to create "fake" objects or mock objects that we can use in place of real objects for unit testing. The benefit of using mock objects is that the process of mocking creates a "dummy object" that simulates the behaviors of a real object. By doing this developers do not have to create objects to test certain methods and objects. 

### What functionalities can we perform with Mockito objects?
- Beyond using fake objects to simulate real object behaviors, developers can control what methods return manually which skips the logic of the object is being mocked. 

### What are methods provided by Mockito?
- We can use `mock()` which creates a mock instance of an object, which we can use to execute code with, but a thing to note is that all the methods of the real object are not implemented in a mock object which means that there will be no effects when calling the method on the mock object. 
- We have `spy()` which requires a real object be created and the spy() creates a spy  for that real object. This spy is of the same typing as the real object and will be interacted with when tested. So when we call methods on the spy object it will observe how the functions perform and the effects of these methods are still being done to the real object that is spied on.  
- `verify()` is used to verify that a certain function/method runs as once as intended and makes a test fail if the method in question was not invoked.
- `.when().thenReturn()` are two methods used together to allow for **stubbing** which we means we listen for a method to get called and upon that method be invoked we can return a value that determines if a method was called and is working properly.

---

### What are data structures?
- A data structure is mechanism that stores and organizes data that can be processed/manipulated or retrieved as well. 

### What are algorithms?
- An algorithm is sequence of well-defined instructions used to solve a class of problems or to perform a common task

### What is an array?
- An array is a data structure that stores a collection elements sequentially. In Java, it stores objects of the same data type. All arrays have fixed length and this is determined during the declaration of the array. The length of an array is a property that can be called via `length` to get the length of an array. 
- Each element of an array has a specific index starting from 0.
- Other operations you can do to array include changing the values of an element and iterating through it.

### What is an ArrayList?
- An ArrayList is a data structure that is similar to an Array, but with differences. Similar to Arrays, it can store a collection of objects of the same data type. One big difference though is that ArrayLists are dynamically sized meaning that their size changes as the number of elements inside of it changed so it will expand or shrink.
- ArrayLists are an implementation of the List Interface which is a part of the Collection API which refers to various collection classes and interfaces that implement the Collection Interface. 

### What is a LinkedList?
- A LinkedList is another implementation of the List Interface just like ArrayLists.
- A linked list stores a collection of objects, are also dynamically sized as well but unlike ArrayLists, data is inserted through the front end and doesn't have constant time access as an Array or ArrayList when retrieving a value of an element. To get an element inside a linked list, you have to traverse it from the head or front end of the list till you reach the node with the element you want.
- Beside implementing the List Interface, LinkedLists also implement the Queue Interface so it also gains functionalities of a Queue and not just as a list 
- Linked lists are made of Nodes which are objects that hold pieces of data usually primtives or other objects. And each node points to the next node in the list. 
    - can only traverse from beginning to end

### What are the two types of linked lists?
- There are singly linked lists and doubly linked lists. Singly linked lists are the default representation of what one may think of when hearing linked list as it showcases nodes that point to the next node in the list. Doubly linked lists add an additional pointer to what is included in a singly linked list. This extra pointer goes from a Node to the Node previous to it. 
- The benefit of a doubly linked list is that it allows you to traverse both directions in a linked list and not just from beginning to end like with a singly linked list. 

### What are searching algorithms?
- A searching algorithm is an algorithm that allows for the retrieval of an element from a collection of elements or just in check if it exists in the collection
- There are two main categories of search algorithms **sequential search** which the data structure is traversed sequentially and every element is checked. An example algorithm is a linear search, which starts from the beginning of a collection and goes through all the elements and only stops when it finds the matching element or at the end of the list
- **Interval Search** is another algorithm which is specifically designed for sorted data structures and are considered much more efficient compared to sequential search. The premise of an interval search is to repeatedly target the center of collection and try to match it and if no match, the collection of element is narrow down one half to be searched again. This is otherwise known as the divide and conquer approach. An example of this is binary search which compares the middle value with the search value and if not match and search number is bigger than the right half is searched otherwise if the number is smaller then the left half is search and this process is repeated on the next half searched. 

### What are sorting algorithms?
- Sorting algorithms are algorithms that involve sorting some of collection of data like Lists so that the elements are ordered based on their natural ordering which could be alphabetical, numerical or both. Note that comparison operator used to compare is not bound to just the natural ordering, it can also order some other way that may be more specific to an object's data or field.

### What are some examples of sorthing algorithms?
- There are merge sort, quick sort, insertion sort, selection sort, and bubble sort and each have different time complexities when executed

### What is recursion?
- Recursion is a technique where a method call itself during execution. The reason for recursion is to use it for breaking down hard problems to get a base case in which is a smaller version of the original problem that can't be broken down any further and that can be solved. 

### What is time complexity?
- Time Complexity is the amount of time it takes an algorithm to run as a function of the number of inputs provided
- when talking about complexities this isn't the exact time an algorithm executes but rather this is expressed in Big O Notation meaning the value is rather an estimate that has bounds for that algorithm. 

### What is Big O Notation?
- Big O Notation helps track the relationships between the growth of the functions and amount of inputs. 

### What are the diffferent complexities?
- There is O(1) which means constant time which is not dependent of input size
- O(n) which is linear time meaning that time increases with the input size in a linear manner
- O(log n) or logarithmic time which describes the number of operations done decreases as input size increases.
- O(n ^ 2) describes the relationship of input and execution time as quadratic time where the relation grows quadratically

### What is space complexity?
- Similar to time complexity, space complexity is a measure of the amount of space used by an algorithm and this is estimated with Big O Notation as well. The memory scales with the number of inputs.

---

## Week 2

### What is a database?
- A database is an application that we to store, view, and manipulate long term data. 
    - Long term data could be user information, product prices, forum posts.
- Why we might use them?:
    - **Necessary for any organization and storing/accessing large amounts of data that robust applications might accumulate**
    - **Web pages (front-end) and servers (back-end) aren't really fit to store data long term**

### What is SQL?
- SQL or otherwise known as Structured Query Language, is a query langugage which we used to **communicate** with databases by **storing, viewing, and manipulating the data**. There two types of databases: NoSQL and Relational databases. SQL is used exclusively in relational databases as it was designed to create relational databases and manipulate their data. 

### What is a relational database?
- A relational database is a type of database that stores a collection of data that can have predefined relationships between pieces of data. 

### What is a relational database managment system? (RDBMS)
-  A relational database management system (RDBMS) is a software that allows you to perform CRUD operations and administer a **relational database**.

### What are sublanguages of SQL?
- In SQL, there are three main sublanguages that are used to categorized the commands used. There are DML or data manipulation language, DDL or data definition language, and DCL data control language. Respectively each has commands that grouped by their functionality. In DML, the commands are generally used to change/manipulate/use the data in tables. 
In DDL,  or data definition language the the commands are used to build the structure or schema of the database and how the objects containing data will be created and stored.
In DCL, the commands are used to manage access to the database and permissions to structures in the database. 

```SQL
CREATE TABLE tableName (
    column1 TEXT Primary Key NOT NULL,
    column2 int
);

ALTER TABLE tableName 
ADD columnName int;

ALTER TABLE tableName
ALTER COLUMN columnName TEXT;

ALTER TABLE table_name
ADD CONSTRAINT constraintName UNIQUE(column1, column2...);

DROP TABLE tableName;

TRUNCATE TABLE tableName;
```

### What is a schema?
- A schema is a set of related tables grouped together under a single name.

### What is referential integrity?
- Referential integrity refers to the consistency, accuracy, and validity of data in a database. More importantly is describes the relationship constraint of ensuring that a foreign key in one table has a matching primary key in another table or be null to validfy the data in records between records. There are two rules that are followed when using referential integrity, one is to have a foreign key in Table A can be only a value contained in an appropriate column in Table B, and this column is usually the primary key of table B. The second rule is that you can't always delete or update the values in that column in table B, since the foreign key in table A are dependent on it. 
- One way we can update or delete a value is dependent on by another is that we can use the CASCADE keyword which allows us to perform the update or deleteing processed on not just the original value but also on all referencing records to that value. 

### What is a join?
- A join is an operation used in query to combine rows from two tables, based on a related column between the tables. 

### What are different type of joins?
- Inner joins are used to combine and return records that have a matching value in both tables 
- Left outer joins return the rows all in the left table and any matching rows in the right table.
- Right outer joins returns the rows all in the right table and matching rows in the left tables
- Full outer joins which return alls rows from both tables regardless if they are matching or not but matching rows are combined. 

```SQL
Select * from tableA 
inner join tableB 
on tableA.fk = tableB.pk;
```

### What are set operations?
- Set operations are used to combine two queries into one resultset. The difference between joins and set operations is that joins combine two tables and not queries. 
- There are 4 set operations, union, union all, intersect adn except.
- Union is used to return all distinct rows from both queries (which means no duplicate rows will exist)
- Union all returns all rows from both queries and this allows for duplicate rows to show 
- Intersect returns all unique rows that are found in both queries
- Except returns all unique rows the first query that doesn't appear in the second query

```SQL
select * from tableA
Union 
select * from tableB;
```

### What are scalar functions?
- Scalar functions take in a single value and return a single value based on some calculation. Functions that are scalar include upper, round ,lower and now which is for returning the current time. 

```SQL
SELECT now();
```

### What are aggregate functions?
- Aggregate functions take in a group of values and return a single value calculated from the set. Functions that are aggregate include avg, min, max, sum, and count

```SQL
Select count(columnA) From tableB;
```

### How do we group rows based on values in the columns?
- We can use the GROUP BY method to put together rows that have equivalent values for some column.  To further restrict the rows shown in the result we can use the Having statement and a condition for Having statement. Both group by and having are typically used following aggregate functions. 

```SQL
Select * from tableA
GROUP BY column1
HAVING column1 > someValue;
```

### What is a subquery?
- A subquery is a SQL query nested within a larger query. We can think of subqueries being used to query to filter out a subset of the all the available data or resultset. 

### What is a view?
- A view is database object containing a stored query that can return the resultset of a SQL query. There are two types of views the regular view stores the query and under the hood executes that same query at runtime so it will always reflect any updated values in a result set. The second type of views are materialized views are save in memory and the result set they hold is static in that the data stored is the same when it was originally created. Materialized views will immediately display the data and under the hood won't execute the query again as it already stores the resultset.

### What is cardinality or multiplicity?
- Multiciplity refers to the different ways we can build a relationship between tables in your database. We can have One to One , One to Many, and Many to Many relationships. 
One to One describes that one row in table A is directly related and only associated to one row in table B.
One to Many describes that one row in table A can associate with multiple rows in table B
Many to Many describes that many rows in table A can have relations with many rows in table B. This can be seen as multiple students taking classes and classes can have many students.

### What is normalization?
- Normalization is a strict process of multiple levels that focuses on reducing data redundancy and improving data integrity"

### What are the different levels of normalization?
- There is 0NF which no restrictions are applied and tables are filled with data. 
- 1NF - which requires all tables to have a primary key and that columns must be atomic where atomic means thats a column can only hold one value
- 2NF - requires that we be in 1NF and that we remove partial dependencies meaning any piece of data dependent on a part of the primary key must be removed. Partial dependencies do not occur if the primary key is a single column
- 3NF - requires that we be in 2NF and that we remove transitive dependencies which is when a column is reliant on any other column. so any columns dependent on another must be removed.

