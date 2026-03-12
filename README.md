# Context-Aware PPE Compliance System

A real-time workplace safety monitoring system that validates Personal Protective Equipment 
compliance based on zone risk level — not just generic detection. Workers are tracked, 
zones are classified, and compliance is enforced dynamically per area.

---

## The Problem

Most PPE detection systems flag violations without considering where a worker actually is. 
A hardhat requirement in a factory floor is not the same as in an office corridor. 
Generic detection leads to false alarms and ignored alerts.

---

## The Solution

This system combines zone classification with PPE validation to give context-aware compliance:

- Workers are tracked with persistent identities across frames
- Zones are classified as Safe, Moderate, or High-Risk
- PPE requirements are enforced dynamically based on zone
- Temporal smoothing reduces false positives over time
- Alerts are explainable — describing what is missing and why

---

## Architecture
```
Worker Detection (YOLOv8)
     ↓
Zone Classification (Safe / Moderate / High-Risk)
     ↓
PPE Validation per Worker per Zone
     ↓
Temporal Smoothing Engine
     ↓
Contextual Reasoning Engine
     ↓
Alert System (Green / Yellow / Red)
     ↓
Streamlit Dashboard
```

---

## Zone-Based PPE Requirements

| Zone | Risk Level | Required PPE |
|------|------------|--------------|
| Office | Safe | Basic work apparel |
| Storage | Moderate | Long trousers, work shoes |
| Factory Floor | High-Risk | Long trousers, work shoes, goggles |

---

## Tech Stack

| Layer | Technology |
|-------|------------|
| Detection | YOLOv8, OpenCV |
| Core Logic | Python, NumPy, SciPy |
| Dashboard | Streamlit |

---

## Getting Started

### 1. Clone and Install
```bash
git clone https://github.com/justinthomas11/context-aware-ppe-compliance.git
cd context-aware-ppe-compliance
pip install -r requirements.txt
```

### 2. Run
```bash
streamlit run ui/dashboard.py
```

---

## Project Structure
```
├── app.py
├── config/
│   └── zones.json
├── core/
│   ├── zone_manager.py       # Zone classification logic
│   ├── ppe_validator.py      # Per-zone PPE validation
│   ├── tracker.py            # Worker identity tracking
│   ├── temporal.py           # Smoothing engine
│   ├── reasoning.py          # Contextual alert reasoning
│   └── alerts.py             # Green / Yellow / Red tagging
├── utils/
│   └── geometry.py
└── ui/
    └── dashboard.py
```

---

## Note on Simulation

Worker positions, PPE states, and zone assignments are currently simulated using 
hardcoded values to validate the reasoning engine and alert logic independently 
of live camera input.

---

## Roadmap

- [x] Zone detection with polygon ROIs
- [x] PPE validation per zone
- [x] Worker tracking with persistent IDs
- [x] Temporal smoothing
- [x] Contextual reasoning engine
- [x] Alert tagging
- [x] Streamlit dashboard
- [ ] Live camera feed integration
- [ ] YOLO-based PPE detection model
- [ ] Pose estimation for misplaced gear
- [ ] Multi-camera ReID
