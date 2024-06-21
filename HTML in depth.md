HTML Tags, typical HTML page structure looks like this:
```
<!DOCTYPE html>
<html>
	<head>
	</head>
	<body>
		<header>
		logo goes here
		<nav>
			<ul>
				<li><a href="#home">Home</a></li>
			</ul>
		</nav>
		</header>
		<main>
			<article>
				<h2>Article heading</h2>
				<p>Lorem</p>
			</article>
		</main>
		<footer
			social media links
			contact
		</footer>
	</body>
</html>
```

### Semantic HTML cheat sheet

Sectioning tags

| Tag                        | Description                                                                                                                                                      |
| -------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `<header>`                 | The header of a content section or the web page. The web page header often contains the website branding or logo.                                                |
| `<nav>`                    | The navigation links of a section or the web page.                                                                                                               |
| `<footer>`                 | The footer of a content section or the web page. On a web page, it often contains secondary links, the copyright notice, privacy policy and cookie policy links. |
| `<main>`                   | Specifies the main content of a section or the web page.                                                                                                         |
| `<aside>`                  | A secondary set of content that is not required to understand the main content.                                                                                  |
| `<article>`                | An independent, self-contained block of content such as a blog post or product.                                                                                  |
| `<section>`                | A standalone section of the document that is often used within the body and article elements.                                                                    |
| `<details>`                | A collapsed section of content that can be expanded if the user wishes to view it.                                                                               |
| `<summary>`                | Specifies the summary or caption of a `<details>` element.                                                                                                       |
| `<h1><h2><h3><h4><h5><h6>` | Headings on the web page. `<h1>` indicates the most important heading whereas `<h6>` indicates the least important.                                              |

Content tags

| Tag            | Description                                                                                        |
| -------------- | -------------------------------------------------------------------------------------------------- |
| `<blockquote>` | Used to describe a quotation.                                                                      |
| `<dd>`         | Used to define a description for the preceding `<dt>` element.                                     |
| `<dl>`         | Used to define a description list.                                                                 |
| `<dt>`         | Used to describe terms inside `<dl>` elements.                                                     |
| `<figcaption>` | Defines a caption for a photo image.                                                               |
| `<figure>`     | Applies markup to a photo image.                                                                   |
| `<hr>`         | Adds a horizontal line to the parent element.                                                      |
| `<li>`         | Used to define an item within a list.                                                              |
| `<menu>`       | A semantic alternative to `<ul>` tag.                                                              |
| `<ol>`         | Defines an ordered list.                                                                           |
| `<p>`          | Defines a paragraph.                                                                               |
| `<pre>`        | Used to represent preformatted text. Typically rendered in the web browser using a monospace font. |
| `<ul>`         | Unordered list                                                                                     |

Inline tags

| Tag        | Description                                                                                                                                                         |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `<a>`      | An anchor link to another HTML document.                                                                                                                            |
| `<abbr>`   | Specifies that the containing text is an abbreviation or acronym.                                                                                                   |
| `<b>`      | Bolds the containing text. When used to indicate importance use `<strong>` instead.                                                                                 |
| `<br>`     | A line break. Moves the subsequent text to a new line.                                                                                                              |
| `<cite>`   | Defines the title of creative work (for example a book, poem, song, movie, painting or sculpture). The text in the `<cite>` element is usually rendered in italics. |
| `<code>`   | Indicates that the containing text is a block of computer code.                                                                                                     |
| `<data>`   | Indicates machine-readable data.                                                                                                                                    |
| `<em>`     | Emphasizes the containing text.                                                                                                                                     |
| `<i>`      | The containing text is displayed in italics. Used to indicate idiomatic text or technical terms.                                                                    |
| `<mark>`   | The containing text should be marked or highlighted.                                                                                                                |
| `<q>`      | The containing text is a short quotation.                                                                                                                           |
| `<s>`      | Displays the containing text with a strikethrough or line through it.                                                                                               |
| `<samp>`   | The containing text represents a sample.                                                                                                                            |
| `<small>`  | Used to represent small text, such as copyright and legal text.                                                                                                     |
| `<span>`   | A generic element for grouping content for CSS styling.                                                                                                             |
| `<strong>` | Displays the containing text in bold. Used to indicate importance.                                                                                                  |
| `<sub>`    | The containing text is subscript text, displayed with a lowered baseline.                                                                                           |
| `<sup>`    | The containing text is superscript text, displayed with a raised baseline.                                                                                          |
| `<time>`   | A semantic tag used to display both dates and times.                                                                                                                |
| `<u>`      | Displays the containing text with a solid underline.                                                                                                                |
| `<var>`    | The containing text is a variable in a mathematical expression.                                                                                                     |

