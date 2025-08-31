# 🌱 Automatic Irrigation System  

A simple **Arduino Nano based automatic irrigation system** that automatically waters plants when the soil moisture level goes below a set threshold. The system helps conserve water and ensures plants receive optimal care without constant manual intervention.  

---

## 🚀 Features  
- Monitors soil moisture using a soil moisture sensor.  
- Automatically turns **water pump ON** when soil is dry.  
- Turns **pump OFF** when soil moisture reaches threshold.  
- Uses a **relay module** for safe switching of the water pump.  
- Low-cost, simple, and efficient for small gardens/pots.  

---

## 🛠️ Components Used  
- **Arduino Nano**  
- **Soil Moisture Sensor**  
- **Relay Module (5V)**  
- **Mini Water Pump** (DC pump)  
- **PCB dotted board**  
- **Female connector for external power supply**  
- **Jumper wires, tubing, and container housing ** 

---

## ⚡ Circuit Diagram  
📌<img width="273" height="185" alt="image" src="https://github.com/user-attachments/assets/95901152-5e94-43b8-84d5-b27dc06f91c1" />


Connections:  
- Soil Moisture Sensor → Arduino A0 (Analog input)  
- Relay IN → Arduino D7 (Digital output)  
- Pump → Relay → External Power Supply (Vcc & GND)  
- Arduino powered via USB or external adapter  

---

## 📟 Working Principle  
1. Soil moisture sensor continuously measures soil resistance.  
2. If the value is **below threshold (dry soil)** → Arduino activates relay → Pump turns ON.  
3. If the value is **above threshold (wet soil)** → Relay deactivates → Pump turns OFF.  

---

## 🔑 Arduino Code  

```cpp
#define sensorPin A0
#define relayPin 7
int threshold = 500;  // Adjust according to soil moisture calibration

void setup() {
  pinMode(relayPin, OUTPUT);
  digitalWrite(relayPin, HIGH); // Relay OFF initially
  Serial.begin(9600);
}

void loop() {
  int sensorValue = analogRead(sensorPin);
  Serial.print("Soil Moisture: ");
  Serial.println(sensorValue);

  if (sensorValue > threshold) {  
    digitalWrite(relayPin, LOW);  // Pump ON
    Serial.println("Soil Dry → Pump ON");
  } else {
    digitalWrite(relayPin, HIGH); // Pump OFF
    Serial.println("Soil Wet → Pump OFF");
  }
  
  delay(1000);
}
```

---

## 📸 Project Setup  
  ![WhatsApp Image 2025-08-31 at 8 59 22 PM](https://github.com/user-attachments/assets/37e708b5-01d4-46d5-8be5-8a569152839d)

---

## 💡 Future Improvements  
- Add **IoT connectivity (ESP32/Blynk)** for remote monitoring.  
- Include **DHT11/22 sensor** for temperature & humidity.  
- Solar-powered irrigation for complete automation.  

---

## 👨‍💻 Author  
Developed by Jerald Jaxon  
Mini Project 
Diploma in Electronics Engineering  
