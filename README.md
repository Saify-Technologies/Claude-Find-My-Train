# 🚂 Find My Train (IRCTC) — MCP Connector by Saifs AI

> Connect Claude AI to Indian Railways. Ask questions about trains, routes, live status, and more — in plain English.

---

## 📖 Table of Contents

- [What is this?](#what-is-this)
- [Features](#features)
- [How to Connect](#how-to-connect)
- [Available Tools](#available-tools)
- [Use Cases & Example Prompts](#use-cases--example-prompts)
- [Station Codes Reference](#station-codes-reference)
- [Limitations](#limitations)
- [Troubleshooting](#troubleshooting)
- [About Saifs AI](#about-saifs-ai)

---

## What is this?

The **Find My Train (IRCTC) MCP Connector** by Saifs AI lets you query Indian Railways data directly inside Claude. Instead of opening the IRCTC website or a separate app, you can simply ask Claude in plain language — and get instant, structured answers about trains, routes, and live running status.

This connector is built on the [Model Context Protocol (MCP)](https://www.anthropic.com/news/model-context-protocol), which allows Claude to securely call external data tools during a conversation.

---

## Features

- 🔴 **Live train running status** — Know exactly where a train is right now
- 🗺️ **Full route & stoppage details** — Every station a train passes through
- 🔍 **Train info by number** — Name, running days, origin, destination, timings
- 🛤️ **Trains between stations** — Find all trains connecting two cities
- 🎫 **PNR status check** — Confirm your booking status instantly

---

## How to Connect

1. Go to [claude.ai](https://claude.ai)
2. Open **Settings → Connectors** (or the Integrations panel)
3. Search for **"Find My Train IRCTC"** by Saifs AI
4. Click **Connect**
5. A login screen will appear — sign in using your **Google account** (or other available social login)
6. Once authenticated, you'll be redirected back to Claude automatically
7. Start a new chat and ask anything about Indian trains!

> **Why do I need to log in?**
> The social login links your identity to the connector so we can manage access, prevent misuse, and ensure reliable data for every user. We do not store any personal travel data.

### Login Troubleshooting

- **Popup blocked?** Allow popups for `claude.ai` in your browser settings and try again.
- **Login loop / not redirecting back?** Try disconnecting and reconnecting the connector, or use a different browser.
- **"Access denied" after login?** Make sure you're signing in with the correct Google account. If the issue persists, contact Saifs AI support.

---

## Available Tools

The connector exposes five tools that Claude uses automatically based on your question:

| Tool | What it does | Input Required |
|------|-------------|----------------|
| `railway_train_liveStatus` | Real-time running position of a train | 5-digit train number |
| `railway_train_route` | Complete route with all stoppages | 5-digit train number |
| `railway_train_getByNumber` | Core details of a train (name, days, timings) | 5-digit train number |
| `railway_train_betweenStations` | All trains running between two stations | Source & destination station codes |
| `railway_train_pnrStatus` | Ticket booking confirmation status | 10-digit PNR number |

> Claude automatically picks the right tool — you don't need to name any tool yourself.

---

## Use Cases & Example Prompts

### 🔴 Use Case 1: Live Train Running Status

For passengers waiting at a station, family members tracking arrivals, or anyone needing real-time location of a train.

**Example prompts:**
```
Where is train 12951 right now?
Is the Rajdhani Express 12002 running on time today?
What's the current status of train 19028?
How delayed is train 12909?
```

**What Claude returns:**
- Current location (last station crossed)
- Delay in minutes (if any)
- Expected arrival at destination
- Train name and journey details

---

### 🗺️ Use Case 2: Full Train Schedule & Route

For passengers planning to board at an intermediate station, or anyone wanting to know all stops of a train.

**Example prompts:**
```
Show me all stops for train 12951
What stations does the 19489 pass through?
Give me the complete schedule of train 12002 with arrival and departure times
Does train 12909 stop at Ratlam?
```

**What Claude returns:**
- Every station on the route with station codes
- Scheduled arrival and departure times at each stop
- Distance from origin
- Day of arrival at each stop

---

### 🛤️ Use Case 3: Find Trains Between Two Stations

For travelers planning a trip who want to compare all available train options between two cities.

**Example prompts:**
```
What trains run between New Delhi and Mumbai?
Show me all trains from Ratlam (RTM) to Indore (INDB)
Which trains go from Jaipur to Ahmedabad?
Are there any express trains between NDLS and BCT?
```

**What Claude returns:**
- List of all trains on that route
- Train numbers and names
- Departure and arrival times
- Days of operation

---

### 🔍 Use Case 4: Train Details by Number

For anyone who knows a train number and wants full information about it.

**Example prompts:**
```
Tell me about train 12951
What days does the 19489 run?
Where does train 12002 start and end?
Give me full details of the Shatabdi Express 12001
```

**What Claude returns:**
- Train name and number
- Origin and destination stations
- Departure and arrival times
- Days on which it runs

---

### 🎫 Use Case 5: PNR Status Check

For passengers who've booked a ticket and want to check if their seat is confirmed, waitlisted, or RAC.

**Example prompts:**
```
Check my PNR status: 2832453235
Is my ticket confirmed? PNR 4521367890
What's the booking status for PNR 8823401567?
```

**What Claude returns:**
- Passenger name(s)
- Current booking status (Confirmed / RAC / Waitlist)
- Coach and seat/berth number (if confirmed)
- Train name, date, and journey details

---

## Station Codes Reference

Common Indian railway station codes you can use in your prompts:

| City | Station Name | Code |
|------|-------------|------|
| New Delhi | New Delhi Railway Station | NDLS |
| Mumbai | Mumbai Central | BCT |
| Mumbai | Chhatrapati Shivaji Terminus | CSTM |
| Bangalore | Krantivira Sangolli Rayanna | SBC |
| Chennai | Chennai Central | MAS |
| Kolkata | Howrah Junction | HWH |
| Hyderabad | Hyderabad Deccan | HYB |
| Ahmedabad | Ahmedabad Junction | ADI |
| Jaipur | Jaipur Junction | JP |
| Pune | Pune Junction | PUNE |
| Ratlam | Ratlam Junction | RTM |
| Indore | Indore Junction | INDB |
| Bhopal | Bhopal Junction | BPL |
| Nagpur | Nagpur Junction | NGP |
| Lucknow | Lucknow Charbagh | LKO |
| Patna | Patna Junction | PNBE |
| Surat | Surat | ST |
| Vadodara | Vadodara Junction | BRC |

> **Tip:** You can also just say city names in your prompt ("trains from Delhi to Mumbai") and Claude will interpret them.

---

## Limitations

- **No booking or payment:** This connector is read-only. It cannot book tickets, cancel reservations, or process any transactions.
- **India only:** Only Indian Railways (IRCTC) data is supported. International routes are not available.
- **Train number required for live status:** For live running status and route details, a valid 5-digit train number is needed.
- **Station codes for between-station search:** For best results when finding trains between stations, use standard station codes (e.g., NDLS, BCT).
- **Data source:** All data is sourced from Indian Railways / IRCTC and is subject to their availability and accuracy.

---

## Troubleshooting

**Claude says it can't find train information**
- Double-check the train number is exactly 5 digits
- Confirm the station codes are correct (refer to the table above)
- Try rephrasing — e.g., "train number 12951" instead of just "12951"

**PNR status not found**
- Ensure the PNR is exactly 10 digits
- PNR status may not be available for very old or cancelled journeys

**Connector not responding**
- Disconnect and reconnect the connector from Claude Settings
- Check if the connector is enabled for your current chat session

**Train between stations returns no results**
- Verify both station codes are valid
- Some routes may have limited or no direct trains; try nearby major junctions

**Still stuck?**
Open an issue or reach out via the Saifs AI support channel.

---

## About Saifs AI

This connector is built and maintained by **Saifs AI**, focused on building practical MCP connectors that make everyday information accessible through Claude.

---

*Data provided by Indian Railways / IRCTC. This connector is not officially affiliated with IRCTC or Indian Railways.*