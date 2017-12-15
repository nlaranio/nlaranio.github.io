---
layout: project
type: project
image: images/micromouse.jpg
title: EZGif
permalink: projects/ezgif
date: 2017
labels:
 - EZJava
 - EZGraphics
 - Animation
 - Java
 - ICS111
summary: A tool for use with EZJava to quickly and easily create GIF style animations.
---
 
### Table of contents

* [Overview: EZGif](#overview-of-ezgif)
* [Usage](#usage)

#### Overview of EZGif
EZGif is meant as a plugin to the useful java beginner tool EZJava (now EZGraphics) used by the ICS111 class at UH Manoa; you can find out more about EZJava [here](http://www2.hawaii.edu/~dylank/ics111/). EZJava is a great tool for beginners to learn to code, especially those who learn best visually. One thing that was missing from it was an easy way to implement animation; you generally need to hardcore it which was very time consuming. EZGif is something I put together which allows you to take a number of images sorted by name and create animated objects easily. There are features such as changing the speed of the animation, changing the location, and morphing images in the animation. 

#### Usage
EZGif uses the EZJava framework, so EZJava is required. it can be found [here](http://www2.hawaii.edu/~dylank/ics111/).
You will also need EZGif found [here](http://github.com/nlaranio/ezgif/).
Most of EZGif is just formatting; the constructor takes in two strings as arguments when making an EZGif object, first is the file name, second is the gif name. For the sample that file would be "gifs.txt" and the gif name would be "STAR."

Sample file given (gifs.txt):
```
STAR
star1.png
star2.png
star3.png
star4.png
star5.png
star6.png
star7.png
STAR
```

<ul>
  <li>The file names are the path to the file</li>
  <li>No spaces or blank lines are allowed</li>
  <li>Only one file per line can be read</li>
  <li>Only .png files are supported</li>
</ul>

If everything runs properly for the sample you should see an animation in your EZJava window that looks like this:
<iframe src="https://giphy.com/embed/3o6fIYvQ3XZFvr3nK8" width="480" height="360" frameBorder="0" class="giphy-embed" allowFullScreen></iframe>

multiple gifs can be put in one file and the format would be as follows.
```
STAR
star1.png
star2.png
star3.png
star4.png
star5.png
star6.png
star7.png
STAR
CIRCLE
path/circle1.png
path/circle2.png
path/circle3.png
CIRCLE
```

For current documentation on available modifier functions (such as time and movement) please refer to the code documentation.

