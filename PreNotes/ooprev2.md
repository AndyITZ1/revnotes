# Encapsulation

## What is Encapsulation?
- Encapsulation is the process of wrapping code and data together into a single unit.
    - It essentially binds together code and the data it manipulates 
    - One can think of it as a medicine caplet that contains many different medicines/chemical compounds inside of it. 
- To create a **fully encapsulated** class in Java, we make all the data members of that class **private**
    - This pushes the need for **getter** and **setter** methods to be able to manipulate/use that data.
    - **Java Bean** is an example of a fully encapsulated class.

## Advantages of Encapsulation
- **Data hiding** is now possible, given that no other piece of code nor another class can gain **easy access** to **privated data** in the current class.
    - Furthermore this hide any implementation details about a class like we can't see what it stores. 
- Similarly, we can make a class restrictive to a user in that it can **be read-only/write-only/both**. In that the only way to get to the data is via **getter/setter** methods and if the developer chooses to not provide some or none of those methods then the user has restrictions in using that class.
- As the programmer/developer, you again have full control over how much a user can see/use. 
- Encapsulating a class also makes it easy for testing 
    - In the sense that we know what behaviors we can test for and there isn't any changes that can affect encapsulated code.

## Access Modifiers
- In Java, there two types of modifiers: **access modifiers** and **non-access modifiers**
- **Access modifiers** in Java, specifies accessibility (scope) of a data member, method, constructor, or class. 
    - In depth, this means we can control what other code can have access or use the listed things above.
- There are 4 types of **access modifiers**:
    - private 
    - default
    - protected
    - public
- The two most commonly used ones are **public and private** where **public** allows users to be able to access code pretty much from anywhere and the **private** is the opposite where users can only access code relative to the class it was created/initialized in. 

## Non-access Modifiers
- 

## Accessibility Chart
|                                | private | default | protected | public |
|--------------------------------|---------|---------|-----------|--------|
| Same Class                     | Yes     | Yes     | Yes       | Yes    |
| Same Package Subclass          | No      | Yes     | Yes       | Yes    |
| Same Package Non-Subclass      | No      | Yes     | Yes       | Yes    |
| Different Package Subclass     | No      | No      | Yes       | Yes    |
| Different Package Non-Subclass | No      | No      | No        | Yes    |

## Default
- Unlike all other modifiers, the **default** modifier requires **no keyword** and as in the name modifies the accessibility of code by default when the code is written as is. 
- However this means that for **default** to work is that you can't use any other **modifiers** in the code for that specific data member otherwise it becomes that modifier instead. 
- **Data members, methods, classes which are not declared with any access modifiers** are only accessible in the same package.

