footer: © NodeProgram.com, Node.University and Azat Mardan 2018
slidenumbers: true
theme: Simple, 1
build-lists: true

[.slidenumbers: false] 
[.hide-footer]

![fit](images/node-testing-cover-2x 16by9.png)

---

# HTML and HTML5
## Geolocation

##Geolocation Outline

- **Geolocation Basics**
- **Get the Device Position**
- **Watch the Device Position**

---

##Geolocation Basics

---

###Why Geolocation

- Allows people to know where they are and where stuff is around them
- Wouldn’t it be nice to know the barometric pressure?
- Wouldn’t it be nice to know where the nearestRedbox is?

---

###Geolocation

- Not a first class member of HTML5
- A W3C standard
- A JavaScript API

---

###Privacy

- You don’t just automatically get to know a person’s location
- Browsers will ask users for their approval to use the device location
- Usually an alert of some sort will pop-up to grant permission

---

###Google Maps

- Google Maps API and the Geolocation API are different
	- Both are JavaScript APIs
- Geolocation tells you where the device is at in relation to the earth
- Google Maps takes that location and then gives the application information about it

---

###Position Makeup

- **Coordinate system is based on longitude and latitude**
	- Longitude is measured East / West from Greenwich, England
		- A negative longitude means west of Greenwich
	- Latitude is measured North / South from the equator
		- A negative latitude means south of the equator

---

###Position Markup

- **Where is Boulder CO?**
- **Normal every day usage is in degrees/minutes/seconds format**
	- (47o0’54”, 105o16’12”) … 47o0’54” N / 105o16’12” W
- **Programmatically we get decimals**
	- (40.176, -105.2797) … 40.176° N, 105.2797° W

---

###Conversion

- **Conversion formula for degrees to decimal**

>
	var degreesToDecimal = function(degrees, minutes, seconds) {
	  return degrees + (minutes / 60.0) + (seconds / 3600.0);
	};

---

###How?

- **Really a location?**
	- Different layers of detection
	- Some are better than others

---

###How? [cont.]

- **Browser might use any or all of:**
	- IP address
		- External database that will map a device to a physical location
		- Usually resolves to the ISP office
		- At least the correct city =)
	- GPS IP address
		- Supported by a lot of devices
		- Usually GPS chips coincide with wireless antennas (e.g. 3G, 4G/LTE)
		- Location can include elevation (i.e. altitude), speed and heading (i.e. directional information)
		- You do need a view of the sky for this to work
		- Can load slowly and is a battery hog

---

###How? [cont.]

- **Browser might use any or all of:**
	- Cell towers and signal strengths (i.e. cell triangulation)
		- Gets a device location based on distance from one or more cell towers
		- The more towers the better accuracy
		- It can work indoors
		- Quicker than GPS
	- WiFi hotspots (i.e. WiFi triangulation)
		- Uses one or more WiFi access points to get the device location
		- Relatively quick
		- Very accurate and works indoors
		- The device does have to be stationary (i.e. eating a bagel at Panera)

---

##Get the Device Position

---

###Sounds Complicated

- **Not really … Your browser does the hard work**
	- It “rolls” through the options available and picks the most accurate positioning it has to offer

