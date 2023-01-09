# Week 4

## HTML

### What is HTML?
- **HTML (HyperText Markup Language)** is the language used to describe the structure of a webpage and used to create a web page. HTML is the standard for displaying web pages and like some markup languages uses tags in its syntax. 

### What are tags?
- Tags are essentially like keywords used to denote an encapsulating structure that stores some data a markup language. HTML tags are used to define HTML elements which do contain content that will define how a webpage looks and how content is shown. 

### What are HTML elements?
- HTML elements provide the structure of the document and are defined by tags. In order for HTML to be valid, the tags must be nested properly for the defining of an element. HTML elements can contain **attributes** which further define certain details to be held or shown by an element. 

### What are the two types/categories of HTML elements?
- HTML elements are divided into two types: **block elements** and **inline elements**. 
- **Block elements** are elements that will render on a web page as a block and each block is displayed on its own line when shown on a web page.Elements following a block element will render on a new line and not the same line as the block element. 
- **Inline elements** are elements that will render on the same line if multiple inline elements are used together and they do not force elements after them to be on a new line.
- We can also nest elements inside of each other. This feature mainly applies to block elements which can contain both other block elements and inline elements.

### What are HTML attributes?
- **HTML attributes** are metadata used to describe HTML elements and are defined within a tag. An example of an attribute is the src attribute inside of an img tag, the src attribute allows us to define the path to where an image is located at this could be a URL or the local filesystem path. 

### What are global attributes?
- Global attributes are HTML attributes that can be applied to any tag, this includes the class and id attributes which respectively can be used to group elements together under a class name or provide an identifier to uniquely refer to a single element. 

### How you setup an HTML Document?
- Prior to writing any form of HTML, an HTML document must start with a **doctype declaration**. This declaration informs the browser what type of document is being displayed as well as the version. The standard doctype declaration used defines an HTML5 document, however for versions older than HTML5 one must reference to a DTD (Document Type Definition) URL to use those versions. 

### What is the root tag of HTML Document?
- Following the doctype declaration, the first tag and root tag of your HTML document is the `<html>` tag. Just like any other tag it is used to define the main HTML element, which will contain all other HTML elements/tags to be used for the HTML document.  
- The HTML page can be further divided and defined into a `<head>` section, which is usually for where metadata elements, and the `<body>` section which is for the actual content to be displayed.

### What are some common elements used in HTML documents?
- `<div>`: defines a "division" of a page, is a block element and usually contains other elements
- `<h1>` through `<h6>` are header tags used to contain text that are typically headings for different sections of a page. Similar to how there can be headings of different sizes, each heading tags makes the heading inside of it a different size. With the largest heading be contained in `<h1>` and the smallest in `<h6>`
- `<p>`defines a paragraph element (block)
- `<span>` is a standard inline element
- `<br>` is an inline element used to add a line break and does not need a closing tag.
- `<img>` is an inline element, is used to display an image, and does not need a closing tag.
- `<a>` is an inline element and is known as the anchor element, which is used to make a hyperlink.

### How are lists implemented in HTML?
- HTML has built-in functionality for how lists are displayed.
- There are two types of lists, ordered and unordered. **Ordered lists** are defined by the `<ol>` tags and are lists where the items are marked or numbered progression with values in a specified order, by default each list item is numbered with numbers, starting from 1. 
- **Unordered lists** are defined by the `<ul>` tag and are lists where the items are bulleted when displayed and the type of bullet can be changed through CSS `list-style-type` property, but by default the bullets are discs.
- List items inside either type of lists are to be enclosed in list items elements defined by `<li>` tags
- Lists can also be nested in others lists regardless of the type of list. 

### How are tables implemented in HTML?
- Tables are defined by `<table>` tags and are a way to structure HTML pages and display information. 
- Inside the `<table>` element we use various different tags to define different sections of the table. 
- We have the `<thead>` tag which define header rows, for defining rows we use the `<tr>` tag, and then the `<th>` tag is used to provide data to an individual header cell.
- Similarly for the body section, we have the `<tbody>` element defining the body of the table, the `<tr>` tags for defining the rows and `<td>` element holds data for the individual cells for rows in the table body.
- Finally, the footer element of a table is defined by `<tfoot>` tags 

