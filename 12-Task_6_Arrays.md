# Task 6 — Arrays and Loops

---

## Task 1: Traffic Light Sequence

### Scenario
You have been hired by a local council to build a prototype traffic light system for a pedestrian crossing at a school. The system must cycle through red, yellow, and green lights in the correct order, holding each colour for a set amount of time. The council wants the code to be easy to update if timing needs to change.

### Objective
Write an Arduino program that:
- Stores 3 LED pins (red, yellow, green) in an array
- Stores the delay time for each colour in a second array
- Uses a `for` loop to step through both arrays and light each LED for its matching duration

### Expected Output
The LEDs cycle: Red (3 s) → Yellow (1 s) → Green (3 s) → repeat.

### Hardware Requirements
- Arduino Uno
- Red, Yellow, and Green LEDs
- 3 × 220Ω resistors
- Breadboard and jumper wires

---

## Task 2: LED Chaser

### Scenario
A local theatre group needs a simple stage lighting effect for their next production. They want a row of 5 LEDs to light up one at a time from left to right, then reverse back from right to left — creating a back-and-forth chasing effect that runs continuously.

### Objective
Write an Arduino program that:
- Stores 5 LED pins in an array
- Uses a `for` loop to light LEDs left to right, turning each off before moving to the next
- Uses a second `for` loop counting backwards to chase right to left
- Runs both loops continuously inside `loop()`

### Expected Output
LEDs chase forward then backward in a smooth sequence with a 150 ms delay between each step.

### Hardware Requirements
- Arduino Uno
- 5 LEDs (any colour)
- 5 × 220Ω resistors
- Breadboard and jumper wires

---

## Task 3: Voting Machine

### Scenario
A classroom teacher wants a simple electronic voting machine for in-class polls. The system has 3 buttons — one for each candidate. Students take turns pressing their chosen button. When the teacher presses a reset button, all counts clear and a new round begins. The current vote counts are printed to Serial Monitor after every press.

### Objective
Write an Arduino program that:
- Stores 3 button pins in an array
- Stores a vote counter for each button in a second array, all starting at 0
- Uses a `for` loop to check every button each pass through `loop()`
- Adds 1 to the matching counter when a button is pressed
- Prints all three vote counts to Serial Monitor after each press

### Expected Serial Output
```
--- Vote Counts ---
Candidate 0: 3
Candidate 1: 1
Candidate 2: 2
```

### Hardware Requirements
- Arduino Uno
- 3 push buttons
- Breadboard and jumper wires

---

## Task 4: Temperature Logger

### Scenario
You are working for an environmental monitoring company. They need a device that reads the temperature from a sensor every 2 seconds and stores the last 5 readings in memory. After every new reading, the device prints all stored readings and the average temperature to Serial Monitor so staff can spot trends.

### Objective
Write an Arduino program that:
- Declares an array of size 5 to store temperature readings (use `random(15, 35)` to simulate sensor values)
- Uses a `for` loop to fill the array with new readings each cycle
- Uses a second `for` loop to add all values and calculate the average
- Prints every stored reading and the average to Serial Monitor

### Expected Serial Output
```
Readings: 22 25 19 28 23
Average: 23.4 C
```

### Hardware Requirements
- Arduino Uno
- USB cable (Serial Monitor only — sensor values are simulated)

---

## Task 5: Melody Player with LED Feedback

### Scenario
A primary school wants an interactive musical toy. When a child presses a button, the device plays a short 6-note melody through a buzzer. While each note plays, one of 3 LEDs lights up in sequence so the child gets a visual beat alongside the sound.

### Objective
Write an Arduino program that:
- Stores 6 note frequencies in one array and their durations in a second array
- Stores 3 LED pins in a third array
- When the button is pressed, loops through the notes array — playing each note and lighting the LED at index `i % 3`
- Turns the LED off and moves to the next note after each duration

### Expected Output
The buzzer plays 6 notes. LEDs cycle through all 3 in time with the beat.

### Hardware Requirements
- Arduino Uno
- 1 push button
- Passive buzzer
- 3 LEDs
- 3 × 220Ω resistors
- Breadboard and jumper wires

---

## Task 6: Parking Space Monitor

### Scenario
A small shopping centre wants a low-cost parking monitor for their 4-space car park. Each space has a sensor (simulated with a button) that reads LOW when a car is present. A display (Serial Monitor) shows which spaces are taken and how many are still free. The information updates every second.

### Objective
Write an Arduino program that:
- Stores 4 sensor pins in an array
- Uses a `for` loop to read every sensor each second
- Stores the result (occupied/free) for each space in a second array
- Prints the status of every space and the total free count to Serial Monitor

### Expected Serial Output
```
Space 0: OCCUPIED
Space 1: FREE
Space 2: OCCUPIED
Space 3: FREE
Free spaces: 2
```

### Hardware Requirements
- Arduino Uno
- 4 push buttons (simulate car sensors)
- Breadboard and jumper wires

---

## Task 7: Progressive LED Brightness

### Scenario
An interior design firm wants a mood lighting demo. A strip of 4 LEDs should glow at increasing brightness levels — the first LED dim, the last LED at full brightness — creating a gradient effect. Pressing a button cycles the gradient one step forward across the LEDs.

### Objective
Write an Arduino program that:
- Stores 4 PWM-capable LED pins in an array
- Stores 4 brightness values in a second array (e.g. `{64, 128, 192, 255}`)
- Uses a `for` loop to write each brightness level to its matching LED using `analogWrite()`
- Each button press shifts the brightness values one position forward in the array so the gradient moves

### Expected Output
LEDs display a brightness gradient that shifts one step right on every button press.

### Hardware Requirements
- Arduino Uno (use PWM pins: 3, 5, 6, 9)
- 4 LEDs
- 4 × 220Ω resistors
- 1 push button
- Breadboard and jumper wires

---

## Task 8: Quiz Buzzer System

### Scenario
A quiz night organiser needs a 4-player buzzer system. When a player presses their button, their LED lights up, their buzzer number is announced on Serial Monitor, and all other buttons are locked out until the host presses a reset button to clear the round and start again.

### Objective
Write an Arduino program that:
- Stores 4 button pins and 4 LED pins in separate arrays
- Uses a `for` loop each pass through `loop()` to check all buttons
- When the first button press is detected, lights that player's LED and prints their number to Serial Monitor
- Sets a `locked` flag to ignore further presses until the reset button is pressed
- Pressing reset turns off all LEDs, clears the flag, and prints "Ready for next question"

### Expected Serial Output
```
Player 2 buzzed in!
Ready for next question
Player 0 buzzed in!
```

### Hardware Requirements
- Arduino Uno
- 4 push buttons (players) + 1 push button (reset)
- 4 LEDs
- 4 × 220Ω resistors
- Breadboard and jumper wires
