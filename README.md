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
- Use `document.getElementById()` method to select the target DOM node.
  - "There is a div with id='challenge-node' available for you to use"
    - This means that there is a `<div>` element in the index.html file with `id='challenge-node'`
      - `<div id='challenge-node'></div>`
- `ReactDOM.render(JSX, document.getElementById("challenge-node"))` will inject the `JSX` component (the React element) into the specified `div` element, which will then appear on a web page.
