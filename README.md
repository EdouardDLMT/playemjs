[![Analytics](https://ga-beacon.appspot.com/UA-1858235-12/playemjs/github)](https://github.com/igrigorik/ga-beacon)

PlayemJS
========

PlayemJS is a javascript component that manages a music/video track queue and plays a sequence of songs by embedding several players in a HTML DIV including Youtube, Soundcloud and Vimeo.

PlayemJS powers the music curation service [Openwhyd.org](http://openwhyd.org) (formerly whyd.com). That's the best demonstration of its capabilities.

Usage example
-------------

The following lines of HTML and Javascript create a container and play two videos in it, sequentially.

```javascript
<div id="container"></div>
<script>
new PlayemLoader().loadAllPlayers().whenReady(function(playem){
  playem.addTrackByUrl("https://www.youtube.com/watch?v=fuhHU_BZXSk");
  playem.addTrackByUrl("https://www.dailymotion.com/video/x25ohb");
  playem.play();
});
</script>
```

Demos
-----

1. [Playing a Vimeo video](http://codepen.io/adrienjoly/pen/QjLRXa?editors=101)
2. [Playing video from a combined file](http://codepen.io/adrienjoly/pen/bVbPbo?editors=101)
3. [Playing two videos in sequence](https://jsfiddle.net/adrienjoly/0xqoo0s0/)
4. [Playing two Youtube videos in sequence](http://rawgit.com/adrienjoly/playemjs/master/test/sample.html)

Usage with npm & browserify
---------------------------

    npm install playemjs

Then use it that way in your front-end code:

```javascript
<html>
<body>
  <div id="container"></div>
  <script src="your-browserify-bundle.js"></script>
  <script>
    // your app's API KEYS here
    window.SOUNDCLOUD_CLIENT_ID = "11f9999111b5555c22227777c3333fed"; // your api key
    window.DEEZER_APP_ID = 123456789;
    window.DEEZER_CHANNEL_URL = "http://mysite.com/deezer-channel.html";
    window.JAMENDO_CLIENT_ID = "f9ff9f0f";

    var playerParams = {
      playerId: "genericplayer",
      origin: window.location.host || window.location.hostname,
      playerContainer: document.getElementById("container")
    };

    window.makePlayem(null, playerParams, function onLoaded(playem){
      playem.on("onTrackChange", function(track){
        console.log("streaming track " + track.trackId + " from " + track.playerName);
      });
      playem.addTrackByUrl("https://www.youtube.com/watch?v=fuhHU_BZXSk");
      playem.addTrackByUrl("https://www.dailymotion.com/video/x25ohb");
      playem.play();
    });
  </script>
</body>
</html>
```

Install using Bower
-------------------

    bower install playemjs
    make install
    make compile
    make tests

... or download the javascript files (playem.js and player files you need) into your public directory of your web project.

React component
---------------

(Work in progress) Check out [react-music-player](https://github.com/adrienjoly/react-music-player).

Tests and further development
-----------------------------
    
You can run tests from that page:

- [PlayemJS Youtube Video Test](https://cdn.rawgit.com/adrienjoly/playemjs/master/test/sample.html)
- [PlayemJS Video Players Test](https://cdn.rawgit.com/adrienjoly/playemjs/master/test/test-players/index.html)
- [PlayemJS URL Detection Test](https://cdn.rawgit.com/adrienjoly/playemjs/master/test/test-detection/index.html)


If they don't work from there, you can clone the project, and run them locally.

Any help in documenting/fixing/developing this project is welcome! :-)
