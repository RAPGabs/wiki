---
id: reactandnextjs
title: React & Next JS
---

React is a JavaScript library for building user interfaces.It is a declarative, efficient, and flexible JavaScript library for building reusable UI components. It is an open-source, component-based front end library which is responsible only for the view layer of the application. It was initially developed and maintained by Facebook and later used in its products like WhatsApp & Instagram.

### Components, Props & Two way binding

-**Components And Props:**Components let you split the UI into independent, reusable pieces, and think about each piece in isolation.Conceptually, components are like JavaScript functions. They accept arbitrary inputs (called `“props”`) and return React elements describing what should appear on the screen.
o define a React component class, you need to extend `React.Component`.

**Note:**Whether you declare a component as a function or a class, it must never modify its own props hence, props are read-only in nature.
React is pretty flexible but it has a single strict rule:
- All React components must act like pure functions with respect to their props.Pure functions are those functions which do not change or make any changes in the arguments.

**Syntax**
```bash
//Class-Component
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}

//Function-Component
function Comment(props) {
  return (
    <div className="Comment">
      <UserInfo user={props.author} />
      <div className="Comment-text">
        {props.text}
      </div>
      <div className="Comment-date">
        {formatDate(props.date)}
      </div>
    </div>
  );
}

//Sample Code-Function Component
return (
      <>
        <a className="btnStyle btnPrim display-block mb-10" style={{ textDecoration: 'none' }} onClick={handleViewAlerts}>View Alerts</a>
        <Modal id="uwAlerts" show={uwAlerts} onEscapeKeyDown={handleViewAlerts} centered>
          <ModalBody className='custPopup mx-0 action-modal-style'>
            <div className='mfp-wrap mfp-close-btn-in mfp-auto-cursor mfp-ready'>
              <div className='mfp-container mfp-s-ready mfp-inline-holder'>
                <div className='mfp-content'>
                  <div className='popupMedium'>
                    <div>
                      <div>
                        <h3>
                          Underwriter rules
                        </h3>
                      </div>
                      <ul>
                        {
                          summary?.Rules?.MatchingRules?.map((value,index)=>
                          <li key={index}>
                            <h4>{index+1}. {value.Description}</h4>
                          </li>
                          )
                        }
                      </ul>
                      <div className='mt-4'>
                        <button className="btnStyle btnReject" onClick={handleViewAlerts}>
                          Close
                        </button>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </ModalBody>
       </Modal>
      </>
      
    );

//Pure Function Example
function sum(a, b) {
  return a + b;
}

//Impure Function Example
function withdraw(account, amount) {
  account.total -= amount;
}
```
-**Two-Way Binding:**Two data binding means

- The data we changed in the view has updated the state.
- The data in the state has updated the view.

In the code example given below, we have attached an `onChange` event handler to the input element and also value attribute is connected to the `this.state.name` so that the value attribute is always synced with `this.state.name` property.

Whenever the user changes an input in the view it triggers the onChange event handler then it calls the this.setState method and updates the this.state.name property value at final the UserInput component is re-rendered with the updated changes.

This is also called controlled component because the value of an input element is controlled by the react.

**Syntax**
```bash
class UserInput extends React.Component{

  state = {
      name:"reactgo"
  }
  handleChange = (e) =>{
    this.setState({
        name: e.target.value
    })
  }

   render(){
    return(
      <div>
       <h1>{this.state.name}</h1>
       <input type="text"
         onChange={this.handleChange}
         value={this.state.name} />
      </div>
      )
   }
}

//Two way data binding in React hooks
import React,{useState} "react";

function App(){
   const [name,setName] = useState('');

  const handleChange = (e)=>{
     setName(e.target.value);
  }

 return (
   <div>
     <input onChange={handleChange} value={name} />
     <h1>{name}</h1>
   </div>
 )
}

export default App;
```
#### References
Please refer to the below references for more detail-

