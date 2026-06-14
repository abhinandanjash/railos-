# 🚂 RailOS - Autonomous Railway Intelligence Operating System

**RailOS** is a next-generation, AI-powered operating system built to manage, monitor, and optimize railway networks in real-time. Designed for enterprise deployment and government railway authorities, it seamlessly integrates Multi-Agent AI, IoT Hardware, and Digital Twins to ensure proactive safety, predictive maintenance, and optimized logistics.

> **Built for the International Hackathon Finals** 🏆

---

## 🌟 Key Features

* **Multi-Agent AI Orchestration:** Autonomous agents (Safety, Logistics, Scheduling, and Emergency) built with CrewAI and LangGraph collaborate in real-time to solve complex routing and safety scenarios.
* **IoT Sensor Gateway:** Direct integration with ESP32 hardware (Vibration, Tilt, Ultrasonic Obstacles, Temperature, and ESP32-CAM Vision) to stream live telemetry.
* **Digital Twin & 3D Visualization:** Real-time 3D WebGL rendering of trains and tracks for unparalleled situational awareness.
* **Predictive Maintenance:** Machine Learning (YOLOv8 & threshold-based anomaly detection) predicts track fractures and derailment risks before they happen.
* **Real-Time WebSocket Telemetry:** Redis Pub/Sub powered live streaming ensures the dashboard reflects physical reality with sub-second latency.
* **Software Simulation Engine:** Fully functional without hardware. The built-in simulator generates synthetic kinematics and telemetry for seamless development.

---

## 🏗️ Technology Stack

**Frontend:**
* Next.js 15, React 19, TypeScript
* Tailwind CSS
* Three.js (3D WebGL Digital Twin)

**Backend & AI:**
* FastAPI (Python 3.10+)
* CrewAI & LangGraph (Multi-Agent Systems)
* Ultralytics YOLOv8 (Computer Vision)

**Databases & Infrastructure:**
* PostgreSQL + SQLModel (Relational Data)
* Redis (Pub/Sub & WebSocket State)
* Neo4j (Knowledge Graph for Logistics)
* Docker & Docker Compose (Containerization)
* Nginx (Reverse Proxy)

**Hardware Firmware:**
* C++ / Arduino (ESP32 DevKit, ESP32-CAM)
* Sensors: SW420, MPU6050, HC-SR04, DS18B20

---

## 🚀 Getting Started

### Prerequisites
* Node.js 18+
* Python 3.10+
* Docker & Docker Compose (Optional but recommended)

### 1. Start the Backend

```bash
cd backend
python -m venv venv
source venv/bin/activate  # On Windows use: .\venv\Scripts\activate
pip install -r requirements.txt

# Run the backend server (Binds to 0.0.0.0 for IoT hardware access)
python -m uvicorn app.main:app --host 0.0.0.0 --port 8000
```
*Note: The backend automatically falls back to SQLite and MockRedis if Docker containers are not running.*

### 2. Start the Frontend

```bash
cd frontend
npm install
npm run dev
```

The RailOS Command Center will be available at [http://localhost:3000](http://localhost:3000).

---

## 🔌 Hardware Integration (ESP32)

RailOS is fully ready for physical IoT hardware. The `firmware/` directory contains complete C++ sketches for various sensors:

1. Connect your ESP32 to the local Wi-Fi.
2. Update the `SERVER_IP` in your `.ino` sketch to match your local backend IP.
3. Flash the firmware. The ESP32 will auto-register with RailOS and begin streaming live data to the Digital Twin dashboard.

Check out the [Firmware Guide](firmware/README.md) for detailed wiring diagrams and setup instructions.

---

## 🧠 AI Agent Architecture

RailOS operates using a hierarchical Multi-Agent System:

* **Orchestrator Agent:** Delegates incoming telemetry and incidents to specialized sub-agents.
* **Safety Agent:** Monitors structural integrity, thermal stress, and track clearance.
* **Emergency Agent:** Triggers lockdown protocols and reroutes trains during critical hazards.
* **Logistics Agent:** Optimizes cargo loading, unloading, and transit times across the knowledge graph.
* **Scheduling Agent:** Resolves track conflicts and delays to maintain the timetable.

---

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.