>
	var getMyLocation = (function (displayLocation) {
	  if (navigator.geolocation) {
		navigator.geolocation.getCurrentPosition(function(position) {
		  console.log(“latitude: " + position.coords.latitude +
			“\nlongitude: " + position.coords.longitude);
		});
	  } else {
		  console.log(“no location available");
	  }
	}());

- **WARNING: Chrome blocks geolocation on http
(insecure) and local files. Use https instead or use
firefox or Safari to test.**

---

###Get the Current Location

- **Let’s dissect this method signature**
	- **successHandler**: Function invoked if the location was found
	- **errorHandler**: Function invoked if the browser couldn’t get a location
	- **options object**: Extra options to tweak geolocation

>
	navigator.gelolocation.getCurrentPosition(
	  successHandler, errorHandler, options)

---


###API: Success Handler

- **Function invoked if the location was found**
	- Passed a **position** object, as an argument, containing the location information
	- Position contains coords and timestamp
		1. **coords**: A coordinates object
		2. **timestamp**: A timestamp in milliseconds
			- If you need to use it simply create a new Date() out of it
			- Let’s you know how old the location is
>
	new Date(position.timestamp)

---

###API: Success Handler [cont.]

- **Coordinates object**
	- **latitude**: North / South measurement
	- **longitude**: East / West measurement
	- **accuracy**: Accuracy of longitude and latitude specified in meters
	- **speed** (optional): Current ground speed of the device
	- **heading** (optional): Direction of travel of the device, measured in degrees from 0o to 360o clockwise
	- **altitude** (optional): Height of the device above sea level
	- **altitudeAccuracy** (optional): Accuracy of height specified in meters

---

###API: Error Handler

- Function invoked if the browser couldn’t get a location
- There is an **error** object argument given to the **errorHandler**
	- That error object has a **message** and a **code** property
	- Code 0: Unknown error
		- Catchall error used when nothing else makes sense
		- The **error.message** property gives more information
	- Code 1: Permission denied by the user
		- The user shut you down and they don’t want you to know where they are
>
	navigator.gelolocation.getCurrentPosition(
	  successHandler, errorHandler, options)

---

###API: Error Handler [cont.]

- There is an **error** object argument given to the **errorHandler**
	- Code 2: Position is not available
		- The browser tried to get the position, but failed =(
		- The **error.message** property gives more information
	- Code 3: Request timed out
		- The browser had an internal timeout that was triggered before it was able to retrieve a location
		- This timeout can be set to a longer/shorter interval
- Errors with codes 0 or 2 have extra information

>
	navigator.gelolocation.getCurrentPosition(
	  successHandler, errorHandler, options)

---

###API: Position Options\

- **Three properties that can be set (all optional)** 
	- **enableHighAccuracy**: boolean
		- Defaults to false
		- Might make location resolution slower
		- Tries to retrieve exact location
		- iPhones and Androids have separate permissions for high-accuracy positioning
>
	navigator.gelolocation.getCurrentPosition(
	  successHandler, errorHandler, options)

---

###API: Position Options [cont.]

- **Three properties that can be set (all optional)**
	- **timeout**:
		- No default
		- Defined in milliseconds
		- How long the application is willing to wait for the position
		- Starts counting after user gives permission for the search
>
	navigator.gelolocation.getCurrentPosition(
	  successHandler, errorHandler, options)

---

###API: Position Options [cont.]

- **Three properties that can be set (all optional)**
	- **maximumAge**:
		- Defaults to 0
		- Defined in milliseconds
		- Allows the browser to answer with a cached position if it is not longer than the allotted time
>
	navigator.gelolocation.getCurrentPosition(
	  successHandler, errorHandler, options)

---

##Watch the Device Position

---

###Skynet

- Maybe you want to continuously know where the user is located
- You want to know whenever they move
	- getCurrentPosition() won’t be a good fit
- You will need to watch their position

---

###Watch Position

- the **watchPosition** method is very similar to **getCurrentPosition** method
- **Differences**
	- Has built in polling functionality looking for a change in position
		- successHandler will be called if a new position is found
		- Used in real-time geolocation apps
		- Don’t roll your own polling mechanism
	- **watcher**
		- A unique identifier for this watch position operation
>
	var watcher = navigator.geolocation.watchPosition(
	  successHandler, errorHandler, options)

---

###Clear Watch

- When we need to clear out the watch we can use the **clearWatch** method
	- You have a reference to the **watcher** that was setup
	- You need to pass that **watcher** into the **clearWatch** method
	- This could be done in the **successCalback** method
		- Maybe after you get a good location you clear the **watcher**
>
	navigator.geolocation.clearWatch(watcher)

---

##Lab 1

- **Where did you say you updated the supply inventory?**
	- Add Geolocation coordinates to your Total Sales form on the supplies page
- **How far is our lemonade stand away from Alex’s home town?**
	- Lemonade headquarters: 333 E. Lancaster Ave., #414, Wynnewood, PA 19096
	- Use Geolocation coordinates to give the distance in miles or kilometers to the Lemonade headquarters! Put this in the **give** page `<aside>` section


