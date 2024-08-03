Learning objectives:
- Render and transform lists with keys in React
- Distinguish between controlled and uncontrolled React components
- Create controlled form component in React
- Share component state by lifting state up to the closest common ancestor
- Share global state using React Context


Module 1
## Rendering lists in React
Use `map()` method in JavaScript to to transform lists of data. In JavaScript, when you deal with lists of items of any kind, you need to use the array type. JavaScript offers different methods that you can use with arrays to perform various operations. In order to perform a transformation operation, you must use the map method

Map method always returns a new array, so you need to define a new variable.
Using the `map()` method in JavaScript to display data fetched from a third party or external provider differently in your app is a common use case of the `map()` method.

With React, you can transform any list of items into a collection of React components.
When a JSX transformation will be part of the render method of components, you need to use curly braces to wrap your dynamic data so it can be accessed.

Lab:
```
const DessertsList = (props) => {
	const lowCaloriesDesserts = props.data
		.filter((dessert) => {
			return dessert.calories < 500;
		})
		.sort((a, b) => {
			return a.calories - b.calories;
		})
		.map((dessert) => {
			return (
				<li>
					{dessert.name} - {dessert.calories} cal
				</li>
			);
		});
	return <ul>{lowCaloriesDesserts}</ul>;
}

export default DessertsList;
```

### What are Keys in React?
A “key” is **a special string attribute you need to include when creating lists of elements in React**. Keys are used in React to identify which items in the list are changed, updated, or deleted. Keys are used to give an identity to the elements in the lists.

NOTE
Although item indexes can be used as keys, using indexes as keys can create problems if the order of your list of items is prone to change and can negatively affect performance. Using unique and stable identifiers, such as item IDs, is recommended instead.

