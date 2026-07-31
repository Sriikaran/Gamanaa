# 🚦 Gamana

**The Intelligent, AI-Driven Traffic Orchestration System**

[![React](https://img.shields.io/badge/Frontend-React%20Vite-blue)](https://reactjs.org/)
[![Backend](https://img.shields.io/badge/Backend-Flask%20%7C%20Python-green)](https://flask.palletsprojects.com/)
[![YOLOv8](https://img.shields.io/badge/Computer%20Vision-YOLOv8-yellow)](https://github.com/ultralytics/ultralytics)
[![Featherless AI](https://img.shields.io/badge/AI%20Reasoning-Featherless%20%7C%20Kimi--K2--Instruct-purple)](https://featherless.ai)

Welcome to **Gamana**, a next-generation traffic management system built for the modern smart city. Traditional traffic lights are dumb—they run on static, hardcoded timers that cause immense congestion, wasted fuel, and phantom traffic jams. 

**Gamana** changes everything by combining real-time edge computer vision (YOLOv8) with high-level LLM reasoning (Featherless AI) to dynamically orchestrate traffic lights based on live vehicle density, lane pressure, and complex traffic states.

---

## 🚀 The Hackathon Edge: What Makes Gamana Special?

While most smart traffic systems stop at basic vehicle counting, Gamana introduces a **Dual-Brain Architecture**:
1. **The Fast Brain (YOLOv8 + Motion Tracking):** Processes video frames at 30+ FPS, mapping exact bounding boxes, counting vehicles, and tracking their persistent IDs across multiple lanes.
2. **The Slow Brain (Featherless AI Integration):** An asynchronous LLM-powered traffic strategist (`moonshotai/Kimi-K2-Instruct` via Featherless AI). It ingests JSON snapshots of the entire intersection state and reasons through complex edge cases (e.g., phantom braking, asymmetrical congestion) to override basic logic with human-like strategic foresight.

## ✨ Key Features

- **Real-Time YOLOv8 Vehicle Tracking**: High-precision edge inference that doesn't just detect cars, but tracks their trajectories and wait times.
- **Dynamic Lane Pressure Analysis**: Computes algorithmic "pressure" scores based on volume, stagnation time, and queue length.
- **Featherless AI Command Center**: A live React dashboard panel that exposes the AI's real-time reasoning. Watch the AI digest intersection metrics and dictate signal overrides live!
- **Real-Time Dashboard**: A blazing-fast React/Vite UI visualizing video feeds, lane geometries, dynamic charts, and AI telemetry (inference latency, snapshot age, model status) via WebSockets.
- **Anti-Phantom Jam Logic**: Algorithmic interventions to clear "ghost traffic" caused by cascading brake lights.

---

## 🏗️ Architecture Stack

### Backend Pipeline
- **Computer Vision**: PyTorch, Ultralytics YOLOv8, OpenCV
- **Core API & Real-time Sync**: Python 3.8+, Flask, Flask-SocketIO
- **AI Strategist**: Featherless AI API (`Kimi-K2-Instruct`) running on an isolated daemon thread to prevent blocking the video pipeline.

### Frontend Dashboard
- **Framework**: React, Vite, Tailwind CSS
- **Data Binding**: Real-time SocketIO streams powering dynamic React states.

---

## 🛠️ Detailed Setup & Execution Guide

Gamana requires both the **Backend AI Server** and the **Frontend Dashboard** to run simultaneously.

### Prerequisites
- **Python 3.8+** installed on your system.
- **Node.js** (v16+) installed for frontend compilation.
- **Featherless AI API Key**: Added to `backend/.env`.

---

### Step 1: Running the Backend

The backend handles heavy lifting: video parsing, YOLO inference, calculating signal logic, fetching LLM strategies, and WebSocket broadcasting.

1. **Open a terminal** and navigate to the backend:
   ```bash
   cd gamana/backend
   ```
2. **Configure Environment Variables**:
   Create a `.env` file in the `backend/` directory (or use `.env.example`):
   ```env
   FEATHERLESS_API_KEY=your_featherless_api_key_here
   FEATHERLESS_BASE_URL=https://api.featherless.ai/v1
   FEATHERLESS_MODEL=moonshotai/Kimi-K2-Instruct
   ```
3. **Install Dependencies** (Using the local virtual environment):
   ```bash
   ..\venv\Scripts\python.exe -m pip install -r requirements_local.txt
   ```
4. **Start the AI Server**:
   ```bash
   ..\venv\Scripts\python.exe main.py --source ../indian_traffic.mp4 --no-display
   ```
   *(The server will boot up on Port 5000 and begin processing the video.)*

---

### Step 2: Running the Frontend Dashboard

1. **Open a SECOND terminal** and navigate to the frontend:
   ```bash
   cd gamana/frontend
   ```
2. **Install Node Packages**:
   ```bash
   npm install
   ```
3. **Start the Development Server**:
   ```bash
   npm run dev
   ```

### Step 3: View the Magic!

Navigate to **[http://localhost:5173](http://localhost:5173)**. You will instantly see:
- The YOLO bounding boxes tracking traffic.
- The dynamic charts adjusting to lane pressures.
- The **Featherless AI panel** at the bottom analyzing the JSON intersection state and producing intelligent signal overrides in real time!

---

## 💡 What's Next?
- **Emergency Vehicle Preemption (EVP)**: Training the vision model to detect ambulances and fire trucks, allowing the AI to instantly force a green corridor.
- **Multi-Intersection Sync**: Scaling the Featherless AI prompt to ingest data from adjacent intersections to orchestrate "green waves" across entire city grids.

---
*Built with ❤️ for the Hackathon.*
