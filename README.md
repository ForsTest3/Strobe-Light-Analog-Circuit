# Strobe-Light-Analog-Circuit
Analog circuit using a NE555 IC in astable configuration to flicker LEDs at customizable rates with potentiometers. The entire circuit is powered by a 9V alkaline battery. <br/>

<img width="300" height="721" alt="image" src="https://github.com/user-attachments/assets/57a52e68-895c-40d6-9b2c-bdc6c7f6e26d" /> Figure 1 <br/>

This is the first circuit implementation. The 900k ohm potentiometer allows for the brightness of the LED to be adjusted. It is made in such a way that when it is turned close to either end, the brightness is close to maximum, and when the potentiometer is turned close to center, the LED dims down. However, we want to modify this so that ideally it will only be bright on ONE side. To implement this in further circuits, we can try using a diode.

A 10µF capacitor was selected over a 100µF alternative to allow responsive LED brightness control. As larger capacitance values increase the RC time constant, it slowis the capacitor's charge and discharge rates. Since the 555 timer's trigger thresholds (1/3Vcc and 2/3Vcc) are fixed, a larger capacitor takes significantly longer to reach these voltages. This excessive filtering would make the LED's brightness changes feel sluggish and less precise when adjusting the potentiometer.<br/>
<img width="300" height="721" alt="image" src="https://github.com/user-attachments/assets/dc8b1b64-4159-4cfa-a0ee-1fc3b8950063" /> Figure 1 annotated <br/>
Now, one may wonder whether a 1uF capacitor could be used, and in this case it definitely could. However, the potentiometer values would require adjusting, as a 1uF capacitor would be much too sensitive. 

Likewise, with some potentiometer values there are cases that result in the LED not lighting up while trying to obtain a very high frequency of blinking.

# Theory and decisions behind pinout placements
<img width="600" height="279" alt="image" src="https://github.com/user-attachments/assets/9b49348d-215b-4eff-a162-9608d2c26ac6" /> [4] NE555 Timer Pinout Diagram <br/>

As shown in the picture above, we have trigger (pin 2) and threshold (pin 6) connected to each other directly with a GREEN wire. No resistor is needed since we do not want voltage drop to affect the 2/3Vcc and 1/3Vcc for each comparator in the 555 timer. Next, we have reset (pin 4) and Vcc (pin 8) connected, this is so that the timer can constantly operate without any random resets occuring. 

For discharge (pin 7) and Vcc (pin 8) being connected through resistors, this is so that discharge can occur when the base is given enough voltage in the BJT. As such the resistors used here prevent component damage from overheating, and the potentiometer allows for the duty cycle and frequency to be altered. (As shown in the 555 timer image). <br/>
 
<img width="727" height="400" alt="image" src="https://github.com/user-attachments/assets/a9f3fd03-95f2-4187-9d05-816f2ea36fed" /> [2] Exterior Configuration for Astable <br/>
<img width="800" height="445" alt="image" src="https://github.com/user-attachments/assets/c75aa674-0e2f-431d-9106-f576fbede37c" /> [4] NE555 interior BJT orientation <br/>


As for the connection between threshold (pint 6) and discharge (pin 7), this allows for primarily changing the period (duty cycle changes a bit too but its very small in comparison to period change). This is because threshold is a comparator input, so when we have it connected to discharge, threshold input goes through the flip-flop and then triggers the base of the BJT once there's enough voltage, and this allows for the direct relationship between input and discharge, hence determining the period.
The connection of the two allows for the general case shown in the I/O table image, giving the general pulse width on and off functionality for the 555 timer. This is shown in the circuit below as such.

<img width="782" height="366" alt="image" src="https://github.com/user-attachments/assets/67f311a8-c2c1-4d6f-85b7-d8ed320b2da3" /> [A] <br/>


<img width="798" height="422" alt="image" src="https://github.com/user-attachments/assets/1d012e24-c07c-49d2-bd87-19c463be594d" /> [4] <br/>

# Second Circuit Implementation
<img src="https://github.com/user-attachments/assets/c97514b8-139f-48ea-9cce-27dd3798662c" width="500" /><br/>

