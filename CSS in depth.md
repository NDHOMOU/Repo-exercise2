
## CSS web layout
- Flex box is short for flexible box model and it was introduced before the grid layout. For example, the flex box property with an id named sample contains the display property with flex as its value, flex box adds responsiveness to CSS with float elements and positioning one dimensional refers to the fact that a given flex box container will arrange items in either a column or a row along its axis. The flex box container applied over an element can flex to shrink or expand. Thus resulting in a flexible responsive design.
- CSS grid is similar to the flex box except it creates a two dimensional grid along both the row and column axes. For example, the grid rules for the sample id can be added after adding the display property with the grid as its value while the grid increases dimensionality and helps to create an advanced layout with relative ease. It can also lead to increased complications later.

### Undestanding flexbox
**Flexbox** is a type of container. Flexbox can overcome the limitations caused by containers such as block and inline because it does a better job of scaling over larger web pages and also provides more dynamic control of the containers. This is because it can grow, shrink and align the items inside it which give better control to the programmer over the contents and styling of the items inside the container. 

### CSS units of measurement

#### Absolute units
|**Unit**|**Name**|**Comparison**|
|---|---|---|
|Q|Quarter-millimeters|1Q = 1/40th of 1cm|
|mm|Millimeters|1mm = 1/10th of 1cm|
|cm|Centimeters|1cm = 37.8px = 25.2/64in|
|in|Inches|1in = 2.54cm = 96px|
|pc|Picas|1pc = 1/6th of 1in|
|pt|Points|1pt = 1/72nd of 1in|
|px|Pixels|1px = 1/96th of 1in|
#### Relative values
|**Unit**|**Description and relativity**|
|---|---|
|em|Font size of the parent where present.|
|ex|x-co-ordinate or height of the font element.|
|ch|Width of the font character.|
|rem|Font size of the root element.|
|lh|Value computed for line height of parent element.|
|rlh|Value computed for line height of root element which is <html>.|
|vw|1% of the viewport width.|
|vh|1% of the viewport height.|
|vmin|1% of the smaller dimension of viewport.|
|vmax|1% of the larger dimension of viewport.|
|%|Denotes a percentage value in relation to its parent element.|

### Basic flexbox
The most common uses of flexbox in CSS are creating a responsive search bar, navigation bar and image gallery.

### CSS Grid
Using the repeat function in addition to the auto properties will reduce redundancy and provide ease of code modification.
```
selector{
	display: grid; /* or inline-grid */
}
```

- `grid` A grid will allow you organize the various elements on your page.
- `grid-template-rows: none` This feature allows you configure your elements so that they are organized similarly to rows on a table.
- `grid-template-columns: none` This feature allows you to configure your elements but with this setting the elements are organized like columns on a table.
- `grid-template-areas: none` This feature allows you to configure the names of a grid and how they sit in relation to one another.
- `grid-auto-rows: auto` Default setting for all row sizes that have not been explicitly configured.
- `grid-auto-columns: auto` Default setting for all column sizes that have not been explicitly configured.
- `grid-auto-flow: row` Default location for rows that are not explicitly allocated.
- `column-gap: normal` This sets the gap between the rows.
- `row-gap: normal` This sets the gap between the rows.

#### Grid properties for container
- `grid-template-columns: measurement units | % units |repeat()` Defines the line names, and maintains a constant size of column items. Can accept a range of different measurement sizes.
- `grid-template-rows: measurement units | % units |repeat()` Defines the line names, and maintains a constant size of rows. Can accept a range of different measurement sizes.
- `grid-auto-columns: measurement unit (fixed value for all columns)` Determines the default size for columns that have not been explicitly configured.
- `grid-auto-rows: measurement unit (fixed value for all rows)` Determines the default size for rows that have not been explicitly configured.
- `grid-template: “header header” auto` This allows you to define and maintain named cells on a grid.
- `“main right” 75vh` This defines two cells named main and right, that have a sizing of 75% of the viewport hight.
- `“footer footer” 20rem` This defines two cells named footer and footer, that have a sizing of 20 root em(rem). This defines the size in relation to the html font size.

