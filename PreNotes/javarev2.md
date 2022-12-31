# Looping Constructs
- With many programming languages, they all provide various controls structures that allow for more complicated execution paths.
- Loops statements are a structure that allows us to execute a statement or group of statements multiple times 
- There are 3 types of loops that Java provides:
    - While loop
    - For loop
    - Do..While loop

## While Loop
- A while loop is one that allows us to executes a target statement(s) as long as a given condition is evaluated as true
### Syntax
```Java
while (condition) {
    // Statements
}
```
- The **condition** provided in the while loop can be any boolean expression or even *integers*.
    - In Java, any non-zero value can evaluates to **true** and zero itself evaluates to **false**
- Following the end of each execution of all statements in the loop block, the condition/boolean expression is reevaluated again to check for true, if its false then the loop ends and the following code after the loop block is ran.
    - This is similar to an IF statement where initially you have to evaluate the condition prior to executing the statement(s). If false then you just move on pass the block

## For Loop
- A **for loop** is slightly different from a while loop in that while it is a repetitition control structure, it's use to create a loop that will only execute a specific amount of times
- It can be useful when you know how many times a task should be repeated
### Syntax
```Java
for (initialization; condition; update) {
    // Statements
}
```
- Unlike a while loop, a for loop has two more statements that it evaluates/executes at the beginning and during the loop to control the loop. 
    - The initialization statement is only executed during the first phase of the loop (before the loop starts executing), where it declares/initializes a variable that would be used in the condition/boolean expression statement and in the updating statement.
    - Skipping the condition statement as its just an boolean expression similar to its use in the **while loop**
    - The update statement executes during the end of each execution of the whole loop block. It basically updates any variable that you put in that statement, but mainly it updates the variable that we initialized and utilized in the loop condition\
        - Updating could mean incrementing/decrementing not just by 1 but by a factor of some amount
- Similar to the while loop, the **for loop** stop executing when its loop condition is evaluated to be false

## Do-While Loop
- A **do-while** loop is rather the same thing as a **while loop**, however the difference is that rather than evaluating before the first time the loop runs, the loop executes all the statements in the loop block at least once before starting to evaluate the loop condition to progress with the loop repetition.
### Syntax
```Java
do {
    // Statements
} while (condition);
```

## Enhanced For Loop
- While this is not technically a different type of loop, this is a **for loop** mainly used to traverse collections of elements like arrays
### Syntax
```Java
for (declaration : expression) {
    // Statements 
}
```
- Unlike a regular **for loop**, the enhanced for loop only uses different statements that aren't necessarily conditional-based statements but rather just a declaration and the "collection" object that you would traverse through
- The **declaration** is basically the variable that we declare to use and it represents each object inside the collection.
    - During each iteration of the loop the variable is reassigned to the next object in the collection of objects. 
    - Also the declaration variable should be of a compatible type/same type as the elements inside the collection that you are iterating through. 
- The **expression/collection** is the variable name of the collection or a function call that returns a collection.
    - The collection is usually data structures like an array. 

---

# Usage of Keywords
## "this" Keyword
- In Java, the **this** keyword refers to the reference variable that refers to the current object.
- There are 6 usages of **this**
    - **this** can be used to refer the current class instance variable
    - **this** can be used to invoke current class method (implicitly)
    - **this** can be used to invoke the current class constructor
    - **this** can be passed as an argument in the method call
    - **this** can be passed as an argument in the constructor call
    - **this** can be used to return the current class instance from the method

## **this**: current class instance variable
```Java
class Student {
    int rollno;
    String name;
    Student(int rollno, String name) {
        this.rollno = rollno;
        this.name = name;
    }
}
```
- In this example, the Student constructor method has parameters that are named the same as the class instance's variables (rollno, name). To avoid conflict with the naming ambiguity as to what name refers to what variable is being referred, the **this** keyword can be used
- **this** here refers to the class instance and to get its variable we use the dot operator and the variable name `this.rollno`.
- Now in the constructor you can see that this.rollno refers the 'rollno' variable that belongs to the class instance and that the *rollno* being used to assign is the parameter/argument passed in. Similarly the same thing happens with the *name* and 'name'. 


