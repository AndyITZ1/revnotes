# OOP
## Object Oriented Programming
- **Object** means a real-world entity such as a pen, chair, table, etc.
- **Object Oriented Programming** is a methodology or paradigm to design a program using **classes** and **objects**
- OOP simplifies the software development and maintenance by providing some concepts:
    - **Object**
    - **Classes**
    - **Inheritance**
    - **Polymorphism**
    - **Abstraction**
    - **Encapsulation**

# Object and Classes

## Object
- An entity that has **state** and **behavior**
    - can be physical or logical
- An instance of a **class**
- Contains an address and takes up some space in memory
- Objects can communicate with each other without know either one's data or code
    - the only necessary things is the type of message accepted and type of responses returned by the bojects
- EX: a dog is an **object**, it has **states** like color, name, breed and it has **behaviors** like tail wagging, barking, eating.

## Class
- A **class** in Java, are **templates** used to create objects and define object data types and methods (these are core properties of the object)
- Sometimes refer to as a **blueprint** for creating individual objects 
- Classes don't consume any space

## Advantages OOP over Procedure Oriented Programming
- **OOPs** makes development and maintenance easier whereas in a procedure oriented programming language it's not easy to manage if code grows as project size increases.
- **OOPs** provides/allows for **data hiding** whereas in procedure oriented porgramming languages a global data can be accessed from anywhere

## Example of OOP
```Java
public class Dog {
    // states/attributes
    String breed;
    int age;
    String color;

    // methods
    void barking() {
        // barking code
    }
    void hungry() {
        // hungry code
    }
    void sleeping() {
        // sleeping code
    }
}
```

# Constructors
- In Java, **constructors** are like methods, but are unique in which they are **called** when an instance of the **object** is created and memory is allocated for that object.
- Special type of method used to **initialize** an object
- A constructor name must **match the class name** and it doesn't nor it **can't have a return type** (void...)
- Also **constructors** cannot be **abstract, static, final, and synchronized**

## What happens during a constructor call?
- When an **object** is created, the **compiler** makes sure that **constructors** for all its subobjects (its member and inherited objects) are called.
    - If members have **default constructors** or **constructors** without parameters then these **constructors** are called automatically. Otherwise any parameterized constructors can called using an **initializer list**
    - **NOTE Objects can have subobjects in terms of C++, but not in Java as only objects can hold references of objects inside of itself**
- **NOTE 2: initializer lists while used to provide parameters to subobject constructors, this only happens in C++**
    - **Java doesn't have initializer lists** as it has references instead of subobjects and references in Java act similar to C++ pointers rather than C++ references, in that you don't need to initialized them immediately and you can do it later (initializing)
    - C++ references must be initialized to bind to some object which is why initializer lists are mentioned above
- **NOTE 3** const (C++) vs final (Java), both keywords pretty much do the same in that they create fields that become unchangeable (CONSTANTS)
    - The main difference is that const (C++) requires those fields must be initialized by initializers lists
    - **In Java, final fields can be initialized in the constructor, However this illegal in C++**

## Types of constructors 
- There are two types of **constructors**: **default** and **parameterized** constructors

## Default Constructor
- **Default constructors** are the basic and often used constructors when instantiating an object. 
- They have **no arguments/parameters** and don't require them
- In Java, if a programmer chooses not to create/define a **default constructor** then the compiler will create/insert one on your behalf.
    - However in reverse (Java), if you do create one, then the compiler will not create one.
    - The main reason why the Java compiler does this is to suffice the condition of having the keyword **super** work. In the sense that if a subclass needs to use the parent (current) class object then a call super() is done implicitly/explicitly to access such object. 
```Java
public class Bicycle {
    int gear;
    int cadence;
    int speed;

    public Bicycle() { // default constructor
        gear = 1;
        cadence = 10;
        speed = 0;
    } 
}
```
- Constructors in depth are utilized to initialized/setup an object's internals such as its data (as shown in the example)

