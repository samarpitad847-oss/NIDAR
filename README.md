# NIDAR 

**NIDAR** is a three-layer road safety system for India that detects animals on highways at night and warns drivers before a collision happens.

**The core problem:** Roadside sensor nodes detect cattle or dogs on the carriageway, publish an MQTT alert to the cloud in under a second, and push a notification to every driver within 2 km — all in under 4 seconds, before they can see the animal in their headlights.

🌐 **[Open Dashboard](https://nidar-xi.vercel.app)**

## The Problem

A large share of Indian highway fatalities involve animal collisions at night. Most happen on the same few high-density stretches — cows and dogs on carriageways are invisible in headlights until it is too late. There is no existing early-warning infrastructure for this.

NIDAR is designed to monitor exactly those high-risk KM markers, starting with corridors like NH-48.

---

## System Architecture — Three Layers

### Layer 1: Hardware (Edge)
- **Device:** ESP32 microcontroller with PIR + ultrasonic sensors
- **Power:** Solar-powered, designed for roadside deployment at high-risk KM markers
- **Logic:** Dual-validation algorithm runs entirely on-device — filters false alarms (wind, small debris) before transmitting, so the cloud only receives confirmed animal detections
- **Connectivity:** LoRa transmission for rural highway coverage where cellular is unreliable
- **Why this matters:** The device makes decisions without internet dependency — reliable even at zero-connectivity stretches of national highways

### Layer 2: Cloud (Backend)
- **Stack:** Node.js server with MQTT broker
- **Flow:** Sensor node publishes event → MQTT broker receives → geofencing logic identifies all drivers within 2 km → FCM push notification fires to their devices
- **Database:** PostgreSQL storing detection events, node health status, and historical data
- **API:** REST API serving the dashboard and mobile clients
- **Latency target:** Full pipeline (detection to driver notification) under 4 seconds

### Layer 3: Dashboard (Frontend)
- **Stack:** React
- **Users:** Highway authorities and road safety teams
- **Features:**
  - Live animal detection map with real-time alerts
  - Road Safety Index — aggregated risk scoring by highway stretch
  - Node health monitoring — battery, connectivity, last-ping status
  - Historical heatmaps showing high-density detection zones over time

---

## Tech Stack

| Layer | Tech |
|---|---|
| Firmware | C++ (Arduino/ESP32) |
| Communication | LoRa, MQTT |
| Backend | Node.js, PostgreSQL |
| Push Alerts | FCM (Firebase Cloud Messaging) |
| Frontend | React |
| Deployment | Vercel (dashboard) |

---

## Deployment Context

Designed for high-risk KM markers on Indian national highways (e.g. NH-48). Sensor nodes are solar-powered and self-contained — no external power infrastructure needed for roadside deployment.

---

## Hackathon Recognition

Built and presented at multiple national-level hackathons focused on road safety and IoT infrastructure and got shortlisted in two hackathons and emerged as finalists.
