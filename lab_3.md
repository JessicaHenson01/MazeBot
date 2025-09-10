## Lab 3

**Objectives**

Build High and Low Pass Circuits with LTSpice
Build and Analyze a Simple Microphone Circuit
Build an Amplifier Microphone Circuit 
Test the Amplifier Microphone Circuit with only the Nano
Install the Override Button for the Final Demo 

**Introduction**

The goal of this lab was to implement the circuit and code that will cause our robot to begin navigation for the final demonstration. When a specific frequency is played, our robot will begin navigation and look for the treasures. We also added a failsafe, the override button, in case the robot doesn’t catch when the note is played. We can press this button and the robot will start navigation. 

**Building High and Low Pass Circuits with LTSpice**

To start off the lab, we used LTSpice to build and analyze some circuits. The first circuit we simulated was a low pass circuit. 

Low Pass Circuit:

<img width="788" alt="Low" src="https://media.github.coecis.cornell.edu/user/13440/files/97cae94b-0313-4ee9-aa24-74bb8cfe655c">

This circuit takes in a sinusoidal frequency. It allows lower frequencies through, while blocking higher frequencies.

LTSpice Plot for Low Pass Circuit:

<img width="542" alt="Low Pass Filter" src="https://media.github.coecis.cornell.edu/user/13440/files/5ab5d936-4f3f-4dd0-83b7-4fdc7c6d5c55">

From this plot we can see how frequencies less than 1 KHz pass through the circuit without too much depreciation. After the 1KHz mark, the graph drastically slopes downward.

LTSpice Plot for Low Pass Circuit showing Cutoff Frequency:   

<img width="546" alt="Low Pass Filter - Cut off frequency" src="https://media.github.coecis.cornell.edu/user/13440/files/f1696ac6-07f8-4844-a26b-41039cc71106">

Here we can see the cutoff frequency is located around 2.4KHz, that is when the slope of the graph seems to become constant.

The second circuit we simulated was a high pass circuit.

High Pass Circuit:

<img width="785" alt="High" src="https://media.github.coecis.cornell.edu/user/13440/files/abaf3b0c-c31a-48d5-a5af-02e2f15d779a">

This circuit also takes in a sinusoidal frequency. The difference is a high pass circuit allows for higher frequencies through, while blocking lower frequencies.

LTSpice Plot for High Pass Circuit:

<img width="546" alt="High Pass Filter" src="https://media.github.coecis.cornell.edu/user/13440/files/860b840f-f45b-4c7c-bbb8-c9abe1331c3e">

From this plot we can see how frequencies less than 1 KHz have an increasing slope, whereas frequencies higher than 1 KHz have a more horizontal slope. 

LTSpice Plot for High Pass Circuit showing Cutoff Frequency:

<img width="542" alt="High Pass Filter - Cut off frequency" src="https://media.github.coecis.cornell.edu/user/13440/files/b1b2cf65-85b3-40b5-9772-01d678ae891c">

Here we can see the cutoff frequency is located around 607Hz.

**Build and Analyze a Simple Microphone Circuit**

The next part for our robot is the microphone, which will pick up sound for the Nano to analyze in order to determine what frequencies are present in the noise. 

Simple Microphone Circuit:

![Screen Shot 2022-11-05 at 5 48 09 PM](https://media.github.coecis.cornell.edu/user/13440/files/b703b678-bbba-49fd-a32f-ae3fc6442bf0)

First we had to convert the signal from analog to digital. We did this through a Matlab code. We had the computer play a note at 500 Hz and then compute a graph to display the signals picked up by the microphone. 

500 Hz Signal Graph:

![Screen Shot 2022-11-05 at 5 48 04 PM](https://media.github.coecis.cornell.edu/user/13440/files/e89f4bf6-d46c-4a44-a493-144151d78dc2)

We can see peaks at 500 Hz, 1000 Hz, and 1500 Hz. These are the harmonic frequencies, therefore multiples of 500. 

**Amplified Microphone Circuit**

In order to remove the noise from analysis, we need to improve the circuit. This circuit will amplify the 500 Hz signal above the rest, hence the name “amplified circuit”. 

Amplified Microphone Circuit:

![Screen Shot 2022-11-05 at 5 47 58 PM](https://media.github.coecis.cornell.edu/user/13440/files/e93f5d5f-d2df-4307-af83-01c937def9d6)

Using the matlab code again, we played a 500 Hz signal and analyzed the results. 

500 Hz Signal Graph:

![Screen Shot 2022-11-05 at 5 47 51 PM](https://media.github.coecis.cornell.edu/user/13440/files/f2e06dd2-733f-4214-a08a-7ca7b967a237)

From the graph above, we can see how well the circuit did its job. We still picked up harmonics, but we the noise significantly reduced, we can tell that 500 Hz was the starting frequency.

**Coding the Nano to perform a Fourier Analysis without Matlab**

The graph above looks great, but it doesn’t really work to have a **mobile** robot hooked up to a computer in order for the Fourier Analysis to return a frequency. This means we need to code the Arduino to perform a fourier analysis. In order to do this, we used  the FFT arduino library. After completing the code, we were able to get about 256 discrete data points. Graphing these points, we were able to identify the starting frequencies. 

500 Hz Signal Graph:

![Screen Shot 2022-11-05 at 5 47 38 PM](https://media.github.coecis.cornell.edu/user/13440/files/ddf81464-5506-4be7-8ffd-a403ef25963a)

700 Hz Signal Graph:

![Screen Shot 2022-11-05 at 5 47 31 PM](https://media.github.coecis.cornell.edu/user/13440/files/9ea343b3-adbe-4838-a5a2-15f2cfad77c2)

900 Hz Signal Graph:

![Screen Shot 2022-11-05 at 5 47 24 PM](https://media.github.coecis.cornell.edu/user/13440/files/78f9f5bb-8c8f-41d5-a018-7e1267a5865c)

The FFT puts signals into bins, instead of just showing the frequency. We can see the largest peaks around 53 to 54 for the 500 Hz graph, 72 to 75 for the 700 Hz graph, and 95 to 96 for 900 Hz graph. This means to find the frequency we will take the bins with the highest frequency and divide by around 10. Now we can use this to analyze input frequencies, so the robot will know when to start navigating.

**Override Button**

The final part of the lab was to wire an override button. This button will cause navigation to start if the microphone does not pick up on the frequency when it is played. This was a very simple circuit. We had a little trouble with finding the right input pin on the Nano, but with a little trouble shooting we got it figured out.

**Conclusion** 

Throughout this lab we got to apply mathematical concepts such as fourier analysis in a real world application, along with building and analyzing various types of circuits. We now have all the parts of the robot in order to set up for the final demonstration. Lab 4 will cover putting all the pieces together!
