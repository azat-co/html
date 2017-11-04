footer: © NodeProgram.com, Node.University and Azat Mardan 2018
slidenumbers: true
theme: Simple, 1
build-lists: true

[.slidenumbers: false] 
[.hide-footer]

![fit](images/node-testing-cover-2x 16by9.png)

---

# HTML 
## Introduction to CSS

---

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
