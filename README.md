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

## Override Default Props

- Override the default props value by explicitly setting the prop value.

```jsx
const Items = (props) => {
  return <h1>Current Quantity of Items in Cart: {props.quantity}</h1>
}

Items.defaultProps = { quantity: 0 }

class ShoppingCart extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return <Items quantity = {10} /> {/* This will set the quantity prop value to 10 and override the default value */ }
  }
};
```

## Use PropTypes to Define the Props You Expect

- React provides useful type-checking features to verify that the components receive the correct type of props.
- You can set `propTypes` on the component to require the data to be of a specific type, such as an array or a function.
- This will generate a warning when the data is of any other type.

- It is considered best practice to set `propTypes` when you know what type of prop to expect ahead of time.
- The method for defining `propTypes` is the same as the method used for `defaultProps`.

For example,

```jsx
MyComponent.propTypes = { handleClick: PropTypes.func.isRequired }
```

- In the above example, `PropTypes.func` checks if `handleClick` is a function, and `isRequired` informs React that `handleClick` is a required property for that component.
- If missing, it will generate a warning.

- Note: `func` represents function. `bool` represents boolean.
  - These are the only two that use unusual spelling among the seven primitive JavaScript types.
  - In addition to the primitive types, there are other types available.
  - You can also check that a prop is a React element. (Search for all other options)

- Note: As of React v15.5.0, `PropTypes` is imported independently from React.
  - `import PropTypes from 'prop-types';`

```jsx

const Items = (props) => {
  return <h1>Current Quantity of Items in Cart: {props.quantity}</h1>
};

Items.propTypes = { quantity: PropTypes.number.isRequired }; { /* This will set the PropTypes to number */ }

Items.defaultProps = { quantity: 0 };

class ShoppingCart extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return <Items />
  }
};
```

## Access Props Using this.props

- If a prop is passed to a ES6 class component as the child component (rather than a stateless functional component), the ES6 class component uses a slightly different convention to access props.
- Anytime you refer to a class component within itself, use the `this` keyword.
- To access props within a class component, preface the code that you use to access it with `this`.
- for example, if an ES6 class component has a prop called `data`, write `{this.props.data}` in JSX

```jsx
class APP extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return {
      <div>
        <Welcome name = "Jesus" />
      </div>
    };
  }
};

class Welcome extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <p>Hello, <strong>{this.props.name}!</p>
      </div>
    );
  }
};
```

## Review Using Props with Stateless Functional Components

- All of the exercises until now, except for the last one, dealt with passing props to stateless functional components.
- Stateless functional components act like pure functions.
  - It accepts props as input and return the same output every time they are passed the same props.

- `Stateless functional component` is any function you write, which accepts props and returns JSX.
- `Stateless component`, on the other hand, is a class that extends `React.Component`, but does not use internal state.
- `stateful component` is a class component that does maintain its own internal state.
  - These are commonly referred to as components or React components.

- Commonly, try to minimize statefulness and to create stateless functional components wherever possible.
- This helps contain the state management to a specific area of the application, which will in turn improve development and maintenance of the app by making it easier to follow how changes to state affect its behavior.

```jsx
class CampSite extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <Camper />
      </div>
    );
  }
};

const Camper = (props) => {
  return (
    <div>
      <p>{props.name}</p>
    </div>
  )
};

Camper.defaultProps = { name: "CamperBot" }
Camper.propTypes = { name: PropTypes.string.isRequired }
```

