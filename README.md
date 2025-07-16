# 🌡️ ESP32 DHT11 Firebase Live Monitor

This project uses an **ESP32** microcontroller and a **DHT11** sensor to collect temperature and humidity data and uploads it in real-time to **Firebase Realtime Database**. The live data is then displayed on a web page with automatic updates every 5 seconds.

## 🔧 Features

- Read temperature and humidity using DHT11 sensor.
- Connect ESP32 to Wi-Fi and send data to Firebase.
- Display live sensor values on a modern web dashboard.
- Auto-refresh data on the frontend using JavaScript + Firebase.

---

## 📷 Project Preview

<img src="https://raw.githubusercontent.com/Shivangi-022/esp32/main/preview.png" alt="Live Sensor Dashboard" width="600"/>

---

## 🧰 Hardware Requirements

- ESP32 development board
- DHT11 temperature and humidity sensor
- Jumper wires
- Breadboard
- USB cable

---

## 📁 File Structure

```

esp32/
├── esp32\_dht11\_firebase.ino   # ESP32 Arduino code
├── index.html                 # Web interface to display live data
└── README.md                  # Project documentation (this file)

````

---

## 🧪 Sensor Wiring (DHT11 to ESP32)

| DHT11 Pin | ESP32 Pin |
|----------:|:----------|
| VCC       | 3.3V      |
| DATA      | GPIO 4    |
| GND       | GND       |

> ⚠️ Ensure you connect the data pin to GPIO4 as defined in the code (`#define DHTPIN 4`).

---

## 🚀 Setup & Deployment

### 1. Firebase Setup

- Go to [Firebase Console](https://console.firebase.google.com/)
- Create a new project (e.g., `esp32-dht11`)
- Enable Realtime Database
- Set the database rules to:

```json
{
  "rules": {
    ".read": true,
    ".write": true
  }
}
````

* Note the **Database URL**, e.g.,
  `https://dht11-a5753-default-rtdb.firebaseio.com/`

---

### 2. Arduino IDE Setup

#### Required Libraries

Install the following libraries via Library Manager:

* **DHT sensor library by Adafruit**
* **Adafruit Unified Sensor**
* **WiFi (comes built-in with ESP32 support)**
* **HTTPClient (comes built-in)**

#### Code Upload

* Open `esp32_dht11_firebase.ino`
* Replace Wi-Fi credentials:

```cpp
const char* ssid = "your_wifi_name";
const char* password = "your_wifi_password";
```

* Replace Firebase URL:

```cpp
const char* firebaseHost = "https://<your-project-id>.firebaseio.com/sensordata.json";
```

* Connect ESP32 and upload the code.

---

## 🌐 Web Dashboard Setup

1. Open `index.html` in a browser
2. It will automatically fetch and display data from Firebase
3. Auto-refreshes every 5 seconds

> You can host it using GitHub Pages, Netlify, Firebase Hosting, or simply open the HTML file in a browser.

---

## 📊 Sample JSON Data Sent to Firebase

```json
{
  "sensorid": "DHT-11",
  "samplename": "Weather",
  "temp": 26.4,
  "hum": 55.2
}
```

---

## 🛠️ Troubleshooting

* **No Data on Webpage?**

  * Check Firebase URL in both `index.html` and `.ino` files.
  * Ensure Firebase Realtime Database rules allow read/write.
* **ESP32 Not Connecting?**

  * Double-check Wi-Fi SSID and password.
  * Use Serial Monitor to debug connection issues.
* **Incorrect Temperature/Humidity?**

  * Check sensor wiring and make sure DHT type is set to `DHT11`.

---

## 📄 License

MIT License

---

## 🙋‍♀️ Author

Made with ❤️ by [Shivangi](https://github.com/Shivangi-022)

---