## Parameterized Constructor
- A **parameterized constructor** is self-defined in that it is a **constructor** with parameters
- The main goal of these **constructors** is to allow users to provide different values to creating distinct objects. However they still can provide the same values if they wished to. 


## Constructor Overloading
- In Java, **constructor overloading** is having more than one constructor with different parameter lists.
- Allows for each **constructor** to perform different tasks.
- The **compiler** differentiates each **constructor** by the **number of parameters** and **their types**


```Java
class Student {
    int id;
    String name;
    int age;

    Student(int i, String n) {  // parameterized
        id = i;
        name = n;
        age = 0;
    }

    Student(int i, String n, int a) { // parameterized
        id = i; 
        name = n;
        age = a;
    }
}
```
- The above examples showcases **parameterized constructors** and also **constructor overloading** as seen where there multiple versions of the class constructor which have different parameters lists that differ in typing and size.

## Constructor vs Method
- **Constructors** are used to **initialized** the state of an object
- **Methods** are used to expose the **behavior** of an object
- **Constructors** are invoked implicitly, while **methods** are invoked explicitly
- Unlike **constructors**, **methods cannot** share their name with the class they are in. 
- **Methods** have return types, while **constructors** don't
- The Java compiler provides a **default constructor** when there is none (no constructors at all or no default constructors) in a class. 


# Inheritance

## What is Inheritance and its advantages?
- Inheritance in Java is a mechanism where an object **acquires** all the properties and behaviors of a parent object.
- Important part of OOPs (Object Oriented Programming system)
- The purpose of **inheritance** is that you **can create** new classes via building upon existing classes.
    - When inheriting a class, you get access to methods and fields of your parent class and be able to **reuse** them as your own.
    - For the new class, you can still have new methods and fields.
- **Inheritance** represents the **IS-A** relationship in which the class **inheriting** (child class) **is-a** parent class as it has acquire the same behaviors as the parent
- Advantages:
    - You can do **method overriding** (runtime polymorphism)
    - Code Reusability 

## Types of Inheritance
- There are various different types of inheritance that can occur
    - Single: where only one class inherits from another class, no other relationships
    - Multilevel: When there is a chain of inheritance where there's different **levels** inheriting from the previous class and being subclassed 
    - Hierarchical: When there are branches (multiple classes) inheriting from a class
    - Multiple: When one class inherits from multiple classes
    - Hybrid: When inheriting multiple classes, but the parent classes inherit the same class. (Diamond shape)
- In Java, there is only 3 types of inheritance supported: **single, multilevel and hierarchical.**

## Why no multiple inheritance in Java?
- To reduce complexity and simplify the language
- To avoid conflicting scenarios, like when one class inherits from two different classes, **but both classes have a method they implement that have the same name**, here if the child/current class chooses to call that named method, which one does it call?
    - Here the compiler would experience ambiguity, there would be no right way to determine which parent's method should be called.
- Due to that developers of Java, made **multiple inheritance** an error/exception when tried by a programmer. 
    - It's also a compile-time errors as its better than a runtime-error.
    - Also the fact that when the **compiler** loads the class it will immediately trigger the error if the class inherits from multiple classes
- Again handling such an issue with ambiguity would be complex and the developers Java wanted it to be simple so they omitted such a feature.


# Polymorphism

## What is polymorphism?
- **Polymorphism** is the ability of an object to take on many forms.
- Most common use of **polymorphism** in OOP occurs when a parent class reference is used to refer to a child class object.
- Any Java object that **can pass** more than one **IS-A** test is considered to be **polymorphic**
- In Java, all objects are **polymorphic** since any object will **pass** the **IS-A** test for their own type and for the class **Object**

## Other ways of proving polymorphism
- In Java, polymorphism can be divided into two types:
    - Compile-time polymorphism
    - Runtime Polymorphism

# Method Overloading/Compile-time polymorphism
- Sometimes known as **static polymorphism**
- **Compile-time polymorphism** can be **achieved** by **method overloading**.
- **Method overloading** is the idea of having multiple functions in a class share the same name but differ in the parameters they have. 
- By doing this, we can improve the **readability** of the program and offer different methods to perform different tasks for the same essential goal given the amount of arguments/parameters provided.