## **this**: to invoke the current class method
```Java
class A {
    public void m() {
        System.out.println("m");
    }
    public void n() {
        System.out.println("n");
        this.m(); // Same as m()
    }
}
```
- In this example we can see that the **this** keyword is being used like a class object to call a method m() from the class.
- In simple terms, this case usage is not used often as we would just call m() as is and not this.m(). But however in the background Java actually, does automatically add the **this** keyword when the compiler invokes/calls the method. 
- To explain the usage here, the **this** here is referred to as the current class instance and an instance is just an object of that class type containing variables and methods. Each object/class instance has their own copy of instance variables that may contain different values and instance methods that pretty much do the same action but may differ depending on the data stored in the instance. 
- So the **this** here is the same as the first case, but here we are using it to call a method and not to grab/refer to one of its variables

## **this** : to invoke current class constructor
```Java
class A {
    A() {
        System.out.println("a");
    }
    A(int x) {
        this();
        System.out.println(x);
    } 
}
```
- Similar to the previous two case usages for the **this** keyword it refers to the current class instance, but moreso here it actually refers to the current class.
- Using this reference we can call the class constructor. Note that the usage here is in a overridden class constructor. 
- The purpose of using **this** like this is to allow for constructor chaining
    - This can be helpful if you want to carry functionality of another constructor into one that is being used, so that there's no need to write the same line of code used in the other constructor again in the one being used.
### Extra example
```Java
A(int x) {
    // Some code
}
A(int x, int y) {
    this(x);
    System.out.println(y);
}
```
- You can see that you can still pass arguments to using this as a constructor method.

## **this** : to pass as an argument in the method
```Java
class A{
    void m(A obj) {
        System.out.println("This method has been invoked");
    }
    void p() {
        m(this);
    }
}
```
- While this isn't the best example, the idea here is that we are using **this** to refer to current class instance/object and now we are using an argument for a function that takes in a parameter of type "current class". 
- Application of using **this** this way, when we want to do **event handling** or have a situation where we want to provide this current class instance to another class function or object that needs **this current instance**. 

## **this** : to pass as an argument to a constructor call/invocation
```Java
class A {
    int data = 10;
    A() {
        B b = new B(this);
        b.display();
    }
}

class B {
    A obj;
    B(A obj) {
        this obj = obj;
    }
    void display() {
        System.out.println(obj.data);
    }
}
```
- Similar to the previous usage case, we can refer **this** as a reference to the current class instance, here the example shows it being used in a constructor call.
- Use case of this is when we have to use one object in multiple classes, so we might want to pass this object/instance to those classes when we create it. 

## **this**: used to return the current class instance
```Java
class A {
    A getA() {
        return this;
    }
}
```
- While this example isn't the best application of how we use **this** in this way, it works to show that again we use **this** to refer to the current class instance and that it can now be return as a value from a function. 

## Summary of **this**
- 5 of the 6 use cases for **this** refers to the current class instance, and in case 3 we see that it rather is more using to refer to the class as we calling that class constructor via **this()**

## **new** keyword 
- The **new** keyword is used when we want to instantiate a new object.
```Java
Student will = new Student();
```
- In this example, the **new** is being used to say that we want to a physical copy of an object of type Student, which is created by its class constructor **Student()**. Upon acquiring the object we can assign it to the variable **will** that is of data type **Student** which is the class. 
- To go in depth, the **new** keyword when used allocates memory for the object it wants to create and then returns a reference to that memory that is usable and the store/assigned to the variable **will**.

## **super** keyword
- The **super** keyword is reference variable used to refer to the immediate parent class object
    - Whenever you create an instance of a subclass, an instance of the parent class is created implicitly which is referred to by the **super** keyword
