# 🚦 Smart Traffic Light Controller  
### AI-Powered Real-Time Intelligent Traffic Management System

Traditional traffic lights run on fixed timers, causing congestion, wasted fuel, and inefficient road usage. This project introduces an **AI-driven, real-time traffic control system** capable of dynamically adjusting signal timings based on **live vehicle density** using **computer vision + simulation**.

---

## 📌 Features

- 🔍 Real-time vehicle detection using YOLOv8 + OpenCV  
- 🤖 Intelligent signal switching based on vehicle density  
- ⏱️ Dynamic green time calculation using traffic load + vehicle types  
- 🧵 Multithreaded architecture (Detection + Signal Control)  
- 🚗 Traffic simulation built using PyGame  
- 📊 Performance comparison with traditional fixed signals  

---

## 🧠 System Architecture

### 1️⃣ Vehicle Detection Module
- Uses **YOLOv8** for accurate, real-time vehicle detection and classification  
- OpenCV processes video frames and identifies vehicle counts per lane  

**Sample Outputs**

Traffic movement from live feed:  
![image](https://github.com/user-attachments/assets/d3e98b2f-3665-4a21-8748-a0438d80707f)

YOLOv8 detection using OpenCV:  
![image](https://github.com/user-attachments/assets/ae22e527-3124-4336-beb7-a818b54127ea)

---

### 2️⃣ Signal Switching Algorithm
A multithreaded controller manages signal transitions:

- Cyclic order: **Red → Green → Yellow → Red**
- Dynamic adjustment of green time based on real-time vehicle count  
- Parallel processing:  
  - **Thread 1:** Vehicle detection  
  - **Thread 2:** Traffic signal control  

This ensures smooth and congestion-free flow even under uneven traffic loads.

---

### 3️⃣ Dynamic Green Time Calculation

Green signal time is calculated using:

- Vehicle count per lane  
- Vehicle class (car, bus, truck, bike)  
- Estimated crossing time per vehicle  
- Lane width and number of lanes  
- Start-up delay and typical vehicle speed  

This results in real-world–accurate timing and highly efficient traffic movement.

---

### 4️⃣ Simulation Module (PyGame)

A custom 4-way intersection simulation designed with **PyGame** supports:

- Realistic vehicle movement  
- Random turning behavior  
- Countdown timers on signals  
- Live visualization of smart vs traditional signal performance  

**Simulation Demo**  
![image](https://github.com/user-attachments/assets/161d22f1-621e-4fbd-bab6-878f2e24d1e9)

---

## 📝 Flowchart  
![image](https://github.com/user-attachments/assets/5fda893b-61cf-49b3-9b99-54b5ab9907be)

---

## 📈 System Evaluation

Both systems (Traditional vs Smart AI Controller) were simulated for **15 runs**, each lasting **5 minutes**.  
The total number of vehicles passing through the intersection was recorded.

![image](https://github.com/user-attachments/assets/b4ffd007-ec33-45a3-9383-9cd062ac00e8)

**Result:**  
The AI-based system allows significantly more vehicles to pass through compared to traditional fixed-timer signals.

---

## 📂 Tech Stack

| Component | Technology |
|----------|------------|
| Vehicle Detection | YOLOv8, OpenCV |
| Simulation | PyGame |
| Logic & Timing | Python |
| Architecture | Multithreading |

---

## 🏁 How to Run

### 1. Clone the repository
```bash
git clone https://github.com/<your-username>/smart-traffic-light-controller.git
cd smart-traffic-light-controller

```

## 📦 YOLO Model Weights

The YOLO model file (e.g., `yolov8s.pt`) is **not included** in this repository due to file size limits.

The script will automatically download the required model when you run:

```python
from ultralytics import YOLO
model = YOLO("yolov8s.pt")  # auto-downloads model if missing
