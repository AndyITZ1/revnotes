# Exceptions
## What are Exceptions?
- **Exceptions** are events that occur during the execution of programs that disrupt the normal flow of instructions (ex: divide by zero, array access out of bound)
- **Exceptions** in Java are objects that wraps around an error event that occurred within a method
- **Exceptions** contain various info:
    - information about the error including its type
    - The state of the program when the error occurred
    - optionally, other custom information
- There three different categories of **exceptions**:
    - Checked Exceptions
    - Unchecked Exceptions
    - Errors

## Checked Exceptions
- Are exceptions that:
    - The **compiler** enforces that you handle them explicitly
    - Any methods that generate **them** must declare that they **throw** them
    - Methods that utilized other methods that **throw** checked exceptions must either handle them or propagate it by **throwing** as well
- **Checked exceptions** are called compile-time exceptions as they are checked at compile-time 

## Example of Checked Exceptiosn
```Java
import java.io.File;
import java.io.FileReader;

public class FileReadingDemo {
    public static void main(String[] args) {
        File file = new File("file.txt"); // 
    }
}
```
- In this example, if the file via the File constructor is not found/doesn't exist, an exception is thrown (FileNotFoundException)
- Also this program at compile-time will request that you **handle** the exception before running the program meaning you have to catch or throw the exception (in this case the main() throw is one way to handle)
```Java
public static void main(String[] args) throws IOException {
    // File code from above
}
```
## Unchecked Exceptions
- **Errors** and **RuntimeExceptions** are unchecked
    - unchecked: compiler **doesn't** enforce (check) that you handle them explicitly
    - This means that methods **don't have** to handle (declare to throw) the error when writing the **method signature**
- It can also be assumed that the application **can't do*** anything to recover from these exceptions (at runtime)
```Java
public static void main(String[] args) {
    int num[] = {1, 2, 3, 4};
    System.out.println(num[5]);
}
```
- In this example, creating an array and accessing doesn't need to checked/handled for exceptions as you can go about accessing the array.
- However if you try to access an index that doesn't exist in the array then it will trigger an **ArrayIndexOutOfBoundsException**.
- Again this happens at runtime as the compiler can't predict/"run" your code to check it beforehand

## Errors
- These aren't **exceptions** but rather they are problems that occur beyond the control of the user/programmer.
- **Errors** are typically ignored in your code because you can rarely do anything about an error.
- Example: If a stack overflow occurs, an error will arise.
    - Stack overflow refers to when a value like an integer can't represent/store a huge value so it will cycle back to a number it can represent with its capacity. 
    - The error here is that what the user/program will see is that the integer is definitely the wrong value and this is an error that is a limitation of the system architecture. 
    - Again these errors can't be checked by the compiler or handled since no exception will be raised to warn of such scenario. This is what differs them from runtime exceptions that do trigger and also aren't checked/handled.
- They (errors) are also ignored at compilation time.

## Exception Hierarchy in Java
- All **exception classes** are subtypes of the **java.lang.Exception** class. 
- The **Exception** class is a subclass of the **Throwable** class.
- **Error** class is also another subclass of the **Throwable** class.
- java.lang -> Object -> Throwable
- Throwable -> Exception 
- Throwable -> Error
- Exception -> Runtime Exceptions
- Exception -> Other Exceptions

## Handling Exceptions 
- There are 5 keywords used in handling/dealing with exceptions:
    - **try**
    - **catch**
    - **throw**
    - **throws**
    - **finally**

## Try-Catch-Finally 
- For programmer to catch and handle exceptions often you can use a **try/catch** block to surround exception-raising code. 
```Java
try {
    // Possible exception-inducing code
}
catch (ExceptionName e) {
    // How to handle an exception caught code
}
finally {
    // block of code that will execute after the "try/ try-catch block ends
}
```
- Here the try block is where you put your code normally, upon an exception occurring the, the program transitions to the catch block.
- In the catch block, a programmer can decide what to do when getting the exception. Note that you have to provide a type of Exception that is being caught as a parameter for the catch block to even run. If the exception doesn't match the parameter type that means it won't be caught unless a catch block is written for its type of exception
- In short:
    - Try block is where all code including ones with possible **exceptions** are placed
    - There can be more than one **catch block** to handle specific types of those **exceptions** that occurr from the **try block**
    - The **finally block** is rather optional in that it runs code after the **try/try-catch block** scenario has finish running code wise. 
        - Here often the code put in **finally blocks** are code to clean up (ex: closing files, closing connections) 
