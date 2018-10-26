---
layout:      project
title:       Personal Statement
date:        26 May 2018
screenshot:
  src:       /img/personal/personal_1920.png
  srcset:
    1920w:   /img/personal/personal_1920.png
    960w:    /img/personal/personal_960.png
    480w:    /img/personal/personal_480.png
caption:     A simple slideshow made in P5.js.
description: A simple slideshow made in P5.js.
links:
  - title:   View Project
    url:     ../../project_code/personal_statement_p5/index.html
  - title:   Github
    url:     https://github.com/inspectordanno/personal_statement_p5
featured:    false
---
For this assignment, I was tasked with implementing a slide show in P5.js. It ended up evolving into a strange, stream-of-consciousness comparison between Philadelphia and Boston, complete with Ben Franklin and oddly placed bottles of milk. The code itself is not as efficient as I would like it be. I had some problems with some P5 functions and I wasn't able to make them reusable.

The major challenge I had with this project was implementing the variable logic throughout global, setup, and draw. I implemented this project in JavaScript, and am accustomed to declaring my variables as arguments within functions, along with some globally defined variables. Because setup and draw do not take arguments, and draw cannot access variables within setup, I was initially confused on the proper way to define a function globally and then redefine its value within setup or draw.

This issue came to a head when I was building the iteration array that cycled through the functions that ran in my program. Most of my functions fall into two broad categories—writing text to the canvas and attaching pictures to the canvas. The text was placed in the canvas using a consistent typographic technique, and the pictures were also written to the canvas in a consistent manner. Because of this, I attempted to create functions that would serve as templates for writing text and images, and pass in strings as arguments. This solution didn't work and I needed to test other strategies.

The problem was that I was setting variables equal to function invocations, and then attempting to call them from an array. One cannot set a variable to a function invocation—rather, one has to set it to a function declaration (with the function keyword). However, if I were to do this, I would still have to write each function out individually, without using the invocation shorthand, which would defeat the purpose.

The ideal solution would probably be to store the strings in an array, and invoke the functions from draw, while cycling through the strings. The only other minor issue was collectively positioning rectangles on the canvas, but I learned that I could do with translate. 

This is the draw function. It is basically a timer that changes the slides every three seconds.

~~~js
function draw() {

// timeElapsed is the duration between the current time and lastPrint, when the previous function was run.
//  When timeElapsed is greater than 3 seconds (basically as soon as it hits 3 seconds), a function
//  in the array is run, and then i is iterated to the next value. Then, lastPrint is set to the
//  current millisecond time. In this way, lastPrint is constantly updated, yielding a timeElapsed value
//  that approaches the three second threshold.

//The initial state is not paused

  if (!paused) {
    var timeElapsed = millis() - lastPrint;
    if (timeElapsed > 3000) {
    background(themeRed);
    myFunctions[i]();
      console.log(i);
    if (i < myFunctions.length-1){
      i++;
      } else {
      i = 0;
      }
    lastPrint = millis();
    }
  }
}

//This function sets paused to its opposite, which either pauses or resumes the slideshow

function playPressed(){
  paused = !paused;
}
~~~