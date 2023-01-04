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
- JavaScript is a high-level programming language generally used for front