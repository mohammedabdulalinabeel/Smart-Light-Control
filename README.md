# Smart-Light-Control
Control an LED light with Arduino and Mobile App


## 🚀 Project Title
Design a System to Control an LED Light Using a Microcontroller and a Mobile App

---

## 📋 Intern Details

- **👨‍💼 Name:** Mohammed Abdul Ali Nabeel
- **🎓 Intern ID:** CITS0D781
- **🏢 Company:** CodTech IT Solutions
- **🌐 Domain:** Internet of Things (IoT)
- **📅 Internship Duration:** 4 Weeks
- **🧑‍🏫 Mentor:** Neela Santhosh

---

## 📌 Project Overview

This project demonstrates a **smart lighting system** using **Arduino Uno** or **NodeMCU** and the **Blynk app** to remotely control an LED light.  
The LED responds instantly to commands sent from a mobile app, representing a simple yet effective **IoT automation prototype**.

---

## 🔧 Components Required

| Component               | Quantity         |
|-------------------------|------------------|
| Arduino Uno / NodeMCU   | 1                |
| LED                     | 1                |
| 220Ω Resistor           | 1                |
| Blynk App (Mobile)      | 1                |
| Jumper Wires            | As required      |
| USB Cable               | 1                |
| Wi-Fi Connection        | 1 (for NodeMCU)  |

---

## 🧩 Circuit Connections (For Arduino Uno)

| Component | Arduino Pin        |
|-----------|--------------------|
| LED +     | Digital Pin 7      |
| LED -     | GND (via resistor) |

---

## 📱 Blynk App Setup Instructions

1. Download and install the **Blynk IoT App** from Play Store or App Store.
2. Create a **New Project**:
   - Device: *NodeMCU* or *Arduino Uno (with ESP8266)*
   - Connection Type: *WiFi*
3. Add a **Button Widget**:
   - Set to: **Virtual Pin V0**
   - Mode: **Switch**

---

## 💻 Arduino Code (`smart_light.ino`)

### ▶ For NodeMCU (Wi-Fi Enabled):

```cpp
#define BLYNK_TEMPLATE_ID "YourTemplateID"
#define BLYNK_TEMPLATE_NAME "SmartLight"
#define BLYNK_AUTH_TOKEN "YourAuthToken"

#include <ESP8266WiFi.h>
#include <BlynkSimpleEsp8266.h>

char auth[] = "YourAuthToken";
char ssid[] = "YourWiFiName";
char pass[] = "YourWiFiPassword";

#define LED_PIN D1

void setup() {
  pinMode(LED_PIN, OUTPUT);
  Blynk.begin(auth, ssid, pass);
}

BLYNK_WRITE(V0) {
  int value = param.asInt(); // 1 = ON, 0 = OFF
  digitalWrite(LED_PIN, value);
}

void loop() {
  Blynk.run();
}
