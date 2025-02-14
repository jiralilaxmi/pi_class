**Session 1: Introduction to Web-Based IoT & Hosting a Web Server (2 Hours)**

---

## **Part 1: Introduction to Web-Based IoT (45 minutes)**

### **1. What is Web-Based IoT? (10 minutes)**
- **Definition:** Web-based IoT allows users to monitor and control IoT devices remotely using a web interface.
- **Examples:**
  - Smart home automation (controlling lights, fans, etc.).
  - Remote weather monitoring dashboards.
  - Industrial IoT applications.

### **2. Web Servers in IoT (15 minutes)**
- **What is a Web Server?**
  - A server that listens for HTTP requests and responds with web pages or data.
- **Why Use Web Servers in IoT?**
  - Provides remote access to sensor data.
  - Enables user interaction with IoT devices.
- **Common Web Technologies Used:**
  - HTML, CSS, JavaScript for front-end.
  - Flask (Python) for back-end processing.

### **3. Setting Up a Flask Web Server on Raspberry Pi (20 minutes)**
- **Installing Flask:**
  ```bash
  pip install flask
  ```
- **Creating a Simple Flask Server:**
  ```python
  from flask import Flask
  
  app = Flask(__name__)
  
  @app.route('/')
  def home():
      return "Hello, IoT World!"
  
  if __name__ == '__main__':
      app.run(host='0.0.0.0', port=5000)
  ```
- **Running the Server:**
  ```bash
  python server.py
  ```
- **Accessing the Server:**
  - Open a browser and go to `http://<raspberry_pi_ip>:5000`

**Hands-on Activity:**
- Students set up and run their own Flask web server.

---

## **Part 2: Creating a Web Dashboard to Display Sensor Data (45 minutes)**

### **1. Displaying Live Sensor Data on a Web Page (20 minutes)**
- **Modifying Flask Server to Send Sensor Data:**
  ```python
  import Adafruit_DHT
  from flask import Flask, jsonify
  
  app = Flask(__name__)
  
  @app.route('/sensor')
  def get_sensor_data():
      humidity, temperature = Adafruit_DHT.read_retry(11, 4)
      return jsonify({'temperature': temperature, 'humidity': humidity})
  
  if __name__ == '__main__':
      app.run(host='0.0.0.0', port=5000)
  ```
- **Accessing Sensor Data:**
  - Open `http://<raspberry_pi_ip>:5000/sensor` in a browser.

**Hands-on Activity:**
- Students modify the script to read data from another sensor.

### **2. Designing a Simple Web Page for Data Visualization (25 minutes)**
- **Creating an HTML Page (`index.html`):**
  ```html
  <html>
  <head>
      <script>
          function fetchData() {
              fetch('/sensor')
                  .then(response => response.json())
                  .then(data => {
                      document.getElementById('temp').innerText = data.temperature;
                      document.getElementById('humidity').innerText = data.humidity;
                  });
          }
          setInterval(fetchData, 5000);
      </script>
  </head>
  <body>
      <h1>Sensor Data</h1>
      <p>Temperature: <span id='temp'></span>°C</p>
      <p>Humidity: <span id='humidity'></span>%</p>
  </body>
  </html>
  ```
- **Serving the HTML Page via Flask:**
  ```python
  from flask import Flask, render_template
  
  app = Flask(__name__)
  
  @app.route('/')
  def home():
      return render_template('index.html')
  ```
- **Placing `index.html` in a `templates/` folder** and running Flask.

**Hands-on Activity:**
- Students create and test their own web-based dashboard.

---

## **Wrap-Up & Q&A (10 minutes)**
- **Review:**
  - How to host a Flask web server.
  - Fetching and displaying real-time sensor data on a web page.
- **Encourage Questions:** Help students debug issues.

---

## **Homework/Practice Task**
- Modify the web page to show a live graph of temperature changes using JavaScript.
- Experiment with CSS to improve the dashboard's design.

---

## **Summary of Session 1 (Day 4)**
✅ **Understanding Web-Based IoT and its applications.**
✅ **Hosting a Flask web server on Raspberry Pi.**
✅ **Fetching and displaying sensor data on a web dashboard.**

