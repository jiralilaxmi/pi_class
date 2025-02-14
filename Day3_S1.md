**Session 1: IoT Communication & Setting Up MQTT Broker (2 Hours)**

---

## **Part 1: Understanding IoT Communication & Protocols (45 minutes)**

### **1. Introduction to IoT Communication (10 minutes)**  
- **What is IoT Communication?**
  - The process of devices exchanging data over a network.
  - IoT devices use different communication protocols to send and receive information.

### **2. IoT Communication Protocols (15 minutes)**  
- **Comparison of IoT Protocols:**
  - **HTTP (Hypertext Transfer Protocol):** Used for web-based IoT applications.
  - **MQTT (Message Queuing Telemetry Transport):** Lightweight and efficient for IoT.
  - **CoAP (Constrained Application Protocol):** Used for low-power devices.

**Why MQTT is Preferred for IoT?**
  - Designed for low-bandwidth networks.
  - Works on the publish-subscribe model.
  - Efficient for real-time communication.

### **3. Understanding the MQTT Architecture (20 minutes)**  
- **Components of MQTT:**
  - **Broker:** Centralized server that manages message delivery.
  - **Publisher:** Device that sends data.
  - **Subscriber:** Device that receives data.
- **How MQTT Works:**
  - Devices publish messages to topics.
  - Subscribers receive messages from topics they are subscribed to.

**Hands-on Activity:**
- Students discuss real-world IoT applications where MQTT is used.

---

## **Part 2: Setting Up MQTT Broker (45 minutes)**

### **1. Installing Mosquitto MQTT Broker on Raspberry Pi (15 minutes)**  
- **Why Mosquitto?**
  - Free and lightweight MQTT broker.
- **Installation Commands:**
  ```bash
  sudo apt update
  sudo apt install mosquitto mosquitto-clients -y
  ```
- **Starting the Mosquitto Service:**
  ```bash
  sudo systemctl start mosquitto
  sudo systemctl enable mosquitto
  ```

### **2. Testing MQTT Communication on Raspberry Pi (30 minutes)**  
- **Opening Two Terminal Windows:**
  - **Publisher Terminal:**
    ```bash
    mosquitto_pub -h localhost -t test/topic -m "Hello IoT"
    ```
  - **Subscriber Terminal:**
    ```bash
    mosquitto_sub -h localhost -t test/topic
    ```
  - When the publisher sends a message, the subscriber receives it in real-time.

**Hands-on Activity:**
- Students publish and subscribe to messages using Mosquitto.

---

## **Wrap-Up & Q&A (10 minutes)**
- **Review:**
  - IoT communication protocols and their differences.
  - MQTT architecture and setup.
  - Sending messages using Mosquitto.
- **Encourage Questions:** Address any doubts students have.

---

## **Homework/Practice Task**
- Experiment with publishing temperature data using a Python script.
- Research how to connect multiple devices using MQTT.

---

## **Summary of Session 1 (Day 3)**
✅ **Understanding IoT communication protocols.**
✅ **Introduction to MQTT and its architecture.**
✅ **Setting up and testing an MQTT broker on Raspberry Pi.**

