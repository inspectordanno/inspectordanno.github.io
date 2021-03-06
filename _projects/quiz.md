---
layout:      project
title:       U.S. State Capitals Quiz
date:        12 Jun 2018
screenshot:
  src:       /img/trivia/trivia_1920.png
  srcset:
    1920w:   /img/trivia/trivia_1920.png
    960w:    /img/trivia/trivia_960.png
    480w:    /img/trivia/trivia_480.png
caption:     Time to test your grade school knowledge.
description: Time to test your grade school knowledge.
links:
  - title:   Launch Project
    url:     https://danspector.io/trivia_game_p5/
  # - title:   Github
  #   url:     https://github.com/inspectordanno/trivia_game_p5
featured:    false
---
This is a quiz about U.S. state capitals. It is coded in P5.js, and loads an external JSON file. For the assignment, the professor required us to use object-oriented programming. I was the only one in the class using JavaScript (most were using Processing, a Java paradigm), so this was a little more challenging for my implementation. JavaScript, unlike Java, is not a class-based programming language. That said, the ES6 class syntactic sugar mapped fairly well and I was still able to emulate the class-based thinking of a language like Java.

## Functionality 

1.	Scoring
    *	A score will be displayed of how many questions the user got right as well as the total number of questions answered so far.
    *	When the game is done, the final score will be displayed.
    *	A face that changes from grin to frown will also keep track of the result of the last answered questions.
    *	Sounds will indicate if the user got the answer right or wrong.
2.	Buttons
    * For each answer, the user will have to click a button that corresponds to Choice A, B, or C.
3.	Game State
    * There are three states.
        * Welcome screen
        * Game playing screen
        * Final result screen
    *	The start/reset button brings the user back to the welcome screen
4.	Miscellaneous technical challenges
    *	Displaying possible answers
        * Two of the answers have to be incorrect and there shouldn’t be any duplicates
        * One answer should be correct
    *	Matching buttons to possible answers
    *	Toggling between the three game states
    *	Displaying active questions
    * Getting the score to display correctly

## Post Mortem

This was the first fully object-oriented project I created from scratch using ES6 classes. I am glad to say I achieved ~95% of the functionality I envisioned. Let me illustrate some of the challenges that I encountered in this project.

First, I ran into a lot of encapsulation issues. I declared a lot of global variables, modified them in object methods, and then found that the variables were not being changed to what I expected. I haven’t really found an answer for this yet, since P5 requires global variables that can be accessed both in setup and draw. Somehow, through trial and error, I managed to overcome the encapsulation issues.
Changing state was also difficult for me. I managed to achieve it by writing a gargantuan if/else statement many levels deep, but this solution was not elegant. 

I was able to map the possible answers to the buttons by using their index values and mapping them to values I set to the buttons. One of the advantages of creating DOM elements is that it is very easy to create individual objects and assign data to them, so this solution worked well for me.

Overall, I definitely learned a lot from this project.  Structuring JavaScript in an object-oriented classes pattern is a very useful paradigm to understand. I used a lot of ```Math.random()``` and comparison logic in this program, which is always good to improve upon. I also learned a lot about changing state through switch statements.

In terms of the core programmatic logic, this project is one of the most complex I have made so far, which belies the simplicity of the game. I also was able to make the canvas somewhat responsive for all screen sizes, which speaks to the power of the P5 width and height attributes.
Initializing sound was far easier than I expected. All I had to do was preload sound files that played depending if the answer was correct or not. 
This project was challenging, but I managed to pull through in the end. 

Thanks to Mark Sivak for all the help.



