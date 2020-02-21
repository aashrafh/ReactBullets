# React.JS
For the software engineering project in college, I will be in the Front-End team so this repo contains all the stuff I will learn.

# Notes
* Use camelCase in JSX attributes as it treateed as JavaScript objects not DOM elements.
* Always start component names with a capital letter: For example, <div /> represents an HTML div tag, but <Welcome /> represents a component and requires Welcome to be in scope.
* If a part of your UI is used several times (Button, Panel, Avatar), or is complex enough on its own (App, FeedStory, Comment), it is a good candidate to be a reusable component.
* Pure Functions: they do not attempt to change their inputs, and always return the same result for the same inputs.
* Impure Functions: changes its own input.
* The single React strict rule: All React components must act like pure functions with respect to their props.
* Three things about setState():
 1- Do Not Modify State Directly: The only place where you can assign this.state is the constructor.
 2- State Updates May Be Asynchronous: Because this.props and this.state may be updated asynchronously, you should not rely on their values for calculating the next state.
 3- State Updates are Merged: You can update independant variables independently with seperate setState() calls.
* State is often called local or encapsulated. It is not accessible to any component other than the one that owns and sets it.
* A “top-down” or “unidirectional” data flow. Any state is always owned by some specific component, and any data or UI derived from that state can only affect components “below” them in the tree.
* Handling events in React VS DOM:
 1- React events are named using camelCase, rather than lowercase.
 2- With JSX you pass a function as the event handler, rather than a string.
 3- You cannot return false to prevent default behavior in React. You must call preventDefault explicitly.
 4- You generally don’t need to call addEventListener. Just provide a listener when the element is initially rendered.
* Important note on how functionswork in JavaScript:
   * Generally, if you refer to a method without () after it, such as onClick={this.handleClick}, you should bind that method.
   * You have to be careful about the meaning of this in JSX callbacks. Class methods are not bound by default. If you forget to bind this.handleClick and pass it to onClick, this will be undefined when the function is actually called.
* How to avoid binding ```this```?
 1- Experimental public class fields syntax (assign it to an arrow function).
 2- Use an arrow function in the callback: ```onClick={(e) => this.handleClick(e)}```
 Note: Binding in constructor or Class field sytaxt is recommended to avoid performance problems.
* In JavaScript, true && expression always evaluates to expression, and false && expression always evaluates to false.
* Conditional Redering: it is up to you to choose an appropriate style based on what you and your team consider more readable. Also remember that whenever conditions become too complex, it might be a good time to extract a component.
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


## Learning reasources:
- [Complete Intro to Web Development](https://frontendmasters.com/courses/web-development-v2/)
- [JavaScript](https://frontendmasters.com/learn/javascript/)
- [JavaScript](https://frontendmasters.com/courses/getting-started-javascript-v2/)
- [React.JS](https://reactjs.org/docs/getting-started.html)
- [React.JS](https://frontendmasters.com/learn/react/)

## Best Practices:
- [Front-End Checklist](https://github.com/thedaviddias/Front-End-Checklist)
- [Clean Code](https://github.com/ryanmcdermott/clean-code-javascript)
- [Front-End Performance Checklist](https://github.com/thedaviddias/Front-End-Performance-Checklist)
- [33 concepts JS](https://github.com/leonardomso/33-js-concepts)
