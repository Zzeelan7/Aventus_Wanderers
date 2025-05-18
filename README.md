# Aventus_Wanderers
RescueBot: Heat and Sound-Sensing Robot



# Avent Hackathon 2025 | Team [Wanderers]

# Overview

RescueBot is a heat and sound-sensing robot designed to detect human presence in disaster scenarios, built for the Avent Hackathon 2025. It uses an ESP32 with an INMP441 microphone for audio detection and an Arduino with an MLX90614 sensor for thermal sensing, achieving ~90% accuracy with a TensorFlow Lite Micro (TFLM) model (audio) and logistic regression (thermal). Results are displayed on a Flask-based website, enabling real-time monitoring for rescue operations.

# Features





Audio Detection: Captures sound via INMP441 (ESP32, I2S) to identify human presence (e.g., voices, tapping).



Thermal Sensing: Measures temperature with MLX90614 (Arduino Uno) to detect body heat.



ML-Powered: Audio classification (TFLM, ESC-50 dataset) and thermal classification (logistic regression, UCI HAR-derived).



Bluetooth Integration: ESP32 sends audio data via HTTP POST; Arduino sends thermal data via serial.



Dynamic Website: Flask app displays detection reports (status, confidence, timestamp).



Low-Cost: ~$30 per unit (ESP32: $8, INMP441: $3, Arduino Uno: $10, MLX90614: $8, misc: $1).



# Hardware Setup







ESP32 DevKit v1 + INMP441:





I2S: GPIO14 (WS), GPIO15 (SCK), GPIO32 (SD).



Power: 3.3V, GND.



Arduino Uno + MLX90614:





I2C: A4 (SDA), A5 (SCL).



Power: 5V or 3.3V, GND.



Connections: Breadboard, jumper wires.



# Repository Structure



RescueBot-Hackathon/
├── docs/                     # Documentation and images
│   ├── rescuebot_logo.png
│   ├── website_screenshot.png
│   └── hardware_setup.png
├── models/                   # ML models
│   ├── audio_model.py
│   └── thermal_model.py
├── templates/                # Flask templates
│   ├── index.html
│   ├── results.html
│   ├── about.html
│   └── about_us.html
├── Avent_Hack.ipynb          # Model training notebook
├── app.py                    # Flask backend
├── rescuebot.ino             # ESP32 firmware
├── thermal_sensor.ino        # Arduino firmware
├── requirements.txt          # Python dependencies
└── README.md



# Prerequisites





Hardware:





ESP32 DevKit v1, INMP441 microphone, Arduino Uno, MLX90614 sensor, breadboard, jumper wires.



Software:





Arduino IDE (2.3.2+), Python 3.8+, Git, ngrok.



Dependencies:





Arduino libraries: WiFi, HTTPClient, ESP32 I2S, Adafruit_MLX90614.



Python packages: See requirements.txt.



Setup Instructions





Clone Repository:



git clone https://github.com/Zzeelan7/Aventus_Wanderers.git
cd Aventus_Wanderers



Hardware Setup:





Connect ESP32 to INMP441 (I2S: GPIO14/WS, GPIO15/SCK, GPIO32/SD, 3.3V, GND).



Connect Arduino Uno to MLX90614 (I2C: A4/SDA, A5/SCL, 5V or 3.3V, GND).



Power both via USB.



ESP32 Firmware:





Open rescuebot.ino in Arduino IDE.



Update WiFi SSID/password and Flask URL (ngrok or local IP).



Install libraries: WiFi, HTTPClient, ESP32 I2S.



Select “ESP32 Dev Module” and upload.



Arduino Firmware:





Open thermal_sensor.ino in Arduino IDE.



Install library: Adafruit_MLX90614.



Select “Arduino Uno” and upload.



Flask Website:





Install dependencies:




pip install -r requirements.txt




Run Flask:




python app.py




python app.py




Access: https://<ngrok-url> (update ESP32 firmware with this URL).



# ML Models:





Audio: Run Avent_Hack.ipynb in Colab to train/save yamnet.tflite to models/.



Thermal: Logistic regression model in thermal_model.py.



# Usage





Run RescueBot:





Power ESP32 and Arduino Uno.



Start Flask (python app.py) and ngrok.



Open https://<ngrok-url> in a browser.



# Test Detection:





Click “Generate Report” on the homepage.



Audio: Tap near INMP441 → Expect “HUMAN DETECTED” (e.g., 92% confidence).



Thermal: Point MLX90614 at skin → Expect “HUMAN DETECTED” (e.g., 85% confidence).



# Explore:





Website: Home, Results, About, About Us pages.




# Results



The table above shows a sample report with audio and thermal detection results, including status, confidence, and timestamp. Green indicates “HUMAN DETECTED”; red indicates “NO HUMAN”.





# Future Work





Sensor Fusion: Combine audio and thermal data for higher accuracy.



Mobile App: Develop a companion app for real-time alerts.



Battery Power: Add battery packs for portability.



Scalable IoT: Deploy multiple units with a central dashboard.



# Acknowledgments





Avent Hackathon 2025.



TensorFlow Lite Micro, Flask, Arduino.



ESC-50 dataset, UCI HAR dataset.



# Contact

[zzeelan7@gmail.com] or GitHub Issues.
