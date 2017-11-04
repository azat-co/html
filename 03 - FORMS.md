footer: © NodeProgram.com, Node.University and Azat Mardan 2018
slidenumbers: true
theme: Simple, 1
build-lists: true

[.slidenumbers: false] 
[.hide-footer]

![fit](images/node-testing-cover-2x 16by9.png)

---

# HTML 
## Introduction to Forms

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















