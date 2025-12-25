# Strobe-Light-Analog-Circuit
Analog circuit using a NE555 IC to flicker LEDs at customizable rates with potentiometers. The entire circuit is powered by a 9V alkaline battery. <br/>
Image credits go to CircuitBread https://www.youtube.com/watch?v=iwbGccGU4io <br/>
Circuit inspiration credits go to Skosan Electronics https://www.youtube.com/watch?v=euiDv51VVt4 <br/>
I/O table and 555 pinout credits go to element14 presents https://www.youtube.com/watch?v=oZzjmAbyyIQ&t=315s <br/>

<img width="300" height="721" alt="image" src="https://github.com/user-attachments/assets/57a52e68-895c-40d6-9b2c-bdc6c7f6e26d" />

This is the first circuit implementation. The 900k ohm potentiometer allows for the brightness of the LED to be adjusted. It is made in such a way that when it is turned close to either end, the brightness is close to maximum, and when the potentiometer is turned close to center, the LED get's dim or doesn't show any light at all.

We want to modify this, so that ideally it will only be bright on ONE side, and that ideally the potentiometer value be swapped to something smaller (like 100k or 10k).

# Theory and decisions behind pinout placements
<img width="600" height="337" alt="Screenshot 2025-12-25 014243" src="https://github.com/user-attachments/assets/b7137da6-18c2-4a44-85cd-b1db7436b96f" /><br/>
As shown in the picture above, we have trigger (pin 2) and threshold (pin 6) connected to each other directly with a GREEN wire. No resistor is needed since we do not want voltage drop to affect the 2/3Vcc and 1/3Vcc for each comparator in the 555 timer. 
<img width="798" height="422" alt="image" src="https://github.com/user-attachments/assets/1d012e24-c07c-49d2-bd87-19c463be594d" />
The connection of the two allows for the general case shown in the I/O table image, giving the general pulse width on and off functionality for the 555 timer. This is shown in the circuit as such.

<img width="300" height="721" alt="image" src="https://github.com/user-attachments/assets/dc8b1b64-4159-4cfa-a0ee-1fc3b8950063" />


<img src="https://github.com/user-attachments/assets/c97514b8-139f-48ea-9cce-27dd3798662c" width="500" />

This is the second circuit implementation. It can be seen that two more potentiometers are added, another 900k potentiometer and a 100k potentiometer. The 2nd 900k potentiometer determines the pulse width of the duty cycle, and can customize how long it stays ON or OFF for each pulse. The 100k potentiometer determinse the period. This will be further updated so that ideally they are all same value potentiometers unless required to be different.

