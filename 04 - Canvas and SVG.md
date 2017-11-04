footer: © NodeProgram.com, Node.University and Azat Mardan 2018
slidenumbers: true
theme: Simple, 1
build-lists: true

[.slidenumbers: false] 
[.hide-footer]

![fit](images/node-testing-cover-2x 16by9.png)

---

# HTML 
## Canvas Outline

- **Canvas Basics**
- **Drawing Operations**
- **Adding Gradients**
- **Shadowing**
- **Writing Text**
- **Canvas Examples**

---

##Canvas Basics

---

###What?

- Canvas saw its beginnings with Apple and its Dashboard widgets
	- The WebKit browsers gave it the start
- On the fly create dynamic images
- Use for games and animations
- Pixel based (i.e. raster based)
- Requires JavaScript to perform drawing

---

###What? [cont.]

- **Pixels give us**
	- Quick rendering =)
	- Poor scaling =(
	- Changes/screen refreshes require whole canvas to be redrawn
		- It is immediate mode bitmapped
- **Our job is to get the screen ready before each frame**

---

###Simple Canvas

- Evidence that canvas exists
- If you get the message “Your browser does not…” in your browser it is time to upgrade from IE8

CSS

	canvas { border: 1px solid black; }

HTML

	<canvas id="aCanvas" width="200" height="100">
	  Your browser does not support HTML5 Canvas.
	</canvas>

---

###Size

- **Canvas default is 300px wide by 150px tall**
	- It is good to specify the height and width
- **The height and width need to be specified in the `<canvas>`**
	- If style with CSS the Canvas @ 300px by 150px will scale to the size defined in the CSS
	- Causes pixelation if it is scaled up (i.e. CSS defined as 600px by 300px)
- **Oh yeah … you can put more than one canvas on a page**

---

###Drawing

- **Context is used for drawing on the canvas**
	- Canvas has no content on its own
	- It has no border
	- It is transparent
	- We use the drawing context to create
- **How do we get that context?**
	- JavaScript

---

###Drawing [cont.]

- Let’s get that canvas context
- 2D context let’s us draw two dimensionally

CSS

	canvas { border: 1px solid black; }

HTML5

	<canvas id="aCanvas" width="200" height="100">
	  Your browser does not support HTML5 Canvas.
	</canvas>

JS

	var canvas = document.getElementById("aCanvas");
	var context = canvas.getContext("2d");

---

###Fill Rectangle

- **Let’s draw on it**
	- Use the **fillRect** method to draw a rectangle and fill it
	- The color defaults to black
- **fillRect(x, y, width, height)**
	- If width or height are zero then there is no drawing

JS

	var canvas = document.getElementById("aCanvas");
	var context = canvas.getContext("2d");
	context.fillRect(2, 5, 75, 75);

---

###Fill Style

- With the **fillStyle** method we can modify that color
	- It represents the color or style inside the shape
	- Should accompany fillRect so the color isn’t simply black

JS

	var canvas = document.getElementById("aCanvas");
	var context = canvas.getContext(“2d");
	context.fillStyle="rgba(100,110,205,0.6)";
	context.fillRect(2, 5, 75, 75);

---

###Fill Style [cont.]

- **fillStyle(value)**
	- value could also be a CSS color like orange (i.e. **context.fillstyle=“orange”**)
	- value could be a hex lik #00FFFF or #0FF (i.e. **context.fillstyle=“#0FF”**)
	- value could be using Hue Saturation Lightness (i.e. **context.fillstyle=“hsl(90, 50%, 50%)”**)
	- Also gradients, patterns, images

JS

	var canvas = document.getElementById("aCanvas");
	var context = canvas.getContext(“2d");
	context.fillStyle="rgba(100,110,205,0.6)";
	context.fillRect(2, 5, 75, 75);

---

###Stroke Rectangle

- **Let’s draw on it**
	- Use the **strokeRect** method to draw a rectangle outline
	- The color defaults to black
- **strokeRect(x, y, width, height)**
	- If width or height are zero then there is no drawing

JS

	var canvas = document.getElementById("aCanvas");
	var context = canvas.getContext("2d");
	context.strokeRect(2, 5, 75, 75);

---

###Stoke Style

- With the **strokeStyle** method we can modify that color
	- It represents the color or style outlining the shape
	- Should accompany strokeRect so the color isn’t simply black

JS


	var canvas = document.getElementById("aCanvas");
	var context = canvas.getContext(“2d");
	context.strokeStyle="rgba(100,110,205,0.6)";
	context.strokeRect(2, 5, 75, 75);

---

###Clear Rectangle

- **Maybe we should clear it**
	- Use the **clearRect** method to clear a rectangle and puts the canvas back to transparent
	- Faster than **fillRect**
	- Clears out all the properties that that have been set
- **clearRect(x, y, width, height)**

JS

	var canvas = document.getElementById("aCanvas");
	var context = canvas.getContext("2d");
	context.clearRect(0, 0, 200, 100);

---

##Drawing Operations

---

###Drawing Operations

- The coordinate space is 0,0 at the top-left corner
- The Coordinate system is floating point
- Some operations include the word “stroke”, these draw immediately, others need a beginPath() and stroke() operation surrounding them

---

###Paths

- Paths are generalized shapes, and can be created either open or closed
- Paths are shapes that can be drawn (i.e. stroked) or filled

---

###Triangle

- There is no **fillTriangle** method
- First we will need to create a path
	- A path is like tracing the outline of our shape
	- It will actually not show anything to a user

JS

	var canvas = document.getElementById("aCanvas");
	var context = canvas.getContext("2d");
	context.beginPath();
	context.moveTo(100, 150);
	context.lineTo(250, 75);
	context.lineTo(125, 30);
	context.closePath();

---

###Triangle Outline

- There is no **strokeTriangle** method
- So we will need to **stroke** the triangle after drawing the path

JS

	var canvas = document.getElementById("aCanvas");
	var context = canvas.getContext("2d");
	context.beginPath();
	context.moveTo(100, 150);
	context.lineTo(250, 75);
	context.lineTo(125, 30);
	context.closePath();
	context.stroke();

---

###Triangle Filling

- There is no **fillTriangle** method
- So we will need to **fill** the triangle after drawing the path

JS

	var canvas = document.getElementById("aCanvas");
	var context = canvas.getContext("2d");
	context.beginPath();
	context.moveTo(100, 150);
	context.lineTo(250, 75);
	context.lineTo(125, 30);
	context.closePath();
	context.fill();

---

###Line Styles

- **Line Width: controls line width**
	- Default is 1.0
- **Line Cap: controls the ends of line**
	- “butt”, “round”, “square”
- **Line Join: controls joins in lines**
	- “miter”—creates “pointy” corners
	- “round”—creates “rounded” corners
	- “bevel”—creates “chopped-off” corners

>
	context.lineWidth = 10;
	context.lineJoin = “round”;

---

###Circle

- There is no **fillCircle** method

JS

	var canvas = document.getElementById("aCanvas");
	var context = canvas.getContext("2d");
	context.beginPath();
	context.arc(150, 150, 50, 0, 2 * Math.PI, true);
	context.closePath();
	context.fill();

--- 

###Circle [cont.]

- **context.arc method**
	- x, y: is the center point of the circle
	- radius: is half the width of the circle

JS

	context.arc(x, y, radius, startAngle, endAngle, direction)

---

###Circle [cont.]

- **context.arc method**
	- startAngle: Angle between the x axis and starting point of arc
	- endAngel: Angel between the x axis and the stopping point of arc

JS

	context.arc(x, y, radius, startAngle, endAngle, direction)

---

###Radians

- **The canvas thinks in terms of radians not degrees**
	- 360o is equal to 2 * PI radians
	- 1 radian is equal to 180 / PI
	- radians = degrees * Math.PI / 180

JS

	var radians = 270 * Math.PI / 180;

---

###Circle [cont.]

- **context.arc method**
	- direction: The direction we will be tracing the arc
		- **true**: counterclockwise
		- **false**: clockwise

JS

	context.arc(x, y, radius, startAngle, endAngle, direction)

---

###Circle [cont.]

- **Putting it all together for our partial circle**
	- Wait is this what we wanted?

JS

	var canvas = document.getElementById("aCanvas");
	var context = canvas.getContext("2d");
	context.beginPath();
	var radians = 270 * (Math.PI / 180);
	context.arc(150, 150, 50, 0, radians, true);
	context.closePath();
	context.stroke();

---

###Circle [cont.]

- **Changing order of closePath**
- **Allows us to have an unfinished path**
	- If we don’t close the path before we stroke then we get an open circle

JS

	var canvas = document.getElementById("aCanvas");
	var context = canvas.getContext("2d");
	context.beginPath();
	var radians = 270 * (Math.PI / 180);
	context.arc(150, 150, 50, 0, radians, true);
	context.stroke();
	context.closePath(); //Doesn’t do anything after the fact

---

###Circle [cont.]

- **We can also draw the other side of our circle**
	- All we need to do is change the direction of our tracing arc

JS

	var canvas = document.getElementById("aCanvas");
	var context = canvas.getContext("2d");
	context.beginPath();
	var radians = (270 * Math.PI)/180;
	context.arc(100, 100, 50, radians, 0, false);
	context.closePath();
	context.fill();

---

##Lab 1

- Experiment with Canvas
- Draw a red square
- Draw a blue rectangle
- Draw a vertical line

---

##Adding Gradients

---

###Other cool things you can do

- Use Gradients
- Add Shadows
- Add Text
- Move and Transform: Rotate, Scale, Skew

---

###Cool Canvas Examples

- Free Rider HD
	- [http://www.freeriderhd.com/](http://www.freeriderhd.com/)
- Picozu Editor
	- [www.picozu.com/editor](www.picozu.com/editor)

---

###Canvas Frameworks

- **EaselJS:**
	- [http://www.createjs.com/#!/EaselJS](http://www.createjs.com/#!/EaselJS)
	- Demos: [http://www.createjs.com/demos/easeljs/spritesheet](http://www.createjs.com/demos/easeljs/spritesheet)
- **Paper.js:**
	- [http://paperjs.org/](http://paperjs.org/)
- **Fabric.js:**
	- [http://fabricjs.com/](http://fabricjs.com/)
- **Dojo & the canvas:**
	- [http://dojotoolkit.org/reference-guide/1.9/dojox/gfx.html](http://dojotoolkit.org/reference-guide/1.9/dojox/gfx.html)
- **KineticJS:**
	- [http://kineticjs.com/](http://kineticjs.com/)

---

###Canvas Helps

- Canvas & Canvas Framework help
	- [http://www.html5canvastutorials.com/](http://www.html5canvastutorials.com/)

---

###Browser Test

- **Mark Pilgrim: Dive Into HTML**

>
	function canvasSupport () {
		return !!document.createElement('canvas').getContext;
	}
	function canvasApp() {
	   if (!canvasSupport) {
			return;
	  }
	}

- **Modernizr (detects HTML5 features)**

>
	function canvasSupport () {
	   return Modernizr.canvas
	}  

---

##SVG: Scalable Vector Graphics

---

###SVG Outline

- SVG Basics
- Shapes
- Paths
- CSS
- Text
- Transformation
- Animation

---

##SVG Basics

---

###SVG Basics

- **HTML5 integrates SVG with HTML**
	- Instead of drawing and manipulating pixels (i.e. Canvas)
- **SVG is an HTML-like markup language for graphics**
	- Create elements to make graphics
	- These elements interact together to make complex scenes
- **SVG with DOM allows interaction with those elements such as event handling and dynamic interactions**

---

###SVG Basics [cont.]

- SVG with CSS allows for centralized style control for maintainability
- Been around since 1999
- SVG available in all major browsers (i.e. IE 9+)

---

##SVG Shapes

---

###Basic Shape Drawing

- **Drawing a rectangle**

>
	<svg xmlns=“http://www.w3.org/2000/svg”
	  version=“1.1” width=“400” height=“300”>
	  <rect x=“0” y=“0” width=“800” height=“600”
		fill=“none” stroke=“black” stroke-width=“4”/>
	</svg>

---

###Basic Shape Drawing

- **Drawing a circle**

>
	<svg xmlns=“http://www.w3.org/2000/svg”
	  version=“1.1” width=“400” height=“300”>
	  <circle id=“theCircle” r=“200” cx=“300” cy=“400”
		fill=“green” stroke=“orange” stroke-width=“10”>
	  </circle>
	</svg>

---

###SVG in HTML

- **Integrating SVG into HTML**

>
	<body>
	  <h1>A Heading</h1>
		<svg xmlns="http://www.w3.org/2000/svg"
		  xmlns:svg="http://www.w3.org/2000/svg"
		  version="1.2" baseProfile="tiny"
		  width="400px" height="300">
		  <rect x="0" y="0" width="400" height="300"
			fill="none" stroke="black" stroke-width="4"/>
		  <circle id="theCircle" r="100" cx="125" cy="125"
			fill="green" stroke="orange" stroke-width="10"/>
		</svg>
	  <p>A paragraph of stuff</p>
	<body>

---

###Other Shape Elements

- `<rect>`
- `<circle>`
- `<ellipse>` a shape similar to a circle except that the x and y radius are not the same
- `<line>`
- `<polyline>` a shape consisting of only straight lines
- `<polygon>` a shape consisting of a shape of only 3 sides

---

##SVG Paths

---

###Paths

- Paths are generalized shapes, and can be created either open or closed
- Paths and shape can be drawn (“stroked”), or filled
- Paths are specified using textual commands

---

###Specifying Paths

- **`<path>` element takes an attribute “d” which specifies the drawing instruction(s)**
	- “M x y” move to x,y
	- “L x y” draw a line to x,y
	- “H x” draw a horizontal line to x

>
	<svg xmlns=“http://www.w3.org/2000/svg”
	  version=“1.1” width=“800” height=“600”>
		<path d=“M 20 20 L 200 20 L 200 200 h -180 Z”
		fill=“none” stroke=“orange” stroke-width=“4” />
	</svg>

---

###Specifying Paths [cont.]

- **`<path>` element takes an attribute “d” which specifies the drawing instruction(s)**
	- “V y” draw a horizontal line to x
	- “Z” close up the path to make a polygon

>
	<svg xmlns=“http://www.w3.org/2000/svg”
	  version=“1.1” width=“800” height=“600”>
		<path d=“M 20 20 L 200 20 L 200 200 h -180 Z”
		fill=“none” stroke=“orange” stroke-width=“4” />
	</svg>

---

###Specifying Paths [cont.]

- **Lowercase commands are relative (i.e. m, l and h)**
	- Meaning they change with respect to their current location
- **Let’s see how that changes our previous shape**

>
	<svg xmlns=“http://www.w3.org/2000/svg”
	  version=“1.1” width=“800” height=“600”>
		<path d=“M 20 20 l 200 20 l 200 200 h -180 Z”
		fill=“none” stroke=“orange” stroke-width=“4” />
	</svg>

---

###Bezier Curve Paths

- Bezier curves are potentially complex curves that can be joined seamlessly
- Each curve is governed by two endpoints and two control points
- Curve ends at the endpoints and are tangential to the line between the end point and the control point
- So, to make a smooth join, “reflect” the control point that is the end of one line to create the control point of the start of the next line

---

###Bezier Curves

- **Bezier curves are often designed/created by “feel”,
though the math is not hard**

---

###Specifying Bezier Curves In SVG

- **Path control elements:**
	- “C c1x c1y c2x c2y ex ey”
	- Draws a bezier (i.e. a parametric curve) from the current point to ex, ey, using c1x, c1y as the first control point, and c2x, c2y as the second control point 
	- “S c2x c2y ex ey”
	- Draws a bezier curve from the current point, that joins smoothly with the previous curve created by a C command, ending at ex, ey, with c2x, c2y as the second control point

---

###Bezier Examples

- **A single curve:**
>
	<path d=“M 20 20 C 200 20 150 250 300 150”
	fill=“none” stroke=“orange” stroke-width=“4” />

- **Two joined curves:**
>
	d=“M 20 20 C 200 20 150 250 300 150 S 700 550 20 500”

---

###Groups

- The `<g>` element defines a group, allowing setting
of attributes such as id, or painting properties on
the group, or groups the elements to facilitate
structural navigation in script.

>
	<svg xmlns=“http://www.w3.org/2000/svg”
	  version=“1.1” width=“10cm” height=“10cm”>
	  <g id=“group1” fill=“red”>
		<rect x=“1cm” y=“1cm” width=“1cm” height=“1cm”/>
		<rect x=“3cm” y=“1cm” width=“1cm” height=“1cm”/>
	  </g>
	</svg>

---

##SVG CSS & Text

---

###Using CSS Styles for SVG

- **SVG can take style instructions from CSS style**
	- This will be particularly valuable when SVG and HTML are essentially the same thing
>
	<svg xmlns="http://www.w3.org/2000/svg"
	  version="1.1" width="10cm" height="10cm">
	  <style type=“text/css”>
		<![CDATA[
		  .fatGreen {
			fill:none;
			stroke:green;
			stroke-width:6;
		  }
		]]>
	  </style>
	  <path class=“fatGreen” d=“M 20 20 C 200 20 150 250
	300 150 S 700 550 20 500”/>
	</svg>

---

###Drawing Text

- **SVG also renders text**
	- Can be styled by attributes directly on the text

>
	<svg xmlns="http://www.w3.org/2000/svg"
	  version="1.1" width="10cm" height="10cm">
	  <text x="20" y="50" font-family=“Verdana"
		font-size="30" fill="blue" >
		  Hello, Graphic World!
	  </text>
	</svg>

---

###Drawing Text [cont.]

- **SVG text can also be styled via CSS**

>
	<svg xmlns="http://www.w3.org/2000/svg"
	  version="1.1" width="10cm" height="10cm">
	  <style type=“text/css">
		<![CDATA[
		  .fatGreenText {
			fill:green;
			font-family:Helvetica;
			font-size:20pt;
			font-style:oblique;
		  }
		]]>
	  </style>
	  <text x="20" y="100" class="fatGreenText">
		Hello, Graphic World!
	  </text>
	</svg>

---

###Drawing Text [cont.]

- **SVG text can also be styled via external CSS**
	- As it should be =)

CSS

	.fatGreenText {
	  fill:green;
	  font-family:Helvetica;
	  font-size:20pt;
	  font-style:oblique;
	}

SVG

	<svg xmlns="http://www.w3.org/2000/svg"
	  version="1.1" width="10cm" height="10cm">
	  <text x="20" y="100" class="fatGreenText">
		Hello, Graphic World!
	  </text>
	</svg>

---

##SVG Transformations

---

###Transformations

- **In addition to the various drawing commands, SVG provides a comprehensive set of transformations**
- **transform=“xxxx” attribute can be applied to most relevant elements, notably groups**
- **e.g.**
	- transform=“scale(2)” double the size of everything
	- transform=“rotate(45)” rotate 45 degrees clockwise
	- transform=“skewX(20)” shear 20 degrees on the X axis

---

###Transformations [cont.]

- **Transformations are:**
	- scale: grow/shrink based on a scaling factor
	- translate: reorients the origin (i.e. moves our starting position)
	- rotate: rotation of an object
	- skewX: shoves all the x-coordinates by the specified angle
	- skewY: shoves all the y-coordinates by the specified angle
	- matrix: allows for optimizing of linear translations
- e.g.

>
	transform=“translate(300, 50) scale(0.5) rotate(45)”

---

##SVG Animation

---

###SVG Animation

- **Many aspects of SVG elements can be animated**
	- We can animate around a CSS property
	- `<animate>` needs to be embedded within a shape in order to define how the shape will move
	- The attribute will change **from** it is initial value **to** its final over the **duration**

>
	<circle r=“200” cx=“300” cy=“300”
		fill=“orangered” stroke=“red”
		stroke-width=“20”>
	  <animate attributeType=“CSS”
		attributeName=“opacity”
		from=“1” to=“0” dur=“5s”
		repeatCount=“indefinite” />
	</circle>

---

###More SVG Animation

- Animation can affect attributes
- Transformations
- Positions

---

###Animating

- **Basic text movement**
	- `<animateMotion>` causes its parent element to move along a designated path

>
	<path d=“M 100 100 h 200 v 200 h -200 z”
		stroke=“yello” stroke-width=“5” fill=“none”/>
	<text x=“100” y=“100”
		style=“font-family:Verdana;font-size:24pt;”
		fill=“blue”>
	  Hello, Graphics!
	  <animateMotion
		path=“M 0 0 h 200 v 200 h -200 z”
		dur=“5s” repeatDur=“indefinite” />
	</text>


- **SVG API - [http://www.w3.org/TR/SVG/](http://www.w3.org/TR/SVG/)**

---

###User Interaction

- **SVG allows for simple user interaction**
	- We can consume events from the SVG DOM
	- Let’s take a look: Svg.html

---



