- `CampSite` component renders `Camper` component as its child.
- `Camper` component is assigned a default prop of `{ name: 'CamperBot' }
- `Camper` component renders a `div` element with a nested `p` element to which `{props.name}` is passed.
- `Camper` component requires a `name` prop of type `string`.

## Create a Stateful Component

- One of the most important topics in React is `state`.
- `State` consists of any data your application needs to know about, which can change over time.
- You want the apps to respond to state changes and present and updated UI when necessary.

- Create state in a React component by declaring a `state` property on the component class in its `constructor`.
- This initializes the component with `state` when it is created.
- The `state` property must be set to a JavaScript `object`.

```jsx
this.state = {

}
```

- `State` object is accessible throughout the life fo the component.
- It can be updated, rendered in the UI, and passed as props to child components.
- The `state` object can be as complex or as simple as required.
- Note that creating a class component by extending `React.Component` is mandatory in order to create `state`

```jsx
class StatefulComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = { firstName: "Josh" }
  }
  render() {
    return (
      <div>
        <h1>{this.state.firstName}</h1>
      </div>
    );
  }
}
```

## Render State in the User Interface

- Once a component's initial state is defined, any part of it can be displayed in the UI that is rendered.
- If a component is stateful, it will always have access to the data in `state` in its `render()` method.
- The data can be accessed with `this.state`.
- To access a state value within the `return` of the render method, enclose the value in curly braces

- `state` is one of the most powerful features of components in React.
- It allows you to track important data in your app and render a UI in response to changes in this data.
- React uses a 'virtual DOM', which keeps track of changes under the hood.
- When state data updates, it re-renders components using that data, including child components that received the `state` data as a prop.
- React automatically updates the actual DOM only where necessary.
- Simply declare what the UI should look like.

- Note: If a component is stateful, no other components are aware of its `state`.
- It is completely encapsulated, or local, to that component.
- It is possible to pass the state data to a child as `props`.
- This is important because it allows you to write certain logic that can be contained and isolated in one place in the code.

```jsx
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: "freeCodeCamp"
    }
  }
  render() {
    return (
      <div>
        <h1>{this.state.name}</h1>
      </div>
    );
  }
};
```

- The above code will display 'freeCodeCamp' on the browser page.
- Note that in JSX, anything written in curly braces({}) are treated as JavaScript.

## Render State in the UI Another Way

- There is another way to access `state` in a component.
- In the `render()` method, before the `return` statement, write JS directly.
- It is possible to declare functions, access data from `state` or `props`, perform computations on this data, etc.
- Then, you can assign any data to variables, which are accessible in the `return` statement.

```jsx
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: 'freeCodeCamp'
    }
  }
  render() {
      const name = this.state.name { /* Note that const 'name' is assigned the same value as the name value in the component's state */ }
    return (                       { /* Also note that curly braces for JS is not required in this part of the code */ }
      <div>
        <h1>{name}</h1>
      </div>
    );kk
  }
};
```

## Set State with this.setState

- Previous challenges covered how initialize `state` in the `constructor`.
- There is also a way to change the component's `state`.
- Update the component `state` by calling `this.setState()` in the component class and pass in an object with key-value pairs.
- The keys are the state properties and the values are the updated state data.

- React never expects `state` to be directly modified.
- Always use `this.setState()` when state changes occur.
- Note that React may 'batch' multiple state updates in order to improve performance.
- In other words, state updates implemented using `setState` method can be asynchronous.

```jsx
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: 'Initial State'   { /* This portion of the code will initialize 'state' */ }
    };
    this.handleClick = this.handleClick.bind(this);
  }
  handleClick() {
    this.setState({
      name: 'React Rocks!'    { /* This portion of the code will update the 'state' data */ }
    });
  }
  render() {
    return (
      <div>
        <button onClick={this.handleClick}>Click Me</button>
        <h1>{this.state.name}</h1>
      </div>
    );
  }
};
```

## Bind 'this' to a Class Method

- In addition to setting and updating `state`, it is also possible to define methods for the component class.
- A class method typically requires the use of `this` keyword in order to access properties on the class (such as `state` and `props`) inside the scope of the method.

- A common way used is to explicitly bind `this` in the constructor so `this becomes bound to the class methods after the component is initialized.

`this.handleClick = this.handleClick.bind(this)`

- The above was used in the previous exercise for the `handleClick` method in the constructor.
- When a function like `this.setState()` is called within the class method, `this` refers to the class and will not be undefined.

```jsx
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      text: "Hello"
    };
    this.handleClick = this.handleClick.bind(this);
  }
  handleClick() {
    this.setState({
      text: "You clicked!"
    });
  }
  render() {
    return(
      <div>
        <button onClick={this.handleClick}>Click Me</button>
        <h1>{this.state.text}</h1>
      <div>
    );
  }
};
```

## Use State to Toggle an Element

- Sometimes it is necessary to know the previous state when updating the state.
- As mentioned before, state updates may be asynchronous.
- It means that the previous value of `this.state` or `this.props` can't relied upon when calculating the next value.