Gap
- `grid-gap: measurement units` Determines the gap between rows and columns.
- `grid-column-gap: measurement units` Determines the gap between columns.
- `grid-row-gap: m-unit-1 m-unit-2` Determines the gap between rows.

Alignment
- `justify-items: start | center | end | stretch` Defines the default space that is allot to each item on the grid.
- `align-items: start | center | end | stretch` Defines the default space related to an item along the grid’s block axis.
- `place-items: start | stretch /* shorthand for two properties above */` This feature allows you align items with the block and inline directions.

Justification
- `justify-content: start | center | end | stretch | space-between | space-evenly | space-around` Defines browser allocation of space to content items in relation to the main-axis.
- `align-content: start | center | end | stretch | space-between | space-evenly | space-around` Defines browser allocation of space to content items in relation to cross axis and block axis.
- `place-content: center | start` This feature allows you align items with the block and inline directions.

Positioning
- `grid-auto-flow: row | column | dense` This relates to how the items are placed automatically within the grid.
- `grid-auto-columns: measurement units` This relates to the size for columns created without specific size specifications.
- `grid-auto-rows: measurement units` This relates to the size for rows created without specific size specifications.

Grid properties for items (child)
- `grid-column: column position /* E.g. 1/2 */` Allows for specifying where on the grid the column is to start.
- `grid-column-start: column start position`This property determines the starting column position an item is placed on a grid.
- `grid-column-end: column end position` This property determines the end column position an item is placed on a grid.
- `grid-row: row position /* E.g. 1/2 */` Allows for specifying where on the grid the row is to start.
- `grid-row-start: row start position` This property determines the starting row position an item is placed on a grid.
- `grid-row-end: row end position` This property determines the end row position an item is placed on a grid.

Justification and alignment
- `justify-self: start | center | end | stretch` Determines how an item is positioned inside its aligned container in relation to the appropriate axis.
- `align-self: start | center | end | stretch` Aligns an item within a grid area.
- `place-self: start | stretch /* shorthand for two properties above */` This setting lets one align and justify an item within a block.

#### Flexbox
The syntax for creating a flexbox:
```
selector{
	display: flex | inline-flex
}
```
Here the selector can refer to any of the following flex attributes
- Attribute selector
- Class Selector
- ID Selector
- Type Selectors
- Universal Selectors
The display relates to how you want the selector to be shown. Setting display to flex makes the given selector a flex box. Setting display to `inline-flex` makes the selector a flex box container while will be inline.

Properties for flexbox container
`flex-direction: row | row-reverse | column | column-reverse`
It is possible to specify the direction your elements will follow. Traditionally text goes from left to right which is flex’s default setting however it can be set from right to left or even top to bottom. The four flex-direction are:
- row : organized from left to right
- row-reverse: organized from right to left
- column: organized from top to bottom
- column-reverse: organized from bottom to top.

`flex-wrap: wrap | nowrap`
The standard layout is to plot the elements from left to right in a straight line. The wrap feature allows you customize this to match the size of the window displaying the page.
- wrap: Automatically wrap the items with as the window space gets smaller.
- Nowrap: Default setting, items remain rigid and don’t respond to adjustments made to the window size.

`align-items: flex-start | flex-end | center |Stretch`
This determines how the flex items are to be positioned on the page. Items can be aligned in a variety of ways
- Flex-start: Similar to standard writing, items start at the top left-hand corner and are positioned from left to right
- Flex-end: Position begins in the bottom right hand corner.
- Center: Item is positioned from the center.
- Stretch: item expands to fill the container.

`justify-content: flex-start | flex-end | center | space-between | space-evenly`
Justify-content determines the alignment of the flex items.
- Flex-start: goes from right to left along the main axis.
- Flex-end: goes from left to right along the main axis.
- Center: Starting at the middle, alignments expands from there.
- Space-between: first and last item are flush with the left and right wall respectively, every other item is evenly spaced.
- Space-evenly: each item is equidistant from each other and the boundary wall

Properties for flexbox items (child)

