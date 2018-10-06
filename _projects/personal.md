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
For this assignment, I was taked with implementing a slide show in P5.js. It ended up involving into a strange, stream-of-consciousness comparison between Philadelphia and Boston, complete with Ben Franklin and oddly placed rectangles and bottles of milk. The code itself is not as efficient as I would like it be. I having some strange problems with some P5 functions and I wasn't able to make them reusable.

This is the draw function. It is basicaly a timer that changes the slides every three seconds.

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