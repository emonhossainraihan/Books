## Main Roadblocks to Learning React

- New Design Pattern: modular and declarative design
- **JSX** language: we can type HTML into a JavaScript statement, without quotes surrounding the HTML
wait, what? :dizzy_face: In reality, this type of code is "transpiled" from XML to EcmaScript 5, so browsers can understand it
- Babel & Transpiling

## Good Reasons for learning React
- It's fast
- Modular design
- Scalability
- Flexibility

## Reactive Programming

While React is considered to be mostly dealing with the view areas of your
application, don't believe the myths that React is strictly the "view" in the MVC
(model-view-controller) pattern you're probably already familiar with.

We can refer to programming with React as functional templating.
Not to be confused with functional programming languages. Here I simply mean
that your React components have a specific function to perform and that this is a
way to customize your components with unique capabilities. Whereas HTML
provides us with a set of elements (as HTML tags) that handle the layout of our
web application and provide interfacing with JavaScript code via attributes, React
is that… and a lot more.

## The Essentials

```js
React.createElement(type,props,children)
```
Here, we programmatically created HTML elements using React method
createElement. 
```js
let link1 = React.createElement('a', {href: '#'}, "Save");
let link2 = React.createElement('a', {href: '#'}, "Delete");
let nav = React.createElement(MyNav, {flat: true}, link1, link2);
```
ou can go like this forever, adding as many children as required by your
application. As long as we use the leading capital letter
React knows we're referring to a custom element. No need to use surrounding
quotes. So, while in ES5, you would use createElement function, in JSX you could create exactly the same
functionality by simply writing it out as follows: `let link1 = <a href = "#">Save</a>` you can also
clone existing elements using cloneElement `React.cloneElement(element, props, children)`. This is reminiscent of extending object functionality in traditional
Object-Oriented programming. Here, we're somewhat imitating OOP functionality.


React provides render method on the main ReactDOM object as shown
below. In reactive programming ReactDOM is the second most important object
after React. 
```js
ReactDOM.render(reactElement, domContainerNode)
```

Here domContainerNode is the parent element on which reactElement will be
rendered, re-rendered or attached for the first time (mount.) If you have an element already associated with a variable name, you can look it
up using ReactDOM.findDOMNode: 
```js
ReactDOM.findDOMNode( element )
```
This statement returns the DOM node associated with the given element. Note,
that this will only work only after element has been rendered to the DOM with the
render method. Until then, it is not findable in the DOM, even if it was already
created.

## Special Props

- **children:** he prop name children is utomatically added to this.props by
**React.createElement**
- **className:** This prop corresponds to the HTML's class attribute
- **htmlFor:** Same as className only for the "for" attribute
- **key:** he key prop uniquely identifies a ReactElement. It's used with elements in
arrays
- **ref:**  ref prop accepts a callback function
- **style:** The style prop accepts an object of styles, instead of a string. n React, there is
no mechanism for specifying CSS styles as a text string.

## PropTypes
Let's say we already have a React component created, and
named ReactComponent. 
```js
ReactComponent.propTypes = {
    name: React.PropTypes.string
}
```
## Class Component Options
Components are defined by createClass method existing on the main React object:
```js
var MyComponent = React.createClass({

    displayName: 'MyComponent',
    /* This is the core of your React Class
        options and lifecycle methods will be written here */
    render: function() {
        // Once rendered, let's return a newly created element
        return React.createElement( /* … */ );
    }
});
```
## Component Options

Components hold the propTypes object and two methods that return an object:
- propTypes object mapping prop names to types
- getDefaultProps function returning object
- getInitialState function returning object

## Component Instances
- The this keyword within a component refers to itself
- One component instance may persist over multiple equivalent ReactElements

## Properties
- Property **this.props** contains any props passed to React.createElement through
tag attributes
- The **this.state** property contains state set by setState and getInitialState
methods

**forceUpdate()** immediately re-renders the component to the DOM.

## Gem 2 - Render Method
Until the render method is called, the react's component isn't even "mounted" to the actually
JavaScript DOM, nor will it be displayed. And it's possible to create React
components without mounting them. We know that render triggers an update of the data set (or state of the
component). But when should the data be updated? :thinking:

