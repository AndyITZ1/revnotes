# Week 5

## AWS/RDS

### What is cloud computing?
- Cloud computing is the practice of using a network of remote servers hosted on the Internet to store, manage, and process data/information, rather than on your local computer

### What is the cloud?
- The cloud refers to a network of remote servers that are accessed over the Internet, along with the software and databases that run on those servers. Many companies provide their own "cloud" or group of remote servers that will provide **cloud computing services**.

### What is AWS?
- Amazon Web Services (AWS) is a cloud service provider that hosts a collection of hundreds of cloud computing services that provide the building blocks for IT Infrastructure.
- To use AWS, individuals or companies must pay a fee, but they only pay for what they use so this is cheaper than trying to buy all the hardware and software needed to perform the same actions as AWS.

### What are benefits of using AWS?
- You only pay for what services you use
- You can **easily scale** certain services like RDS or EC2 to have more or less storage (highly scalable)
- AWS is highly available meaning that you can have your services be executed in various places in the world that have AWS servers and are available for those services. 

### What are some services provided by AWS?
- AWS offers over 200 fully featured services and some them that we may use are:
    - S3 or Simple Storage Service, is a service that provides **object storage repositories** up to 5000+ TB, which can be good for static data storage.
    - EC2 or Elastic Cloud Compute is a service that provides scalable computing capacity in the AWS Cloud. This allows user to launch virtual servers, configure security and networking, and deploy applications without needing their own hardware upfront and this can be all managed from a dashboard on the AWS platform. 
    - Security Groups, these are like a firewall for instances of AWS services, which can restrict traffic in a service by IP, protocols, or ports.

### What is RDS?
- RDS, which is the Relational Database Service, which creates a virtual, scalable relational database. Through this service we can have an environment that can host a database and has support for different types of RDBMS, and multiple people can connect to the database using this service.

---
## React Code/NPM commands
- To create a React app (w/ TypeScript), all the folders necessary for React application we use the following command:
```
npx create-react-app app-name --template typescript
```
- To install any dependencies we use the npm install comand and the dependencies' names
```
// Both lines are installing packages
npm install typescript react-router-dom 
npm i react-redux redux
```
- One neat thing about `npm install` is that if we have dependencies or packages that are not yet installed and it is listed in the `package.json` file, then the `npm install` command will automatically install those packages/dependencies as well as still installing the package(s) you explicitly wrote.
- To start your React application we use the start command
```
npm start
```
```
// This is not the start command, read BELOW!
npm run build
```
- To run the build field from the `package.json` file, which contains how your application will be structured file/folder-wise when deployed
- IT SHOULD BE NOTED, that every command excluding `npx` one should be executed/ran in the React app's folder (that was created using `npx`). 
---
## React/TypeScript/JS

### What is NodeJS?
- **NodeJS** is an open-source cross-platform runtime environment used to execute JavaScript code outside of a web browser. 
- Node allows for users to develop server-side applications with JS like APIs interact with client-side views like displaying data retrieve from databases on a web page. Vice versa we can use NodeJS to collect form data from a web page and let it be used in server-side operations like manipulating or storing it in a database.
- **NodeJS** also provides a library of various JavaScript modules which help simplify the development of web applications.

### What is Node Package Manager (npm)?
- npm or Node Package Manager is a built-in software package manager that comes with NodeJS and is utilized by developers to share software in the form of code packages. Users can use npm to download and install frameworks and libraries for development stored in npm's software registry using specific npm or npx commands in a command line client. 
- **React and its dependencies are installed using npm and ran on a NodeJS environment, which is why we need both of them when using React.**

### What is the package.json file?
- **package.json** is a file usually found in the project root and the file itself is used to give information to npm that allows it to identify the project and handle project dependencies. In general, it contains **metadata** relevant to the project, such as project description, project verision, licenses, the author, any scripts, project name, the main entry point, **dependencies** and **devdependencies**.
- **dependencies** section of the file contains the list of packages/modules installed using npm that are required to run the project.
- **devDependencies** section, contains a list of packages/modules that are required only for development and these are usually install only on the developer's machine. So they not be run for production build.


### What is React?
- **React** is lightweight JS library created by Facebook and it is use for creating front end user interfaces in the form of **Single Page Applications**. A React application is made up of **components**, which are different pieces that move in and out to create the view, which is what the user sees. We can think of components as building blocks for a web page. For single page applications this is in the sense that components will be removed and added or replace with others to do different functionalities on a single web page. 
- React **does not utilize HTML files**, but rather is written within JSX or TSX files using JSX/TSX which is a markup language specific to React being used with JavaScript/TypeScript. JSX and TSX is similar and mostly looks like HTML, but has some subtle syntatical differences. One being that the `class` attribute in HTML is written or used in JSX/TSX as `className`.
- **React components** follow a specific design pattern, in which all data for a component is **stored in one file** and each component is **separated by its concerns or functionalities**. React components each **create their own view with JSX or TSX** instead of HTML. 

