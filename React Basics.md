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