- The main difference between code that follows the try block scenario vs the code inside a **finally block** is that the **finally block** executes regardless if an **exception** is caught or not. 
    - If an exception was not caught by a **catch block** then like any other program, the program terminates abnormally and displays the exception to the user.
    - With that code following the **try block** can't be run as the program is terminated before reaching those lines as the exception was not caught. 
    - However within a **finally block**, code within that block will always execute after the try block and will still run before the program terminates if an exception wasn't caught


## Throw/Throws Keyword
- While both keywords are similar, their usage is quite nuanced in the differences. 
- **throw** is the keyword used to invoke **exceptions**
    - what this means is that if a programmer wanted to raise an exception upon some event/part of code that occur they could do so by using the **throw** keyword 
- **throw** is often used to throw custom exceptions (user-created)
- Any exception thrown by **throw** should be handled accordingly like with a catch block otherwise it will halt the program.
- **throws** keyword is specific to **method signatures**, in that it implies/states that a method will throw an exception and that the person calling this method should handle it (as the method itself will not handle it)
- **throws** differs from **throw** in that the method is doing the throwing and that its often used to **defer** the handling of an exception to the caller of the method instead
- To summarize handling exceptions, one can choose **to catch** the exception or **defer** the exception.
- **throws** isn't used by the programmer, but rather the programmer puts in on a method, where the method uses it to forego the process of handling an exception. 
- **throws** isn't required of all methods, it should only be used when a method has the possibility of having an exception due to it calling a method that could have an exception, or itself has exception-inducing code or that the programmer has decided to **throw** an exception in its code"
- **throw** on the other hand is to be used to be able designate certain scenario of codes where you might want to trigger an Exception 

```Java
class ThrowExample {
    static void fun() throws IllegalAccessException {
        System.out.println("I'm having fun!");
        throw new IllegalAccessException("damn");
    }
    public static void main (String[] args) {
        try {
            fun();
        }
        catch(IllegalAccessException e) {
            System.out.println("caught the illegal access exception!");
        }
    }
}
```
- **throws** other points:
    - it's only required with **checked exceptions** and meaningless for **unchecked exceptions** as we don't know when such an exception may occur.
    - by **deferring** the exception(s), the compiler isn't going complain about exceptions and no termination of program as the exception will *be handled*
    - **throws** helps let programmers/users know what exception is to be expected and need to handled when using that method


    # Data Structures in Java
    ## Array
    - An **array** is collection of similar type elements that have a **contiguous** memory location
        - **contiguous**: next or together in sequence
    - In Java, **arrays** are objects that store/contain elements of a similar data type
    - Arrays can only contain a fixed set of elements (fixed-size)
    - Arrays follow 0-based indexing meaning that the first element always starts at index 0 (and not 1)
    - There are two types of arrays:
        - 1D arrays
        - Multi-dimensional (2D and more) arrays

    ## Advantages/Disadvantages of Arrays
    - **Arrays** makes code optimized in that we can retrieved/sort data efficiently
    - **Arrays** allows for random accessing (we can get data/element at any index position quickly)
    - However **arrays** don't have an infinite size nor can they grow during runtime. It's always a **fixed size** and can't store any more elements when capacity limit is reached.

## Array Example
```Java
class TestArray {
    public static void main(String[] args) {
        int[] a = new int[5];
        int arr[] = new int[5]; // syntax allows for brackets to be after variable name or after data type of array
        int[] seq = {1, 2, 3, 4, 5}; // creating and initializing an array 
        a[0] = 10; // assign an array element a new value (initialization/reassignment)

        // print all values in array
        for (int i = 0; i < seq.length; i++) {
            System.out.println(seq[i]);
        }
    }
}
```
## Queue
- A data structure that follows First-In-First-Out (FIFO) guidelines, where elements are stored in an ordered list and the first element is always the first to get remove and all new elements are inserted at the end of the list
- In Java, the Queue interface is a part of the **java.util** package and extends the **Collection interface**.
- Popular implementations used in Java are **LinkedList, ArrayBlockingQueue, PriorityQueue**.

## Collection Interface
- Main foundation/interface which the collections framework is built from. 
    - Collection frameworks: refers to classes and interfaces that represent a **collection** of objects 
        - Interfaces - are abstract representations of collections
            - allows collections to be manipulated independently of details of their representation.
            - In OO languages, interfaces form a hierarchy
        - Implementations/Classes - These are concrete implementation of the **collection interfaces**
            - These are usually reusable data structures
        - Algorithms - methods that are used to perform computations such as searching and sorting on object that implement **collection interfaces**.
            - can be polymorphic: the same method can be use on many different implementations of appropriate collection interfaces
    - Collection framework also defines **map interfaces and classes**
        - Although maps are not collections in defintion/proper use of the term, they are **fully integrated** with collections
        - Maps: storing key-value pairs

 ## List Interface
 - The **List** interface extends **Collection** and declares the behavior of a collection that stores a sequence of elements
 - Some Behaviors:
    - elements can be **inserted or accessed** by their position in the list (indexing)
    - A list may **contain** duplicate elements