- Pass a function that allows access to state and props to `setState`.
- Using a function with `setState guarantees the most current values of state and/or props.

```jsx
this.setState((state, props) => ({
  counter: state.counter + props.increment
}));
```

OR

```jsx
this.setState(state => ({
  counter: state.counter + 1
}));
```

- Note that the object literal has to be wrapped in parentheses.
- Otherwise JavaScript will think of it as a block of code.

```jsx
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      visibility: false
    };
    this.toggleVisibility = this.toggleVisibility.bind(this) { /* bind 'this' keyword to the method */ }
  }
  toggleVisibility() {                  { /* this is the toggleVisibility function */ }
    this.setState(state => {            { /* Remember that you can write JS with React */ }
      if (state.visibility === true) {  { /* if state.visibility is 'true', visibility is set to 'false', and vice versa */ }
        return {visibility: false};     { /* true and false are playing 'tag' in a sense to produce a 'toggle' effect */ }
      } else {
        return {visibility: true};
      }
    })
  }
  render() {
    if (this.state.visibility) {
      return {
        <div>
          <button onClick={this.toggleVisibility}>Click Me</button> { /* Clicking on the button will call the 'toggleVisibility' function */ }
          <h1>Now you see me!</h1>
        </div>
      };
    } else {
      return (
        <div>
          <button onClick={this.toggleVisibility}>Click Me</button>
        </div>
      );
    }
  }
}
```

## Write a Simple Counter

```jsx
class Counter extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0
    };

    this.increment = this.increment.bind(this)  // Bind the methods in the constructor 
    this.decrement = this.decrement.bind(this)
    this.reset = this.reset.bind(this)

  }

  increment() {                     // Define the methods to be called when rendered
    this.setState(state => {
      return {count: state.count+1} // Failure to include 'return' will return a statement rather than an undated state 
    })                              // Remember to use curly braces for JS code
  };

  decrement() {
    this.setState(state => {
      return {count: state.count-1}
    })
  };

  reset() {
    this.setState ({                // There is no need to pass in a function here since the count is simply being reset to '0'
      count: 0
    })
  };

  render() {
    return (
      <div>
        <button className='inc' onClick={this.increment}>Increment!</button>
        <button className='dec' onClick={this.decrement}>Decrement!</button>
        <button className='reset' onClick={this.reset}>Reset</button>
        <h1>Current Count: {this.state.count}</h1>
      </div>
    );
  }
};
```

## Create a Controlled Input

- Applications may have much more complex interactions between `state` and the rendered UI.
- For example, form control elements, such as `input` and `textarea` maintain its own state in the DOM as the user types.
- Using React, this mutable state can be moved into a React component state, which means that the user input becomes a part of the application state.
- In other words, React is able to control the value of that input field.
- This is particularly useful for validating email addresses and passwords.
- Used in conjunction with regex, it is possible to display error messages or change colors to warn the user that the format is invalid in real time.
- Typically, if a user can type into an input field, and that input field is a part of a React component, it will be a controlled input form

```jsx
class ControlledInput extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      input: ''
    };
    this.handleChange = this.handleChange.bind(this)
  }
  handleChange(event) {         // When the input field receives an input, handleChange() method will be called with the input 'event' as its parameter
    this.setState ({            // this.state.input value will be updated with the input 'event' value.
      input: event.target.value
    })
  };
  
  render() {
    return (
      <div>
        <input value={this.state.input} onChange={this.handleChange} />
        <h4>Controlled Input:</h4>
        <p>{this.state.input}</p>
      </div>
    );
  }
};
```

## Create a Controlled Form

- This is very confusing so far.
- It's difficult to keep track of what's calling what, and what `this` is referring to.

```jsx
class MyForm extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      input: '',
      submit: ''
    };
    this.handleChange = this.handleChange.bind(this;)
    this.handleSubmit = this.handleSubmit.bind(this);
  }
  handleChange(event) {
    this.setState({
      input: event.target.value
    });
  }
  handleSubmit(event) {
    this.setState(state => {
      return {submit: this.state.input}
    });
    event.preventDefault()
  }
  render() {
    return (
      <div>
        <form onSubmit={this.handleSubmit}>
        { /* 2. When the submit button is clicked, handleSubmit method will be called to return the state input */ }
          <input value={this.state.input} onChange={this.handleChange} /> 
          { /* 1. When text is entered, the input value "event" will call the handleChange method (controlled input)*/ }
          <button type="submit">Submit!</button>
        </form>
        <h1>{this.state.submit}</h1>
        { /* 3. The return value from handleSubmit will be displayed in the <h1> tag */ }
      </div>
    );
  }
}
```

- I can't even explain the process flow of this code.
- I'll need some more time on this

## Pass State as Props to Child Components

- Commonly, a stateful component contains all of the `state` that are important to the application, which then renders child components.
- The state should be accessible by the components in the form of passed `props`.

- for example, there is an `App` component that renders a `Navbar`.
- The `App` also contains multiple `states`, which also contain multiple information.
- If the `Navbar` only requires access to the username information, that `state` can be passed to the `Navbar` component as a prop.

- Some important things to note:
  - Unidirectional flow
    - State flows in one direction down the tree of the application's components - from the stateful parent component to the child components.
    - The child component only receives the state data it requires.
  - Complex stateful apps can be broken down into just a few, or maybe a single stateful component.
    - The rest of the components simply receive state from the parent as props and render a UI from that state.
    - It begins to create a separation where state management is handled in one part of code and UI rendering in another.

- this principle of separating `state logic` and `UI logic` is one of React's key principles.
- When used correctly, it makes the design of complex, stateful applications significantly easier to manage.

```jsx
class MyApp extends React.Component {
  constructor(props) {
    super(props);
    this.state = {        // class component with a state defined is also known a 'stateful component' or 'container component'
      name = 'CamperBot'  // stateful components are used to manage dynamic behaviors of applications, handle user events and update state changes
    }
  }
  render() {
    return (
      <div>
        <Navbar name={this.state.name} /> {/* MyApp component renders 'Navbar', which receives the name property of the MyApp state */ }
      </div>
    );
  }
};

