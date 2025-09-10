## Lab 1 Overview and Results

**Introduction**

For Lab 1 in Intelligent Systems (ECE3400), Leo and I built and programmed a robot that could navigate through a pre-designed course. There were three parts. Part one consisted of the build and programming of basic movements, such as forward, backward, 90 degree turns left and right, and 180 degree turns. Part two consisted of attaching the ultrasonic sensors and programming them to read distances between the robot and the next solid object in front, to the right, and to the left of the robot. Part three consisted of navigating the course using the ultrasonic sensors. 

**Part 1: Build and Servo Demo**

First step was to build the robot. We were provided with the materials listed in the handout and followed the instructions to build the frame and attach the servo motors. There were two wheels on the side connected to the servo motors powering movement and one caster wheel at the rear to keep the frame balanced. One top, we placed two sets of batteries, a 9V battery in the rear and a group of three AAs in front. Later the three AAs were replaced with four AAs to provide more power. The batteries were attached with Velcro to provide easy access if the batteries need to be changed. After completing the frame, Leo and I got checked off by a TA for our build. 


<img width="257" alt="Screen Shot 2022-09-25 at 9 02 55 PM" src="https://media.github.coecis.cornell.edu/user/13440/files/1735bb70-8baf-4d7d-9879-a3506a4843f8">

 
I did most of the first step, while Leo completed the second step. We found it helpful to split up the tasks given that four hands didn’t mesh well with all of the small parts.

Second step was wiring and attaching the bread board. First we placed the Arduino (Nano) on the end of the board and taped over the Nano. We got the tape job checked off by a TA and we moved on to programming. 

Third step was connecting the Nano to Leo’s computer. We used a USB cable to manually connect the device to the computer and then set the IDE to connect with the “Arduino Nano Every”. After downloading the device, it connected and we ran the blinking light code downloaded from Canvas to make sure the Nano was working properly. 

Fourth step was wiring the servo motors to the Nano. This went smoothly and we began programming. Using the Servo.h library and downloading the Lab1_Servo.ino file, we redesigned the movement to follow the checkoff servo demo list. 

Finally we were able to run the robot. After the robot followed the instructions, we went to get checked off. This was when we found out the caster wheel was supposed to be in the rear and not the front. Accounting for this mistake, we went back and changed the numbers throughout the code so that the correct side faced north. We were able to get checked off by a TA. This step concluded the first session we spent in the lab. 


  <video id="Trajectory" preload="auto" autoplay loop muted="muted" width="642" height="504" src="https://media.github.coecis.cornell.edu/user/13440/files/9d693b38-9e29-4a51-a27e-99c7bc749ceb" type="video/mov"></video>



**Part 2: Ultrasonic Sensors - Measure Distances**

The second part consisted of attaching, programming and testing the Ultrasonic Sensors (US). We attached three US in preparation to help navigate the maze and identify the walls and distances. One US was attached to the front on the 9V battery. Another US was attached to the left side, plugged directly into the bread board. The final US was attached to the right side, also plugged directly into the bread board. We attached the triggers to the same Arduino pin and each echo to a unique pin. Using the US_EnableOnDemand_Canvas.ino. Leo and I used the US to detect objects surrounding the robot. After making sure the sensors were all working, we got checked off by a TA and moved to the exciting part. 


![IMG_9176](https://media.github.coecis.cornell.edu/user/13440/files/79bd40e1-36bf-4946-9a9b-e075c1323be8)


**Part 3: Ultrasonic Sensors - Navigation**

In the final part of the lab, Leo and I programmed the Nano so that the robot could navigate around the predetermined maze. We decided to go through the maze step by step with each step triggered when the front sensor detected a wall within 10cm of the robot. Then we programmed the robot to commit the final step after the front sensor no longer detected anything in front of the robot. That way it knew all steps were complete and exited from the Arduino loop. 

After attempting the maze, our wheels no longer moved at the same speed. So we went back to the code and did a lot of trouble shooting. By changing the speeds for the wheels throughout our code, we finally got our robot to go forward, backward, and make turns within reasonable accuracy. 

Leo and I did have to return to the lab another time after our scheduled lab time, in order to complete the trouble shooting. This was when a TA let us know the wiring to the batteries was incorrect. We rewired the bread board so that the correct amounts of power went to each component and then returned to troubleshooting. After a while we found the right speeds for each wheel. Leo and I completed the maze, making sure to record the video you can now view below.

**Expected Path**


<img width="380" alt="Screen Shot 2022-09-25 at 9 30 01 PM" src="https://media.github.coecis.cornell.edu/user/13440/files/bc1611db-9d56-46af-996f-ded6ae14e3da">


**Final Results**


  <video id="Trajectory" preload="auto" autoplay loop muted="muted" width="642" height="504" src="https://media.github.coecis.cornell.edu/user/13440/files/c6d1d635-23d5-4837-a096-471c9cc2f090" type="video/mov"></video>


**Serial Monerator Outputs**

![IMG_9174](https://media.github.coecis.cornell.edu/user/13440/files/a21389e5-619f-4b5e-9d7c-3b9be6da4e13)
![IMG_9175](https://media.github.coecis.cornell.edu/user/13440/files/31c47284-ba19-41b6-83d4-c938989b6415)



