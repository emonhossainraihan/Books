# Chapter 2. JavaScript for React
## Function Expressions

Another option is to use a function expression. This just involves creating the function as a variable.

> One thing to be aware of when deciding between a function declaration and a function expression is that function declarations are hoisted and function expressions are not. In other words, you can invoke a function before you write a function declaration. You cannot invoke a function created by a function expression. This will cause an error. 

```js
// Invoking the function before it's declared
hey(); // <-- TypeError: hey is not a function
// Function Expression
const hey = function() {
  alert("hey!");
};
```


## Returning objects

What happens if you want to return an object? Consider a function called person that builds an object based on parameters passed in for firstName and lastName:

```js
const person = (firstName, lastName) =>
    {
        first: firstName,
        last: lastName
    }
console.log(person("Brad", "Janson"));
```

As soon as you run this, you’ll see the error: Uncaught SyntaxError: Unexpected token :. To fix this, just wrap the object you’re returning with parentheses:

```js
const person = (firstName, lastName) => ({
  first: firstName,
  last: lastName
});
console.log(person("Flad", "Hanson"));
```

These missing parentheses are the source of countless bugs in JavaScript and React apps, so it’s important to remember this one!

## Declaring Variables
- The const Keyword
- The let Keyword
- Template Strings
## Creating Functions
- Function Declarations
- Function Expressions
- Passing arguments
- Default Parameters
- Arrow Functions
- Arrow functions and scope
## Compiling JavaScript
## Objects and Arrays
- Destructuring Objects
- Assignment without declaration: `({a, b} = {a: 1, b: 2});` The parentheses ( ... ) around the assignment statement are required when using object literal destructuring assignment without a declaration.
- Destructuring Arrays
- Object Literal Enhancement
- The Spread Operator
## Asynchronous JavaScript
- Simple Promises with Fetch
- Async/Await
- Building Promises
## Classes
## ES6 Modules
- CommonJS

# Chapter 3. Functional Programming with JavaScript

> In a declarative program,the syntax itself describes what should happen, and the details of howthings happen are abstracted away.

## Functional Concepts
- Immutability
- Pure Functions
- Data Transformations
- Higher-Order Functions
- Recursion
- Composition

## Chapter 6. React State Management

[codesandbox](https://codesandbox.io/s/star-component-ln3u7?file=/src/App.js)

### Creating Custom Hooks
When you have a large form with a lot of input elements, you may betempted to copy and paste these two lines of code:

```js
value={title}
onChange={event => setTitle(event.target.value)}
```

We can package the details necessary to create controlled form components into a custom hook. We could create our own useInput hook where we can abstract away the redundancy involved with creating controlled form inputs:

```js
import { useState } from "react";

export const useInput = initialValue => {
  const [value, setValue] = useState(initialValue);
  return [
    { value, onChange: e => setValue(e.target.value) },
    () => setValue(initialValue)
  ];
};
```
Then we can use it as:

```js
export default function Form() {
  const [titleProps, resetTitle] = useInput("");


const submit = event => {
  event.preventDefault();
  onNewColor(titleProps.value);
  resetTitle();
};

return (
  <form onSubmit={submit}>
    <input
      {...titleProps}
      type="text"
      placeholder="color title..."
      required
    />
    <button>ADD</button>
  </form>
);
}
}
```