Additional resources:
- [Map()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map) allows you to create new arrays populated with the results of calling a transformation function on every element. 
- [Rendering lists on official React docs website](https://beta.reactjs.org/learn/rendering-lists#rendering-data-from-arrays) dives deeper into how to display multiple similar components from a collection of data, providing examples of both filtering and transformations.
- [React keys on official docs](https://beta.reactjs.org/learn/rendering-lists#where-to-get-your-key) offers a comprehensive set of memotecnic rules to reinforce how to use keys properly.

### Controlled components vs. Uncontrolled components
In most cases, React recommends using controlled components to implement forms. While this approach aligns with the React declarative model,  uncontrolled form fields are still a valid option and have their merit.

**Uncontrolled Inputs**
Uncontrolled inputs are like standard HRML form inputs:
```
const Form = () => {
	return(
		<div>
			<input type="text" />
		</div>
	);
};
```
They remember exactly what you typed , being the DOM itself that maintains that internal state. How can you then get their value? The answer is by using a React ref.

In the code bellow, you can see how a ref is used to access the value of the input whenever the form is submitted.
```
const Form = () => {
	const inputRef = useRef(null);

	const handleSubmit = () => {
		const inputValue = inputRef.current.value;
		//Do something with the value
	}
	return (
		<form onSubmit={handleSubmit}>
			<input ref={inputRef} type="text" />
		</form>
	);
};
```
In other words, you must **pull** the value from the filed when needed.

Uncontrolled components are the simplest way to implement form inputs. There are certainly valued cases for them, especially when your form is straightforward. Unfortunately, they are not as powerful as their counterpart.

**Controlled Inputs**
Controlled inputs accept their current value as a prop and callback to change that value. That implies that the value of the input has to live in the React somewhere. Typically, the component that renders the input(like a form component) saves that in its state:
```
const Form = () => {
	const [value, setValue] = useState("");

	const handleChange = (e) => {
		setValue(e.target.value)	
	}

	return (
		<form>
			<input
				value={value}
				onChange={handleChange}
				type="text"
			/>
		<form>
	);
};
```
Every time you type a new character, the `handleChange` function is executed. It receives the new value of the input, and then it sets in in the state. In the code example above, the flow would be as follows:
- The input starts out with an empty string `""`
- You type `a` and `handleChange` gets an `a` attached in the event object, as `e.target.value`, and subsequently calls `setValue` with it. The input is then updated to have the value of `a`.
- You type `b` and `handleChange` gets called with `e.target.value` being `ab` and sets that to the state. That gets set into the state. The input is then re-rendered once more, now with `value= "ab"`
This flow **pushes** the value changes to the form component instead of pulling like the ref example from the uncontrolled version. Therefore, the Form component always has the input's current value without needing to ask for it explicitly.

As a result, your data (React state) and UI (input tags) are always in sync. Another implication is that forms can respond to input changes immediately, for example, by:
- Instant validation per field
- Disabling the submit button unless all the fields have valid data
- Enforcing a specific input format, like phone or credit card numbers
Sometimes you will find yourself not needing any of that. In that case uncotrolled could be a more straightforward choice.

**The file input type**
There are some specific form inputs that are always uncontrolled, like the file input tag.
In React, an `<input type="file" />` is always uncontrolled component because its value is read-only and can't be set programmatically.
The following example illustrates how to create a ref to the DOM node to access any files selected in the form submit handler:
```
const Form = () => {
	const fileInput = useRef(null);

	const handleSubmit = (e) => {
		e.preventDefault();
		const files = fileInput.current.files;
		//Do something with the files here
	}

	return (
		<form onSubmit={handleSubmit}>
			<input
				ref={fileInput}
				type="file"
			/>
		</form>
	);
};
```

**Conclusion**
Uncontrolled components with refs are fine if your form is incredibly simple regarding UI feedback. However, controlled input files are the way to go if you need more features in your forms.

Evaluate your specific situation and pick the best option that works best for you.

The table bellow summarizes the features that each one supports.

|Feature|Uncontrolled|Controlled|
|---|---|---|
|One-time value retrieval (e.g. on submit)|**Yes**|**Yes**|
|Validating on submit|**Yes**|**Yes**|
|Instant field validation|No|**Yes**|
|Conditionally disabling a submit button|No|**Yes**|
|Enforcing a specific input format|No|**Yes**|
|Several inputs for one piece of data|No|**Yes**|
|Dynamic inputs|No|**Yes**|
### Creating a Form component in React
Note: Controlled components (component's state handles form data), Uncontrolled components (DOM handles form data)

Basic form example
`create react-app`
```
import "./App.css"

function App () {
	return (
		<div className="App">
			<form>
				<filedset>
					<div className="Field">
						<label>Name:</label>
						<input type="text" placeholder="Name" name="name" />
					</div>
					<button type="submit">Submit</button>
				</fieldset>
			</form>
		</div>
	);
}

export default App;
```
This is uncontrolled version.
In React, this current implementation is considered an uncontrolled form, having all the states living in the DOM.

```
import { useState} from "react";
import "./App.css"

function App () {
	const [name, setName] = useState("");

	const handleSubmit = () => {
		e.preventDefault();
		setName("");
		console.log("Form has been submitted!");
	}
	
	return (
		<div className="App">
			<form onSubmit={handleSubmit}>
				<filedset>
					<div className="Field">
						<label htmlFor="name">Name:</label>
						<input
						id="name"
						type="text" 
						placeholder="Name" 
						name="name"
						value={name}
						onChange={(e) => setName(e.target.value)}
						/>
					</div>
					<button disabled={!name} type="submit">
						Submit
					</button>
				</fieldset>
			</form>
		</div>
	);
}

export default App;
```
This is controlled version.

### Context 
Props and state
???
React solved the problem of parent components having to drilldown props all the way to the children that need to consume them by introducing the Context API.
Context is useful for global state. It is the right tool when you need to share data that can be considered global for a tree of React components.

Using an ID generated by a library that guarantees no duplications.


Module 2
### React Hooks
`useState` hook works with state in React components.

The concept of a array destructuring, recall that array destructuring is a way to get individual items from an array of items and save those individual items as separate components.
Array destructuring example:
```
let veggies = [parslay, onion, carrot];
const [v1, v2, v3] = veggies;
console.log(v1); //parslay
console.log(v2); //onion
console.log(v3); //carrot
```

**Object destructuring**
When destructuring objects, you have to destructure a property of an object using that exact properties name as the name of the destructured variable. This makes objects a lot stricter in terms of what you can name your destructure variables. For that reason, react uses the array data structure for the used state hooks return value.


### Working with complex data in useState
An example of holding state in an object and updating it based on user-generated events:
```
import {useState} from "react";

export default function App() {
	const[greeting, setGreeting] = useState({ greet:"Hello"});
	console.log(greeting, setGreeting);

	function updateGreeting() {
		setGreeting({greet: "Hello, WWW"});
	}

	return(
		<div>
			<h1>{greeting.greet}</h1>
			<button onClick={updateGreeting}>Update greeting</button>
		</div>
	);
}
```
While this works, it's not the recommended way of working with state objects in React, this is because the state object usually has more than a single property, and it is costly to update the entire object just for the sake of updating only a small part of it.

**The correct way to update the state object in React when using useState**
The suggested approach for updating the state object in React when using useState is to copy the state object and then update the copy.
This usually involves using the spread operator (`...`).
Here's the updated code:
```
import {useState} from "react";

export default function App() {
	const [greeting, setGreeting] = useState({greeting: "Hello"});
	console.log(greeting, setGreeting);

	function updateGreeting() {
		const newGreeting = {...greeting};
		newGreeting.greet = "hello WWW";
		setGreeting(newGreeting);
	}

	return (
		<div>
			<h1>{greeting.greet}</h1>
			<button onClick={updateGreeting}>Update greeting</button>
		</div>
	);
}
```

**Incorrect ways of trying to update the state object**
To prove that a copy of the old state object is needed to update state, let’s explore what happens when you try to update the old state object directly:
```
import { useState } from "react";

export default function App() {
	const [greeting, setGreeting] = useState({ greet: "Hello" });
	console.log(greeting, setGreeting);

	function updateGreeting() {
		greeting = {greet: "Hello, World-Wide Web};
		setGreeting(greeting);
	}

	return (
		<div>
			<h1>{greeting.greet}</h1>
			<button onClick={updateGreeting}>Update greeting</button>
		</div>
	);
}
```
The above code does not work because it has a `TypeError` hiding inside of it. Specifically, the `TypeError` is: "Assignment to constant variable".
In other words, you cannot reassign a variable declared using const, such as in the case of the `useState` hook's array destructuring:
`const [greeting, setGreeting] = useState({greet: "Hello"});`
Another approach you might attempt to use to work around the suggested way of updating state when working with a state object might be the following:
```
import { useState } from "react";

export default function App() {
	const [greeting, setGreeting] = useState({ greet: "Hello, World" });
	console.log(greeting, setGreeting);
	
	function updateGreeting() {
		greeting.greet = "Hello, World-Wide Web;
		setGreeting(greeting);
	}
	return (
		<div>
			<h1>{greeting.greet}</h1>
			<button onClick={updateGreeting}>Update greeting</button>
		</div>
	);
}
```
The above code is problematic because it doesn't throw any errors; however, it also doesn't update the heading, so it is not working correctly. This means that, regardless of how many times you click the "Update greeting" button, it will still be "Hello, World".

To reiterate, the proper way of working with state when it's saved as an object is to:
1. Copy the old state object using the spread (...) operator and save it into a new variable and 
2. Pass the new variable to the state-updating function

**Updating the state object using arrow functions**
Now let's use a more complex object to update state. The state object now has two properties: greet and location.
The intention of this update is to demonstrate what to do when only a specific property of the state object is changing, while keeping the remaining properties unchanged:
```
import { useState } from "react";

export default function App() {
	const [greeting, setGreeting] = useState(
		{
			greet: "Hello",
			place: "World"
		}
	);
	console.log(greeting, setGreeting);

	function updateGreeting() {
		setGreeting(prevState => {
			return {...prevState, place: "World-Wide Web"}
		});
	}
	
	return (
		<div>
			<h1>{greeting.greet}, {greeting.place}</h1>
			<button onClick={updateGreeting}>Update greeting</button>
		</div>
	);
}
```
The reason this works is because it uses the previous state, which is named `prevState`, and this is the previous value of the greeting variable. In other words, it makes a copy of the `prevState` object, and updates only the place property on the copied object. It then returns a brand-new object:
`return {...prevState, place: "WWW"}`
Everything is wrapped in curly braces so that this new object is built correctly, and it is returned from the call to `setGreeting`.


Note:
You can use an object with multiple properties as the initial value of the state variable, just like the formData state variable in the example, where the useState hook was invoked with the object containing two properties (the goal property and the by property).

##### What are side effects?
The name of the use Effect hook is closely related to the concept of an effect or more precisely a side effect.
A side effect is something that makes a function in pure. Did you know that functions can be classified as pure and impure simply put pure functions don't have side effects.

**Pure function**
A pure function should receive specific input. That is a specific parameter will always return the exact same output. No matter how many times it gets invoked.
Pure function example:
```
function EstablishedYear (props) {
	return <h1>Established year: {props.year}</h1>
}

function App() {
	return <EstablishedYear year={1345} />
}

export default App;
```

**Impure function**
Impure function will perform a side effect. That means it will do things such as invoke console log, invoke, fetch or invoke browsers geolocation functionality. In this context, a side effect can be thought of as something external to or outside of a function.
```
function ShoppingCart(props) {
	const total = props.count * props.price;
	console.log(total); // Call to Browser API
	return <h1>Total: {total}</h1>
}
export default function App() {
	return (
		<ShoppingCart items={5} pricePerItem={10} />
	)
}
```
It is an impure function because of the line that reads console log total. 
The console log call makes the function impure as it's a call to a browser, application programming interface or API. The ShoppingCart function now depends on something outside of itself and even outside of the react app to work properly. So how should you deal with the issue of impure functions in react. Well, it's all about containing the impure actions inside their own special areas. To do this and react you need to use the use Effect hook.
useEffect hook example:
```
function ShoppingCart(props) {
	const total = props.count * props.price;

	useEffect(()=>console.log(total), []);

	return <h1>Total: {total}</h1>
}
```

### What is the useEffect hook?
A built-in React hook best suited to perform side effects in your React components.

The code you place inside the `useEffect` hook always runs after your components mounts, or in other words, after React has updated the DOM. In addition, depending on your configuration via the dependencies array, your effects can also run when certain state variables or props change.
By default, if no second argument is provided to the `useEffect` function, the effect will run after every render.
```
useEffect(()=> {
	document.title = 'Little Lems';
});
```
However, that may cause performance issues, especially if your side effects are computationally intensive. A way to instruct React to skip applying an effect is passing an array as a second parameter to `useEffect`.

In the bellow example, the integer variable `version` is passed as the second parameter. That means that the effect will only be re-run if the `version` number changes between renders.
```
useEffect(() => {
	document.title = `Little Lem, v${version}`;
}, [version]); //Only re-run the effect if version changes
```
If `version` is 2 and the component re-renders and version still equals 2, React will compare `[2]` form the previous render and `[2]` form the next render. Since all items inside the array are the same, React would skip running the effect.

**Use multiple Effects to Separate Concerns**
React doesn't limit you in the number of effects your component can have. In fact, it encourages you to group related logic together in the same effect and break up unrelated logic into different effects.
```
function MenuPage(props) {
	const [data, setData] = useState([]);

	useEffect (() => {
		document.title = 'Little Lem';
	}, []);

	useEffect(() => {
		fetch(`https://whateverURL.com/menu/${id}`)
			.then(response => response.json())
			.then(json => setData(json));
	}, [props.id]);

	//...
};
```
Multiple hooks allow you to split the code based on what it is doing, improving code readability and modularity.

**Effects with Cleanup**
Some side effects may need to clean up resources or memory that is not required anymore, avoiding any memory leaks that could slow down your applications.
For example, you may want to set up a subscription to an external data source. In that scenario, it is vital to perform a cleanup after the effect finishes its execution.
How can you achieve that? In line with the previous point of splitting code based on what it is doing, the `useEffect` hook has been designed to keep the code for adding and removing a subscription all together, since it's tightly related.
If your effects return a function, React will run it when it's time to clean up resources and free unused memory.
```
function LittleLemonChat(props) {
	const [status, chatStatus] = useState('offline');

	useEffect(() => {
		LemonChat.subscribeToMessages(props.chatId, () => setStatus('online'))
		return () => {
			setStatus('offline');
			LemonChat.unsubscribeFromMessages(props.chatID);
		};
	}, []);

	// ...
}
```
Returning a function is optional and it's the mechanism React provides in case you need to perform additional cleanup in your components.

React will make sure to run the cleanup logic when it's needed. The execution will always happen when the components unmounts. However, in effects that run after every render and not just once, React will also clean up the effect from previous render before running the new effect next time.

Additional resources:
- The article on [destructuring](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment) assignment describes how the destructuring assignment, which allows you to get values out of the array that gets returned when the useState hook is invoked, works in more detail. 
- [The read props inside the child component](https://beta.reactjs.org/learn/passing-props-to-a-component#step-2-read-props-inside-the-child-component) link on the Beta version of React docs discusses how to use destructuring assignment to get values out of the props object. 
- The [useState reference on official React docs website](https://beta.reactjs.org/apis/react/useState#usestate) helps you understand how to work with this hook and some of the caveats involved. 
- The [useEffect reference on official React docs website](https://beta.reactjs.org/apis/react/useEffect#useeffect) helps you understand the syntax of this hook and goes into some depth to explain how to use and troubleshoot the useEffect hook. 

### Rules of hooks
The four main rules of hooks are as follows. 
- First, you should only call hooks from a React component function. 
- Second, you should only call hooks at the top level of a React component function. 
- Third, you are allowed to call multiple state hooks or effect hooks inside a component. 
- And finally, always make these multiple hook calls in the same sequence.


##### What you need to know before fetching data

Fetch is used to make a server requests to retrieve some JSON data from it. Fetch API is a set of functionalities that we have at our disposal to use in JavaScript to make such a server request.

Note: JavaScript uses the fetch function it is delegating duties to an external API so that it can continue its process. This is known as asynchronous JavaScript.

### Data fetching using hooks
Fetching data from a third-party API is considered a side-effect that requires the use of `useEffect` hook to deal with the Fetch API calls in React. To understand what that entails, let me illustrate it with a code example where a component is fetching some data from an external API to display info about a cryptocurrency.
```
import {useState, useEffect} from "react";

