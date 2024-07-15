### JavaScript Modules

In JavaScript, a module is simply a file.
The purpose of a module is to have more modular code, where you can work with smaller files, and import and export the so that the apps you build are more customizable and have more composable parts.

A module can be as simple as a single function in a separate file.
```
function addTwo(a, b) {
	console.log(a + b);
}
```
Say that you have a file named **addTwo.js** that contains only the above code. How would you make this file a JavaScript module? All that you would need to do to make it a JavaScript module is use the export syntax.

### Module Exports
There is more than one way to export a module in JS.
In general, there are two ways to export modules in JS:
- Using default exports
- Using named exports

#### Default Exports
You can have **one default export** per JavaScript module. Using the above **addTwo.js** file as an example, here are two ways to perform a default export:
```
export default function addTwo(a, b) {
	console.log(a + b);
}
```
alternative syntax:
```
function addTwo(a, b) {
	console.log(a + b);
}

export default addTwo;
```

#### Named Exports
Named exports are a way to export only a certain parts of a given JS file. In contrast with default exports, you can export as many items from any JavaScript file as you want. In other words, there can be only one default export, but as many named exports as you want.
```
function addTwo(a, b) {
	console.log(a + b);
}

function addThree(a, b, c) {
	console.log(a + b + c);
}
```
If you want to export both the addTwo and the addThree functions as named exports, one way to do it would be the following:
```
export function addTwo(a, b) {
	console.log(a + b);
}

export function addThree(a, b, c) {
	console.log(a + b + c);
}
```
Another way:
```
function addTwo(a, b) {
	console.log(a + b);
}

function addThree(a, b, c) {
	console.log(a + b + c);
}

export { addTwo, addThree };
```

#### Importing Modules
Just like when exporting modules in JS, there are several ways to import them. The exact syntax depends on how the module was exported. Say that you have two modules in a folder. The first module is **addTwo.js** and the second module is **mathOperations.js**. You want to import the **addTwo.js** module into the **mathOperations.js** module.

##### Importing a Module that was Exported as Default
```
// addTwo.js module:
function addTwo(a, b) {
	console.log(a + b);
}

export default addTwo;
```
To import it into the **mathOperations.js** module, you could use the following syntax:
```
import addTwo from "./addTwo";

// the rest of the mathOperations.js code goes here
```
So, you could start this import with `import` keyword, then the name under which you'll use this imported code inside the **mathOperations.js** file. You would then type the keyword `from` and finally the location of the file, without the .js extension.
Contrast the above import of the default addTwo export with the different import syntax if the addTwo function was instead a named export:
```
import { addTwo } from "./addTwo";

// the rest of the mathOperations.js code goes here
```

#### Additional reading