`flex-grow: factor of flex’s main size`
This attribute enables the flex container to grow proportionally to the other containers present.

`flex-shrink: factor of flex’s main size`
This allows elements to shrink in relation to items around it.

`flex-basis: auto | factor of main’s size | measurement unit`
The sets the initial main size of an item. It can be overridden if other stylized elements are configured.

`order:position in flex /* Set ascending by default */`
The standard positioning of items is by source order, however this feature will enable you to configure where the items appear on the page.

`align-self: start | center | end | stretch`
This determines where on the page the child items will be positioned. Similar to the main flex attributes, start is to the left and end is to the right.


### Grid template area
Grid areas are a way to group one or more grid cells. The grid template area is an extension of this concept where you can give names to these grid areas. Once you have the names defined, you can address these new grid area items by their names and configure them accordingly. 

The property grid-template-areas is usually placed inside the body tag or any container where the grid needs to be placed, the same way that you would define the rules for the grid. The main difference is, in case of grid-template-areas the values present will be the different names.

##### Process
The process isn’t prescriptive but these are the steps in general:
- Define the grid using display property 
- Set the height and width of the grid 
- Set the grid-template-areas with the appropriate name identifiers
- Add the appropriate sizes for the rows inside the grid using grid-template-rows property 
- Add the appropriate sizes for the columns inside the grid using grid-template-columns property
```
<head>
	<link rel="stylesheet" href="gridta.css">
</head>
<body>
	<header> Header </header>
	<nav class="nav-bar"> Navigation </nav>
	<main> Main area </main>
	<footer> Footer </footer>
</body>
```
CSS Code
```
body {
	display: grid;
	height: 200px;
	grid-template-areas:"head head"
						"nav main"
						"footer footer";
	grid-template-rows: 30px 1fr 30px;
	grid-template-columns: 150px 1fr;
}

header {
	grid-area: head;
	background-color: lightsalmon;
}

.nav-bar {
	grid-area: nav;
	background-color: lightblue;
}

main {
	grid-area: main;
	background-color: lightyellow;
}

footer {
	grid-area: footer;
	background-color: firebrick;
}
```
There are five sets of rules, logically the CSS code is divided into two sections. The first is where you define the rules for the grid inside the body selector. And second is where you allocate specific rules for the different grid areas. The way these grid areas are distributed is according to how you have defined the names inside the grid-template-areas property. In the example above the relevant code is:
```
grid-template-areas:"head head"
					"nav main"
					"footer footer";
```
The ‘head’ is written twice to imply two columns and the rest of the content follows the usual convention. The number of rows will be the number of ‘pairs of quotes’ you have used which in this case is three. Namely  “head head”, “nav main” and “footer footer”. Once you know the number of rows and columns, the values for those will be set by grid-template-rows and grid-template-columns. Since these are three and two respectively here, you need to add that many values. The height simply gives the overall value of the height for the grid.

Note that the number of times you wrote “header” did not have to be two. You could write more of those and if you align the rest of the grid-names correctly, the height and width of the grid-areas will be distributed proportionately.

Grid-areas are convenient when you have a clear schematic of what you want in a grid. It’s also easier to configure individual areas if you can address them by their names. Let’s say you are designing a resume on your website, you will be able to name the different areas such as ‘Bio’, ‘Education’, ‘Work experience’ and so on. And it’s easier to use these labels when you are defining the rules. Creating a block diagram using pen and paper before starting to work on a grid is always a good idea.

### Additional resources
[Broad overview of layouts in CSS](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout)

[Detailed overview of flexboxes](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)