export default function App() => {
	const [btcData, setBtcData] = useState({});
	useEffect(() => {
		fetch(`https://api.coindesk.com/v1/bpi/currentprice.json`)
			.then((response) => response.json())
			.then((jsonData) => setBtcData(jsonData.bpi.USD))
			.catch((error) => console.log(error));
	}, []);
	return (
		<>
			<h1>Current BTC/USD data</h1>
			<p>Code: {btcData.code}</p>
			<p>Symbol: {btcData.symbol}</p>
			<p>Rate: {btcData.rate}</p>
			<p>Description: {btcData.description}</p>
			<p>Rate Float: {btcData.rate_float}</p>
		</>
	);
}
```
This example shows that in order to fetch data from a third party API, you need to pass an anonymous function as a call to the `useEffect` hook.
```
useEffect(
	() => {
		//... data fetching code goes here
	},
	[]
);
```
The code above emphasizes the fact that the `useEffect` hook takes two arguments, and that the first argument holds the anonymous function, which, inside its body, holds the data fetching code.
Alternatively, you might extract this anonymous function into a separate function expression or function declaration, and then just reference it.
Using the above example, that code could be presented as follows:
```
import {useState, useEffect} from "react";
export default function App () {
	const [btcData, setBtcData] = useState({});

	const fetchData = () => {
		fetch(`https://api.coindesk.com/v1/bpi/currentprice.json`)
			.then((response) => response.json())
			.then((jsonData) => setBtcData(jsonData.bpi.USD))
			.catch((errror) => console.log(error));
	};

	useEffect(() => {
		fetchData();
	}, []);

	return (
		<>
			<h1>Current BTC/USD data</h1>
			<p>Code: {btcData.code}</p>
			<p>Symbol: {btcData.symbol}</p>
			<p>Rate: {btcData.rate}</p>
			<p>Description: {btcData.description}</p>
			<p>Rate Float: {btcData.rate_float}</p>
		</>
	);
}
```
This code does the same thing, but this second example is cleaner and better organized. One additional thing that can be discussed here is the `return` statement of the above example. Very often, the response from fetching third-party data might fail, or be delayed. That's why it an be useful to provide different renders, based on whether or not data has been received. The simplest conditional rendering might involve setting up two renders, based on whether data has been successfully fetched or not.
Example:
```
	return someStateVariable.lenght > 0 ? (
		<div>
			<h1>Data returned:</h1>
			<h2>{someStateVariable.results[0].price}</h2>
		</div>
	) : (
		<h1>Data pending...</h1>
	)