### What are disadvantages to using React?
- React is updated frequently, so **concerns about forward compatibility** should be taken into account when version changes. This does not just refer to syntax changes in React but also how reliable are sources if the React used in the sources are outdated.
- React while being flexible, it **can have many moving parts in a bigger React application** meaning that to understand how an application works we have to understand the anatomy of it and how everything works together.

### What is the React Virtual DOM?
- When rendering components from a React application, we interject these components into the root HTML element which is what is displayed on our page. However this process, requires that we manipulate the DOM (Document Object Model) which is the tree layout structure that shows how an HTML page is setup and is usable to JS/TS through the `document` object. When we manipulate the DOM it can be **time consuming**, **resource intensive**, and overall we have to re-render the DOM, which means we basically reload all pieces of the DOM with each edit to the DOM. This results in a slow process issue as doing one thing to edit DOM results in the whole DOM being rebuilt or reloaded for at least the same elements and the addition of one change. 
- To work around the inefficiency of manipulating the DOM, React has a corresponding **virtual DOM** for every DOM object. A **virtual DOM** object has the same properties as the real DOM object, but it lacks the power to directly change what's on the screen. However this is the benefit, as manipulating the virtual DOM is much faster and nothing is drawn onscreen. The reason why we want to edit the virtual DOM object is that we want to record all the changes and update when rendering a JSX element into it. After we record the change, a pre-update version of the virtual DOM is used to compare with the newly changed virtual DOM, this lets React know what DOM objects have changed (this is called **diffing**). With this information, React can update only the necessary parts of the actual DOM to reflect the changes from adding a JSX element instead of having to rebuild or reload every DOM object. In terms, a virtual DOM is a lightweight copy of the actual DOM that allows recording of changes made to a DOM by adding a JSX element. The actual updating of the real DOM is only done once React figures out the necessary changes that need to be made to the DOM.

### What is TSX (TypeScript XML)?
- TypeScript XML or TSX is used to create the template or the view for React components. It looks like HTML when written, but has it owns syntax. TSX code is what is injected into the virtual DOM, and then displayed on the browser. 
- For our TSX elements that need to be returned for one component to be displayed, we wrap all the "returned" elements in one element. The reason why we do this is that when React tries to create all the TSX elements for a component it expects to only create one element and not multiple at the same level. Which can cause a React syntax error to pop up. To avoid this error we wrap all TSX elements into one element and this element can be like a div or a React.Fragment. 
- Depending on whether you use a div or React.Fragment, you may add an extra DOM element (div).
- **Unlike regular HTML, JSX/TSX HTML (really just call it TSX/JSX no need HTML) allows for custom attributes (attributes with whatever name)**
    - While this is true for the most part. We can have "custom attributes" in HTML, but the restriction in HTML is that you have to prefix `data-` before the custom name.

### What is a single page application (SPA)?
- A SPA is web application that fits on a single page in the browser. This means that with a single page load the browser will retrieve all the necessary JavaScript/TS, HTML, and CSS code. When we **navigate** between pages, the content of the page is changed however this is being without refreshing the whole page.
- A reason to use SPAs is that we can use it to build responsive web applications, examples of SPAs include Gmail, Facebook, and Trello. 

### What are the advantages of SPAs?
-  SPAs are fast and responsive. They (SPAs) only update the required content instead of the whole page. Which means that only data is truly being sent back and forth in the background and this significantly improves the website's speed. It should be noted that all the code like JS/HTML/CSS is retrieved with one page load which is the initial page load, so it will never go away when navigating.
- SPAs have **caching capabilities**. When a SPA sends a request to the server it **caches all the received data locally**. With this the SPA can reuse data and even work offline or in situations where the user has poor connectivity. The local data can be synchronized later with the server when connection has improved.

### What are the disadvantages of SPAs?
- While performance is overall better, more data is front loaded meaning that the first page load can be slower as it has to received all the data first.
- SPAs do not perform well with search engine optimizations or SEOs, which is the process improving traffic to a website or web page from search engines. Simply we can see SEOs, where certain websites or pages appear at the top of search results compare to other ones. 
- SPAs have some increased vulnerabilities to **Cross-Site Scripting (XSS)** attacks. Where XSS attacks occur when a third party inserts code into JS during the page load, to perform some malicious operation. 

 ---
