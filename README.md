# Four-way-traffic-light-Arduino-
An Arduino-based four- way traffic light control system using LEDs, resistors, and Arduino Uno ,implement safe traffic management with Green, Yellow, and Red light cycles
# 🚦 Four Way Traffic Light Control System  
![Arduino](https://img.shields.io/badge/Arduino-Uno-blue) ![License](https://img.shields.io/badge/License-MIT-green)  

##  Overview  
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



*/

// === Pin Definitions ===
#define RED1     2
#define YELLOW1  3
#define GREEN1   4

#define RED2     5
#define YELLOW2  6
#define GREEN2   7

#define RED3     8
#define YELLOW3  9
#define GREEN3   10

#define RED4     11
#define YELLOW4  12
#define GREEN4   13

// === Timing Configuration (milliseconds) ===
int greenTime  = 5000;   // 5 seconds Green
int yellowTime = 2000;   // 2 seconds Yellow
int redTime    = 1000;   // 1 second buffer

// === Setup ===
void setup() {
  // Set all pins as OUTPUT
  pinMode(RED1, OUTPUT); pinMode(YELLOW1, OUTPUT); pinMode(GREEN1, OUTPUT);
  pinMode(RED2, OUTPUT); pinMode(YELLOW2, OUTPUT); pinMode(GREEN2, OUTPUT);
  pinMode(RED3, OUTPUT); pinMode(YELLOW3, OUTPUT); pinMode(GREEN3, OUTPUT);
  pinMode(RED4, OUTPUT); pinMode(YELLOW4, OUTPUT); pinMode(GREEN4, OUTPUT);

  // Turn all signals RED at start
  allRed();
}

// === Loop (Main Program) ===
void loop() {
  // Sequence: 1 → 2 → 3 → 4
  trafficCycle(RED1, YELLOW1, GREEN1);
  trafficCycle(RED2, YELLOW2, GREEN2);
  trafficCycle(RED3, YELLOW3, GREEN3);
  trafficCycle(RED4, YELLOW4, GREEN4);
}

// === Function: Run one direction cycle ===
void trafficCycle(int red, int yellow, int green) {
  // Green ON
  digitalWrite(green, HIGH);
  digitalWrite(red, LOW);
  delay(greenTime);

  // Yellow ON
  digitalWrite(green, LOW);
  digitalWrite(yellow, HIGH);
  delay(yellowTime);

  // Back to Red
  digitalWrite(yellow, LOW);
  digitalWrite(red, HIGH);
  delay(redTime);
}

// === Helper: Turn all signals RED ===
void allRed() {
  digitalWrite(RED1, HIGH);
  digitalWrite(RED2, HIGH);
  digitalWrite(RED3, HIGH);
  digitalWrite(RED4, HIGH);

  digitalWrite(YELLOW1, LOW);
  digitalWrite(YELLOW2, LOW);
  digitalWrite(YELLOW3, LOW);
  digitalWrite(YELLOW4, LOW);

  digitalWrite(GREEN1, LOW);
  digitalWrite(GREEN2, LOW);
  digitalWrite(GREEN3, LOW);
  digitalWrite(GREEN4, LOW);
}
