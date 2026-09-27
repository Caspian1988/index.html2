# 🚌 Live Route 6 GPS Probability Tracker & Simulator

> A real-time GPS telemetry and stochastic delay forecasting dashboard for transit bus operators (Ride On Route 6 – Run 758).

[![Live Demo](https://img.shields.io/badge/Demo-Live%20Tracker-brightgreen?style=for-the-badge&logo=github)](https://caspian1988.github.io/index.html2/)

---

## 📍 Overview

During a full transit shift, small delays from traffic, signal timing, and passenger boarding accumulate across trips. For drivers on **Route 6 (Run 758)**, this cumulative delay determines how and where their shift concludes—specifically predicting the likelihood of reaching the **8:47 PM Parkside Cul-de-Sac finish** versus terminating early at **Westfield Montgomery Mall**.

This application turns any mobile device or cab-mounted phone into a live telematics unit that calculates real-time delay accumulation and projects the probability of the scheduled terminal finish.

---

## 🚀 Live Demo
Test the live application on your browser or mobile device:  
🔗 **[Live Route 6 Tracker](https://caspian1988.github.io/index.html2/)**

---

## ✨ Key Features

- **🛰️ Live GPS Telemetry**: Monitors latitude, longitude, and ground speed in real-time using the HTML5 Geolocation API.
- **📍 Geofenced Stop Recognition**: Uses the **Haversine formula** to measure proximity to key waypoints (*Westfield Montgomery Mall*, *Parkside Cul-de-Sac*, *Grosvenor Metro*).
- **⏱️ Automated Run 758 Timetable Matching**: Compares current time against all 19 scheduled departure times to auto-detect the active trip number and direction (Eastbound vs. Westbound).
- **📈 Stochastic Delay Projection**: Analyzes existing delay plus expected compounding delay per remaining leg to calculate the percentage probability of hitting the 15-minute terminal threshold.
- **📱 Screen Wake Lock API**: Prevents the driver's device screen from dimming or sleeping while mounted in the bus console.
- **🌙 Operator-Friendly Dark UI**: High-contrast, night-mode interface optimized for rapid glances and low-light transit cab environments.

---

## 🧮 How the Probability Model Works

1. **Current Delay Calculation**:
   $$\text{Current Delay} = \max(0, \text{Current Time} - \text{Scheduled Departure})$$

2. **Projected Accumulation**:
   Transit delays are stochastic and compound over successive trips. The simulator models remaining trips with an expected delay factor:
   $$\text{Projected Delay} = \text{Current Delay} + (\text{Remaining Trips} \times 3\text{ mins})$$

3. **Terminal Decision Threshold**:
   - **$\ge 15$ min delay buffer**: High probability of triggering the alternate 8:47 PM Parkside finish condition.
   - **$< 15$ min delay buffer**: Projected on-time or near-schedule finish at Montgomery Mall.

---

## 🛠️ Built With

- **HTML5 & CSS3** (Mobile-first responsive design, CSS Grid & Flexbox)
- **Vanilla JavaScript** (Zero external dependencies)
- **Browser APIs**:
  - `navigator.geolocation` (High-accuracy continuous position tracking)
  - `navigator.wakeLock` (Keep-awake screen persistence)
- **Hosted on**: GitHub Pages

---

## 💻 Running Locally

1. Clone this repository:
   ```bash
   git clone https://github.com/caspian1988/index.html2.git