- **ReactJs Org Resources** - [``https://reactjs.org/docs/react-component.html``](https://reactjs.org/docs/react-component.html)

- **React-Go Resources** - [``https://reactgo.com/two-way-data-binding-react/``](https://reactgo.com/two-way-data-binding-react/)

### State & Lifecycle

-**State:**The state is an instance of React Component Class can be defined as an object of a set of observable properties that control the behavior of the component. In other words, the State of a component is an object that holds some information that may change over the lifetime of the component.States can be used in Class Components, Functional components with the use of React Hooks (useState and other methods).It is generally updated by event handlers.

When using State, we need the state of a component to always exist — so we need to set an initial state. We can do so by defining our state in the constructor of our component class, like so:

```bash
class MyClass extends React.Component {
  constructor(props){
    super(props);
    this.state = { attribute : "value" };
  }
} 
```

- Updating State
The next thing to know about state is that it should never be explicitly updated. React will use an observable object for state, which allows the component to behave accordingly.

If for example, we we’re to update a components’ state like so:
```bash
this.state.attribute = "changed-value";
```

- setState()

This is why we use the built-in React method of setState(). It takes a single parameter and expects an object containing our set of values to be updated.

The method will update our state and then call the render() method to re-render the page. Therefore the proper way to update our state, is like so:
```bash
this.setState({attribute: “changed-value”});
```

-**Lifecycle:**In general, we might define a lifecycle as birth, growth & death. And our React components follow this cycle as well: they’re created (mounted on the DOM), they experience growth (by updating) and they die (unmounted from the DOM). This is the component lifecycle!

Within the lifecycle of a component, there are different phases. These phases each have their own lifecycle methods.These methods are:

- Initialization
- Mounting
- Updating
- Unmounting

#### References
Please refer to the below references for more detail-

- **ReactJs Org Resources** - [``https://reactjs.org/docs/state-and-lifecycle.html``](https://reactjs.org/docs/state-and-lifecycle.html)

- **Medium Blog By Timothy Robards** - [``https://itnext.io/react-understanding-state-lifecycle-d45df5d2cf3f``](https://itnext.io/react-understanding-state-lifecycle-d45df5d2cf3f)

### Reconcillation & Virtual DOM

The virtual DOM (VDOM) is a programming concept where an ideal, or “virtual”, representation of a UI is kept in memory and synced with the “real” DOM by a library such as ReactDOM. This process is called `reconciliation`.
This approach enables the declarative API of React: You tell React what state you want the UI to be in, and it makes sure the DOM matches that state. This abstracts out the attribute manipulation, event handling, and manual DOM updating that you would otherwise have to use to build your app.

Since “virtual DOM” is more of a pattern than a specific technology, people sometimes say it to mean different things. In React world, the term “virtual DOM” is usually associated with React elements since they are the objects representing the user interface. React, however, also uses internal objects called “fibers” to hold additional information about the component tree. They may also be considered a part of “virtual DOM” implementation in React.

#### References
Please refer to the below references for more detail-

- **ReactJs Org Resources** - 

[``https://reactjs.org/docs/faq-internals.html``](https://reactjs.org/docs/faq-internals.html)

[``https://reactjs.org/docs/reconciliation.html``](https://reactjs.org/docs/reconciliation.html)

### Handling Events

Handling events with React elements is very similar to handling events on DOM elements. There are some syntax differences:

- React events are named using camelCase, rather than lowercase.
- With JSX you pass a function as the event handler, rather than a string.

**Examples**
```bash
//For example, the HTML:
<button onclick="activateLasers()">
  Activate Lasers
</button>

//In React
<button onClick={activateLasers}>
  Activate Lasers
</button>
```

Another difference is that you cannot return false to prevent default behavior in React. You must call preventDefault explicitly. For example, with plain HTML, to prevent the default form behavior of submitting, you can write:
```bash
function Form() {
  function handleSubmit(e) {
    e.preventDefault();
    console.log('You clicked submit.');
  }

  return (
    <form onSubmit={handleSubmit}>
      <button type="submit">Submit</button>
    </form>
  );
}
```

#### References
Please refer to the below references for more detail-

- **ReactJs Org Resources** - 

[``https://reactjs.org/docs/handling-events.html``](https://reactjs.org/docs/handling-events.html)


### React Refs
Refs provide a way to access DOM nodes or React elements created in the render method.

-**When to Use Refs**

There are a few good use cases for refs:

- Managing focus, text selection, or media playback.
- Triggering imperative animations.
- Integrating with third-party DOM libraries.
- Avoid using refs for anything that can be done declaratively.

For example, instead of exposing open() and close() methods on a Dialog component, pass an isOpen prop to it.

**Example**
```bash
//Creating Refs
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.myRef = React.createRef();
  }
  render() {
    return <div ref={this.myRef} />;
  }
}

//Accessing Refs
const node = this.myRef.current;
```

#### References
Please refer to the below references for more detail-

- **ReactJs Org Resources** - 

[``https://reactjs.org/docs/refs-and-the-dom.html``](https://reactjs.org/docs/refs-and-the-dom.html)

## NextJS
Next.js is a flexible React framework that gives you building blocks to create fast web applications.

### Benefits
Broadly, there are three verticals of benefits that Next JS can help you avail -

- Benefits for business
- Benefits for marketing
- Benefits for development

#### References
Please refer to the below references for more detail-

- **NextJS Documentation** - [``https://nextjs.org/docs/getting-started``](https://nextjs.org/docs/getting-started)

- **Medium Blog** - [``https://medium.com/eincode/what-are-the-benefits-of-the-next-js-framework-7c5b083c8d23``](https://medium.com/eincode/what-are-the-benefits-of-the-next-js-framework-7c5b083c8d23)

### SCSS, Environment Variables, And Routing

-**SCSS:**Next.js allows you to import Sass using both the `.scss` and `.sass` extensions. You can use component-level Sass via CSS Modules and the `.module.scss` or `.module.sass` extension.

Before you can use Next.js' built-in Sass support, be sure to install sass:

```bash
npm install --save-dev sass
```
>Note: Sass supports two different syntaxes, each with their own extension. The .scss extension requires you use the SCSS syntax, while the .sass extension requires you use the Indented Syntax ("Sass"). 
>If you're not sure which to choose, start with the .scss extension which is a superset of CSS, and doesn't require you learn the Indented Syntax ("Sass").

-**Environment Variables:**Next.js comes with built-in support for environment variables, which allows you to do the following:

- Use .env.local to load environment variables
- Expose environment variables to the browser by prefixing with `NEXT_PUBLIC_...`

**Loading Environment Variables**

Next.js has built-in support for loading environment variables from `.env.local` into `process.env`.

An example `.env.local`:
```bash
DB_HOST=localhost
DB_USER=myuser
DB_PASS=mypassword
```
This loads `process.env.DB_HOST`, `process.env.DB_USER`, and `process.env.DB_PASS` into the Node.js environment automatically allowing you to use them in Next.js data fetching methods and API routes.

For example, using `getStaticProps`:
```bash
// pages/index.js
export async function getStaticProps() {
  const db = await myDB.connect({
    host: process.env.DB_HOST,
    username: process.env.DB_USER,
    password: process.env.DB_PASS,
  })
  // ...
}
```

-**Routing:**Next.js has a file-system based router built on the concept of pages.When a file is added to the `pages` directory, it's automatically available as a route.The files inside the `pages` directory can be used to define most common patterns.

- **Index Routes:**The router will automatically route files named index to the root of the directory.

- **Nested Routes:**The router supports nested files. If you create a nested folder structure, files will automatically be routed in the same way still.

-**Dynamic route segments:**To match a dynamic segment, you can use the bracket syntax. This allows you to match named parameters.

#### References
Please refer to the below references for more detail-

- **NextJS Documentation**-

[``https://nextjs.org/docs/routing/introduction#nested-routes``](https://nextjs.org/docs/routing/introduction#nested-routes)

[``https://nextjs.org/docs/basic-features/built-in-css-support``](https://nextjs.org/docs/basic-features/built-in-css-support)

[``https://nextjs.org/docs/basic-features/environment-variables#loading-environment-variables``](https://nextjs.org/docs/basic-features/environment-variables#loading-environment-variables)
