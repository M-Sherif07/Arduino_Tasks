# Arduino Programming – Assessment Task

**Student Name:** ___________________________  

**Date:** ___________________________  


---

## Instructions

- Answer **all** questions in each section.
- For coding tasks, use Wokwi to test and submit a link to your working project.
  


---

## Section 1 – Theory Questions 

### 1.1 LED and Hardware 

**Q1.** Label the following parts of an LED. 

| Terminal | Symbol | Pin Leg Length (Short/Long) |
| -------- | ------ | ---------- |
| A        |        |            |
| B        |        |            |


**Q2.** A student connects an LED backwards. What will happen?

> _______________________________________________________________


**Q3.** Which Arduino function is used to set a pin as an output?

> _______________________________________________________________

**Q4.** What value do you write to a pin to turn an LED **ON**? 

> _______________________________________________________________




### 1.2 Variables and Data Types 

**Q5.** What is a **variable** in programming? 

> _______________________________________________________________

**Q6.** Choose the correct data type for each value. 

| Value | Data Type |
| ----- | --------- |
| `true` / `false` | |
| `3.14` | |
| `42` | |

**Q7.** What is wrong with this variable declaration? 

```cpp
int 1count = 0;
```

> _______________________________________________________________



### 1.3 Functions 
**Q8.** What is a **function** in programming?
> _______________________________________________________________

**Q9.** What is the purpose of the  function in Arduino code?
> _______________________________________________________________

**Q10.** What are the two main parts of a function?
> 1. _______________________________________________________________
> 2. _______________________________________________________________


 **Q11.** What is the difference between a **built-in function** and a **custom function**?
> _______________________________________________________________    

**Q12.** What are **two benefits** of using custom functions instead of writing all code inside `loop()`? 

> 1. _______________________________________________________________  
> 2. _______________________________________________________________

**Q13 .** What is a **parameter** in a function? Give one example from the tasks. 

> _______________________________________________________________

**Q14.** True or False: A function can only be called once. 

> _______________________________________________________________



### 1.4 Selection and Decision Making 

**Q15.** What is the difference between `=` and `==` in Arduino code? 

> _______________________________________________________________

**Q16.** Complete the truth table for the following condition: `(temp > 25 && humidity > 60)` 

| temp | humidity | Result |
| ---- | -------- | ------ |
| 10   | 70       |  False      |
| 30   | 50       |        |
| 30   | 70       |        |
| 20   | 50       |        |

**Q17.** When would you use a `switch...case` statement instead of `if/else`? 

> _______________________________________________________________

**Q18.** What does `INPUT_PULLUP` mean when configuring a button pin? 

> _______________________________________________________________

**Q19.** What is **debouncing** and why is it important when using push buttons? 

> _______________________________________________________________



## Section 2 – Code Analysis and Debugging 

### 2.1 Read and Explain 

Study the following code and answer the questions below.

```cpp
int ledPin = 13;
bool ledState = false;

void setup() {
  pinMode(ledPin, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  ledState = !ledState;
  digitalWrite(ledPin, ledState);

  if (ledState == true) {
    Serial.println("System Ready");
  } else {
    Serial.println("System Busy");
  }

  delay(3000);
}
```

**Q20.** What does `bool ledState = false;` declare? 

> _______________________________________________________________

**Q21.** What does `ledState = !ledState;` do on each loop? 

> _______________________________________________________________

**Q22.** How often does the LED change state? 

> _______________________________________________________________

**Q23.** What will the Serial Monitor display after the LED turns ON? 

> _______________________________________________________________

**Q24.** A student wants the LED to toggle every **1 second** instead of 3 seconds. What change do they need to make? 

> _______________________________________________________________

**Q25.** Rewrite the `if/else` block using a **single line** `Serial.println()` with a ternary operator or describe the logic change needed to print the correct message without using `if/else`. *(4 marks)*

```cpp
// Your answer here:



```

---

### 2.2 Spot the Bug 

Each code snippet below contains **one bug**. Identify and fix it.

**Q26.** 

```cpp
void blinkLED(int speed) {
  digitalWrite(ledPin, HIGH);
  delay(speed);
  digitalWrite(ledPin, LOW);
  delay(speed);
}

void loop() {
  blinkLED;   
}
```

**Bug:** _______________________________________________________________  
**Fix:** _______________________________________________________________

