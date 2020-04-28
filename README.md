# ReactBullets
While learning ReactJS, I took notes in the form of bullet points. Here are some points I wrote before start coding [Oud Frontend](https://github.com/AbdallahHemdan/oudFrontend) in addition to some helpfull rsources which was a helping hand.

## Notes
* Use ```camelCase``` in JSX attributes as it treateed as JavaScript objects not DOM elements.
* Always start component names with a capital letter: For example, ```<div />``` represents an HTML div tag, but ```<Welcome />``` represents a component and requires Welcome to be in scope.
* If a part of your UI is used several times (Button, Panel, Avatar), or is complex enough on its own (App, FeedStory, Comment), it is a good candidate to be a reusable component.
* ```Pure Functions```: they do not attempt to change their inputs, and always return the same result for the same inputs.
* ```Impure Functions```: changes its own input.
* The single React strict rule: <strong>All</strong> React components must act like pure functions with respect to their props.
* Three things about ```setState()```:
  1. <strong>Do Not</strong> Modify State Directly: The only place where you can assign ```this.state``` is the constructor.
  2. State Updates May Be <strong>Asynchronous</strong>: Because ```this.props``` and ```this.state``` may be updated asynchronously, you <strong>should not</strong> rely on their values for calculating the next state.
  3. State Updates are <strong>Merged</strong>: You can update independant variables independently with seperate ```setState()``` calls.
* State is often called local or encapsulated. It is not accessible to any component other than the one that owns and sets it.
* A ```top-down``` or ```unidirectional``` data flow; Any state is always owned by some specific component, and any data or UI derived from that state can only affect components ```below``` them in the tree.
* Handling events in React VS DOM:
  1. React events are named using ```camelCase```, rather than ```lowercase```.
  2. With JSX you pass a <strong>function as the event handler<strong>, rather than a <strong>string</strong>.
  3. You <strong>cannot</strong> return false to prevent default behavior in React. You must call ```preventDefault``` explicitly.
  4. You generally don’t need to call ```addEventListener```. Just provide a listener when the element is initially rendered.
* Important note on how functions work in JavaScript:
   * Generally, if you refer to a method without ```()``` after it, such as ```onClick={this.handleClick}```, you should bind that method.
   * You have to be careful about the meaning of this in JSX callbacks. Class methods are <strong>not bound</strong> by default. If you forget to bind ```this.handleClick``` and pass it to onClick, this will be ```undefined``` when the function is actually called.
* How to avoid binding ```this```?
  1. Experimental public class fields syntax (assign it to an ```arrow function```).
  2. Use an arrow function in the callback: ```onClick={(e) => this.handleClick(e)}```
  <strong>Note</strong>: Binding in constructor or Class field sytaxt is <strong>recommended</strong> to avoid performance problems.
* In JavaScript, ```true && expression``` always evaluates to <strong>expression</strong>, and ```false && expression``` always evaluates to <strong>false</strong>.
* Conditional Redering: <strong>it is up to you</strong> to choose an appropriate style based on what you and your team consider more readable. Also remember that whenever conditions become too <strong>complex</strong>, it might be a good time to extract a <strong>component</strong>.
* Preventing Component from Rendering: return null instead of its render output. Returning null from a component’s render method does not affect the firing of the component’s lifecycle methods. For instance componentDidUpdate will still be called.
* A “key” is a special string attribute you need to include when creating lists of elements. Keys help React identify which items have changed, are added, or are removed. Keys should be given to the elements inside the array to give the elements a stable identity.
* The best way to pick a key is to use a string that uniquely identifies a list item among its siblings. Most often you would use IDs from your data as keys. When you don’t have stable IDs for rendered items, you may use the item index as a key as a last resort.
* Indexes for key are not recommended so it's better to assign an explicit key for a list item. Indexes for keys are the default in React.
* Keys only make sense in the context of the surrounding array. A good rule of thumb is that elements inside the map() call need keys.
* Keys used within arrays should be unique among their siblings. However they don’t need to be globally unique.
* Keys serve as a hint to React but they don’t get passed to your components. If you need the same value in your component, pass it explicitly as a prop with a different name (use different name from ```key```).
* It's convenient to have JavaScript function that handles the submission of the form and its related validation stuff. The standard way is ```Controlled Component``` which differs a little bit from plain HTML form.
* Controlled Component: combining elements state and update it based on user input. An input form element whose value is controlled by React. This makes it straightforward to modify or validate user input.
* Files from user device are read-only so they are ```uncontrolled components```.
* ```Fomik``` is a good complete solution for handling forms. It is built on controlled component princeples so it is important to learn them.
* If you want to reflect the same data in several components, it is recommended to lift the shared state up to their closest ancestor.
* There should be a single “source of truth” for any data that changes in a React application.
* It is recommended to use composition instead of inheritance to reuse code between components.
* State is reserved only for interactivity, that is, data that changes over time. Don’t use state at all to build a static version.
* In simpler examples, it’s usually easier to go top-down, and on larger projects, it’s easier to go bottom-up and write tests as you build.
* Steps to build the UI in React:
 * Step 1: Break The UI Into A Component Hierarchy
 * Step 2: Build A Static Version in React
 * Identify The Minimal (but complete) Representation Of UI State
 * Step 4: Identify Where Your State Should Live:
   For each piece of state in your application:
    * Identify every component that renders something based on that state.
    * Find a common owner component (a single component above all the components that need the state in the hierarchy).
    * Either the common owner or another component higher up in the hierarchy should own the state.
    * If you can’t find a component where it makes sense to own the state, create a new component solely for holding the state and add it somewhere in the hierarchy above the common owner component.
 * Step 5: Add Inverse Data Flow
 
 * aria-* attributes should be hyphen-cased.
* Accessibility Points for Consideration:
 * Semantic HTML: foundation of accessibility in a web application.
 * Accessible Forms: Labeling + Notifying the user of errors.
 * Ensure that your web application can be fully operated with the keyboard only.
 * Mechanisms to skip to desired content
 * Be carefull about focus as React modify HTML DOM during runtime which may cause to keyboard focus being lost or set to an unexpected element.
 * Ensure that all functionality exposed through a mouse or pointer event can also be accessed using the keyboard alone.
 * Indicate the human language of page texts as screen reader software uses this to select the correct voice settings.
 * Set the document <title> to correctly describe the current page content as this ensures that the user remains aware of the current page context.
 * Ensure that all readable text on your website has sufficient color contrast to remain maximally readable by users with low vision.

 * Code Splitting:
* A bundle: the process of following imported files and merging them into a single file.
* Create React App, Next.js, Gatsby, or a similar tool, has a Webpack setup out of the box to bundle your app.
* You need to keep an eye on the code you are including in your bundle so that you don’t accidentally make it so large that your app takes a long time to load.
* Code-Splitting is a feature supported by bundlers like Webpack, Rollup and Browserify (via factor-bundle) which can create multiple bundles that can be dynamically loaded at runtime.
* The best way to introduce code-splitting into your app is through the dynamic import().

JavaScript Overview:
* JavaScript language has no concept of input or output. It is up to the host environment to provide mechanisms for communicating with the outside world.
* JavaScript's types are (the building blocks of any language):
* Number
* String
* Boolean
* Symbol(ES6)
* Object:
  * Function(technically, it's a special type of object)
  * Array
  * Data
  * RegExp
* null
* undefined

* Numbers: "double-precision 64-bit format IEEE 754 values"
* Be carefull about stuff like: ```0.1 + 0.2 == 0.30000000000000004;```
* The standard arithmetic operators are supported with some built-in objects like ```Math``` object,  ```parseInt()```, and ```parseFloat()``` functions.
* Unlike ```parseFloat()```, ```parseInt()``` can use different bases like decimal, octal, or hexadecimal but be carefull when dealing with old browsers(befor 2013).
* the unary ```+``` operator can be used to convert values to numbers like that: ```+ '42'; //42```
  * So, what is the difference? The parseInt() and parseFloat() functions parse a string until they reach a character that isn't valid for the specified number format, then return the number parsed up to that point. However the "+" operator simply converts the string to NaN if there is an invalid character contained within it.
* ```NaN```: a special value returned when the string is non-numeric:
   * If you provide it as an operand to any mathematical operation, the result will also be NaN
   * You can test for NaN using the built-in isNaN() function.
* ``` Infinity``` and ```-Infinity``` are also special types:
   * You can test for Infinity, -Infinity and NaN values using the built-in isFinite() function.

Strings: "sequences of UTF-16 code units; each code unit is represented by a 16-bit number. Each Unicode character is represented by either 1 or 2 code units."
* We can use strings as objects too. They have methods as well that allow you to manipulate the string and access information about the string.
* undefined VS null:
* undefined indicates an uninitialized variable. undefined is actually a constant.
* null is a value that indicates a deliberate non-value (and is only accessible through the null keyword).
* Boolean: any value can be converted to boolean value according to the following rules:
 1. false, 0, empty strings (""), NaN, null, and undefined all become false.
 2. All other values become true.
* Conversion can be done explicitly using the Boolean() function or JavaScript will silently perform this conversion when it expects a boolean, such as in an if statement.

* Variables: in modern JavaScript there, variables are declared using one of three keywords: ```let```, ```const```, or ```var```
* let allows you to declare block-level variables. The declared variable is available from the block it is enclosed in.
* const allows you to declare variables whose values are never intended to change. The variable is available from the block it is declared in.
* var is the most common declarative keyword. It does not have the restrictions that the other two keywords have.
* Before ECMAScript2015, only functions have a scope so if a variable is defined using var in a compound statement (for example inside an if control structure), it will be visible to the entire function. However, starting with ECMAScript 2015, let and const declarations allow you to create block-scoped variables.

Operators: similar to other programming languages
* If you add a string to a number (or other value) everything is converted into a string first.
* Adding an empty string to something is a useful way of converting it to a string itself.
* The double-equals operator performs type coercion if you give it different types, with sometimes interesting results. To avoid type coercion, use the triple-equals operator.

Control structures: similar set of control structures to other languages in the C family
* ```while``` is good for basic looping. ```do-while``` for loops where you wish to ensure that the body of the loop is executed at least once.
* ```for...of```: creates a loop iterating over iterable objects. It invokes a custom iteration hook with statements to be executed for the value of each distinct property of the object.
* ```for...in```: iterates over all enumerable properties of an object that are keyed by strings (ignoring ones keyed by Symbols), including inherited enumerable properties.
* The && and || operators use short-circuit logic, which means whether they will execute their second operand is dependent on the first. This is useful for checking for null objects before accessing their attributes.

Objects: can be thought of as simple collections of name-value pairs, they are similar to Hash tables in C and C++.
* Everything in JavaScript is an object which mean that any JavaScript program naturally involves a great deal of hash table lookups.
* Two basic ways to create an empty object:
  1- var obj = new Object();
  2- var obj = {}; : object literal syntax and is more convenient. This syntax is also the core of JSON format and should be preferred at all times.
* Once created, an object's properties can again be accessed in one of two ways:
 1- dot notation.
 2- bracket notation: has the advantage that the name of the property is provided as a string, which means it can be calculated at run-time. However, using this method prevents some JavaScript engine and minifier optimizations being applied. It can also be used to set and get properties with names that are reserved words like ```obje['for']```
* Notes: 
 1- Starting in ECMAScript 5, reserved words may be used as object property names "in the buff". This means that they don't need to be "clothed" in quotes when defining object literals.
 2- Starting in ECMAScript 2015, object keys can be defined by the variable using bracket notation upon being created. {[phoneType]: 12345} is possible instead of just var userPhone = {}; userPhone[phoneType] = 12345.

Arrays: a special type of object
* Numerical properties can naturally be accessed only using [] syntax.
* How to create an Array? 
 1- 
    var a = new Array();
a[0] = 'dog';
a[1] = 'cat';
a[2] = 'hen';

 2- more convenient notation is to use an array literal: ```var a = ['dog', 'cat', 'hen'];```

* ```array.length``` isn't necessarily the number of items in the array, WHY? the length of the array is one more than the highest index.
* If you query a non-existent array index, you'll get a value of undefined in return
* for...in does not iterate over the array elements, but the array indices. Furthermore, if someone added new properties to Array.prototype, they would also be iterated over by such a loop. Therefore this loop type is not recommended for arrays.
* Another way of iterating over an array that was added with ECMAScript 5 is forEach()

Functions: Along with objects, functions are the core component in understanding JavaScript
* If no return statement is used (or an empty return with no value), JavaScript returns undefined.
* You can call a function without passing the parameters it expects, in which case they will be set to undefined. You can also pass in more arguments than the function is expecting.
* arguments, an array-like object holding all of the values passed to the function.
* The rest parameter operator is used in function parameter lists with the format: ...variable and it will include within that variable the entire list of uncaptured arguments that the function was called with. 
* It is important to note that wherever the rest parameter operator is placed in a function declaration it will store all arguments after its declaration, but not before.
* JavaScript lets you create anonymous functions which stored in variables. This enables all sorts of clever tricks like a way of "hiding" some local variables — like block scope in C.
* JavaScript uses functions as classes.
* this refers to the current object. What that actually means is specified by the way in which you called that function. If you called it using dot notation or bracket notation on an object, that object becomes this. If dot notation wasn't used for the call, this refers to the global object.
* new is strongly related to this. It creates a brand new empty object, and then calls the function specified, with this set to that new object.
* JavaScript lets you modify something's prototype at any time in your program, which means you can add extra methods to existing objects at runtime ("prototype chain"). You can also add things to the prototype of built-in JavaScript objects.
* An important detail of nested functions in JavaScript is that they can access variables in their parent function's scope but not vice versa.

Closures: one of the most powerful abstractions that JavaScript has to offer — but also the most potentially confusing.
* Whenever JavaScript executes a function, a 'scope' object is created to hold the local variables created within that function. It is initialized with any variables passed in as function parameters.
* A closure is the combination of a function and the scope object in which it was created. Closures let you save state — as such, they can often be used in place of objects. 

Hooks: They let you use state and other React features without writing a class.
* Hooks let you split one component into smaller functions based on what pieces are related (such as setting up a subscription or fetching data). Hooks let you use more of React’s features without classes.
* Classes don’t minify very well, and they make hot reloading flaky and unreliable. There are no plans to remove classes from React. 

https://www.npmjs.com/package/eslint-plugin-react-hooks
What is a Hook? Hooks are functions that let you “hook into” React state and lifecycle features from function components. Hooks don’t work inside classes — they let you use React without classes.
* React provides a few built-in Hooks like useState. You can also create your own Hooks to reuse stateful behavior between different components.
* Hooks are a way to reuse stateful logic, not state itself.
* Hooks must be called on the top level of our components. If we want to run an effect conditionally, we can put that condition inside our Hook

State Hook:
* ```useState``` returns a pair: the current state value and a function that lets you update it. 
* It’s similar to this.setState in a class, except it doesn’t merge the old and new state together.
* The only argument to useState is the initial state.
* Unlike this.state, the state here doesn’t have to be an object — although it can be if you want. 
* You can use the State Hook more than once in a single component.
* What does calling useState do? It declares a “state variable”, we could call it anything. Normally, variables “disappear” when the function exits but state variables are preserved by React.


Effect Hook:
* ```useEffect``` adds the ability to perform side effects from a function component. It serves the same purpose as componentDidMount, componentDidUpdate, and componentWillUnmount in React classes, but unified into a single API.
* When you call useEffect, you’re telling React to run your “effect” function after flushing changes to the DOM.
* Effects are declared inside the component so they have access to its props and state.
* By default, React runs the effects after every render — including the first render.
* Effects may also optionally specify how to “clean up” after them by returning a function. 
*  think that effects happen “after render”. React guarantees the DOM has been updated by the time it runs the effects.
* Unlike componentDidMount or componentDidUpdate, effects scheduled with useEffect don’t block the browser from updating the screen. 
* Every effect may return a function that cleans up after it. 
* React performs the cleanup when the component unmounts. React also cleans up effects from the previous render before running the effects next time. There is no special code for handling updates because useEffect handles them by default.
* Tips: Use Multiple Effects to Separate Concerns
* In some cases, cleaning up or applying the effect after every render might create a performance problem.
* You can tell React to skip applying an effect if certain values haven’t changed between re-renders.

Rules of Hooks:
Hooks are JavaScript functions, but they impose two additional rules:
* Only call Hooks at the top level. Don’t call Hooks inside loops, conditions, or nested functions.
* Only call Hooks from React function components. Don’t call Hooks from regular JavaScript functions. (There is just one other valid place to call Hooks — your own custom Hooks.)
* React provide a linter plugin to enforce these rules automatically.

Building Your Own Hooks:
* Custom Hooks let you reuse some stateful logic between components but without adding more components to your tree.
* Custom Hooks are more of a convention than a feature. If a function’s name starts with ”use” and it calls other Hooks, we say it is a custom Hook.
* It’s just like a normal function.
* All we do isto extract some common code between functions into a separate function.
* Without starting the Hook with ```use``, React wouldn’t be able to automatically check for violations of rules of Hooks because we couldn’t tell if a certain function contains calls to Hooks inside of it.
* Tip: Pass Information Between Hooks

Testing: Similar to testing other JavaScript code.
Two ways of testing React Components:
* Rendering component trees in a simplified test environment and asserting on their output.
* Running a complete app in a realistic browser environment (also known as “end-to-end” tests).
When choosing testing tools, it is worth considering a few tradeoffs:
* Iteration speed vs Realistic environment.
* How much to mock.
Recommended Tools:
*Jest
* React Testing Library
Testing Recipes: Common testing patterns for React components.
* Setup/Teardown: You may use a different pattern, but keep in mind that we want to execute the cleanup even if a test fails.
* act(): makes sure all updates related to these “units” have been processed and applied to the DOM before you make any assertions.
* Rendering
* Data Fetching: Instead of calling real APIs in all your tests, you can mock requests with dummy data.
* Mocking Modules: Some modules might not work well inside a testing environment, or may not be as essential to the test itself. Mocking out these modules with dummy replacements can make it easier to write tests for your own code.
* Events: It is recommended dispatching real DOM events on DOM elements, and then asserting on the result.
* Timers: Your code might use timer-based functions like setTimeout to schedule more work in the future.
* Snapshot Testing: Frameworks like Jest also let you save “snapshots” of data with toMatchSnapshot / toMatchInlineSnapshot. With these, we can “save” the rendered component output and ensure that a change to it has to be explicitly committed as a change to the snapshot.These kinds of tests include implementation details so they break easily, and teams can get desensitized to snapshot breakages.
* Multiple Renderers: In rare cases, you may be running a test on a component that uses multiple renderers. 
Testing Environments:
* If you use Create React App, Jest is already included out of the box with useful defaults.
* It is recommended simulating a browser with jsdom, a lightweight browser implementation that runs inside Node.js.
* If you’re writing a library that tests mostly browser-specific behavior, and requires native browser behavior like layout or real inputs, you could use a framework like mocha.
* Frameworks like Cypress, puppeteer and webdriver are useful for running end-to-end tests.
* When writing tests, we’d like to mock out the parts of our code that don’t have equivalents inside our testing environment. It is then useful to be able to selectively mock these functions with test-friendly versions.

## Learning reasources:
- [Complete Intro to Web Development](https://frontendmasters.com/courses/web-development-v2/)
- [JavaScript](https://frontendmasters.com/learn/javascript/)
- [JavaScript](https://frontendmasters.com/courses/getting-started-javascript-v2/)
- [React.JS](https://reactjs.org/docs/getting-started.html)
- [React.JS](https://frontendmasters.com/learn/react/)
- [JS Tutorial](https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript)

## Best Practices:
- [Front-End Checklist](https://github.com/thedaviddias/Front-End-Checklist)
- [Clean Code](https://github.com/ryanmcdermott/clean-code-javascript)
- [Front-End Performance Checklist](https://github.com/thedaviddias/Front-End-Performance-Checklist)
- [33 concepts JS](https://github.com/leonardomso/33-js-concepts)