### What are HTML Forms?
- HTML has elements to define forms. Forms are essentially used to take various inputs from a user visiting a the website and dependent on the data submitted, the data is processed or handled differently. The data could be sent to be stored in a database or used by the server to process some request made.
- There are various to taking input and various input elements are provided by HTML to allow for this in HTML forms. All input elements are defined by `<input>` tags and to define what type of input an element can take in we use the `type` attribute and provide the input type. 
- Other attributes that are used in forms include name, value, and placeholder which are placed in the `<input>` tag. The name attribute is used to give a name to the value taken in by the input, this is sort like a label for the data. The `value` attribute holds the data or value provided by input and a default value can be given as input by using this attribute. The `placeholder` attribute is used to specify a short hint that describes the expected value of an input field. It should be noted that unlike the first two attributes, the `placeholder` attribute does not work with input types that utilizes anything that is not a text field (Ex: button, checkbox, ...)

### What are the different types of inputs that can be defined from the `<input>` element?
- You can specify text to define a general text field for input, radio to have radio buttons for options a user chooses from, checkbox to have boxes where users can check multiple options, submit and reset which both are buttons that submit the data or reset/clear the data in an HTML form. 
- Other types of input include: password, email, date

### What are other tags or HTML elements used in HTML forms?
- `<button>` element defines a clickable button
- `<select>` element defines a drop-down list, options in the list are specified using `<option>` elements, for specifying the number of visible options the `size` attribute is used in the `<select>` tag, and to allow for multiple selections, the `multiple` attributes is used in the `<select>` tag
- `<textarea>` elemeent defines a mulit-line input field, which can increase in dimensions by using the `rows` and `cols` attributes
- `<datalist>` element specifies a list of pre-defined options for an `<input>` element, this can be seen in scenarios where you are typing something a dropdown list is shown with some already completed values that relatively complete the value you tried to type. And options are again defined by `<option>`
- `<label>` element can be used to give a specific text label to an input field

### What is HTML5 and how is it different from past versions of HTML?
- HTML5 otherwise known as HTML 5.0 is current standard version of HTML used today in most websites. 
- HTML5 introduced a lot of new features when using HTML including **DOCTYPE declaration**, character encoding declaration using the `<meta>` element (to allow coverage of being able to use "pretty much" every character in the world), new semantic tags, and more media elements.

### What are **semantic tags**?
- **Semantic tags** in general are tags that clearly describe its meaning and use beyond functionality through its name. Unlike div elements and span elements which names are not descriptive or having any pertience to what they contain.
- Examples of semantic tags introduced in HTML5 include `<header>`, `<footer>`, and  `<section>` which respectively define a container for introductory content or navigational links, a container for footer content like copyright, ownership, and contact information, and a container for defining a "section" of a document which can be used for chapters on a page, for different news items. and any content that is needed to splited into a separate section. 

### What are media elements?
- Media elements is a descriptive term for tags used to display media content such as images, audio, and videos. 
- HTML5 introduces the `<audio>` and `<video>` element to embed audio and video content on a web page.


---

## CSS

### What is CSS?
- Cascading style sheet is a language used for styling HTML documents. CSS specifies certain rules to the layout and displaying of HTML elements and these rules are applied through key/value pairs.
- CSS use is to have a simple but powerful way of changing how HTML documents are rendered to make it more pleasant to look at.

### What does CSS syntax look like?
- CSS syntax can be broken down into selectors and declarations.
- **Selectors** defines the HTML element or elements you want to style.
- **Declarations** are the key/value pairs used to define the style you want to apply on the elements defined by the selector for styling

### Where can CSS styling be used?
- You can declare CSS styling by using external stylesheets, internally in the `<head>` section, and via inline styling which is inside of an HTML element tag.

### What happens when you try to style the same element in multiple declarations?
- If you style the same element via different locations for style declaration, then the CSS that is "closest to the element" is the one that overrides. This means that inline styling is prioritized over CSS styling in the head section, which is priortized over external style sheets. 
- It should be noted that only styling that conflicts like if a text was changed to be a different color in each way of styling will result in the color applied in the CSS closest. If there are styles that don't conflict then those changes are maintained.

