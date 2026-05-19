# Arrays in Arduino

## What is an Array?

An **array** is a variable that stores multiple values of the same type in a single, ordered list. Instead of creating separate variables for each value, you group them together under one name and access each value using an **index number**.

Think of an array like a row of labelled boxes:

```
Index:  [0]   [1]   [2]   [3]   [4]
Value:   10    20    30    40    50
```

- The index always **starts at 0**, not 1.
- Each item in the array is called an **element**.

---

## Why Use Arrays?

Without arrays, storing 5 LED pin numbers looks like this:

```cpp
int led1 = 2;
int led2 = 3;
int led3 = 4;
int led4 = 5;
int led5 = 6;
```

With an array, it becomes one clean line:

```cpp
int leds[5] = {2, 3, 4, 5, 6};
```

Arrays also let you use **loops** to work with many values at once, which saves a lot of repetitive code.

---

## Declaring an Array

### Syntax

```cpp
dataType arrayName[size];
```

| Part        | Meaning                                      |
|-------------|----------------------------------------------|
| `dataType`  | The type of data stored (int, float, etc.)   |
| `arrayName` | The name you give the array                  |
| `size`      | How many elements the array can hold         |

### Examples

```cpp
int scores[5];              // Array of 5 integers (values undefined)
float temperatures[3];      // Array of 3 floats
bool buttons[4];            // Array of 4 booleans
```

---

## Initialising an Array

You can set values when you declare the array:

```cpp
int scores[5] = {85, 90, 78, 92, 88};
```

If you provide all the values, you can leave out the size — Arduino figures it out:

```cpp
int scores[] = {85, 90, 78, 92, 88};  // Size is automatically 5
```

---

## Accessing Elements

Use the index inside square brackets to read or write a specific element.

```cpp
int scores[] = {85, 90, 78, 92, 88};

int first  = scores[0];   // 85
int second = scores[1];   // 90
int last   = scores[4];   // 88
```

You can also **change** an element:

```cpp
scores[2] = 95;   // Changes 78 to 95
```

> **Common mistake:** Accessing `scores[5]` on a 5-element array goes out of bounds. Valid indexes are 0 to 4.

---

## What is a Loop?

A **loop** is a block of code that repeats automatically. Instead of writing the same instruction ten times, you write it once and tell Arduino how many times to run it.

```cpp
// Without a loop — 5 lines doing the same thing:
digitalWrite(2, HIGH);
digitalWrite(3, HIGH);
digitalWrite(4, HIGH);
digitalWrite(5, HIGH);
digitalWrite(6, HIGH);

// With a loop — one block, same result:
for (int i = 2; i <= 6; i++) {
  digitalWrite(i, HIGH);
}
```

---

## Why Use Loops?

| Without a Loop | With a Loop |
|----------------|-------------|
| Lots of repeated lines | One compact block |
| Hard to change (edit every line) | Easy to change (edit one place) |
| Error-prone | Less chance of mistakes |

Loops become even more powerful when combined with arrays — the loop index `i` points directly to each array element in order.

---

## Types of Loops

### 1. `for` Loop

Use when you **know how many times** to repeat.

#### Syntax

```cpp
for (initialisation; condition; increment) {
  // code to repeat
}
```

| Part             | Meaning                                      |
|------------------|----------------------------------------------|
| `initialisation` | Runs once at the start — sets up the counter |
| `condition`      | Checked before each pass — loop stops when false |
| `increment`      | Runs after each pass — usually advances the counter |

#### Example

```cpp
for (int i = 0; i < 5; i++) {
  // Runs 5 times: i = 0, 1, 2, 3, 4
}
```

| Part        | Meaning                          |
|-------------|----------------------------------|
| `int i = 0` | Start: `i` begins at 0           |
| `i < 5`     | Condition: keep going while true |
| `i++`       | Step: add 1 to `i` each time     |

---

### 2. `while` Loop

Use when you want to repeat **as long as something is true**, and you may not know how many passes are needed.

#### Syntax

```cpp
while (condition) {
  // code to repeat
}
```

| Part        | Meaning                                          |
|-------------|--------------------------------------------------|
| `condition` | Checked before each pass — loop stops when false |

#### Example

```cpp
int count = 0;

while (count < 3) {
  digitalWrite(LED_BUILTIN, HIGH);
  delay(500);
  digitalWrite(LED_BUILTIN, LOW);
  delay(500);
  count++;   // Add 1 each pass — stops the loop at count = 3
}
```

The LED blinks 3 times, then the loop ends.

---

### 3. `do...while` Loop