Embedded content and media tags

| Tag         | Description                                                                                                                                  |
| ----------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| `<audio>`   | Used to embed audio in web pages.                                                                                                            |
| `<canvas>`  | Used to render 2D and 3D graphics on web pages.                                                                                              |
| `<embed>`   | Used as a containing element for external content provided by an external application such as a media player or plug-in application.         |
| `<iframe>`  | Used to embed a nested web page.                                                                                                             |
| `<img>`     | Embeds an image on a web page.                                                                                                               |
| `<object>`  | Similar to `<embed>` but the content is provided by a web browser plug-in.                                                                   |
| `<picture>` | An element that contains one `<img>` element and one or more `<source>` elements to offer alternative images for different displays/devices. |
| `<video>`   | Embeds a video on a web page.                                                                                                                |
| `<source>`  | Specifies media resources for `<picture>`, `<audio>`, and `<video>` elements.                                                                |
| `<svg>`     | Used to define Scalable Vector Graphics within a web page.                                                                                   |

Table tags

| Tag          | Description                                                                                                                                                                  |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `<table>`    | Defines a table element to display table data within a web page.                                                                                                             |
| `<thead>`    | Represents the main content of a table. typically contains one `<tr>` element.                                                                                               |
| `<tbody>`    | Represents the main content of a table. Contains one or more `<tr>` elements.                                                                                                |
| `<tfoot>`    | Represents the footer content of a table. Typically contains one `<tr>` element.                                                                                             |
| `<tr>`       | Represents a row in a table. Contains one or more `<td>` elements when used within `<tbody>` or `<tfoot>`. When used within `<thead>`, contains one or more `<th>` elements. |
| `<td>`       | Represents a cell in a table. Contains the text content of the cell.                                                                                                         |
| `<th>`       | Defines a header cell of a table. Contains the text content of the header.                                                                                                   |
| `<caption>`  | Defines the caption of a table element.                                                                                                                                      |
| `<colgroup>` | Defines a semantic group of one or more columns in a table for formatting.                                                                                                   |
| `<col>`      | Defines a semantic column in a table.                                                                                                                                        |

## Metadata

The `<meta>` element has two attributes, name and content. The name attribute specifies the name of the metadata and the content attribute specifies the value of metadata.
```
<!DOCTYPE html>
<html>
	<head>
		<meta name="author" content="Joe Doe">
	</head>
	<body>
	</body>
</html>
```

Metadata that plays role in SEO (search engine optimization):
- **Author** - The author metadata specifies the author of the web page.
- **Description** - The description metadata describes the content of the web page. This is often used by search engines as descriptive text in search results. The name attribute is set to description and the content attribute is the descriptive text.
- **Keywords** - The keywords metadata was previously used to provide search keywords for search engines. However, this led to a lot of websites using the keywords metadata to manipulate search rankings. One of the major search engines now ignores this metadata and another uses keywords metadata as a spam indicator because of this, it's recommended not to include this metadata in modern web pages.
- **Robots** - tells search engines if and how they should analyze your web page. The name robots comes from the automated software often referred to as bots, that search engines used to analyze websites. The content attribute for Robots has four possible values. Index tells the bot to analyze the page. Follow tells the bot to also visit all links on the web page. No index tells the bot not to analyze the page. Some bots will ignore this so it's best not to rely on this to stop bots from analyzing your page and no follow tells the bot not to visit links on the web page. Again, some bots will ignore this value so it's best not to rely on it.
- **Viewport** - The view port metadata is important when designing responsive web pages. There are many values available for view ports metadata. The most used value for the mobile experiences is to set the width to device dash with and the initial scale to 1.0

