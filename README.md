# 📈 2JZ-GTE Predictive Monitoring System

[![License: GPL v3](https://img.shields.io/badge/license-GPLv3-blue?style=for-the-badge&logo=gnu)](LICENSE)
[![Build](https://img.shields.io/badge/build-passing-brightgreen?style=for-the-badge&logo=github-actions)]()
[![Docker](https://img.shields.io/badge/docker-ready-blue?style=for-the-badge&logo=docker)]()
[![Python](https://img.shields.io/badge/python-3.10%2B-blue.svg?style=for-the-badge&logo=python)]()
[![Coverage](https://img.shields.io/badge/coverage-95%25-brightgreen?style=for-the-badge)]()
[![Version](https://img.shields.io/badge/version-v1.2.1-blue?style=for-the-badge&logo=semver)]()

**Real-time machine learning–driven predictive monitoring system for the Toyota 2JZ-GTE engine.**

---

## 🧭 Overview

A production-oriented telemetry and prediction platform that ingests engine data and performs low-latency inference using hybrid ML models.

**Core capabilities:**
- Real-time ingestion (OBD-II / CAN / simulation)
- Dual-model inference (`scikit-learn`, `TensorFlow`)
- WebSocket streaming (~23.6 Hz, ~41 ms latency)
- Derived metrics (AFR Δ, boost gradient, thermal rates)
- Fault prediction with confidence scoring

---

## 🏗 Architecture

```mermaid
flowchart LR
    A[Frontend Dashboard<br/>Chart.js + Socket.IO] --> B[WebSocket Server<br/>~23.6 Hz]
    B --> C[SKLearn Model]
    B --> D[TensorFlow Model]
    C --> E[Prediction Engine]
    D --> E
    E --> F[Flask API]
    F --> G[Sensor Ingestion]
    G --> H[OBD-II / CAN / Simulator]
