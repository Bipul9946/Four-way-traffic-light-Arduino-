# Four-way-traffic-light-Arduino-
An Arduino-based four- way traffic light control system using LEDs, resistors, and Arduino Uno ,implement safe traffic management with Green, Yellow, and Red light cycles
# 🚦 Four Way Traffic Light Control System  
![Arduino](https://img.shields.io/badge/Arduino-Uno-blue) ![License](https://img.shields.io/badge/License-MIT-green)  

## 📌 Overview  
This project demonstrates a *four-way traffic light control system* using an *Arduino Uno*.  
It manages traffic at a four-way intersection by controlling *Red, Yellow, and Green lights* in a sequence.  
The logic ensures *safe and smooth traffic flow* by cycling through all four directions with proper timing intervals.  

---

## 🛠 Technologies Used  
- *Arduino Uno (ATmega328P)*  
- *C/C++ (Arduino IDE)*  
- LEDs (Red, Yellow, Green)  
- Resistors (220Ω for LEDs)  
- Breadboard & Jumper Wires  
- Power Supply (5V USB)  

---

## ⚡ Circuit Diagram  
Each direction has 3 LEDs (Red, Yellow, Green) connected to Arduino pins.


*(You can add an image later in /docs/circuit-diagram.png)*  

---

## ⏱ Working Principle  
1. One direction is given *Green* while all others remain *Red*.  
2. Before turning Red, a *Yellow light* indicates a transition.  
3. The cycle repeats for all four directions in order.  

### Timing Configuration  
- *Green light*: 5 seconds  
- *Yellow light*: 2 seconds  
- *Red buffer*: 1 second  

These values can be modified in the code:  
```cpp
int greenTime = 5000;   // 5 sec Green
int yellowTime = 2000;  // 2 sec Yellow
int redTime = 1000;     // 1 sec Red buffer


four-way-traffic-light-arduino/
│── traffic_light.ino        # Arduino source code
│── README.md                # Documentation
│── /docs                    # Circuit diagram (optional)
│── LICENSE                  # Open-source license
