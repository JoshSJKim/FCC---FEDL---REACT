# FCC---FEDL---REACT

- React is an Open Source view library created and maintained by Facebook.
- It is a tool used to render the User Interface (UI) of modern web applications.

- React uses a syntax extension of JavaScript called `JSX`, which allows you to write HTML directly within JavaScript.
  - It allows you to use the full programmatic power of JS within HTML
  - It helps to keep your code readable.

- For the most part, JSX is very similar to HTML, but with a few key differences.
  - Since JSX is a syntactic extension of JavaScript, you can write JS directly within JSX.
  - To do this, simply include the code you want to be treated as JS within curly braces
  - `{ 'JavaScript Code Here' }

- However, since JSX os not valid JavaScript, JSX code must be compiled into JavaScript.
  - Transpiler Babel is a popular tool for this process

- It is worth noting that under the hood, FCC React challenges are called `ReactDOM.render(JSX, document.getElementByID('root'))`
- This function call is what places your JSX into React's own lightweight representation of DOM (Document Object Model).
  - React then uses snapshots of its own DOM to optimize updating only specific parts of the actual DOM.

## Create a Simple JSX Element

- JSX can represent more complex HTML
- One important thing to note about nested JSX is that it must return a single element.
- In other words, a single parent element is required to wrap all levels of nested elements.

For example,

```JSX
const JSX = 
<div>
    <p>Paragraph One</p>
    <p>Paragraph Two</p>
    <p>Paragraph Three</p>
</div>
```

- The child elements `<p>` in the above code are nested in one parent element `<div>`
- If you remove the `<div>` and leave only the `<p>` elements on its own, it would not be a valid JSX element.

```JSX
const JSX = 
    <p>Paragraph One</p>
    <p>Paragraph Two</p>
    <p>Paragraph Three</p>
```

- The above is invalid and it will not transpile.

## Add Comments in JSX

- JSX has its own commenting syntax

`{/* This is a JSX comment */}`

## Render HTML Element to the DOM

- With React, we can render JSX directly to the HTML DOM using React's rendering API known as ReactDOM
- It offers a simple method to render React element o the DOM, which looks like the following
  - `ReactDOM.render(componentToRender, targetNode)`
  - The first argument is the React element or component that requires rendering
  - The second argument is the DOM node to which the component will be rendered.

- `ReactDOM.render()` must be called after the JSX element declarations, just like variables need declaring before use.

Challenge

- The code editor has a simple JSX component.
- Use the `ReactDOM.render()` method to render this component to the page.
- You can pass defined JSX elements directly in as the first argument and use `document.getElementById()` to select the DOM node to render them to.
- There is a div with id='challenge-node' available for you to use.
- Make sure you don't change the JSX constant.

```jsx
const JSX = (
  <div>
    <h1>Hello World</h1>
    <p>Lets render this to the DOM</p>
  </div>
);
// Change code below this line

ReactDOM.render(JSX, document.getElementById("challenge-node"))
```

- `ReactDOM.render()` method will render the specified component (JSX) to the page by specifying the `target node`
- Use `document.getElementById()` method to select the target DOM node. (Make sure not to capitalize ID)
  - "There is a div with id='challenge-node' available for you to use"
    - This means that there is a `<div>` element in the index.html file with `id='challenge-node'`
      - `<div id='challenge-node'></div>`
- `ReactDOM.render(JSX, document.getElementById("challenge-node"))` will inject the `JSX` component (the React element) into the specified `div` element, which will then appear on a web page.

## Define an HTML Class in JSX

- HTML and JSX seems very similar, but there are several things to keep in mind.
- the word `'class'` cannot be used to define HTML classes since it is a reserved word in JS.
- JSX uses `'className'` instead.

- Naming convention for all HTML attributes and event references in JSX become `camelCase`.

```jsx
const JSX = ( 
  <div className="myDiv">
    <h1>Add a class to this div</h1>
  </div>
);
// Note that 'className' is used to define the HTML class.
```

## Learn About Self-Closing JSX Tags

- The idea of 'self-closing tags' is different in JSX and HTML
- In HTML, almost all tags have both opening and closing tags.
  - The closing tags always begin with a forward slash before the tag name that is being closed.
  - There are special instances in HTML that have 'self-closing tags'.
  - For example, line-break tags can be written as `<br>` or `<br />`, but never `<br></br>` since it does not contain any content.

- In JSX, the rules are a little different.
- Any JSX element can be written with a self-closing tag, and every element must be closed.
- A `<div>` element can be written as `<div />` or `<div></div>`, depending on the circumstance.
  - If the `<div>` element contains content, it requires a separate closing tag
  - but if it does not contain any content, the self-closing tag is valid.

## Create a Stateless Functional Component

- Components are the core of React. Everything in React is a component.
- There are two ways to create a React component.
  - The first way is to use a JS function.
  - Defining a component in this manner creates a 'stateless functional component'.
    - Think of it as a component that can receive data and render it, but does not manage or track changes to the data.
    - (The second method to create components will be covered later)

- Simply write a JS function that returns either JSX or `null`.
- Make note that React requires the function name to begin with an uppercase letter.

```js
const DemoComponent = function() {
  return (
    <div className="customClass" />
  ):
}:
```

- Above is a stateless functional component that assigns an HTML class in JSX.

- Since JSX components represent HTML, it is possible to put several components together to create a more complex HTML page.
- It allows the developer to compose the UI from many separate, isolated components, making it easer to build and maintain complex UI.

## Create a React Component

- The other method to create a React component is by using the ES6 `class` syntax.

```js
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h1>Hello React!</h1>
      </div>
    );
  }
}
```

- This creates an ES6 class `MyComponent` which extends the `React.Component` class.
- Now, `MyComponent` class has access to many useful React features (which will be covered later on)

- Notice `MyComponent` class has a `constructor` defined within it that calls `super()`.
- `super()` is used to call the constructor of the parent class, which in this case is `React.Component`.
- The constructor is a special method used during the initialization of objects that are created with the `class` keyword.
- It is best practice to call a component's `constructor` with `super`, and pass `props` to both.
  - This ensures that the component is initialized properly. It is a standard for this code to be included.

## Create a Component with Composition

- In order to compose multiple React components together, you could create a `parent` component, which then renders the defined 'stateless functional components' as the `children` of the `parent` component.
- To render a component as a child in a React component, include the component name written as a custom HTML tag in the JSX.

```js
const ChildComponent = () => {
  return (
    <div>
      <p>I am the Child</p>
    </div>
  );
};

const SiblingComponent = () => {
  return (
    <div>
      <p>I am the sibling</p>
    </div>
  );
};

class ParentComponent extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return(
      <div>
        <h1>I am the parent</h1>
        <ChildComponent />
        <SiblingComponent />
      </div>
    );
  }
};
```

- When React encounters a custom HTML tag that references another component (component name with a self-closing tag in this case), it renders the markup for that component in the location of the tag.
- Anything defined in the `stateless functional components` will be displayed on the page if included in the parent component.

- Note `ChildComponent` and `SiblingComponent` above are defined with an ES6 arrow function because this is a very common practice when using React.