footer: © NodeProgram.com, Node.University and Azat Mardan 2018
slidenumbers: true
theme: Simple, 1
build-lists: true

[.slidenumbers: false] 
[.hide-footer]

![fit](images/node-testing-cover-2x 16by9.png)

---

# HTML and HTML5
## Video and Audio Outline

- **History**
- **HTML5 Video**
- **HTML5 Audio**

---

###History of Video and Audio

- **Plugins and the embed tag**
- **Linking to media with an anchor tag**
- **Streaming formats and players**
	- Flash
	- Real Player

>
	<EMBED SRC="peanuts.mid" AUTOSTART=FALSE LOOP=FALSE WIDTH=145
	HEIGHT=55
	ALIGN="CENTER">
	</EMBED>
	or
	<a href=" mysounds/filename.wav"> Click Here</a>
	<a href="myvideos/filename.avi"> Click Here to see video</a>

---

###HTML5 Video Formats

- **MPEG 4: .mp4 or m4v**
	- Based on Apple’s QuickTime format of .mov
- **Ogg: .ogv or .ogg**
	- Open … not hindered with any known patents
	- Contains Theora (Ogg video) and Vorbis (Ogg audio)
	- Can be played with the VLC player
- **Flash: .flv**
	- Used by Adobe Flash plugin
	- Supports MPEG 4
- **WebM: .webm**
	- Open … royalty free
	- Uses VP8 video codec and Vorbis audio codecWebSockets Intro

---

###Watching a Video

- **The player interprets the format**
	- Finds information about the video and audio tracks
- **The player decodes the video stream**
- **The player decodes the audio stream**

---

###Codec

- **Way in which an algorithm is encoded**
- **A coder + decoder … co + dec … codec**
- **Top codecs:**
	- Both produce great video with low decoding complexity
	- H.264: MPEG-4 (Safari, IE 9+)
	- VP8: (Chrome, Mozilla, Opera)

---

###Horizon is Complex

- **Along with the different formats there come different browser support issues**
- **We need to make videos of different formats**
	- WebM (VP8 + Vorbis) … for Chrome
	- H.264 baseline video with AAC “low complexity” audio within an MP4 container … for Safari
	- Possibly a Theora vide with Vorbis audio in an Ogg Container
		- You shouldn’t need this format as Firefox plays H.264/WebM
- **FFmpeg is useful for making video formats as it
can be scripted**
	- [http://www.ffmpeg.org/](http://www.ffmpeg.org/)

---

###Now What?

- **Along with the different formats there come different browser support issues**
- **Serve up MP4 before WebM and you should be all set**
	- Historically this was for an iOS bug … but it was resolved back in iOS 4
>
	<video width="640" height="360">
	  <source src="http://media.w3.org/2010/05/sintel/trailer.mp4"
		type="video/mp4" />
	  <source id='webm' src=“http://media.w3.org/2010/05/sintel/
		trailer.mp4" type='video/webm'>
	</video>

---

###Now What? [cont.]

- **IE 8 needs a flash fall back**
	- [https://flowplayer.org/player/](https://flowplayer.org/player/) - Pretty cheap / pay per domain
	- Wraps your MP4 video so no flash creation needed
	- Allows the HTML5 player to work for all browsers and then falls back to flash for IE 8

---

###Video Attributes

- **controls**: Provides a browser defined way to interact/control with the movie
- **poster**: Allows for a custom image to be displayed while loading
- **preload**: Will make the browser begin downloading right when the page loads
	- **preload** = **“none”** will minimize network traffic
- **autoplay**: Will start downloading and playing as soon as the page loads

>
    <video poster=“[http://media.w3.org/2010/05/sintel/poster.png](http://media.w3.org/2010/05/sintel/poster.png)”
      controls preload autoplay>

---

###HTML5 Audio

- **Similar to video setup but uses <audio> tag**
- **Audio formats depend on browser support**
	- Includes mp3, ogg, aac, and pcm/wave.
	- [https://developer.mozilla.org/en-US/docs/Web/HTML/Supported_media_formats](https://developer.mozilla.org/en-US/docs/Web/HTML/Supported_media_formats)

>
	<audio id="demo" src="audio.mp3"></audio>
	<div>
	  <button onclick="document.getElementById('demo').play()">Play
	the Audio</button>
	  <button onclick="document.getElementById('demo').pause()">Pause
	the Audio</button>
	  <button onclick="document.getElementById('demo').volume
	+=0.1">Increase Volume</button>
	  <button onclick="document.getElementById('demo').volume-
	=0.1">Decrease Volume</button>
	</div>

---

###Mobile Devices

- **Benefits of Video and Audio on Mobile Devices**
	- Native audio - Control Center integration
	- Native video player

---

##Demo

- **Let’s play**
	- **Video/index.html**