### Metadata cheat sheet IMPORTANT!
**HTML `<meta>` tags**
The structure of a meta tag is as it follows:
- **Name** - The name of the property can be anything you like, although browsers usually expect a value they understand and can take an action upon. An example would be `<meta name="author" content="name">` to state the author of the page.
- **Content** - The content field specifies the property's value. For example, you can use `<meta name="language" content="english">`, to specify the language of the webpage to search engines.
- **Charset** - The charset is a special field that lets you specify the character encoding used for the page so that the browser can display it properly. The most frequently used is **utf-8**, and you would add it to your HTML header as follows: `<meta charset="UTF-8">`
- **HTTP-equiv** - This field stands for HTTP equivalent, and it's used to simulate HTTP response headers. This is rare to see, and it's recommended to use HTTP headers over HTML http-equiv meta tags. For example, the next tag would instruct the browser to refresh the page every 30 minutes: `<meta http-equiv="refresh" content="30">`

### Basic meta tags (meta tags For SEO)
- `<meta name="description"/>` provides a brief description of the web page.
- `<meta name=”title”/>` specifies the title of the web page.
- `<meta name="author" content="name">` specifies the author of the web page.
- `<meta name="language" content="english">` specifies the language of the web page.
- `<meta name="robots" content="index,follow" />` tells search engine how to crawl or index a certain page.
- `<meta name="google"/>` tells Google not to show the sitelinks search box for your page when showing search page.
- `<meta name="googlebot" content=”notranslate” />` tells Google you don’t want to provide an automatic translation for your page if the user uses a different language.
- `<meta name="revised" content="Sunday, July 18th, 2010, 5:15 pm" />` specifies the last modified date and time on which you have made certain changes.
- `<meta name="rating" content="safe for kids">` specifies the expected audience for your page.
- `<meta name="copyright" content="Copyright 2022">` specifies a Copyright.

### `<meta http-equiv="..."/>` tags
- `<meta http-equiv="content-type" content="text/html">` specifies the format of the document returned by the server.
- `<meta http-equiv="default-style"/>` specifies the format of the styling document.
- `<meta http-equiv="refresh"/>` specifies the duration of the page before it's considered stale.
- `<meta http-equiv=”Content-language”/>` specifies the language of the page.
- `<meta http-equiv="Cache-Control" content="no-cache">` instructs the browser how to cache your page.

### Responsive design/mobile meta tags
- `<meta name="format-detection" content="telephone=yes"/>` indicates that telephone numbers should appear as hypertext links that can be clicked to make a phone call.
- `<meta name="HandheldFriendly" content="true"/>` specifies that the page can be properly visualized on mobile devices.
- `<meta name="viewport" content="width=device-width, initial-scale=1.0"/>` specifies the area of the window in which web content can be seen.

## Bare bones layout

VSC workspace keep CSS and JS files in separate folders (specific folders for CSS and JS) index.html can remain in the root folder itself.

-  `<link>` always goes at the end of `<head>`
- TIP: create a template for future projects and keep it on local machine or git repo.


## UX with meta tags

**Open Graph Protocol** is a set of metadata rules that allows web pages to describe themselves to social networks. Social media platforms use these meta tags to create a preview of the shared web page.

