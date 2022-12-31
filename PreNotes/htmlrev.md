# HTML
## What is HTML?
- HTML stands for Hyper Text Markup Language
- **HTML** describes the structure of Web pages using markup
- **HTML** elements are the building blocks of **HTML** pages
- HTML elements are represented by tags

### What are Tags?
- Tags defined HTML elements
- Every HTML element has at least a tag to create/render it on an HTML page
- Example 'p' tag allows defining a paragraph element
- Usually common HTML elements have an **opening** and **closing** tag
    - These differ with opening just having the tag label by itself. Ex: `<p>`
    - and the closing have a forward slash ('/') appended in front of the label. Ex: `</p>`

## Rendering of an HTML Page
- When a browser renders/reads an HTML page, the contents of the body element are shown to the client / end user accessing the Web page from the browser
- As for what the browser reads and utilizes, it reads each tag and defines/uses elements to display content in a certain way based on tag-specifics
- Browsers will never display HTML tags, but use them to render the content

## Understanding from an Example
```HTML
<!DOCTYPE html>
<html>
    <head>
        <title>Page Title</title>
    </head>
    <body>

        <h1>My First Heading</h1>
        <p>My first paragraph.</p>

    </body>
</html> 
```
- `<!DOCTYPE html>` tag is always declared at the beginning of the HTML page
    - This tag is used to define/declare that this HTML document will follow a specific version of HTML guidelines
    - For this specific tag, this is used to define this document is an HTML5 document
- `<html>` element is the root of an HTML page / starting point of HTML page
    - any elements within it are utilized in defining the HTML page

### Two main sections in an HTML document 
- `<head>`
    - in this section which is defined by the head element, all the metadata stuff relevant to a page is defined and initialized here
    - `<title>` element defines the title of the HTML page 
        - you can usually see this type in the browser's title bar or in the page's tab
    - Other elements you might see include:
        - `<link>`
            - This allows for linking other resources such as stylesheets (CSS)
        - `<style>`
            - This provides internal styling of HTML elements instead of using external CSS files
        - `<meta>`
            - This tag can be used to set various different metadata attributes for an HTML page including (character sets, author, keywords, description, viewport settings)
- `<body>`
    - This is viewable page section and final half to an HTML document.
    - Majority variety of tags/elements are often used in this section.
        - Text-specific tags like `<strong>`, `<p>`, `<h1>`
            - Which all change text styling or way text appears
        - Media tags like `<img>` and `<iframe>`
            - used to display images and other media content
        - Table tags like th, td, tr, and more

## Continuing the above example 
- `<h1>` element defines a large heading
    - other headings do exist and decrease in size with higher number (h2 < h1)
    - all the way up to h6
- `<p>` element defines a paragraph which is the default text with no formatting


## HTML Links - Hyperlinks
- HTML links are hyperlinks
- Clicking on one lets you jump to another web page/document
- Upon hovering links, your cursor will change to a little hand symbol to indicate this is a clickable link (note a link doesn't have to be always a URL but can be regular text, images, and other HTML elements)

### Creating links in HTML
- To make a link, you would use the anchor tag otherwise known as `<a>` element
```HTML
<a href="url"> link text </a>
```
- In this syntax, the URL or document path you want to link/jump to is placed in the href attribute inside the starting `<a>` tag
- *Any piece of text or elements situated in between the `<a>` tags become a hyperlink linking to the page that is designated in the 'href' attribute
    - Note that there are restrictions in what can be put in between anchor tags due to HTML guidelines, elements like `<div>` cannot be used inside `<a>` (This is due to the block and inline conflict)

## HTML Images
- Images can be placed in HTML via the `<img>` tag
- Unlike most tags, the `<img>` tag doesn't have a closing tag
    - and so it doesn't have anything to contain
- To use it the image URL/path is placed in the 'src' attribute inside the `<img>` tag
    - Note that contain meaning "situated between two tags" and inside the tag is referring to attributes that are always in the "starting" tag
```HTML
<img src="img_url.png" alt="URL Image">
```
- Another thing to note is the 'alt' attribute this allows developers to put in a description/alternative image replacement when an image can't render. This then shows that description of the image instead of the actual image.

## HTML Lists
- There are two types of lists in HTML
- Unordered Lists
- Ordered Lists
- For putting items into the lists, use `<li>` tags to define list items

### Unordered Lists
- Created using `<ul>` tags and define an unordered list
- Unordered lists in HTML are visibly displayed to users as bulleted lists
```HTML
<ul>
    <li>Item C</li>
    <li>Item E</li>
    <li>Item A</li>
</ul>
```
### Displayed:
<ul>
    <li>Item C</li>
    <li>Item E</li>
    <li>Item A</li>
</ul>

### Ordered Lists
- Creating using `<ol>` tags
- Shown visibly as lists with (numerical/alphabetical ordered bullets)
```HTML
<ol>
    <li>Item C</li>
    <li>Item E</li>
    <li>Item A</li>
</ol>
```
### Displayed
<ol>
    <li>Item C</li>
    <li>Item E</li>
    <li>Item A</li>
</ol>