### What is the CSS Box Model?
- In CSS, each HTML element in document is treated as a "box" that contains 4 different properties that can be styled independently of each other by CSS. 
- The 4 properties of the CSS box model are margins, borders, padding, and the content of the element

### What is margin?
- Margin is the outermost layer when shown in the box model. It is the property that creates the spacing area between an element and its neighboring elements to separate them. It is also the empty area that extends from the border area to the margin edge which is the defined margin-width. 

### What is padding?
- Padding is the layer of area between the border and the content of an element. The space is defined by the padding width and height given to the padding box.

### What is border?
- Border in the CSS Box Model is the layer that separates the content and padding from the margin layer. And it is the property that creates a border, an enclosing line around the padding and content. This enclosing line can be style to change not only in width, but also in color and type/style such as not a solid line but a dotted line. 

### What is content?
- Content is the layer that contains like text, images and other content bounded by the content edge. The content can be sized with the width and height property in CSS.

### What are CSS properties?
- CSS properties are characteristics whose value can define how a HTML element is styled, behaves, and displays in the browser. 

### Margin and Paddig Properties
- Both margin and padding are layers in the CSS Box Model and are properties that can be used in styling elements. Both properties used set units to alter their box widths. In which all 4 box widths can be listed as values for the property in variant order dependent on the number of values provided.
- 1 Value will be applied as the widths to all sides
- 2 Values will be applied as for top & bottom for the first value and the second value for left & right
- 3 Values will be applied: 1st value for top, 2nd value for left & right, and 3rd value for bottom
- 4 Values will be applied: top, right, bottom, and left
- Each side has their own property-value pair to adjust just one side, which are called margin-left, margin-top, margin-bottom, margin-right for margin and similar the saming naming scheme for padding (padding-top ...)

### What are examples of properties in CSS?
- Beyond margin, padding, and border there are other common properties that can be styled with CSS. This includes `display`, `position`, `color` and `text align`. 
- `display` can be changed to make an element display as inline or block element. By default the display value for an element is their original type meaning inline will be inline for `display` and same for block elements having block for `display`
- `position` determines where an element is displayed on the page and can be styled to be relative, absolute, and fixed from the default static value
- `color` allows you to change the color of an element. You can specify a color by a given name, hex values, rbg values, or hsl values
- `text align` allows us to change the alignment of text such as left/right/justified/center

### What are CSS selectors?
- **Selectors are how we choose which HTML element or elements to style**
- There are different types of selectors, some basic selectors are element selectors, id selectors, and class selectors.
- **Element selectors** select all instances of a specific HTML element
- **ID selectors** select elements by an ID attribute and the # symbol is used in front of the ID.
- **Class selectors** select eleemnts by the class assigned in the class attribute declared. Similar to ID selectors a symbol must be used in front of the identifier, for classes its the . symbol
- Overall ID selectors are better used for individual elements as IDs should be unique and shouldn't be the saem multiple elements. While class selectors are better used for groups of elements that all share the same class attribute. 
- You can combine the class selector with the element selector to select all instances of an element that has the specified class
- **Universal selectors** selects everything using just the * symbol.

```CSS
// Universal Selector
* {
    text-align: center;
    color: pink;
}

// Element Selector
p {
    text-align: center;
    color: blue;
}

// ID Selector (#)
#blackbox1 {
    text-align: center;
    color: black;
}

// Class Selector (.)
.dark-theme {
    text-align: center;
    color: grey;
}

// Class + Element Selector
p.dark-theme {
    text-align: left;
    color: pink;
}
```