## Gem 4 - Virtual DOM and Bandwidth Salvation
Reactive programming isn't just a bunch of ajax calls that pull the data and
replace an HTML element. It's much more sophisticated.

## Gem 4 - Two Distinct Ways of Initializing a React Class
EcmaScript5 example looks as follows:
```js
var NewComponent = React.createClass({
    getInitialState() {
        return { /* initial state */ };
    }
});
```
EcmaScript6:
```js
class NewComponent extends React.Component( {
    constructor(props) {
        super(props);
        this.state = { /* initial state */ };
    }
} );
```

## Gem 5 - States & Life Cycles
Each component will usually control its own states via following helper
methods. They are designed to modify or update component's state at a unique time
during the application flow or component's Life Cycle.
```js
var MyComponent = React.createClass( {

    displayName:      'MyComponent',
    // This is almost like a component's constructor!
    getInitialState:      function() { … },
    // Component mounting events
    componentWillMount: function() { … },
    componentDidMount: function() { … },
    componentWillUnmount: function() { … },
    // Component updating events
    componentWillReceiveProps: function() { … },
    componentWillUpdate: function() { … },
    componentDidUpdate: function() { … },
    shouldComponentUpdate:       function() { … }
    // Render the component to the DOM
    render: function() { /* return something */ }

});
```
That's a whole lot of Wills and Dids. But what do they all mean? :worried:

## Gem 6 - Component Mounting
component is a programmatic (declarative) way to
render what you want in your application. eact doesn't actually care about where or how you choose to render those
elements. Whether it is JavaScript DOM or elsewhere. This can sound surprising
at first, because React is known for being primarily as a front end library. :hushed:

>A react component is a fusion between its state and its rendering method.

React is an isomorphic framework. It's functionality can be mapped to arbitrary
output. Not just JSX-style HTML UI elements. The virtual DOM provided by react library is exactly just that: virtual. It
doesn't physically exists within actual JavaScript DOM until it actually needs to be
used by the application.

Just think about it this way. The JavaScript's DOM is a physical tree of HTML
elements stored in memory. It is populated while the page is loading into your
browser.

React, on the other hand, doesn't even touch that DOM tree. As discussed in
one of the previous gems, it adds or removes components from or to its own
virtual DOM, which is stored completely in memory. An element becomes
physically represented in memory of the render target usually only when the
component is purposely used within your application.

```js
var component = React.createElement( ComponentDefinition );
/* In reality, ComponentDefinition would correspond to a component like 
LoginScreen, NavigationMenu or Button. 
It is not yet physically existent anywhere in the
primary JavaScript's document (DOM) object. But this is true only until 
render method is executed on this component.
*/
React.render(component, container);
//Here, container is just some is of a DIV or other HTML element
```
This mounting mechanism make React a versatile library. Because at its
basic principle, React also doesn't care whether the final result is rendered in the
DOM or elsewhere.

## props
In React, props take on the "pure" ideology. This means you can pass them,
under the condition that your react component will not be changing their values
from within itself. This is exactly what makes react props read-only. It's good to
stick to that rule.

## Handling Component Events
Always remember that a React component has state. The whole purpose of
components is to be tied to a custom state represented by that component's object.
A state is an object with data. But components also have helper functions that
make it easier to control how these states will work in a given context. 

### Method 1 - getInitialState
Each component is in charge of rendering its own state but the method
getInitialState is always called before our render function. This has similar
functionality to an object constructor function. Here we set the default values.
```js
var Example = React.createClass( {
    getInitialState: function() {
        return {
            state: 0;
        }
    }
});
```
You can use this method interchangeably with the default constructor method
provided in EcmaScript 6:
```js
class Example extends React.Component( {
    constructor: function() {
        this.state: 0;
    }
});
```
### Method 2 - componentDidMount
componentDidMount is called automatically by React when a component is
rendered. By adding it to your custom React component, you are overloading it.
Overloading means, adding your own functionality to the method that already exists
in the default  React component object, from which you are extending your own
custom component. That's the whole purpose of using extend keyword. We're
extending default functionality of React's  component object already provided by
the library. This method is always called after
executing render command from the component.