class Navbar extends React.Component {
  constructor(props) {
    super(props);         // class components without a state defined is also known as 'functional component'
  }                       // It does not perform state management is used to display information or accept user input via props.
  render() {
    return(
      <div>
        <h1>Hello, my name is: {this.props.name}</h1> { /* functional component 'Navbar' receives the name property passed from the MyApp component as props */}
      </div>
    );
  }
};
```

## Pass a Callback as Props

- Just like you can pass `state` as props to the child components, it is also possible to pass handler functions or any other methods defined on a React component.
- This way, it is possible for child components to interact with its parent components.
- It's assigned a name and you have access to that method name under `this.props` in the child component.

```jsx
class MyApp extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      inputValue: ''
    }
    this.handleChange = this.handleChange.bind(this);
  }
  handleChange(event) {
    this.setState({
      inputValue: event.target.value
    });
  }
  render() {
    return (
      <div>
        <GetInput input={this.state.inputValue} handleChange={this.handleChange} />
        <RenderInput input={this.state.inputValue} />
      </div>
    );
  }
};

class GetInput extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h3>Get Input:</h3>
        <input value={this.props.input} onChange={this.props.handleChange} />
      </div>
    );
  }
};

class RenderInput extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h3>Input Render:</h3>
        <p>{this.props.input}</p>
      </div>
    );
  }
};
```

- Stateful component `MyApp` maintains the `state` `inputValue`.
- `handleChange()` method is bound to `MyApp` so that any `state` update will be ultimately handled by `MyApp`.
- `handleChange()` method updates the state of `inputValue` by targeting the input text information entered (event) in the input field in `GetInput` component.
- `MyApp` renders both `GetInput` component and `RenderInput` component.
- `GetInput` is passed an `input` prop assigned to `inputValue` from `MyApp`'s `state`.
- It's also passed a `handleChange` prop that calls the `handleChange()` method.
- `RenderInput` is also passed an `input` prop and `inputValue` from `state` is passed to it.

- `GetInput` has an `<h3>` tag that will be displayed when called.
- It also has a text input field, which is linked to the input prop passed to `GetInput` in the render method in `MyApp`.
- It will also call the `handleChange()` method to pass over the handles to `MyApp`

- `RenderInput` also has an `<h3>` tag that will be displayed when called.
- It also has a `<p>` element which will render the text input in the input field.

- when the user types into the input field in GetInput, the handleChange() method passed down from MyApp is called, which then updates the inputValue state of MyApp.
- This state change causes the MyApp component to re-render, which in turn causes the RenderInput component to display the updated inputValue prop passed down from MyApp.

## Use the Lifecycle Method componentWillMount

- React components have several special methods that provide opportunities to perform actions at specific points in the lifecycle of a component.
- These are called `lifecycle methods` or `lifecycle hooks`.
- The execution can occur before they are rendered, before an update, before receiving props, before unmount, etc.
- Some examples of lifecycle methods are:

- `componentWillMount()`
- `componentDidMount()`
- `shouldComponentUpdate()`
- `componentDidUpdate()`
- `componentWillUnmount()`

- Note: `componentWillMount` lifecycle method will be deprecated in a future version of 16.x

- `componentWillMount()` method is called before the `render()` method when a component is being mounted to the DOM

```jsx
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
  }
  componentWillMount() {
    console.log("Mount component")
  }
  render() {
    return <div />
  }
};
```

- the browser console will display "Mount component".

## Use the Lifecycle Method componentDidMount

- Often times it is necessary to call an API endpoint to retrieve data.
- When working with React, it is important to know and understand where to perform this action.

- The best practice with React is to place API calls or any calls to the server in the lifecyle method `componentDidMount()`
- This method is called after a component is mounted to the DOM.
- Any calls to `setState()` here will trigger an re-rendering of the component.
- When API is called using this method and the API data returned is used to set the state, it will automatically trigger an update when the data is received.

```jsx
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      activeUsers: null
    };
  }
  componentDidMount() {
    setTimeout(() => {
      this.setState({
        activeUsers: 1273
      });
    }, 2500);
  }
  render() {
    return (
      <div>
        <h1>Active Users: {this.state.activeUsers} </h1>
      </div>
    );
  }
};
```

- The above is a mock API call that simulates a server call requesting data to be retrieved.
- The time is set to 2.5 seconds

## Add Event Listeners

- `componentDidMount()` method is also the best place to attach any event listeners you need to add for specific functionality.

- React provides a synthetic event system which wraps the native event system present in browsers.
- This means that the synthetic event system behaves exactly the same, regardless of the user's browser - even if the native events may behave differently between different browsers.

- Event listeners in React are functions that are registered to handle events triggered by user actions or by the system, such as mouse clicks, key presses, form submissions, to just name a few.
- React provides a way to attach event listeners to specific elements in the UI using the `on*` props, where `*` is the name of the event.
- For example, to handle a click event on a button element, you can define a function and pass it as a prop to the `onClick` attribute of the button.

- React's synthetic event system is great to use for most interactions managed on DOM elements.
- However, in order to attach an event handler to the document or window objects, it must be done directly.

```jsx
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      message: ''
    };
    this.handleEnter = this.handleEnter.bind(this);
    this.handleKeyPress = this.handleKeyPress.bind(this);
  }
  componentDidMount() {
    document.addEventListener("keydown", this.handleKeyPress); // Use quoted strings for event names ('keydown') and callback should be called using 'this.'
  }
  componentWillUnmount() {
    document.removeEventListener("keydown", this.handleKeyPress);
  }
  handleEnter() {
    this.setState((state) => ({
      message: state.message + 'You pressed the enter key! '
    }));
  }
  handleKeyPress() {
    if (event.keyCode === 13) {
      this.handleEnter();
    }
  }
  render() {
    return (
      <div>
        <h1>{this.state.message}</h1>
      </div>
    );
  }
};
```

- `document.addEventListener(event, function(callback), optional(useCapture)`
- `document.removeEventListener(event, function(callback), optional(useCapture)`
- It is good practice to use this lifecycle method to do any cleanup on React components before they are unmounted or destroyed.
- Failure to remove the event listener can lead to potential memory leaks because the vent listener will continue to exist after the component is removed from the DOM. It could cause unexpected behavior in the application.
- Also, if the component is re-rendered and mounted again, it will register a new event listener, resulting in duplicate event listeners listening in on the same event.
- Note: Memory leaks can occur when components that are no longer required continue to hold on to memory resources.
  - If not properly cleaned up when the component is unmounted or removed from the DOM, it could accumulate over time and eventually lead to performance issues, crashes, or other unexpected behavior.

## Optimize Re-Renders with shouldComponentUpdate

- up until the current exercise, if any component receives new `state` or `props`, it re-renders itself and all its children.
- This is usually acceptable.
- React provides a lifecycle method that can be called when child components receive new `state` or `props`, and declare specifically if the components should update or not.
- It is `shouldComponentUpdate()` method, and it takes `nextProps` and `nextState` as parameters.

- This method is a useful way to optimize performance.
- For example,the default behavior is that the component re-renders when it receives new `props`, even if the `props` haven't changed.
- `shouldComponentUpdate()` can be used to prevent this by comparing the `props`.
- The method must return a `boolean` value that tells React whether or not to update the component.
- Compare `this.props` to the `nextProps` to determine if update is necessary or not, and return `true` or `false` accordingly.

```jsx
class OnlyEvens extends React.Component {
  constructor(props) {
    super(props);
  }
  shouldComponentUpdate(nextProps, (nextState)) {
    console.log('Should I update?');
    if (nextProps.value % 2 === 0) {
      // remember that 'nextProps' is not a number. It is an object that contains the next props of the component.
      // To access a specific prop value, the prop name must be used as a key in the 'nextProps' object, as shown in the example above.
      return false;
    } else {
      return true;
    }
  }
  componentDidUpdate() {
    console.log('Component re-rendered.');
  }
  render() {
    return <h1>{this.props.value}</h1>
  }
}

class Controller extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      value: 0
    };
    this.addValue = this.addValue.bind(this);
  }
  addValue() {
    this.setState(state => ({
      value: state.value + 1
    }));
  }
  render() {
    return (
      <div>
        <button onClick={this.addValue}>Add</button>
        <OnlyEvens value={this.state.value} />
      </div>
    );
  }
}
```

## Introducing Inline Styles

- Styling JSX elements created in React is a bit different from styling HTML.
- If styles are imported from a stylesheet, it isn't much different from styling HTML.
  - Apply a class t the JSX element using the `className` attribute, and apply styles to the class in the stylesheet.
- Another option is to apply inline styles, which is a very common method.

```HTML
<div style="color: yellow; font-size: 16px">Mellow Yellow</div>
```

- Above is HTML.
- JSX elements also use the `style` attribute.
- But the values can't be set to a `string` because of the way JSX is transpiled.
- Set the values equal to a JavaScrip `object` instead.

```JSX
class Colorful extends React.Component {
  render() {
    return (
      <div style={{color: "red", fontSize: 72}}>Big Red</div>
    );
  }
};
```

- Notice the use of double curly braces.
- Notice `px` is omitted from the font size.
  - all property value length units are assumed to be in `px` unless specified otherwise.
  - in order to use another unit, wrap the value and unit in quotes `{fontSize: "4em"}`
- Notice properties use camelCase instead of kebab-case.

## Add Inline Styles in React

- If there is a large set of styles, assign a style `object` to a constant to keep the code organized.

```jsx
const styles = { color: "purple", fontSize: 40, border: "2px solid purple"};