```
In this example, I'm conditionally returning an `h1` and `h2`, if the length of the `someStateVariable` binding's length is longer than 0. This approach would work if the `someStateVariable` holds an array. If the `someStateVariable` is initialized as an empty array, passed to the call to the `useState` hook, then if would be possible to update this state variable with an array item that might get returned from a `fetch()` call to a third-party JSON data provider. If this work out as described above, the length of the `someStateVariable` would increase from the starting length of zero - because an empty array's length is zero.
Let's inspect the conditional `return` again:
```
	return someStateVariable.lenght > 0 ? (
		<div>
			<h1>Data returned:</h1>
			<h2>{someStateVariable.results[0].price}</h2>
		</div>
	) : (
		<h1>Data pending...</h1>
	)
```
If the data fetching fails, the text of "Data pending..." will render on the screen, since the length of the `someStateVariable` will remain being zero.

### When to choose `useReducer` vs `useState`

The `useState` hook is best used on less complex data. While its possible to use any kind of a data structure when working with `useState`, it's better to use it with primitive data types, such as strings, numbers or booleans.
The `useReducer` hook is best used on more complex data, specifically, arrays or objects.
While this rule is simple enough, there are situations where you might be working with a simple object and still decide to use the `useState` hook.
Such decision might stem from the simple fact that working with `useState` can sometimes feel easier than thinking about how the state is controlled when working with `useReducer`.
It might help conceptualizing this dilemma as a gradual scale, on the left side of which, there is the `useState` hook with primitive data types and simple use cases, such as toggling a variable on or off.
At the end of this spectrum, there is the `useReducer` hook used to control state of large state-holding objects.
There is no clear-cut point on this spectrum, at which point you would decide: "If my state object has three or more properties, I'll use the `useReducer`  hook".
Sometimes such a statement might make sense and other times it might not.
What's important to remember is to keep your code simple to understand, collaborate on, contribute to, and build from. One negative characteristic of `useState` is that it often gets hard to maintain as the state gets more complex.
On the flip side, a negative characteristic of `useReducer` is that requires more prep work to begin with. There's more setup involved. However, once this setup is completed, it gets easier to extend the code based on new requirements.

### Custom hooks

Why would you want to write a custom hook?
Hooks give you a repeatable, streamlined way to deal with specific requirements in your React apps. For example, `useState` hook gives us a reliable way to deal with state updates in React components.
A custom hook is simply a way to extract a piece of functionality that you can use again and again. Put differently, you can code a custom hook when you want to avoid duplication or when you do not want to build a piece of functionality from scratch across multiple React projects. 
```
import { useState } from "react";