### What is the React application architecture comprised of?
- When creating a React application from the npx command, the folder structure of a React is made up of:
- A `node_modules` folder which holds all the dependencies a React app needs. 
- A `public` folder which is a great place to store assets such as images and favicons that maybe utilized in the application.
- A `src` (source) folder which is where all the source code and important files for the application will be stored. This includes the React components that we will make for the application, the App.tsx, App.css, and any other files that help structure the application. 

### Where do we render our main application in a React application?
- The App.tsx file is where we render our main application, we can input components here to be displayed in the view, and we can specify routes to components which are URL endpoints from which a component is accessible from. 

### Where can we apply global styling across a React application?
- Similar to how the App.tsx acts as central place for components to be used and display a view, the **App.css** is the stylesheet we can use to apply a style across the whole React application. 
---
### What are React components and how are they designed?
- **Components** are essentially a "section" of a webpage that can be displayed or removed by a React application. Examples of components are like the newsfeed section, the ads, the sidebar in Facebook. Each of those can be shown or removed from the view and this is dependent on whether the component for is being used or not. 
- Components can communicate with each other to create a larger application. Design-wise these components should follow the **single responsibilty principle**, where a component should have responsibility over a single part of application functionality. This means that the component should not be handling or performing various different tasks when utilized. It should be focus on a single functionality of the application that is to be implemented. 
- Components are designed to be reusable pieces of the user interfaces, which overall is helpful in maintainability and code reusability of the source code. 
- **Overall for a React component to work it has to return/render a JSX/TSX view of some type.**
- React components are really just ES6 classes (that extends React.Component) and functions (that return a view made in JSX/TSX) 

### How does immutability in React help?
- Immutability in things like React component help prevent from state data from being changed directly by other components, which overall helps us create pure components and allow complex features to become easier to implement.

### What are two types of components in React?
- There are two types of components that can be used to build the React application, class components and function components.

### What is a class component?
- A class-based component is simply a ES6 class which can be either a JavaScript or TypeScript class depending which language is used. And that class specifically extends `React.Component` which inherits the properties needed to make a class-component. 
- Class components can have variables or maintains its own data with **state**, can accept **props** which can be used in a constructor() function, and must have have a render() function which returns a React element which is written in JSX/TSX. 

```TS
import React, {Component} from "react";

export class SomeComponent extends React.Component<any, any> {

    constructor(props: any) {
        super(props);

        this.state = {
            color: props.color,
            animal: props.animal
        };
    }

    render() {
        return (
            <div>
                <p>JSX/TSX here</p>
            </div>
        )
    }
}

```
### What is the lifecycle of a class component?
- React class components have a lifecycle, when they are created. Each step of the lifecycle can be accessed in the form of methods designed for class components. 
- The lifecycle consist of mounting, updating and unmounting of a class component. 
- The methods used in the lifecycle are:
    - `constructor`, which is primarily used to initialize data in the component, this means the state object.
    - `componentDidMount` is used for grabbing some data after the page loads.
    - `componentDidUpdate` allows use to executed when a component updates its view.
    - `componentWillUnmount` is used for cleanup when the component leaves the view.

### What is a function component?
- A function component is a written as a function in JS/TS. Prior to React version 16.8, function components were limited in what they could do compare to class components. This meant that most React application built prior used mainly class components and sometimes function components. One feature that was not a part of function components then, were the ability to have state. With the introduction of **hooks** in React 16.8, function components can now have state and other features that makes it capable of doing the same thing as class components now. 
- Today, function components are used more often because they are more simple, flexible, and straightforward to write compared to class components. Along with that, using hooks makes function components powerful in being able to do the same things as a class component such as having states. 
- Unlike class components, which require extending React.Component to make a class an actual valid component. Functions can be valid React components as long as they return JSX/TSX code which is what is also return in class components by the render() method.

```TS
import React from "react";

const SomeComponent: React.FC<any> = (props: any) => {
    const [state, setState] = useState("");

    return (
        <div>
            <p>JSX/TSX here</p>
        </div>
    )
}


```
### What is data binding?
- Data binding is the process of connecting the view element or user interface, with the data which populates it from the component. Specifically in React we have one-way data binding, which means that if we change data in the component's logic it will be reflected in the view or if we change data in the view then it would be reflected in the component's logic. 
- To actually do data binding, we put data we stored in a component, this can be from the state or a variable inside curly braces into the JSX/TSX we are returning which will be render as the view.
- The logic of the syntax in data binding is that the curly braces allows us to utilized JS/TS code inside of JSX and TSX, and data binding allows us to see data in a component into a view.

