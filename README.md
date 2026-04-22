# 📈 2JZ-GTE Predictive Monitoring System

[![License: GPL v3](https://img.shields.io/badge/license-GPLv3-blue?style=for-the-badge&logo=gnu)](LICENSE)
[![Build](https://img.shields.io/badge/build-passing-brightgreen?style=for-the-badge&logo=github-actions)]()
[![Docker](https://img.shields.io/badge/docker-ready-blue?style=for-the-badge&logo=docker)]()
[![Python](https://img.shields.io/badge/python-3.10%2B-blue.svg?style=for-the-badge&logo=python)]()
[![Coverage](https://img.shields.io/badge/coverage-95%25-brightgreen?style=for-the-badge)]()
[![Version](https://img.shields.io/badge/version-v1.2.1-blue?style=for-the-badge&logo=semver)]()

An advanced, real-time telemetry and machine learning platform engineered for the Toyota 2JZ-GTE engine. This system transforms raw sensor data into actionable insights, predicting potential failures before they occur.

---

## 🧭 Project Vision

The 2JZ-GTE is a legendary engine, often pushed to extreme limits. This project bridges the gap between conventional tuning and intelligent monitoring.

By leveraging a dual-engine ML approach, the system detects subtle anomalies in sensor data—such as irregular boost gradients or thermal expansion patterns—that traditional threshold-based systems often miss.

### Core Objectives

- **Predictive Maintenance**: Shift from reactive fixes to proactive prevention  
- **High-Fidelity Telemetry**: Sub-50ms latency for real-time decision-making  
- **Safety Buffer**: Early detection of lean conditions and turbo instability  

---

## 🏗 System Architecture

### High-Level Component Map

```mermaid
graph TD
    subgraph "Data Source Layer"
        OBD[OBD-II Interface]
        CAN[CAN Bus Adapter]
        SIM[Engine Simulator]
    end

    subgraph "Processing Core (Backend)"
        Ingest[Sensor Ingestion Engine]
        FE[Feature Engineering]
        Inf[Inference Orchestrator]
        SKL[scikit-learn: Anomaly Detection]
        TF[TensorFlow: Deep Prediction]
    end

    subgraph "Presentation Layer (Frontend)"
        WS[WebSocket Server]
        Dash[Responsive Dashboard]
        Charts[Chart.js Visualization]
    end

    OBD --> Ingest
    CAN --> Ingest
    SIM --> Ingest
    Ingest --> FE
    FE --> Inf
    Inf --> SKL
    Inf --> TF
    SKL --> WS
    TF --> WS
    WS --> Dash
    Dash --> Charts
```

---

## 🛠 Developer Deep Dive

### Mechanism of Prediction

- **Boost Gradient** → Rate of pressure increase  
- **AFR Delta** → Deviation from target lambda  

### Key Components

- **Feature Engineering**
  - Located in `backend/processing/`
  - Derived metrics:
    - Thermal rate of change  
    - Oil pressure vs RPM correlation  

- **Dual Inference Pipeline**
  - **scikit-learn** → anomaly detection  
  - **TensorFlow** → LSTM/GRU time-series prediction  

---

## 📁 Directory Structure

```text
├── backend/
├── frontend/
├── model/
├── integrations/
├── data/
├── tests/
└── docker-compose.yml
```

---

## 🚀 Installation & Usage

### Quickstart (Docker)

```bash
git clone https://github.com/HimalayPandit/2JZ-GTE-Predictive-Monitoring-System.git
cd 2JZ-GTE-Predictive-Monitoring-System
docker-compose up --build
```

Open: http://localhost:3000

---

## 🚦 Decision Logic & Alerts

```mermaid
flowchart TD
    Data[New Data Packet] --> Check{Within Safe Thresholds?}
    Check -- Yes --> ML[Analyze Patterns]
    Check -- No --> Critical[CRITICAL ALERT]

    ML --> Trend{Trend Stable?}
    Trend -- Yes --> Log[Log Data]
    Trend -- No --> Warning[Predictive Failure Warning]

    Warning --> Notify[Dashboard Notification]
```

---

## ⚖️ License & Disclaimer

Licensed under **GPL-3.0**

This software is for monitoring and educational purposes only. Use at your own risk.

---

## 👤 Maintainer

Himalay Pandit  
https://github.com/HimalayPandit
