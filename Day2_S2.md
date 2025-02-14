**Session 2: Controlling Actuators & Building a Smart Fan System (2 Hours)**

---

## **Part 1: Controlling Actuators (Buzzer, Relay, DC Motor) (45 minutes)**

### **1. Introduction to Actuators (10 minutes)**  
- **What are Actuators?**
  - Devices that convert electrical signals into physical action.
  - Examples: Buzzer (sound alerts), Relay (switching high-power devices), DC Motor (motion control).

### **2. Controlling a Buzzer (15 minutes)**  
- **Circuit Setup:** Connect a passive buzzer to Raspberry Pi.
- **Writing Python Code to Control Buzzer:**
  ```python
  from gpiozero import Buzzer
  from time import sleep
  buzzer = Buzzer(18)
  while True:
      buzzer.on()
      sleep(1)
      buzzer.off()
      sleep(1)
  ```

### **3. Working with a Relay (10 minutes)**  
- **What is a Relay?**
  - Electromechanical switch for controlling AC appliances.
- **Circuit Setup:** Connect a relay module to Raspberry Pi.
- **Python Code to Toggle Relay:**
  ```python
  from gpiozero import OutputDevice
  relay = OutputDevice(17)
  relay.on()  # Turns the relay ON
  relay.off() # Turns the relay OFF
  ```

### **4. Controlling a DC Motor using L298N Module (10 minutes)**  
- **Understanding Motor Driver Modules:**
  - L298N allows Raspberry Pi to control DC motors.
- **Python Code to Control a Motor:**
  ```python
  from gpiozero import Motor
  from time import sleep
  motor = Motor(forward=23, backward=24)
  motor.forward()
  sleep(2)
  motor.backward()
  sleep(2)
  motor.stop()
  ```

**Hands-on Activity:** Students control a buzzer, relay, and motor using Python scripts.

---

## **Part 2: Building a Smart Fan System (45 minutes)**

### **1. Introduction to the Smart Fan System (10 minutes)**  
- **Concept:** Automatically turn on a fan when temperature is high.
- **Components Used:** DHT11 Sensor, DC Fan, Raspberry Pi.

### **2. Circuit Setup (15 minutes)**  
- Connect DHT11 sensor to GPIO pin.
- Connect DC fan to relay module.

### **3. Writing the Python Code (20 minutes)**  
- Install required library:
  ```bash
  pip install Adafruit_DHT
  ```
- Python script to turn on fan based on temperature:
  ```python
  import Adafruit_DHT
  from gpiozero import OutputDevice
  from time import sleep

  sensor = Adafruit_DHT.DHT11
  pin = 4  # DHT11 connected to GPIO4
  relay = OutputDevice(17)  # Relay connected to GPIO17

  while True:
      humidity, temperature = Adafruit_DHT.read_retry(sensor, pin)
      print("Temp:", temperature, "C, Humidity:", humidity, "%")
      if temperature > 30:
          relay.on()
          print("Fan ON")
      else:
          relay.off()
          print("Fan OFF")
      sleep(5)
  ```

**Hands-on Activity:** Students build and test the Smart Fan System.

---

## **Wrap-Up & Q&A (10 minutes)**
- **Review:**
  - Actuators (Buzzer, Relay, DC Motor).
  - Smart Fan System using DHT11 and Relay.
- **Encourage Questions:** Address doubts students have.

---

## **Homework/Practice Task**
- Modify the Smart Fan System to also turn on a buzzer when the temperature is high.
- Try controlling a servo motor with Raspberry Pi.

---

## **Summary of Session 2 (Day 2)**
✅ **Understanding and controlling actuators (Buzzer, Relay, DC Motor).**
✅ **Hands-on programming for real-world applications.**
✅ **Building an IoT-based Smart Fan System.**

