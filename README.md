# IoT-Edge-AI-Smart-EV-Charging-Station
ESP32-based IoT prototype for smart EV charging using MQTT, ThingsBoard, Wokwi and Edge AI concepts.

# IoT and Edge AI Based Smart EV Charging Station

## 📌 Project Overview

The **IoT and Edge AI Based Smart EV Charging Station** is an embedded IoT prototype developed during my internship at **Emertxe Technologies**.

The project demonstrates how an **ESP32** can be used to acquire sensor data, process the data at the edge, communicate through **Wi-Fi and MQTT**, send telemetry to the **ThingsBoard** IoT platform, and control an actuator using a relay.

The project also explores the application of **Edge AI concepts** for local data analysis, anomaly detection, and intelligent decision-making in EV charging systems.

> **Note:** This is an educational/prototype project and is not intended to be used as a commercial EV charging system. A real EV charging station requires appropriate electrical protection, isolation, contactors, interlocks, charging-control hardware, and certified safety mechanisms.

---

## 🎯 Objectives

* Understand IoT-based embedded system architecture.
* Interface sensors with an ESP32.
* Understand ADC and GPIO-based data acquisition.
* Process sensor data using an embedded controller.
* Establish Wi-Fi connectivity.
* Implement MQTT-based communication.
* Understand the MQTT publish-subscribe architecture.
* Send telemetry data to ThingsBoard.
* Visualize device data through an IoT dashboard.
* Demonstrate the concept of remote actuator control.
* Simulate the embedded system using Wokwi.
* Understand the role of Edge AI in EV charging applications.

---

## 🏗️ System Architecture

```text
                    ┌──────────────────────┐
                    │       Sensors        │
                    │                      │
                    │ Voltage / Current /  │
                    │ Temperature / etc.   │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │        ESP32         │
                    │                      │
                    │ ADC / GPIO           │
                    │ Data Processing      │
                    │ Local Decision Logic │
                    └──────────┬───────────┘
                               │
                             Wi-Fi
                               │
                               ▼
                    ┌──────────────────────┐
                    │        MQTT          │
                    │  Communication Layer │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │     ThingsBoard      │
                    │                      │
                    │ Telemetry            │
                    │ Dashboard            │
                    │ Monitoring            │
                    └──────────┬───────────┘
                               │
                         Control Command
                               │
                               ▼
                    ┌──────────────────────┐
                    │        MQTT          │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │        ESP32         │
                    └──────────┬───────────┘
                               │
                              GPIO
                               │
                               ▼
                    ┌──────────────────────┐
                    │   Relay / Actuator   │
                    └──────────────────────┘
```

---

## ⚙️ Working Principle

The system follows these major steps:

1. Sensors measure parameters associated with the charging system.
2. The ESP32 acquires the sensor signals using ADC/GPIO interfaces.
3. The raw sensor readings are processed by the ESP32.
4. The ESP32 connects to the network using Wi-Fi.
5. Sensor data is formatted as telemetry data.
6. The telemetry is transmitted using MQTT.
7. ThingsBoard receives and displays the telemetry.
8. The dashboard can be used for monitoring the system.
9. A control command can be sent from the cloud side.
10. The command is transmitted to the ESP32 through MQTT.
11. The ESP32 processes the command and changes the appropriate GPIO state.
12. The GPIO can control a relay/actuator in the prototype.

---

## 🔄 Complete Data Flow

### Telemetry Flow

```text
Sensor
   ↓
ESP32
   ↓
Data Processing
   ↓
Wi-Fi
   ↓
MQTT
   ↓
ThingsBoard
   ↓
Dashboard
```

### Control Flow

```text
ThingsBoard
   ↓
MQTT
   ↓
ESP32
   ↓
GPIO
   ↓
Relay
   ↓
Actuator
```

---

## 🔌 ESP32

The ESP32 is used as the main embedded controller.

### Main responsibilities

* Sensor interfacing
* ADC-based data acquisition
* GPIO control
* Local data processing
* Wi-Fi communication
* MQTT communication
* Telemetry generation
* Receiving control commands
* Relay/actuator control

The ESP32 is suitable for this prototype because it combines microcontroller capabilities with built-in wireless connectivity.

---

## 📡 Wi-Fi and MQTT

### Wi-Fi

Wi-Fi provides network connectivity between the ESP32 and the IoT/cloud infrastructure.

```text
ESP32 → Wi-Fi Network → MQTT Infrastructure
```

### MQTT

**MQTT (Message Queuing Telemetry Transport)** is a lightweight messaging protocol commonly used in IoT systems.

It follows a **publish-subscribe model**.

```text
ESP32
   │
   │ Publish Telemetry
   ▼
MQTT Broker
   │
   │ Subscribe
   ▼
ThingsBoard
```

For control:

```text
ThingsBoard
   │
   │ Publish Command
   ▼
MQTT Broker
   │
   │ Subscribe
   ▼
ESP32
```

---

## ☁️ ThingsBoard

ThingsBoard is used as the IoT platform for device monitoring and telemetry visualization.

The platform can be used for:

* Device connectivity
* Telemetry collection
* Dashboard visualization
* Device monitoring
* Remote control concepts
* Historical data visualization

The general flow is:

```text
ESP32 → MQTT → ThingsBoard → Dashboard
```

---

## 📊 Sensor Data Acquisition

The general sensor data acquisition process is:

```text
Physical Parameter
        ↓
      Sensor
        ↓
 Electrical Signal
        ↓
       ADC
        ↓
 Digital Value
        ↓
Data Processing
        ↓
Meaningful Parameter
```

