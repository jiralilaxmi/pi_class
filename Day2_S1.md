**Session 1: Understanding GPIO Pins and Interfacing Digital Sensors (2 Hours)**

---

## **Part 1: Understanding GPIO Pins on Raspberry Pi (45 minutes)**

### **1. Introduction to GPIO (10 minutes)**  
- **What are GPIO Pins?**
  - GPIO (General Purpose Input/Output) pins allow Raspberry Pi to interact with electronic components.
  - Can be used as **input** (sensors) or **output** (LEDs, motors).
- **Pin Layout Overview:**
  - 40-pin GPIO header.
  - **Power Pins (3.3V, 5V, GND).**
  - **Data Pins (GPIO0 – GPIO27).**

**Hands-on Activity:**
- Show students the Raspberry Pi board and explain the GPIO layout.

### **2. Using GPIO in Python (15 minutes)**  
- Install GPIO library:
  ```bash
  sudo apt update
  sudo apt install python3-gpiozero
  ```
- Importing and controlling GPIO in Python:
  ```python
  from gpiozero import LED
  from time import sleep
  led = LED(17)
  while True:
      led.on()
      sleep(1)
      led.off()
      sleep(1)
  ```
- **Hands-on Activity:** Students execute this code to blink an LED.

### **3. Safety & Precautions (20 minutes)**  
- **Avoid short circuits.**
- **Use resistors to prevent damage.**
- **Do not exceed voltage limits.**

**Hands-on Activity:**
- Connect an LED to a GPIO pin using a breadboard.

---

## **Part 2: Interfacing Digital Sensors (LED, Button, DHT11) (45 minutes)**

### **1. LED Blinking – Basic GPIO Control (15 minutes)**  
- Circuit connection using a resistor and LED.
- Writing Python code to blink an LED:
  ```python
  from gpiozero import LED
  from time import sleep
  led = LED(17)
  while True:
      led.toggle()
      sleep(1)
  ```

### **2. Button Press Detection (15 minutes)**  
- Circuit setup using a push button.
- Writing Python code to detect button press:
  ```python
  from gpiozero import Button
  button = Button(2)
  while True:
      if button.is_pressed:
          print("Button Pressed!")
  ```

**Hands-on Activity:** Students modify the code to turn an LED on when the button is pressed.

### **3. Reading Temperature & Humidity using DHT11 (15 minutes)**  
- Connect **DHT11 sensor** to Raspberry Pi.
- Install necessary library:
  ```bash
  pip install Adafruit_DHT
  ```
- Write Python code to read data:
  ```python
  import Adafruit_DHT
  sensor = Adafruit_DHT.DHT11
  pin = 4
  humidity, temperature = Adafruit_DHT.read_retry(sensor, pin)
  print("Temp:", temperature, "C, Humidity:", humidity, "%")
  ```

**Hands-on Activity:**
- Students run the script and observe real-time temperature and humidity data.

---

## **Wrap-Up & Q&A (10 minutes)**
- **Review:**
  - GPIO basics and pin layout.
  - Interfacing LED, Button, and DHT11 sensor.
  - Running Python scripts to control GPIO.
- **Encourage Questions:** Address doubts students have.

---

## **Homework/Practice Task**
- Modify the LED blinking code to blink in a pattern (e.g., SOS Morse code).
- Try using a button to control an LED using Python.

---

## **Summary of Session 1 (Day 2)**
✅ **Understanding GPIO and its applications.**
✅ **Interfacing digital sensors (LED, button, DHT11).**
✅ **Hands-on coding exercises for real-world IoT applications.**