Ttwo more potentiometers are added, another 900k potentiometer and a 100k potentiometer. The 2nd 900k potentiometer determines the pulse width of the duty cycle, and can customize how long it stays ON or OFF for each pulse. The 100k potentiometer determinse the period. This will be further updated so that ideally they are all same value potentiometers unless required to be different.

<img width="669" height="840" alt="image" src="https://github.com/user-attachments/assets/742bb47a-0f4f-4952-a780-7fba1219de35" /><br/>
In the case where we want more than one LED blinking at the same rate as the original LED, we can set it so that it is in series. If set in parallel, only some LEDs will light up. This is because in parallel, current is distributed, while voltage is the same. So while one voltage drop may activate one LED, it may not activate the others which results in uneven lighting. However, having LEDs in series is simply a temporary solution, as if you stack more than 3 LEDs, the voltage drop across the LEDs starts to result in the lighting becoming too dim.

![IMG_3261](https://github.com/user-attachments/assets/b489ccf2-dd0e-4c49-8bea-d6fe16edfb81)
As such, you can get them to alternate in this configuration, however the brightness is not easily adjustable. This is due to voltage limitations, and that in adjusting the brightness of the first LED, it will also adjust the brightness of the 2nd LED as a result.

One other aspect taken into consideration is whether a non-polarity capacitor could be used. In terms of having a circuit that works, yes it could be used, but it will not achieve the blinking capability that the polarity capacitor can do. As a result, it will simply show the two LEDs as on, and the potentiometer connected pin 7 and pin 8 will work as a mode slider, making it that either one LED will be brighter or the other LED will be brighter.

# Third Circuit Implementation
![IMG_3264](https://github.com/user-attachments/assets/cb1ab372-8628-4bf7-962c-544e2e20f7f0)
By adding a potentiometer, this instead makes it such that

# Fourth Circuit Implementation
<img width="600" height="934" alt="image" src="https://github.com/user-attachments/assets/2bb101a4-a18c-4835-9917-ff5a3177059e" /><br/>
In this configuration, this results in the red LED allowing change in brightness with the bottom right 100k potentiometer, meanwhile maintaining the brightness of the green LED closest to the BJT.

<img width="400" height="622" alt="image" src="https://github.com/user-attachments/assets/eb8ca181-2995-411b-aaa0-a47e8cea53bc" /><br/>
To verify correctly, we also test with matching LEDs for each respective port. Through this we are able to have it so that one of the LEDs blink and decay with adjustable brightness, while the other LED blinks as pulses, and stays the same brightness. <br/>

<img width="500" height="856" alt="image" src="https://github.com/user-attachments/assets/96c2ec1c-a54b-4fc8-9876-22c223f607d7" /><br/>
Here we obtain a circuit that allows for both LEDs to be modified in brightness, while also having alternating blinking patterns. However, the top potentiometer can dim the top red LED but only a bit, while the bottom potentiometer can dim both of the LEDs, dimming the top LED first and then the bottom LED. This is mainly due to more current entering the BJT emitter, so that it can come out the collector when the base takes enough input. As a result, the bottom LED stays powered on longer than the top LED despite it requiring current into the base from the output of the 555 timer.

# References
[1] Image theory https://www.youtube.com/watch?v=iwbGccGU4io <br/>
[2] https://www.youtube.com/watch?v=APghHcA-MOI <br/>
[3] Circuit inspiration https://www.youtube.com/watch?v=euiDv51VVt4 <br/>
[4] I/O table and 555 pinout https://www.youtube.com/watch?v=oZzjmAbyyIQ&t=315s <br/>
[5] Logic Gates https://www.youtube.com/watch?v=sTu3LwpF6XI <br/>

Theory: <br/>
[A] Math equations https://www.youtube.com/watch?v=gTn_HmzXYLo <br/>
[B] https://www.youtube.com/watch?v=OsQObXu4TSA&t=147s <br/>
[C] https://www.youtube.com/watch?v=sWbSeJmUFfw
