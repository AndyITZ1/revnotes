# CSS

## What is CSS?
- CSS or Cascading Style Sheets is a way of styling or defining how HTML elements will appear on a display, paper, or other media
- CSS can help save the work of styling multiple Web pages at once
- Often Web pages will use external stylesheets which are in the form of CSS files
- Other advantages to using CSS
    - Beyond just being able to style multiple pages
    - You can also structure web pages to display differently for different devices and screen sizes (mobile vs PC)
    - Rather than having style content be written in the HTML document this can be done in a separate CSS file

## Why CSS rather than in HTML?
- HTML was never intended to contain tags for formatting the web page
    - rather HTML is used to describe the content of the web page
- HTML 3.2 introduced new tags like `<font>` and other color attributes which allow for developers to format their web pages in HTML, but this created a longer process for developers when building multiple web pages for large websites and having to format each page 
- CSS removed the necessity to style formatting inside an HTML document, where CSS allows for formatting to be done externally in a CSS file

## CSS Example
```CSS
body {
    background-color: lightblue;
}

h1 {
    color: white;
    text-align: center;
}

p {
    font-family: verdana;
    font-size: 20px;
}
```
- For formatting HTML elements, you can style specifically all of one type of element one way as shown all `<h1>` elements will be colored white and their text aligned as center.
- Another thing is that you can list HTML elements to style one way by writing them as a comma-separated list before assigning the formatting
```CSS
h1, h2, h3 {
    color: white
}
```

## Styling HTML with CSS
- CSS/formatting can be added to HTML 3 different ways:
    - Inline: by using the "style" attribute in HTML elements
    - Internal: Using the `<style>` element in the `<head>` section of the document
    - External: Using the `<link>` element to link an external CSS file


## Inline CSS
- Inline CSS allows developers to write formatting alongside HTML elements in the `<body>` section.
- This also allows formatting a **single HTML element uniquely**
- This requires the use of the 'style' attribute in each HTML element being formatted.
### Example Code
```HTML
<h1 style="color: blue;">This is a Blue Heading</h1>
``` 
### Display
<h1 style="color: blue;">This is a Blue Heading</h1>

## Internal CSS
- Internal CSS is done using the `<style>` element
- This is always done at the top of the HTML document in the `<head>` section
```HTML
<!DOCtype html>
<html>
<head>
    <style>
        h1 {
            color: blue;
        }
        p {
            color: grey;
        }
    </style>
</head>
<body>
    <h1> This is blue. </h1>
    <p> This is grey. </p>
</body>
</html>
```
<!DOCtype html>
<html>
<head>
    <style>
        h1 {
            color: blue;
        }
        p {
            color: grey;
        }
    </style>
</head>
<body>
    <h1> This is blue. </h1>
    <p> This is grey. </p>
</body>
</html>

--- 
## External CSS
- Unlike Inline and Internal CSS, External CSS is using an external CSS file that is linked inside the HTML document to be formatted
- No styling formatting code is written in the HTML document
- Often this offers a way developers can format multiple Web pages at once.
    - You can the way an entire website looks, by changing one file
- To link/use the external CSS file, you have to add a `<link>` element to access it from the HTML document
```HTML
<head>
    <link rel="stylesheet" href="styles.css">
</head>
```
- As shown here, 'href' attribute is the same as in the `<a>` element where its used to provide URL/path and 'rel' attribute is to identify what kind of relationship is between the external resource and the HTML document
    - `<link>` element isn't just used to connect to stylesheets but also to things like favicons or external fonts sources
- `<link>` element is another HTML element that is self-closing and doesn't contain anything

## CSS Selectors
- Majority of what is shown above is written in HTML 
- But what is used inside of CSS files, **SELECTORS** are!
- Selectors are patterns used to pick the HTML elements you want to style 

### Basic selectors
- More often you just want to format one type of element a certain way, so you can simply just write that tag identifier as the selector
`p`, `h1`, `body`
- '*' is used as a selector to select all elements 
- If you want to select multiple elements and format them the same way you just list the elements in a comma-separated list
```CSS
p, h1, body {}

// VS

p {}
h1 {}
body{}
```

## Class/ID selectors
- Often elements may have classes or ids assigned to them to kind categorized them to have a certain use that may be different from another element with the same tag but not same class/id
- To pick out these elements you can use their class/id as a selector along with the element name (this isn't necessary)
```CSS
.example {} // refers to elements with the class "example"
#exam {} refers to elements with the id "exam"

p.example {} // refers to all p elements with the class "example"
p#exam {} // refers to all p elements with the id "exam"
```

## Nested Selectors/ Chain Selectors
- Elements in HTML can be nested inside each other given the way we want to describe the content shown
- So to select elements inside other elements we can use a selector like:
` div p ` which refers to all p elements inside/contained in a div element. We can also use `div > p` which refers to all `p` elements whose parent element is a `div` element.
    - The difference between the two selectors is the latter `div > p` is referring to a direct relationship so if a `p` element is inside a `span` element which is inside a `div` element then that selector wouldn't work as the `p` element should be a child element of the `div` element
    - However the former selector `div p` would work as the `p` element is technically inside a `div` element
- Other than that we can also select elements that immediately follow another element in the HTML document (follow here doesn't mean nested but the next element at the same level as the previous)
    - Here we would use `div + p` so all `p` elements that directly follow a `div` element. Again here a direct relationship is mentioned so this means that there can't be another element in between the `div` and `p` at the same level

## CSS Cont'd
- There are more different selectors that can handle unique cases
- Note: There are no selectors for cases like selecting parent eleemnts, siblings of parents or children of parent siblings

