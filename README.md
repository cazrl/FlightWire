# FlightWire

FlightWire is an XPPython3 plugin for X-Plane 12 that turns the FlightFactor 777v2 free-text ACARS system into an interactive airline operations desk. It combines the current SimBrief flight plan, live aircraft state, operational services, and concise OpenAI-generated replies to make company communication feel useful throughout the flight.

Current open-beta version: **v0.5.0-Beta_B2**

FlightWire is beta software for entertainment and flight simulation only. It is not real-world ATC, dispatch, maintenance, safety, or operational authority.

## Highlights

- **Interactive company ACARS:** exchange free-text messages with an OPS desk that understands the active flight, current phase, aircraft state, recent conversation, retained crew updates, and open operational items.
- **Useful automatic operations support:** Auto-OPS schedules occasional, non-repetitive company contacts across the flight and avoids routine messages when there is nothing useful to say.
- **Dedicated support functions:** independent controls provide ATC, weather, fuel, divert, and ETOPS monitoring when the required data is available.
- **Operational awareness:** FlightWire uses SimBrief route and navlog data, live FF777v2 data, worldwide SIGMET information, optional CheckWX weather, and VATSIM sector/radio data without repeatedly sending the full OFP to OpenAI.
- **Focused fuel monitoring:** planned-versus-actual fuel checks are designed to alert only when the developing arrival-fuel situation becomes operationally serious, with a minimum two-hour alert cooldown.
- **Flight plan and progress tools:** the FPL page presents the data FlightWire has loaded, while route progress and OPS WATCH provide a quick view of the current operational picture.
- **Response control:** the Response Manager lets the user inspect, edit, delay, cancel, or send planned messages. Optional response settings adjust style without changing the default behavior.
- **Flight records and reporting:** OOOI times, manual and autopilot time, defects, significant events, messages, and API usage can be retained in an aviation-style post-flight report.
- **Built-in diagnostics:** bounded rotating logs and sanitized bug reports provide useful troubleshooting information while shielding configured credentials.

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
5. Open **SETTINGS > SERVICES**, enter the required Hoppie, SimBrief, and OpenAI credentials, test them, and press **SAVE**. Add CheckWX only if used.

The release contains the installable `PythonPlugins` folder and documentation. Copy the `PythonPlugins` folder itself into `X-Plane 12\Resources\plugins`; do not copy the complete release ZIP into the simulator folder. Close and restart X-Plane when updating FlightWire.

## How to use

1. Create the intended SimBrief OFP before starting X-Plane. FlightWire loads the latest plan once when the plugin starts.
2. Open FlightWire and confirm the callsign, route, alternate, fuel, and plan information on **MAIN** or **FPL**.
3. On the FF777v2 COMM page, send a free-text Hoppie message to the private OPS station shown on MAIN. The default station is the full callsign plus the configured desk suffix, for example `BOX123MX`.
4. Leave **AUTO-OPS** and any wanted support functions enabled. Unavailable functions are marked `N/A` and do not run.
5. Use **FETCH FPL** only after generating a new or revised SimBrief OFP. FlightWire otherwise retains the loaded plan for the flight.
6. Use the large OPS station button to pause or resume all online FlightWire activity. A long pause does not create a backlog of missed messages.
7. Open **RESPONSE MANAGER** to review, edit, delay, cancel, or immediately send a planned response.
8. Use **LOG** for troubleshooting. Use **BUG REPORT** from Settings when a technical problem needs to be submitted, and review the sanitized report before sending it.
9. At the end of the flight, FlightWire can export its post-flight report to the folder selected under report settings.

Hoppie polling does not contact OpenAI. OpenAI is used only when FlightWire actually needs to generate a message.

## Support functions

- **ATC Support:** checks whether the active callsign is on VATSIM and whether COM1 or COM2 matches relevant sector coverage before issuing a bounded advisory.
- **WXR Support:** combines CheckWX arrival and alternate checks with low-frequency domestic and international SIGMET monitoring along the remaining route. It does not determine active runways or landing minima.
- **Fuel Support:** compares reliable SimBrief/navlog planning against actual fuel and warns only when a credible arrival-fuel emergency risk develops. Alerts have a minimum two-hour cooldown.
- **Divert Support:** retains phase-appropriate candidates, crew decisions, reasons, weather and fuel context, and follow-ups without pretending to make the command decision.
- **ETOPS Support:** follows usable SimBrief ETP sectors and reports a primary-divert change when the equal-time point is crossed.

## OpenAI cost estimates

These projections represent a 12-hour flight with all FlightWire features enabled. Actual usage depends on the number and complexity of generated messages, the selected model, and current OpenAI pricing.

| Model | Predicted flight cost |
|---|---:|
| GPT-4o mini | ~$0.0018 |
| GPT-4.1 mini - default | **~$0.0049** |
| GPT-5.6 Luna | ~$0.0137 |
| GPT-5.6 Terra | ~$0.0342 |
| GPT-5.6 Sol | ~$0.0683 |

The model selector normally shows only suitable models returned for the entered OpenAI account. If model discovery is unavailable, FlightWire offers only the conservative GPT-4.1 mini and GPT-4o mini fallback choices. The optional per-flight API limit defaults to `$0.10`.

## Settings, storage, and privacy

Settings and current-flight memory are stored as `FlightWire.json` and `FlightWire_memory.json` in X-Plane's preferences directory, outside the plugin folder, so normal updates retain them. Never publish `FlightWire.json`.

Credential fields are shielded after successful testing. Logs and bug reports are sanitized for common credentials, personal paths, and email addresses, but users must still review report content. Diagnostic files rotate at 5 MiB with two backups.

Public Beta B builds use an independent remote version-policy lane. A check sends only the FlightWire version and never a callsign, credential, flight plan, or installation identifier. A successful check creates a seven-day Windows-DPAPI-protected authorization lease and is normally rechecked every 12 hours. A retired build disables FlightWire operational networking while keeping X-Plane, the local UI, LOG, and bug reporting available.

GitHub and Ko-fi shortcut squares are active. Reserved X-Plane.org and Discord squares are visibly inactive until destinations are published.

## Documentation

The user manual and changelog are included in the downloadable release ZIP.

## Licence

FlightWire is distributed under the **FlightWire Personal Use License 1.0**. Personal, non-commercial use is permitted. Redistribution, resale, rebranding, commercial use, and publishing modified versions require prior written permission. See [LICENSE](LICENSE).

The historical `v0.3.0-alpha` release remains under the MIT License that accompanied that specific release.

## Support

Use the in-simulator **BUG REPORT** function for a sanitized technical report. For general enquiries or when the relay is unavailable, contact **connect.flightwire@gmail.com**.