- You can **super** in different ways:
    - to refer to an immediate parent class instance variable
    - to invoke an immediate parent class method
    - to invoke an immediate parent class constructor

### Example of **super** keyword
```Java
class Animal {
    String color = "white";
    Animal() {
        System.out.println("Animal created");
    }
    void printColor() {
        System.out.println(color);
    }
}

class Dog extends Animal {
    Dog() {
        super();
        System.out.println(super.color);
        super.printColor();
    }
}
```
## **static** Keyword
- **static** keyword is used for memory management mainly in Java
- **static** can be applied to variables, methods, blocks, and nested classes
- The **static** keyword belongs to the class rather than an instance of the class

## **static** Variable
- A **static variable** can be used to refer to a common property of all objects
    - meaning that it's not unique to any object
    - Ex: company's name for all employees of that company, college name for all students who attend that college
- **static variables** gets allocated memory once and this done during the time the class is loaded.
- Advantages: It makes your program **memory efficient** (saving memory)
```Java
class Student {
    static String college = "ITS";
    int rollno;
    String name;
    Student(int rollno, String name) {
        this.rollno = rollno;
        this.name = name;
    }
}
```
- How does it save memory?
    - A good example of this is if the 'college' variable above wasn't static and its like any other instance variable for all instances for the classes. When you create the object, the object has to allocate space for all its instance variables and the data it stores. The intention of instance variables having their own allocated memory is because they all differ in the data they store because each instance/object can have different data they store that is unique in cases to that instance. But since we know that the college any **Student** object goes to is "ITS" well then that isn't *unique* and so we are allocating space for an instance variable that stores the same thing for multiple **Student** instances. Which means we using more memory. 
    - The key point is that **static** making 'college' a static variable is to only allocate memory for that variable once and its done during when the class is loaded/compiled. This variable can be used by all **Student** instances but is not multiple copies (that each have their own memory space) that is unique to each instance, but rather just one variable being pulled from a pre-allocated space for it. 
## Proving that a **static variable** is shared by all instances of a class
```Java
class Friend {
    static int friendCount = 0;
    String name;
    Friend(String name) {
        this.name = name;
        friendCount++;
    }
}
```
- The above example shows that we have a static variable called 'friendCount' and this variable is incremented upon each call to the Friend constructor.
- When instantiating multiple **Friend** instances, if you were to print the 'friendCount' you could see how many **Friend** instances were made. This shows that each **Friend** instance doesn't have a separate count of friends that is unique to them but that they share the same variable 'friendCount' and can see when more **Friend** instances increment the count. 
- Also when accessing/retrieving the **static variable** it should be noted, that the variable belongs to the class **Friend** and not the instance of it. So calling it would something like this:
```Java
Friend.friendCount;
```
- While you can call friendCount via an instance its not recommended, the reason being is that its not being accessed in a static way and it would violate why its a static variable if an instance would try to modify it. As it's not unique or bound to any instance. It's only belongs to the class and is shared by all instances.

## Static methods
- Similar to static variables, a **static method** is a static member, which means it belongs to the class.
- Why would we use static methods?: The idea is that when making a method like for example the Math class' `round()` method, you can justify the idea that such a method isn't unique to any instance in any way rather its something that is the same across every instance. So in terms of how we would call this method is we do `Math.round();` vs having to instantiate a Math object and then calling from that Math object.
- And from this example you wouldn't need to make a Math object as there is no need to make unique instances of the Math class as its purpose is to provide math methods that is written the same way everytime when used.

## **final** Keyword
- The **final** keyword is used to restrict the user from doing an action. 
- It can be applied on variables, methods, and classes.

## Final Variables
- The **final** keyword is used on variables to prevent users from being able to change that variable.
    - Essentially, this is known as a **CONSTANT** variable, where the value "doesn't need to" change and that its always the same regardless of anything else.
- **Final variables** can be either initialized when they are declared or when the constructor is ran. 
    - All final variables must initialized otherwise a compiler would throw an error.