## Private
- As explained above, means that all data members/methods are accessible only within the class they were declared in. 
- Private Class:
    - While we can **private** a class, there are only certain scenarios we can do it.
    - Top-level class: refers to a class that is seen by everyone (this doesn't mean its content are accessible)
    - Inner classes: are classes that are within/nested inside other classes.
    - When we use **private** on a **top-level** class, we can't use that class at all in general (it would be a useless class)
        - No access to a constructor/data/methods
    - However we can **private** inner classes, what this does is that an inner class and its content are not accessible to user basically hiding the inner class. 

## Protected
- Is the modifier that allows a data member and etc. to be accessible within the same package and **by a subclass** of a different package.
- The latter part of the definition refers to that when we have two different packages and we have one class in each package. Lets call them **A** and **B**. As long as **B** (inside package 2) inherits **A** (inside package 1), then **B** has access to **A**'s stuff.
- However if **B** is not a subclass (it doesn't inherit) of A then it cannot access/use **A** in anyway. 

## Example of Access Modifiers**

```Java
package p1; 
protected class A {
    private int age; // privating data makes only usable in the same class
    public void setAge(int a) {
        age = a; // This is the only way a private data can be used
    }
}

private class B { // Unusable class B can't be used or accessed by any class
    private int ball;
}

public class C { // public class
    public static int card = 0;
}


package p2;
import p1.*;

class D extends A {
    A obj; // here we show that "obj" here is a default object meaning that it can be accessed by other classes in the same package
    public A show() {
        A a = new A(); // here A is usable due to class D is a subclass of A which is within restrictions of a protected class like A
        System.out.println(C.c); // since C is public and its card data is public as well we can access it anywhere (even in another package)
        return a;
    }
}

public class E {
    A obj;
    public A showA() {
        A a = new A(); // Error as A is a protected class in another package, if E isn't a subclass it can't use/access A in anyway
        return a;
    }
}
```


# Abstraction

## What is Abstraction?
- While we did talk about **encapsulation** hiding detail implementations, **abstraction** is the process/concept of hiding implementation details. 
- The purpose is show **only** functionality to a user without needing to show details of implementation.
- A good example of this is SMS or otherwise known as text messaging. Here you don't know anything about the internal process behind the texting like how is the message sent or how the message is received.
- **Abstraction** lets user focus on what an object does rather than how it does it. 

## Generalization
- **Generalization** is the process of extracting shared characteristics from multiple classes and combining them into a **generalized** superclass. **Shared characterisitics** can be things like attributes, associations, or methods.
- Why we might generalized?
    - Prevent code duplication in the sense that we can create subclasses of a superclass and those subclasses can easily gain all their common characteristics with other subclasses from the same parent class. 
        - If we created classes and then created another class that has some same features (A Student class that has a name and age and then a Teacher class with a name and age), we have to write the same lines of code twice as to once when we only write it in the superclass Person. 

## Specialization
- **Specialization** is rather slightly the opposite of **generalization**, where was want to create subclasses/classes that have unique attributes/data/methods only to them. 
- By doing this we can see the point that not all classes share the same characteristics
- We can think of it as the scenario of People, Student and Teacher
    - While Student and Teachers are both People, A Student is not a Teacher nor is a Teacher a Student.
- We **specialized** to be able to create unique classes for specific scenarios. If we did not subclass the Person class to Teacher/Student? Then we would have to accommodate for things like a Student's roll number or a Teacher's employee number. And a Person class should not have to have both as it attributes as it is not true for every Person to have those attributes. 

## How can we achieve Abstraction?
- **Abstract class**
- **Interfaces**

## Abstract classes
- Are essentially classes that are designed to be superclasses but in terms doesn't need to provide complete implementations of every method it has.
- It kinds of used to **generalized** a form for its subclasses to extend from but also be able to make subclasses instill their own specifics to what methods it may provide. 

## Characteristics of an Abstract Class
- Its always a class declared with the **abstract** keyword
- It can have **abstract methods** which are methods that are declared without implementations.
- Can have a mix regular and abstract methods.
- Note that any class that has one or more **abstract methods** must be declared with **abstract** making it an **abstract class**
- **Abstract classes** can't be directly **instantiated** meaning it can't have an instance/object via the **new** operator.
- However **abstract classes** can have both default and parameterized constructors. Which are usable by the **super** keyword which means only classes that extend the **abstract class** can implicitly create an **instance** of it.
- Other things it can contain are **static and final fields/methods**

## Abstract methods
- **Abstract methods** are methods without implementation and only exist in **abstract classes**
- Any subclass of the **abstract class** must implement/override all **abstract methods**
    - This means defining the body of the method for it to be usable
    - Or making the subclass another abstract class by maintaining the **abstract** keyword on the method.

```Java
abstract class Shape {
    String color;
    abstract double area();

    public Shape(String color) {
        System.out.println("Shape constructor called");
        this.color = color;
    }

    public String getColor() {
        return color;
    }
}

class Circle extends Shape {
    double radius;

    public Circle(String color, double radius) {
        super(color);
        System.out.println("Circle constructor called");
        this.radius = radius;
    }

    @Override double area() {
        return Math.PI * Math.pow(radius, 2);
    }
}

class Test {
    public static void main(String[] args) {
        Shape c = new Circle("blue", 2.0);
        System.out.println("Circle is color: " + color + " and Area is " + c.area() + ".");
    }
}
```
- In the above example, we showcase both **abstract classes and abstract methods**. Where **Circle** class has to implement the **area()** which is abstract and then the **Circle** constructor uses the **Shaper** constructor **implicitly** instantiating a **Shape** object. 
- **getColor** is shown that **abstract classes** can have regular methods.