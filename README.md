# V2X Cyclist Safety System

## 🧠 Overview
This project builds a **machine learning based V2X (Vehicle-to-Everything) safety ecosystem** aimed at enhancing road safety for cyclists and surrounding vehicles.  
The system integrates **mmWave radar**, **GPS**, and **IMU sensors** on a **Raspberry Pi 5** mounted on the bicycle to create an **intelligent, self-aware cyclist node** that communicates bi-directionally with approaching vehicles.

---

## ⚙️ System Concept
The ecosystem is powered by **two interconnected machine learning models** deployed on the cyclist’s Raspberry Pi:

### 🚗 **Model 1 — Environmental Risk Prediction (Radar-Based)**
- **Input:** mmWave radar data from the cyclist’s rear-mounted sensor (object range, velocity, angle).  
- **Output:** Risk category — `Safe`, `Warning`, or `Critical`.  
- **Function:** Detects approaching vehicles and estimates the probability of collision risk.  
- **Action:**  
  - Sends a **real-time haptic alert** via a wearable vest (TactSuit).  
  - Logs risk prediction data for further analysis.

### 🚴‍♀️ **Model 2 — Cyclist Reaction Prediction (GPS + IMU-Based)**
- **Input:** GPS and IMU data from the bicycle (speed, acceleration, orientation, braking, leaning angle).  
- **Output:** Cyclist behavior state — `Stable`, `Brake`, or `Evasive Maneuver`.  
- **Function:** Predicts the cyclist’s physical reaction after receiving the alert.  
- **Action:** Transmits this reaction data wirelessly to **approaching vehicles**, enabling them to adjust behavior (e.g., reduce speed or increase distance).

Together, these models form a **real-time, closed-loop V2X communication system**:
> **Radar detects → ML predicts → Haptic warns cyclist → GPS/IMU track reaction → ML predicts response → Alert sent to vehicle**

---

## 🧩 System Architecture
**Hardware Components**
- Raspberry Pi 5 (processing unit)  
- TI IWR6843ISK mmWave Radar (rear-mounted on bicycle)  
- SparkFun NEO-M8U GPS module  
- Adafruit BNO08x IMU module  
- TactSuit haptic feedback vest  
- LM2596 voltage regulator and 11.1 V Li-ion battery pack  

**Software Stack**
- Python 3  
- scikit-learn / TensorFlow  
- NumPy · pandas · matplotlib  
- Socket/Wi-Fi communication for data exchange  
- Ubuntu 24.04 / Raspberry Pi OS  

---

## 🤖 Machine Learning Pipeline
### **Model 1 – Risk Prediction**
- **Features:** Vehicle range, velocity, approach angle, time-to-collision.  
- **Output:** Risk level (`Safe`, `Warning`, `Critical`).  
- **Algorithm:** Random Forest / LSTM.  
- **Training Data:** Collected radar readings from real-world or simulated vehicle approach scenarios.  

### **Model 2 – Reaction Prediction**
- **Features:** Speed variation, acceleration, gyroscope data, braking pattern, heading change.  
- **Output:** Cyclist response (`Stable`, `Brake`, `Evasive`).  
- **Algorithm:** Random Forest / Neural Network.  
- **Training Data:** GPS + IMU data recorded during cyclist responses to alerts.

---

## Repository Structure
V2X-Cyclist-Safety-System/
├── data/ # Radar, GPS, and IMU datasets
├── radar_model/ # ML model for risk prediction
├── reaction_model/ # ML model for cyclist reaction
├── raspberry_pi/ # Real-time communication and control scripts
├── results/ # Confusion matrices, metrics, plots
├── docs/ # Circuit diagrams, setup guides, architecture images
└── README.md

---

## 🚀 System Workflow
1. Radar detects approaching vehicles.  
2. Risk Prediction Model (Model 1) estimates threat level.  
3. Haptic vest vibrates based on risk intensity.  
4. Cyclist reaction (braking, swerving, etc.) is captured by GPS + IMU.  
5. Reaction Prediction Model (Model 2) classifies cyclist response.  
6. System transmits alert + reaction data to nearby vehicles via Wi-Fi.  

---

## 🧪 Results
- End-to-end alert latency: **< 0.5 s**  
- Risk prediction accuracy: **XX %**  
- Reaction prediction accuracy: **XX %**  
- Reliable Wi-Fi V2X communication between cyclist and test vehicle.  

---

## 🔮 Future Improvements
- Integrate **Extended Kalman Filter (EKF)** for smoother sensor fusion.  
- Collect more outdoor data across traffic scenarios.  
- Optimize ML inference using **ONNX Runtime** or **TensorRT**.  
- Add cloud dashboard for visualizing risk and cyclist states in real time.  

---

## 👩‍💻 Author
**Sapan Parikh**  
M.S. in Machine Learning Engineering | Drexel University  
📫 [LinkedIn](https://www.linkedin.com/in/sapan-parikh13/)  |  [GitHub](https://github.com/Sapan2003)