### Other selectors for more advanced styling
- **Attribute selectors** are used to allow you to select elements that declare a specific attribute and utilizes [] notation to contain the specific attribute and also the value if provided.
```CSS
[title] {
    text-align: right;
    color: green;
}

[class="warning"] {
    color: red;
}
```
- **Grouping selectors** allows for grouping multiple selectors and applying the same style to all of them. All selectors are declared as normal, but are separated by commas
```CSS
h1, #parsing1, .curbs {
    text-align: right;
    color: white;
}
```
- **Child selectors** select specific elements that are direct children of another specific type of element using the '>' symbol.
- **Descendants selectors** select all the elements of a specified type nested inside the parent element.
```CSS
// Child Selector (>)
// All p elements that are direct children element of a div element.
div>p {
    text-align: justified;
    color: teal;
}

// Descendants Selector (space)
// All p elements nested inside div regardless if p is a direct child or not.
div p {
    text-align: left;
    color: violet;
}
```
- **Sibling selectors** select elements that directly are "siblings" but more specifically elements that follow another element and have the same parent element and uses the '~' symbol for the selector. 
```CSS
// All p elements following the div element and all p elements must share the same parent as the div element.
div~p {
    text-align: center;
    color: lightblue;
}
```
#### HTML example of last 3 selector types
- Note: an element **before** another element is **not consider** a sibling element. As defined sibling selector, matches all iterations of the second element, **that are following** the first element.
```HTML
<div id="div1">
    <p>I am a direct child and descendant of div1</p>
    <div id="div2">
        <p>I am a direct child and descendant of div2, and I am a descendant of div1</p>
    </div>
    <p>I am a direct child and descendant of div1, and I am a sibling to div2.</p>
</div>
<span>Just some element here, but I am a sibling of div1.</span>
<p> I am a sibling of div1</p>
```
### What to do if selectors conflict with each other?
- The "winning" or overruling CSS is determined by specificity, with ID selectors overriding any selector, Class selectors beat anything but ID, and element selectors our of the lowest priority. If none of the determinations lead to a decision, then the latest/last declaration declared "wins".

---

## JavaScript

### What is JS?
- JavaScript is a high-level programming language generally used for front-end development. JS has built-in support in all web browsers. 

### What are other features of JS?
- JS can be used as a server side language through NodeJS which is a JS runtime environment. JS is multi-paradigm which means it can do various styles of programming including object-oriented programming, procedural and functional programming. jS is also **loosely-typed** meaning that we don't need to define variables to use them.

### What specification does JS follow?
- JavaScript follows an official language specification called **ECMAScript** which is also used as an identifier for what JS version is being used like ES6, ES7. 

### How do you link JavaScript usage to HTML documents?
- HTML supports the use of JavaScript through the `<script>` tag, allowing for raw JS to be put in the HTML document or generally you will just link a path to an external JS using the same tag. The placement of the `<script>` tag in HTML can either go in the `<head>` section or at very bottom of the `<body>` section. Preferably the `<script>` tag for JS should go at the bottom of the `<body>` section to prevent errors from compiling JS scripts where certain elements accessed by scripts are not rendered prior to the script if the script is placed in the head. Along with that, if JS scripts are linked in the head then they are executed prior to the body section and it DOM construction, which can cause delays to loading content due to scripts running first. 

### What are features in JS syntax?
- Comments in JS are the same as Java.
- In JavaScript, values are represented through JavaScript literals, which are **fixed values** that a user can provide and this is not a variable but the **literal** value. JavaScript does contain keywords like many other programming languages which are reserved. Unlike Java, the use of semicolons to end of a line are optional.

### What are the different types of JavaScript literals?
- **Integer literals**, which are numeric values with no fractional parts and these values can be written in different bases (base 10, base 8, and base 16)
- **Floating-point literals**, which are also a subcategory with integer literals under the grouping of **numeric literals**, are numeric values can include fractional parts like decimal values and even exponent values are included as floating-point literals using the `e` to represent exponent in a value. 
- **String literals** are a sequence of zero or more characters, which are enclosed in either single quotes or double quotes. String literals can be concatenated using the `+` operator.
- **Array literals** are a list of elements contained in square brackets when written. If no value is passed into the brackets, then the array literal will create an empty array with zero length. 
- **Boolean literals** in JavaScript have only two literal values, which are `true` and `false`.
- **Object literals** are each a list of zero or more pairs of property names and associated values of an object, and this list is enclosed in curly brackets/braces '{}'. 
- **RegExp literal** is a pattern enclosed between slashes. (This one is most likely not on QC)

### How are variables defined/declared in JS?
- Variables in JS, are like in other programming languages, where variables are used to store data values and this is done using the `=` assignment operator.
- There are 3 ways to declare a variable in JS since the introduction of ES6. 
- The first is using the `var` keyword, this was the default and only declaration prior to ES6 and is less used due to the way it is scoped. `var` keyword allows us to declare a function-scoped or globally-scoped variables
- Second way is to use the `let` keyword similar to `var`, it is used to declare a variable but it is block-scoped rather than functional-scoped.
- Third way is to use the `const` keyword, which unlike `var` and `let`, is used to declare a variable that can not be reassigned after it was assigned once. And it shares the same scope as `let` variables. 