### What is two way binding?
- Two way binding is essentially when we change data in a component, we can see the change be reflected in the view and also if we change the same data in the view, then it should be reflected in the component.

- The biggest difference between one-way and two-way data binding, is that one-way data binding only performs one of the two actions meaning we can use the data in the component's logic to be shown into the view, but data won't be change in the component logic if changed in the view. 

- While React, does not implement two-way binding directly, we can achieve it through using event handlers. Where we can still data bind with curly braces the data from a component in JS/TS into the JSX/TSX code returned for the rendering the view. And with the view component we can have an event handler for when it changes that would manipulate the data in the component if we change it in the view. The result of this is now the data is synchronized on both ends meaning if one change is done on either side it will be reflected in the other side immediately.


### What are nested components?
- React allows for components to be nested inside one another which can create an implicit parent-child relationship between the outer and inner components. This eventually leads to concepts of being able to pass data or state from a parent to a child component as props that can be used but is immutable. 

### What are hooks?
- Hooks are functions in React that allow you to **"hook" into React state and lifecycle methods from within functional components.**
- Hooks only work functin components and not class components.
- Hooks cannot be used inside of other hooks, however it can be called from custom hooks. 
- Hooks should be called for the top level of a React component, as the component will know what order hooks will be called, if we decided to call hooks elsewhere (except custom hooks), React would failed to associate local states with the expected hook order. This can lead to bugs.
- **With hooks we can manage state in function components (useState).**

### What are example of hooks?
- Common hooks used are useState and useEffect:
    - **useState** allows you to store and change state inside a function component which is equivalent to the state object in a class component
        - To use **useState** we have to declare a state variable and a mutator inside of square brackets, then we assign **useState** and a value to initialize state to a default value. 
        - In this syntax, the state variable is what holds the data and the mutator is a function that we can use to change that data stored.
        - Another thing about **useState** is that the state variable doesn't have to be an object like in class components meaning it can just hold a single primitive value. 
    - **useEffect** allows you to perform some action during an application's life. This action or basically a callback function is run based on an interval. 
        - This interval can be decided in 3 different situations:
            1. The callback function is executed  **after every render** which occurs when a page loads in a component's view and this view can change or re-render when state(s) are changed.
            2. **useEffect** hook has a second parameter which allows for a dependency array. If this array is empty (has no dependencies), then the callback function is executed once, which is after the initial page load of the component's view. That means also that if any states are changed and there is re-rendering, then still the callback function will not be called. **As it is not dependent on any state.**
            3. If the **dependency array** has a dependency or multiple dependencies, then when those state changes (which does re-render). then the callback function will be after those state changes. **Clarification** the callback will only be executed when those state changes, if a state not listed as a dependency is called and the re-render happens the **callback will NOT be executed** as it is dependent on the states listed in the array. 
        - This hook is useful watching for state changes to perform some logic and this is similar to event listeners in event handling.
    - **useContext** is another hook that can be used in function components. In summary we can use it to help get state or values from another component. It's used with the Context API and used in situations where a component is deeply nested in a chain of nested components to help get the state of an ancestor component to that deeply nested component instead of having to pass that state as a prop (prop drilling) through every in between component, since not every component needs that specific state.

### What are props (React)?
- A prop is an object with variables that can be used to pass data from a parent component to a child component. We can include props we want to pass down in the child component's element tag.
- Props sent to a child component are typically the state object of a parent component. Due to that, props are designed to be immutable to prevent a parent component's state from being changed by a child component. 

### What is the difference between state and prop?
- State is the data/information about a component that is stored within a component and this is what we send from the parent component as "props" for the child component. Props is the data/information coming into a component from another component (parent) or outside source. We can defined props for a child component via putting data binding the data in attributes in the child component's opening tag.
- **State is the current state of the component, while Props is passed into the component.**


### How can you break apart the prop object passed into a component into individual variables?
- **Destructuring** is a JS/TS expression that makes it possible to unpack properties from objects into individual variables. 
- We can do the same with prop objects as they are objects and so each piece of data passed to child component from a parent can be assign to an individual variable.


```JS
const [firstName, lastName] = personNameObject;
// We can now access a person's first name and last name separately/individually with the variables firstName and lastName.
```
### How does data flow in React?
- React's data flows one way, from the top down. This can be seen when we are passing data from parent component to child component. However we can work around this using a process known as "lifting state up". 