---

**Q27.** 

```cpp
int mode = 0;

void loop() {
  switch (mode) {
    case 1:
      digitalWrite(greenLED, HIGH);
      break;
    case 2:
      digitalWrite(yellowLED, HIGH);
      break;
    case 3:
      digitalWrite(redLED, HIGH);
      break;
  }
}
```

**Bug:** _______________________________________________________________  
**Fix:** _______________________________________________________________

---

**Q28.** 

```cpp
if (temperature > 25) {
  Serial.println("Hot and Humid");
} else if (temperature > 25 && humidity < 60) {
  Serial.println("Hot and Dry");
}
```

**Bug:** _______________________________________________________________  
**Fix:** _______________________________________________________________

---

**Q29.** 

```cpp
void dot() {
  digitalWrite(ledPin, HIGH);
  delay(200);
  digitalWrite(ledPin, LOW);
  delay(200)
}
```

**Bug:** _______________________________________________________________  
**Fix:** _______________________________________________________________

---

### 2.3 Trace the Output 

**Q30.** What will the Serial Monitor display when this code runs? Write the output in order. 

```cpp
void warningBlink(int speed) {
  Serial.print("Blinking at speed: ");
  Serial.println(speed);
}

void loop() {
  warningBlink(1000);
  warningBlink(300);
  warningBlink(100);
  delay(5000);
}
```

```
Output:
Line 1: _______________________________________________________________
Line 2: _______________________________________________________________
Line 3: _______________________________________________________________
(then repeats after 5 seconds)
```

**Q31.** A `mode` variable starts at `1` and increases by 1 each button press. It resets to `1` after reaching `3`. Fill in the mode values after each press: *(3 marks)*

| Button Press | Mode Value |
| ------------ | ---------- |
| Start        | 1          |
| Press 1      |            |
| Press 2      |            |
| Press 3      |            |
| Press 4      |            |

---

## Section 3 – Practical Coding Tasks 

> Test all code in Wokwi and paste your project link next to each task.

---

### Task A – Smart Office Status Light 

**Scenario:** You are building a Smart Office Status Light System.

**Requirements:**
- Green LED → **System Ready**
- Red LED → **System Busy**
- LEDs must toggle automatically every **3 seconds**
- Print the current status to the **Serial Monitor**

**You must use:**
- Variables for pin numbers
- `digitalWrite()` and `delay()`
- An `if/else` statement for the Serial Monitor message

**Wokwi Link:** _______________________________________________________________



---

### Task B – Modular Warning Light System 

**Scenario:** A factory needs a reusable warning light system.

**Requirements:**

Create a function called `warningBlink()` that accepts one parameter called `speed`. Inside `loop()`, call the function three times:

```
warningBlink(1000);   // Slow
warningBlink(300);    // Medium
warningBlink(100);    // Critical
```

Each call should blink the LED the correct number of times at the given speed.

**You must use:**
- A custom function with a parameter
- Meaningful comments
- Serial Monitor output showing which mode is active

**Wokwi Link:** _______________________________________________________________



### Task C – Emergency Override System 
**Scenario:** A manufacturing company uses a status light to show normal operation.  
When an emergency button is pressed:

- Green LED turns **OFF**
- Red LED turns **ON**
- Serial Monitor prints `"EMERGENCY – Machine Stopped"`

When no emergency:

- Green LED stays **ON**
- Red LED stays **OFF**
- Serial Monitor prints `"System Running"`

**You must use:**
- A push button with `INPUT_PULLUP`
- An `if/else` statement
- A boolean variable to track the emergency state

**Wokwi Link:** _______________________________________________________________



---

### Task D – Machine Status Indicator with Switch Case 

**Scenario:** An industrial control panel needs three LED modes:

| Mode | LED | Meaning |
| ---- | --- | ------- |
| 1 | Green | Safe |
| 2 | Yellow | Maintenance |
| 3 | Red | Error |

Each button press moves to the next mode. After mode 3, it resets to mode 1. Only one LED is ON at a time.

**You must use:**
- A `mode` variable
- A `switch...case` statement
- A push button to change modes

**Wokwi Link:** _______________________________________________________________



*Good luck! Remember: a good programmer is not someone who never makes mistakes — they are someone who knows how to find and fix them.*
