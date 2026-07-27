# FlightWire

FlightWire brings a simulated airline operations and maintenance desk into the FlightFactor 777v2 ACARS workflow. It combines the SimBrief operational flight plan, live simulator context, Hoppie communications, deterministic operational logic, and concise AI-generated company replies.

Flightwire requires OpenAI API credit ($5 minimum) but consumes only cents per long-haul flight.

> Currently being tested in closed-beta. Contact me with your github username if you want access.

[View public releases](https://github.com/cazrl/FlightWire/releases)

## Highlights

- Turns the FF777v2 free-text ACARS workflow into a context-aware virtual airline OPS and maintenance desk.
- Builds replies from the actual flight: SimBrief OFP data, aircraft state, flight phase, position, fuel, timing, weather context, and the conversation already in progress.
- Provides practical operational support for diversions, ETOPS changes, EETA updates, fuel deviations, arrival and alternate weather concerns, defects, and requested follow-ups.
- Adds optional Auto-OPS contacts that are spread naturally across the flight instead of repeating at fixed intervals, while contacting OpenAI only when a message actually needs to be written.
- Keeps the pilot in control through the Response Manager, where planned follow-ups can be reviewed, edited, delayed, cancelled, or sent manually.
- Presents a dedicated operations workstation with a one-page LIDO-style FPL view, live flight overview, diagnostic LOG, selectable message text, and BRIGHT, DARK, and AUTO display modes.
- Records OOOI events, defects, messages, manual and autopilot time, and API usage for an optional end-of-flight operations report.
- Protects saved credentials with Windows DPAPI and sanitizes logs and reports before they leave the simulator.

## Native aircraft support

FlightWire currently supports the **FlightFactor 777v2** natively. It is built around that aircraft's free-text ACARS workflow and live simulator data. Other aircraft are not advertised as supported because they do not provide the same integration.

## From dispatch release to flight closure

- Loads the latest SimBrief OFP when FlightWire starts and retains it until the pilot deliberately fetches a replacement.
- Uses flight phase and aircraft state to keep responses relevant during preflight, departure, cruise, arrival, and shutdown.
- Can provide deterministic dispatch clearance, ETOPS following, divert assistance, EETA retention, fuel-deviation advisories, and supported scheduled follow-ups.
- Can monitor CheckWX arrival and alternate conditions when the optional service is configured.
- Suppresses Auto-OPS distractions during sterile takeoff and approach phases.
- Creates an optional post-flight operations report in a user-selected folder.

FlightWire deliberately avoids filling messages with advice the crew already knows, such as generic reminders to contact ATC or monitor the aircraft.

## Requirements

- Windows 10 or Windows 11
- X-Plane 12
- XPPython3 v4.7.0 using Python 3.12
- FlightFactor 777v2
- Hoppie logon code
- SimBrief username or user ID
- OpenAI Platform API key with available API billing or credit (uses tiny ammounts of credit per flight)
- Internet access

CheckWX is optional. Navigraph functionality remains unavailable until FlightWire receives and implements approved developer access. A ChatGPT subscription does not include OpenAI API credit.

## Installation

1. Install XPPython3. https://xppython3.readthedocs.io/en/latest/
2. Copy the PythonPlugins folder from the release zip into X-Plane 12\Resources\plugins and overwrite.
3. Start X-Plane.
4. Open **Plugins > FlightWire > Open FlightWire**.
5. Open **SETTINGS > SERVICES**, enter the required Hoppie, SimBrief, and
   OpenAI credentials, test them, and press **SAVE**. Add CheckWX only if used.

Do not copy the complete ZIP into PythonPlugins. Public documentation remains outside the installation folder. Restart X-Plane after every update.

## Services, privacy, and cost

FlightWire polls Hoppie without contacting OpenAI. The OpenAI API is used only when a company message actually needs to be written. Per-message token and cost information is recorded in LOG, and the user can configure a session spending limit.

Saved credentials are shielded in the UI and protected locally with Windows DPAPI. Logs and bug reports are sanitized, but every report must still be reviewed before submission. Never share FlightWire.json, API keys, or Hoppie credentials.

Version authorization sends the FlightWire release identity but no callsign, flight plan, credential, or installation identifier. Existing Beta 129/130 builds, future Beta B releases, and private Alpha tests use independent authorization sequences.

FlightWire is beta software for entertainment and flight simulation only. It is not real-world ATC, dispatch, maintenance, safety, or operational authority.

## Development status

- The current public-test information and releases remain in this repository.
- The next external testing cycle will begin privately with Beta B1.
- No closed-beta or public Beta B1 release has been published yet.
- Future public releases will continue the Beta B sequence after closed testing.
- User-facing plans are listed in the [roadmap](ROADMAP.md).

## Support

Use the in-simulator BUG REPORT function for a sanitized technical report. For general enquiries or when the relay is unavailable, contact **connect.flightwire@gmail.com**.

If FlightWire adds something to your flights, you can support development at [Ko-fi](https://ko-fi.com/flightwire).

## Licence

Current FlightWire builds are distributed under the FlightWire Personal Use License 1.0 included with the release. Personal, non-commercial use is permitted. Redistribution, resale, rebranding, commercial use, and publishing modified versions require prior written permission.

The historical v0.3.0-alpha release remains under the MIT License that accompanied that specific release.
