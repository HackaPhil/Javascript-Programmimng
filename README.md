# Javascript-Programmimng

**Winter Programming Summative**

Original Sketch: https://www.openprocessing.org/sketch/652448

This sketch is a simple game where the aim is to reach point goals in ten consecutive rounds by making balls expand in a chain from the point where you click. Clicking causes a large circle to appear which is worth no points by itself, but any small bouncing ball that touches this original will grant 100 points; any ball that touches a 100 point circle will grant 800 points, and so on. The longer the chain reaction, the greater the numnber of points gained. 


Code Structure
==============

Having only discovered the ability to access the source code of the sketch after I'd finished my own version, my code differs in many ways to the original, but I was also surprised to see some clear similarities, which should be obvious considering it's an almost exact replica made in a slightly different programming language. 

The code starts with a barrage of variables, including two long pre-set arrays for circle scores and target scores for rounds in order from lowest to highest. Two other variables will become arrays; circles and bigCircles. A for loop (the second loop inside 'function init()') will be used to fill the 'circles' array with bouncing balls using the 'Circle' class, the quanitity of which are calculated by adding 5 to the product of the round number multiplied by 5 (10,15,20,25 etc.). The bigCircles array has empty slots equivelant to the number of balls in 'circles' plus one. The extra slot is for the big circle created upon the user's click, and the rest are filled as ball expansions occur. This second array allows the 'expand()' method in the 'Circle' class to work, the function of which is to expand the balls when they touch another expanded ball.

The setup function is short, as it calls another function called 'init()' which contains the code that would otherwise be in 'setup()'. The purpose of 'init()' is to allow the game to be reset when a round ends, or the game finishes at round 10. Several conditionals can be found in 'function draw()' and 'function mousePressed()' which call 'init()' as well as make necessary variable modifications, for example increasing 'roundNum' by 1, which in turn increases the number of balls by 5 upon restart. 

The p5 draw() function contains all the growing and shrinking mechanisms of the circles, as well as the format of the background and scoresheet. The 'mousePressed()' function below that has all the possible outcomes of a user's click, from initiating a round to making the starter circle appear. Finally, the 'Circle' class is defined, taking a large number of parameters in its constructor. 

About the 'Circle' class
========================

When this class is called (look to 'function init()' for an example), it takes its RGB values as its first three parameters, followed by its coordinates and its inital direction. Next, 'id' is a parameter I used to identify a particular circle in the 'circles' array. As my circles are called in a for loop, their id is 'i', therefore they can be found in circles[i], and eventually some of their details are stored in bigCircles[i]. The 'otherCircles' parameter is set to bigCircles, and I use it in my expand() method. 'activeTime' is used to track how long a circle has been expanded for so it knows when to disappear, 'status' is so it knows whether its growing or shrinking, and 'circleScore' will be the score assigned to the circle when it expands. 

The expand() function calls on some variables that are defined outside the class, and is only really necessary for the Chain Reaction game. It can be removed as a whole if the class is reused, along with relevant parameters such as otherCircles, activeTime, status and circleScore. 

Game Tips
=========

- As you get more points with a longer chain, avoid clicking anywhere near the middle.
- Try to pick out the slower-moving balls first.

License
=======