- When a final variable is **not initialized** when its declared, its called a **blank final variable**
    - To avoid getting a compiler error, a **blank final variable** must then be initialized in some other way:
        - One way is initializing it in an **instance-initializer block (IIB)** or inside the constructor
            - If you have more than one constructor, then the **final variable** must be initialized in all of them (constructors)
        - The difference between an **IIB** and a constructor is that an **IIB** is executed before a constructor but it runs during the initialization of a class. 
            - In terms of parent/child classing, super() goes first, then the IIB, and then constructor code.
        - Another way is initializing the variable in a static block similar to IIBs, static block dedicated to initializing static code that is intended to allocated once in memory and is shared by all class instances.
            - Unlike IIBs, where they are executed when an instance is being initialized, **static blocks** are ran when the class is being loaded into memory
            - Like IIBs, there can be multiple blocks and they all execute before the constructor.
        - However the intention of the last way is that the **final variable** is also static, which means its a *blank final static variable**
            - This also means that **final variables** can be static variables 

## Final Reference Variables
- As we know, **final variables** can't be reassigned their value can't change.
- However if the variable is a reference variable, then there's a property to **final** known as **non-transivity**.
    - This property, allows for **internal state of an object be changeable**, but in terms of the value/object the reference variable is holding is not changed.
    - Reassigning a reference variable would mean you are switching which object a the variable is pointing to, but if we are just changing the internal state of that object is not switching to another object. 
    - With that **final reference variables** can exist such as **final arrays**, Strings, and any other objects. 

## Final Classes
- The **final** keyword when applied to classes, is used to prevent inheritance and creating immutable classes.
- The idea of preventing inheritance is that the current class we make **final** is intended to stay that way and isn't corrupted in behavior by any subclass. 
    - The String class in Java is a good example, the developers wanted the String object to behave in ways like being immutable and have all of its String functions. But if it wasn't final and was able to extend from anybody could easily change how the String class acts through its subclass, (while this doesn't change the code of the String class) all the behaviors can be overridden meaning that they will act differently now in the subclass. 
    - The point here is that the String object was to behave just like a String and it would not need any other changes/corruption. 
- Immutability of a class again kind of describes the same thing in that you don't want to change the object's behavior, but also as with the String class we can make the object's data unchangeable so that the object stays the same way 
- Another thing is that why would we need immutable classes, think of scenarios where objects don't really need to change. Example would be a playing card object, there are 52 different cards each with unique value and suit combination. With that if we had a card "5 of clubs" we don't need to change anything about it internally so we could just make it immutable. Its constant its not like we need to change its suit or value. A basic example would be the Wrapper classes like Integer and Float.
    - Yes while we can reassign variables different values, this is not the same as changing the object internally meaning that when we say "x = 5" and then say "x = 9", the 5 is not being change internally the only thing that is changing is that we now have a different Integer "object" being assigned to x so therefore Integer class being immutable makes its so that its data is not changed as its internal 5 is not changed as 5 and 9 are two different instances of the Integer class

## Final Methods
- **Final methods** are used to prevent overriding of methods. 
- Overriding can be defined as reimplementing/redefining how a method works that already exists 
- Usually overriding is seen when a child class/subclass is implementing a method that is of the same name and has same parameters as a method in the parent class. 
- We might override a method to customize its functionality to fit a class. 
- Why would we apply **final** to a method?
    - Well we might want to keep the same implementation of a method across all classes from parent to derived classes


## **final** Example
```Java
final class A {
    final static int X;
    final double PI;
    final int y;

    // static block
    static {
        x = 10;
    }

    // IIB
    {
        PI = 3.14;
    }

    A() {
        y = 0;
        System.out.println(X);
    }
}

class B extends A { // Compiler Error can't extend
    B() {
        super();
    }
}

class C {
    final void display() {
        System.out.println("Show me the world!");
    }
}

class D extends C {
    void display() { 
        // Compiler Error can't override
        System.out.println("Show me the new world!");
    }
}
```