**The Open Graph Protocol requires that you must always include four properties on a webpage. These are title, type, URL, and image.**
```
<head>
	<meta property="og:title" content="A brief description">
	<meta property="og:type" content="website">
	<meta property="og:url" content="https://www.example.com">
	<meta property="og:image" content="image.png">
</head>
```

Additional resources

[HTML meta tags](https://www.dofactory.com/html/metatags)

[Semantic elements](https://www.freecodecamp.org/news/semantic-html5-elements/)

[Simple bare bones HTML webpage](https://www.instructables.com/Bare-Bones-Web-Page/)

[HTML5/CSS bare-bones newsletter template](https://www.vandelaydesign.com/newsletter-tutorial/)

[Add open graph social metadata- Twitter](https://www.digitalocean.com/community/tutorials/how-to-add-twitter-card-and-open-graph-social-metadata-to-your-webpage-with-html)

[Essential meta tags for social media](https://css-tricks.com/essential-meta-tags-social-media/)

[The meta element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/meta "The meta HTML element")

[Open graph protocol](https://ogp.me/)

[Using open graph protocol on website](https://www.freecodecamp.org/news/what-is-open-graph-and-how-can-i-use-it-for-my-website/)

[Meta OGP guide for webmasters](https://developers.facebook.com/docs/sharing/webmasters/)

[Bootstrap with HTML](https://www.bootstrapdash.com/blog/use-bootstrap-with-html)

[Bootstrap Layout Examples](https://getbootstrap.com/docs/5.2/examples/ "Bootstrap Layout Examples")


## Forms and validation

There are two forms of validation: **Client-side** and **Server-side** validation.
- **Client-side validation** checks for errors as soon as they are typed into the form. This is done by the web browser or by JavaScript code, and provide the user with immediate feedback. The client-side validation process starts by checking if a form has been filled out correctly. If there are no errors, the form will be submitted to the server for processing. However, if there are errors, an error message will alert the user of the invalid data and how to change it for successful submission.
- **Server-side** validation checks for errors after the data has been submitted to the web server. Server-side validation is more secure because it prevents malicious users from tampering with your website's code and submitting invalid data to your server. When the form data is received by the web server, the backend will validate the data before processing it. This validation can run more complex checks, such as checking the data against a database, or validating the data against business requirements.

HTML has several input types that are validated by the web browser:
- `<input type="email">`
- `<input type="tel">`
- `<input type="url">`
- `<input type="date">`
- `<input type="time">`
- `<input type="number">`
- `<input type="range">`
- **Required** `<input type="text" id="username" name="username" required>`

## Input types
- **Button** -`<input type="button" value="Click me" onclick="msg()" />` Keep in mind you can also define buttons with the `<button>` tag, with the added benefit of being able to place content like text or images inside the tag.
```
<button onclick="alert('Are you sure you want to continue?')">
	<img src="https://yourserver.com/button_img.jpg"
	alt="Submit the form" height="64" width="64">
</button>
```

- **Checkbox** - Defines a check box allowing single values to be selected or deselected. They are used to let a user select one or more options of a limited number of choices.
```
<input type="checkbox" id="dog" name="dog" value="Dog">
<label for="dog">I like dogs</label>
<input type="checkbox" id="cat" name="cat" value="Cat">
<label for="cat">I like cats</label>
```
- **Radio** - Displays a radio button, allowing only a single value to be selected out of multiple choices. They are normally presented in radio groups, which is a collection of radio buttons describing a set of related options that share the same "name" attribute.
```
<input type="radio" id="light" name="theme" value="Light">
<label for="light">Light</label>
<input type="radio" id="dark" name="theme" value="Dark">
<label for="dark">Dark</label>
```
- **Submit** - Displays a submit button for submitting all values from an HTML form to a form-handler, typically a server. The form-handler is specified in the form’s "action" attribute:
```
<form action="myserver.com" method="POST">
  …
<input type="submit" value="Submit" />
</form>
```
- **Text** - Defines a basic single-line text field that a user can enter text into.
```
<label for="fname">First name:</label>
<input type="text" id="fname" name="fname">
```
- **Password** - Defines a single-line text field whose value is obscured, suited for sensitive information like passwords.
```
<label for="pwd">Password:</label>
<input type="password" id="pwd" name="pwd">
```
- **Date** - Displays a control for entering a date with no time (year, month and day).
```
<label for="dob">Date of birth:</label>
<input type="date" id="dob" name="date of birth">
```
- **Datetime-local** - Defines a control for entering a date and time, including the year, month and day, as well as the time in hours and minutes.
```
<label for="birthdaytime">Birthday (date and time):</label>
<input type="datetime-local" id="birthdaytime" name="birthdaytime">
```
- **Email** - Defines a field for an email address. It’s similar to a plain text input, with the addition that it validates automatically when submitted to the server.
```
<label for="email">Enter your email:</label>
<input type="email" id="email" name="email">
```
- **File** - Displays a control that lets the user select and upload a file from their computer. To define the types of files permissible you can use the "accept" attribute. Also, to enable multiple files to be selected, add the "multiple" attribute.
```
<label for="myfile">Select a file:</label>
<input type="file" id="myfile" name="myfile">
```
- **Hidden** - Defines a control that is not displayed but whose value is still submitted to the server.
```
<input type="hidden" id="custId" name="custId" value="3487">
```
- **Image** - Defines an image as a graphical submit button. You should use the “src” attribute to point to the location of your image file.
```
<input type="image"src="submit_img.png" alt="Submit" width="48" height="48">
```
- **Number** - Defines a control for entering a number. You can use attributes to specify restrictions, such as min and max values allowed, number intervals or a default value.
```
<input type="number" id="quantity" name="quantity" min="1" max="5">
```
- **Range** - Displays a range widget for specifying a number between two values. The precise value, however, is not considered important. This is typically represented using a slider or dial control. To define the range of acceptable values, use the “min” and “max” properties.
```
<label for="volume">Volume:</label>
<input type="range" id="volume" name="volume" min="0" max="10">
```
- **Reset** - Displays a button that resets the contents of the form to their default values.
```
<input type="reset">
```
- **Search** - Defines a text field for entering a search query. These are functionally identical to text inputs, but may be styled differently depending on the browser.
```
<label for="gsearch">Search in Google:</label>
<input type="search" id="gsearch" name="gsearch">
```
- **Time** - Displays a control for entering a time value in hours and minutes, with no time zone.
```
<label for="appt">Select a time:</label>
<input type="time" id="appt" name="appt">
```
- **Tel** - Defines a control for entering a telephone number. Browsers that do not support “tel” fall back to standard text input. You can optionally use the "pattern" field to perform validation.
```
<label for="phone">Enter your phone number:</label>
<input type="tel" id="phone" name="phone" pattern="[+]{1}[0-9]{11,14}">
```
- **URL** - Displays a field for entering a text URL. It works similar to a text input, but performs automatic validation before being submitted to the server.
```
<input type="url" id="homepage" name="homepage">
```
- **Week** - Defines a control for entering a date consisting of a week-year number and a year, with no time zone. Keep in mind that this is a newer type that is not supported by all the browsers.
```
<label for="week">Select a week:</label>
<input type="week" id="week" name="week">
```
- **Month** - Displays a control for entering a month and year, with no time zone. Keep in mind that this is a newer type that is not supported by all the browsers.
```
<label for="bdaymonth">Birthday (month and year):</label>
<input type="month" id="bdaymonth" name="bdaymonth" min="1930-01" value="2000-01">
```


### Making the most of client-side validation
- `required` - we can use client-side validation to ensure the user enters values to both fields. With the `required` attribute in the code, if one of the fields is empty and the user clicks the submit button, the request will not be submitted to the web server. The web browser will focus on the first empty input element and inform the user that a field is empty.
```
<input type="text" id="user" name="user" required> 
```
- `minlength="3"` & `maxlenght="12"` - there are two more attributes you can use to ensure the correct length of data. You can add the min length and max length attributes to the fields to specify the required length.
```
<input type="text" id="user" name="user" required minlenght="3" maxlenght="12"> 
```


### Form submission
There are two ways a form can send data to the web server using the HTTP GET method or the HTTP POST method. You can specify which method the form should use with the method attribute of the form element.
Get
```
<form method="get">
</form
```
Post
```
<form method="post">
</form>
```
**!!!!** The HTTP POST method is more secure than the HTTP GET method. The form will default to the HTTP GET method when the method attribute is not provided. When the form is submitted using the HTTP GET method, the data in the form's fields are encoded in the URL. And when the form is submitted using the HTTP POST method, the data is sent as part of the HTTP request body.
When the web server receives the request, it processes the data and sends back an HTTP response. The response indicates the result of the submission, which can be successful or fail due to invalid or incorrect data.


### Glossary: HTML Form elements
The `<form>` element in HTML is an important and useful element. The following sheet provides an overview of the `<form>` constituent elements and their common attributes with simple examples for quick reference.

- `<input>` - It is used to create interactive controls, for example, buttons and various types of text fields and so on, to accept input or data from the user. The key attribute of this element is type. Some common values for the type include: button, checkbox, date, email, number, password, submit, text, and url. These values dictate the appearance of the element.
- `<label>` - Defines a label for an element. It has an attribute "for", the value of which should be equal to the id attribute of the element it is associated with. Note how in the example above, the `<label>`is associated with the `<input>` using its id value.
- `<select>` - Defines a drop-down list of options presented to the user. It has a couple of attributes:
	- Form, the id of the form in which the drop-down appears
	- Name specifies the name of the control
	- Multiple Boolean attribute, when specified, indicates if a user can select multiple options out of the list
	- Required indicates if the user is required to select an option before submitting a form
	- Size mentions the number of visible options in a drop-down list
	- The options in a drop-down list are defined using the `<option>` element inside `<select>`. Note the example in the `<option>` description below.
- `<textarea>` - Defines a multi-line input field, typically to allow the user to input longer textual data. The common attributes for this element include:
	- cols defines the width of the text area, the default value is 20
    - form the form element the text area is associated with
    - maxlength when specified, limits the maximum number of characters that can be entered in the text area
    - minlength the minimum number of characters that the user should enter
    - readonly once set, the user cannot modify the contents
    - rows defines the number of visible text lines for the text area
- `<button>` - Defines a clickable button. The onclick attribute defines the behavior when the button is clicked by the user. For example, in the code below, an alert message is shown to the user.
- `<fieldset>` - Used to group related input elements in a form. For instance, elements related to the user’s personal information and educational qualification can be grouped separately in two field sets.
- `<legend>` - Defines a caption for the `<fieldset>` element.
- `<datalist>` - Specifies a list of pre-defined options for an input element. It differs from `<select>` since the user can still provide textual or numeric input other than the listed options.
- `<output>` - Represents the result of a calculation (typically the output of a script) or the outcome of the user action.
- `<option>` - Defines an option for the drop-down list. The following code example demonstrates how a simple list can be defined, with the rendered view below the code block.By default, the first item in the drop-down list is selected. To define a pre-selected option, add the selected attribute to the option.
- `<optgroup>` - Defines a group of related options in a drop-down list. Its attribute label names the group.

## Media Elements

For videos following file types are supported by most browsers: .mp4, .webm, .ogg.
For audio following file types are supported by most browsers: .mp3, .wav, .ogg.


### iFrames
DO NOT USE iFRAMES! EASLY MANIPULATED, EASY TO INJECT MALICIOUS CODE!


### The canvas element
There are many authoring tools available to produce animated and video game content for the web browser. But all of these are underpinned by one of four technologies GIF. WebP 2D canvas and WebGL.