

##CSS Outline

- **Why CSS?**
- **Rules**
- **Properties**
- **Selectors**
	- Classes
	- IDs

---

##Why CSS?

- **Separation of concerns**
- **Better page layout control**
- **Less work**

---

##CSS Standards

- **CSS 1: Released in 1996**
- **CSS 2: Released in 1998**
- **CSS 2.1: Released in 2011**
- **CSS 3: Modularized and currently being released**
- **CSS 4: Not really a thing**
	- Level 4 modules currently under consideration
	- Really part of CSS3 or rather CSS

---

##Basics

- **CSS is declarative**
	- It declares how HTML markup will look
- **Always start with HTML markup**
	- Layer on CSS rules for the presentation of the content

---

##Rules

- **Made up of a selector and a declaration**
- **Selector**
	- Specifies HTML elements to be styled
- **Declaration**
	- Property
		- Specifies what is to be changed on the element
	- Value
		- Specifies what the property will be assigned to

---

##Rules [cont.]

- Element **selector** identifies elements to style
	- h1
- Presentation **declaration**
	- color: yellow
- Selected rules affect presentation of element
	- [http://jsfiddle.net/kamrenz/HaK5j/](http://jsfiddle.net/kamrenz/HaK5j/)

CSS


    h1 { color: yellow; }

HTML

    <h1>A bright outlook</h1>

---

##Rules [cont.]

- **Every CSS declaration needs to end in a semicolon**
	- Only the last rule does not need a semi-colon
	- Best practice to add a semi-colon even after the last rule

>
	h1 {
	  background-color: green;
	  color: white;
	}

---

###Comments



- Every language has comments

CSS

	h1 {
	  /* Single line comment */
	  background-color: green;
	  /*
	    Multi-line comment
	  */
	  color: white;
	}

---

###Syntax Gotcha

- **Values with units**
- **Zero bound measurements**
- **White-space**

	    .box {
    	  /* No white-space between units and values */
    	  margin: 1px;
    	}
    	section {
    	  /* No units with a zero bound measurement */
    	  margin: 0;
    	}
    	/* White-space doesn’t matter most of the time */
    	p        {
    	        margin   :       1px; }

---

###CSS Rule Location

- **Usually defined in an external style sheet (external)**
	- styles.css
- **Can be written in `<style>` tags (internal)**

	    <style>
    	  h1 { background-color: green; }
    	</style>

- **Can be written inline on HTML elements (inline)**

	`<h1 style=“background-color: green”>Hello World</h1>`

---

###Element Selector

- **Otherwise known as a type selector**
- **Matches HTML elements by their tag name**
- **Examples:**
	- `h1` matches an `h1` element
	- `h1`, `p` matches an `h1` and/or a `p` element
	- [http://jsfiddle.net/kamrenz/g78TT/](http://jsfiddle.net/kamrenz/g78TT/)

CSS

    h1, p {
      color: blue;
    }

HTML

    <h1>A bright outlook</h1>
    <p>Sometimes it just is…</p>

---

###Class Selector

- Matches HTML elements by a `class` attribute on the element
- Examples:
	- `.important` matches any elements having the class tokens
	- [http://jsfiddle.net/kamrenz/fCXGn/](http://jsfiddle.net/kamrenz/fCXGn/)

CSS

    .important {
      background-color: red;
    }

HTML

    <h1>A bright outlook</h1>
    <p class=“important”>Sometimes it just is…</p>

---

###ID Selector

- **Matches HTML elements by an `id` attribute on the element**
- **Examples:**
	- `#heading` matches the element having the id heading
	- [http://jsfiddle.net/kamrenz/KEXNt/](http://jsfiddle.net/kamrenz/KEXNt/)
	
CSS

    #heading {
      font-weight: normal;
    }

HTML

    <h1 id=“heading”>A bright outlook</h1>
    <p>Sometimes it just is…</p>

---

##CSS Colors

---

###Color

- **Colors can be specified a few different ways**
	- **background-color**: Specifies the background color of the box
	- **color**: Specifies the color of the font

---

###Color [cont.]

---

- **Color choices**
	- **rgb(0,255,255)** : red, green, blue … aqua color
		- Colors are specified by their intensity
		- 0 no color
		- 255 is full intensity
		- Can also be specified rgb(0,100%,100%)
	- **rgba(0,0,0,0.5)** : alpha channel specifies the opaqueness
		- 0 is transparent
		- 1 is opaque

CSS

    color: rgb(0,255,255);
    color: rgba(0,0,0,0.5);
    
---

###Color [cont.]

- **rgba isn’t supported by IE8**
	- Make sure to specify an **rgb** fallback
	- IE8 will understand and use rgb and not be able to utilize rgba
	- Chrome / Firefox will understand rgb and rgba, so rgba will be utilized because it comes later

CSS

    /**
     * IE
     **/ 
    color: rgb(0,255,255); 
    color: rgba(0,0,0,0.5);

---

###Color [cont.]

- **Color choices**
	- **#00FFFF** : red, green, blue … aqua color
		- Colors are specified by three dublets
		- If the numbers are repeating we could specify them with shorthand
			- **#0FF**

CSS

    color: #00FFFF;
    color: #0FF;

---

###Color [cont.]

- **Color choices**
	- Color names: **purple**, **blue**, **green**, **cornflowerblue**
	- Need the complete list of names?
		- [http://www.w3.org/TR/css3-color/](http://www.w3.org/TR/css3-color/)

CSS

    color: pink;
    color: cornflowerblue;

---

##CSS Units

---

###Absolute Units

- Specify a fixed unit of measurement
- Usually better for print media
- **px**: Pixels are absolute units equal to 1/96th of an inch
- **pt**: Points are absolute units equal to 1/72nd of an inch

---

###Relative Units

- **Specify a value in relation to another value**
- **Usually better for digital screen media**
- **%: Percentage of the inherited value**
	- Relative to the container
- **em: Equal to the width of the current font-size (i.e. the width of the capital letter “M”)**
	- Relative to the encapsulating container font-size
	- Can have a compounding issue from inheritance
	- [http://jsfiddle.net/kamrenz/gdc8tyjm/3/](http://jsfiddle.net/kamrenz/gdc8tyjm/3/)

---

###Relative Units

- **Specify a value in relation to another value**
- **rem: Equal to the em size of the root element (i.e. `<html>`)**
	- Gets rid of the compounding issue as the unit is based off the root element (i.e. set html font-size to 100%)
	- Allows for easy resizing of elements
	- No compounding issues
	- [http://jsfiddle.net/kamrenz/Lukn17jn/](http://jsfiddle.net/kamrenz/Lukn17jn/)

---

###rem

- **IE8 can’t handle rem units**
	- [http://caniuse.com/#feat=rem](http://caniuse.com/#feat=rem)
	- IE9 and IE10 can even have [some problems](https://connect.microsoft.com/IE/feedback/details/776744)
- **Provide a px fallback for rem**
	- 62.5% makes the calculation for a fallback simple

CSS

    /* Set the base to make conversion simple */
    html { font-size: 62.5% }
      
    h1 {
        font-size: 14px;
        font-size: 14px;
    }

---

##CSS Box Model

---

###CSS Box Model

- top, right, bottom, left (like a clock)

---

##CSS Floats and Clears

---

###CSS Floats

- **We can float left or right**
- **Boxes stack against each other**
- **Gotcha: There is no float: center**
	- Use margin: 0 auto; for that

---

###CSS Clears

- If you DON’T want an item to flow and stack next to the item before it, use the css “clear” property.
- clear: both; (clears both left and right floated items)

---

##CSS Text

---

###Styling Text Content

- **Fonts**
- **Line-height**
- **Other textual content**

---

###Font Family

- **Property for choosing the family of fonts to represent text**

- **Main types of font families**
	- serif: Fonts with extra at “hooks” at edges of letters
		- times, times new roman, georgia
	- sans-serif: Fonts with no hooks at the edges of letters
		- verdana, roboto, arial, helvetica, geneva
	- monospace: Fonts where every character take up the same space
		- courier, andale mono

---

###Font Family

- **Font families are specified in a named ordered list**
	- First in list will be used if the browser has it available
	- Last in list should be a generic font family in case none are found
- **Best practice**
	- Use sans-serif for most text
	- Use monospace for code in text
	
>

    body {
    	font-family: Verdana, Geneva, sans-serif;
    }

---

###Font Size

- **Font size can be set with absolute or relative measurements**
	- Relative are preferred
- **Let’s take a look at how font sizes scale based on
the user’s browser settings**
	- [http://jsbin.com/dilifovipe/edit?html,css,output](http://jsbin.com/dilifovipe/edit?html,css,output)

>

    body {
    	font-size: 2em;
    }

---

###Font Weight

- **Sets the font boldness**
- **Can be set with keywords or numbers**
	- normal, bold, bolder, lighter
	- 100, 200, 300, 400, 500, 600, 700, 800, 900

**Hello World**

```<h1>Hello World</h1>```
    


    body {
    	font-weight: bold;
    }

---

###Font Style

- **Sets the font to be italic or oblique**

- **Italic: Separate font type**
- **Oblique: Normal font type, but rendered slanted**

**Hello World**

```<h1>Hello World</h1>```
    


    body {
    	font-style: italic;
    }

---

###Font Variant

- **Sets the font to be small caps**

- **Italic: Separate font type**
- **Oblique: Normal font type, but rendered slanted**

**Hello World**

```<h1>Hello World</h1>```
    


    body {
    	font-variant: small-caps;
    }

---

###Line Height

- When you need to change the height of a line use **line-height**
	- A unit-less number … typical use
	- %, em or rem
	- [http://jsfiddle.net/kamrenz/wvsropLq/4/](http://jsfiddle.net/kamrenz/wvsropLq/4/)

---

###Text Indentation


- **Used to indent first-line of text with white-space**

HTML

    <h1>Hello World</h1>

CSS

    p {
      text-indent: 2em;
 	}

---

###Text and Elements

- **What happens if we have more text than can fit in
the width of an element?**

I am a

long

piece

of text


---

###Text and Elements

- **How do we get the text to stay in one line?**

I am a long piece of text

CSS

    div {
      white-space: nowrap;
    }

---

###Text and Elements

- **How do we keep the white-spacing?**

HTML

    <h1>Hello world
     this
 	is great</h1>
   
CSS

    h1 {
      white-space: pre;
 	}

---

##CSS Tables (an intro)

We’ll cover more in the next lesson

---

###Table Styling

- **Tables used to be styled directly on the HTML**
	- Not anymore

HTML 4:

    <TABLE BORDER=“1" BORDERCOLOR=“red" cellspacing="20"
    cellpadding="20%">
 	
- **What can be styled within a table?**
	- Fonts, text and background colors

---

###Table Spacing


- How is the whitespace between table cells
removed?

May not want that white space

---

###Table Spacing [cont.]


- **Border spacing**

May not want that white space

	table {
	  border-spacing: 0;
	}

---

###Table Spacing [cont.]


- **Border collapse**

Gives us a single border between cells instead of double.

	table {
	  border-collapse: collapse;
	}

---

##Lab 5: CSS

- **Goal: Gain familiarity with HTML5 & CSS**
- **Specifications:**
	- Make sure to use em units for sizing
	- Make the document font-size 1.5em
	- Increase the header font-size by 2x, change its background color and change its text color
	- Make your image as wide as the browser window
	- Make the first paragraph italicized

---

##Lab 5: CSS [cont.]

- **Goal: Gain familiarity with HTML5 & CSS**
- **Specifications:**
	- Make the second paragraph bold without using the bold keyword
	- Make a span element in the second paragraph and make it monospace font and 1/2 the size of the surrounding text
	- Make the third paragraph triple-spaced
	- Make the list header the size of the document text
	- Make Moose be in small-caps
	- Make the link 3/4 the size of the document text

---

##Lab 5: CSS [cont.]

- **Goal: Gain familiarity with HTML5 & CSS**
- **Specifications:**
	- Change from ems to rems and mimic the exact sizing

---

##Tables Outline

- **Tables**
- **Head (th), Rows (tr), Cell’s (td)**
- **Captions and Spanning**
- **Extras**
- **Styling**

---

###Tables

- Used to represent tabular data
- `<table>` : Table root
- `<tr>` : Table row
- `<th>` : Table head
- `<td>` : Table cell data

---

###Tables [cont.]

	<table>
		<tr>
			<th>Rank</th>
			<th>States</th>
		</tr>
		<tr>
			<td>1</td>
			<td>Colorado</td>
		</tr>
		<tr>
			<td>2</td>
			<td>Michigan</td>
		</tr>
	</table>

---

###Table Caption

- Defines a caption for a table
- Needs to be placed within the table tag

>
	<table>
	  <caption>Money</caption>
	  <tr>
	    <td>$50.00</td>
		<td>$45.00</td>
	  </tr>
	</table>

---

###Table Spanning

- Cells can be spanned across multiple rows

>
	<table>
	  <tr>
		<th rowspan="2">Snacks</th>
		<td>Score Bar</td>
	  </tr>
	  <tr>
		<td>Mountain Dew</td>
	  </tr>
	</table>

---

###Table Spanning [cont.]

- Cells can be spanned across multiple columns

>
	<table>
	  <tr>
		<th colspan="2">Snacks</th>
	  </tr>
	  <tr>
		<td>Score Bar</td>
		<td>Mountain Dew</td>
	  </tr>
	</table>

---

###Table Spanning

- Cells can be spanned across multiple rows

>
	<table>
	  <tr>
		<th rowspan="2">Snacks</th>
		<td>Score Bar</td>
	  </tr>
	  <tr>
		<td>Mountain Dew</td>
	  </tr>
	</table>

---

###Table Spanning [cont.]

>
	<table>
	  <tr>
		<th colspan="2">Snacks</th>
	  </tr>
	  <tr>
		<td>Score Bar</td>
		<td>Mountain Dew</td>
	  </tr>
	</table>

---

###Table Extras

- Simple way to wrap the header and footer of a table
- Table headers <thead>
- Table body <tbody>
- Table footers <tfoot>

---

###Table Extras [cont.]

>
	<table>
	  <thead>
		<tr><th>Name</th><th>Amount</th></tr>
	  </thead>
	  <tbody>
		<tr><td>Kamren</td><td>$55.00</td></tr>
		<tr><td>Bekah</td><td>$35.00</td></tr>
	  </tbody>
	  <tfoot>
		<tr><td>Total</td><td>$90.00</td></tr>
	  </tfoot>
	</table>

---

##Lab 6: Styling Tables

- **Goal: Gain familiarity with Tables**

- **Specifications:**
	- Create a table on animals using the images provided
	- What happens when words are mixed with an image?
	- What needs to happen to create the look to the right with the table as wide as the page?

---

##Forms Outline

- **Form Basics**
- **Form Attributes**
- **Input Types**

---

##Form Basics

---

###Info

- **Initially were going to be called Web Forms 2.0**
	- They were an initiative was started by Opera in 2005
- **HTML5 forms have pretty good support**
	- [http://caniuse.com/forms](http://caniuse.com/forms)
	- [http://www.wufoo.com/html5/](http://www.wufoo.com/html5/)
	- They gracefully degrade in browsers without support

---

##Form Attributes

---

###placeholder

- Allows information to be put inside form elements
	- Once a user clicks on the form element and begins to type the **placeholder** text goes away
	- Works even with JavaScript off because no JavaScript is needed
	- Without browser support it simply doesn’t show up
- In HTML4 we had a **value** attribute 
	- The value attribute does not go away when a user begins typing
	- It is a bit muddled
	
>

	<input type="text" id="favoriteColor"
	  placeholder="Favorite color”>
	  
---

###placeholder [cont.]

- **Browser Support / Comparison**

---

###autofocus

- **Autofocuses on the input field when the page is rendered**
	- Without support no autofocus is given
- **No more JavaScript needed for this**

>

	<input type="text" id="favoriteColor"
	  placeholder="Favorite color”
	  autofocus>
	
>

	<input type="text" id="favoriteColor"
	  placeholder="Favorite color”
	  autofocus=“autofocus”>
>

	<input type="text" id="favoriteColor"
	  placeholder="Favorite color”
	  autofocus=“”>

---

###autofocus


- **Browser Support / Comparison**

---

###autocomplete

- Allows browsers to autocomplete fields for quicker access
- Main usage is to set the **autocomplete** property so fields you don’t want autocompleted don’t (e.g. passwords and usernames)
	- By default it is set to true
- Can be used as a `<form>` attribute or an `<input>` attribute
	- Setting it at the nested `<input>` level will override the `<form>` level

---

###autocomplete [cont.]

- **Unsupported browsers simply will allow autocomplete
to take place**

>
	<form autocomplete="off">
	  <input type="text" id="favoriteColor"
	    placeholder="Favorite color"
	    autocomplete="off"> 
	</form>

---

###autocomplete [cont.]

- **Browser Support / Comparison**
	- Mobile Safari: Instead try turning off autocorrect and autocapitalize

---

###required

- **Reminds the user that the form element needs to be filled out before continuing**
	- Remember this is client-side validation
	- No need to write JavaScript to give users warning
- **CSS could be styled with the :required pseudoclass**
- **JavaScript can be used to customize the validation message via** `setCustomValidity()`
- **Should have a `name` attribute because otherwise it
isn’t going to be wrapped up to the backend**

---

###required [cont.]

- **Only performs validation on click of submit**
	- JavaScript validation could be placed onBlur() of each input field for better usability
- **Can be used on radio buttons**
	- Placing it on one will make whole group required
- **Can be used on individual check boxes**

>
	<form>
	  <input type="text" id=“favoriteColor” name=“favoriteColor 
	    placeholder="Favorite color" required />
	  <input type="submit" /> 
	</form>

---

###required [cont.]

- **Browser Support / Comparison**

---

###pattern

- **Allows you to specify your own requirements for validation via a regular expression**
	- Useful for customer numbers, product codes …
	- A good place to find patterns: [http://html5pattern.com/](http://html5pattern.com/)

>
	<form>
 	  <input type="text" id=“zipcode” name=“zipcode
	    placeholder="Zipcode" pattern=“\d{5}” />
	  <input type="submit" />
	</form>

---

###list & `<datalist>`

- **Allows you to populate a drop down menu with a
corresponding list of data**
	- Needs to be used with the `<datalist>` element
	- If completely supported it will work like an autocomplete search

>
	<form>
	  <datalist id="colors"> 
	    <option value="Red">Red</option> 
	    <option value="Yellow">Yellow</option>
		<option value="Blue">Blue</option>
	  </datalist>
	  Add a color if you'd like to:
	  <input type="text" name="color"
	    placeholder="Favorite color" list="colors">
	</form>

---

###list [cont.]

- **Browser Support / Comparison**

---

###list [cont.]

- **Better browser support is to embed a `<select>`
within the `<datalist>`**
	- Jeremy Keith: [http://adactio.com/journal/4272/](http://adactio.com/journal/4272/)

>
	<form>
	  <datalist id="colors">
	    <select name="colors"> 
	      <option value="Red">Red</option>
		  <option value="Yellow">Yellow</option>
	      <option value="Blue">Blue</option>
	    </select>
	  </datalist>
	  Add a color if you'd like to:
	  <input type="text" name="color"
	    placeholder="Favorite color" list="colors">
	</form>

---

###list [cont.]

- **Browser Support / Comparison**

---

###formaction

- Allows you to be able to direct a forms submission to a different location than set in the **action** attribute of the `<form>`
- Used on submit or image input types
- Browser first looks to **formaction** attribute. If none it looks to the form’s **action** attribute

>
	<form action=“/sales“>
	  <input type=submit value=“Send to Sales”>
	  <input type=submit value=“Send to Marketing”
	    formaction=“/marketing">
	</form>

---

###formaction [cont.]

- **Browser Support / Comparison**

---

###formmethod

- Allows you to be able to choose the appropriate HTTP method for submission (e.g. GET, POST, PUT, DELETE)
- Used on submit or image input types
- Browser first looks to **formmethod** attribute. If none it looks to the form’s **method** attribute

>
	<form action=“/marketing“>
	  <input type=submit value=“Send with get”>
	  <input type=submit value=“Send with post”
		formmethod=“POST">
	</form>

---

###formmethod [cont.]

- **Browser Support / Comparison**

---

###formtarget

- Allows you to be able to override the form’s target
- Used on submit or image input types
- Browser first looks to **formtarget** attribute. If none it looks to the form’s **target** attribute

>
	<form action="/marketing" method="GET">
	  <input type="submit" value="Send">
	  <input type="submit" value=“Send in new page"
	    formtarget="_blank">
	</form>

---

###formtarget [cont.]

- **Browser Support / Comparison**

---

###tel

- **Allows you to specify a text input field will be functioning as a web address (i.e. as a URL)**
	- Browser rendering make it look like a regular text field
- **No browser validation built in for this**

HTML4

	<input type="text" name="tel">
	<input type="submit" value="go">

HTML5

	<input type="tel" name="tel">
	<input type="submit" value="go">

---

###tel [cont.]

- **Browser Support / Comparison**

---

##Lab 1

- Add a form to the **give** page for people to give a certain amount of money to your charity
	- Get their phone number it is required
	- Get their address information
	- Make sure you prevent the default action of clicking the form submission input

---

##Input Types

---

###search

- Allows you to specify a text input field will be functioning as a search
	- Initial browser rendering make it look like a regular text field until you start typing and an **x** shows up to clear the input
- Combine with a `<datalist>` to help your users know what to search for
- Browsers without support simply fall back to a regular text input

HTML4

	<input type="text" name="search">
	<input type="submit" value="go">

HTML5

	<input type="search" name="search">
	<input type="submit" value="go">

---

###search [cont.]

- **Browser Support / Comparison**

---

###email

- **Allows you to specify a text input field will be functioning as a search**
	- Browser rendering make it look like a regular text field 
- `pattern` attribute is **not needed** to have a simple email validation looking for @ and .

HTML4

	<input type="text" name="email">
	<input type="submit" value="go">

HTML5

	<input type="email" name="email">
	<input type="submit" value="go">

---

###email [cont.]

- **Browser Support / Comparison**

---

###email [cont.]

- **Validation**

---

###url

- **Allows you to specify a text input field will be functioning as a web address (i.e. as a URL)**
	- Browser rendering make it look like a regular text field
- `pattern` attribute is **not needed** to have a simple url validation looking for http: or an https:

HTML4

	<input type="text" name="url">
	<input type="submit" value="go">

HMTL5

	<input type="url" name="url">
	<input type="submit" value="go">

---

###url [cont.]

- **Browser Support / Comparison**

---

###url [cont.]

- **Validation**

---

###novalidate attribute

- **Adding this attribute will force the form to not use
the built in field validation**

>
	<form novalidate>
	  <input type="url" name="url">
	  <input type="submit" value="go">
	</form>

---

###formnovalidate

- **Adding this attribute will force the form to not use
the built in field validation**
	- Makes the form function the same as the **novalidate** on the `<form>`

>
	<form>
	  <input type="url" name="url">
	  <input type="submit" value=“go" formnovalidate>
	</form>

---

###number

- **Allows you to specify a text input field will be
functioning as a web address (i.e. as a number)**
	- Browser rendering make it look like a regular text field
- **No browser validation built in for this**
	- Except for Chrome / IE 10+

HTML4

	<input type="text" name="number">
	<input type="submit" value="go">

HTML5

	<input type="number" name="number">
	<input type="submit" value="go">

---

###number [cont.]

- **Browser Support / Comparison**

---

###number [cont.]

- **Validation**

---

###number Attributes

- **Max attribute**
	- Allows the up arrows to move to the defined max (e.g. 5)

>
	<input type="number" name=“number" max="5">
	<input type="submit" value="go">

- **Min attribute**
	- Allows the up arrows to start at the defined min and not go below it (e.g. 5)

>
	<input type="number" name=“number" min="5">
	<input type="submit" value="go">

---

###number Attributes [cont.]

- **Step attribute**
	- Allows the use of the up and down arrow to move in defined increments (e.g. 5)

>
	<input type="number" name=“number" step="5">
	<input type="submit" value="go">

- **Combination**
	- Allows the use of the up and down arrow to move in defined increments
	- The input will have a min value of 2, increment by 2, and have a max value of 10

>
	<input type="number" name=“number"
	  min=“2” max=“10” step=“2">
	<input type="submit" value="go">

---

##Lab 2

- Add the form submission to the **sales** page.
	- Make sure you can grab what you would need for a sale
	- Allow the form to submit the total sales at any point
	- Reset the individual sales numbers after submitted
		- At this point your submit shouldn’t take you anywhere
	- Make sure you prevent the default action of clicking the form submission input
- Update **give** page form
	- Add a zip code to the **give** page
	- You need to validate the full 9 digit zip code pattern 48

---

###range

- Similar to the **number** input type
	- Has the **max** and **min** attributes
	- Has a **value** attribute to set an initial range setting

>
	<form>
	  <input type="range" name="range"
	    min="1" max="100" value="20">
	  <input type="submit" value="go">
	</form>

---

###range [cont.]

- **Browser Support / Comparison**

---

###date

- **Allows you to implement a date picker that is built
into the browser without having to load a component library**
	- Browser rendering make it look like a regular text field
>
	<form>
	  <input type="date" name="date">
	  <input type="submit" value="go">
	</form>

---

###date [cont.]

- **Browser Support / Comparison**

---

###date [cont.]

- **Browser Support / Comparison**

---

###month

- **Allows you to implement a month picker that is built into the browser without having to load a component library**
	- Browser rendering make it look like a regular text field

>
	<form>
	  <input type="month" name="month">
	  <input type="submit" value="go">
	</form>

---

###month [cont.]

- **Browser Support / Comparison**

---

###week

- **Allows you to implement a week picker that is built
into the browser without having to load a component library**
	- Browser rendering make it look like a regular text field

>
	<form>
	  <input type="week" name="week">
	  <input type="submit" value="go">
	</form>

---

###week [cont.]

- **Browser Support / Comparison**

---

###time

- **Allows you to implement a week picker that is built
into the browser without having to load a component library**
	- Browser rendering make it look like a regular text field

>
	<form>
	  <input type="time" name="time">
	  <input type="submit" value="go">
	</form>

---

###time [cont.]

- **Browser Support / Comparison**

---

###Dates & Times Validation [cont.]

- **Validation**

---

###date Closing Thought

- **Use dates when you want a calendar**
- **Don’t use dates when you need to quickly type a date (i.e. type someone’s birthday)**
	- Way to slow to make a user choose a birthday when they can type it quickly

---

###color

- **Allows you to implement a color picker that is built
into the browser without having to load a component library**
	- Browser rendering make it look like a regular text field

>
	<form>
	  <input type="color" name="color">
	  <input type="submit" value="go">
	</form>

---

###color [cont.]

- **Browser Support / Comparison**

---

###color [cont.]

- **Browser Support / Comparison**

---

##Lab 3

- **Create a page about the supplies we have on reserve**
	- Create a list of lemonade supplies on hand
	- Create a list of snacks on hand
- **Add a form that shows how we are doing with supply inventory and allows us to make adjustments to it**
	- Use the range input
- **Add an input to save the date of the update**
	- Have the calendar default to today
	- After submission have it reset to today’s date
























