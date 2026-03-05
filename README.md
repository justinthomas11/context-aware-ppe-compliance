#  PPE Context Vision

A **Context-Aware Safety Gear Compliance System** that tracks workers, classifies workplace zones, and validates Personal Protective Equipment (PPE) compliance in real time.

---

## Problem

Industrial workplaces require different PPE depending on the risk level of each area. Most existing systems perform generic PPE detection without considering location or zone context — leading to false alarms, missed violations, and poor usability.

---

## Solution

**PPE Context Vision** is an intelligent monitoring system that:

- Tracks workers and assigns them persistent identities
- Classifies zones as **Safe (Office)**, **Moderate (Storage)**, or **High-Risk (Factory)**
- Validates PPE compliance dynamically based on zone risk
- Tags workers visually: 🟢 Green / 🟡 Yellow / 🔴 Red
- Generates explainable alerts describing what PPE is missing and why
- Uses temporal smoothing to reduce false positives over time

---

## Architecture

```
Simulated Worker Data (Hardcoded)
    ↓
Zone Classification (Safe / Moderate / High-Risk)
    ↓
PPE Validation per Worker
    ↓
Temporal Smoothing Engine
    ↓
Contextual Reasoning Engine
    ↓
Alert System (Green / Yellow / Red tagging)
    ↓
Streamlit Dashboard
```

---

## 📋 Zone-Based PPE Requirements

| Zone                    | Required PPE                              |
|-------------------------|-------------------------------------------|
| 🟢 Safe (Office)         | Basic work apparel                        |
| 🟡 Moderate (Storage)    | Long trousers, work shoes                 |
| 🔴 High-Risk (Factory)   | Long trousers, work shoes, goggles        |

---

## 📁 Project Structure

```
ppe_context_vision/
├── app.py
├── requirements.txt
├── config/
│   └── zones.json
├── core/
│   ├── zone_manager.py
│   ├── ppe_validator.py
│   ├── tracker.py
│   ├── temporal.py
│   ├── reasoning.py
│   └── alerts.py
├── utils/
│   └── geometry.py
└── ui/
    └── dashboard.py
```

---

## ⚙️ Setup & Installation

### 1. Clone the repo

```bash
git clone https://github.com/yourteam/ppe-context-vision
cd ppe-context-vision
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Run the dashboard

```bash
streamlit run ui/dashboard.py
```

---

## 🔧 Tech Stack

- **Python** — Core logic
- **OpenCV** — Video/image processing
- **YOLOv8** — Person detection
- **Streamlit** — Live compliance dashboard
- **NumPy / SciPy** — Geometry and signal processing

---

## 📌 Note on Simulation

Worker data (positions, PPE states, zone assignments) is **simulated using hardcoded values** to demonstrate the full pipeline end-to-end. This includes:

- Worker IDs with predefined bounding box positions
- PPE compliance states (helmet, goggles, boots, etc.) set per worker
- Zone assignments mapped to camera regions via polygon-based ROIs

This approach was used to validate the reasoning engine, temporal smoother, and alert logic independently of live camera input.

---

## 🗺️ Roadmap

- [x] Zone detection with polygon ROIs
- [x] PPE validation per zone
- [x] Worker tracking with persistent IDs
- [x] Temporal smoothing (reduce false positives)
- [x] Contextual reasoning engine
- [x] Green / Yellow / Red alert tagging
- [x] Streamlit dashboard
- [ ] Live camera feed integration
- [ ] YOLO-based PPE detection model
- [ ] Pose estimation for misplaced gear (e.g. goggles on forehead)
- [ ] Multi-camera ReID



MIT License