class Colorful extends React.Component {
  render() {
    return (
      <div style={styles}>Style Me!</div>
    );
  }
};
```

- Notice that `const styles` is assigned an object (wrapped in curly braces) and when setting `const styles` to the `style` attribute in the `div` element, it also needs to be wrapped in curly braces.

## Use Advanced JavaScript in React Render Method

- It is possible to write JavaScript directly in the `render` methods before the `return` statement.
- At this point, curly braces are not required since it is not yet within the JSX code.
- When using the variables declared as JS later in the code, it must be placed inside curly braces.

```jsx
const inputStyle = {    // inline style declared.
  width: 235,
  margin: 5
};

class MagicEightBall extends React.Component {d
  constructor(props) {
    super(props);
    this.state= {
      userInput: '',
      randomIndex: ''
    };
    this.ask = this.ask.bind(this);
    this.handleChange = this.handleChange.bind(this);
  }
  ask() {
    if (this.state.userInput) {   // 'ask' method is called when the button is clicked.
      this.setState({
        randomIndex: Math.floor(Math.random() * 20),  // 'randomIndex' generates a random integer between 0 and 19, and it is stored in the state.
        userInput: ''                                 // userInput is reset to an empty string.
      });
    }
  }
  handleChange(event) {
    this.setState({
      userInput: event.target.value
    });
  }
  render() {
        const possibleAnswers = [
          'It is certain',
          'It is decidedly so',
          'Without a doubt',
          'Yes, definitely',
          'You may rely on it',
          'As I see it, yes',
          'Outlook good',
          'Yes',
          'Signs point to yes',
          'Reply hazy try again',
          'Ask again later',
          'Better not tell you now',
          'Cannot predict now',
          'Concentrate and ask again',
          "Don't count on it",
          'My reply is no',
          'My sources say no',
          'Most likely',
          'Outlook not so good',
          'Very doubtful'
        ];
        const answer = this.state.randomIndex;  // const variable 'answer' is assigned with the randomly generated index value
    return (
      <div>
        <input type="text" value={this.state.userInput} onChange={this.handleChange} style={inputStyle} />
        { /* 1. When text is entered in the input field, it calls the 'handleChange' method, updates the 'userInput', making it a controlled input.
                'inputStyle' defined globally is assigned to 'style' */ }
        <br />
        <button onClick={this.ask}>Ask the Magic Eight Ball!</button>
        { /* 2 when button is clicked, it calls the 'ask' method. */ }
        <br />
        <h3>Answer:</h3>
        <p>{possibleAnswers[answer]}</p> 
        { /* When rendered, the browser page will display a randomly generated message from the 'possibleAnswers' array with the randomly generated index value */ }
      </div>
    );
  }
};
```

- Add some more code so that pressing enter has the same effect as clicking the button.
- Make sure to clean up the components.
- For the ask() method, ensure that key press only works if text is entered in the input field

```jsx
const inputStyle = {      // inline styling
  width: 235,
  margin: 5
};

