# 🛡️ S.A.M.A.R.T.H.

## Spatial Analytics & Money Account Routing Tracker for Home-affairs

> **Law Enforcement Operational Grid for Cyber-Fraud Intelligence, Geospatial Analysis & ATM/Cash-Out Corridor Detection**

S.A.M.A.R.T.H. is a web-based **cyber-fraud investigation and geospatial intelligence prototype** designed to demonstrate how a reported financial fraud incident can be analyzed using location intelligence, ATM infrastructure data, transaction-flow visualization, and risk scoring.

The system provides an operational-style dashboard where an authorized officer can enter a fraud incident, resolve its geographical location, query nearby **real OpenStreetMap (OSM) ATM/Bank points**, calculate distances, generate dynamic risk scores, and visualize potential cash-out corridors.

---

# 🚀 Key Capabilities

### 🔐 Officer Authentication

The dashboard is protected by an authentication layer that provides:

* Officer login
* Officer registration
* Password recovery
* Security passphrase verification
* Session logout
* Officer identity display
* Locked dashboard before authentication

Credentials are stored locally using the browser's `localStorage`.

> ⚠️ This authentication system is intended for demonstration purposes and is **not suitable for production law-enforcement systems**.

---

### 📍 Smart Location Resolution

Officers can enter locations such as:

```text
Hazratganj, Lucknow
Connaught Place, Delhi
Sector 17, Chandigarh
Andheri, Mumbai
```

The application uses **OpenStreetMap Nominatim** to resolve the location into latitude and longitude coordinates.

The geocoder attempts multiple query variations before falling back to the default Lucknow coordinates if no result is found.

---

### 🗺️ Live OpenStreetMap Infrastructure Query

Unlike a static hotspot demo, this version queries **actual OpenStreetMap POI data** around the incident location.

The system searches for:

```text
ATM
Bank
```

within the selected geographical area.

Returned nodes contain:

* Latitude
* Longitude
* Operator/name
* POI type

The dashboard then plots the returned infrastructure directly onto the Leaflet map.

---

### 📐 Haversine Distance Calculation

The system calculates the geographical distance between:

```text
Incident Location
        ↓
ATM / Bank Node
```

using the **Haversine formula**.

Distances are displayed in:

```text
Meters
Kilometers
```

Example:

```text
842 m
0.84 km
```

This allows the system to rank infrastructure based on proximity to the incident anchor point.

---

# 🧠 Dynamic Risk Engine

The prototype calculates a risk score dynamically using:

* Distance from incident location
* Time elapsed since the reported incident

The base risk decreases as the distance from the incident increases.

A simplified representation is:

```text
Risk ≈ Distance-based score − Time decay
```

Risk is constrained between:

```text
30% ─────────────── 98%
```

If the incident is older than approximately 25 minutes, an additional time-decay factor is applied.

---

# ⏱️ Cash-Out Corridor Estimation

The system also calculates an estimated time window using the distance between the incident and the infrastructure node.

The current prototype uses an estimated transit calculation based on geographical distance.

Example:

```text
ATM Distance: 1.2 km
Estimated Corridor: ~6 mins
```

> This is a mathematical prototype estimate, **not a real prediction of criminal behavior or ATM usage**.

---

# 💰 Money Mule Routing Visualization

The dashboard contains a visual representation of a simplified financial transaction chain:

```text
                    ┌── Layer 2A
                    │     55%
Victim ──► Mule ────┤
                    │
                    └── Layer 2B
                          45%
```

The fraud amount is dynamically divided into:

```text
55%
45%
```

For example:

```text
Fraud Amount = ₹85,000

Layer 1
   ↓
₹85,000

   ├── 55% → ₹46,750
   │
   └── 45% → ₹38,250
```

This provides a visual demonstration of how transaction layering could be represented in an investigative interface.

---

# 🚨 Risk Visualization

The map uses different markers for different investigation states.

| Marker    | Meaning               |
| --------- | --------------------- |
| 🔵 Indigo | Incident Anchor Point |
| 🔴 Red    | Critical Risk         |
| 🟠 Amber  | Secondary Candidate   |

Critical candidates are currently defined as:

```text
Risk > 80%
```

Secondary candidates fall within:

```text
50% – 80%
```

---

# 📊 Investigation Dashboard

The interface is divided into three operational sections.

## Left Panel

Contains:

* 1930 complaint ingestion
* Incident location
* Fraud amount
* Incident time
* Destination mule account
* OSM query control
* Money-mule routing visualization

## Center Panel

Contains:

* Interactive Leaflet map
* Incident anchor
* ATM/Bank POI nodes
* Risk circles
* Geographic visualization

## Right Panel

Contains:

* Live OSM infrastructure results
* Risk percentage
* Coordinates
* Distance
* Estimated corridor
* Interception actions

---

# 🛰️ Interception Actions

The dashboard provides two simulated response controls:

### 🏦 Bank Auto-Hold

```text
Trigger Bank Auto-Hold
        ↓
REST Webhook
        ↓
Core Banking API
```

### 👮 Police Dispatch

```text
Dispatch Beat Police Alert
        ↓
Geo-Push
        ↓
Nearest Police Patrol
```

These actions currently provide **frontend simulation messages only**.

They do not actually contact:

* Banks
* Police departments
* NCRP
* I4C
* Core banking systems
* Government APIs

---

# 🛠️ Technology Stack

