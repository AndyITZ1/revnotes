# JavaScript
- JS is a programming language and is often used to program the behavior of web pages

## JS in Web Development
- JavaScript can update and change HTML and CSS via code without the user needing to edit the HTML document/CSS file directly
- JavaScript like other programming languages can have functionality in performing calculations, manipulating data, and validating data
```JS
var x, y; // declaring variables
x = 5; y = 6; // assigning variables values
z = x + y; // using other variables to perform arithmetic and store values in other variables
```
- JS can handle different types of data like strings, integers, floats, and more
- In JS, strings are text data that can be written by surrounding text with double quotes or single quotes to form **string literals**

## JavaScript Variables
- In programming languages, variables are often used to store data values.
- In JS, you can create/declare variables with the **var**, **let**, and **const** (and optionally with no keywords)
    - The **var** keyword was use pre-release of ES6 (new standard for JS), but is still used nowadays, but has some problems/disadvantages. Such as redeclaring a variable. 
        - While reassigning a variable is one thing we might do often, redeclaring a variable is a little extra as now we create a variable vs using it as an existing one.
        - Another kind of iffy use of **var** is that when place in conditional statements like for loops, that variable can also be used outside of that for loop as its not bound by the loop block. Rather the variable is bound by the function scope its within
        ```JS
        for (var i = 0; i < 5; i++)
            console.log(i)
        console.log(i) // prints 5
        ```
    - **let** and **const** were introduced with ES6 and are **block-scoped**
        - **let** is like **var** where we can still declare variables and reassign values.
            - However it triggers an error when trying to redeclare or declare an existing variable 
            - As its block-scoped, that means also that we can't access variables other than inside the block it was declared
            - This is the alternative to **var**, that is use more often now to avoid the flaws of **var**
        - **const** unlike **var** and **let** is only meant for variables that are to be constant
            - This means a variable that won't change and with the **const** keyword cannot be changed at all. So **const** variables can't be reassigned at all
        - For variables that don't use these keywords, they are called undeclared variables.
            - Undeclared variables aren't use often, but occur when no keywords are used to declare a variable and these variables are assigned a value.
        - However for variables that haven't been declared and haven't gotten a value and are used those are **undefined variables** which triggers an error when trying to use them.
## Comparison Operators
- '==' operator tests for abstract equality, where type conversions happen before equality comparison is done
- '===' tests for strict equality, where if the value is not of the same type but have "same value" then this will be false 

```JS
a = 9; // Numerical 9
b = "9"; // String-literal 9
console.log(a == b); // prints true, (type conversion occurs to match data types)
console.log(a === b); // prints false
```

