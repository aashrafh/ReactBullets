## 📝 Table of Contents
- [About](#bullets)
- [JavaScript Overview](#js)
- [What does react.js try to solve?](#virtualDom)
- [General Notes](#general)
- [React Rendering Behavior](#rendering)
- [Accessibility](#accessibility)
- [Code Splitting](#codeSplitting)
- [Hooks](#hooks)
- [Testing](#testing)
- [Redux](#redux)
- [Learning Resources](#learningResources)

# ReactBullets <a name = "bullets"></a>
 While learning ReactJS, I took notes in the form of bullet points for fast revision. Here are some points I wrote before start coding [Oud](https://github.com/aashrafh/Oud) Frontend in addition to some helpful resources which was a helping hand that may help you if you are learning React.js. I also will keep updating the repo with any usefull notes, or resources.

## JavaScript Overview<a name = "js"></a>: 
* JavaScript language has no concept of <strong>input</strong> or <strong>output</strong>. It is up to <strong>the host environment</strong> to provide mechanisms for communicating with the outside world.
* JavaScript's types are <strong>the building blocks of any language</strong>:
  * ```Number```
  * ```String```
  * ```Boolean```
  * ```Symbol```
  * ```Object```:
    * ```Function```
    * ```Array```
    * ```Date```
    * ```RegExp```
  * ```null```
  * ```undefined```

* <strong>```Numbers```</strong>: "double-precision 64-bit format IEEE 754 values"
  * Be carefull about stuff like: ```0.1 + 0.2 == 0.30000000000000004;```(float problems)
  * The standard arithmetic operators are supported with some built-in objects like ```Math``` object,  ```parseInt()```, and ```parseFloat()``` functions.
  * Unlike ```parseFloat()```, ```parseInt()``` can use different bases like decimal, octal, or hexadecimal but be carefull when dealing with old browsers(befor 2013).
  * the unary ```+``` operator can be used to convert values to numbers like that: ```+ '42'; //42```
    * So, what is the difference? The parseInt() and parseFloat() functions parse a string until they reach a character that isn't valid for the specified number format, then return the number parsed up to that point. However the "+" operator simply converts the string to NaN if there is an invalid character contained within it.
  * ```NaN```: a special value returned when the string is non-numeric:
     * If you provide it as an operand to any mathematical operation, the result will also be NaN
     * You can test for ```NaN``` using the built-in ```isNaN()``` function.
  * ``` Infinity``` and ```-Infinity``` are also special types:
     * You can test for ```Infinity```, ```-Infinity``` and ```NaN``` values using the built-in ```isFinite()``` function.

* <strong>```Strings```</strong>: "sequences of UTF-16 code units; each code unit is represented by a 16-bit number. Each Unicode character is represented by either 1 or 2 code units."
  * We can use strings as objects too. They have methods as well that allow you to manipulate the string and access information about the string.
 
* <strong>```undefined``` VS ```null```</strong>:
  * ```undefined``` indicates an uninitialized variable. undefined is actually a constant.
  * ```null``` is a value that indicates a deliberate non-value (and is only accessible through the null keyword).

* <strong>```Boolean```</strong>: any value can be converted to boolean value according to the following rules:
  1. ```false```, ```0```, empty strings ```("")```, ```NaN```, ```null```, and ```undefined``` all become false.
  2. All other values become ```true```.
  * Conversion can be done <strong>explicitly</strong> using the ```Boolean()``` function or JavaScript will <strong>silently</strong> perform this conversion when it expects a boolean, such as in an if statement.

* <strong>Variables</strong>: in modern JavaScript there, variables are declared using one of three keywords: ```let```, ```const```, or ```var```
  * ```let``` allows you to declare <strong>block-level</strong> variables. The declared variable is available from the block it is enclosed in.
  * ```const``` allows you to declare variables whose values are <strong>never intended to change</strong>. The variable is available from the block it is declared in.
  * ```var``` is the most common declarative keyword. It <strong>does not have the restrictions that the other two keywords have</strong>.
  * Before <strong>ECMAScript2015</strong>, only functions have a scope so if a variable is defined using var in a compound statement (for example inside an if control structure), it will be <strong>visible</strong> to the entire function. However, starting with ECMAScript2015, ```let``` and ```const``` declarations allow you to create block-scoped variables.

* <strong>Operators</strong>: similar to other programming languages
  * If you add a ```string``` to a ```number``` <strong>(or other value)</strong> everything is converted into a <strong>```string```</strong> first.
  * Adding an empty string to something is a useful way of converting it to a string itself.
  * The double-equals - ```==``` - operator performs type coercion if you give it different types, with sometimes interesting results. To avoid type coercion, use the triple-equals - ```===``` - operator.

* <strong>Control structures</strong>: similar set of control structures to other languages in the C family
  * ```while``` is good for basic looping. ```do-while``` for loops where you wish to ensure that the body of the loop is executed at least once.
  * ```for...of```: creates a loop iterating over iterable objects. It invokes a custom iteration hook with statements to be executed for the value of each distinct property of the object.
  * ```for...in```: iterates over all enumerable properties of an object that are keyed by strings (ignoring ones keyed by Symbols), including inherited enumerable properties.
  * The ```&&``` and ```||``` operators use short-circuit logic, which means whether they will execute their second operand is dependent on the first. This is useful for checking for ```null``` objects before accessing their attributes.

* <strong>```Objects```</strong>: can be thought of as simple collections of ```name-value``` pairs, they are similar to Hash tables in C and C++.
  * <strong>Everything</strong> in JavaScript is an ```object``` which mean that any JavaScript program naturally involves a great deal of hash table lookups.
  * Two basic ways to create an empty object:
     1. ```var obj = new Object();```
     2. ```var obj = {};``` : object literal syntax and is <strong>more convenient</strong>. This syntax is also the core of JSON format and should be preferred at all times.
  * Once created, an object's properties can again be accessed in one of two ways:
    1. ```dot``` notation.
    2. ```bracket``` notation: has the advantage that the name of the property is provided as a string, which means it can be calculated at run-time. However, using this method prevents some JavaScript engine and minifier optimizations being applied. It can also be used to set and get properties with names that are reserved words like ```obje['for']```
  * Notes: <strong>Starting in ECMAScript2015</strong>
    1. Reserved words may be used as object property names. This means that they don't need to be "clothed" in quotes when defining object literals.
    2. Object keys can be defined by the variable using bracket notation upon being created. ```{[phoneType]: 12345}``` is possible instead of just ```var userPhone = {}; userPhone[phoneType] = 12345;```.

* <strong>```Array```</strong>: a special type of object
  * Numerical properties can naturally be accessed only using ```[]``` syntax.
  * How to create an Array?
    1. ```var a = new Array();```
       ```a[0] = 'dog';```
       ```a[1] = 'cat';```
       ```a[2] = 'hen';```
    2. More <strong>convenient notation</strong> is to use an array literal: ```var a = ['dog', 'cat', 'hen'];```

  * ```array.length``` isn't necessarily the number of items in the array, WHY? the length of the array is one more than the highest index.
  * If you query a non-existent array index, you'll get a value of ```undefined``` in return
  * ```for...in``` does not iterate over the array elements, but the array ```indices```. Furthermore, if someone added new properties to ```Array.prototype```, they would also be iterated over by such a loop. Therefore this loop type is <strong>not recommended</strong> for arrays.
  * Another way of iterating over an array that was added with ECMAScript2015 is ```forEach()```.

* <strong>Functions</strong>: Along with objects, functions are the core component in understanding JavaScript
  * If no return statement is used (or an empty return with no value), JavaScript returns ```undefined```.
  * You can call a function without passing the parameters it expects, in which case they will be set to ```undefined```. You can also pass in <strong>more arguments</strong> than the function is expecting.
  * ```arguments```, an array-like object holding all of the values passed to the function.
  * The ```rest parameter operator``` is used in function parameter lists with the format: ```...variable``` and it will include within that variable the entire list of uncaptured arguments that the function was called with. 
  * It is important to note that wherever the rest parameter operator is placed in a function declaration it <strong>will store all arguments after its declaration, but not before</strong>.
  * JavaScript lets you create anonymous functions which stored in variables. This enables all sorts of clever tricks like a way of <strong>hiding</strong> some local variables — like block scope in C.
  * JavaScript uses <strong>functions</strong> as <strong>classes</strong>.
  * ```this``` refers to the current object. What that actually means is specified by <strong>the way in which you called that function</strong>. If you called it using dot notation or bracket notation on an object, ```that``` object becomes ```this```. If dot notation wasn't used for the call, this refers to the global object.
  * ```new``` is strongly related to ```this```. It creates a brand new empty object, and then calls the function specified, with this set to that new object.
  * JavaScript lets you modify something's prototype at any time in your program, which means you can add extra methods to existing objects at runtime <strong>(prototype chain)</strong>. You can also add things to the prototype of built-in JavaScript objects.
  * An important detail of nested functions in JavaScript is that they can access variables in their parent function's scope but <strong>not vice versa</strong>.

* <strong>Closures</strong>: one of the most powerful abstractions that JavaScript has to offer — but also the most potentially confusing.
  * Whenever JavaScript executes a function, a ```scope``` object is created to hold the local variables created within that function. It is initialized with any variables passed in as function parameters.
  * A closure is the combination of a function and the scope object in which it was created. Closures let you save state — as such, they can often be used in place of objects. 

## What does react.js try to solve?<a name="virtualDom"></a>
* DOM operations are quite expensive in terms of performance.
* Doing optimizing DOM manipulation by hand will result in a lot of <strong>boilerplate</strong> code, which is error-prone, boring and repetitive.
* If the page has data that changes over time at high rates (for example, lots of people commenting on a post, likes being generated etc), then there is a requirement for DOM updates to be very fast and also reflect in other parts of the UI if they use the same data.
* React solves this by giving the developer a virtual DOM to render to instead of the actual DOM, which it then diffs with the real DOM, and does the minimum number of DOM operations needed to achieve the new state.
## React Notes<a name="general"></a>
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
  2. With JSX you pass a <strong>function as the event handler</strong>, rather than a <strong>string</strong>.
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
* Preventing Component from Rendering: return ```null``` instead of its render output. Returning ```null``` from a component’s render method does not affect the firing of the component’s lifecycle methods. For instance ```componentDidUpdate``` will still be called.
* A ```key``` is a special string attribute you need to include when creating lists of elements. Keys help React identify which items have changed, are added, or are removed. Keys should be given to the elements inside the array to give the elements a stable identity.
* The best way to pick a key is to use a <strong>string that uniquely identifies a list item</strong> among its siblings. Most often you would use IDs from your data as keys. When you don’t have stable IDs for rendered items, you may use the item <strong>index</strong> as a key as a last resort.
* <strong>Indexes</strong> for key are <strong>not recommended</strong> so it's better to assign an explicit key for a list item. Indexes for keys are the default in React.
* Keys only make sense in the context of the surrounding array. A good rule of thumb is that elements inside the ```map()``` call need keys.
* Keys used within arrays should be unique among their siblings. However they don’t need to be globally unique.
* Keys serve as a hint to React but they <strong>don’t get passed to your components</strong>. If you need the same value in your component, <strong>pass it</strong> explicitly as a prop with a different name (use different name from ```key```).
* It's <strong>convenient</strong> to have JavaScript function that handles the submission of the form and its related validation stuff. The standard way is ```Controlled Component``` which differs a little bit from plain HTML form.
* ```Controlled Component```: combining elements state and update it based on user input. An input form element whose value is controlled by React. This makes it straightforward to modify or validate user input.
* Files from user device are ```read-only``` so they are ```uncontrolled components```.
* ```Formik``` is a good complete solution for handling forms. It is built on controlled component princeples so it is important to learn them.
* If you want to reflect the same data in several components, it is recommended to <strong>lift the shared state up</strong> to their closest ancestor.
* There should be a <strong>single source of truth</strong> for any data that changes in a React application.
* It is recommended to use <strong>composition</strong> instead of <strong>inheritance</strong> to reuse code between components.
* ```State``` is reserved only for <strong>interactivity</strong>, that is, <strong>data that changes over time</strong>. Don’t use ```state``` at all to build a static version.
* In <strong>simpler</strong> examples, it’s usually easier to go <strong>top-down</strong>, and on <strong>larger</strong> projects, it’s easier to go <strong>bottom-up</strong> and write <strong>tests</strong> as you build.
* Steps to build the UI in React:
  * <strong>Step 1</strong>: Break The UI Into A Component Hierarchy
  * <strong>Step 2</strong>: Build A Static Version in React
  * <strong>Step 3</strong>: Identify The Minimal (but complete) Representation Of UI State
  * <strong>Step 4</strong>: Identify Where Your State Should Live:
    #### For each piece of state in your application:
    * <strong>Identify</strong> every component that renders something based on that state.
    * <strong>Find</strong> a common owner component (a single component above all the components that need the state in the hierarchy).
    * Either the common owner or another component higher up in the hierarchy should <strong>own</strong> the state.
    * If you can’t find a component where it makes sense to own the state, <strong>create</strong> a new component solely for holding the state and add it somewhere in the hierarchy above the common owner component.
  * <strong>Step 5</strong>: Add Inverse Data Flow
 
 * ```aria-*``` attributes should be ```hyphen-cased```.
* React Rendering Behavior:<a name = "rendering"></a>
  * React's default behavior is that when a <strong>parent component renders</strong>, React will recursively render <strong>all child components</strong> inside of it!
  * In normal rendering, React does not care whether "props changed" - it will render child components unconditionally just because the parent rendered!
  * Rendering is not a bad thing - it's how React knows whether it needs to actually make any changes to the DOM!
  * Optimizing React rendering is primarily about doing less work by skipping rendering components when appropriate.
  * How to skip rendering a component?
    * [```React.Component.shouldComponentUpdate```](https://reactjs.org/docs/react-component.html#shouldcomponentupdate)
    * [```React.PureComponent```](https://reactjs.org/docs/react-api.html#reactpurecomponent)
    * [```React.memo()```](https://reactjs.org/docs/react-api.html#reactmemo)
  * Skipping rendering a component means React will also skip rendering that entire subtree, because it's effectively putting a stop sign up to halt the default "render children recursively" behavior.
  * If the child component is trying to optimize renders by checking to see whether props have changed, then passing new references as props will cause the child to render.
  * When a context provider has a new value, every nested component that consumes that context will be forced to re-render..
  * Passing a new object to a context provider will cause it to update.
  * Currently, there is no way for a component that consumes a context to skip updates caused by new context values, even if it only cares about part of a new value.

* Accessibility Points for Consideration:<a name = "accessibility"></a>
  * <strong>Semantic HTML</strong>: foundation of accessibility in a web application.
  * <strong>Accessible Forms</strong>: Labeling + Notifying the user of errors.
  * Ensure that your web application can be <strong>fully operated</strong> with the <strong>keyboard only</strong>.
  * Mechanisms to skip to <strong>desired content</strong>.
  * Be carefull about <strong>focus</strong> as React modify HTML DOM during runtime which may cause to keyboard focus being <strong>lost</strong> or set to an <strong>unexpected element</strong>.
  * Ensure that <strong>all functionality</strong> exposed through a <strong>mouse or pointer</strong> event can also be accessed using the keyboard alone.
  * Indicate <strong>the human language of page</strong> texts as screen reader software uses this to select the correct voice settings.
  * Set the document ```<title>``` to correctly <strong>describe</strong> the current page content as this ensures that the user remains aware of the current page context.
  * Ensure that all readable text on your website has <strong>sufficient color contrast</strong> to remain maximally readable by users with low vision.

* Code Splitting:<a name = "codeSplitting"></a>
  * <strong>A bundle</strong>: the process of following imported files and merging them into a single file.
  * Create React App, Next.js, Gatsby, or a similar tool, has a <strong>Webpack</strong> setup out of the box to bundle your app.
  * You need to keep an eye on the code you are <strong>including</strong> in your bundle so that you don’t accidentally make it <strong>so large</strong> that your app takes a <strong>long time</strong> to load.
  * Code-Splitting is a feature supported by bundlers like Webpack, Rollup and Browserify (via factor-bundle) which can create multiple bundles that can be dynamically loaded at runtime.
  * The best way to introduce code-splitting into your app is through the <strong>dynamic ```import()```</strong>.

* Hooks: They let you use ```state``` and other React features without writing a class.<a name = "hooks"></a>
  * What is a Hook? Hooks are functions that let you <strong>hook into</strong> React ```state``` and lifecycle features from function components. Hooks don’t work inside classes — they let you use React without classes.
  * Hooks let you split one component into smaller functions based on what pieces are related (such as setting up a subscription or fetching data). Hooks let you use more of React’s features without classes.
  * Classes <strong>don’t</strong> minify very well, and they make hot reloading <strong>flaky and unreliable</strong>. <strong>There are no plans to remove classes from React</strong>.
  * React provides a few built-in Hooks like useState. You can also create your own Hooks to reuse stateful behavior between different components.
  * Hooks are a way to reuse <strong>stateful logic, not state itself</strong>.
  * Hooks <strong>must</strong> be called on the top level of our components. If we want to run an effect conditionally, we can put that condition <strong>inside our Hook</strong>.
  * <strong>State Hook</strong>:
    * ```useState``` returns a pair: the current state value and a function that lets you update it. 
    * It’s similar to ```this.setState``` in a class, except it doesn’t merge the old and new state together.
    * The only argument to ```useState``` is the initial state.
    * Unlike ```this.state```, the state here doesn’t have to be an object — although it can be if you want. 
    * You can use the State Hook more than once in a single component.
    * What does calling ```useState``` do? It declares a <strong>state variable</strong>, we could call it anything. Normally, variables <strong>disappear</strong> when the function exits but state variables are preserved by React.
  * <strong>Effect Hook</strong>:
    * ```useEffect``` adds the ability to perform side effects from a function component. It serves the same purpose as ```componentDidMount```, ```componentDidUpdate```, and ```componentWillUnmount``` in React classes, but unified into a single API.
    * When you call useEffect, you’re telling React to run your <strong>effect</strong> function after flushing changes to the DOM.
    * Effects are declared inside the component so they have access to its ```props``` and ```state```.
    * By default, React runs the effects after every render — including the first render.
    * Effects may also optionally specify how to <strong>clean up</strong> after them by returning a function. 
    * Think that effects happen <strong>after render</strong>. React guarantees the DOM has been updated by the time it runs the effects.
    * Unlike ```componentDidMount``` or ```componentDidUpdate```, effects scheduled with useEffect don’t block the browser from updating the screen. 
    * Every effect may return a function that cleans up after it. 
    * React performs the cleanup when the component unmounts. React also cleans up effects from the previous render before running the effects next time. There is no special code for handling updates because ```useEffect``` handles them by default.
    * <strong>Tip</strong>: Use Multiple Effects to Separate Concerns
    * In some cases, cleaning up or applying the effect after every render might create a performance problem.
    * You can tell React to skip applying an effect if certain values have not changed between re-renders.
  * <strong>Rules of Hooks</strong>: Hooks are JavaScript functions, but they impose two additional rules:
    * <strong>Only call Hooks at the top level</strong>. Don’t call Hooks inside loops, conditions, or nested functions.
    * <strong>Only call Hooks from React function components</strong>. Don’t call Hooks from regular JavaScript functions. (There is just one other valid place to call Hooks — your own custom Hooks.)
    * React provide a <a href="https://www.npmjs.com/package/eslint-plugin-react-hooks">linter plugin</a> to enforce these rules automatically.
  * <strong>Building Your Own Hooks</strong>:
    * Custom Hooks let you reuse some stateful logic between components but without adding more components to your tree.
    * Custom Hooks are more of a <strong>convention</strong> than a feature. If a function’s name starts with ```use``` and it calls other Hooks, we say it is a <strong>custom Hook</strong>.
    * It’s just like a normal function.
    * All we do is to <strong>extract</strong> some common code between functions into a separate function.
    * Without starting the Hook with ```use```, React would not be able to automatically check for violations of rules of Hooks because we could not tell if a certain function contains calls to Hooks inside of it.
    * <strong>Tip</strong>: Pass Information Between Hooks.
    
* Testing: Similar to testing other JavaScript code.<a name = "testing"></a>
  * Two ways of testing React Components:
    * Rendering component trees in a simplified test environment and asserting on their output.
    * Running a complete app in a realistic browser environment (also known as ```end-to-end``` tests).
  * When choosing testing tools, it is worth considering a few tradeoffs:
    * <strong>Iteration speed</strong> VS <strong>Realistic environment</strong>.
    * <strong>How much to mock</strong>.
  * Recommended Tools:
    * ```Jest```
    * ```React Testing Library```
  * Testing Recipes: Common testing patterns for React components.
    * ```Setup/Teardown```: You may use a different pattern, but keep in mind that we want to execute the cleanup even if a test fails.
    * ```act()```: makes sure all updates related to these <strong>units</strong> have been processed and applied to the DOM before you make any assertions.
    * ```Rendering```
    * ```Data Fetching```: Instead of calling real APIs in all your tests, you can mock requests with dummy data.
    * ```Mocking Modules```: Some modules might not work well inside a testing environment, or may not be as essential to the test itself. Mocking out these modules with dummy replacements can make it easier to write tests for your own code.
    * ```Events```: It is recommended dispatching real DOM events on DOM elements, and then asserting on the result.
    * ```Timers```: Your code might use timer-based functions like setTimeout to schedule more work in the future.
    * ```Snapshot Testing```: Frameworks like ```Jest``` also let you save ```snapshots``` of data with ```toMatchSnapshot``` / ```toMatchInlineSnapshot```. With these, we can <strong>save</strong> the rendered component output and ensure that a change to it has to be explicitly committed as a change to the snapshot.These kinds of tests include implementation details so they break easily, and teams can get desensitized to snapshot breakages.
    * ```Multiple Renderers```: In rare cases, you may be running a test on a component that uses multiple renderers. 
  * Testing Environments:
    * If you use ```Create React App```, ```Jest``` is already included out of the box with useful defaults.
    * It is <strong>recommended</strong> simulating a browser with <strong>jsdom</strong>, a lightweight browser implementation that runs inside ```Node.js```.
    * If you’re writing a library that tests mostly browser-specific behavior, and requires native browser behavior like layout or real inputs, you could use a framework like ```mocha```.
    * Frameworks like ```Cypress```, ```puppeteer``` and ```webdriver``` are useful for running ```end-to-end``` tests.
    * When writing tests, we’d like to mock out the parts of our code that don’t have equivalents inside our testing environment. It is then useful to be able to selectively mock these functions with test-friendly versions.

## Redux<a name = "redux"></a>
  * The store holds all of the application's state.
  * Reducers produce the state of your application.
  * The state is immutable and cannot change in place.
  * The only way to change the state is by sending a signal to the store. This signal is an action.
  * <strong>Dispatching an action</strong> means sending out a signal to the store.
  * Redux actions are nothing more than JavaScript objects.
  * The type property drives how the state should change and it's always required by Redux.
  * The payload property instead describes what should change, and might be omitted.
  * A best practice in Redux we wrap every action within a function. Such function takes the name of action creator.
  * The most important Redux methods are:
    * ```getState``` for reading the current state of the application.
    * ```dispatch``` for dispatching an action.
    * ```subscribe``` for listening to state changes.
  * The key for connecting a React component with Redux is connect.
  * <strong>mapStateToProps</strong> connects a part of the Redux state to the props of a React component.
  * <strong>mapDispatchToProps</strong> connects Redux actions to React props.
  * <strong>mapStateToProps</strong>, and <strong>mapDispatchToProps</strong> are just conventions.
  * A Redux middleware is a function that is able to intercept, and act accordingly, our actions, before they reach the reducer. 
  * Benefits from using a Redux middleware:
    * Most of the logic can live outside the UI library.
    * Middleware become reusable pieces of logic, easy to reason about.
    * Middleware can be tested in isolation.
  * redux-thunk is a middleware for Redux. With redux-thunk you can return functions from action creators, not only objects. You can do asynchronous work inside your actions and dispatch other actions in response to AJAX calls.
  * redux-saga is a Redux middleware for managing side effects.
  * redux-saga you can have clear separation between synchronous and asynchronous logic.
 

## Learning Resources:<a name = "learningResources"></a>
  * <strong>General</strong>:
    * [Complete Intro to Web Development - Frontend Masters](https://frontendmasters.com/courses/web-development-v2/)
    * [Front-End Checklist](https://github.com/thedaviddias/Front-End-Checklist)
    * [Front-End Performance Checklist](https://github.com/thedaviddias/Front-End-Performance-Checklist)
    * [Frontend Guidelines](https://github.com/bendc/frontend-guidelines)
    * [HTTP Status Codes](https://httpstatuses.com/?fbclid=IwAR0XdzvwMT7iqavv9Q0BEH6W9rAxE3G_36igC84uX9Ix6B_knFAE9vvj5Z4)
    * [Illustrated](https://illustrated.dev/)
    * [Code Guide](https://codeguide.co/)
  * <strong>JavaScript</strong>:
    * [Clean Code JavaScript](https://github.com/ryanmcdermott/clean-code-javascript)
    * [JS Tutorial](https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript)
    * [33 JS concepts](https://github.com/leonardomso/33-js-concepts)
    * [The Modern JavaScript Tutorial](https://javascript.info/)
    * [JavaScript Path - Frontend Masters](https://frontendmasters.com/learn/javascript/)
    * [Getting Started with JavaScript - Frontend Masters](https://frontendmasters.com/courses/getting-started-javascript-v2/)
    * [Code documentation for JavaScript with JSDoc](https://www.valentinog.com/blog/jsdoc/)
    * [JavaScript Documentation Standards](https://make.wordpress.org/core/handbook/best-practices/inline-documentation-standards/javascript/)
  * <strong>React</strong>:
    * [What does react.js try to solve?](https://www.quora.com/What-does-react-js-try-to-solve-Can-you-provide-a-practical-example)
    * [React Docs](https://reactjs.org/docs/getting-started.html)
    * [React Path - Frontend Masters](https://frontendmasters.com/learn/react/)
    * [React.js cheatsheet](https://devhints.io/react)
    * [React Cheat Sheet](https://reactcheatsheet.com/)
    * [A Guide to using JSDoc for React.js](https://www.inkoop.io/blog/a-guide-to-js-docs-for-react-js/)
    * [A (Mostly) Complete Guide to React Rendering Behavior](https://blog.isquaredsoftware.com/2020/05/blogged-answers-a-mostly-complete-guide-to-react-rendering-behavior/)
  * <strong>React Router</strong>:
    * [Routing and Navigation in React](https://medium.com/javascript-in-plain-english/routing-and-navigation-in-react-cffc26e8a389)
    * [Step by step guide of simple routing transition effect for React](https://medium.com/@khwsc1/step-by-step-guide-of-simple-routing-transition-effect-for-react-with-react-router-v4-and-9152db1566a0)
    * [A Modular Approach To Routing With React Router 4](https://medium.com/iqube-bits/a-modular-approach-to-routing-with-react-router-4-d4a3db9f56ae)
  * <strong>Unit Testing</strong>:
    * [React unit testing with Jest & React-testing-library](https://www.youtube.com/watch?v=3e1GHCA3GP0)
    * [Jest Docs](https://jestjs.io/docs/en/getting-started)
    * [How to Test React Components using Jest and Enzyme](https://blog.bitsrc.io/how-to-test-react-components-using-jest-and-enzyme-fab851a43875)
    * [Testing React Components with Jest and Enzyme- In Depth](https://blog.bitsrc.io/how-to-test-react-components-with-jest-and-enzyme-in-depth-145fcd06b90)
    * [How to unit test in React](https://itnext.io/how-to-unit-test-in-react-72e911e2b8d)
    * [8 simple steps to start testing React Apps using React Testing Library and Jest](https://dev.to/ibrahima92/8-simple-steps-to-start-testing-react-apps-using-react-testing-library-and-jest-3922?fbclid=IwAR0T7T3jTAtv4fAfv6n3zhNiOUyFWMMfOb9p-Fu_hB6ABKj9v4MNEs3tOjw)
    * [What and How to Test with Jest and Enzyme](https://djangostars.com/blog/what-and-how-to-test-with-enzyme-and-jest-full-instruction-on-react-component-testing/?fbclid=IwAR3T4-chn8IGM8fMqFcKMhnpBe53pe5HDVWXMOAfPTFyaQe-rryX9lzFO4U#utm_source=medium&utm_medium=blog.bitsrc.io&utm_campaign=react%20components%20testing&utm_content=continue%20reading%20the%20original%20article%20on%20our%C2%A0blog)