class MagicEightBall extends React.Component {  // stateful component with constructor and state
  constructor(props) {                        
    super(props);
    this.state = {
      userInput: '',
      randomIndex: ''
    };
    this.ask = this.ask.bind(this);                         // 'bind' section within constructor
    this.handleChange = this.handleChange.bind(this);
    this.handleKeyPress = this.handleKeyPress.bind(this);
  }
  componentDidMount() {                                         // Add lifecycle methods
    document.addEventListener("keydown", this.handleKeyPress);
  }
  componentWillUnmount() {
    document.removeEventListener("keydown", this.handleKeyPress);
  }
  handleKeyPress(event) {                                   // Add other methods
    if (this.state.userInput && event.keyCode === 13) {
      this.ask();
    }
  }
  ask() {
    if (this.state.userInput) {
      this.setState({
        randomIndex: Math.floor(Math.random() * 20),
        userInput: ''
      });
    }
  }
  handleChange(event) {
    this.setState({
      userInput: event.target.value
    });
  }
  render() {                                      // render method section
    const possibleAnswers = [                     // Add JavaScript if necessary within render() method before 'return'
      'It is certain',
      'It is decidedly so',
      'Without a doubt',
      'Yes, definitely',
      'You may rely on it',
      'As I see it, yes',
      'Outlook good',
      'Yes',
      'Signs point to yes',
      'Reply hazy try again',
      'Ask again later',
      'Better not tell you now',
      'Cannot predict now',
      'Concentrate and ask again',
      "Don't count on it",
      'My reply is no',
      'My sources say no',
      'Most likely',
      'Outlook not so good',
      'Very doubtful'
    ];
    const answer = this.state.randomIndex;
    return (                                      // return section within render() method
      <div>
        <input type="text" value={this.state.userInput} onChange={this.handleChange} style={inputStyle} />
        <br />
        <button onClick={this.ask}>Ask the Magic Eight Ball!</button>
        <br />
        <h3>Answer:</h3>
        <p>{possibleAnswers[answer]}</p>
      </div>
    );
  }
};
```

## Render with an If-else condition

- Another application of JS when rendering is to tie the elements that are rendered to a condition.
- When the condition is true, one view renders. If false, it renders a different view.
- This is achievable using a standard `if/else` statement in the `render()` method.

```jsx
class MyComponent extends React.Component {
  constructor(props){
    super(props);
    this.state = {
      display = true;
    }
    this.toggleDisplay = this.toggleDisplay.bind(this);
  }
  toggleDisplay() {
    this.setState((state) => ({
      display: !state.display
    }));
  }
  render() {
    if (this.state.display) {
      return (
        <div>
          <button onClick={this.toggleDisplay}>Toggle Display</button>
          <h1>Displayed!</h1>
        </div>
      )
    } else {
      return (
        <div>
          <button onClick={this.toggleDisplay}>Toggle Display</button>
        </div>
      )
    }
  }
};
```

## Use && for a More Concise Conditional

- There is a more concise method to achieve the same result shown in the previous exercise.
- If there are multiple conditions in a component and each condition renders a slightly different UI based on the `else if` conditions, it is prone to error.
- Use the `&&` logical operator to perform conditional logic.
- This is possible since we're working with boolean values at the moment.

`{condition && <p>markup</p>}`

- If the condition is true, it returns the markup.
- If false, the operation will evaluate the condition and return nothing.
- These statements can be included directly in the JSX, and multiple conditions can be stringed together by joining each condition with a `&&`.
- This allows for handling complex logic in the `render()` method without the redundancy.

```jsx
class MyComponent extends React.Component :{
  constructor(props) {
    super(props);
    this.state = {
      display: true
    }
    this.toggleDisplay = this.toggleDisplay.bind(this);
  }
  toggleDisplay() {
    this.setState((state) => ({
      display: !state.display
    }));
  }
  render () {
    return (
      <div>
        <button onClick={this.toggleDisplay}>Toggle Display</button>
        {this.state.display && <h1>Displayed!</h1>} 
        { /* Notice that it does not require 'if' statements. 
             Simply wrap the condition and the markup separated by '&&" in curly braces */ }
      </div>
    );
  }
};
```

## Use a Ternary Expression for Conditional Rendering

- There is one more way to use built-in JS conditionals for rendering: ternary operator.
- It is often used as a shortcut for `if/else` statements in JS.
- They're not quite as robust as traditional `if/else` statements, but it is popular among React developers for various reasons.
- One of the main reasons is that it can be inserted directly into the JSX code.
- Notice that traditional `if/else` statements are always placed outside the return statement.

`condition ? expressionIfTrue : expressionIfFalse;`

```jsx
const inputStyle = {
  width: 235,
  margin: 5
};