### What is "lifting state up"?
- "Lifting state up" is a way to update a state which is shared and utilized by multiple components. With React data flows top down from parent to child in the form of states and props. However when we want to have a state that has the same information across multiple components that utilizes it, we need the parent holding the state, to have the state updated to reflect any possible changes to the state that happens in a child component. While props are immutable meaning a child cannot change a props object it receive which inherently would affect a parent's state, we can pass functions as a prop object. This function passed in can have code that edits the state stored in the parent, which lifts the state up from the child to parent component.
- An example of how we would use lifting state is the shopping cart of an e-commerce website. We can have two components one to add items to the cart and one to checkout the cart. In terms of state we are referring to the list of items in a cart. We need to pass state to each of these component as each component does need the list state to perform its functionality. And they both should see the same list. So when we go to add an item to the cart, the add component should be able to edit this list state. So we can pass a special mutator function to edit the state as a prop for the add component. For the checkout component we only need to pass it a just the list state and no necessary mutator function. Everytime we add to the cart the list should be updated and be ready for the checkout component to process everything in the list. So we are lifting state from the add component to the parent component holding the list state.
- Lifting state can cause complications for React applications in that lifting state is trying to move a state so it's accessible to many state, but when that state is nested through many components then the process of lifting state can really make the application become more complicated in terms of now having to move state through various components.
    - This could be that we need to move that state into components that don't need it to just pass it on and similarly moving state to a commonpoint where that common point is a component that doesn't serve the purpose of holding that state can cause flaws in following design principles like single responsiblity. 

### What are states (React)?
- State objects is how we store information/data within a component this similar to variables in a class. But the difference is that State objects are easily passable to child components. 
- States are encapsulated by components which means they can't be directly accessed or manipulated by external components to the component they are contained in. 
- With that, in class components **states** are mutable in a component by using the constructor method or declaring a field called state, and to change the state we use `this.setState()`.
- For function components, they don't have states by themselves but can gain states through the use the useState hook.
- While it is true **states** are mutable, **states** are to be treated "immutable" in that we shouldn't be changing state directly for any reason and that it only updates based on certain conditions based on rendering and input. 

### What are events in React?
- Events in React are very similar to ones utilized in regular HTML, however there are slight differences between HTML ones. Events in general are scenarios that occur because some action occurring and for the most part this action it is incurred by end users. Examples of this include clicking a button, hovering over an element, and keyboard input.
- So what are differences:
    - React events are **named using camelCase**, whereas in HTML they are all lowercase
        - React: `onClick` vs HTML: `onclick`
    - In JSX/TSX you pass just the function name, however in HTML you use strings with the function call
        - React: `={funcName}` vs HTML: `="funcName()"`
    

### What are list and keys?
- If we want to render a collection of JSX elements, we could loop the array of items that we wanted to create or pass to as part of a JSX element. We can do this looping through the `.map()` function which then we perform some functionality to create each JSX element with the data from the array/list item. As per React, we would also assign a key or  **keys** which are unique/special string attributes to identify uniquely each JSX element in the collection. This identification is helpful if we wanted to know what JSX element have been changed, added, or removed. For deciding what should be a key, it should be either the item in the list or it can be a property of it (if its an object) that uniquely identifies it. 

### What is routing in React?
- Routing allows for the navigation from one view to another, by changing which components are displayed on the single page in React. Routing essentially is what helps emulate the experience of browsing multiple pages to the end user, when on a single page application where only one page is actually created. 
- Since routing does involve changing which components are visible in the view, we can assign and determine which components by using URLs in the Route elements and passing the specific component to be render in view to the Route element.
- To perform or use routing in React we use the react router.
- The react router or React Router DOM is a dependency that provides several solutions for creating a router in React applications. 
- From this dependency we can import BrowserRouter which is a JSX element and component that is use to set up routing. Inside of the BrowserRouter component we can nest Routes components and in Routes we can have multiple Route components. 
    - `BrowserRouter` is the specific router we will used to set up routing
        - This is meant for the web, whereas `NativeRouter` is for mobile
    - `Routes` is where we will hold all our routes for our application.
        - Note: We can have multiple `Routes` components if we consider that we may want to render different view/content in specific parts of the web page but the components in view are not gonna overlap. Think as sidebar content and then we have the main content. 
    - `Route` is the component where we will have our specific path or route and there's one `Route` for every route in our application. 
        - We can add the specific component(s) to show up at a specific route by using the `element` attribute to pass in the component we want to render in view.

### What are the two ways to create HTTP requests in React?
-  We can use either the **Fetch API** or **Axios** to create HTTP requests in React.

### What is Axios?
- Axios is a popular promise-based library used with NodeJS and your browser to make and send asynchronous HTTP requests to REST endpoints.
- Axios is supported by most modern browsers and comes with features 
    - like being able to automatically parse JSON response data, 
    - has built-in protection again cross-site request forgery,
    - it can intercept and transform request and response data
    - and has better error handling.

