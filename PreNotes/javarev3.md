# String Manipulation
## What is a String?
- **Strings** are a sequence of characters.
- In Java, **strings** are treated as objects
- They can be made from the **String** class which is built-in the Java platform to create and manipulate strings.

## Creating Strings
```Java
String s = "I'm a string!";
```
- Unlike most objects, **strings** can created using *string literals* which when compiler encounters one it creates a **String** object with the value. 
- Other than that, you can create a string using the **new** keyword like any other object and with its constructor
- The **String** class has 11 constructors that allows you to use different sources to provide the initial value of the string.

```Java
char[] helloArray = { 'h', 'e', 'l', 'l', 'o'};
String helloString = new String(helloArray);
```
- When a String object is **created**, it can't be changed. So given if we need to make modifications to a string, you should use the **StringBuffer** and **StringBuilder** classes instead to create strings that are modifiable. 

## String methods 
- Similar to other objects, string objects can have methods provided by the **String** class. 
### Accessor Methods
- **Accessor methods** are methods used to obtain information about an object.
- With a string, we can use a method like the **length()** method to get its length (the number of characters it contains)
```Java
String hello = "hello";
int len = hello.length();
```
## String methods Cont'd
- Methods provided by the String class include:
    - `concat(string2)` which allows two strings to concatenate (combine together into one)
        - the result is a new string returned
    - Concatenation of strings is not bound to the **concat()** method you could also use the **+** operator (which is the most common way of concatenating strings in Java)
    ```Java
    String s1 = "Hello";
    String s2 = " World!";
    String s3 = s1.concat(s2);
    String s4 = "Hi".concat(s2);
    System.out.println(s1 + s2);
    System.out.println("Hi" + " Everyone! " + s3);
    ```
## Other String methods
```Java
String s = "string";
char c = s.charAt(0); // get the character at specified index
String s3 = "strong";
int diffVal = s.compareTo(s3); // compares two objects (Strings) lexicographically. If first is greater than the second, then returns a positive number. 0 if the strings are the same and negative number if second string is greater
boolean equal = s.equals(s3); // returns true if both strings are the same when compared.
boolean equalNoCase = s.equalsIgnoreCase(s3) // returns if the strings are the same regardless of the case (upper/lower) both strings are in 
```

# Java Packages
- A **package** in Java is used to group related classes.
    - It can be thought of as **a folder in a file directory**
- **Packages** are used to avoid name conflicts and to write a better maintainable code.
- **Packages** can also provide access protection
- **Packages** are divided into two categories:
    - Built-in packages (packages from the Java API)
    - User-defined packages (packages a user can create)

## Using packages
```Java
import java.util.*; // Gets all classes within package
import java.util.Scanner; // Gets one specific class from a package
```
- When retrieving a package and the classes the store within, we have to use the package name and the dot operator to get all classes (using wildcard notation *) or just get one class we want by the class name. 
- In the above example, Scanner is a class part of the java.util package and java.util is the package.

## Creating packages (User-defined packages)
- When creating a package, the **package** keyword is used and follow by the name we want to assign this package.
```Java
package mypack;
class MyPackageClass {
    public static void main(String[] args) {
        System.out.println("This is my package!");
    }
}
```
- It should be noted that all packages have **identifiers** that are all written in lowercase to avoid conflicts with the names of classes and interfaces 
- In adding to a package, we put the class we want to be a part of the package following the **package declaration**.
- Upon compiling the Java file that contains the **declaration** (package) and the class, we would also need to compile the package as well for it to be created and then relatively stored in a way in which it parent folder to the class file that is part of its package.

## Accessing a package from other packages
- There are different ways to access a package outside the package
    - importing the whole package
    - importing the class from that package
    - using the **fully qualified name**

### Importing the whole package
- To get access to all the classes and interfaces of a package, we use the package's name, dot (.) operator, and the wildcard notation (*).
```Java
import packname.*;
```
- Here we also need the **import** keyword as it is what allows us to even access the package from another location that isn't where the package is located.
- One thing that can be noted is that packages can be within other packages.
    - Meaning that **subpackages** exist, but when we import the whole package, we aren't allow access to them (subpackages) unlike the classes and interfaces.

### Importing only the desired class from a package
```Java
import packname.PackagedClassName;
```
- Similar to getting the whole package, instead of the wildcard notation (*) we just simply put the name of the desired class we want to access from that package. 

