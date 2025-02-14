# **Session 2: Linux Basics, Remote Access & Running Your First Python Program (2 Hours)**

---

## **Part 1: Basic Linux Commands for Raspberry Pi (45 minutes)**

### **1. Introduction to Linux & Why It's Used in Raspberry Pi (10 minutes)**  
- Raspberry Pi OS is based on Linux, an open-source and stable operating system.
- **Why Linux for IoT?**  
  - Most IoT devices use Linux-based OS.
  - It’s free, customizable, and gives full control over Raspberry Pi.

### **2. Navigating the Linux File System (15 minutes)**  
Essential Linux commands:
- **Checking current directory:** `pwd`
- **Listing files and folders:** `ls`
- **Changing directories:** `cd`
- **Creating a new folder:** `mkdir my_folder`
- **Creating a file:** `touch my_file.txt`
- **Editing a file:** `nano my_file.txt`
- **Removing files and folders:** `rm my_file.txt`, `rmdir my_folder`

**Hands-on Activity:**
- Students create a folder, add a file inside it, write content using `nano`, save, and delete it.

### **3. Networking & Installing Packages (20 minutes)**
- **Checking Internet Connection:** `ping google.com`
- **Updating Raspberry Pi:** `sudo apt update && sudo apt upgrade -y`
- **Installing a package:** `sudo apt install git -y`
- **Checking the IP Address:** `hostname -I`

**Hands-on Activity:**
- Students install `figlet` and try:
  ```bash
  sudo apt install figlet -y
  figlet Hello
  ```

---

## **Part 2: Connecting to Raspberry Pi Remotely (SSH & VNC) (30 minutes)**

### **1. What is SSH and Why Use It? (10 minutes)**
- SSH (**Secure Shell**) allows remote control of Raspberry Pi.
- Useful for **headless setups** (no monitor/keyboard needed).

### **2. Enabling SSH on Raspberry Pi (10 minutes)**  
- Run:
  ```bash
  sudo raspi-config
  ```
- Navigate to **Interfacing Options → SSH → Enable**.

### **3. Connecting via SSH from Another Computer (10 minutes)**
- **Windows:** Use **PuTTY** to enter Raspberry Pi’s IP address.
- **Linux/macOS:** Open terminal:
  ```bash
  ssh pi@<your_pi_ip>
  ```
- Example:
  ```bash
  ssh pi@192.168.1.10
  ```
- Enter password (`raspberry` by default).

**Hands-on Activity:**
- Students SSH into Raspberry Pi from their laptops.

---

## **Part 3: Running Your First Python Program (45 minutes)**

### **1. Introduction to Python on Raspberry Pi (10 minutes)**
- Raspberry Pi supports **Python** for IoT projects.
- Open Python interpreter:
  ```bash
  python3
  ```
- Run:
  ```python
  print("Hello, Raspberry Pi!")
  ```

### **2. Writing and Running a Python Script (20 minutes)**  
- Open a text editor:
  ```bash
  nano hello.py
  ```
- Inside `hello.py`, type:
  ```python
  print("Hello, IoT World!")
  ```
- Save and run:
  ```bash
  python3 hello.py
  ```
- Output:
  ```
  Hello, IoT World!
  ```

**Hands-on Activity:**
- Students write a script to print their name and favorite subject.

### **3. Basic Python Programming Concepts (15 minutes)**
- **Variables:**
  ```python
  name = "Alice"
  age = 17
  print("My name is", name, "and I am", age, "years old.")
  ```
- **Loops:**
  ```python
  for i in range(5):
      print("Iteration", i)
  ```
- **User Input:**
  ```python
  user_name = input("Enter your name: ")
  print("Hello,", user_name)
  ```

**Hands-on Activity:**
- Modify script to ask for name and favorite hobby, then print it.

---

## **Wrap-Up & Q&A (10 minutes)**
- **Review:**
  - Linux commands & file navigation.
  - Remote access via SSH.
  - Running a Python program.
- **Ask for Doubts:** Encourage student questions.

---

## **Homework/Practice Task**
- Modify the Python script to ask for name and favorite hobby, then print it.

---

## **Summary of Session 2 (Day 1)**
✅ **Linux Basics** (File handling, package installation, networking).
✅ **SSH Setup & Remote Access** (Connecting Raspberry Pi without a monitor).
✅ **Running a Python Program** (Hands-on with basic coding).

