footer: © NodeProgram.com, Node.University and Azat Mardan 2018
slidenumbers: true
theme: Simple, 1
build-lists: true

[.slidenumbers: false] 
[.hide-footer]

![fit](images/node-testing-cover-2x 16by9.png)

---

# HTML and HTML5
## Introduction to HTML5

![inline 100%](images/azat.jpeg)
Azat Mardan @azat_co

![inline right](images/nu.png)

---

## Outline

- **Web Development Basics**
- **What is HTML5?**
- **Content Basics**
- **Sectioning & Heading Content**
- **Phrasing Content**
- **Microformats**

---

## Web Development Basics

---

### Web Development Basics

- **Build applications that are useful, usable and easy
to maintain**

---

### Separation of Concerns

- **Design our applications using distinct sections in mind**
	- Sections that will control the organization and structure
	- Sections that will control the presentation
	- Sections that will control the logic and behavior
- **Separate Documents**
	- Easier to maintain
	- Smaller document size

---

### HTML

- **Hypertext Markup Language**
- **Section that will control the organization**
	- Tags for content
	- Semantic layout
- **When building an application**
	- Start with thinking through your content
	- Then begin building the structure

---

### CSS

- **Cascading Style Sheets**
- **Sections that will control the presentation**
	- Brings style to the content
	- Describes the HTML elements
- **When building an application layer on the presentation**
- **Place your external CSS within the head element of your document**

---

### JavaScript

- **Sections that will control the application logic and behavior**
	- Can handle page routing
	- Handle user interaction
	- Form submission
- **When building an application, layer on the behavior and control**
- **Place your external JS within the body element of your document, directly above the closing body element**

---

##Lab 1
****

- **Create a web page that we are going to use for the
class in HTML 4**
	- Create a welcome page to a lemonade stand
	- No doctype, just standard HTML 4 markup.
	- Tags: head, body, table, br, hr, a, img, div, span, etc

---

##What is HTML5?

---

### HTML5 Background

- **Overseen by the W3C**
	- Founded in 1994 by Tim Berners-Lee, inventor of the Web
- **HTML4 > XHMTL**
	- People thought XHTML was where the web was going
	- It became a broken specification forcing strict syntax over flexibility
- **HTML4**
	- HTML4 was a W3C recommendation in 1999****
	- Just stuck on **web pages** and **plugins**…

---

### HTML5 Background [cont.]


- **HTML5**
	- W3C (World Wide Web Consortium) and WHATWG (Web Hypertext Application Technology Group)
	- Both groups have been working together to create the move towards **web applications** and **native simplification**
	- A superset of HTML 4.01: It is backwards compatible

---

### Doctype


- **Tells the browser what type of document is going to be rendered**
- **Allows the browser to better render and interpret the content**
- **Not needed**
	- The browser is going to render html fine
	- **However** it makes browsers work in standards mode

---

### HTML4 Doctype

- **!DOCTYPE html**: The document type is html
- **PUBLIC**: This standard is publicly available
- **“-//W3C … ”**: Using HTML version 4.01 and that it is in English
- **“http://…”**: Points to a file that identifies the standard
- Observations:
	- Verbose
	- Not forward thinking