### Using **fully qualified name**
- Unlike the other two ways, this method of accessing the package doesn't require the import keyword rather when we want to use a specific class from a package we just use the package name along with the class when using that specific class type anywhere. 
```Java
packname.PackageClassName varName = new packName.PackageClassName();
```
- We generally use the **fully qualified name** when there is a scenario where two different packages have a class each that has the same name as each other.
- Example: java.util and java.sql both have a **Date** class
- So in order to avoid running in those problems we use the **fully qualified name** (basically the package and the class together)
- It should be noted that the **fully qualified name** is used when importing a package/class to be used. 

## Sequence of a Program
- When writing a program and with the intent to package it. We must package then import and then create classes in that order.
- Package to store whatever follows
- Import is second as to have access what other packages/classes that may be needed during a program
- And then class which is what the program class should be compiled and then stored into the package.

# Interface
## What is an interface?
- An **interface** is a reference type in Java.
    - What this means is that its similar to a class when being refered to as a type of an object. **BUT** this does not mean you can create/instantiate an object from an interface.
- An interface has the purpose of being able to store things like constants, abstract methods, default methods, static methods and nested types. 
- By storing these, an **interface** is necessarily being use to group behaviors that can be implemented by a class which allows us to create objects which uses behaviors. 
- By implementing an interface, all classes except **abstract classes** are required to defined the all ehaviors/methods that exist in the interface.

## Interface vs Class
- While both are similar in that they can **contain methods, have names that match the .java file they are written in, the bytecode of both appear in .class file when compiled, and both can be stored in packages**
- There are differences
    - Again you **can't instantiate** an interface
    - An interface doesn't have a constructor
    - All methods that exist in an interface are **abstract**
    - An interface can't have **instance** fields (variables), however fields that can be used have to be static and final (constants)
    - An interface is **implemented** and not extended by a class
    - An interface can extend multiple interfaces.
        - This is however similar to the idea that a class can implement multiple interfaces, **but not** extend.

## Clearing/Defining what Interface can contain
- Prior to Java 8, **interfaces** could only contain methods that were abstract. With Java 8 we allowed **default methods** to be inside **interfaces**. 
- **Default methods** are basically methods that **can** have implementation when written inside an **interface**
    - The purpose is to allow backwards compatibility where if we want to write new methods for an interface, then given the implementation of those methods, this wouldn't affect existing classes that implement the interface (also classes wouldn't have to implement those methods)
- Similar to default methods, **static methods** could be implemented into interfaces. **Static methods** act the same way as they do in classes, where its allocated upon loading of the interface and that it's a method that is general and not necessarily unique per case of implementing the interface via a class. 
- One big thing to note about **default methods and having a class implement multiple interfaces** is that when two interfaces have a same name method that the class has to use, the class itself must override that method to avoid collsion and customly define how it wants that method to run (as in running both one after another or choosing one version to run)
- Constants in interfaces was popular thing in early times in Java development, but nowadays we would put constants in classes as an implementation detail for that class
    - The purpose of interface is to just contain the behaviors for the object and not any of its data 
    - As mention earlier if we do place **constants** in interfaces it has to be both static and final as there is no place for instance data in an interface as it will never create an instance of itself

## Example of Using Interfaces
```Java
public interface Animal {
    public void eat();
    public void travel();
}

public interface Canine {
    static void howl() { // static method in interface
        System.out.println("Howling");
    }
    default void findPack() { // default method in interface
        System.out.println("I found my pack!");
    }
    default void bite() {
        System.out.println("Biting something");
    }
}

public interface Sneak {
    public void sneak();
}

public interface Feline extends Animal, Sneak { // interface extending multiple interfaces
    public void purr();
}

public class Dog implements Animal, Canine { // class implementing multiple interfaces
    public void eat() {
        System.out.println("Dog eats.");
    }
    public void travel() {
        System.out.println("Dog travels.");
    }
    public void bite() { // override default method from interface
        System.out.println("Biting a chew toy");
    }
}
```
- In the above example, there various cases that are shown:
    - Interfaces can **extend** an interface or multiple interfaces
        - extending interfaces similar to subclassing with classes
        - child interfaces inherit the methods of the parent interface
        - ultimately the class implementing the child interface will have to implement all the methods
    - Classes can **implement** one or more interfaces (however cannot extend multiple classes, only can extend one)
    - Classes can override default methods from interfaces
        - The main purpose is to avoid ambiguity between two interfaces having a method that is the same name and the implementing class not knowing which one to call
    - Static methods are the same as the ones in classes
