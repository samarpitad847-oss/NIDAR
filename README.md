# NIDAR 🛣️

**NIDAR** is a road safety dashboard concept for India that detects animals on highways at night and warns drivers before a collision happens.

🌐 **[Open Dashboard](https://nidar-xi.vercel.app)**

> 💡 Add a screenshot of the dashboard here — upload to this repo and replace this line with: `![NIDAR Dashboard](screenshot.png)`

---

## The Problem

A large share of Indian highway fatalities involve animal collisions at night. Most happen on the same few high-density stretches — cows and dogs on carriageways are invisible in headlights until it is too late. There is no existing early-warning infrastructure for this.

NIDAR is designed to address exactly those high-risk KM markers, starting with corridors like NH-48.

---

## What This Repo Contains

A frontend prototype dashboard demonstrating the authority-facing interface:

- Live animal detection map with alert markers
- Road Safety Index — risk scoring by highway stretch
- Node health monitoring — status indicators per sensor location
- Historical heatmaps showing high-density detection zones

**Built with:** HTML, CSS, JavaScript
**Deployed on:** Vercel

---

## The Broader System Vision

The full system is designed as a three-layer IoT pipeline:

1. **Hardware** — Solar-powered ESP32 sensor nodes (PIR + ultrasonic) at high-risk KM markers, with on-device dual-validation to filter false alarms, transmitting via LoRa
2. **Cloud** — Node.js + MQTT backend receiving sensor events, running geofencing, and firing FCM push alerts to drivers within 2 km in under 4 seconds
3. **Dashboard** — This React frontend for highway authorities showing live detections and node health

This repo is the dashboard prototype. Hardware and backend are in active development.

---

## Hackathon Recognition

Built and presented at multiple national-level hackathons focused on road safety and IoT infrastructure.

---

*Built by [Samarpita Das](https://github.com/samarpitad847-oss)*
