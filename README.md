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