class CheckUserAge extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      input: '',
      userAge: ''
    }
    this.submit = this.submit.bind(this);
    this.handleChange = this.handleChange.bind(this);
  }
  handleChange(event) {
    this.setState({
      input: event.target.value,
      userAge: ''
    });
  }
  submit() {
    this.setState((state) => ({
      userAge: state.input
    }));
  }
  render() {
    const buttonOne = <button onClick={this.submit}>Submit</button>;
    const buttonTwo = <button>You May Enter</button>;  // add (onClick={this.handleChange}) to buttonTwo and buttonThree to reset the input field when clicked on
    const buttonThree = <button>You Shall Not Pass</button>;
    return (
      <div>
        <h3>Enter Your Age to Continue</h3>
        <input 
          style={inputStyle}
          type='number'
          value={this.state.input}
          onChange={this.handleChange}
        />
        <br />
        {this.state.userAge == '' ? buttonOne :             // if input field is an empty string, render buttonOne
         this.state.userAge >= 18 ? buttonTwo : buttonThree}
      </div>
    );
  }
}
```

## Render Conditionally from Props

- The `if/else`, `&&`, and `ternary operator` conditionals can be used with another React feature: props.
- Using props to conditionally render code is very common among React developers.
- The value of a given prop is used to automatically make decisions about what to render.

```jsx
class Results extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return <h1>{this.props.fiftyFifty? "You Win!" : "You Lose!"}</h1>;
  }
}