Use when you want the code to run **at least once**, then keep repeating while a condition is true.

#### Syntax

```cpp
do {
  // code to repeat
} while (condition);
```

| Part        | Meaning                                              |
|-------------|------------------------------------------------------|
| `do`        | The block runs once immediately, before any check    |
| `condition` | Checked after each pass — loop continues while true  |

#### Example

```cpp
int reading;

do {
  reading = analogRead(A0);   // Read sensor at least once
} while (reading < 512);      // Keep reading until value is 512 or above
```

> In Arduino, `for` loops are the most common — especially when working with arrays.

---

## Using Arrays with Loops

A `for` loop and an array are a natural pair. The loop variable `i` acts as the index, so you can visit every element without writing each one out manually.

### The Basic Pattern

```cpp
int leds[] = {2, 3, 4};
int numLeds = 3;

for (int i = 0; i < numLeds; i++) {
  // leds[i] refers to each pin in order: leds[0], leds[1], leds[2]
  pinMode(leds[i], OUTPUT);
}
```

### Example — Blink All LEDs One at a Time

**Circuit:** 3 LEDs on pins 2, 3, 4.

```cpp
int leds[]  = {2, 3, 4};   // Pins for the 3 LEDs
int numLeds = 3;            // Number of LEDs

void setup() {
  for (int i = 0; i < numLeds; i++) {
    pinMode(leds[i], OUTPUT);   // Set each LED pin as output
  }
}

void loop() {
  for (int i = 0; i < numLeds; i++) {
    digitalWrite(leds[i], HIGH);  // Turn this LED on
    delay(300);                   // Wait 300 ms
    digitalWrite(leds[i], LOW);   // Turn this LED off
  }
}
```

**How it works:**
- `setup()` uses a loop to configure all 3 pins in one go instead of three separate `pinMode` calls.
- `loop()` steps through the array, turning each LED on then off in sequence — creating a chasing light effect.

---

## Example 1 — Each Button Controls Its Own LED

**Circuit:** 3 buttons on pins 2, 3, 4 — 3 LEDs on pins 8, 9, 10.

Each button and its matching LED share the same array index. Pressing button 0 lights up LED 0, pressing button 1 lights up LED 1, and so on.