>
	<!DOCTYPE html PUBLIC “-//W3c//DTD HTML 4.01//EN”
	“[http://www.w3.org/TR/html4/strict.dtd](http://www.w3.org/TR/html4/strict.dtd)”>```

---

### HTML5 Doctype

- **!doctype html**: The document type is html
- Observations:
	- That was simple
	- Will work for every future version of HTML


```<!DOCTYPE html>```

### Meta Tag

- **Provides structured metadata about the html document**
- **Defines what the content will be**
- **Defines what kind of character set should be used**
	- **UTF-8** supports lots of alphabets not just western alphabets

HTML4

    <meta http-equiv=“content-type” content=“text/html; charset=UTF-8”>

HTML5

    <meta charset=“utf-8”>

---

### CSS Link

- [HTML](#html)
  - [Introduction to HTML5](#introduction-to-html5)

HTML4

    <link type=“text/css” rel=“stylesheet” href=“app.css”>

HTML5

    <link rel=“stylesheet href=“app.css”>
	
---

### JavaScript Link

- **HTML links to external JS via a script element**
- **No more type attribute because JS has become the standard/default scripting language**
	- Backwards compatible: Browsers have always assumed this standard.

HTML4

    <script type=“text/javascript” src=“app.js”></script>
    <script type=“text/javascript”>var color = ‘blue’;</script>

HTML5

    <script src=“app.js”></script>
    <script>var color = ‘blue’;</script>

---

### Welcome to the Family

**- HTML5 is a conglomeration of web technologies**

**- Think of it like this (don’t get too bent out of shape):**

**Markup + JavaScript APIs + CSS = HTML5**

- Semantic markup
- 	Multimedia without plugins
- 	Rich Internet clients: canvas, transforms, JavaScript interfaces
- 	More efficient applications: client-side storage, offline applications, web workers
- 	Advanced CSS: selectors, animations, shadows

---

### Bad In-laws Not Here

- **Browsers don’t support HTML5**
	- [http://caniuse.com/](http://caniuse.com/)
	- [http://html5please.com/](http://html5please.com/)
- **IE isn’t going to work**
	- IE9 and above work pretty well
- **HTML5 isn’t going to be done until 2022**
	- Well … it might not be finalized, but what we have should be there
- **I need to relearn everything!**
	- Nope, this is an evolution not a revolution
	- [http://html5doctor.com/](http://html5doctor.com/)

---

##Content Basics

---

### The Minimalist

- **HTML5 style comes in a couple of flavors**

Loose syntax

    <!DOCTYPE html>
      <meta charset=UTF-8>
      <title>Minimalist</title>
      <p>I don’t like to talk

Strict syntax

    <!DOCTYPE html>
    <html lang=“en”>
      <head>
        <meta charset=“UTF-8” />
        <title>Full Tilt</title>
      </head>
      <body>
        <p>Yeah, I’m gonna talk your ear off!</p>
      </body>
    </html>

---

### Why Validate?

- Validation can offer insight into errors
- Useful to see how the markup should function
- WHATWG has a list of validators
	- [http://validator.whatwg.org/](http://validator.whatwg.org/)

---

### Validation

- **Validation can offer insight into errors**

Loose syntax

    <!DOCTYPE html>
      <meta charset=UTF-8>
      <title>Minimalist</title>
      <p>I don’t like to talk

[http://html5.validator.nu/](http://html5.validator.nu/)

The document is valid HTML5 + ARIA + SVG 1.1 + MathML 2.0 (subject to the utter previewness of this service). 

**SOURCE**



---

##Validation

- **Validation can offer insight into errors**

Strict syntax

    <!DOCTYPE html>
    <html lang=“en”>
      <head>
        <meta charset=“UTF-8” />
        <title>Full Tilt</title>
      </head>
      <body>
        <p>Yeah, I’m gonna talk your ear off!</p>
      </body>
    </html>
    

[http://html5.validator.nu/](http://html5.validator.nu/)

The document is a valid HTML + ARIA + SVG 1.1 + MathML 2.0 (subject to the utter previewness of this service.

---

##Lab 2 - Convert to HTML5

- **Modify the header information of your HTML 4 document**
- **Validate it**

---

##Sectioning & Heading Content

---

### Semantic Markup

- **You don’t need to describe your elements with classes and divs**
- **Use elements with meaning**
- **What are the most common names for class attributes**
	- [https://developers.google.com/webmasters/state-of-the-web/2005/classes?csw=1](https://developers.google.com/webmasters/state-of-the-web/2005/classes?csw=1)
	- Maybe they should become HTML tags

---

### Semantic Elements

- Our building blocks should have meaning
- `<div>` and `<span>` don’t have much meaning
	- We can still use them, but not so heavily
	- We can do better
- **More meaningful elements means less classes and ids are needed to provide meaning to elements.**

---

### Sectioning Element

- `<section>` is a generic document or application
 section
- Usually used in conjunction with a heading and sometimes a footer
- Semantically it is a grouping of logically related content
- Example:
	- Sections of a long article

---

### Article Element

- `<article>` is an independent section of the document
- A specialized section
- They should be able to stand alone without the rest of the page
- They should have a heading and could have a footing
- Examples:
	- Journal entry
	- Blog
	
---

### Div Element

- `<div>` is a generic container that handles flow control
- Has no additional semantic meaning
- The content doesn't have to have any relationship
- Not used for sectioning
- It is an element of last resort

---

### Heading

- `<header>` semantically used for introduction and navigation
- Used anywhere a heading is needed (e.g. `<section>`, `<article>`, `<body>`)
- Can contain other elements (e.g. `<h1>`, `<p>`, `<nav>`)
- Can’t contain another `<header>` or a `<footer>`

---

### Footer

- `<footer`> semantically used for additional information about the content
- Usually appears at the end of the content
- Can contain other elements (e.g. `<h1>`, `<p>`, `<nav>`)
- Can’t contain another `<header>` or a `<footer>`

---

### Document Outlining

- **Headers and sections give the outline of the document structure**
- **Simply put this is still theoretical**
	- No user agents support this yet
	- Something to know about, but not sure how/if it will mature
- **Want to play with it?**
	- [http://gsnedders.html5.org/outliner/](http://gsnedders.html5.org/outliner/)

---

### Document Outlining [cont.]

- Gives an outline based on headings
- Section based

HTML

	<h1>Let’s Begin</h1>
	<section>
	  <h1>Walking</h1>
	  <p>Slowly move</p>
	  <section>
	    <h1>Trail Shoes</h1>
	    <p>Very supportive</p>
	  </section>
	</section>
	<section>
	  <h1>Biking</h1>
	  <p>Not so slow</p>
	</section>

Outline

	1. Let’s Begin
		1. Walking
			1. Trail Shoes
		2. Biking

---

### Document Outlining [cont.]

- Gives an outline based on headings
- Without sections
- Developer’s choice for implementation

HTML

	<h1>Let’s Begin</h1>
	<h2>Walking</h2>
	<p>Slowly move</p>
	<h3>Trail Shoes</h3>
	<p>Very supportive</p>
	<h2>Biking</h2>
	<p>Not so slow</p>

Outline

	1. Let’s Begin
		1. Walking
			1. Trail Shoes
		2. Biking

---

### More Sectioning Elements

- `<nav>` Semantic navigation element
- Groups links together for major navigation
- Doesn’t have to be a list
- Examples:
	- Bread crumbs, table of contents, header navigation

HTML4

	<ul class=“nav”>
	  <li>Cars</li>
	  <li>Boats</li>
	  <li>Planes</li>
	</ul>

HTML5

	<nav>
	  <ul>
	    <li>Cars</li>
	    <li>Boats</li>
	    <li>Planes</li>
	  </ul>
	</nav>

---

### More Sectioning Elements [cont.]

- `<aside>`
	- Used for content directly related to its structural element it is within (i.e. an aside within an article)
	- Used for secondary content when not nested inside of an `<article>`
- **Could be used as a sidebar, but style shouldn’t force the use of the element**

---

### More Structural Elements



-  `<figure>` & `<figcaption>` semantically allows images/charts to have a caption associated with them.

>
	<figure>
	  <img src=“comic.jpg”>
	  <figcaption>What if?</figcaption>
	</figure>


What if? 

**![](http://x.annihil.us/u/prod/marvel/i/mg/6/70/53582ba8e24b7/detail.jpg)**


[http://x.annihil.us/u/prod/marvel/i/mg/6/70/53582ba8e24b7/detail.jpg](http://x.annihil.us/u/prod/marvel/i/mg/6/70/53582ba8e24b7/detail.jpg)

---
### More Structural Elements [cont.]

	<figure>
	  <img src=“comic1.jpg”>
	  <img src=“comic2.jpg”>
	  <figcaption>
	    Let’s do this
	  </figcaption>
	</figure>

Let’s do this!!

![](http://i.annihil.us/u/prod/marvel/i/mg/3/a0/53592e58262ad/detail.jpg)
![](http://x.annihil.us/u/prod/marvel/i/mg/6/80/5356ca195c4d6/detail.jpg)

[http://i.annihil.us/u/prod/marvel/i/mg/3/a0/53592e58262ad/detail.jpg](http://i.annihil.us/u/prod/marvel/i/mg/3/a0/53592e58262ad/detail.jpg)
[http://x.annihil.us/u/prod/marvel/i/mg/6/80/5356ca195c4d6/detail.jpg](http://x.annihil.us/u/prod/marvel/i/mg/6/80/5356ca195c4d6/detail.jpg)

---
##Lab 3

- Change the welcome page over to html5
	- Add a `<figcaption>` and `<figure>` tag
	- Add a footer to take us through the navigation
- Add a **give** page that explains where your proceeds will go
	- Pick your charity of choice to highlight
	- Make sure to give some information about Alex's lemonade stand in an `<aside>`
	- Make sure to add some pictures and links to their pages
	- Use strong, em, and mark tags
- Add a **sales** page for people to buy lemonade and snacks
	- Think about how you are going to want your users to enter their purchases

---

##Phrasing Content

---

### Phrasing Content

- **Elements and text that make up phrases within a paragraph (i.e. a group of phrases makes up a paragraph)**

---

### Confusion


- HTML4 used `<i>` and `<b>` for font styling
- Now they have semantic meaning (i.e. they aren’t just presentational)
- `<i>` now for text in an alternate voice (e.g. technical terms, foreign words, taxonomy)

>
	<p>The <i class=“taxonomy”>Tyrannosaurus rex</i> was
	a huge.<p>

- `<b>` now for stylistically offset text without raising importance (i.e. keywords in a sentence, product names)
>
	<p>I love <b>olives</b> with feta cheese.</b><p>


---

### Confusion [cont.]

- **The new semantic meaning allows the `<i>` and `<b>` to be styled differently than italics and bold**
	- Adding a class allows you to identify its use
>
	<p><b class=“lead”>A breaking story.</b><p>


- Should be used as a last resort when h1 to h6 elements aren’t appropriate

---
### Confusion [cont.]

- Don’t forget we still have `<em>` and `<strong>` 
- `<em>` to stress emphasis (i.e. something that could be pronounced differently based on emphasis)
- `<strong>` strong importance (i.e. text with semantic importance or urgency)

---
### Confusion [cont.]

- `<small>`
- Used to be used for small text when it was presentation based
- Semantically it is to be used for side comments (i.e. the inline equivalent of an `<aside>`)
- Doesn’t affect the semantics of `<strong>` or `<em>`
- Example:
	- Inline legal jargon, copyright, disclaimers

---

### Confusion [cont.]

- `<hr>`
- Used to be a horizontal rule
- Semantically it means a section break (i.e. `</section><section>`)
- Browsers style it with a horizontal line, however, with CSS you could replace that with a more stylistic separation
- Anywhere a `<p>` element can go an `<hr>` element can go

---

### Confusion [cont.]

- `<s>`
- Used to be a strikethrough
- Semantically it means the content is no longer useful or is out of date
- The style is simply being unhinged from its semantic meaning
	- However, browsers are still rendering it with a strikethrough

---

### Block-level links

- `<a>`
- In the past links have only been able to surround inline information … mainly text
- We have wanted to simplify the process of creating large clickable objects
- HTML5 allows for wrapping flow control content with an `<a>`
	- We can wrap div, section, article, p, li … basically any element
	- As long as there is no extra interactivity in that flow control content	
	
>
	<a href="/"><img src="spider.jpg"></a>


---
### Semantic Lists

- `<ol>`
- **Ordered lists have been given a semantic update**
- **type attributes are again allowed:**
	- **type = “1”** decimal ordering this is the default
	- **type = “a”** lower-case alpha ordering
	- **type = “A”** upper-case alpha ordering
	- **type = “i”** lower-case roman numeral ordering
	- **type = “I”** upper-case roman numeral ordering
 
> 	<ol type=“I”>
> 	    <li>A</li>
> 		<li>B</li>
> 		<li>C</li>
> 	</ol>


---
### Semantic Lists [cont.]

- `<ol>`
- reversed property
- Allows the list to have the ordering backwards
- IE11 still doesn’t support this
	- We can use a polyfill for this: we will look at later
>
	<ol reversed>
		<li>A</li>
		<li>B</li>
		<li>C</li>
	</ol>

---
##Semantic Lists [cont.]
- `<ol>`
- start property
- Allows you to break lists up and keep the ordering

>     <h1>What happened</h1>
>     <ol>
>       <li>A</li>
>       <li>B</li>
>       <li>C</li>
>     </ol>
>     <p>Then we went fishing. It was awesome</p>
>     <ol start=“4”>
>       <li>D</li>
>       <li>E</li>
>     </ol>

---

### Semantic Lists [cont.]

- `<li>`
- value property: similar to the `<ol>` start property
- Allows you to break lists up and keep the ordering

>     <h1>What happened</h1>
>     <ol>
>       <li>A</li>
>       <li>B</li>
>       <li>C</li>
>     </ol>
>     <p>Then we went fishing. It was awesome</p>
>     <ol>
>       <li value=“4”>D</li>
>       <li>E</li>
>     </ol>

---
### Semantic Lists [cont.]

- Final thoughts
- Only use your **type** when it is semantic
	- You still have the CSS property list-style-type for extra options
- With the **start** property first think if your lists could simply be combined
- The **value** property shouldn’t be needed. Use it as a last resort

---
### `<cite>`


- Used to give props to a creative reference
	- Books, videos, blogs, tweets …
- Must include a **title**, an **author** or **URL**

>       <p>My favorite hero is Captain America in the
>       <cite>Marvel’s: The Avengers</cite> movie.</p>

         
---

### ```<mark>```

- Used to highlight or bring attention to text
	- It doesn’t change the texts importance (e.g. `<strong>`)or emphasis (e.g. `<em>`)
- Useful for marking up search terms

>       <p><strong>Captain America is awesome!</strong> He
>       is definitely sweeter than <em>Hawkeye</em>. Even
>       if <mark>Hawkeye has a better outfit.</mark></p>

---

##Microdata

---

### `<time>`

- A semantic way to display the time, date or
- Contains an optional **datetime** property
	- If not used the ```<time>``` must be a valid date
>	
	<time>1970-1-1</time>

- Some valid dates:
	- 1970-1-1 a valid year, month, day
	- 1970-1 a valid year, month
	- 1-1 a valid year-less string
	- 12:24 a valid time (i.e. a time based on a 24hour clock)
	- 12:24:32 a valid time
	- 4h 31m 22s a valid duration

       
---

### ```<time>``` [cont.]

- A **datetime** property can be used to describe the date given
- Gives a standard microformat way to consume the data for browsers, search engines …
	- [http://microformats.org/wiki/Main_Page](http://microformats.org/wiki/Main_Page)


>       <time datetime=“1970-1-1”>January 1st</time>
       
---

### `<data>`

- A generic element to hold data and give some relational information about the data
- Needs to be combined with a value property
- Useful for scripts to consume human readable text

    <p>I like to take <data value=“16km”>10 mile</data> bike
rides.</p>

>
       <p>I like to take <data value=“16km”>10 mile</data> bike 
	   rides.</p>

---

### data-* attribute

- A personal favorite: Sometimes you just need to store a bit of data in an element for JavaScript
- This data isn’t seen by your user unless they view the source
- It is easily consumed by JavaScript and doesn’t affect the layout or presentation

>
    <em data-user-code=“50352A”>Brian</em>

---

### rel attribute

**Used to add a relationship on an `<a>`, `<link>` or `<area>`**

- We are all familiar with this in our link to external CSS

>
	<link rel=“stylesheet href=“app.css”>


- In links rel is used to specify external links

>
	<a href=“http://www.yahoo.com”
	  rel=“external”>Yahoo!</a>

- **rel** can also be used to give the author of the link 65

>
	<a href="http://twitter.com/devintelligence"
	rel="me">@DevIntelligence</a>


---

##Lab 4

- **Let's put the time and date in the header**
	- Make sure it validates and is readable
	- Feel free to use a JS library if you would like