- Classes that implement List are **ArrayList, LinkedList, Stack and Vector**. With ArrayList and LinkedList being the most widely used in Java programming
- Just like any other interface you can't create objects of the **interface** type.
- However we can use it when declaring a type of an object, but as for the creation of the object **we need a class that implements** the **List** interface.
```Java
List<Integer> list = new ArrayList<Integer>();
```
- As you see the object/variable type is a List, but to create we use the ArrayList class which implements the List interface.
- Note that also with Java 1.5 we can restrict what data type the elements of the list. This is shown `<Integer>` meaning only Integer objects can exist in the list


## ArrayList
- A part of the java.util package and collection framework.
- Provides **dynamic arrays** in Java.
    - Note that regular **arrays** are of fixed size and **dynamic arrays** are **arrays** that **can** grow in size at runtime.
- Is slower than standard arrays, but can be helpful where many manipulation of an array is needed
- **ArrayList** inherits from the **AbstractList** class and implements the **List** interface
- An **ArrayList** is initialized by size, however the size can increase/decrease depending on adding/removing elements
    - Unlike an array where we do give it an initial **size**, with an ArrayList we **can** give it an initial **capacity**
    - The difference is that capacity here means the number of elements it could possibly hold and that size refers to the number of elements in it already. 
- Just like an array, **ArrayList** allows use to randomly access the list
- ArrayList like all other List-implemented classes cannot hold primitive types (int, char, short), they can only hold objects
    - We can hold instead **wrapper classes** of those primitive types as the wrapper classes are objects.
    - **Primitive** data types are not objects, they don't have methods nor other instance fields that are accessible. The only thing they have is the value that can be modify
```Java
ArrayList<Integer> arr = new ArrayList<Integer>();
arr.add(0); // add element 0
arr.remove(3); // rmeoves object at index 3
arr.set(0, 3); // changing the element at index 0 to 3
```
- Going back to size vs capacity these terms are sometimes used interchangeably, but to be clear when we provide an ArrayList with the value for initialization this is the **capacity** this isn't necessarily its current size, but rather the possibility of how large it can get.
- When we try to access an index assuming that we have created an initialized capacity/size ArrayList, it will prompt an Exception as the ArrayList has no objects in it. The value we gave it was just a capacity that kind of also allocates space for that many elements but its actual size is 0 as we have yet to initialized any elements into it.

## Set Interface
- A **Collection** that can't contain **duplicate** elements
- Based on the mathematical set abstraction.
- Implements the **Collection** interface and only adds the restriction no duplicates
- Set also adds a stronger contract on the behavior of the equals and hashCode operations.
    - This allows Set instances to be compared meaningfully even if their implementation types differ.
        - This refers to the idea that while sets are unordered, when compared as long as they have the same size and same values contained in them then both sets **are the same**
- The **Set** interface is implemented in classes like **HashSet, TreeSet, LinkedHashSet**
- It should be noted that in classes like the **HashSet** the values/elements are inserted based on their hashcode (refers to stronger contract on behaviors of hashCode operations). 
```Java
Set<Integer> set = new HashSet<Integer>();
set.add(0); // adds element to set
set.remove(0); // removes the value (this is not index)
set.contains(0); // check to see if element exist inside set
```

## Map Interface
- Outlines the behaviors of **maps** which is mapping unique keys to values. Keys are objects you can use to retrieve a value at a later time.
- Using map
    - Given a key and value you can store a value in a Map object and retrieve it (after storing) via using its key.
    - There are situations where various methods throw a **NoSuchElementException** when no items exist in the map
    - A **ClassCastException** may be thrown when object is incompatible with elements in a map
    - **NullPointerException** may be thrown if an attempt is made to use a **null object** and **null** is not allowed in a map
    - **UnsupportedOperationException** is thrown when attempt is made to change an **unmodifiable map**
```Java
Map m = new HashMap();
m.put("Zara", "8");
String age = m.get("Zara"); // returns value using key
m.remove("Zara") // removes key-value pair from map
m.size() // returns number of elements/pairs in the collection
```
- `size()` is available to all **Collections**