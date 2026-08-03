# FlightWire Roadmap

These are planned directions for FlightWire. They are not promises for a particular release or listed in a fixed development order. Features will only be advertised as supported after successful flight testing.

## Aircraft compatibility

- **Zibo 737 integration**  
  Bring FlightWire messaging to the Zibo FMC through a dedicated **AOC → Company Message** page, subject to permission and a supported integration path from the Zibo developers.

- **Additional aircraft support**  
  Expand FlightWire to more X-Plane aircraft that provide a reliable two-way company-message workflow. Every aircraft will be individually tested before being advertised as supported.

## Company messaging

- **Interactive company responses**  
  Investigate cockpit **ACCEPT** and **REJECT** controls for suitable OPS messages. FlightWire will only use AOC/company functionality—never ATC CPDLC controls or simulated ATC clearances.

- **Companion datalink mirroring**  
  Explore a safe way for the Mobile Companion to display messages received directly through the aircraft's Hoppie channel, including controller datalink messages, without competing with the aircraft's own Hoppie client or consuming messages before they reach the cockpit.

- **Pinned flight notes**  
  Allow pilots to ask OPS to retain important operational information for the remainder of the flight.

## Operational data

- **Navigraph integration**  
  Add optional Navigraph authorization and use approved navigation data to strengthen route, airport, position and diversion context.

- **Installed-airport awareness**  
  Recognize installed add-on airports so diversion support can account for the airports and scenery actually available to the user.

- **VAMSYS and Pegasus integration**  
  Explore an optional, supported connection for virtual-airline users without unreliable process scanning or interfering with existing flight tracking.

## Distribution

- **Automatic updates**  
  Investigate SkunkCrafts Updater integration so FlightWire can be updated more easily while preserving credentials and user settings.
