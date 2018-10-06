---
layout:      project
title:       Ballpit
date:        4 Jun 2018
screenshot:
  src:       /img/ballpit/ballpit_1920.png
  srcset:
    1920w:   /img/ballpit/ballpit_1920.png
    960w:    /img/ballpit/ballpit_960.png
    480w:    /img/ballpit/ballpit_480.png
caption:     A bouncing ball simulation with collision detection.
description: Ballpit is a bouncing ball simumlation built with P5.js. It features collision detection.
links:
  - title:   View Project
    url:     ../../project_code/ballpit_p5/index.html
  - title:   Github
    url:     https://github.com/inspectordanno/ballpit_p5
featured:    false
---
This is a p5.js experiment that creates balls and has them bounce around a screen. When certain balls hit each other, they change colors and reverse direction. I used ES6 classes to give each ball a class and a set of behaviors that control for collision detection and color changing:

~~~js

//make ball class
class Ball {
  constructor(fill) {
    this.x = random(width);
    this.y = random(height);
    this.r = random(5, 25);
    this.fill = fill;            //line 24 sets the fill to a fill argument which is set when a button is
    this.yVel = random(-3, 3);  //clicked and when the balls hit each other
    this.xVel = random(-3, 3);
  }

  //this sets the x position to the constructor + the x velocity
  //and sets the y position to the constructor + the y velocity
  //and runs the checkBalls() and checkWalls() functions

  move() {
  //this.xVel += xVel;
  this.x = this.x + this.xVel;
  this.y = this.y + this.yVel;
  this.checkWalls();
  this.checkBalls();
  }

  //this is a for loop that loops through all the balls in an array
  //if the current ball doesn't equal itself
  //then when half the current balls radius plus half the other balls radius is greater than their
  //midpoints, a hit is made, and velocity is reversed
  //I also have the balls change color when they hit each other

  //Note: There is a weird edge case when the balls get stuck inside each other
  //which I haven't been able to figure out

  checkBalls() {
    for(this.i = 0; this.i < balls.length; this.i++){
      if(this !== balls[this.i]){
      if( this.r/2 + balls[this.i].r/2 > 1 + dist(this.x, this.y, balls[this.i].x, balls[this.i].y)){
        if((this.xVel / Math.abs(this.xVel) != balls[this.i].xVel / Math.abs(balls[this.i].xVel)) &&
        (this.yVel / Math.abs(this.yVel) != balls[this.i].yVel / Math.abs(balls[this.i].yVel))) { 
          console.log("hit");
          this.xVel *= -1;
          this.yVel *= -1;
          if (this.fill === themeGreen) {
            balls[this.i].fill = themeOrange;
          } else if (this.fill === themeOrange) {
            balls[this.i].fill = themePurple;
          } else if (this.fill === themePurple) {
            balls[this.i].fill = themeGreen;
          }
        }
      }
    }
  }
}

  //if x is less than zero and greater than width,
  //and y is less than zero and greater than height,
  //reverse velocity

  checkWalls() {
   //check for walls
   if(this.x < 0 || this.x > width) {
    this.xVel *= -1;
    //this.x = width-this.r;
    console.log(this.xVel);
   }
   if(this.y < 0 || this.y > height) {
    this.yVel *= -1;
    console.log("hit y wall");
   }
 }

 //this is a method that shows the ball, and is run in draw

  show() {
  stroke(255);
  strokeWeight(1);
  fill(this.fill);
  ellipse(this.x, this.y, this.r);
  }

} //end class declaration
~~~