The ADC converts an analog signal into a digital value that can be processed by the ESP32.

Depending on the sensor, calibration and conversion equations may be required to obtain the corresponding physical parameter.

---

## 🔧 Relay-Based Control

The project demonstrates the concept of controlling an actuator using an ESP32 GPIO.

```text
ThingsBoard
     ↓
MQTT Command
     ↓
ESP32
     ↓
GPIO
     ↓
Relay
     ↓
Actuator
```

For a commercial EV charging station, a relay alone would not represent the complete charging-control and protection system. Properly rated contactors, electrical protection, isolation, interlocks, emergency shutdown, and certified charging hardware would be required.

---

## 🤖 Edge AI Concept

**Edge AI** refers to processing data and performing intelligent analysis closer to the data source instead of relying entirely on a remote cloud platform.

For EV charging applications, Edge AI can potentially support:

* Anomaly detection
* Abnormal charging-condition detection
* Local decision-making
* Predictive maintenance
* Charging optimization
* Detection of unusual sensor patterns

In this internship project, Edge AI was explored as a **concept and application area** rather than as a claim of a production-grade AI model.

---

## 🖥️ Wokwi Simulation

**Wokwi** was used to simulate the ESP32-based embedded system and test the basic hardware and firmware logic.

Simulation helps with:

* ESP32 firmware testing
* GPIO verification
* Sensor interface testing
* Debugging
* System connection verification
* Embedded system prototyping

### Wokwi Project

Add your Wokwi project link here:

```text
PASTE YOUR WOKWI PROJECT LINK HERE
```

---

## 🛠️ Technologies Used

| Technology         | Purpose                            |
| ------------------ | ---------------------------------- |
| **ESP32**          | Main embedded controller           |
| **Embedded C/C++** | Firmware development               |
| **ADC**            | Analog sensor data acquisition     |
| **GPIO**           | Digital I/O and actuator control   |
| **Wi-Fi**          | Wireless connectivity              |
| **MQTT**           | IoT messaging                      |
| **ThingsBoard**    | Cloud monitoring and visualization |
| **Wokwi**          | Embedded system simulation         |
| **JSON**           | Telemetry data representation      |
| **Relay**          | Prototype actuator control         |
| **Edge AI**        | Local intelligence concept         |

---

## 📁 Repository Structure

```text
IoT-Edge-AI-Smart-EV-Charging-Station/
│
├── README.md
│
├── src/
│   └── main.cpp
│
├── include/
│   └── config.h
│
├── docs/
│   ├── Project-Presentation.pdf
│   ├── Project-Report.pdf
│   └── System-Architecture.png
│
├── simulation/
│   ├── wokwi-project-link.txt
│   └── simulation-notes.md
│
├── dashboard/
│   ├── thingsboard-dashboard.png
│   └── dashboard-notes.md
│
└── screenshots/
    ├── wokwi-simulation.png
    ├── thingsboard-dashboard.png
    └── system-flow.png
```

---

## 📸 Project Screenshots

### Wokwi Simulation

Add your Wokwi simulation screenshot here.

```text
screenshots/wokwi-simulation.png
```

### ThingsBoard Dashboard

Add your ThingsBoard dashboard screenshot here.

```text
screenshots/thingsboard-dashboard.png
```

### System Architecture

Add your system architecture diagram here.

```text
screenshots/system-flow.png
```

---

## 📚 Key Learning Outcomes

Through this project, I gained practical exposure to:

* ESP32-based embedded development
* Sensor interfacing
* ADC and GPIO concepts
* Embedded firmware development
* Wi-Fi communication
* MQTT protocol
* Publish-subscribe architecture
* IoT telemetry
* ThingsBoard dashboards
* Remote device control
* Wokwi simulation
* JSON-based communication
* Edge AI concepts
* IoT system architecture
* Embedded system debugging

---

## 🚀 Future Improvements

The prototype can be extended with:

* Real-time current and voltage monitoring
* Energy consumption calculation
* State-of-charge estimation
* Advanced fault detection
* Machine-learning-based anomaly detection
* Local Edge AI inference
* Predictive maintenance
* Secure device authentication
* OTA firmware updates
* Historical energy analytics
* Advanced charging optimization
* Integration with a properly engineered EV charging control system

---

## ⚠️ Project Limitations

This project is an educational internship prototype.

It should not be treated as a production EV charging system.

A real EV charging station would require appropriate:

* Electrical isolation
* Overcurrent protection
* Overvoltage protection
* Earth-leakage protection
* Proper contactors
* Emergency shutdown
* Charging-control mechanisms
* Hardware safety interlocks
* Certified EV charging equipment
* Compliance with applicable electrical and charging standards

---

## 👩‍💻 Author

### Dharani M Dharwad

**Electronics and Communication Engineering**

Smt Kamala And Shri Venkappa M Agadi College of Engineering and Technology, Laxmeshwar, Karnataka

**Areas of Interest:**

* Embedded Systems
* IoT
* Microcontrollers
* Embedded C
* VLSI
* Edge Computing

### GitHub

https://github.com/DharaniDharwad

---

## 🏢 Internship

**Emertxe Technologies**

**Internship Area:** Embedded Systems / IoT

**Project:** IoT and Edge AI Based Smart EV Charging Station

---

## 🙏 Acknowledgement

I would like to thank **Emertxe Technologies** for providing me with the opportunity to gain practical exposure to embedded systems, IoT, ESP32 development, MQTT communication, cloud connectivity, simulation, and Edge AI concepts.

---

## 📄 License

This project is intended for educational and learning purposes.

