footer: © NodeProgram.com, Node.University and Azat Mardan 2018
slidenumbers: true
theme: Simple, 1
build-lists: true

[.slidenumbers: false] 
[.hide-footer]

![fit](images/node-testing-cover-2x 16by9.png)

---

# HTML and HTML5
## Other HTML5 APIs

- **Offline Apps**
- **Web Storage**
- **Web Sockets**
- **Web Workers**
- **The File API**

---

##Offline Apps

---

###Offline Apps

- **Use a combination of features:**
	- Online/offline events
	- localStorage
	- Web SQL & indexed databases
		- IndexedDB
	- Service Workers (replaces Application Cache)
- **Example: Mobile GMail.**
	- [http://googlecode.blogspot.com/2009/04/gmail-for-mobile-html5-series-using.html](http://googlecode.blogspot.com/2009/04/gmail-for-mobile-html5-series-using.html)
- **More info:**
	- [http://www.html5rocks.com/en/tutorials/offline/whats-offline/](http://www.html5rocks.com/en/tutorials/offline/whats-offline/)

---

###Progressive Web Apps

- **The future of mobile apps.. maybe.**
	- No need to install from an app store. Works like native.
	- App Shell Model
		- The minimal HTML, CSS, and JavaScript powering a user interface. Loads first (fast), then adds in other features.
- **Creating Progress Web Apps w/Ionic**:
	- [http://blog.ionic.io/what-is-a-progressive-web-app/](http://blog.ionic.io/what-is-a-progressive-web-app/)
- **Google PWA Guide:**
	- [https://developers.google.com/web/progressive-web-apps/?hl=en](https://developers.google.com/web/progressive-web-apps/?hl=en)
- **Service Worker Samples:**
	- [https://github.com/GoogleChrome/samples/tree/gh-pages/service-worker](https://github.com/GoogleChrome/samples/tree/gh-pages/service-worker)

---

###Online/Offline Events

- **Check online/offline status:**
>
	navigator.onLine;                              //true

- **Adding event listeners:**

>
	window.addEventListener('offline', function(){
	   alert(‘cannot connect to internet :( ’);
	});
	window.addEventListener('online', function(){
	   alert(‘we are back in business!’);
	});

---

##Web Storage

---

###Client-Side Storage

- Storage similar to cookies but is not copied to the server side
	- Therefore much more suitable for “large” data (reduced network load)
	- Typically limited to 5mb
- Storage scopes are specific to the host
- User might have to approve storage over that amount

---

###Session and Local Storage

- **Session storage**
	- **sessionStorage**
	- Lasts for this client session, in this window
	- Thereby allowing concurrent operations in multiple windows without data confusion between them
- **Local storage**
	- **localStorage**
	- Is permanent and exists across all windows, even after a browser restart

---

###Programming With Storage

- Storage uses simple key-value pairs
- Set with a set operation


	```localStorage.setItem(“color”, “blue”);```

	```sessionStorage.setItem(“style”, “modern”);```

- Read as an attribute of the storage

	```selection = localStorage.color;```
	```userSelection = sessionStorage.style;```

---

###Programming With Storage [cont.]

- Storage uses simple key-value pairs
- Key-value pairs are nice and all, but the W3C specification seems to only want primitives stored
- How could you store more?
	- Create a JSON file and then stringify it
>
	JSON.stringify(“foo”); 				//‘“foo”’
	JSON.stringify([3, “true”, true]); 	//‘[3, “false”, false]’
	JSON.stringify({a: 42}); 			//‘{“x”:5}’
	JSON.stringify({a: 42, b: 3}); 		//‘{“a”:42,”b”:3}’

- Retrieve it via JSON parse

>
	JSON.stringify(‘false’); 			//false
	JSON.stringify(‘[1, “false”, false]’);
		   //[1, “false”, false]
	JSON.stringify(‘null’);    			//null

---

###Web Storage

- **Storage uses maps**
	- sessionStorage.**setItem**(key, value)
	- localStorage.**getItem**(key)
- **Shorthand for getting values with keys known at coding time**
	- localStorage.**removeItem**(key): Removes an entry
	- sessionStorage.**clear**(): Removes all entries

---

###Storage Wars

- Web SQL
	- Seemed like it was going to be a good thing =)
	- Based on Sqlite database queries
	- It is still supported by Chrome and Apple, however it is deprecated
- IndexedDB
	- W3C replacement for Web SQL
	- Another way of storing data on the client via database queries
	- NoSQL (i.e. it is unstructured)
	- Supported by IE 10+, FireFox, Chrome
	- No support by Safari or Mobile Safari

---

###Limits

- Browsers basically allow 5MB per database without requiring the user’s permission
- It can be extended upward usually up to 50mb with users permission

---

###Lawnchair

- **Lawnchair**
	- Purpose is to make sure you have a constant API for accessing some form of localStorage
	- You can store and query data without having to worry about what is underneath the API
		- It will work with whatever is available (e.g. local storage, IndexedDB, Web SQL …)
	- JSON storage, key/value pairs
	- lawnchair: [http://brian.io/lawnchair/](http://brian.io/lawnchair/)

---

###IndexedDB

- **Works with Service Workers**
- **How to:**
	- [https://developer.mozilla.org/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB](https://developer.mozilla.org/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- **Easier interfaces:**
	- [http://dexie.org](http://dexie.org)
	- [http://mozilla.github.io/localForage/](http://mozilla.github.io/localForage/)

---

###Demo - Using Dexie

- [https://jsfiddle.net/dfahlander/3tf5r0cu/](https://jsfiddle.net/dfahlander/3tf5r0cu/)

---

##WebSockets

---

###WebSockets Outline

- **WebSocket Basics**
- **Connections**

---

###Demo

[https://starwarsttt.firebaseapp.com](https://starwarsttt.firebaseapp.com)

---

##WebSocket Basics

---

###History

- Static web pages (html)
- Dynamic web pages (JSP, ASP, PHP)
- Truly dynamic web pages (Ajax)
- Truly truly dynamic web pages (Comet web applications)
- Truly truly truly dynamic web pages (WebSocket)

---

###Connections

- **Open pipe**
	- Allows the server to push information to the client
	- Server can do what it needs to an keep sending updated information
	- “peer to peer” communication with the server
	- Full duplex communication
- **No polling with Ajax requests**
	- Sometimes you might make a request for no reason (i.e. there is no new data for you to pick up)
	- Or you poll after poll after poll which is bad for scalability

---

###Connections [cont.]

- **Less latency**
	- Ajax data transfer can be small, but still has overhead
	- WebSockets don’t contain unnecessary header information

---

###The Stealthy Ninja

- **WebSockets have the ability to traverse firewalls and proxies**
- **Similar to what Adobe Flash tried to do via their socket support**
	- Flash still hampered by proxy and firewalls
- **WebSockets detect proxy and create a tunnel**
	- Tunnel established via HTTP CONNECT method
	- Asks server to open a TCP/IP connect to the specific host and port
- **Secure WebSockets can be setup over SSL**

---

###Support

- **Every major browser supports web sockets**
	- IE 10+
- **WebSocket support in servers:**
	- WebSphere 8.5.5
	- Tomacat 7+
	- NodeJS
	- IIS 8.0

---

##WebSocket Connections

---

###Support

- **Create a new WebSocket instance**
	- Prefix is **ws://** or **wss://**
- **onopen**: Indicates that there was an established connection
- **onmessage**: Indicates that there was a message received
- **onclose**: Indicates that the server closed the connection
- **onerror**: Indicates that there are network or protocol issues

>
	var aWebSocket = new WebSocket(“ws://host:8081”);
	aWebSocket.onopen = function(event) { /*do stuff*/ };
	aWebsocket.onmessage = function(event) { /*do stuff*/ };
	aWebsocket.onclose = function(event) { /*do stuff*/ };
	aWebsocket.onerror = function(event) { /*do stuff*/ };

---

###Outbound Messages

- **If the socket is open then messages can be sent**
	- **send**: Sends a message from browser to server
	- **close**: Closes/terminates the connection
>
	aWebSocket.send(“Hello World!”);
	aWebSocket.close();

---

###Inbound Messages

- **Browser/client gets a message**
	- Message event is triggered and callback invoked
	- Callback gets an event object containing data

---

###Demo

- **Socket.io**
	- Real time chat application
	- Node.js back end

---

##Web Workers and Service Workers

---

###Web Workers Outline

- Web Worker Basics
- Implementation

---

##Web Worker Basics

---

###History

- **Web Workers began in part with the Google Gears team**
	- Worked on creating a worker pool module
- **Wanted to get JavaScript to run in parallel on a web page (i.e. the user interface won’t get blocked)**
	- To do this you had to break up chunks of your computation and split execution tasks
	- Usually used timers
	- Didn’t work great

---

###Problem

- **JavaScript can only run one thing at a time**
	- It is single threaded
- **A complex computation can make a user interface drag and be unresponsive**

---

###Solution

- What if we could hand off large/complex processing to a helper
- Web Workers allow us to pass off that processing to a separate thread to work
	- When it is finished it can pass the work back to our application
- Allows our main thread to manage the user interface and interaction

---

###Solution [cont.]

- JavaScript being threaded is a good thing
- It was easy to interact with and didn’t go crazy with multithreading
- Web Workers take step to multithreading, but aim to keep things simple

---

##Web Worker Basics

---

###Keep it Simple

- Web Workers have limitations
- They can’t access the DOM
	- That is the main threads job
	- We want the DOM interaction to be single threaded for a consistent state
- They can’t access any program variables or functions in the application code
- They are separate code in separate JavaScript files

---

###Keep it Simple [cont.]

- The main JavaScript application and the Web Workers communicate back and forth via messaging
	- Workers can send messages anytime, not just when they are done

Main application
>
	worker = new Worker(‘worker.js’);
	worker.postMessage(‘Start please’);

Web Worker
>
	postMessage(‘I’m done here is your stuff:’ + stuff);

---

###Keep it Simple [cont.]

- Both the main app and the Web Worker contain **onmessage** handlers
	- These handlers get an **event** object
		- **event.data** property: Information passed between
		- **event.target** object: A reference to the Web Worker object

Main application
>
	worker.onmessage = function(event) {
	  console.log(‘Passed data from Web Worker: ‘ + event.data);
	};

Web Worker
>
	var onmessage = function (event) {
	  console.log(‘Passed data from main: ‘ + event.data);
	};

---

###What to Pass

- **Strings can be passed**
>
	worker.postMessage(“Hello World”);

- **Arrays are fine**
>
	worker.postMessage([1, 3, 4, 8, 13]);

- **Object are fine**
>
	worker.postMessage({
		   firstWord: “Hello”,
		   secondWord: “World”
	});

- **No functions!**
	- They could contain DOM manipulation allowing the worker to do bad bad bad things =)

---

###Error Handling

- If the worker throws an object (e.g. due to failure) it receives the error via the **onerror** callback
- If a Worker needs to be killed use **terminate**

Main application
>
	worker.onerror = function(event) {
	  console.log(‘Passed data from Web Worker: ‘ + event.data);
	};

Main application
>
	worker.terminate()

---

###Uses

- Caching data for use in pages
- Processing large amounts of data or complex data
- Polling web services and alerting the main thread when data is ready
- Pre-fetching data

---

###Limitations

- **JavaScript lacks concurrency controls**
- **DOM access must be single-threaded, so:**
	- Workers have no DOM access
- **Workers are “heavy weight”**
	- Each worker takes memory and an OS thread
	- Avoid creating many of them
	- Avoid wasting them

---

###Support

- IE 10+ Browser support

---

###Worker Detection

- To test a browser check for the **Worker** object
	- Yes it is a capital "**W**"

Browser Test
>
	if (window.Worker) {
	  console.log(“We have a winner”);
	} else {
	  console.log(“No Web Worker support”);
	}

---

###Demo

- SimpleWorker.html: Simple Worker HTML
- workerManager.js: Main JS application
- worker.js: The Web Worker
- Needs a web server

---

###Service Workers

- Read about service workers:
	- [https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers)
- Demo App:
	- [https://mdn.github.io/sw-test/](https://mdn.github.io/sw-test/)

---

##The File API

---

###What is the file API?

- Provides information about files.
- Allows JavaScript to access file contents.
- Uses html `<input type=“file”>`

---

###Accessing via JavaScript

- **File.name**
- **File.lastModifiedDate**
- **Can also add an .onchange listener to the file input box.**
	- Useful for things like displaying an image preview on the web page.

---

##Let’s check it out

- [https://scotch.io/tutorials/use-the-html5-file-apitowork-with-files-locally-in-the-browser](https://scotch.io/tutorials/use-the-html5-file-apitowork-with-files-locally-in-the-browser)
- Fork the demo:
	- [http://codepen.io/iScott/pen/PzYXVw](http://codepen.io/iScott/pen/PzYXVw)

