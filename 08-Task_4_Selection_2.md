## Task 1 – Button Turns LED Red 

### Scenario

You are developing a simple warning system for a machine control panel.

The control panel has a push button and a Red LED.

When the operator presses the button, the system should activate the red warning light to indicate that the machine requires attention.

However, **the system should first check if the LED is currently OFF before turning it ON**. This prevents the program from repeatedly sending the same command to the LED.

This task demonstrates how nested `if` statements allow a program to check multiple conditions inside another condition.

### Hardware Requirements

- ESP32
- 1 Push Button
- 1 Red LED
- Breadboard
- Jumper wires

**WokWi Link: https://wokwi.com/projects/457977366200336385**
  
#
## Task 2 – Button Toggles LED ON/OFF

### Scenario

You are designing a machine control panel that uses one button to control a warning light.

The operator presses the button to activate the warning light, and presses the same button again to deactivate it.

This requires the program to remember the current LED state and switch it each time the button is pressed.

### Hardware Requirements

- ESP32
- 1 Button
- 1 LED
- Breadboard
- Jumper wires
  
**Wokwi Link: https://wokwi.com/projects/457978024360140801**

#
## Task 3 – Machine Status Indicator (Switch Case)

### Scenario

You are developing a machine status indicator system for an industrial control panel.

The machine uses three LED lights to display its current operating condition:

- 🟢 Green LED – Safe Mode (the machine is operating normally)
- 🟡 Yellow LED – Maintenance Mode (the machine requires inspection or servicing)
- 🔴 Red LED – Error Mode (the machine has detected a fault)

An operator can press a button on the control panel to cycle through the different machine modes for testing purposes.

Each time the button is pressed, the system should change the machine mode and update the LED indicator.

The program must:

1. Use a variable called `mode` to store the current system state.
2. Increase the mode value each time the button is pressed
3. Reset the mode back to 1 after mode 3.
4. Use a `switch` statement to control which LED turns on.

### Hardware Requirements

- ESP32
- 1 Button
- 1 LED for each mode (🟢 Green, 🟡 Yellow, 🔴 Red)
- Breadboard
- Jumper wires

**WokWi Link: https://wokwi.com/projects/457979388832474113**

#
## Task 4 – RGB Colour Selector (Switch Case)

### Scenario

You are developing a colour selection system using an RGB LED.

The system allows a user to cycle through different LED colours using a push button.
Each time the button is pressed, the system moves to the next colour state.

The RGB LED can display the following states:

|State  |LED Colour   |
|---------|-------------|
|0     | OFF       |
|1    | RED      |
|2    | GREEN     |
|3    | BLUE      |


### Programming Requirement

You must:

- Create a variable called state
- Increase the state value when the button is pressed
- Use a `switch...case` statement
- Control the RGB LED based on the current state

### Hardware Requirements

- ESP32
- 1 Push Button
- 1 RGB LED
- Breadboard
- Jumper wires

### Example Connections

| RGB LED Pin | ESP32 Pin |
| ----------- | --------- |
| Red         | GPIO 16   |
| Green       | GPIO 17   |
| Blue        | GPIO 19   |
| Button      | GPIO 18   |

**Wokwi Link: https://wokwi.com/projects/457980264822427649**