### What are reasons to use Axios over Fetch API?
- Axios can cancel, timeout, and interrupt HTTP requests, which Fetch cannot do that easily. Axios automatically translates request/response bodies to and from JSON, whereas we have to explicitly use the `parse()` and `stringify()` to do the same with data being received/sent.

```TS
// const axios = require('axios');
// Making an Axios Request
// HTTP Request made using Axios functions will return Promise objects
// Hence the then() and catch()

// GET 
axios.get('urlHere')
.then((res) => console.log(res))
.catch((err) => console.log(err));

// POST
axios.post('urlHere', {
    data: 7,
    object: 8
})
.then((res) => console.log(res))
.catch((err) => console.log(err));
```


### What is problem with Application State Management in React?
- We know that all data in React flows only one way. So this can be tricky to try sharing **state** among multiple components.
    - A state is a built-in React object that lets us store data in a component that we can send to other components. 
- We can resolve this issue with 3 possible solutions:
    1. **Lifting State**, this can become complicated quickly 
    2. **React Context API**, this is a built-in centralized data store for React (useContext hook)
    3. **Using the Flux Design Pattern through React Redux**
- The advantages of using Flux Design Pattern include:
    - Ability to manage state in one centralized place, this can be one file that will store all the application's states, and no longer store state in each individual component. The file will be a globally accessible place to get data/state.
    - We can easily handle more complex data flows, as now we only have to pull and change data from the same place instead of navigating between different components like with **lifting state** and **prop drilling**
    - We have **more intuitive communication** between components and non-hierarchical data
    - Leveraging/utilizing unidirectional as an advantage and not an obstacle.

### What is conditional rendering?
- **Conditional rendering** is just applying JS/TS conditional operators and clauses to render views only when a certain state/condition is met.
- When doing inline conditions with TSX elements, note that `true && <div></div>` will show the element, but if `false && <div></div>` the TSX element won't show.
    - Another thing is that falsy expressions may show the falsy value despite the boolean values never showing with TSX (ex: 0)
```TSX
// Examples of Conditional Rendering

if (someState > 0) {
    return <div>someState</div>
}
return <div>falseState</div>


// Inline
return (
    <div>
        {stateCondition && <h2>Appear</h2>}
    <div>
)
```
---
### What are JavaScript modules (same in TypeScript)?
- JS modules are self-contained units of functionality that can shared and reused across project files. In essence, code in one JS or TS file is a module and to use code from that file, we need import that module. 

### How do we import JS modules?
- We can **import** modules into other JS/TS files by using the `import` and `export` keywords. The `export` keyword is used to export "live bindings" to functions, objects or primitive values from a module so they can be used by other programs. And we can get these "live bindings" through the use of the `import` keyword in the external file/program we want to use the "live bindings" in. 
- The syntax of using the `export` keyword is as follows, we can put the `export` keyword in front of the declaration of the variable, function, or class we want to be exported or make usable by other programs. We can however also use the `export` keyword at the end of the file instead and in curly braces write the name of the variable/function/class we want to export, if there are multiple then we add a comma to separate each item being exported. 
- Besides that syntax there are two types of exports that can be done **named exports** and **default exports**.
- Similar to the exporting syntax, instead of `export` we use the `import` keyword and then we have the curly braces around the functions/classes/variables that we will use and then we finish with the `from` keyword and the location of the importing module. 

### What are default exports and how are they different from named exports (the basic export syntax)?
- Default exports are a special type of export where we use `default` keyword after the `export` keyword and when exporting variables/functions/classes. The main difference from using the `default` keyword is that we no longer need curly braces for the export if its at the end of the file. However we can only have one default export per module and we can have a mix of named exports and default exports in a module. 
- As for importing default exported code, we do not need to match the name of the expression being exported in the import syntax, we only need to keep the `import`/`from` keywords and the location of the module the same. And again we do not need curly braces around the imported expression as it is a default export. 
- For importing and exporting syntax with a default export and multiple named exports we write the default export not in the curly braces and then followed by a comma and in curly braces all the named exports.

```JS
// This the module file we want to export stuff from. "A.js" This will be similar in TS
export default function bar() {
    // does some functionality;
};

export function foo() {
    // some code;
}

export let x = 6;

// NOTE: All functions/variables written ABOVE will be exported, so it is NOT NEEDED to write an export line at the bottom of the file.

// "B.js" this is another exporting module
function cool() {
    // does something cool
}

export default cool

// "C.js" this has mixed exports (both named and default)
function fun() {
    // fun code
}

var n = 9;

// This the export line at the bottom of the file, note that we have both a default export (fun) and named export (n)
// For default exports, we used the keywords `as` and `default`
// Again, only one default export is allowed for a module

export {fun as default, n};


// NOW it's time to IMPORT 
// "D.js" the file that will import all the other modules
import bar, {foo, x} from "A.js";
// Default exports can be named anything and are not required to match their name in module they were exported from.
import notCool from "B.js";
import yayFun, {n} from "C.js";
```

