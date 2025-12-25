# Strobe-Light-Analog-Circuit
Analog circuit using LEDs with a NE555 to flicker at customizable rates with potentiometers.

Image credits go to CircuitBread's video https://www.youtube.com/watch?v=iwbGccGU4io

Circuit inspiration credits go to Skosan Electronics video https://www.youtube.com/watch?v=euiDv51VVt4 

I/O table credits go to element14 presents video https://www.youtube.com/watch?v=oZzjmAbyyIQ&t=315s

<img src="https://github.com/user-attachments/assets/918a3fbf-338d-4a15-a2cd-0778598d1b12" width="500" />
This is the first circuit implementation.

# Theory and decisions behind pinout placements
<img width="600" height="337" alt="Screenshot 2025-12-25 014243" src="https://github.com/user-attachments/assets/b7137da6-18c2-4a44-85cd-b1db7436b96f" />
As shown in the picture above, we have trigger (pin 2) and threshold (pin 6) connected to each other directly with a GREEN wire. No resistor is needed since we do not want voltage drop to affect the 2/3Vcc and 1/3Vcc for each comparator in the 555 timer. 
<img width="798" height="422" alt="image" src="https://github.com/user-attachments/assets/1d012e24-c07c-49d2-bd87-19c463be594d" />
The connection of the two allows for the general case shown in the I/O table image, giving the general pulse width on and off functionality for the 555 timer. This is shown in the circuit as such.

<img src="https://github.com/user-attachments/assets/c97514b8-139f-48ea-9cce-27dd3798662c" width="500" />

This is the second implementation