### What are data types used in JS?
- There are 7 major data types for JS variables:
    - **Number**, which includes integers and floating point 
    - **String**, which are sequence(collection) of characters
    - **Boolean**, truth or false
    - **Null**, absence of value
    - **Undefined**, value when a variable has not been assigned anything and only exists when a variable is declared.
    - **Object**, objects are collections of key/value pairs, and are written in {}.
    - **Symbol**, were introduced in ES6, though not used often, are objects with guaranteed to be uniqued when created and can unique properties that are hidden and prevents collision of other keys that might be added to an object. However, the same Symbol object wiil return if you provide a key when searching for a Symbol. 
- There are other data types like BigInt (used to hold large integers beyond regular numbers), NaN(not a number), which is a value returned when a math operation goes wrong.
- We can also identify a value's data type using the `typeof` keyword
- Objects can have subtypes like Arrays (which are like Java ones, but difference), which can hold any number of different data types and their length is not fixed, and functions are also objects but with more functionality.

### What are JS operators?
- JavaScript have most operators similar to Java like arithmetic, logic, assignment, comparison, and ternary operators. However a couple of differences are like the `===` operator which is only in JS and it compares types **AND** values, while regular `==` compares only values.
- The `==` operator in JS also performs type coercion, which is similar to type casting but can be different.
- Ternary operators in JS are used for shorthanding IF-ELSE statements `condition ? value1 : value2`

### How does control flow work in JS?
- For most of the syntax, JS has the same loops and if-else syntax, switch, etc. However things that are specific to JS include the **for-in** and **for-of**, which respectively are used to loop through an object(for-in) and an array (for-of).
```JavaScript
let person = {
    name: "Bob",
    age: 25
}
for (let key in person) {
    console.log(person[key]);
}

let arr = [12, "Susie", true, 0];
for (let value of arr) {
    console.log(value);
}
```
### What is type coercion?
- **Type coercion** is the process of converting a value from one data type to another. There two types of type coercion: explicit and implicit type coercion. 
- Explicit type coercion is when we explicitly specify the data type we want a value to change to. Which we can surround the value to be changed with the data type name and parentheses to enclose the value. 
- **Implicit type coercion** is where JS will assume and attempt to do the changing of a value if values aren't matching comparatively or used in a context where another data type is expected.
- While this does seem similarly to type casting, there are slight nuances that are different in that programming languages like Java there might be a need to use a class to do the conversion instead of simply saying the data type you want to change to.

### What is an example where type coercion is in action?
```JS
console.log("3" * 2); // it will return 6 since * is an arithmetic operator and strings aren't typically used to interact with arithmetic operators like *
console.log("3" + 2); // returns a string "32", while + is an arithmetic operator it is also used for concatenating so we in the context working with strings JS will convert the 2 into a string to concatenate it.
console.log(2 + "3" + 2); // here we will get "232" a string because again the + will have assumption of concatenation when working with strings
console.log(2 * "3" + 2); // returns 8, in terms precedence rules will still apply when multiple types of operators are used in this case * has higher precedence than + so when we do 2 * "3" we get a number 6 and then do 6 + 2 to get 8 and note that the "3" lost its string value due to type coercion
```

### What are truthy and falsy values?
- In JS, any expression or value can be evaluated as a boolean. Therefore different values can evaluate to either true or false otherwise known as truthy and falsy values to describe values if they aren't inherently booleans.
- There are 6 values/expression that return as false:
    - boolean: false
    - string: empty string 
    - undefined
    - null
    - NaN
    - 0
- We can say that any values that are not these will evaluate to true, but the exception to this is that only the number 1 evaluates to true and not 2 when actually compared with the real boolean value `true`