### How we do give aliases to exported/imported members?
- We can use aliases by using the `as` keyword following the name of the expression we are exporting. 
- Note that we do not use `as` keyword with **default exports/imports** as they already can be renamed when imported plus the `as` keyword in default exports is used in tandem with the `default` keyword when we list it in with named exports.
- Aliases are alternative names we can use to refer/call an expression when imported and used. 

```JS
export {n as N};
import {x as X};
```
---
## TypeScript

### What is TypeScript?
- **TypeScript** is a programming language and is a superset of JavaScript. A superset in the case of TypeScript means that TypeScript contains all of the features of JS and has been expanded or enhanced to include other features as well. 
- **TS** has more strictness & applies OOP principles. 
- In order for TS to be used by browsers it must be transpiled into JS, as most browsers support JS. 

### What is transpilation?
- Transpilation is the process of converting source code written in one language and converting it into another language with a similar level of abstraction. 
- This is different from compilation in the sense that when we compile one language to another we essentially change the level of abstraction that the source code has. This is seen when we compile Java source code to bytecode. Java source code has a higher level of abstraction than bytecode. This level of abstraction is noted when we say a programming language is a low-level or high-level language, where low-level languages like machine code are more understandable by machines and can be difficult to debug and understand from a programmer perspective. High-level languages like JS and TS essentially abstract some or a lot of that difficulty of understanding machine code to a level where we might see syntax is more readable and understandable to a programmer.
- With that when we use TS we transpile it to JS to be use code in the browser. And both TS and JS are very similar in that TS is a superset of JS. 

### What are features of TS?
- TS is open-source, object oriented, strongly typed, and mostly strictly typed.
    - Open-source free to use but also open to the public to make edits
    - OO - it supports features like classes, interfaces, inheritance
    - Strongly-typed - when declaring a variable, you need to declare a type as well
    - Strictly-typed - when you declare a variable, you can't change its type

### What data types are in TS?
- TS has all the basic data types of JS and includes more like:
    - **`any`** allows for a variable to store data of any type. This is similar to how JS works where a variable can change its data type based on the data stored and its not strictly typed. However, **any** in practice should be used when we don't know the exact type of the data we intend on storing. 
    - **Arrays** are more similar to Arrays in Java where there are typed arrays meaning the values in the array are of one type and the TS arrays are fixed in size like the ones in Java. 
        - This means arrays in TS can't be resized and however much space is allocated is the fixed size of it. We can explicitly say how many elements can be stored through the use the Arrays constructor in TS. Otherwise if we initialized the array with a list of elements, then the size of that list is the fixed size. 
    - **`never` & `void`** are both return types used for functions.
        - **`void`** is used explicitly and implicitly to denote that a function is not returning any values at all. So if you try to return a value, then TS will complain that you are trying to return a value when the return type is void meaning no values are to be returned.
            - **One big thing** this complaining **ONLY** happens when you explicitly declare a return type for a function. Otherwise if you return in a function that has no explicit return type, the return type of that function is really the return type of the value being returned.
        - **`never`** is a return type that should be explicitly declared if intended to use. `never` is used to declare that a function should not have a reachable end point, by end point it means that the function can either run forever or throw some error, which will throw us out of the function but that doesn't mean it ends that function. 
```TS
// Function with no explicit return type and implicitly has a return type of void
function sum(a: number, b: number) {

}

// Function with no explicit return type and implicitly has a return type of number
function sum(a: number, b: number) {
    return a + b;
}

// Function with no explicit return type and implicitly has a return type of void
function sum(a: number, b: number) {
    let c = a + b;
}

// Function with explicit return type of void. 
/* 
ALSO THIS WILL PROMPT AN EXCEPTION/ERROR/WARNING about a function 
trying to return when clearly (void) it should not return anything at all.
*/
function sum(a: number, b: number): void {
    return a + b;
}

// Explicit return type: never
// Warning/Error about a function has an endpoint and/or trying to return
function sum(a: number, b: number): never {
    return a + b;
}

// Explicit return type: never
// Warning/Error about a function has an endpoint
function sum(a: number, b: number): never {
    let c = a + b;
}


// VALID usages of never

function infinity(): never {
    while (true) {
        console.log("PRINT FOREVER");
    }
}

function raiseError(message: string): never {
    throw new Error(message);
}
```