class GameOfChance extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      counter: 1
    };
    this.handleClick = this.handleClick.bind(this);
  }
  handleClick() {
    this.setState(prevState => {    // prevState is a parameter that represents the previous sate of a component before an update.
      return(
        counter: prevState.counter + 1
      )
    });
  }
  render() {
    const expression = Math.random() >= 0.5;
    return (
      <div>
        <button onClick={this.handleClick}>Play Again</button>
        <Results fiftyFifty = {expression} />
        <p>{'Turn: ' + this.state.counter}</p>
      </div>
    );
  }
}
```

- Note: It doesn't matter whether the child component is defined before the parent component and vice versa, as long as it's referencing the appropriate state and props.

## Change Inline CSS Conditionally Based on Component State

- CSS can be rendered conditionally based on the state of a React component.
- Check for a condition, if the condition is satisfied, modify the styles object that is assigned to the JSX elements in the render method.

- Traditional approach to applying styles by modifying DOM elements directly (common in jQuery) requires the developer to keep track of element changes, and also handle actual manipulations directly.
- Keeping track of changes can become overbearing, and potentially make the UI unpredictable.
- By setting a style object based on a condition, the developer has control over how the UI should look as a function of the application's state.
- The flow of information is clear, and it move only in one direction.
- This is the preferred way of writing applications with React.

```jsx
class GateKeeper extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      input: ''
    };
    this.handleChange = this.handleChange.bind(this);
  }
  handleChange(event) {
    this.setState({
      input: event.target.value
    })
  }
  render() {
    let inputStyle = {
      border: '1px solid black'
    };
    {if (this.state.input.length > 15) {  // This is the conditional to check if the input length is greater than 15 characters
      inputStyle = {                      // if so, the inputStyle changes to the specified border style. 
        border: '3px solid red'
      }
    }};
    return (
      <div>
        <h3>Don't Type Too Much:</h3>
        <input
          type='text'
          style={inputStyle}
          value={this.state.input}
          onChange={this.handleClick} />
      </div>
    );
  }
};
```

## Use Array.map() to Dynamically Render Elements

- Conditional rendering is useful, but it many be necessary to render an unknown number of elements.
- Often in reactive programming, the programmer has no way of knowing what the state of an application is until runtime.
- This is because so much depends on a user's interaction with the program.
- The code must be written to handle the unknown state, ahead of time.
- Use of `Array.map()` in React illustrates this concept.

- For example, if there is a simple program that creates a 'To Do List', it is impossible for the programmer to know how many items the user has on his/her list.
- The component must be set up to dynamically render the correct number of list elements.

```jsx
const textAreaStyles = {
  width: 235,
  margin: 5
};

class MyToDoList extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      userInput: '',
      toDoList: []
    };
    this.handleSubmit = this.handleSubmit.bind(this);
    this.handleChange = this.handleChange.bind(this);
  }
  handleSubmit() {
    const itemsArray = this.state.userInput.split(',');
    this.setState({
      toDoList: itemsArray
    });
  }
  handleChange(event) {
    this.setState({
      userInput: event.target.value
    });
  }
  render() {
    const items = this.state.toDoList.map(i => <li>{i}</li>)
    // sibling child elements created by a mapping operation need to be supplied with a unique key attribute.
    // this.state.toDoList.map((item, index) => (<li key={index}>{item}</li>))
    // This will be covered in the next exercise.
    return (
      <div>
        <textarea
          onChange={this.handleChange}
          value={this.state.userInput}
          style={textAreaStyles}
          placeholder='Separate Items With Commas'
        />
        <br />
        <button onClick={this.handleSubmit}>Create List</button>
        <h1>My "To DO" List</h1>
        <ul>{items}</ul>
      </div>
    );
  }
}
```

- When the user enters the list items, separated by commas as specified with the placeholder, and clicks the button, it will call the 'handleSubmit' method.
- 'handleSubmit' will split the entered items `userInput` at every 'comma' and assign the result to a variable 'itemsArray'
- the empty array 'toDoList' in the state will be updated with 'itemsArray' data.
- When rendered, the updated 'toDoList' in the state will be mapped.
  - each item 'i' will be dynamically rendered as a list item `<li>` and stored in the variable `items`
- `items` is rendered into an unordered list `<ul>`

## Give Sibling Elements a Unique Key Attribute

- When an array of elements is created, each element requires a `key` attribute set to a unique value.
- React uses these `keys` to keep track of which items are added, changed, or removed.
- This helps make the re-rendering process more efficient when the list is modified.
- Note: Keys only need to be unique between sibling elements, not globally unique in the application.

```jsx
const frontEndFrameworks = [
  'React',
  'Angular',
  'Ember',
  'Knockout',
  'Backbone',
  'Vue'
];

function Frameworks() {
  const renderFrameworks = 
  frontEndFrameworks.map((item) => <li key={item}>{item}</li>);
  return (
    <div>
      <h1>Popular Front End JavaScript Frameworks</h1>
      <ul>
      {renderFrameworks}
      </ul>
    </div>
  );
};
```

- It is best practice to make the key something that uniquely identifies the element being rendered.
- As a last resort, the array index may be used, but this should be avoided.
- If the order of the elements change, or if new elements are added, or elements are removed from the array, the index may point to an unintended element.
- using the value of the `item` as the `key` value would be the safest approach.

## Use Array.filter() to Dynamically Filter an Array

- Another method commonly used in React is the `filter()` method.
- It filters the contents of an array based on a condition, and returns a new array.

```jsx
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      users: [
        {
          username: 'Jeff',
          online: true
        }.
        {
          username: 'Alan',
          online: false
        },
        {
          username: 'Mary',
          online: true
        },
        {
          username: 'Jim',
          online: false
        },
        {
          username: 'Sara',
          online: true
        },
        {
          username: 'Laura',
          online: true
        }
      ]
    };
  }
  render() {
    const usersOnline = this.state.users.filter(user => user.online); // filter the users who are online by accessing the 'online' property of each user object
    const renderOnline = usersOnline.map((user) => <li key={user.username}>{user.username}</li>); // map and render the names of the online users
    return (
      <div>
        <h1>Current Online Users:</h1>
        <ul>
          {renderedOnline}
        </ul>
      </div>
    );
  }
}
```
