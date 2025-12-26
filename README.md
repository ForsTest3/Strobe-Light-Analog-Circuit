# Strobe-Light-Analog-Circuit
Analog circuit using a NE555 IC to flicker LEDs at customizable rates with potentiometers. The entire circuit is powered by a 9V alkaline battery. <br/>

<img width="300" height="721" alt="image" src="https://github.com/user-attachments/assets/57a52e68-895c-40d6-9b2c-bdc6c7f6e26d" />

This is the first circuit implementation. The 900k ohm potentiometer allows for the brightness of the LED to be adjusted. It is made in such a way that when it is turned close to either end, the brightness is close to maximum, and when the potentiometer is turned close to center, the LED get's dim or doesn't show any light at all.

We want to modify this, so that ideally it will only be bright on ONE side, and that ideally the potentiometer value be swapped to something smaller (like 100k or 10k).

As for why we chose a 10uF capacitor instead of say a 100uF capacitor, it is because the higher the value the capacitor is, the less sensitive the LED display is. This is because the capacitor charge and discharge will take longer as it can now store more. Due to the voltage change being smaller as Vcc is constant, having it store 1/3Vcc and 2/3Vcc will take longer for the larger value capacitor. 

Now, one may wonder whether a 1uF capacitor could be used, and in this case it definitely could. However, the potentiometer values would require adjusting, as a 1uF capacitor would be much too sensitive.

Likewise, with some potentiometer values there are cases that result in the LED not lighting up while trying to obtain a very high frequency of blinking.

# Theory and decisions behind pinout placements
<img width="600" height="279" alt="image" src="https://github.com/user-attachments/assets/9b49348d-215b-4eff-a162-9608d2c26ac6" /><br/>

As shown in the picture above, we have trigger (pin 2) and threshold (pin 6) connected to each other directly with a GREEN wire. No resistor is needed since we do not want voltage drop to affect the 2/3Vcc and 1/3Vcc for each comparator in the 555 timer. Next, we have reset (pin 4) and Vcc (pin 8) connected, this is so that the timer can constantly operate without any random resets occuring.

For discharge (pin 7) and Vcc (pin 8) being connected through resistors, this is so that discharge can occur. As such the resistors used here prevent component damage from overheating, and the potentiometer allows for the duty cycle and frequency to be altered.

<img width="800" height="445" alt="image" src="https://github.com/user-attachments/assets/c75aa674-0e2f-431d-9106-f576fbede37c" /><br/>
The connection of the two allows for the general case shown in the I/O table image, giving the general pulse width on and off functionality for the 555 timer. This is shown in the circuit below as such.

<img width="782" height="366" alt="image" src="https://github.com/user-attachments/assets/67f311a8-c2c1-4d6f-85b7-d8ed320b2da3" />


<img width="798" height="422" alt="image" src="https://github.com/user-attachments/assets/1d012e24-c07c-49d2-bd87-19c463be594d" /><br/>

<img width="300" height="721" alt="image" src="https://github.com/user-attachments/assets/dc8b1b64-4159-4cfa-a0ee-1fc3b8950063" /><br/>


<img src="https://github.com/user-attachments/assets/c97514b8-139f-48ea-9cce-27dd3798662c" width="500" /><br/>

This is the second circuit implementation. It can be seen that two more potentiometers are added, another 900k potentiometer and a 100k potentiometer. The 2nd 900k potentiometer determines the pulse width of the duty cycle, and can customize how long it stays ON or OFF for each pulse. The 100k potentiometer determinse the period. This will be further updated so that ideally they are all same value potentiometers unless required to be different.

Image theory credits https://www.youtube.com/watch?v=iwbGccGU4io <br/>
Circuit inspiration credits https://www.youtube.com/watch?v=euiDv51VVt4 <br/>
I/O table and 555 pinout credits https://www.youtube.com/watch?v=oZzjmAbyyIQ&t=315s <br/>
Theory calculation credits https://www.youtube.com/watch?v=gTn_HmzXYLo
