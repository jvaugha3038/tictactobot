# tictactobot

## Table of Contents
* [Table of Contents](#TableOfContents)
* [Goal](#Goal)
* [Planning](#Planning)
* [CAD](#CAD)
* [Code](#Code)
* [Building](#Building)
* [End Result](#EndResult)
* [Problems](#Problems)
* [Reflection](#Reflection)
---
# `Goal`
The overall goal of this assignment was to create a robot arm, with at least two joints, to solve a problem. The problem we came up with is that tic-tac-toe sucks because it's always a draw, so we made a robot that will cheat in tic-tac-toe.

# `Planning`

## Requirements
The most important requirement to watch out for is your range of motion. Your robot may need to have far reach in a small area in front of it, or have less reach but all around it. Make sure to plan for the range of motion you need your robot to have. An important aspect of this is servo choice. 180 servos are small and somewhat accurate, but have a very limited range. Continuous servos can go for as long as they like, but in a very inaccurate and unpredictable way. Steppers will be your best choice if you need continuous motion with accurate positioning, but they are big and heavy, so plan accordingly. 
For this project the robot just needs to be able to move in a square shape in front of it. We went with a standard size 180 servo to spin the arm back and forth, and a micro 180 servo to extend the arm. This micro servo was connected to a 3:1 gear system which allowed it to extend the whole length of the board in under 180 degrees of rotation, thanks to the math we did in our planning.
Another thing related to the servos is how much force they can exert. Especially when working with micro servos, you have to be aware of their weight limits. This project was luckily very light on the arm, but if you’re going to be putting any real strain on the servos you should do the math to make sure they can handle it.
![image](https://github.com/jvaugha3038/tictactobot/assets/112961338/d77939f4-6d30-4ff8-927b-d7cd59fc573f)
If you’re ever struggling to think of things your robot needs to do (or even if you aren’t), I recommend looking back at the purpose of your robot and thinking about how you can achieve these things. This helped us realize that we hadn’t planned on how we would detect the pieces on the board (we wouldn’t want a blind tic-tac-toe robot would we?). Luckily for us, this was relatively early on, and we were given the idea of an infrared sensor by Mr. Helmstetter. This sensor can measure how reflective an object is by shining an invisible light on it, and by using different materials for our X’s and O’s, we can use it to differentiate between the board and those two.

## First Sketches
The design of our robot changed a lot during the first few days of planning. We originally planned to have a big rotating pole pinion which the arm would scale up and down while extending. It was a little ambitious, and after realizing that we would have to use multiple stepper motors, all reliant on a flimsy piece of acrylic, we decided to switch it up. The design we settled on was a cylindrical arm. We would have an arm that could extend outwards and be rotated. (see image on right). But you may have noticed that the arm depicted there can move up and down, and given that our bot has to be able to pick up pieces, we need some vertical movement. But given our sketches so far, there was no way to make a reliable elevation system that wouldn’t risk the stability of the arm. We came up with the idea of attaching a magnet to the end of the arm which could be raised and lowered to pick up pieces. This seemed much simpler than our original ideas of claws that would pick up the pieces.

# `CAD`
https://cvilleschools.onshape.com/documents/9f7a2ab06042344ad68077a3/w/577d4a05bb440caa0ac4fef6/e/6a6642626d928ba19f00adb1
## Proof of Concept
Our proof of concept was planned to be a small-scale rack and pinion gear that would represent the arm of the robot (A.K.A the extendo part), and the device we would use to pick up the pieces (the pick-uppy part). However, we did not get any string or magnets in time for the proof of concept, so we just created the small extendo arm.

# `Code`
(check the file for now, we'll post it here when its done)

# `Building`
## Pieces
The pieces were always going to be the standard X’s and O’s, so the only question we had to ask ourselves was what acrylic we should use to make the tops. Since we are using an infrared sensor to detect piece locations on the board, we decided to use a bronze-looking color for the O’s, as it is easy for the sensor to see. The other color didn't matter as much, so we went with gray because it looks nice. 
Each piece has a magnet in it.
In hindsight, having the black base of the X's be a circle, like it is for the O's, would likely be better, so the robot can actually place them in the slots on the board.
## Board
The board design is similar to the pieces, having a black base and a colorful top. The handle-looking things on the top fit around the robot itself, so the board is always stable and the robot can navigate consistently. The purple piece on the side is where the robot grabs pieces to place on the board. The blue squares aren't for anything in particular.
![image](https://github.com/jvaugha3038/tictactobot/assets/112961338/30af98e3-6448-4cf5-84fa-e925a3a747ba)
## Box and Extendo Arm
The box is pretty simple; it's a box with a servo in it, which spins the arm on top of the box. It can also hold the metro M4, a battery pack, and all of the wiring. It has a handle on the back of it so the batteries can be changed out.
The arm is a rack and pinion gear set that helps position the magnet thing along with the servo in the box. Note that one of the gears is 3D printed.
It was originally 2 big gears connected to 3 small gears to create the gear ratio.
![image](https://github.com/jvaugha3038/tictactobot/assets/112961338/6bdf4a24-5df9-48dc-8946-23744670ae74)
## The Magnet thing a.k.a the Pick-Uppy Part
This part is responsible for picking up and dropping pieces, and it's attached to the arm. The servo lowers a magnet attached to a piece of string, which then connects to the magnet in a piece. Then, it can raise the magnet, disconnecting the piece and letting it fall onto the board.
![image](https://github.com/jvaugha3038/tictactobot/assets/112961338/7e5bf1fa-a4a1-4e7e-ad3a-5fa31a9c543d)
## The Whole Thingy
![image](https://github.com/jvaugha3038/tictactobot/assets/112961338/8314c021-9074-407b-83d8-fbfc39e086c0)

# `End Result`
The final product is, admittedly, not exactly what we had hoped for. Yes, it can pick up pieces and place them (with some difficulty), but it is also not great at seeing pieces on the board. This means that it occasionally will completely miss a piece, and place one on top of it. This does mean that we can say "Oh it was supposed to cheat anyway" and move on, but besides that, the robot itself is very creaky for some reason. This might just be because we left it in the bin for a while to work on the other projects. 

# `Problems`
## Big problems
* The gears in the arm were inconsistent.
  * We 3D printed one of them to solve the problem.
* The servo powering the rack and pinion kept destroying itself (tried to spin too hard)
  * We used the servo horn instead of screwing the gear directly onto the servo.
* Servo responsible for rotating the arm could move around in the box.
  * Added a small 3D printed part to the front of the box that allows the servo to be screwed in place.
* We waited about 2 weeks to get string and magnets
  * yeah that one is just our fault, get the stuff early next time
* String is flimsy and keeps breaking.
  * Make the servo spin slower (and hope for the best)
## Less severe problems
* Servo responsible for rotating the arm wasn’t aligned properly.
  * Added an offset into the code to account for this.
* Infrared sensor wires interfered with the box when fully retracted
  * We turned it around.
* Can't screw the infrared sensor in place after turning it around.
  * Completely unnecessary. 
* The top part of the arm interfered with the gears
  * We made cool looking fillets on it.
* Wires cross over the board
  * Didn't have time to do this, but we could have zip-tied the wires to other wires to keep them out of the way.
* The pieces get caught on the board when picked up from the zone on the side of the board.
  * We can stack 2 of the blue squares (or really any acrylic things)

# `Reflection`
