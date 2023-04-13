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