| Technology           | Usage                    |
| -------------------- | ------------------------ |
| HTML5                | Application structure    |
| CSS3                 | Custom interface styling |
| JavaScript           | Application logic        |
| Tailwind CSS         | UI framework             |
| Leaflet.js           | Interactive mapping      |
| OpenStreetMap        | Map & POI data           |
| Nominatim            | Geocoding & POI search   |
| Font Awesome         | Icons                    |
| Google Fonts         | Typography               |
| Browser LocalStorage | Demo credential storage  |

---

# 🔄 System Workflow

```text
┌──────────────────────┐
│   Officer Login      │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│  Submit Fraud Case   │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│ Location Geocoding   │
│    via Nominatim     │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│ Query OSM ATM/Bank   │
│       Nodes          │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│ Calculate Haversine  │
│      Distance        │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│ Dynamic Risk Scoring │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│ Rank & Visualize     │
│ Infrastructure Nodes │
└──────────┬───────────┘
           ↓
     ┌─────┴─────┐
     ↓           ↓
┌─────────┐ ┌─────────────┐
│ Bank    │ │ Police      │
│ Hold    │ │ Dispatch    │
└─────────┘ └─────────────┘
```

---

# 📁 Project Structure

```text
S.A.M.A.R.T.H/
│
├── samarth.html
│
└── README.md
```

---

# ▶️ Installation & Usage

## 1. Clone the Repository

```bash
git clone https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
```

## 2. Open the Project

```bash
cd YOUR-REPOSITORY
```

Open the HTML file directly in a browser.

For the best development experience, use **VS Code + Live Server**.

---

# 🔑 Demo Authentication

The current prototype contains a default fallback credential:

```text
Officer ID:
CYBER-OFFICER

Password:
admin

Security Passphrase:
police
```

### ⚠️ Security Warning

These credentials exist **inside the client-side JavaScript**.

Never use this authentication mechanism for a real production system.

A production implementation should use:

```text
Frontend
    ↓
Secure HTTPS API
    ↓
Authentication Service
    ↓
Hashed Password Database
    ↓
JWT / Secure Session
    ↓
Role-Based Access Control
```

---

# 🌐 External Services

The application currently communicates with public OpenStreetMap services for geospatial information.

### Nominatim

Used for:

* Location geocoding
* ATM searches
* Bank searches

### OpenStreetMap

Used for:

* Map tiles
* Geographic points of interest

Because these are public services, availability, rate limits, and data completeness may vary.

---

# 🧪 Example Investigation

Input:

```text
Location:
Hazratganj, Lucknow

Fraud Amount:
₹85,000

Incident Time:
18 minutes ago
```

The system then:

```text
1. Resolves Hazratganj coordinates
             ↓
2. Queries nearby OSM ATM/Bank nodes
             ↓
3. Calculates distance to each node
             ↓
4. Calculates dynamic risk scores
             ↓
5. Sorts nodes by risk
             ↓
6. Displays them on the map
             ↓
7. Displays transaction-routing visualization
             ↓
8. Enables response-action controls
```

---

# 🔮 Future Development

The current prototype can be extended into a complete full-stack platform.

### 🤖 AI / ML

* Fraud probability prediction
* Transaction anomaly detection
* Money-mule classification
* Temporal fraud pattern detection
* Graph-based fraud detection
* Cash-out probability modelling
* Historical hotspot prediction

### 🕸️ Graph Intelligence

Integration with:

* Neo4j
* Graph Data Science
* Transaction relationship graphs
* Multi-hop account tracing
* Entity resolution

### 🏦 Financial Intelligence

Potential future integrations:

* Secure banking APIs
* Transaction monitoring
* Account risk scoring
* Automated hold workflows
* Suspicious transaction alerts

### 🗺️ Geospatial Intelligence

Potential additions:

* Real ATM datasets
* Road-network routing
* Travel-time estimation
* Historical crime hotspots
* Heatmaps
* Geofencing
* Spatial clustering

### 🔐 Enterprise Security

Production implementation should include:

* Backend authentication
* Password hashing
* MFA
* RBAC
* JWT/session management
* Encryption
* Audit logs
* API authorization
* Rate limiting
* Secure secrets management

---

# ⚠️ Disclaimer

S.A.M.A.R.T.H. is a **proof-of-concept cybersecurity and geospatial intelligence project**.

The application does not provide access to confidential government, banking, police, NCRP, or I4C systems.

Although the application queries **real OpenStreetMap geographic/POI data**, the following components are simulated:

* Financial transaction routing
* Mule-account information
* Risk scoring methodology
* Cash-out corridor estimation
* Bank auto-hold
* Police dispatch
* Law-enforcement integration

The project should **not be used to make real-world enforcement decisions** without validated datasets, appropriate authorization, rigorous testing, and qualified human oversight.

---

# 🎯 Project Goal

The core objective of S.A.M.A.R.T.H. is to demonstrate a unified workflow for:

```text
CYBER FRAUD
     ↓
GEOSPATIAL INTELLIGENCE
     ↓
INFRASTRUCTURE ANALYSIS
     ↓
RISK PRIORITIZATION
     ↓
INVESTIGATIVE RESPONSE
```

The long-term vision is to reduce the time between **fraud reporting, intelligence generation, and coordinated response**.

---

# 👨‍💻 Developed By

## BugBusters

Cybersecurity / Smart India Hackathon Prototype

---

# ⭐ Support

If you find the project useful, consider giving the repository a ⭐ on GitHub.

Contributions, improvements, and research-oriented extensions are welcome.
