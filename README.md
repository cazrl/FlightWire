# FlightWire

FlightWire is an XPPython3 plugin for X-Plane 12 that turns the FlightFactor 777v2 free-text ACARS system into an interactive airline operations desk. It combines the current SimBrief flight plan, live aircraft state, operational services, and concise OpenAI-generated replies to make company communication feel useful throughout the flight.

Current open-beta version: **v0.5.0-Beta_B2**

FlightWire is beta software for entertainment and flight simulation only. It is not real-world ATC, dispatch, maintenance, safety, or operational authority.

## Highlights

- **VATSIM Advisory:** detects relevant departure, enroute, and arrival controllers along the planned route and includes the station name and frequency when available.
- **SIGMET Advisory:** evaluates worldwide SIGMET hazards against the remaining route, affected flight levels, predicted encounter time, and advisory validity.
- **ETOPS Following:** follows usable SimBrief ETOPS sectors and advises when crossing an equal-time point changes the primary divert airport.
- **Event-driven support:** weather, ATC, fuel, divert, ETOPS, arrival-gate, and maintenance monitoring create messages only when there is something relevant to report.
- **Mobile Companion:** delivers FlightWire OPS messages, essential PFD-style aircraft data, autopilot-mode alerts, top-of-descent reminders, and optional background notifications to an iPhone.
- **AI-powered context-driven responses:** creates flight-specific OPS replies using the active flight plan, aircraft state, flight phase, retained crew updates, open follow-ups, and recent conversation. OpenAI or Ollama is contacted only when FlightWire needs to create a message.

FlightWire currently supports the FlightFactor 777v2 natively. Other aircraft do not provide the same free-text ACARS workflow and are not advertised as supported.

## Requirements

- Windows 10 or Windows 11
- X-Plane 12
- XPPython3 v4.7.0 using Python 3.12
- FlightFactor 777v2
- Hoppie logon code
- SimBrief username or user ID
- OpenAI Platform API key with available API billing or credit
- Internet access
- Optional CheckWX API key

Navigraph integration is prepared but unavailable until FlightWire receives developer credentials. Its UI status remains `PLANNED` and dependent values show `N/A`.

A ChatGPT subscription does not include OpenAI API credit. The beta is Windows-only because saved credentials use Windows DPAPI protection.

## Installation

1. Install [XPPython3](https://xppython3.readthedocs.io/en/latest/).
2. Copy the `PythonPlugins` folder from the release ZIP into `X-Plane 12\Resources\plugins` and overwrite when prompted.
3. Start X-Plane.
4. Open **Plugins > FlightWire > Open FlightWire**.