function App() {
	const [count, setCount] = useState(0);

	function increment() {
		setCount(prevCount => prevCount + 1)
	}
	
	return (
		<div>
			<h1>Count: {count}</h1>
				<button onClick={increment}>Plus 1</button>
		</div>
	);
}

export default App;
```
This is a simple app with an `h1` heading that shows the value of the count state variable and a button with an `onClick` event-handling attribute which, when triggered, invokes the `increment()` function.
The hook will be simple too. It will console log a variable's value whenever it gets updated.
Remember that the proper way to handle `console.log()` invocation is to use the `useEffect` hook. 
This means that my custom hook will:
- Need to use the `useEffect` hook
- Be a separate file that you'll then use in the App component.

**How to name a custom hook?**
A custom hook needs to have a name that begins with use.
Because the hook in this example will be used to log values to the console, let's name the hook `useConsoleLog`.

**Coding a custom hook**
First, you'll add it as separate file, which you can name `useConsoleLog.js`, and add it to the root of the `src` folder, in the same place where the App.js component is located.
```
import { useEffect } from "react";

function useConsoleLog(varName) {
	useEffect(() => {
	    console.log(varName);
  }, [varName]);
}

export default useConsoleLog;
```

**Using a custom hook**
Now that the custom hook has been coded, you can use it in any component in your app. Since the app is the example has a single component, named App, you can use it to update this component.
The `useConsoleLog` hook can be imported as follows:
`import useConsoleLog from "./useConsoleLog";` 
And then, to use it, under that state-setting code, I'll just add the following line of code:
`useConsoleLog(count);` 
```
import { useState } from "react";
import useConsoleLog from "./useConsoleLog";

