# FlightWire

FlightWire is an XPPython3 plugin for X-Plane 12 that connects the FlightFactor
777v2 ACARS workflow to a simulated airline operations and maintenance desk.
It combines Hoppie's ACARS network, SimBrief flight-plan data, live simulator
context, and concise OpenAI-generated company replies.

Current public-test version: **v0.4.2-Beta_130**

FlightWire is beta software for entertainment and flight simulation only. It
is not real-world ATC, dispatch, maintenance, safety, or operational authority.

## Highlights

- Uses the full flight callsign plus `MX` as the private company desk address,
  for example `BOX123MX`.
- Loads the latest SimBrief OFP on a fresh plugin start and only reloads it
  when the pilot presses **FETCH FPL**.
- Adds relevant OFP and live FF777v2/X-Plane context to company messages.
- Generates concise OPS or maintenance replies only when a message actually
  needs OpenAI; Hoppie polling itself does not call the OpenAI API.
- Provides deterministic handling for ETOPS following, divert support, EETA,
  open-item, next-contact, and supported timed-follow-up requests.
- Offers optional Auto-OPS contacts spread across the flight, ETOPS sector
  alerts, fuel-deviation warnings, and bounded CheckWX arrival/alternate
  weather monitoring.
- Records OOOI times, sterile takeoff/approach phases, airborne autopilot and
  manual time, defects, messages, and per-flight OpenAI usage.
- Creates an optional post-flight text report in a user-selected folder,
  `Documents/FlightWire` by default, with an X-Plane Output fallback.
- Includes MAIN, FPL, SETTINGS, and LOG pages, a Response Manager, sanitized
  direct bug reporting, selectable text consoles, and BRIGHT/DARK/AUTO themes.

FlightWire currently supports the FlightFactor 777v2 natively. Other aircraft
do not provide the same free-text ACARS workflow and are not advertised as
supported.

## Requirements

- Windows 10 or Windows 11
- X-Plane 12
- XPPython3 v4.7.0 using Python 3.12
- FlightFactor 777v2
- Hoppie logon code
- SimBrief account username or user ID
- OpenAI Platform API key with available API billing or credit
- Internet access

CheckWX is optional. Navigraph integration is prepared but remains unavailable
until FlightWire receives developer credentials; its status is shown as
`PLANNED` and dependent fields show `N/A`.

A ChatGPT subscription does not automatically include OpenAI API credit.

The first public beta is Windows-only because saved credentials are protected
with Windows DPAPI. macOS and Linux must not be advertised until a secure
cross-platform credential store and protected runtime have been tested there.

## Installation

1. Close X-Plane.
2. Open the release ZIP.
3. Copy its complete `PythonPlugins` folder into
   `X-Plane 12\Resources\plugins` and allow the folders to merge.
4. Start X-Plane.
5. Open **Plugins > FlightWire > Open FlightWire**.
6. Open **SETTINGS > SERVICES**, enter the required Hoppie, SimBrief, and
   OpenAI credentials, test them, and press **SAVE**. Add CheckWX only if used.

The packaged runtime contains `PI_GPTBridge.py` and the `flightwire` folder.
The legacy entrypoint filename is retained temporarily so an in-place update
overwrites the old plugin rather than leaving two XPPython3 entrypoints.

Do not copy the complete ZIP into `PythonPlugins`; public documentation sits
outside the installation folder. Close and restart X-Plane when updating.

## Normal workflow

1. Generate the intended SimBrief OFP before starting X-Plane.
2. Confirm the flight identity and OFP values on MAIN or FPL.
3. Confirm the displayed company desk is the full callsign followed by `MX`.
4. Send normal free-text Hoppie telex messages to that exact address.
5. Use the OPS button to pause or resume Hoppie polling when required.
6. Use the Response Manager to inspect, edit, delay, cancel, or manually send
   a planned FlightWire follow-up.
7. Review LOG when diagnosing unexpected behavior and use BUG REPORT only
   after checking the automatically sanitized report content.

Useful company-message examples are listed in the in-simulator HOW TO USE
guide and in the user manual. FlightWire deliberately avoids advertising
requests for information the aircraft already knows better than OPS.

## Settings and privacy

Settings are stored as `FlightWire.json` in X-Plane's preferences directory,
not in the plugin folder, so normal upgrades retain them. Existing
`GPTBridge.json` and `GPTBridge_memory.json` files are migrated once and kept
for rollback.

Credential fields are shielded after successful testing. Logs and bug reports
are sanitized, but users must still review report content and must never share
`FlightWire.json`.

Response humor and the additional response controls are optional prompt-only
preferences. Their middle/default positions preserve the established response
behavior exactly. They never alter deterministic safety/operational messages,
routing, polling, scheduling, retries, or flight-state logic.

Starting with Beta 130, public builds include a transparent remote version-policy
check. It sends only the FlightWire version, never a callsign, credential,
flight plan, or installation identifier. A successful check creates a
seven-day Windows-DPAPI-protected authorization lease in
`FlightWire_version_policy.json`; the policy is rechecked approximately every
12 hours. A confirmed retired build disables
FlightWire operational networking while leaving X-Plane, the local UI, logs,
and bug reporting available. Builds released before this client was added
cannot be retired retroactively.

As with any HTTPS request, Cloudflare receives ordinary connection metadata
such as the source IP. The version-policy Worker does not store or use it.

## Updating

Close X-Plane, merge the new release ZIP's `PythonPlugins` folder into
`X-Plane 12\Resources\plugins`, allow FlightWire files to be replaced, and
restart X-Plane. Configuration and flight memory live outside the plugin
folder and are retained. Do not distribute or copy `__pycache__` directories.

## Documentation and testing

- [User manual](docs/FlightWire_Public_Beta_Manual_v0.4.2.pdf)
- [Public beta test checklist](PUBLIC_BETA_TEST_NOTES.md)
- [Beta 130 release notes](RELEASE_NOTES_BETA_130.md)
- [Roadmap](ROADMAP.md)
- [Changelog](CHANGELOG.md)

## Licence

FlightWire is distributed under the **FlightWire Personal Use License 1.0**.
Personal, non-commercial use is permitted. Redistribution, resale, rebranding,
commercial use, and publishing modified versions require prior written
permission. See [LICENSE](LICENSE).

The historical `v0.3.0-alpha` release remains under the MIT License that
accompanied that specific release. The current licence does not retroactively
change that earlier grant.

## Support

Use the in-simulator **BUG REPORT** function for a sanitized technical report.
For general enquiries or when the relay is unavailable, contact
**connect.flightwire@gmail.com**.
