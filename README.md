S.A.M.A.R.T.H. 🛡️

Spatial Analytics & Money Account Routing Tracker for Home-affairs

Predictive Intelligence Dashboard for Cyber Fraud Detection, Money-Mule Tracking & ATM Cash-Out Hotspot Prediction

S.A.M.A.R.T.H. is a frontend prototype designed to demonstrate how cyber-fraud complaints can be transformed into a spatial intelligence workflow.

The dashboard allows an operator to enter a fraud incident location, fraud amount, and elapsed time, then simulates:

📍 Incident geolocation

🗺️ Spatial ATM hotspot prediction

💰 Money-mule transaction routing

🔗 Multi-layer financial flow visualization

🚨 Risk/confidence scoring

🏦 Simulated bank account hold actions

👮 Simulated geo-tagged police dispatch

Note: This is a prototype/demo application. The fraud predictions, account information, risk percentages, transaction routing, and interception actions are simulated and do not represent real banking, law-enforcement, or NCRP data.

✨ Features

📞 1930 Fraud Complaint Simulation

Enter:

Victim / incident location

Fraud amount

Time elapsed since the incident

The application uses the location to generate a simulated fraud-response scenario.

🗺️ Interactive India Map

The dashboard uses Leaflet.js with OpenStreetMap tiles to display:

Incident origin

Predicted ATM hotspots

Risk zones

Approximate distance from the incident

Estimated cash-out windows

The map initially opens with an India-wide view and automatically moves to the searched location after simulation.

💸 Money Mule Routing Graph

The prototype demonstrates a simplified transaction flow:

Victim
   │
   ▼
Mule Layer 1
   │
   ├──── 55% ────► Layer 2A
   │
   └──── 45% ────► Layer 2B

The transaction split is dynamically calculated from the entered fraud amount.

🚨 ATM Risk Prediction

The prototype generates three simulated ATM hotspots with different risk levels.

Risk

Classification

≥ 80%

🔴 High Risk

50–80%

🟠 Moderate Risk

Each hotspot includes:

ATM/bank name

Distance from incident

Risk percentage

Estimated cash-out window

🏦 Simulated Bank Auto-Hold

After a simulation, the dashboard enables an Auto-Hold action.

The prototype displays a simulated REST webhook response representing a request to place a hold on the suspected mule account.

👮 Simulated Police Dispatch

The dashboard also provides a Beat Police Alert action that simulates sending a geo-tagged interception alert to the nearest police patrol.

🛠️ Technologies Used

Technology

Purpose

HTML5

Application structure

CSS3

Custom styling

JavaScript

Application logic

Tailwind CSS

UI styling

Leaflet.js

Interactive maps

OpenStreetMap

Map tiles

Nominatim

Location geocoding

Font Awesome

Icons

Google Fonts

Inter & JetBrains Mono

The application loads Tailwind CSS, Leaflet, Font Awesome, and Google Fonts through external CDNs.

📁 Project Structure

SMART-H/
│
├── samarth_v2.html
└── README.md

🚀 Getting Started

1. Clone the repository

git clone https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git

2. Enter the project directory

cd YOUR_REPOSITORY

3. Open the application

Simply open:

samarth_v2.html

in a modern web browser.

Alternatively, use VS Code's Live Server extension.

▶️ How to Use

Step 1 — Enter Incident Location

Example:

Connaught Place, New Delhi

You can also enter other Indian locations such as:

Sector 17 Chandigarh
Hazratganj Lucknow
Andheri Mumbai

Step 2 — Enter Fraud Amount

Example:

85000

Step 3 — Enter Time Elapsed

Example:

18

Step 4 — Run Simulation

Click:

Simulate 1930 Fraud & Predict Hotspots

The dashboard will:

Resolve the location.

Place an incident marker.

Generate simulated ATM hotspots.

Calculate transaction splits.

Display the money-mule routing graph.

Enable interception actions.

The location is resolved using the Nominatim geocoding API, with a New Delhi fallback if the search does not return a location.

🧠 Simulation Logic

The prototype dynamically calculates transaction splitting based on the entered fraud amount.

For example, for:

Fraud Amount = ₹85,000

The simulated routing becomes approximately:

₹85,000
   │
   ├── 55% → ₹46,750
   │
   └── 45% → ₹38,250

The application also generates three simulated ATM hotspots around the incident location with predefined risk values of 94%, 87%, and 62%.

🔐 Interception Workflow

Once the simulation completes:

1930 Complaint
      │
      ▼
Location Resolution
      │
      ▼
Incident Mapping
      │
      ▼
Mule Routing Analysis
      │
      ▼
ATM Hotspot Prediction
      │
      ├──────────────┐
      ▼              ▼
Bank Auto-Hold   Police Dispatch

Both interception actions are currently simulated frontend actions and do not communicate with real banking or police systems.

⚠️ Important Disclaimer

This project is a proof-of-concept / hackathon prototype.

It does not currently provide:

Real NCRP telemetry

Real bank API integration

Real police dispatch

Real-time transaction monitoring

Real money-mule identification

Real ATM cash-out prediction

Production-grade machine learning predictions

Access to confidential law-enforcement databases

All financial routing, risk scores, ATM locations, and interception responses are simulated.

🔮 Future Improvements

Potential production extensions include:

Real 1930/NCRP API integration

Machine-learning based fraud-risk prediction

Real-time transaction graph analysis

Neo4j backend integration

Bank API integration

Real ATM and banking-location datasets

Real-time geospatial analytics

Historical fraud hotspot analysis

Role-based authentication

Audit logging

Secure REST API backend

PostgreSQL/PostGIS geospatial database

Automated case-management workflow

Real-time alerting system

🎯 Project Objective

S.A.M.A.R.T.H. demonstrates how geospatial intelligence + financial graph analysis + automated response workflows can be combined into a single operational dashboard for cyber-fraud investigation.

The goal is to reduce the time between:

Complaint → Analysis → Prediction → Intervention

👨‍💻 Team

BugBusters

Built as a cybersecurity / hackathon prototype.

📜 License

This project is intended for educational, research, and demonstration purposes.

Add an appropriate open-source license before public redistribution.

⭐ If You Like This Project

Give the repository a ⭐ on GitHub and feel free to fork it for experimentation and development.
