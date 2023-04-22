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