function App() {
	const [count, setCount] = useState(0);
	useConsoleLog(count);
	
	function increment() {
		setCount(prevCount => prevCount + 1);
	}
	
	return (
	    <div>
			<h1>Count: {count}</h1>
			<button onClick={increment}>Plus 1</button>
		</div>
	);
}

export default App;
```

Module 3
### JSX, Components and Elements

##### High-order components
Best practices:
- never mutate a component inside a HOC (dont mutate the original component)
One of the possible temptations is to modify the component that is provided as an argument, or in other words, mutate it. That's because JavaScript allows you to perform such operations, and in some cases, it seems the most straightforward and quickest path. Remember that React promotes immutability in all scenarios. So instead, use composition and turn the HOC into a pure function that does not alter the argument it receives, always returning a new component.
```
const HOC = (WrappedComponent) => {
	//Dont mutate this and mutate the original component
	WrappedComponent = () => {
	}
}
```
- pass unrelated props to your wrapped component
HOC adds features to a component. In other words, it enhances it. That's why they shouldn't drastically alter their original contract. Instead, the component returned form a HOC is expected to have a similar interface to the wrapped component. HOCs should spread and pass through all the props that are unrelated to their specific concern, helping ensure that HOCs are as flexible and reusable.
```
const withMousePosition = (WrappedComponent) => {
	const injectProp = {mousePosition: {x: 10, y:10}};

	return (originalProps) => {
		return <WrappedComponent injectedProp={injectedProp} {...originalProps} />;
	};
};
```
- maximize composability by leveraging the `Component => Component` signature
The primary signature of a HOC is a function that accepts a React component and returns a new component. Sometimes HOCs can accept additional arguments that act as extra configuration determining the type of enhancement the component receives.
`const EnhancedComponent = HOC(WrappedComponet, config)`

The most common signature for HOCs uses a functional programming pattern called "currying" to maximize function composition. The signature is used extensively in React libraries, such as React Redux.
`const EnhancedComponent = connect(selector, actions)(WrappedComponent);`
This syntax may seem strange initially, but if you break down what's happening separately, it would be easier to understand.
```
const HOC = connect (selector, actions);
const EnhancedComponent = HOC(WrappedComponent);
```
`connect` is a function that returns a higher-order component, presenting a valuable property for composing several HOCs together. 
Single argument HOCs like the ones you have explored so far, or the one returned by the connect function has the signature `Component => Component`. It turns out that functions whose output type is the same as its input type are really easy to compose together.
```
const enhance = compose (
	//These are both single-argument HOCs
	withMousePositio,
	withURLLocation,
	connect(selector)
);

//Enhance is a HOC
const EnhancedComponent = enhance(WrappedComponent)
```

##### Caveats
High-order components come with a few caveats that aren't immediately obvious
- Don't use HOCs inside other components: always create your enhanced components outside any component score. Otherwise, if you do so inside the body of other components and a re-render occurs, the enhanced component will be different. That forces React to remount it instead of just updating it. As a result, the component and its children would lose their previous state.
```
const Component = (props) => {
	//This is wrong. Never do this
	const EnhancedComponent = HOC(WrappedComponent);
	return <EnhancedComponent />;
};

//This is the correct way.
const EnhancedComponent = HOC(WrappedComponent);
const Component = (props) => {
	return <EnhancedComponent />;
}
```
- Refs aren't passed through: since React `refs` are not `props`, they are handled specially by React. If you add a ref to an element whose component is the result of a HOC, the ref refers to an instance of the outermost container component, not the wrapped component. To solve this, you can use the React.forwardRef API.