[Detailed overview of grids (1)](https://learncssgrid.com/)

[Detailed overview of grids (2)](https://web.dev/learn/css/grid/)

[Viewports in CSS](https://www.educba.com/css-viewport/)

[Grid layout applications](https://1stwebdesigner.com/fascinating-css-grid-layout-examples-and-tutorials/)

[Overview of different layouts](https://csslayout.io/)


Module 2
## All selectors and their specificity
As you build a website, the complexity of the code might increase to such a point that more than one CSS rule is applied to the same element. Or, you might accidentally add more than one rule over the same element. This results in conflicts as only one rule can be applied to a specific property. For example, the color of a certain p tag can either be blue or white, but not both. CSS engines use something called specificity to resolve these conflicts. Specificity is the ranking or score that helps CSS determine the final rule that will be applied to a given element.

#### Specificity hierarchy
CSS has a set of rules that it uses to 'score' or assign a certain weight to selectors and this creates a specificity hierarchy. Based on the weight, there are four categories in this hierarchy:
- Inline styles
- IDs
- Classes, attributes, and pseudo-classes
- Elements and pseudo-elements
##### Inline styles
Inline styles are attached to the elements within your HTML code like with the 'style' attribute. Inline styles have the highest specificity. That means that rules that are defined as inline styles will be applied irrespective of other rules.
##### IDs
Next in the hierarchy are IDs and by now you know that they are represented by ‘#’.  For example: `#div`

##### Classes, attributes and pseudo-classes

##### Elements and pseudo-elements
Finally, elements and something you call pseudo-elements have the lowest position in the specificity hierarchy.

### Combination selectors
There are four main types of combination selectors:
- **Descendant Selectors** are useful if you need to select HTML elements that are contained within another selector.
```
<div id="blog">
	<h1> H1 </h1>
	<div>
		<h1> Another H1</h1>
		<p> lorem </p>
	</div>
</div>
```
```
#blog h1{
	color:blue;
}
```
- **Child Selectors** are more specific than descendant selectors.
```
#blog > h1 {
	color: blue;
}
```
- **General Sibling Selectors** The selector now targets all paragraph elements that are siblings of h1 element.
```
h1 ~ p {
	color: blue;
}
```
- **Adjacent Sibling Selector** Adjacent combinators will only target the first element after the specified elements while Sibling combinators target all elements of the same type that follow the specified element.
```
div + p {
	color: blue;
}
```

### Pseudo-classes
General syntax:
```
selector:pseudo-class {
	property: value
}
```
There isn't a broadly accepted classification for pseudo-classes, you can group them in terms of general similarities and their purpose.
- User action states: `:hover` , `:active` , `:focus`
- Specific position-based states: `:first-of-type`, `:last-of-type`, `:nth-of-type()`, `:nth-last-of-type()`

### Pseudo-elements
Pseudo-elements help you style a specific part of an element. For example, you can decide to apply styling to only the first word or line in a given element.
Syntax:
```
selector::pseudo-element {
	property: value;
}
```
**It is important to note that pseudo-elements use two colon characters instead of one.**

Some examples:
- `::first-letter` 
- `::first-line`
- `::selection`
- `::marker`
- `::before`
- `::after`

Developers use the acronym LVHA to remind them of the order that they need to follow when writing pseudo-class rules. LVHA stands for link, visited, hover, active. So always apply pseudo-class styles in the correct order. First link, then visited, next hover, and lastly active.


#### CSS Pseudo cheat sheet
##### Simple Selectors
| **Selector** | **Syntax** | **Example**                  |
| ------------ | ---------- | ---------------------------- |
| Element      | element    | ```<br>div {<br><br>}<br>``` |
| Class        | .class     | ```<br>.alpha { }<br>```     |
| ID           | #id        | ```<br>#alpha { }<br>```     |
| Universal    | *          | ```<br>* { }<br>```          |
##### Variations of simple selectors
| **Elements**      | **Syntax**                | **Example**                   | **Description**                          |
| ----------------- | ------------------------- | ----------------------------- | ---------------------------------------- |
| Two classes       | .first-class.second-class | ```<br>.alpha.beta { }<br>``` | All elements with classes alpha and beta |
| Element and class | element.class             | ```<br>p.alpha { }<br>```     | All alpha class elements inside <p>      |
| Two elements      | element, element          | ```<br>p, div { }<br>```      | All <p> and <div> elements               |
| Two elements      | element element           | ```<br>p div { }<br>```       | All <div> elements inside <p>            |
##### Descendant selectors/combinators
| **Selector**     | **Syntax**      | **Example**               | **Description**                        |
| ---------------- | --------------- | ------------------------- | -------------------------------------- |
| Descendant       | element element | ```<br>div p { }<br>```   | All <p> descendants of <div>           |
| Child            | element>element | ```<br>div > p { }<br>``` | All <p> direct descendants of <div>    |
| Adjacent Sibling | element+element | ```<br>div + p { }<br>``` | <p> element directly after <div>       |
| General Sibling  | element~element | ```<br>div ~ p { }<br>``` | All <p> element iterations after <div> |
##### Attribute selectors
| **Selector**        | **Syntax**                                | **Example**                                                                         |
| ------------------- | ----------------------------------------- | ----------------------------------------------------------------------------------- |
| [attribute]         | ```<br>[href] {<br><br>}<br>```           | Selects all elements with a href attribute                                          |
| [attribute=value]   | ```<br>[lang="fr"] {<br><br>}<br>```      | Selects all elements with lang attribute that has a value of "fr"                   |
| [attribute~=value]  | ```<br>[input~=hello] {<br><br>}<br>```   | Elements with input attribute containing the whitespace separated substring "hello" |
| [attribute\|=value] | ```<br>[lang\|=en] {<br><br>}<br>```      | Elements with lang attribute value equal to "en" or "en-"(en hyphen)                |
| [attribute^=value]  | ```<br>a[href^="https"] {<br><br>}<br>``` | Every <a> element with href attribute value begins with "https"                     |
| [attribute$=value]  | ```<br>a[href$=".docx"] {<br><br>}<br>``` | Every <a> element with href attribute value ends with ".docx"                       |
| [attribute*=value]  | ```<br>a[href*="meta"] {<br><br>}<br>```  | Every <a> element with href attribute value has substring "meta"                    |

| **Pseudo-class**       | **Example**                 | **Description of selection**                                                                           |
| ---------------------- | --------------------------- | ------------------------------------------------------------------------------------------------------ |
| :active                | `a:active { }`              | All active links                                                                                       |
| :checked               | `input:checked { }`         | All the checked `<input> `elements                                                                     |
| :default               | `input:default { }`         | All default `<input>` elements                                                                         |
| :disabled              | `input:disabled { }`        | All disabled `<input>` elements                                                                        |
| :empty                 | `div:empty { }`             | All the <div> elements with no children                                                                |
| :enabled               | `input:enabled { }`         | All the enabled `<input>` elements                                                                     |
| :first-child           | `p:first-child { }`         | All the <p> elements who are the first child of a parent element                                       |
| :first-of-type         | `p:first-of-type { }`       | All the <p> element who are the first <p> element of a parent element                                  |
| :focus                 | `input:focus { }`           | Input element under focus                                                                              |
| :fullscreen            | `:fullscreen { }`           | The element in full-screen mode                                                                        |
| :hover                 | `p:hover { }`               | Action effect on mouse hover                                                                           |
| :invalid               | `input:invalid { }`         | Input elements with an invalid value                                                                   |
| :last-child            | `p:last-child { }`          | All the <p> elements who are the last child of a parent element                                        |
| :last-of-type          | `p:last-of-type { }`        | All the <p> elements who are the last <p> element of a parent element                                  |
| :link                  | `a:link { }`                | All unvisited links                                                                                    |
| :not(_selector_)       | `:not(div) { }`             | All the elements that are not a <div> element                                                          |
| :nth-child(_n_)        | `div:nth-child(3) { }`      | All the <p> elements that are the third child of a parent element                                      |
| :nth-last-child(_n_)   | `div:nth-last-child(3) { }` | All the <div> elements which are the third child of a parent element, counting from last child element |
| :nth-last-of-type(_n_) | `p:nth-last-of-type(2) { }` | The second sibling from the last child of a parent element.                                            |
| :nth-of-type(_n_)      | `p:nth-of-type(2) { }`      | The second sibling of a parent element.                                                                |
| :only-of-type          | `p:only-of-type { }`        | All the <p> elements which are only <p> elements inside its parent                                     |
| :only-child            | `p:only-child { }`          | All the <p> elements which are only child of a parent element                                          |
| :optional              | `input:optional { }`        | The input elements with no "required" attribute                                                        |
| :required              | `input:required { }`        | Selects input elements with the "required" attribute specified                                         |
| :root                  | `:root { }`                 | The Root element of document                                                                           |
| ::selection            | `::selection { }`           | The portion of an element that is selected by a user                                                   |
| :valid                 | `input:valid { }`           | All the input elements with a valid value                                                              |
| :visited               | `a:visited { }`             | Selects all visited links                                                                              |
##### Pseudo-element selectos
| **Syntax**     | **Example**              | **Description**                                               |
| -------------- | ------------------------ | ------------------------------------------------------------- |
| ::after        | `p::after { }`           | Inserts content after content of <p> element                  |
| ::before       | `p::before { }`          | Inserts content before content of <p> element                 |
| ::first-letter | `p::first-letter { }`    | Selects first letter of every <p> element                     |
| ::first-line   | `p::first-line { }`      | Selects first line of every <p> element                       |
| ::placeholder  | `input::placeholder { }` | Selects input elements with "placeholder" attribute specified |
| ::marker       | `::marker { }`           | Selects markers in a list                                     |
### Text effects cheat sheet
|Property|Values|Description|
|---|---|---|
|Text-transform|None, uppercase, lowercase, capitalize, full-width|Modify text properties|
|Font-style|Normal, italic, oblique|Font styling options such as italics|
|Font-weight|Normal, weight, lighter, bolder, 100-900|Other font styling options like change of emphasis such as making text bold|
|Text-decoration|None, underline, overline, line-through|Shorthand for auxiliary elements added to text using other properties such as text-decoration-line|


|Text-align|For horizontal alignment of text|
|---|---|
|Text-align-last|Alignment for the last line when text set to justify|
|Text-combine-upright|Multiple characters into the space of a single character placed upright like in Mandarin|
|Text-decoration-color|Color configuration of the text-decoration|
|Text-decoration-line|Line type in text-decoration such as underline, overline and so on|
|Text-decoration-style|Styles added to lines under text such as wavy, dotted and so on|
|Text-decoration-thickness|Thickness of the decoration line|
|Text-emphasis|Shorthand for other properties such as color and style|
|Text-indent|The indentation of the first line|
|Text-justify|Specifies the justification method used when text-align is "justify"|
|Text-orientation|Orientation of text in a line such as sideways, upright and so on|
|Text-shadow|Adds shadow to text|
|Text-underline-position|Declare position of underline set using the text-decoration property|

|Property|Values|Description|
|---|---|---|
|Text-overflow|Clip, ellipsis|Determines overflow behavior of text with the container|
|Word-wrap|Normal, anywhere, break-word|Applies to inline elements, alias for overflow-wrap|
|Word-break|Normal, break-all, keep-all, break-word|Used for long words to decide if words should break or overflow|
|Writing-mode|Horizontal-tb, vertical-lr, vertical-rl|Can set the text direction vertical or horizontal|
## CSS keyframes
from{} and to{} keywords and using percentages(%) syntax
```
@keyframes animation-name {
from {
	property-a: value-a;
	}
to {
	property-a: value-b;
	}
}
```
The shorthand for the animation property consists of the following properties with their default values:
- animation-name: none 
- animation-duration: 0s 
- animation-timing-function: ease 
- animation-delay: 0s 
- animation-iteration-count: 1 
- animation-direction: normal 
- animation-fill-mode: none 
- animation-play-state: running 
- animation-timeline: auto


### Preprocessors: sass, scss, Stylus
##### SASS and SCSS
Syntactically Awesome Style Sheets (SASS) is a scripting language that CSS compiles and interprets into CSS. SCSS, which stands for Sassy CSS is the syntax for SASS and can be seen as an advanced version of both SASS and CSS. The difference between SASS and SCSS is best explained by the SASS documentation, which states:

"There are two syntaxes available for Sass. The first, known as SCSS (Sassy CSS) and used throughout this reference, is an extension of the syntax of CSS. This means that every valid CSS stylesheet is a valid SCSS file with the same meaning. This syntax is enhanced with the Sass features described below. Files using this syntax have the .scss extension.

The second and older syntax, known as the indented syntax (or sometimes just “Sass”), provides a more concise way of writing CSS. It uses indentation rather than brackets to indicate the nesting of selectors and newlines rather than semicolons to separate properties. Files using this syntax have the .sass extension."

This example highlights these differences.
Regular CSS:
```
body {
	font: 100% Arial;
	color: lightblue;
}
```
This is the SCSS:
```
$font-stack: Arial;
$primary-color: lightblue;

body {
	font: 100% $font-stack;
	color: $primary-color;
}
```
SASS for the same block:
```
$font-stack: Arial
$primary-color: lightblue

body
font: 100% $font-stack
color: $primary-color
```
The variables have been defined at the top with labels such as ‘`$font-stack`’ and ‘`$primary-color`’. This is done with the ‘`$`’ suffix. The result for both will be the same, and it is not hard to imagine how much time this can save for the developer in complex code blocks where there are a number of occurrences of ‘`lightblue`’ color. These variables are placed at the top of the SCSS page. 

In the case of SASS, the variation has mainly removed the curly brackets and semi-colons from the code. 

The nesting of selectors and separation of properties here is done by means of indentation. You should note that all this syntax is valid and will produce the same output. 

For someone familiar with programming concepts, these preprocessors also allow the usage of math and other functions that can be utilized for adding rules conditionally. 

Another important functionality in SASS is the use of directives. Let us explore a couple of directives called @mixin and @include. 

##### Stylus CSS
```
body
font 100% Arial
color lightblue
```
It is not hard to miss the simplicity of the code without the colons, brackets or semicolons. But you should note that it is still allowed to use all of them in Stylus without any error. Similarly, you can also use ‘`$`’ or any other symbol before variables, but you are not ‘required’ to do so. 

For someone unfamiliar with programming, functions are a block of self-contained code that consists of steps designed to accomplish and obtain the desired output. The preprocessors, as mentioned, allow the use of functions. Here is an example of this using Stylus.
```
add(a, b)
	a + b

div
	margin add(10px, 20px)
```
What is evident in the code above is that first, you have defined a function called ‘add’ and passed the variables ‘a’ and ‘b’ inside it. You added some functionality inside the function. In this case, you add the two values a and b with the ‘+’ or addition operator. Once you’ve done that, instead of assigning a value to the ‘margin’ property, you pass the function add with numeric pixel values passed to it. The output of this code will yield to a form ‘`margin 30px`’ after compilation. 

These functions are useful when adding color gradation or creating advanced geometric shapes on your web page. 

There are other features available for preprocessors too. And, just like any programming language, the space of CSS preprocessors is also competitive, and by no means are these the only options available. 

Once you have gained an understanding of regular CSS, the usage of preprocessors should be explored. The use of preprocessors today is almost inescapable given the number of advanced features they provide which are not available in conventional CSS.


### Common errors
The common errors that developers make can broadly be classified as skill-based, rule-based, and knowledge-based. Many skill-based errors can be classified as typos. That is to say, they are mistakes made when typing in the code. These typos can include omitting delimiters at the end of the syntax, or some quotation marks while defining values and forgetting to close brackets.

CSS does not handle errors. It just passes through the code and simply ignores the lines that it does not understand. Although VS code will indicate general errors, a linter can help you find any problematic patterns or inefficiencies in your code.

### Debugging the front-end
CSS is a styling language, unlike conventional programming languages such as Python and Java, that has controls and follows a logical structure. This can make it difficult to find the exact root of the problem. Additionally, as you know, CSS does not flag errors, and most of the ‘bugs’ that you see in CSS are aesthetic in nature and need human intervention to solve. The task of debugging the front-end is more about experience than knowledge. 

The first step in debugging CSS is to find the root of the issue and isolate the elements involved. The majority of CSS issues will be with the layout, such as:

- Content overflow from parent to child or container class
- Misplaced elements in relation to its container class
- Browser and device-related inconsistencies resulting in variable viewports

##### Isolation by reduced test case
One way to deal with a problem is to replicate your code and systematically remove any code unrelated to the HTML and CSS elements that could be the source of the problem. The code should be distilled down to the least amount of code possible, and only then are suitable changes made to get the results you want. Alternatively, you can enable rules one at a time to observe their impact on the displayed elements.

##### Items inside containers
Often, isolation will not work, as the problem is the result of the relative mapping of elements. For example, with the misconfigured width of an item inside a flex layout. It’s important to check the use of suitable CSS properties in such cases. For a given item inside a grid, depending on the use case, width, grid-template-column, margin and padding can all be used to give spacing to an element. Additionally, you can also set different units that will all have their own behavior. In most cases, it helps to be familiar with the unit of measurement in relation to the container type to avoid misconfigurations.


##### Relocating items
The CSS compiler reads the elements from right to left. As an example, for a selector such as `div .alpha > p`, the element read first will be p before moving ‘outside’. When you change the position of the p from inside the .alpha class to some other position inside your code, it is easier to debug the source of the problem. This should be done on a case-specific basis.

##### Getting familiar with the box model
The box model is a very powerful source of information and can solve many issues with alignment. Using margin, padding and border is useful, but can be tricky and must be well understood.


##### Browser issues
Many times, the styling you have renders correctly in the IDE but misbehaves in a browser. That is because browsers have their own default CSS stylesheets called user-agent styles. While modern-day browsers are mostly compatible, you may encounter minor inconsistencies. Overriding the browser's settings can be done with universal selectors, in such cases written at the top of the code, and will include properties such as ‘`margin: 0px;`’ to reset the margin values set by the browser by default.


##### Dev tools
There are lots of user-friendly tools available today that can help debug CSS. However, the best tool you can use is the one provided by the browsers, called the developer tools, or dev tools. You can find these by right-clicking on a web page and selecting ‘Inspect Element’. option Note how every browser has its own expression when it comes to the configuration options, but fundamentally they are similar. Browsers today are very powerful pieces of software. If you spend time exploring the options, you may not need any other additional tools or software for debugging CSS and other front-end languages.

A couple of the important options you can find inside your browser include:

- Sources: Lists the filenames such as HTML, and CSS files used by the webpage that can be explored
- Elements: Scrolls through the code to select a specific element for exploration

Inside the Elements tab, on the right-hand side, you will find several options such as Computed layouts that will show the box model, Layouts that contain page and grid overlay options, and Font.

You can select a specific element much more easily with the help of the ‘Element selection’ icon inside the dev tools. It enables the selection of specific elements on your web page. You can also access this option by hovering over a specific element on your page that will display its properties to you.

  

[attribute^="value"]
Both alpha and beta
Child Selector, Descendant Selector
False
An element with the property set as ‘position: fixed' is placed relative to the parent (or ancestor) element, not the viewport. - False
vh, vw
grid-auto-flow, grid-template-areas


## **Retail: Lucky Shrub**

![Logo of the fictional client Lucky Shrub](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/BmaQRhhPR06mkEYYT5dOwg_f74f715c3a494d75abcd418e7611e6e1_a1.png?expiry=1719273600000&hmac=FZYrqvd_k4hJvbYGiI76mXRbXExW0PoKP58pFUi-L2M)

Based in Tuscon, Arizona, Lucky Shrub is a medium-sized garden design firm that specializes in garden design and creation, maintenance and landscaping. The company also runs a small plant nursery that sells indoor and outdoor plants, making them a one-stop shop for clients to "transform any space into an oasis you can be proud of".

Lucky Shrub was started by a husband and wife team, Jason and Maria, who share a long-time love for plants. Jason is the garden architect. He creates and oversees all designs while managing his team of landscapers. Maria manages all the marketing for the company and oversees the nursery.
![[Pasted image 20240622213650.png]]

![[Pasted image 20240622213845.png]]

![[Pasted image 20240622213957.png]]