## Implementing Method Overloading
- **Method overloading** can be done easily by just changing the amount of parameters and/or the types of the parameters, while the method name stays the same. 

```Java
class Adder {
    static int add(int a, int b) {
        return a + b;
    }
    static int add(int a, int b, int c) {
        return a + b + c;
    }
    static double add(int a, double b) {
        return (double) a + b;
    }
}
```
- In the example, there are 3 different **add()*** methods which all have the same method and similar goal of adding values. 
- The first and second **add()** show that we can have different number of parameters to overload a method.
- The first and third **add()** show that we can change the type of the parameters to overload a method.
- The main reason why this is **method overloading** is that each of the **add()** functions are their own functions and perform slightly different each other, so there is never a collision on which one is being called/used. 
- **NOTE** While we did change the **return type** of the last **add()**, changing only the return type doesn't count or is considered **method overloading**
    - In depth, if there were 2 methods with the same paramemters but only different return types, **the compiler** would not be able to tell us which version of the method to use as **ambiguity** comes in where since all we have to do is provide parameters and they share the same parameters there's no way we know which method is intended to being used. 
    - **By having different number of parameters or changing the type of parameters we can recognized which version a caller might want to use of a method.**
- It is also possible to overload the **main()** method in Java, however when JVM calls the main() method it will always be the one with the string array as a parameter/argument only.

## Method Overriding / Runtime Polymorphism
- **Runtime polymorphism** is when a decision by which method to call is determined during runtime. 
- This happens when we override methods/ do **method overriding**.
- **Method overriding** is when a **subclass** (child class) has the same method signature as declared in its parent class, but the difference is that the subclass has its own specific implementation of the method

## Using and Rules for **Method Overriding**
- Using:
    - used to provide specific implementaiton of a method which is already provided by its superclass
    - used for Runtime polymorphism
- Rules:
    - method must have same name as in parent class
    - method must have same parameter(s) as in parent class
    - There must be an **IS-A** relationship between the classes (parent-child (inheritance))

## Can a static method be overridden?
- The answer is **no**, as **static methods** are bound to classes and not instances. When you call a **static method** you use the class name to call it meaning the compiler will always know which method to call regardless if there is a static method of the same signature in a subclass. 
- In depth: **static methods** are binded to the class during compile-time and not during runtime like with **method overriding**
- And further: if two classes in IS-A relationship have both their own same method signatures. Only one method is hidden by the other depending on what context class the method is being called from. 
```Java
class Parent {
    static void show() { // static method
        System.out.println("I'm the parent static");
    }
    void display() {
        System.out.println("I'm the parent display");
    }
} 

class Child extends Parent {
    static void show() { // static method
        System.out.println("I'm the child static");
    }
    void display() { // normal method overriding
        System.out.println("I'm the display child");
    }
}

public class Test {
    public static void main(String[] args) {
        Parent obj = new Child();
        Child obj2 = new Child();

        obj.display();
        obj.show();

        obj2.display();
        obj2.show();
    }
}
```
- From the above example, we show two different objects one that is instantiated as a Parent and one as a Child.
- When we run the program we can see that both objects' **display() call** are the same as the Child version of **display()**. This is how regular **regular method overriding** works in that the Child's version is specific/reimplements the Parent display(). 
- However when we run both **show()** it can be seen the that the "Parent contained Child" shows the Parent version of the static **show()** method. While the **Child object stored in the Child type object** call to **show()** displays the Child version of the static **show()** method. 
    - This is because as explained above method overriding doesn't work on static methods
    - Along with that, given that the first object (**obj**) is a Child instantiated into a Parent type. The Parent type takes over meaning that the **static method** for Parent will hide the Child **static method**. Vice versa where the Child version will be called if the Child object was instantiated as a Child type. (The parent static method would be hidden by the child version.)