### How do functions work in JS?
- Functions are lines of code grouped together to be callable or usable anywhere in the program.
- In JS, functions are declared using the `function` keyword with the function's name and any parameters
- Unlike Java, there are no explicit return types, but we can still return values using the `return`.
- JS Functions can be used as objects and can be stored in variables.
- There are various types of functions besides the standard function:
    - **Anonymous functions**, which are functions without an identifier (no name)
    - **Arrow functions** which are like lambdas in Java, and they are "one time use" functions that can be written inline. The specific difference from Java is the usage of the `=>` operator for the "arrow"
    - **Callback functions** are functions that get passed into another function as a parameter, and then the original function executes the parameterized function. This can be used in writing asynchronous JS code, which is code that is not intended to follow or will perform in sequence with the normal source code that runs from top to bottom
    - **Closures** are nested functions that were used to achieve encapsulation in JS, where they can access their outer function's variables/arguments, but can't change them.

### What are the scopes in JS?
- JS has two major division of scopes which are global and local. Global scoped variables are accessible anywhere in the application, while local scoped variables are accessible only in their current location, which can be defined by {} curly braces.
- Local scope can be further divided into block scope and functional scope, where variables declared in a function are only accessible in that function and similarly variables declared in a block are only accessible in that block. 
- However one exception to this rule are `var`-declared variables which are functional scoped meaning that despite being declared in a block they can be accessible outside that block, where as block-scoped variables like using the `let`/`const` keyword are restricted to the block.  

### What is hoisting?
- Hoisting is mechanism in JS that works in the background, to specifically move variables and function declarations moved to the top of their scope before code that uses them executes. It should be noted for variables, `var` declared variables will be hoisted but not `let`/`const` declared variables and also the values assigned to them are not hoisted in general, so they all will contain undefined values until the actual line of assignment is executed.

### What is the **this** keyword?
- **this** keyword in JS can refer to many different things:
- It can refer to the global Object (the window object)
- It can be used in event handlers where it represents the HTML element that receives the event
- It can refer to an object involved in **object method binding** (like a constructor)

### What is JS prototypal inheritance?
- All JS objects have a prototype, which is implemented through the `__proto__` property, which is used to define inheritance in JS
- The top-level prototype of all objects is Object.prototype, this is the value that is assigned to `__proto__` by default. 

### How do JS classes work?
- Classes are consider a special type of function in JS, class declarations are done with the `class` keyword and the class name.
- You can also create classes with a class expression where you define a variable and then assign it an object with the `class` keyword
- Like in Java, classes can have constructors 

### What is DOM?
- DOM is the Document Object Model, which is created when JS is attached to the HTML document. The HTML document with all of its elements is converted into a usable JS object called `document` that can be manipulated/interacted in JS code. 
- The DOM is created to be like a "tree" where the root element `<html>` is the root of that tree and similarly all other HTML elements branches from the root. Each element in the HTML is an object in the DOM.

### What are different ways we can interact with HTML through DOM?
- In JS, we can access the DOM using the `document` object and we do operations like **DOM selection** and **DOM manipulation**.
- DOM selection is accessing the elements from HTML through the DOM object with functions like `.getElementById("idName")`
- DOM manipulation is changing the elements of the DOM during runtime with functions like `.setAttribute` and `.appendChild`.

### What are events?
- Events occur when user interaction takes place on the web page, such as clicking a button, hovering over something, or pressing a key on the keyboard. Events can be listened or detected using an **event handler** and through this we can perform some specific action. 
- Some commonly used events:
    - onclick - when a user clicks an element
    - ondblclick - when a user double clicks an element
    - onmouseover - when the mouse cursor goes over an element
    - onload - when the browser finishes loading the web page
    - onsubmit - when a form is submitted


### What are EventListeners?
- EventListener is what we used to detect events and perform some action. We can create/add an EventListener using the `addeventListener` function in JS.
- The syntax of the addEventListener function includes parameters for an event, a function, and the a boolean value called `useCapture`
    - event is the type of event being listened for
    - function is the function/code to run when the event happens
    - useCapture is the boolean value that is optional and is used to determine if the event handler should use **bubbling** or **capturing** for event propagation. This bubbling/capturing refers how to handle situations where multiple event handlers are listening to the same event (which one should run their function first). By default, the value is false (bubbling) if not specified.


### What is event propagation?
- Event propagation refers to the "traveling" of an event through all the DOM elements that it could be related to. (All nested elements from where event happened)
- In order to set whether we want an event to start from inner to outwards or outer to inwards (bubbling/capturing) we use the `useCapture` parameter to be either false/true, where false is the default if we don't specify.

