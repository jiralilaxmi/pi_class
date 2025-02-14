**Session 2: IoT Security Basics & Smart Home Light Control (2 Hours)**

---

## **Part 1: IoT Security Basics (45 minutes)**

### **1. Why is IoT Security Important? (10 minutes)**
- IoT devices are connected to the internet, making them vulnerable to attacks.
- Common threats:
  - **Unauthorized Access:** Hackers gaining control of devices.
  - **Data Breaches:** Sensitive data leaks.
  - **Botnets:** Compromised IoT devices used for cyberattacks.
- Importance of security in smart homes, healthcare, and industry.

### **2. Best Practices for Securing IoT Devices (20 minutes)**
- **Changing Default Credentials:**
  - Default usernames/passwords are easily exploited.
  - Use strong, unique passwords.
- **Keeping Software Up to Date:**
  - Regular updates fix security vulnerabilities.
  - Use `sudo apt update && sudo apt upgrade -y` on Raspberry Pi.
- **Using Firewalls & Network Security:**
  - Disable unused ports.
  - Use `ufw` (Uncomplicated Firewall) for securing connections.
  ```bash
  sudo apt install ufw
  sudo ufw enable
  sudo ufw allow 22/tcp  # Allow SSH
  sudo ufw allow 5000/tcp  # Allow Flask web server
  ```

### **3. Encryption & Secure Communication (15 minutes)**
- **Using HTTPS Instead of HTTP:**
  - Secure web traffic with SSL/TLS.
- **Data Encryption:**
  - Use `AES` or `RSA` for encrypting IoT communication.
- **Example of Encrypting Data in Python:**
  ```python
  from cryptography.fernet import Fernet
  
  key = Fernet.generate_key()
  cipher = Fernet(key)
  encrypted_text = cipher.encrypt(b"Hello, Secure IoT")
  decrypted_text = cipher.decrypt(encrypted_text)
  print(decrypted_text.decode())
  ```

**Hands-on Activity:**
- Students enable `ufw` on their Raspberry Pi and try encrypting a sample message.

---

## **Part 2: Hands-on Project - Smart Home Light Control (45 minutes)**

### **1. Introduction to Smart Home Automation (10 minutes)**
- **How IoT Controls Smart Devices:**
  - Sensors collect data.
  - A microcontroller (Raspberry Pi) processes commands.
  - Actuators (LEDs, relays) perform actions.
- **Example Applications:**
  - Controlling lights with voice commands.
  - Scheduling devices with a mobile app.

### **2. Controlling an LED via Web Interface (20 minutes)**
- **Connecting LED to Raspberry Pi GPIO:**
  - **Circuit:**
    - GPIO 17 → LED (+)
    - Ground → LED (-)
- **Flask Server to Control LED:**
  ```python
  from flask import Flask, render_template
  import RPi.GPIO as GPIO
  
  GPIO.setmode(GPIO.BCM)
  LED_PIN = 17
  GPIO.setup(LED_PIN, GPIO.OUT)
  
  app = Flask(__name__)
  
  @app.route("/on")
  def led_on():
      GPIO.output(LED_PIN, GPIO.HIGH)
      return "LED is ON"
  
  @app.route("/off")
  def led_off():
      GPIO.output(LED_PIN, GPIO.LOW)
      return "LED is OFF"
  
  if __name__ == '__main__':
      app.run(host='0.0.0.0', port=5000)
  ```
- **Running the Web Server & Controlling LED:**
  ```bash
  python led_control.py
  ```
- **Accessing Controls on a Browser:**
  - `http://<raspberry_pi_ip>:5000/on` → Turns LED ON
  - `http://<raspberry_pi_ip>:5000/off` → Turns LED OFF

**Hands-on Activity:**
- Students wire up an LED and control it via their web browser.

### **3. Extending to Relay & Home Appliances (15 minutes)**
- **Using a Relay Module to Control AC Devices:**
  - Similar to LED but connects high-voltage appliances.
  - Replace LED circuit with relay module.
- **Modifying Code for Relay Control:**
  ```python
  RELAY_PIN = 18
  GPIO.setup(RELAY_PIN, GPIO.OUT)
  ```
- **Demo:**
  - Students connect a small fan or bulb to the relay and control it from their browser.

---

## **Wrap-Up & Q&A (10 minutes)**
- **Review:**
  - IoT security best practices.
  - Secure communication methods.
  - Building a smart home light control system.
- **Encourage Questions:** Troubleshoot any issues students faced.

---

## **Homework/Practice Task**
- Modify the Flask web server to include a button UI for LED control instead of typing URLs.
- Research and implement MQTT for better device communication.

---

## **Summary of Session 2 (Day 4)**
✅ **Understanding IoT Security & Best Practices.**
✅ **Using Firewalls & Encryption for Secure IoT Communication.**
✅ **Building a Smart Home Light Control System Using Flask & Raspberry Pi.**

