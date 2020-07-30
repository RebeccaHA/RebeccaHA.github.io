---
layout: post
title:      "Are we heading in the right direction?"
date:       2020-07-30 17:47:23 +0000
permalink:  are_we_heading_in_the_right_direction
---


Everyone I've chatted to talks about the Javascript wall.. After working through this module, I think its probably true. Though I would call it 'The Javascript trough of despair'. 

![](https://image.slidesharecdn.com/smoothing-the-way3049/95/smoothing-the-way-68-728.jpg?cb=1187043227http://)

The first few of the concepts seem simple, and you feel 'oo ok I've got this!', this was manipulating the DOM and adding events. A simple concept, grab an element by an class, id or tag and then do something with it. As you progress you learn about communicating with the server, trying to work out what promises are? (and no it's not promising to not eat that whole bar of chocolate). Here was where I started to feel 'Ok I'm definitely out of my depth'. Then lastly it's about joining everything together, remembering your old friend Ruby as you slowly crawl out of the trough. 

You sit back and wonder 'ah it wasn't that bad after all', and are proud of what you have achieved. We are heading in the right direction.

Talking of directions, I decided to challenge myself further and learn how to integrate the 3rd party Google Maps api. Reading up on the documentation, it can be broken into 3 steps. 

Step 1:

-Create a Google console account, set up a project and enable the Javascript api credientals. This will provide you with a personal api key. Use this key in the script tag below: 
```
<script
src="https://maps.googleapis.com/maps/api/js?key=YOUR_API_KEY
> </script>
```

In the documentation they include the word 'defer', this defers the loading of the script. I removed this as I wanted my map to load as soon as the html page loads.

Step 2:

-In your html file include:
```
<div id=map> 
</div>
```

This id give you the opportunity to add a height and width to your map, it must have a height in order to appear.

Step 3:

-Add your Google Map functions. There are a range of things you can do, adding markers, pin drop click events and info bubbles. You will need to include the getMap function in order to retrieve the base map:
```
let map;

function initMap() {
  map = new google.maps.Map(document.getElementById("map"), {
    zoom: 11,
    center: { lat: 51.5032, lng: -0.1123 }
  });
  return map;
}
```

This initiates a new instance of a map, and adds it to the ```<div>``` we added in the html file. It takes in two arguments and these are passed in a key value pairs. A zoom level and a center focus point.

Completing those steps provides you with a basic map. I wanted to build upon that and use the fetch method to retrieve data from my database and populate the map with location pins. To add pins I created a function that takes in coordinates and content. From my fetch request I moulded the data so it was in the correct format to be passed to the add pins function.

```
function addMarker(coords, content) {
  let marker = new google.maps.Marker({
    position: coords,
    map: map
  });

  let infoWindow = new google.maps.InfoWindow({
    content: content
  });

  marker.addListener("click", function() {
    infoWindow.open(map, marker);
  });
}
```

What I've learnt, is when the task seems to big or unachievable! Break it down, go back to what you know, keep calm and carry on.




