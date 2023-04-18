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
      <p>I am also a child</p>
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

## Use React to Render Nested Components

- Component composition is one of React's powerful features.
- When working with React, it is important to think about the user interface in terms of components.
- Break down the UI into its basic building blocks, which are components.
- This helps to separate the code responsible for the UI from the code responsible for handling the application logic.
- It simplifies the development and maintenance of complex projects.

```js
const TypesOfFruit = () => {
  return (
    <div>
      <h2>Fruits:</h2>
      <ul>
        <li>Apples</li>
        <li>Blueberries</li>
        <li>Strawberries</li>
        <li>Bananas</li>
      </ul>
    </div>
  );
};

const Fruits = () => {
  return (
    <div>
      <TypesOfFruit />
    </div>
  );
};

class TypesOfFood extends React.Component {
  constructor(props) {
    super(props);
  }

  render () {
    return (
      <div>
        <h1>Types of Food:</h1>
        <Fruits />
      </div>
    );
  }
};
```

- in the code above, `TypesOfFruit` is composed, or `nested` within another constant variable `Fruits`.
- Then `Fruits` is `nested` again in `TypesOfFood`.
- Think of it as 'multi-dimensional components'.

## Compose React Components

- When handling more complex compositions with React components and JSX, there is one important thing to note.
- Rendering ES6 style class components within other components is no different than rendering simple components.
- It is possible to render JSX elements, stateless functional components, and ES6 class components within other components.

```js
const NonCitrus = () => {
  return (
    <div>
      <h3>Non-Citrus:</h3>
      <ul>
        <li>Apples</li>
        <li>Blueberries</li>
        <li>Strawberries</li>
        <li>Bananas</li>
      </ul>
    </div>
  );
};

const Citrus = () => {
  return (
    <div>
      <h3>Citrus:</h3>
      <ul>
        <li>Lemon</li>
        <li>Lime</li>
        <li>Orange</li>
        <li>Grapefruit</li>
      </ul>
    </div>
  );
};

const Veggies = () => {
  return (
    <div>
      <ul>
        <li>Brussel Sprouts</li>
        <li>Broccoli</li>
        <li>Squash</li>
      </ul>
    </div>
  );
};

class Vegetables extends React.Component {
  constructor(props) {
    super(props);
  }
  render () {
    return (
      <div>
        <h2>Vegetables:</h2>
        <Veggies />
      </div>
    );
  }
}

class Fruits extends React.Component {
  constructor(props) {
    super(props);
  }
  render () {
    return (
      <div>
        <h2>Fruits:</h2>
        <NonCitrus />
        <Citrus />
      </div>
    );
  }
};

class TypesOfFood extends React.Component {
  constructor(props) {
    super(props);
  }
  render () {
    return (
      <div>
        <h1>Types of Food:</h1>
        <Fruits />
        <Vegetables />
      </div>
    );
  }
};
```

- Examine which stateless functional component is nested where, and which ES6 class component is nested where.

## Render a Class Component to the DOM

- Remember how to use ReactDOM API.

`ReactDOM.render(componentToRender, targetNode)`

- The process for rendering react components is very similar.
- Instead of rendering individual JSX elements, it is possible to render complex React components to the DOM.
- The syntax is slightly different.
- Use the same syntax as if you were rendering nested components

`ReactDOM.render(<componentToRender />, targetNode)`

- The above syntax can be used for both ES6 class components and functional components.

- Let's use the `Fruits` and `Vegetables` components defined in the previous exercise
- There is a `div` with `id = 'challenge-node'` available for use.

```js
class TypesOfFood extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h1>Types Of Food:</h1>
          <Fruits />
          <Vegetables />
      </div>
    );
  }
};

ReactDom.render(<TypesOfFood />, document.getElementById("challenge-node"));
```

## Practice Writing a React Component from Scratch

- It is important to become very familiar with writing React components since they are the building blocks of React applications.
- A typical React component is an ES6 class, which extends `React.Component`.
- It has a render method that returns HTML (from JSX) or `null`.

```js
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h1>My First React Component!</h1>
      </div>
    );
  }
};

ReactDOM.render(<MyComponent />, document.getElementById("challenge-node"));
```

## Pass Props to a Stateless Functional Component

- Another feature very common in React is `props`
- In React, you could pass props, or properties, to child components.

- In the example below, there is an `App` component that renders a child component `Welcome`, which is a stateless functional component.
- You can pass a `user` property to `welcome`

```jsx
<App>
  <Welcome user="Mark" />
</App>
```

- Use custom HTML attributes created that are supported by React to be passed to the component.
- Since `Welcome` is a stateless functional component, it has access to this value.

```jsx
const welcome = (props) => <h1>Hello, {props.user}!</h1>
```

- It is standard to call this value `props`
- When dealing with stateless functional components, consider it as an argument to a function which returns JSX.
- You can access the value of the argument in the function body.
- It is a little different for class components.

```jsx
const CurrentDate = (props) => {
  return {
    <div>
      <p>The current date is: {props.date}</p>
    </div>
  };
};

class Calendar extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h3>What date is it?</h3>
        <CurrentDate date={Date()} />
      </div>
    );
  }
};
```

## Pass an Array as Props

- Similar to the previous exercise, it is possible to pass arrays as `props`.
- To pass an array to a JSX element, it must be treated as JavaScript and wrapped in curly braces.

```jsx
<ParentComponent>
  <ChildComponent colors={["green", "blue", "red"]}>
</ParentComponent>
```

- The child component then has access to the property `colors`.
- Array methods such as `join()` can be used when accessing the property.
- `const ChildComponent = (props) => <p>{props.colors.join(', ')}</p>`
- This will join all `colors` array items into a comma separated string to produce `<p>green, blue, red</p>`

```jsx
const List = (props) => {
  return <p>{props.tasks.join(', ')}</p>
};

class ToDo extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h1>To Do List</h1>
        <h2>Today</h2>
          <List tasks={["a", "b"]} />
        <h2>Tomorrow</h2>
          <List tasks={["c", "d", "e"]}>
      </div>
    );
  }
};
```

## Use Default Props

- React also has an option to set default props.
- Assign default props to a component as a property on the component itself, and React assigns the default prop if necessary.
- If no value is explicitly provided, the default prop value specified will be used.
- For example `MyComponent.defaultProps = { location: 'Toronto' }` will set the default value of the location prop to `Toronto`.
- It will remain `Toronto` unless specified otherwise.
- React assigns default props if props are undefined.
- But if you pass `null` as the value for a prop, it will remain `null`.


```jsx
const ShoppingCart = (props) => {
  return (
    <div>
      <h1>Shopping Cart Component</h1>
    </div>
  )
};

ShoppingCart.defaultProps = { items: 0 }
```