Below you will find links to helpful additional readings.
- [nodejs.org](https://nodejs.org/en/) 
- [npmjs.com](https://www.npmjs.com/) 
- [reactjs.org](https://reactjs.org/) 
- [https://create-react-app.dev/](https://create-react-app.dev/) 
- [VS Code](https://code.visualstudio.com/) 

### Intro to functional components
In the default React application, only one component is rendered and it's the app components located inside the index.js file that's located inside the source folder. It's important to know that every React app must contain at least one component, and it's called the root components. This component is loaded using the import statement.

ALL COMPONENT NAMES IN REACT MUST BE CAPITALIZED!
#### Functional Components
```
function Welcome() {
	return <h1>"Hello"</h1>
};
```
#### Class Components
```
class Welcome extends React.Component
{
	render() {
		return <h1>"Hello"</h1>
	};
};
```

### Transpiling JSX

**A browser cannot understand JSX syntax.**
This means that making a browser understand React code requires a lot of supporting technologies. An example of such a technology is a **transpiler**. A **transpiler** takes a piece of code and transforms it into some other code. To understand why this is done, here is an example of an ES6 variable declaration:
`const PI = 3.14`
This is perfectly valid ES6 syntax.However, if you were using a very old computer, that computer will have an old browser. Perhaps that browser was built before ES6 came out in 2015.This means that the JavaScript engine that is built into your old computer's browser is likely to be an ES5 JavaScript engine.
In ES5, the only way to declare a variable is the following:
`var pi = 3.14`
What this means is that for this old browser to understand the ES6 code, the only way to do it is by **transpiling** it.
For React code to be understood by a browser, you need to have a **transpiling step** in which the JSX code gets converted to plain JavaScript code that a modern browser can work with.

## Building The App

`npm init react-app customizing-example`
This will produce a brand-new starter app with a familiar structure. Inspecting the **src** folder of the starter app, it looks like this:
```
src/
    App.js
    App.test.js
    index.css
    index.js
    logo.svg
    reportWebVitals.js
    setupTests.js
```
Then simply add a components folder to it:
```
src/

    components/
    App.js
    App.test.js
    index.css
    index.js
    logo.svg
    reportWebVitals.js
    setupTests.js
```
Since the components folder is currently empty, you can add a component for each of the sections of the typography-focused blog. Here's the structural update:
```
src/
    components/
        Nav.js
        Promo.js
        Intro1.js
        Intro2.js
        Intro3.js
        Footer.js
	App.js
	App.test.js
	index.css
	index.js
	logo.svg
	reportWebVitals.js
	setupTests.js
```
At this point, there's no need to complicate things. You have the **Nav** component, the **Promo** component, the **Intro1**, **Intro2**, and the **Intro3** component. Finally, there's also a **Footer.js** component.
This means you've fully planned the app, based on some best practices as suggested by the official React docs website, and based on the level of complexity of the project itself. Since this project is relatively simple, this structure feels right.

### Building Components
Nav.js file:
```
function Nav() {
	return (
		<nav className="main-nav">
			<ul>
				<li>Home</li>
				<li>Articles</li>
				<li>About</li>
				<li>Contact</li>
			</ul>
		</nav>
	);
};

export default Nav;
```
Promo.js file:
```
function Promo() {
	return (
		<div className="promo-section">
			<div>
				<h1>Don't miss this deal!</h1>
			</div>
			<div>
				<h2>Subscribe to my newsletter and get all the shop items at 50% off!</h2>
			</div>
		</div>
    );
};

export default Promo;
```
Intro Components
Intro1.js:
```
function Intro1() {
    return (
		<div className="blog-post-intro">
			<h2>I've become a React developer!</h2>
			<div>
				<p>I've completed the React Basics course and I'm happy to announce that I'm now a Junior React Developer!</p>
				<p className="link">Read more...</p>
			</div>
		</div>
	);
};

export default Intro1;
```
Intro2.js component:
```
function Intro2() {
	return (
		<div className="blog-post-intro">
			<h2>Why I love front-end web development</h2>
			<div>
				<p>In this blog post, I'll list 10 reasons why I love to work as a front-end developer.</p>
				<p className="link">Read more...</p>
			</div>
		</div>
	);
};

export default Intro2;
```
Intro3.js component:
```
function Intro3() {
	return (
		<div className="blog-post-intro">
			<h2>What's the best way to style your React apps?</h2>
			<div>
				<p>There are so many options to choose from. Here's a high-level overview of the popular ones.</p>
				<p className="link">Read more...</p>
			</div>
		</div>
	);
};

export default Intro3;
```
Footer component:
```
function Footer() {
	return (
		<div className="copyright">
			<p>Made with love by Myself</p>
		</div>
	);
};

export default Footer;
```

### Additional resources for React components and where they live
- [Basic Concepts of Flexbox](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox) 
- [Importing a Component](https://create-react-app.dev/docs/importing-a-component/) 
- [Babeljs.io](https://babeljs.io/) 
- [NPM docs: package.json](https://docs.npmjs.com/cli/v7/configuring-npm/package-json) 
- [git docs: gitignore](https://git-scm.com/docs/gitignore) 
- [NPM docs: node modules folder](https://docs.npmjs.com/cli/v8/configuring-npm/folders#node-modules) 
- [webpack docs: DevServer](https://webpack.js.org/configuration/dev-server/) 
- [webpack/webpack-dev-server on GitHub](https://github.com/webpack/webpack-dev-server) 
- [Visual Studio Code keyboard shortcuts (Windows)](https://code.visualstudio.com/shortcuts/keyboard-shortcuts-windows.pdf "VS Code keyboard shortcuts Windows")
- [Visual Studio Code keyboard shortcuts (macOS)](https://code.visualstudio.com/shortcuts/keyboard-shortcuts-macos.pdf "VSC keyboards shortcuts (macOS)")


### Principles of components: Props - Properties
Recall that much like parameters in a JavaScript function which allow you to pass in values as arguments, React uses properties, or **props**, to pass data between components.
Remember first that JSX code in React is just syntactic sugar - meaning, a nicer way to write some hard-to-read code. For the browser to understand this syntactic sugar, you need to transpile JSX down to plain JavaScript code.
For example, let’s say you have a component that returns a piece of JSX:
```
function App() {
  return <h1>Hello there</h1>
}
```
… if you used the Babel transpiler to transpile this JSX syntactic sugar code down to plain JavaScript code, you’d get back some unusual code:
```
"use strict";
function App() {
	return /*#__PURE__*/React.createElement("h1", null, "Hello there");
}
```
You just want to focus on the `React.createElement("h1", null, "Hello there");` part. You can ignore the rest.

This means that the `createElement` function receives three arguments:
- The wrapping element to render.
- A null value(which is there to show an absence of an expected JavaScript object value).
- The inner content that will go inside the wrapping element.
Interestingly, the inner content that will go inside the wrapping element can also be a call to the `createElement` function.

For example, let’s say you have a slightly more complex JSX element structure:
```
function App() { 
  return (
	<div>
	<h1>Hello there</h1> 
	</div>
  )
}
```
… the transpiled return statement in plain JavaScript again returns two createElement functions:
```
"use strict";
function App() {
  return /*#__PURE__*/React.createElement("div", null, /*#__PURE__*/React.createElement("h1", null, "Hello there"));
}
```
If you format this output, remove the "use strict" line, and remove the __PURE__ comments, you get a more readable output:
```
function App() {
  return React.createElement(
    "div",
    null,
	React.createElement("h1", null, "Hello there")
  );
}
```
So now the third argument of the outer-most `React.createElement` call is another `React.createElement` call.
This is how you can nest as many elements as you want.
This means that a nested JSX structure is just a bunch of nested `React.createElement` calls, passed in to other `React.createElement` calls as their third argument.

#### The second – null – argument
The second argument of `null` can – in this case – be replaced with an empty object. In that case, your code would contain a pair of curly braces instead of the word null:
```
"use strict";

function App() {
  return React.createElement(
    "div",
    {},
	React.createElement("h1", {}, "Hello there")
  );
}
```
This object is referred to as the _props_ object. It is the main mechanism of sending data from a parent component to a child component in React. The way this works is described in React docs using the following code:
```
React.createElement(
	type,
	[props],
	[...children]
)
```
#### The third argument (...children)

This is the inner content that will go inside the wrapping element. It's what makes it possible to nest elements inside other elements, mimicking the way that HTML works.

In this reading you’ve learned how to use a transpiler to break JSX code to plain JavaScript, making its purpose more understandable.

## Props and children
Special prop called `props.children` is automatically passed to every component.

To understand the concept of `props.children`, consider the following real-life situation: you have a couple of apples and couple of pears. You'd like to carry the apples some distance, so you'll use a bag.

It's not a "bag for apples", and it's not a "bag for pears." It's just a bag. Nothing about this bag makes it such that it needs to be referred to as a bag in which you'd only and always carry apples, nor a bag in which you'd only and always carry pears.

In a way, the bag "doesn't care" if it is used to carry apples or pears. Nothing about the bag changes. There are no changes in the bag's material, size, shape, or color - because it can handle apples or pears being carried inside, without issues.

Now, consider the following component:
```
function Apples(props) {

  return (
	<div className="promo-section">
		<div>
			<h2>These apples are: {props.color}</h2>
		</div>
		<div>
			<h3>There are {props.number} apples.</h3>
		</div>
	</div>
  )
}

export default Apples
```
There is also a `Pears` component:
```
function Pears(props) {
	return (
		<h2>I don't like pears, but my friend, {props.friend}, does</h2>
	)
}
```
Now, the question is this: Let's say you want a `Bag` component, which can be used to "carry" `Apples` or `Pears`. How would you do that?
This is where `props.children` comes in.
You can define a `Bag` component as it follows:
```
function Bag(props) {
	const bag = {
		padding: "20px",
		border: "1px solid gray",
		background: "#fff",
		margin: "20px 0"
	}
	return (
		<div style={bag}>
			{props.children}
		</div>
	)
}
export default Bag
```
So, what this does in the `Bag` component is: it adds a wrapping `div` with a specific styling, and then gives it `props.children` as its content.
In conclusion, when you see a JSX element wrapping another JSX element, you can easily understand that it's all just `props.children` in the background.

### Styling JSX elements
Probably the simplest way to do this is using the `link` HTML element in the head of the **`index.html`** file in which your React app will mount.
The `href` attribute loads some CSS styles, probably with some CSS classes, and then, inside the function component's declarations, you can access those CSS classes using the `className` attribute.
```
function Promo(props) {

	return (
		<div className="promo-section">
			<div>
				<h1>{props.heading}</h1>
			</div>
			<div>
				<h2>{props.promoSubHeading}</h2>
			</div>
		</div>
	);
}
```
CSS:
```
.promo-section {
	font-weight: bold;
	line-height: 20px;
}
```
Another way to add CSS styles to components is using inline styles. The syntax of inline styles in JSX is a bit custom. Consider a starting `Promo` component, containing code that you encountered earlier:
```
function Promo(props) {
	return (
		<div className="promo-section">
			<div>
				<h1>{props.heading}</h1>
			</div>
			<div>
				<h2>{props.promoSubHeading}</h2>
			</div>
		</div>
	);
}
```
Now you can add some inline styles to it:
```
function Promo(props) {
	return (
		<div className="promo-section">
			<div>
				<h1 style={{color:"tomato", fontSize:"40px", fontWeight:"bold"}}>
					{props.heading}
				</h1>
			</div>
			<div>
				<h2>{props.promoSubHeading}</h2>
			</div>
		</div>
	);
}

export default Promo;
```
You can start updating the `Promo` component by adding the JavaScript expression syntax:
`<h1 style={}>`
As explained previously, this means that whatever code you add inside these opening and closing curly braces is to be parsed as regular JavaScript. Now let's add a **style object literal** inside of these curly braces:
`<h1 style={{color:"tomato", fontSize:"30px"}}`
You can re-write this object literal:
```
{
	color:"tomato"
	fontSize:"30px"
}
```
So, there's nothing special about this object, except for the fact that you’ve inlined it and placed it inside a pair of curly braces. Additionally, since it's just JavaScript, those CSS properties that would be hyphenated in plain CSS, such as, for example, `font-size:40px`, become camelCased, and the value is a string, making it look like this: `fontSize:"40px"`.

Besides inlining a _style object literal_, you can also save it in a variable, and then use that variable instead of passing an object literal.

That gives you an updated `Promo` component, with the styles object saved as a JavaScript variable:
```
function Promo(props) {

	cost styles = {
		color:"tomato",
		fontSize:"30px"	
	}

	return (
		<div className="promo-section">
			<div>
				<h1 style={styles}>
					{props.heading}
				</h1>
			</div>
				<h2>{props.promoSubHeading}</h2>
			</div>
		</div>
	);
}
```


### JSX syntax and the arrow function

**Function Expressions**
Let's start with a function declaration used as a component in React:
```
function Nav(props) {
	return (
		<ul>
			<li>{props.first}</li>
		</ul>
	)
}
```
This component's code returns a list item containing the value of the 'first' prop. Now let's change this function declaration to a function expression:
```
const Nav = function(props) {
	return (
		<ul>
			<li>{props.first}</li>
		</ul>
	);
}
```
The component is, for the most part, the same. The only thing that's changed is that you're now using an anonymous (nameless) function, and assigning this anonymous function declaration to a variable declared using the `const` keyword, and the name `Nav`. The rest of the code is identical.

Changing a component from a function declaration to a function expression doesn't change its behavior, or how you write the code to render the `Nav` component. It's still the same:
`<Nav first="Home" />`
You can also that this concept a step further, using arrow functions.

**Components as Arrow Functions**
Arrow functions are a core feature of the ES6 version of JavaScript. One of the main benefits of using arrow functions is its shorter syntax. Consider the Nav function expression written as an arrow function:
```
const Nav = (props) => {
	return (
		<ul>
			<li>{props.first}</li>
		<ul>
	);
}
```
So, the way to think about this is the following:
- The arrow itself can be thought of as the replacement for the `function` keyword.
- The parameters that this arrow function accepts are listed before the arrow itself.
To reiterate, take the smallest possible **anonymous ES5 function**: 
`const example = function () {}`
And then observe how this is written as a arrow function:
`const example = () => {}`
Another important rule regarding arrow function is that using the parentheses is optional if there's a single parameter that a function accepts. In other words, another correct way to write the previous Nav arrow function component would be to drop the parentheses around 'props':
```
const Nav = props => {
	return (
		<ul>
			<li>Home</li>
		</ul>
	)
}
```
In all other cases, when you write arrow functions, **for any number of parameters other than a single parameter, using parentheses around parameters is compulsory**.

For example, if your `Nav` component wasn't accepting any parameters, you'd code it with empty parentheses:
```
const Nav = () => {
	return (
		<ul>
			<li>Home</li>
		</ul>
	);
}
```
Another interesting thing about arrow functions is the **implicit return**.However, it only works if it's on the same line of code as the arrow itself. In other words, the implicit return works if your entire component is a single line of code.
To demonstrate how this works, let's re-write the `Nav` component as a one-liner:
`const Nav = () => <ul><li>Home</li></ul>`
Note that with the implicit return, you don't eve have to use the curly braces that are compulsory function body delimiters in all other cases.

**Using Arrow Functions in Other Situations**
In React, just like in plain JS, arrow functions can be used in many different situations. One such situation is using it with, for example, the `forEach()` built-in array method.
For example:
`[10, 20, 30].forEach(item => item * 10)`
The output of the above vanilla JavaScript line of code would be three number values: 100, 200, 300
You could also write this code in ES5 syntax:
```
[10, 20, 30].forEach(function(item) {
		return item * 10
	}
)
```
Regardless of how you write it, the `forEach()` method can be run on an array. The `forEach()` method accepts a single parameter: **an anonymous function**. If you write this anonymous function in ES5 syntax, then it would contain a return statement:
```
function(item) {
	return item * 10
}
```
ES6:
`item => item * 10`
Both of these functions perform the exact same task. Only the syntax is different. The ES6 function is a lot shorter because:
- The arrow function has a single parameter, so you do not need to add parentheses around the item parameter (to the left of the arrow)
- Since the arrow function fits on one line of code, you do not need to use curly braces around the function body, or the return statement; its implicit.
Arrow functions are used extensively in JSX in React, and getting used to their syntax and being able to "mentally parse" it as you read it is an important skill to have and helps you get better at writing React apps.

#### Embedded JSX Expressions
**Embedded Expressions** allow JavaScript values to be inserted into HTML or React element.

#### Ternary operators and functions in JSX
A different way of writing an `if...else` conditional. You are likely familiar with the structure of an if...else conditional. Here is a quick refresher:
```
let name = 'Bob';
if (name == 'Bob') {
	console.log('Hello, Bob');
} else {
	console.log('Hello, Friend');
};
```
Above, I gave you an example of using an `if...else` conditional. Did you know that there is another, different way, to effectively do the same thing? It's known as the **ternary operator**. A ternary operator in JavaScript uses two distinct characters: the first one is **the question mark**, that is, the `?` character. To the left of the `?` character, you put _a condition that you'd like to check for_. Just like I did in the above `if...else` statement, the condition I'm checking is `name == 'Bob'`. In other words, I'm asking the JavaScript engine to look at the value that's stored inside the `name` variable, and to verify if that value is the same as `'Bob'`. If it is, then the JavaScript engine will return the boolean value of `true`. If the value of the `name` variable is something different from `'Bob'`, the value that the JavaScript engine returns will be the boolean value of `false`.
Here is the code for previous paragraph:
`name == 'Bob ?`

Code is incomplete. I have checked the condition (the `name == 'Bob'` part). I also have the `?` character, that is, the first of the two characters needed to construct a syntactically valid ternary operator. However, I still need the second character, which is colon `:`. This character is placed after the question mark character.
`name == 'Bob' ? :`

This brings me a step closed to completing my ternary operator. Although I've added the characters needed to construct the ternary operators, I still need to add the return values. In other words, if `name == 'Bob'` evaluates to true, I want to return the words, "Yes, it is Bob!". Otherwise, I want to return the words "I don't know this person".
```
name == Bob ? "Yes, it is Bob" : "I don't lnow this person";
```

This, in essence, is how the ternary operator works. It's just some shorthand syntax that I can use as replacement for the `if` statement. To prove this is really the case, here's my starting if...else example, written as ternary operator:
```
let name = 'Bob';
name == 'Bob' ? console.log('Hello, Bob) : console.log('Hello, friend');
```

##### Using ternary expressions in JSX
Let's examine an example of a component which uses a ternary expression to randomly change the text that is displayed.
```
function Example() {
	return (
		<div className="heading">
			<h1>{Math.random() >= 0.5 ? "Over 0.5" : "Under 0.5"}</h1>
		</div>
	);
};
```
Inside the `<h1>` element, the curly braces signal to React that you want it to parse the code inside as regular JavaScript.
Then, inside the curly braces, you can add a ternary statement. Every ternary statement conceptually, expressed in pseudo-code, works like this:
`comparison ? true : false`
In the actual code example at the start of this lesson item, the comparison part, which goes to the left of the question mark, is using the >= (greater-than-or-equal-to operator), to return a Boolean value. If the result of the comparison evaluates to `true`, then the string "Over 0.5" gets returned. In the other words, whatever sits between the question mark and the semi-colon character will get returned. Otherwise, if the result of the comparison evaluates to `false`, then string "Under 0.5" gets returned. In other words, the value that sits to the right of the colon character will get returned from the ternary expression.
This is how you can use a ternary expression in JSX to check for a condition right inside a component and return a value dynamically.


##### Using function calls in JSX
Another way to work with an expression in JSX is to invoke a function. Function invocations is an expression because every expression returns a value, and function invocation will always return a value, even when that return value is `undefined`.
Like previous example, you can use function invocation inside JSX to return a random number:
```
function Example2() {
	return (
		<div className="heading">
			<h1>Here's a random number from 0 to 10: {Math.floor(Math.random() * 10) + 1}</h1>
		</div>
	);
};
```
In the `Example2` component, built in `Math.floor()` and `Math.random()` methods are being used, as well as some number values and arithmetic operators, to display random numbers between 0 and 10.
You can also extract this functionality into a separate function:
```
function Example3() {

	const getRandomNum = () => Math.floor(Math.random() * 10) +1
	return (
		<div className="heading">
			<h1>Here's a random number from 0 to 10: {getRandomNum() }</h1>
		</div>
	);
};
```
The `getRandomNum()` function can also be written as function declaration, or as a function expression. It does not have to be an arrow function.
Lets observe both alternatives: the function expression and the function declaration.
Function expression:
```
const getRandomNum = function() {
	return Math.floor(Math.random() * 10) + 1
};
```
Function declaration:
```
function getRandomNum() {
	return Math.floor(Math.random() * 10) + 1
};
```


### Expressions as props
You've already learned a bit about using expressions as props. These can be, among other things, ternary operators, function calls, or some arithmetic operations.

However, you can pass almost any kind of expression as a prop.
For example:
```
const bool = false;

function Example(props) {
	return (
		<h2>The value of the toggleBoolean prop is: {props.toggleBoolean.toString()}</h2>
	);
};

export default function App() {
	return (
		<div className="App">
			<Example toggleBoolean={!bool} />
		</div>
	);
};
```
In the example above you are using the `!bool`, that is the NOT operator, which evaluates to `true`, since `!false` is true.
Also, for the `toggleBoolean` prop to be rendered on the page you're converting its boolean value to a string using the JavaScript's built in toString method.

Here is an extension of the above code which shows more ways to work with expressions as props in React.

What is happening here is several props are being passed to the `Example` component, and rendering each of those prop's values to the screen.
```
const bool = false;
const str1 = "just";

function Example(props) {
	return (
		<div>
			<h2>
				The value of the toggleBoolean prop is:{props.toggleBoolean.toString()}
			</h2>
			<p>The value of the math prop is: <em>{props.math}</em></p>
			<p>The value of th str prop is: <em>{props.str}</em><p>
		</div>
	);
};

export default function App() {
	return (
		<div className="App">
			<Example
				toggleBoolean={!bool}
				math{(10 + 20) / 3}
				str={str1 + 'another' + 'string'}
			/>
		</div>
	);
};
```
In this improvement to the `Example` component, three props are being passed to it: `toggleBoolean`, `math`, and `str`. The `toggleBoolean` is unchanged, and the `math` prop and the `str` prop have been added.
The `math` prop is there to show that you can add arithmetic operators and numbers inside JSX, and it will be evaluated just like plain JS does.
The `str` prop is there to show that you can concatenate string, as well as string and variables - which is shown by adding string literals of "another" and "string" to the `str1` variable.

Additional resources:
- [Components and props](https://reactjs.org/docs/components-and-props.html) 
- [Intoducing JSX](https://reactjs.org/docs/introducing-jsx.html) 
- [Styling and CSS in React](https://reactjs.org/docs/faq-styling.html) 
- [Introducing expressions in JSX](https://reactjs.org/docs/introducing-jsx.html#embedding-expressions-in-jsx)


Module 2
## Types of Events
HTML: `onclick`
JSX: `onClick` camel cased


#### Eventful issues
You're now aware that React can work with most of the same events found in HTML, although React handles them differently.
This means that you may encounter unfamiliar errors when you run your event-driven React code. However, tin this reading, you'll learn about some of the most common errors associated with events and how you can deal with them.

##### Event errors
When you work in any programming environment, language, or framework you are bound to write code that throws errors for a variety of reasons.
Sometimes it's just about writing the wrong syntax. Other times it's about not thinking of all the possible scenarios and all the possible ways that things can go wrong in your code.
Regardless of what causes them, errors are part of everyday life for a developer.
The JavaScript comes with a built-in error handling system, **try...catch** syntax.
Let's examine an example of an error in JavaScript:
`(5).toUpperCase()`
Obviously you can't uppercase a number value, thus this throws the following error:
`Uncaught TypeError: 5.toUpperCase is not a function`
To handle this TypeError you can update the code with a try...catch block that instructs the code to continue running after the error is encountered:
```
try {
	(5).toUpperCase();
}
catch(e) {
	console.log(`Oops, you can't uppercase a number. Trying to do it resulted in the following`, e);
}
```
The try-catch block will output some text in the console:
**Oops you can't uppercase a number. Trying to do it resulted in the following TypeError: 5.toUpperCase is not a function**
Back to React, here's an example of a simple error in a React component:
```
function NumBillboard(props) {
	return (
		<>
			<h1>{prop.num}</h1>
		</>
	);
};
```
In React, an error in the code, such as the one above, will result in the error overlay showing in the app in the browser.
In this specific example, the error would be:
`ReferenceError`
`prop is not defined`
Since event-handling errors occur after the UI has already been rendered, all you have to do is use the error-handling mechanism that already exists in JavaScrip- that is, you just the `try...catch` blocks.

#### Event handling and embedded expressions
In this reading, you'll learn the different ways to embed expressions in event handlers in React:
- With an inline anonymous ES5 function
- With an inline, anonymous ES6 function (an arrow function)
- Using a separated function declaration
- Using a separate function expression
You may find this reading useful as  a reference sheet.
For clarity and simplicity: a function will simply console log some words. This will allow you to compare the difference in syntax between these four approaches, while the result if the event handling will always be the same: just some word output to the console.

##### Handling events using inline anonymous ES5 function
This approach allows you to directly pass in an ES5 function declaration as the `onClick` event-handling attribute's value:
```
<button onClick={function() {console.log('first example')}}>
	An inline anonymous ES5 function event handler
</button>
```
Although it's possible to write your click handlers using this syntax, it's not a common approach and you will not find such code very often in React apps.

##### Handling events using inline anonymous ES6 functions (arrow functions)
With this approach, you can directly pass in an ES6 function declaration as the `onClick` event-handling attribute's value:
```
<button onClick={() => console.log('second example')}>
	A inline anonymous ES6 function event handler
</button>
```
This approach is much more common then the previous one. If you want to keep all your logic inside the JSX expression assigned to the onClick attribute, use this syntax.

##### Handling events using separate function declarations
With this approach, you declare a separate ES5 function declaration, and they you reference its name in the event-handling `onClick` attribute, as follows:
```
function App() {
	function thirdExample() {
		console.log('third example');
	};
	return (
		<div className="thirdExample">
			<button onClick={thirdExample}>
				using a separate function declaration
			</button>
		</div>
	);
};
```
This syntax make sense to be used when your onClick logic is too complex to easily fit into an anonymous function. While this example is not really showing this scenario, imagine a function that has, for example, 20 lines of code, and that needs to be ran when the click event is triggered. This is perfect use-case for a separate function declaration.

##### Handling events using separate function expression
**Tip**: A way to determine if a function is defined as an expression or a declaration is: if it does not start the line with the keyword `function`, then it's an expression.

In the following example, you're assigning an anonymous ES6 arrow function to a `const` variable-hence, this is a function expression.
You're then using this const variable's name to handle the `onClick` event, so this is an example if handling events using a separate function expression.
```
function App() {
	const fourthExample = () => console.log('fourthExample');

	return (
		<div className="fourthExample">
			<button onClick={fourthExample}>
				using a separate function expression
			</button>
		</div>
	);
};
```
The syntax in this example is very common in React. It uses arrow functions, but also allows us to handle situations where our separate function expression spans multiple lines of code.

Additional resources:
- [Handling Events](https://reactjs.org/docs/handling-events.html#gatsby-focus-wrapper) 
- [Supported Events](https://reactjs.org/docs/events.html#supported-events)
- [SyntheticEvent](https://reactjs.org/docs/events.html#gatsby-focus-wrapper) 
- [How do I pass an event handler (like onClick) to a component?](https://reactjs.org/docs/faq-functions.html#how-do-i-pass-an-event-handler-like-onclick-to-a-component) 
- [JavaScript Expressions as Props](https://reactjs.org/docs/jsx-in-depth.html#javascript-expressions-as-props) 
- [JavaScript Expressions as Children](https://reactjs.org/docs/jsx-in-depth.html#javascript-expressions-as-children) 

## Data and Events

### Data flow in React
You've learned how the parent-child relationship can be set up so that data flows from parent to child.
In this reading, you'll learn how to detail the flow of data from parent to child. You will learn why code samples need to be clear and concise. Finally, you will explore data flow in greater detail by looking at more examples. This should act as a refresher to knowledge gained in previous courses.

##### Parent-child data flow
In React, data flow is a one-way street. Sometimes it's said that the data flow is unidirectional. Put differently, the data in React flows from a parent component to a child component. The data flow starts at the root and can flow to multiple levels of nesting, from the root component (parent component) to the child component, then the grandchild component, and further down the hierarchy.

A React app consists of many components, organized as a component tree. The data flows from the root component to all the components in the tree structure that require this data, using props.

Props are immutable(cannot be changed).

The two main benefits of this unidirectional data flow are that it allows developers to:
- comprehend the logic of React apps more quickly
- simplify the data flow
Here's a practical example of this:
Imagine that the parent component passes a prop (name) to the child component. The child component then uses this prop to render the name in the UI.
Parent component:
```
function Dog() {
	return (
		<Puppy name="Max" bowlShape="square" bowlStatus="full" />
	);
};
```

Child component:
```
function Puppy(props) {
	return (
		<div>
			{props.name} has <Bowl bowlShape="square" bowlStatus="full" />
		</div>
	);
};
```

Grandchild component:
```function Bowl(props) {
	return (
		<span>
			{props.bowlShape}-shaped bowl, and it's currently {props.bowlStatus}
		</span>
	);
};
```
Having data move through props in only one direction makes it simpler to understand the logic of how the components interact. If data were moving everywhere, all the time, then it would be much harder to comprehend its logical flow. Any optimization you tried to implement would likely not be as efficient as it could be, especially in modern React.

##### Children and data
Data in react: State and props
State data is a component’s internal data, which it can control and mutate. Props data is outside of the component and is immutable, meaning it cannot change.

### What are hooks?
One key benefit of hooks is that they solve the problem of unnecessary code reuse across components.
Hooks can be called only at the top level and only from React functions.

##### Using hooks
Now that you understand what hooks are in React and have some basic knowledge on the `useState` hook, let's dive in deeper. In this reading, you will learn how to use hooks in React components and understand the use-cases for the `useState` hook.
Let's say you have a component with an input text field. The user can type into this field. The component needs to keep track of what the user types within this text field. You can add state and use the `useState` hook, to hold the string.
As the user keeps typing, the local string needs to get updated with the latest text that has been typed.
Let's discuss the below example.
```
import {useState} from 'react';

export default function InputComponent() {
	const [inputText, setText] = useState('hello');

	function handleChange(e) {
		setText(e.target.value);
	}

	return (
		<>
			<input value={inputText} onChange={handleChange} />
			<p>You typed: {inputText}</p>
			<button onClick={() => setText('hello')}>
				Reset
			</button>
		</>
	);
};
```
To do this, let's define a React component and call it `InputComponent`. This component render three things:
- An input field
- Any text that has been entered into the filed
- A Reset button to set the filed back to its default state
As the user starts typing within the text field, the current text that was typed is also displayed.

The state variable `inputText` and the `setText` method are used to set the current text that is typed. The `useState` hook is initialized at the beginning of the component.
`const[inputText, setText] = useState('hello');`
By default, the `inputText` will be set to "hello".
As the user types, the `handleChange` function, reads the latest input value from the browser's input DOM element, and calls the `setText` function, to update the local state of `inputText`.
```
function handleChange(e) {
	setText(e.target.value);
};
```
Finally, clicking the reset button will update the `inputText` back to "hello".
Keep in mind that the `inputText` here is local state and is local to `InputComponent`. This means that outside of this component, `inputText` is unavailable and unknown. In React, state always referred to the local state of a component.
Hooks also come with a set of rules, that you need to follow while using them. This applies to all React hooks, including the `useState` hook.
- You can only call hooks at the top level of your component or your own hooks.
- You cannot call hooks inside loops or conditions.
- You can only call hooks from React functions, and not regular JS functions.
To demonstrate, let's extend the previous example, to include three input text field with a single component. This could be a registration form with fields for fist name, last name and email.
```
import { useState } from 'react';

export default function RegisterForm() {
	const [form, setForm] = useState({
		firstName:'Luke',
		lastName:'Jones',
		email:'lukeJones@email.com',
	})

	return (
		<>
			<label>
				First name:
				<input
					value={form.firstName}
					onChange={e => {
						setForm({
							...form,
							firstName: e.target.value
						});
					}}
				/>
			</label>
			<label>
				Last name:
				<input
					value={form.lastName}
					onChange={e => {
						setForm({
							...form,
							lastName: e.target.value
						});
					}}
				/>
			</label>
			<label>
				Email:
				<input
					value={form.email}
					onChange={e => {
						setForm({
						...form,
						email: e.target.value
						});
					}}
				/>
			</label>
			<p>
				{form.firstName}{' '}
				{form.lastName}{' '}
				({form.email})
			</p>
		</>
	);
};
```
Notice that you are using a `form` object to store the sate of all three text input field values:
```
const[form, setForm] =useState({
	fistName:'Luke',
	lastName:'Jones',
	email:'lukeJones@email.com',
});
```
You do not need to have three separate state variables in this case, and instead you can consolidate them all together into one `form` object for better readability.

In addition to the `useState` hook, there are other hooks that come in handy such as `useContext`, `useMemo`, `useRef`, etc. When you need to share logic and reuse the same logic across several components, you can extract the logic into a custom hook. Custom hooks offer flexibility and can be used for a wide range of use-cases such as form handling, animation, timers and more.

##### The `useRef` hook
We use the  `useRef` hook to access a child element directly.
When you invoke the `useRef` hook, it will return a `ref` object. The `ref` object has a property named `current`.
```
function TextInputWithFocusButton() {
	const inputEl = useRef (null);
	const onButtonClick = () => {
		//`current` points to the mounted text input element
		inputEl.current.focus();
	};

	return (
		<>
			<input ref={inputEl} type="text" />
			<button onClick={onButtonClick}>Focus the input</button>
		</>
	);
};
```
Using the ref attribute on the input element, I can then access the current value and invoke the focus() method on it, thereby focusing the input filed.

There are situations where accessing the DOM directly is needed, and this is where the useRef hook comes into play.

##### Prop drilling
Prop drilling is a situation where you are passing data from a parent to a child component, then to a grandchild component, and so on, until it reaches more distant component further down the component tree, where this data is required.
Here is a very simple app that focuses on the process of props passing through several components.
Please not that the goal here is not to build an app that would exist in the real world. The goal of this app is to examine the practice of prop drilling, so that you can focus on it and understand isolation.
Here is the code for the app:
```
function Main(props) {
	return <Header msg={props.msg} />;
}

function Header(props) {
	return (
		<div style={{border:"10px solid whitesmoke"}}>
			<h1>Header here</h1>
			<Wrapper msg={props.msg} />
		</div>
	);
};

function Wrapper(props) {
	return (
		<div style={{ border: "10px solid lightgray" }}>
			<h2>Wrapper here</h2>
			<Button msg={props.msg} />
		</div>
	);
};

function Button(props) {

	return (
		<div style={{ border: "20px solid orange" }}>
			<h3>This is the Button component</h3>
			<button onClick={() => alert(props.msg)}>Click me!</button>
		</div>
	);
};

function App() {

	return (
		<Main
			msg="I passed through the Header and the Wrapper and I reached the Button component"
		/>
	);
};

export default App;
```
This app is simple enough that you should be able to understand it on your own, Let's address the main points to highlight what is happening in the code above.
The top-most component of this app is the `App` component. The `App` component returns the `Main` component. The `Main` component accepts a single attribute, named `msg`.
At the very top of the app, the `Main` function declares how the `Main` component should behave. The `Main` component is responsible for rendering the `Header` component. **Note that when the `Header` component is rendered from inside `Main`, it also receives the `msg` prop**.
The `Header` component's function declaration renders an `h1` that reads "Header here", then another component named `Wrapper`. Note that the naming here is irrelevant - the components `Header` and `Wrapper`are named to make it a bit more like it might appear in a real app- but ultimately, the focus is on having multiple components, rather then describing specific component names properly.
So, the `Header` component's function declaration has a return statement, which **renders the `Wrapper` component with the `msg` prop passed to it**.
In the `Wrapper` component's function declaration is coded to receive the props object, then inside of the wrapping `div` show an `h3`. The `h3` reads "this is the button component", and then under that, there's a button element with an `onClick` event-handling attribute. This is passed to an arrow function which should alert the string that comes from the `props.mgs` prop.

Note: Context consumer - is any component that uses the state provided by context API
Passing state notes:
- Context API is used to work with state from a global store in react.
- You should always use array destructuring when working with `useState`
- The convention is to name the state-setting function using the word "set" plus whatever the name of the state variable is, all written in camelCase
- Lifting up state means moving state up from a child to the parent component
- Lifting upstate can sometimes lead to prop drilling, which lowers maintainability and modularity of a React app

Notes Data and state:
- In React, data flows in one way: from a parent component to a child component.
- One-way data flow ensures that the data is flowing from top to bottom in the component hierarchy.
- State date is data inside a component that a component, which that component controls and can mutate.
- Prop drilling is a situation where you are passing data from a parent to a child component, then to a grandchild component, and so on, until it reaches a more distant component further down the component tree, where this data is required.
- The distinction between stateful and stateless components is that the latter doesn't have its own state.
- Props are immutable and thus you should not attempt to update them in children components.
- The context API allows you to Avoid having to pass state down through multiple levels of components.
Additional Resources
- [React docs website URL which discusses the issue in depth](https://reactjs.org/blog/2018/03/27/update-on-async-rendering.html) 
- [Data flows down](https://reactjs.org/docs/state-and-lifecycle.html#the-data-flows-down) 
- [The Power Of Not Mutating Data](https://reactjs.org/docs/optimizing-performance.html#the-power-of-not-mutating-data) 
- [Add Inverse Data Flow](https://reactjs.org/docs/thinking-in-react.html#step-5-add-inverse-data-flow) 
- [Component state](https://reactjs.org/docs/faq-state.html) 
- [State: A Component's Memory](https://beta.reactjs.org/learn/state-a-components-memory) 
- [Sharing State Between Components](https://beta.reactjs.org/learn/sharing-state-between-components) 
- [State as a Snapshot](https://beta.reactjs.org/learn/state-as-a-snapshot) 
- [Basic useState examples](https://beta.reactjs.org/apis/usestate#examples-basic) 
- [Synchronizing with effects - putting it all together](https://beta.reactjs.org/learn/synchronizing-with-effects#putting-it-all-together) 
- [Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API) 
- [The event loop in JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/EventLoop)

Module 3
### Basic Type of navigation
'Dont make me think' book
In React, the entire app is loaded inside a single div, you're not actually visiting different pages, and Different views are rendered when React makes changes to the Virtual DOM, with React updating the real DOM accordingly.

#### Navigation
**Before Single-Page apps**
Most websites were implemented as multi-page applications. That is, when a user clicks on a link, the browser navigates to a new webpage, sends a request to the web server; this then responds with the full webpage and the new page is displayed in the browser.
This can make your application resource intensive to the Web Server. CPU time is spent rendering dynamics pages and network bandwidth is used sending entire webpages back for every request. If your website is complex it may appear slow to your users, even slower of they have a slow or limited internet connection.
To solve this problem, many web developers develop their web applications as single page applications.

**Single page apps**
You’re using many Single Page Applications every day. Think of your favorite social network, or online email provider, or the map application you use to find local businesses. Their excellent user experiences are driven by Single Page Applications.
A Single Page Application allows the user to interact with the website without downloading entire new webpages. Instead, it rewrites the current webpage as the user interacts with it. The outcome is that the application will feel faster and more responsive to the user.

**How does a Single-Page app work?**
When the user navigates to the web application in the browser, the Web Server will return the necessary resources to run the application. There are two approaches to serving code and resources in Single Page Applications.
1. When the browser requests the application, return and load all necessary HTML, CSS and JavaScript immediately. This is known as _bundling_. 
2. When the browser requests the application, return only the minimum HTML, CSS and JavaScript needed to load the application. Additional resources are downloaded as required by the application, for example, when a user navigates to a specific section of the application. This is known as _lazy loading_ or _code splitting_. 
Both approaches are valid and are used depending on the size, complexity and bandwidth requirements of the application. If your application is complex and has a lot of resources, your bundles will grow quite large and take a long time to download – possibly ending up slower than a traditional web application!
Once the application is loaded, all logic and changes are applied to the current webpage.

**An Example of a Single-Page App**
In a traditional website, when the button is clicked, the browser will send a POST request to the web server. The web server will return a new web page containing the button and movie name, and the web browser renders the new page.
In a Single Page Application, when the button is clicked, the browser will send a POST request to a web server. The web server will return a JSON object. The application reads the object and updates the Label with the movie name.
See, more efficient!

**Practical Differences between Single-page apps and multi-page apps**
You have a web application that has a navigation bar on top and two pages. One page shows the latest news, and the other shows the current user’s profile page. The navigation bar contains a link for each page.
In a traditional website, when the user clicks the Profile link, the web browser sends the request to the web server. The web server generates the HTML page and sends it back to the web browser. The web browser then renders the new web page.
In a Single Page Application, different pages are broken into templates (or views). Each view will have HTML code containing variables that can be updated by the application.
The web browser sends the request to the web server, and the web server sends back a JSON object. The web browser then updates the web page by inserting the template with the variables replaced by the values in the JSON object.

**Anchor tag elements in single-page Elements**
A single-page application can’t have regular anchor tag elements as a traditional web app can.
The reason for this is that the default behavior of an anchor tag is to load another HTML file from a server and refresh the page. This page refresh is not possible in a SPA that's powered by a library such as React because a total page refresh is not the way that a SPA works, as explained earlier in this lesson item.
Instead, a SPA comes with its own special implementation of anchor tags and links, which only give an illusion of loading different pages to the end user when in fact, they simply load different components into a single element of the real DOM into which the virtual DOM tree gets mounted and updated.
That's why navigation in a single-page app is fundamentally different from its counterpart in a multi-page app. Understanding the concepts outlined in this lesson item will make you a more well-rounded React developer.

#### The navbar
React Router - A library that gives you more control over the routing of components.
`npm i react-router-dom@6`
Confirm if it installed correctly, check package.json

##### Applying conditional rendering
State is all the data your app is currently working with. With this in mind, you can decide to conditionally render specific components in your app, based on whether specific state data has specific values. To make this possible, React works with the readily available JavaScript syntax and concepts.
Consider a minimalistic productivity app.

The app takes the client computer’s current datetime, and based on the data, displays one of two messages on the screen:
1. For workdays, the message is: “Get it done” 
2. For weekends, the message is: “Get some rest” 
There are a few ways you can achieve this in React.
One approach would include setting a component for each of the possible messages, which means you’d have two components. Let’s name them `Workdays` and `Weekends`.

Then, you’d have a `CurrentMessage` component, which would render the appropriate component based on the value returned from the `getDay()` function call.

Here’s a simplified `CurrentMessage` component:
```
function CurrentMessage() {
    const day = new Date().getDay();
    if (day >= 1 && day <= 5) {
        return <Workdays />
    }
    return <Weekends />
}
```
Instead of calculating it directly, you could use some historical data instead, and perhaps get that data from a user via an input, from a parent component.
In that case, the `CurrentMessage` component might look like this:
```
function CurrentMessage(props) {
    if (props.day >= 1 && props.day <= 5) {
        return <Workdays />
    }
    return <Weekends />
}
```
**Conditional rendering with the help of element variables**
To further improve your `CurrentMessage` component, you might want to use element variables. This is useful in some cases, where you want to streamline your render code - that is, when you want to separate the conditional logic from the code to render your UI.
Here’s an example of doing this with the `CurrentMessage` component:
```
function CurrentMessage({day}) {
	const weekday = (day >= 1 && day <= 5);
	const weekend = (day >= 6 && day <= 7);
	let message;

	if (weekday) {
		message = <Workdays />
	} else if (weekend) {
		message = <Weekends />
	} else {
		message = <ErrorComponent />
	}

	return (
		<div>
            {message}
        </div>
	)
}
```
The output of the `CurrentMessage` component will depend on what the received value of the day variable is. On the condition of the day variable having the value of any number between 1 and 5 (inclusive), the output will be the contents of the `Workdays` component. Otherwise, on the condition of the day variable having the value of either 6 or 7, the output will be the contents of the `Weekends` component.

**Conditional rendering using the logical AND operator**
Another interesting approach in conditional rendering is the use of the logical `AND` operator `&&`. In the following component, here's how the `&&` operator is used to achieve conditional rendering:
```
function LogicalAndExample() {
    const val = prompt('Anything but a 0')

    return (
        <div>
            <h1>Please don't type in a zero</h1>
            {val &&
                <h2>Yay, no 0 was typed in!</h2>
            }
        </div>
    )
}
```
There are a few things to unpack here, so here is the explanation of the `LogicalAndExample` component, top to bottom:

1. First, you ask the user to type into the prompt, specifying that you require anything other than a zero character; and you save the input into the `val` value.
2. In the return statement, an `h1` heading is wrapped inside a `div` element, and then curly braces are used to include a JSX expression. Inside this JSX expression is a single `&&` operator, which is surrounded by some code both on its left and on its right sides; on the left side, the val value is provided, and on the right, a piece of JSX is provided. 
To understand what will be output on screen, consider the following example in standard JavaScript:
`true && console.log('This will show')`
If you ran this command in the browser’s console, the text ‘This will show’ will be output.
On the flip side, consider the following example:
`false && console.log('This will never show')`
If you ran _this_ command, the output will just be the boolean value of `false`.
In other words, if a prop gets evaluated to `true`, using the `&&` operator, you can render whatever JSX elements you want to the right of the `&&` operator.

##### Conditional components
Have you ever visited a website that requited a user account? To log in you click on a Log In button and once you've logged in the Log In button changes to a Log Out button.
This is often done using something called conditional rendering.
Switch statements allow you to change the behaviour of code based on certain conditions being met.
For example, you can set a variable to a different value based on the result of a condition check.
```
let name;
if (Math.random() > 0.5) {
	name = "Mike"
} else {
	name="Susan"
}
```

```
let name;
let newUser = true;
if (Math.random() > 0.5 && newUser) {
	name = "Mike"
} else {
	name = "Susan"
}
```
Conditional rendering is built on the same principle. By using conditions, you can return different child components. This is often done using the props that are passed into the parent component, but can also be done base on component state.
Let's say you have two child components called `LoginButton` and `LogoutButton`; each displaying their corresponding button.
In the parent component, named `LogInOutButton`, you can check the props passed into the parent component and return a different child component based on the value of the props.
In this example, the props contains a property named `isLoggedIn`. When this is set to `true`, the `LogoutButton` component is returned. Otherwise, the `LoginButton` component is returned.
```
function LogInOutButton(props) {
const isLoggedIn = props.isLoggedIn;
	if (isLoggedIn) {
		return <LogoutButton />;
	} else {
		return<LoginButton />;
	}
}
```
Then when the `LogInOutButton` parent component is used, the prop can be passed in.
`<LogInOutButton isLoggedIn={false} />`
This is a simple example showing how you can change what is displayed based on a condition check. You will use this often when developing React applications.
Note: The logical AND operator is used to conditionally render some JSX elements based on whether a value to the LEFT of the AND operator evaluates to true.

### What is an asset and where does it live?
Best practice is to keep assets folder within source folder. You should keep the sound file and image file in the Assets folder, as they will be used directly in your app components and are necessary for the app to work correctly.

##### Bundling assets
Earlier, you learned what assets are in React and the best practices for storing them in your project folders.
In this reading, you will learn about the advantages and disadvantages of embedding assets, including examples of client/server-side assets. You will also learn about the trade-offs inherent in using asset-heavy apps.
The apps files will likely be bundled when working with a React app. Bundling is a process that takes all the imported files in an app and joins them into a single file, referred to as **bundle**. Several tools can perform this bundling. Since, in this course you have used the `create-react-app` to build various React Apps, you will focus on webpack. This is because webpack is the build in tool for the `create-react-app`.

Let’s start by explaining what webpack is and why you need it.
Simply put, webpack is a module bundler.

Practically, this means that it will take various kinds of files, such as SVG and image files, CSS and SCSS files, JavaScript files, and TypeScript files, and it will bundle them together so that a browser can understand that bundle and work with it.

Why is this important?

When building websites, you could probably do without webpack since your project's structure might be straightforward: you may have a single CSS library, such as Bootstrap, loaded from a CDN (content delivery network). You might also have a single JavaScript file in your static HTML document. If that is all there is to it, you do not need to use webpack in such a scenario.

However, modern web development can get complex.

Here is an example of the first few lines of code in a single file of a React application:
```
import React from 'react';
import '@atlaskit/css-reset';
import styled from 'styled-components';
import './index.css';
import { ThemeProvider } from './contexts/theme';
import { DragDropContext } from 'react-beautiful-dnd';
import { BrowserRouter as Router, Route, Switch } from 'react-router-dom';
import Nav from './components/Nav';
import data from './data';
import Loading from './components/Loading';
```

The imports here are from fictional libraries and resources because the specific libraries are not necessary. All these different imports can be of various file types: .js, .svg, .css, and so on.

In turn, all the imported files might have their own imported files, and even those might have their imports.

This means that depending on other files, all of these files can create a **dependency graph**. The order in which all these files are loading is essential. That dependency graph can get so complex that it becomes almost impossible for a human to structure a complex project and bundle all those dependencies properly.

This is the reason you need tools like webpack.
So, webpack builds a dependency graph and bundles modules into one or more files that a browser can consume.

While it is doing that, it also does the following:
- It converts modern JS code - which can only be understood by modern browsers - into older versions of JavaScript so that older browsers can understand your code. This process is known as _transpiling_. For example, you can transpile ES7 code to ES5 code using webpack.  
- It optimizes your code to load as quickly as possible when a user visits your web pages. 
- It can process your SCSS code into the regular CSS, which browsers can understand. 
- It can build source maps of the bundle's building blocks  
- It can produce various kinds of files based on rules and templates. This includes HTML files, among others.
Another significant characteristic of webpack is that it helps developers create modern web apps.

It helps you achieve this using two modes: **production** mode or **development** mode.

In development mode, webpack bundles your files sot that they are optimized for speed. This means that files are minified and organized to take up the least amount of memory. So they are optimized for speed because these bundles are fast to download when a user visits the website online.

Once all the source files of your app have been bundled into a single bundle file, then that single bundle file gets served to a visitor browsing the live version of your app online, and the entire apps contents get served at once.

This works great for smaller apps, but if you have a more extensive app, this approach is likely to affect your site’s speed. The longer it takes for a web app to load, the more likely the visitor will leave and move on to another unrelated website. There are several ways to tackle this issue of a large bundle.

One such approach is code-splitting, a practice where a module bundler like webpack splits the single bundle file into multiple bundles, which are then loaded on an as-needed basis. With the help of code-splitting, you can **lazy load** only the parts that the visitor to the app needs to have at any given time. This approach significantly reduces the download times and allows React-powered apps to get much better speeds.

There are other ways to tackle these problems.

An example of a viable alternative is SSR (Server-side rendering).

With SSR, React components are rendered to HTML on the server, and the visitor downloads the finished HTML code. An alternative to SSR is client-side rendering, which downloads the index.html file and then lets React inject its own code into a dedicated HTML element (the **root** element in create-react-app). In this course, you’ve only worked with client-side rendering.
Sometimes, you can combine client-side rendering and server-side rendering. This approach results in what’s referred to as **isomorphic apps**.
In this reading, you learned about the advantages and disadvantages of embedding assets, including examples of client/server-side assets. You also learned about the trade-offs inherent in the use of asset-heavy apps.

##### Media packages
`npm install react-player`

```
import React from "react";
import ReactPlayer from "react-player/youtube";

const App = () => {
	return (
		<div>
			<MyVideo />
		</div>
	);
};

const MyVideo = () => {
	return (
		<ReactPlayer url='https://www.youtube.com/watch?v=ysz5S6PUM-U' />
	);
};

export default App;
```

Additional resources:
- [webpack docs](https://webpack.js.org/guides/getting-started/)
- [webpack asset management](https://webpack.js.org/guides/asset-management/)
- [npm docs](https://docs.npmjs.com/)
- [ReactPlayer on npm](https://www.npmjs.com/package/react-player)
- [Video and audio content on the web](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Video_and_audio_content)