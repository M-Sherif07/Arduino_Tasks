
## TASK  1 – One Way Activation Switch 
### Scenario

You are designing a machine start system for a small production unit.

When the system powers on:

- The machine indicator light must be OFF.
- The operator presses a START button.
- The LED turns ON to indicate the machine has started
- After activation, pressing the button again must NOT turn the LED OFF.

This simulates a one-direction trigger system (like starting a motor).


### Hardware Requirement 
- ESP32 Dev board
- LED light
- Push Button
- Jumper Wires

**WokWi Link: https://wokwi.com/projects/457504411332962305**


## TASK 2 – Night Mode Indicator 
### Scenario

You are designing a smart desk lamp controller using an ESP32.

The lamp is designed for night-time study use. For safety and usability reasons:

**The lamp:**

- Turns ON when powered.
- When the user presses the button:
  - The lamp turns OFF.
- When pressed again:
  - The lamp turns ON again.
- The lamp must remember its state.

This simulates a real on/off switch system.

### Hardware Requirement 
- ESP32 Dev board
- LED light
- Push Button
- Jumper Wires
  
  **WokWi Link: https://wokwi.com/projects/457503473630123009**
  

## TASK 3 – Emergency Override System 
### Scenario

You are working as a Junior Embedded Systems Technician for a small manufacturing company in Melbourne.

The company uses a status indicator light to show that a machine is operating normally.

🟢 When the system is running normally ➡️ The LED must stay ON.

🔴 If an emergency situation occurs ➡️ An emergency push button is pressed.

**When the emergency button is pressed:**

- The machine must stop immediately.
- Green LED turns OFF.
- Red LED turns ON.
- Emergency condition has highest priority.

### Hardware Requirement 
- ESP32 Dev board
- Red LED light
- Green LED light
- Push Button
- Jumper Wires

**WoKwi Link:  https://wokwi.com/projects/457502446743796737**


## TASK 4 – Mode Selector 

### Scenario

You are designing a simple control system with three operating modes:

1. OFF Mode – LED stays OFF
2. ON Mode – LED stays ON
3. BLINK Mode – LED blinks continuously

Each time the user presses the button, the system changes to the next mode.

After Mode 3, it returns back to Mode 1.

This simulates a basic mode selection system used in embedded devices.

### Hardware Requirement 
- ESP32 Dev board
- LED light
- Push Button
- Jumper Wires
  
**WokWi Link: https://wokwi.com/projects/457505020720315393**


## TASK 5 – Power Level Indicator

### Scenario

You are designing a power level indicator system.

The system has three power levels:

| Level | LED       |
| ----- | --------- |
| 1     | 🟢 Green  |
| 2     | 🟡 Yellow |
| 3     | 🔴 Red    |

Each time the user presses the button:

-  The power level increases.
-  After Level 3, it resets back to Level 1.

Only one LED should be ON at a time.

### Hardware Requirement 
- ESP32 Dev board
- Green LED light
- Yellow LED light
- Red LED light
- Push Button
- Jumper Wires

**WokWi Link:  https://wokwi.com/projects/457505585180382209**