### How do classes work in TS?
- TS has object-orient programming which means it has support for classes. TS classes are similar to Java in terms of having fields, a constructor, functions, and to declare a new object we use the `new` keyword with the class constructor. Also similar to Java in that it has inheritance such as using the `extends` keyword for inheriting other classes and `implements` keyword to inherit interfaces. 
- There are however slight differences, one being that the constructor in TS is written as the literal word "constructor" for the naming of the class constructor

### How do constructors work in TS?
- Constructors in TS work like Java constructors but require a call to `super()` explicitly. The `super()` is also what allows for us to use the `this` reference to an instance, without `super()` we cannot use `this`. 
- In React specifically, props passed into a constructor must be also passed in `super()`, in order for it to be usable in the context of the `this` keyword. `super(props)` will assign/set the props as a property of the instance of the component and this makes it usable outside of `render()` and `constructor()` in class components.
- Similarly to store a value for an instance we may refer to those values from the `this` reference/object, so in general we should pass any values (props in React) to the `super()` to use it as `this.valueName` (`this.props` for React props)

### What are decorators in TS?
- Decorators are a way to provide additional functionality to your code. Decorators can be attached to classes, functions, properties, parameters, or accessors. When attaching a declarator we use the @ symbol and the expression or decorator name  and this can be written inline or above the class/function/accessor/property/or parameter you are attaching it to. 
- The decorator's name or expression evaluates to a function that will decorate the thing it is attached to. Decorate here means to either modify, observe or replace something about a the decorated thing.

### What are access modifiers in TS?
- Access modifiers in object-oriented programming and in TypeScript is used to control the visibility of data members in a class. 
- There are three types of access modifiers in TS public, private, and protected
- By default when no access modifier is specified for a data member, `public` modifier is the default modifier for that data member. 
-`public` allows for a data member to be accessible from anywhere
- `protected` alllows for a data member to be only accessible from within the same class and within subclasses
- `private` allows for accessibility in the same class only
- If you try to access a data member outside of the access scope it restricts to then an error will shown at compile time.

### What is the **`readonly`** keyword?
- In TypeSript, `readonly` is used to make a property as "read-only" in a class or interface. Essentially "read-only" means to make a property immutable and we can make a readonly declaration when declaring the property. A property is defined as a field or variable that stores data fro a class. So readonly can only be applied to fields and not methods of a class. 
- Since readonly fields can be accessed outside of a class, but their values cannot be changed. You can only initialize a readonly property during its initial declaration or initialize it in the constructor. This also 

### What is another way to make a value read-only?
- You can use getters, getters are functions that allow you to retrieve the data that is stored away in the object's class, with the private access modifier being declared on that data. Without the getter function we would not be able to retrieve the value/field that has been declared with `private`. 
- By doing this and omitting the setter function we can achieve a read-only property for a class which means that we can see that data stored, but not change it at all. 

### 'readonly' keyword vs Getters
- Getters are functions used to retrieve a class's field data, whereas `readonly` is a modifier keyword
- The purpose of getters is to get data that isn't retrievable normally by calling the fields name from the object.
- `readonly` allows for the calling of the field's name from the object but does not allow changes to be made to the field. 

### What are language/feature differences between TypeScript and JavaScript?
- While both languages can perform OOP, please note that you really can't say that TypeScript is better for OOP as JS has pretty the much same features for OOP as TS.
- TypeScript has *static typing*, **strict typing**, and **strong typing**. Strong typing relates to the fact that we have declare the data type of a variable when the variable is declared. Strict typing applies to that once declared a variable cannot change its type (therefore cannot store values of any other data type). 
- TypeScript also points out compilation errors when developing, this overall reduces the chances of runtime errors being encounter. 
- TypeScript enhances encapsulation through the use of access modifiers (which don't exist in JS), access modifiers like in Java limit the scope data members can be accessed from.


### What's the difference between a library and a framework?
- Libraries provides functionalities that we as the user can choose and pick what we want to utilize in our project.
- Frameworks provides already written underlying code and we provide it with the necessary information for it to execute. 
- The difference between the two is that libraries have defined functions and work the way they are and we have more control over how we setup a project and we just functions we need from the library.
- Frameworks have "unfinished" functions in the sense that they do control how the project is setup and to finish the functionality we supply our own code where it is required by the function. The project structure in terms of setup will tend to look the same.
- **A library is not a framework because we are able to call it in our code, can be integrated into a part of the UI.**


## Questions from TypeScript/React 
