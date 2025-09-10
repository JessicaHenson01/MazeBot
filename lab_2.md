## Lab 2

**Objectives**
  - Build a simple IR light detection circuit
  - Build a simple IR light emitting circuit
  - Test and characterize your IR detection circuit
  - Build two IR light detection circuits on robot
  - Build display component of the base station

**IR Light Detection Circuit**
To begin the lab, we built an IR detection circuit on our robot that will be used later in the class to detect treasures throughout the maze. We added circuitry with the current coming from the Arduino and moving through a resistor. When the transistor detects light, it pulls the analog pin high while otherwise the pin is pulled low. Through this process, we are now able to detect when there is IR light with zeros and ones. 

<img width="185" alt="Screen Shot 2022-10-16 at 5 23 32 PM" src="https://media.github.coecis.cornell.edu/user/13440/files/47b3b421-df3a-4cdc-85da-3547f86061ad">

**IR Light Emitting Circuit**
The next step was to test our light detection system. In order to complete this task, we had to build an IR light emitting circuit. On a separate breadboard from our robot, we connected a 60 ohm resistor to an input voltage and an IR LED, with the positive side connected to the resistor and negative side connected to ground. Using the Signal Generator, we had an input voltage of 1.2V with the current flowing through the LED being 20 mA and the frequency set to 1kHz. 

Next, Leo and I confirmed that the signal generator was generating a sinusoidal waveform with the oscilloscope by checking the power through the IR light emitting circuit. 

**Testing our IR Light Detection Circuit**
It was finally time to see if our IR Light Detection Circuit could detect IR Light. We connected the oscilloscope to the phototransistor on the robot. This way we could see if the same square wave fed into the IR Light Emitting Circuit was being detected  by our IR Light Detection Circuit. When we were able to see the wave successfully, we could move onto testing through the Arduino. By writing a few lines of code, we could calculate and display the frequency of the flashing IR light being detected by our phototransistor. We successfully detected a frequency of 1 kHz and 9kHz, showing that the circuit could detect other frequencies. Our measured values were slightly below the frequency provided by the function generator because we ended up using a 62 ohm resistor instead of a 60 ohm resistor. In our code we provided a measurement of ambient light, in order to account for the amount of light exposed when the phototransistor measured the blinking IR LED.

**Building Two More IR Light Detection Circuits**
To insure our robot would be able to detect treasures in all directions, we added two more phototransistors. One was attached to the front of the robot and the other on the opposite side from the first transistor. When incorporating this into code, we will switch between transistors as our robot moves through the maze, allowing for the robot to detect treasure. 

1 kHz Frequency show on Oscilloscope

![1kHz_osillascope_lab2](https://media.github.coecis.cornell.edu/user/13440/files/e26822ef-60da-488c-b27f-dfce55963873)

9 kHz Frequency show on Oscilloscope

![9kHz_Osillascope_lab2](https://media.github.coecis.cornell.edu/user/13440/files/12cb818f-8110-44fc-a010-d7e3af2e6d4c)

1 kHz Frequency shown thorugh Ardino

![1kHz_lab2](https://media.github.coecis.cornell.edu/user/13440/files/1f40a1e0-e9b8-42d5-88aa-05debf44f1b1)

9 kHz Frequency show through Ardino

![9kHz_lab2](https://media.github.coecis.cornell.edu/user/13440/files/30279b5a-6b7c-4254-ac46-e79b2e4fe22c)


**Building the 7-Segment Display Circuit**
The second day of the lab we built the display component of the base station on a separate breadboard. We used the same breadboard as the IR light emitting circuit. The display component consists of a 7-segment display powered by 16 pins. Four of these pins select which digit to light up and eight of these pins select which segment to light up. Below is a picture of the configuration. 

<img width="286" alt="Screen Shot 2022-10-16 at 5 23 17 PM" src="https://media.github.coecis.cornell.edu/user/13440/files/7356eef1-64a6-44de-bf12-52b769396bab">

To minimize the number of pins used on the base station’s Nano, connect each digit to a pin and shift through rapidly. This way it will appear that we are lighting all the digits together. 

Leo and I didn’t seem to run into trouble throughout this part of the lab. To display numbers over 10000, we placed a decimal at 10.00. In this situation the units change from unit to kilo-unit. The only issue we encountered is displaying larger numbers, over 40000. We realized we needed to set the numbers to long ints instead of just ints. 

This part concluded our second lab. We were able to complete all parts during our given lab sessions. The first day we completed our treasure detection component of the robot and the second day we completed the base station display to show detected frequencies of the treasures.

