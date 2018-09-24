# dynamic_webar

This is a proof of concept showing how to dynamically combine and divide different webAR pages.

How To Combine webAR Scenes Dynamically
Author: Matt Nutsch
Date: 9-23-2018

Try it out: 
Print the target markers.
Open the web page at: https://www.mattnutsch.com/dynamic_webar/controller.html
Point the camera at the target markers.
Check or uncheck the boxes to dynamically combine different webAR pages.

What are we doing?

This is an explanation for how to build an experimental controller for combining webAR scenes dynamically (on the fly). The goal is to be able to programmatically add and remove webAR elements from different URL's. 

Why might we want to do this?

One of the advantages of webAR over native apps is that, with webAR, content can be served over the internet like a web page. By combining AR from different sources, we can access content from different publishers simultaneously. 

By doing this dynamically, we can also give context to the AR. For example, imagine that we are traveling through the city and we want to load AR content that relates to certain locations. By using our geolocation as a trigger, then we can load and experience location relevant webAR on the fly as we navigate the real world. 

Finally, devices can't store an infinite amount of AR content. By dynamically loading AR content, we can load only the AR content which is immediately relevant to the user.

What do I need for this tutorial?


You will want a computer and a mobile device (phone or tablet). It helps if you have a basic understanding of website HTML and Javascript. (The specific framework of webAR used in this tutorial is AR.js with Aframe, but the exact framework for webAR isn't important.) Finally, it help

Print out Target Markers:
The webAR framework used in this tutorial works off of target markers. These are 2D images which serve as the location onto which AR objects are placed. The following is an image with the 3D target markers used in this tutorial. You can also find a copy of this image in the tutorial Github code. Please print out this image. (https://mnutsch.github.io/threeCodes.png)

Creating Transparent WebAR Scenes:

In order to demonstrate dynamically loading and unloading webAR scenes, we need some webAR scenes. (I created some for this tutorial, see the files: arjstestBlue.html, arjstestRed.html, arjstestYellow.html.) 

Start with creating a standard webAR scene using AR.js. A webAR scene is a web page showing the camera view with AR content overlayed on it. AR.js is a framework which combines AFrame & image recognition to make web accessible target marker based augmented reality. 
Information about making a webAR scene with AR.js can be found here: https://github.com/jeromeetienne/AR.js/blob/master/README.md
Next, set the background of the webAR scene's body tag to transparent. This will become important later on when we combine AR scenes together.
Add code to strip out the camera feed (which AR.js adds to the background). We have to do this, because if every AR scene rendered a background then we would only see whichever AR scene is on top. A simple hack for this is to wait a set amount of time for the AR scene to load and then remove the video element. 
We now have a webAR scene where the AR objects are shown on a transparent background. We can test this by loading the webAR scene and holding up a target marker in front of the camera. The AR objects will display, but the background (camera feed) will not. 
Repeat this for all of the webAR scenes to combine.

Creating the Background:

We don't want the video to be removed from all of our webAR scenes, because the user needs to be able to see what the camera sees. We will create one webAR scene where we keep the background video. (In the tutorial Github repo, see the file: background.html.)

Create a standard webAR scene using AR.js. 
Information about making a webAR scene with AR.js can be found here: https://github.com/jeromeetienne/AR.js/blob/master/README.md
Leave the camera feed in.

Combining WebAR Scenes - The Controller:

Now that we have multiple webAR scenes, we need a way to display them simultaneously. To do this we will create a single web page with javascript code to control the adding and removing of AR scenes. (See the file: controller.html .)

Create an empty HTML web page.
Style the body element with 100% width and 100% heigh. This element will store the webAR scenes as iFrames.
Add Javascript to add or remove webAR scenes to/from the page. In the tutorial code, I did this with the functions addIframe() and removeIframe(). 
Add Javascript/HTML code to trigger the adding or removing of AR scenes. We will do this with checkboxes and the onchange event. However this could be done with geolocation; voice commands; or any other type of event detection. In the tutorial code, this process is represented by the function toggleOverlay().
We now have a web page which allows the user to dynamically combine and remove webAR scenes. 

Testing it out:

Upload the files to a web server. (Or use my example at: https://www.mattnutsch.com/dynamic_webar/controller.html)
Open the controller.html file in a modern web browser.
If prompted, give the browser permission to use the camera.
The webAR app will appear and the device's webcam will display as the background. 
Hold up the target marker image where the webcam can see it. 
Check and uncheck the checkboxes to experience webAR pages dynamically added and removed. In this tutorial these are represented as simple colored boxes overlayed on the target markers. 