```cpp
int buttons[] = {2, 3, 4};    // Pins connected to the 3 buttons
int leds[]    = {8, 9, 10};   // Pins connected to the 3 LEDs — index matches buttons[]
int numPins   = 3;             // Number of button/LED pairs

void setup() {
  for (int i = 0; i < numPins; i++) {        // Loop through all 3 pairs
    pinMode(buttons[i], INPUT_PULLUP);        // Reads HIGH normally, LOW when pressed
    pinMode(leds[i], OUTPUT);                 // Set the matching LED pin as output
  }
}

void loop() {
  for (int i = 0; i < numPins; i++) {        // Check each button one at a time
    if (digitalRead(buttons[i]) == LOW) {    // LOW means the button is currently pressed
      digitalWrite(leds[i], HIGH);           // Turn on the LED at the same index
    } else {
      digitalWrite(leds[i], LOW);            // Turn off the LED when button is released
    }
  }
}
```
**Wokwi simulation:** [https://wokwi.com/projects/463716775811722241](https://wokwi.com/projects/463716775811722241)

**How it works:**
- Two arrays (`buttons` and `leds`) are linked by the same index `i`.
- The `for` loop checks all 3 buttons in one pass instead of writing 3 separate `if` blocks.
- `INPUT_PULLUP` means the pin reads `HIGH` by default and `LOW` when the button is pressed.

---

## Example 2 — Button Press Counter with Buzzer Feedback

**Circuit:** 3 buttons on pins 2, 3, 4 — 3 LEDs on pins 8, 9, 10.

Each button has its own press counter. Every press lights the matching LED briefly and prints the updated count to Serial.

```cpp
int buttons[] = {2, 3, 4};    // Pins for the 3 buttons
int leds[]    = {8, 9, 10};   // Pins for the 3 LEDs, matched by index
int counts[]  = {0, 0, 0};    // Press counter for each button, all start at 0
int numPins   = 3;             // Number of button/LED pairs

void setup() {
  Serial.begin(9600);                      // Start Serial Monitor to display counts
  for (int i = 0; i < numPins; i++) {     // Loop through all 3 pairs
    pinMode(buttons[i], INPUT_PULLUP);    // Button reads HIGH normally, LOW when pressed
    pinMode(leds[i], OUTPUT);             // Set the matching LED pin as output
  }
}

void loop() {
  for (int i = 0; i < numPins; i++) {          // Check each button one at a time
    if (digitalRead(buttons[i]) == LOW) {       // LOW means this button is being pressed
      counts[i]++;                              // Add 1 to this button's own counter
      digitalWrite(leds[i], HIGH);             // Light up the LED at the same index
      Serial.print("Button ");                 // Print which button was pressed
      Serial.print(i);
      Serial.print(" count: ");
      Serial.println(counts[i]);               // Print the updated count for that button
      delay(300);                              // Pause 300 ms so one press isn't counted twice
      digitalWrite(leds[i], LOW);             // Turn off the LED after the pause
    }
  }
}
```

**Sample Serial output:**
```
Button 0 count: 1
Button 2 count: 1
Button 0 count: 2
Button 1 count: 1
```

**How it works:**
- `counts[]` gives each button its own independent total — changing one slot does not affect the others.
- `delay(300)` acts as a simple debounce — it pauses long enough that one press is only counted once.
- The LED lights up for 300 ms on each press, giving clear visual feedback.

---

## Example 3 — Press a Button to Play a Melody, LEDs Follow the Beat

**Circuit:** 1 button on pin 2 — 3 LEDs on pins 8, 9, 10 — buzzer on pin 11.

Two arrays store the notes (frequencies in Hz) and their durations. When the button is pressed the buzzer plays the melody and the LEDs cycle in time with each note.

```cpp
int button  = 2;                             // Pin for the trigger button
int buzzer  = 11;                            // Pin for the buzzer
int leds[]  = {8, 9, 10};                   // Three LED pins for visual feedback

//                         C4   D4   E4   F4   G4
int notes[]     = {262, 294, 330, 349, 392}; // Frequency (Hz) for each note in the melody
int durations[] = {300, 300, 300, 300, 600}; // How long each note plays in milliseconds
int numNotes    = 5;                          // Total number of notes in the melody

void setup() {
  pinMode(button, INPUT_PULLUP);   // Button reads HIGH normally, LOW when pressed
  pinMode(buzzer, OUTPUT);         // Buzzer receives output signals to produce sound
  for (int i = 0; i < 3; i++) {
    pinMode(leds[i], OUTPUT);      // Set each of the 3 LED pins as output
  }
}

void loop() {
  if (digitalRead(button) == LOW) {             // Wait here until the button is pressed
    for (int i = 0; i < numNotes; i++) {        // Step through each note in the melody
      int led = i % 3;                           // Wrap index to 0–2 so 3 LEDs cycle: 0,1,2,0,1
      digitalWrite(leds[led], HIGH);             // Light up the LED for this note
      tone(buzzer, notes[i], durations[i]);      // Play the note at its frequency and duration
      delay(durations[i] + 50);                 // Wait for the note to finish, plus a 50 ms gap
      digitalWrite(leds[led], LOW);              // Turn the LED off before moving to the next note
    }
    noTone(buzzer);   // Stop any lingering buzzer sound after the last note
    delay(500);       // Short pause so the button can't immediately replay the melody
  }
}
```

**How it works:**
- `notes[]` and `durations[]` are parallel arrays — `notes[i]` and `durations[i]` always describe the same note.
- `i % 3` uses the remainder operator to cycle through only 3 LEDs even though there are 5 notes.
- `noTone(buzzer)` is called at the end to make sure the buzzer stops cleanly.

---

## Getting the Size of an Array

Arduino does not have a built-in `.length` for arrays like some other languages. Use this formula:

```cpp
int leds[] = {2, 3, 4, 5, 6};
int size = sizeof(leds) / sizeof(leds[0]);   // Result: 5
```

`sizeof(leds)` gives the total bytes used; `sizeof(leds[0])` gives bytes per element. Dividing gives the count.

---

## Key Points to Remember

| Concept             | Detail                                             |
|---------------------|----------------------------------------------------|
| Index starts at     | 0                                                  |
| Last valid index    | size - 1                                           |
| Going out of bounds | Causes unpredictable behaviour — avoid this        |
| Use with loops      | `for` loops and arrays work perfectly together     |
| Same data type      | All elements must be the same type (int, float...) |

---

## Quick Reference

```cpp
int arr[5] = {1, 2, 3, 4, 5};  // Declare an array of 5 integers and set their starting values

arr[0];          // Read first element  → 1  (index always starts at 0)
arr[4];          // Read last element   → 5  (last valid index is size - 1)
arr[2] = 99;     // Overwrite the third element — changes it from 3 to 99

for (int i = 0; i < 5; i++) {  // Loop from index 0 to 4, visiting every element
  // Use arr[i] here to read or change each element in order
}
```
