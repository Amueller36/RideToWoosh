# Changelog

All notable changes to this project are documented here.
Format follows [Keep a Changelog](https://keepachangelog.com/); versioning is [SemVer](https://semver.org/).

## [1.0.0] — Unreleased

First public release.

### Added

- ESP32-S3 firmware: reads the Zwift Ride controller over BLE (Central + `RideOn`
  handshake) and emits configurable keystrokes as a BLE-HID keyboard, both roles over
  NimBLE.
- Bilingual (EN/DE) web UI with tile navigation: live view + get-started checklist,
  key mapping with an **on-screen key picker** (works on phones), one-tap
  **MyWhoosh/Zwift presets**, duplicate-key warnings, unsaved-changes indicator,
  50-entry history log, and a connected-devices view (address type + OUI vendor).
- Accessibility: landmarks, heading outline, `aria-live` regions, focus management,
  44 px touch targets, contrast fixes, keycap styling, consistent SVG icon set.
- Dedicated `cfg` NVS partition for the mapping, isolated from system NVS; mutex-guarded
  state (no cross-task races).
- Reduced AP TX power (proximity as access control); WPA2-PSK config AP.
- Single web server: the WebSocket runs at `/ws` on port 80 (the separate
  port-81 server was removed).
- `GET /status` JSON endpoint (firmware, connection state, device labels, IP,
  uptime, free heap) for headless health checks.
- Verified against real Zwift Ride hardware: broad "Zwift" name match (it
  advertises "Zwift Ride"/"Zwift SF2", service `0xFC82`), button bitmap mapped
  empirically, button data via notify + RideOn via write-no-response.
- Analog steering levers decoded (protobuf field 3, zig-zag sint32 −100..100,
  id0 left / id1 right) and exposed as four mappable virtual buttons.
- Reduced BLE scan duty cycle so the WiFi AP coexists (fixes AP join/DHCP timeout).
- Home dashboard shows a live, symmetric SVG map of the Zwift Ride cockpit (D-pad,
  A/B/Y/Z diamond, shift paddles, orange brake/steer levers, aux buttons) that lights
  up the pressed button in real time, plus the key it emits. Bilingual labels.
- Logo, GitHub social preview, rendered UI screenshots; GPL-3.0.

[1.0.0]: https://example.com/REPLACE-WITH-REPO-URL/releases/tag/v1.0.0