### What is bubbling? Capturing?
- Bubbling is when an event travels back up the DOM through all the elements again, where we start with event listening/handling with the innermost element then go through and trigger each next outer element. 
- Capturing is when an event travel through the DOM, where outer elements will trigger their event listeners before inner elements all the way down to the innermost element that triggered the event. 

### How to stop propagation?
- We can stop/interrupt propagation by `event.stopPropagation()` or `event.stopImmediatePropagation()`, where the difference is that the immediate one will prevent other listeners at the same level from triggering.

### What is the Fetch API?
- The Fetch API is a modern and versatile means of sending asynchronous requests.
- We can use the fetch() method to return a **promise object**, and fetch() has parameters the URL for where the request is being handled and a configuration object which is optional but by default the fetch will be a GET request but the configuration object can change this. Configuration objects can define the request.
- A **promise object** is a value that **may not yet be available, but will be resolved in the future**. Once a promise is created, it cannot be canceled before it's resolved.

### What is flow for the Fetch API?
- The browser sends a request to the server and creates a promise object for the response. If the request fails, then the promise is resolved an the Fetch API will reject the promise object and an error code is returned as the response. If there is a successful response, the promise is returned in the response body.

### What are methods to access the response body?
- `response.json()` - parses the response as JSON and returns a JS object
- `response.text()` - returns the response as plain text
- `response.formData()` - returns the response as a form data object
- `response.blob()` - returns the response ats a BLOB (Binary Large Object)
- `response.arrayBuffer()` - returns the response as an ArrayBuffer (low level representation of binary data)

### What are methods that we can use upon fetching a request?
- We can use `.then()` to typically parse through incoming data, `.catch()` to catch errors and provide error handling code, and `.finally()` is used for anything you want to happen after the previous actions complete.

### What are keywords used for performing asynchronous actions?
- `async` is used to tell functions to return a promise when run instead of a value 
- `await` is used to make an asynchronous function pause until a promise is returned.

### What are timing events?
- Timing events are used to automate or run task after certain intervals of time. 
- `setTimeout` takes a function and delays it call for some milliseconds. `setTimeout(function, 2000)`
- `setInterval` takes a function and executes repetitively for intervals. `setInterval(function, 2000)`
- Like other functions in JS, these can be stored in variables, and we can use these variables as arguments to `clearTimeout()` and `clearInterval()` to cancel of execution of either timing event functions. 

### What is strict mode?
- Strict mode was introduced in ES5, and was to restrict JS code in terms not allowing undefined variables, any keywords cannot be used as variable names, and other niche properties of JS. To set JS into strict mode, we declare in the code `use strict` and this can be used to apply for all code in a global scope or function scoped if only written in the function.


### What are template literals?
- **Template literals** were introduced in ES6 and provides an easy way of creating **multiline strings** and easy way for **string interpolation**. Basically template literals are string literals, but are different in that they are created with backticks and not quotes, and also they allow us to embed expressions/values using the $ with the value in {} curly braces
- We can parse through template literals with a function using **tagged templates** which are functions that take in components of a template literal in the order of an array of string elements from the literal followed by each embedded value/expression in the literal as separate arguments. What we choose to do in the function that parses the template literal is up to what we want to perform with that data.

### What are default parameters?
- **Default parameters** allow us to have defined values for when a parameter of a function does not have a value provided to it when an argument is passed to that function. To use the default values we can choose to omit providing an argument for that parameter or pass in `undefined` as the argument for that parameter.
- Default values for parameters are not limited to literals, we can use other parameters as default values.

### What are spread and rest operators?
- The spread operator and rest parameter was introduced in ES6 and they both utilized the three consecutive dot notation as the operator. The spread operator provides us the ability to expand iterable objects like an array into multiple individual elements. With that we can use the spread operator to combine arrays given we use standard array literals and use the spread operator for both arrays as the value of the array.
- The rest parameter unlike the spread operator does not necessarily refer to splitting an iterable object, but used as a parameter inside a function to denote that there could be an indefinite number of parameters for a specific function. It should be noted that if the rest parameter is intended to be used, then it should be the last parameter listed in the parameter list for a function, otherwise an error will occur.


