# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png)

## Review Guide: ES6 and Intermediate React
Below, you'll find key terms, key concepts, key code snippets, and further reading - all covering the basics of ES6, functional components, component lifecycle, unidirectional flow, and immutable data.

### Key Terms & Definitions

* **Arrow Functions**
  - This is a more concise syntax for declaring functions.
  - It can be simplified further if the function does nothing except a return.
  - `const addTwo = num => num + 2;`
  - Arrow functions don't change the definition of `this`.
  - If `this` is already defined in the scope and you call an arrow function, you can access `this` directly.
  * Refer to the "Key Code Snippets" section below for examples

* **Component Lifecycle**
  - React class components have lifecycle methods that are invoked at certain stages of a component's "life" on the DOM. Some of the life cycle methods you'll use frequently include:
    - `constructor()`: Initializes state, binds methods.
    - `componentDidMount()`: Makes AJAX requests, gets DOM refs, binds event listeners, sets `state` if necessary.
    - `componentWillUnmount()`: Unbinds event listeners, performs other clean up.
    - `componentWillReceiveProps()`: Updates `state` based on changes in components.
    - `render()`: Returns markup/UI.
  - React components' lifecycle events fall into three broad categories:
    - Initializing/mounting
    - Updating
    - Destruction/unmounting


![Life Cycles](https://ga-instruction.s3.amazonaws.com/json/REACT/assets/unit3/React_Component_Lifecycle.png)

* **ES6**
  * ES6 is also referred to or part of ES2015, ECMAScript, and ESNext.
  * ES6 is a standardized specification of JavaScript features introduced in 2015.
  * ES6 adds many new features, such as:
    * Arrow functions - `const doStuff = stuff => stuff + 5;`
    * `const` and `let` - `const name = 'Jim'`; `let age = 25;`
    * Object literal shorthand - `const name = 'Jim', jim = { name };`
    * Template literals - `const greet = person => 'Hi, ${person.firstName} ${person.lastName};'`
    * Imports and modules - `import MyModule from './MyModule';`
  * Refer to specific sections below for further information.

* **`const` and `let`**
  * `const` and `let` are new keywords for declaring variables: `const name = 'Jim'`; `let age = 25;`
  * `const` can't be reassigned; `let` can be.
  * `let` exists for block scoping.
  * Refer to the "Key Code Snippets" section below for examples


* **Functional Components**
  - A React functional component takes the `props` object as its argument and returns JSX.
  - It can have logic in it - but it's written as a function!
  - Here's a component written regularly, as a class:
  ```js
  class Name extends React.Component {
    render() {
      return (
        <div>
          Name: {this.props.firstName} {this.props.lastName}
        </div>
      );
    }
  }
  ```
  - Now here's the same component as a functional component:
  ```js
  const Name = props => (
    <div>
      Name: {props.firstName} {props.lastName}
    </div>
  );
  ```

* **Immutable Data Types**
  - Something that is **immutable** is something that cannot be changed.
  - State and props are to be treated as immutable; `const` variables are immutable.
  - Use immutable methods and immutable libraries to make maintaining immutable data types simple - see the Further Reading section.
    - The array methods `map`, `filter`, and `reduce` return modified copies of the array and don't mutate the originals.
    - ES6's `Object.assign` is a way to change data in objects that doesn't mutate the originals.


* **Object Literal Shorthand**
  - If you want to assign a variable as the value of the key of the same name, you don't have to write it twice. Before we would have:
  ```js
  const price = 100;

  const item = {
    price: price,
  };
  ```
  turns into:
  ```js
  const price = 100;

  const item = {
    price,
  };
  ```

* **Template Literals**
  -  Create dynamic strings with more readable syntax.
  ```js
  const name = 'Mike';
  const greeting = `Hi, ${name}.`;
  ```

* **Unidirectional Flow**
  - In React applications, data usually flows from the top down.
    - This is called unidirectional flow.
  - Define the state in the highest component you can, so that you can pass it to any components which will need it.


### Key Concepts

* **`const` vs `let`**
  - It's best practice to use `const` and `let`, rather than `var`, whenever possible
    - Including defining functions!
    - If the variable's value _will_ or _might_ change (unless you need a global scope) you'll likely declare it as a `let`.

* **When do you use a functional component?**
  * Use a **class** if you need:
    - Your component to be stateful (That is, if you need the ability to use `setState` to respond to changes).
    - Lifecycle methods (if you need to do something when the component mounts, receives `props`, or unmounts).
    - A `ref` (that is, a reference to the DOM element rendered by the component)
  * And only if you _don't_ need any of those things:
    - Use a functional component.


### Key Code Snippets - `const`

- `const` and `let` are new keywords for declaring variables.
- `const` can't be reassigned.
  - However, this does _not_ mean that a `const` is immutable.
  - JavaScript assigns by reference.
  - This means that a variable can't be reassigned entirely, but we *can* change a property of an object or add an item to an array.

Using `const`, this is **not** correct or doable - **it will throw an error, because a `const` variable cannot be reassigned.**
```js
const hi = 'hello';
hi = 'goodbye';
```

**However**, using `const`, this **is** correct and doable.

```js
const anObject = {
  hi: 'hello',
  animal: `muffin`
};
```

We can set:

```js
anObject.animal = 'puppy';
```

The new value of `anObject` is now:

```js
{
  hi: 'hello',
  animal: 'puppy'
}
```


### Key Code Snippets - `let`

- `const` and `let` are new keywords for declaring variables.
- `let` has the same assignment rules as `var`.
  - The value and reference of a `let` variable can change.
- `let` is a **block scoped** variable, so its value is scoped to the nearest curly braces {}, rather than to the whole function.

**Simple `let` example**

```js
let hi = 'hello';
hi = 'goodbye';
```
**`let` example of scoping**

```js
function letTest() {
  let x = 1;
  if (true) {
    let x = 2;  // curly braces = different variable
    console.log(x);  // Prints 2
  }
  console.log(x);  // Prints 1
}
```


### Key Code Snippets - Arrow functions

**Simple arrow function example:**
- In regular JavaScript
```js
function multiply(x, y) {
  return x * y;
}
```

- Same function using ES6 arrow syntax. Differences:
  - Declare the function as a variable: `var multiply`.
  - Pass in the parameters (here, `x` and `y`) after an equal sign
  - Put arrow function symbol `=>`
  - Put actual function definition

```js
const multiply = (x, y) => {
  return x * y;
}
```

**Implicit return example:**
- If the function only returns in one line:

```js
const addTwo = num => x * y;
```



### Further Reading

The links below are optional, but they're great resources for you.


##### Other links of interest to reinforce this learning
- [Facebook's Guide to Thinking in React](https://facebook.github.io/react/docs/thinking-in-react.html)
- [Facebook's Documentation on Components](https://facebook.github.io/react/docs/react-component.html).
- [Side Effect Definition](https://en.wikipedia.org/wiki/Side_effect_(computer_science))
  - Thse should be avoided in the `constructor`, so server requests shouldn't be made there. The accepted answer on this [Stack Overflow question](http://stackoverflow.com/questions/41612200/in-react-js-should-i-make-my-initial-network-request-in-componentwillmount-or-co), provided by a member of the React team at Facebook, gives more detail.
- [`window.setTimeout`](https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/setTimeout)
- [Recursion Definition](https://en.wikipedia.org/wiki/Recursion_(computer_science)
  - This is good to know as that's what `incrementSpeed` is
- [Non-official Immutable Libraries](https://gist.github.com/jlongster/bce43d9be633da55053f)
- [Official Immutable.js from Facebook](https://facebook.github.io/immutable-js/)
  - One of several mature JavaScript libraries that provide immutable data types and/or immutable methods that can make maintaining immutable data types simple.
  - This which provides immutable data types like `List`, `Stack`, `Map`, `OrderedMap`, `Set`, `OrderedSet`, and `Record` — and methods for making changes to your data like `set`, `get`, `delete`, and `update`.
  - Just use the types and methods provided, and the library takes care of immutability for you.

#### Some of the features from ES6 and beyond we did _not_ cover, if you'd like to read about ES6 further:

- [Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
- [Async](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function)/[Await](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/await)
- [Generators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Iterators_and_Generators)
- [Classes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)
- [Array Spread](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_operator)
- [Array and Object Destructuring Assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)
- [Object Rest Spread](https://babeljs.io/docs/plugins/transform-object-rest-spread/)

##### Complex topics not covered for your optional future further study
- [A Cartoon Guide To Flux by Lin Clark](https://code-cartoons.com/a-cartoon-guide-to-flux-6157355ab207#.m53psmlww)
- [Redux State Management Library](http://redux.js.org/)
