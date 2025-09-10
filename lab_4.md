##Lab 4

**Introduction**

For lab 4 we put all the components together!!! Below you can view our final demo with our fully built and programmed Bruce (our robot)!

 <video id="Trajectory" preload="auto" autoplay loop muted="muted" width="642" height="504" src="https://media.github.coecis.cornell.edu/user/13440/files/ccb216a8-8ce2-402c-a950-d7a421a581eb" type="video/mov"></video>

**Objectives**

Implement RF Communication Between Robot and Base Station
Finalize FFT and Override button
Implement Navigation without blocking statements
Implement PID control 
Finalize Treasure Retrieval and Display of Frequencies
Debug until everything flows together

**RF Transceivers**

This task was part of week one. We attached an RF transceiver to both the base station and the robot. We calculated our pipe numbers, so that they all didn’t interact with each other around the class. Then we downloaded the given code to test our build. Everything seemed to work well on the first attempt!

<img width="349" alt="Screen Shot 2022-12-09 at 4 28 30 PM" src="https://media.github.coecis.cornell.edu/user/13440/files/2ca35224-4868-44db-ad1b-210516e2edc7">

**FFT & Override Button**

We spent a little more time on this step and revisited it later on. We had already implemented the override button from lab 3, so that worked well. For the FFT we found the three bins that spiked with 440Hz was played. We found a sum total for those bins that the frequency would need to be greater than. I believed it was 180, but this changed later on. With some help from Professor Bernard, we were able to implement a code that would light up the LED after the first time it heard a frequency of 440Hz or the override button was pressed.

**Navigation**

This was the beginning of the second week. Most of my energy was focused on navigation, while Leo was more focused on PID and FFT. Following Professor Bernard’s sudo code and downloading StackArray.h from Github, I programmed the navigation. In essence, the robot would check the front, right, and left to see which coordinates were free. The coordinates that were free were added to the frontiers stack. If the front was free, the robot would then move forward. Then the front coordinate would be bumped off of frontiers and added to the visited stack. If the front wasn’t free, it would go to the right. Turning and following the same steps. Or if the right wasn’t free, it would go to the left. When the robot reached a deadend with walls or previously visited coordinates surrounding the robot, it would turn around and retrace its steps till it is able to move into the next frontier coordinate. 
Also built into the code was a treasure count. When the count reached 2, it would exit the navigation while loop, stop, and set the LED to blink. 

![IMG_9540](https://media.github.coecis.cornell.edu/user/13440/files/dc69eef7-856d-4e9e-8fdb-43e986571fee)

**PID Control**

Leo took on the task of PID. PID is defined as a “control loop feedback controller that measures error in a system and minimizes that error over time” (lec 19). In essence the robot would read the distances from the right and left wall, then throughout its forward movement would change the speeds of the right and left servos to keep these distances consistent. In our first lab you can see the robot not being able to move in a straight, forward direction. The PID allows the robot to do this while actively making up for the drifting. In a manner that is more directed to our code, the robot would check the right wall distance. If it seemed the right wall was “next to the robot”, then it would base the distances off of that. If it didn’t seem like the right wall was there, but the left wall was “next to the robot”, then the robot would go off that distance. 

**Treasure Hunt**

We returned to lab 2 for this part of the lab. Taking the code from lab 2 and from the RF transceiver’s code we did the first week, we combined the code so that the base station would display the frequency with two decimal places on the base station LED board.

![IMG_1042](https://media.github.coecis.cornell.edu/user/13440/files/614e0d62-2761-4e2f-9f41-700fd900a302)

**Debugging Process**

The biggest component of this lab was the debugging process. First, we revisited the FFT start. The microphone no longer picked up sounds greater than the given threshold for frequency. We never solved this issue, we just ended up lowering the threshold. It worked in the demo and when we were testing it, so it seemed like a good enough solution. 

With the navigation completed, we added the PID script to when the robot would move forward. We perfected the turns with feedback (later on we returned to delay turns, because the feedback wasn’t reliable and the error was up to 15 points off of the actual value). We had forward, right turn, left turn, and turn around functions. 

The navigation function did not work at first and the PID didn’t work when it was incorporated into the navigation. Some of the x and y coordinates were mixed up and there were key words missing, but we solved those issues and got the PID working. 

Next, we had to debug the part of code that checked the visited stack for possible collisions with frontiers. This was difficult. There wasn’t too much documentation on the stackArray.h file, so there was a lot of guess and check on with different techniques. As it turned out you couldn’t copy, empty, and copy a stack more than once. This caused issues because it was supposed to do this task three times every time the robot moved to a new coordinate. I ended up rewriting this function a series of ways, but finally decided to empty the stack into an array and iterate through the array. Then added the contents back into the stack. The code was definitely not the most efficient by the end, but our little robot could make it through a maze and find the treasures!!!


 <video id="Trajectory" preload="auto" autoplay loop muted="muted" width="642" height="504" src="https://media.github.coecis.cornell.edu/user/13440/files/f0b8b6c7-23d2-45a0-b667-7963e66a73c8" type="video/mov"></video>

**Issues Our Robot Had**

Our robot did great if there were two walls around him at all times, except for one or two block spaces where it could mark as frontiers and return to if backtracking occurs. Unfortunately, it didn’t do amazing when there was a more open space. It struggled going in a straight line when there were no walls “next to it”. This would throw off the coordinate positioning of the robot and ultimately lead to its failure of solving the maze. It also struggled with complete turns if there were no walls to judge the turns completion off of. Overall, it was a great experience and project!!
