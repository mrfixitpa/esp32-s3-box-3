# Changelog

All notable changes to this project will be documented in this file.

This project follows a simple semantic versioning approach:
- **Major** versions introduce new user-facing features or behavior changes
- **Minor** versions add functionality or improvements
- **Patch / Pre-release** versions fix bugs or regressions during testing

---
## [v1.3.0] – 2026-01-09

### Added
- UI Theme Color Picker exposed as an ESPHome-only RGB light.
- Full Home Assistant color wheel support without HA helpers or templates.
- Theme color applied consistently to:
  - Idle clock
  - AM / PM indicator
  - Indoor temperature text

### Fixed
- Restored idle screen clock rendering regression.
- Corrected ESPHome light implementation to ensure successful compilation and installation.

### Behavior Notes
- HVAC status icons are intentionally excluded from theming:
  - 🔥 Heating icon is always red
  - ❄️ Cooling icon is always blue
- Screen backlight remains brightness-only (hardware limitation).

### Validation
- Tested and verified through multiple pre-release iterations.
- Package YAML fully validated with no duplicate keys or invalid platforms.

---

## [v1.3.0-pre.2] – 2026-01-09

⚠️ **Pre-release** — fixes issues found in `v1.3.0-pre.1`.

### Fixed
- ESPHome compilation failure caused by use of an invalid `light.template` platform.
- Replaced the invalid template light with a **valid virtual RGB light** backed by template outputs.

### Changed
- UI Theme Color Picker implementation corrected while preserving the same Home Assistant color wheel UI.

### Validation
- Package YAML fully validated:
  - No duplicate top-level keys
  - All referenced IDs verified
  - Successful ESPHome install confirmed

---

## [v1.3.0-pre.1] – 2026-01-09

⚠️ **Pre-release** — intended for testing and validation before v1.3.0 stable.

### Added
- UI Theme Color Picker exposed as an ESPHome-only RGB light.
- Full Home Assistant color wheel support without HA helpers or templates.
- Theme color applied consistently to:
  - Idle clock
  - AM / PM indicator
  - Indoor temperature text

### Fixed
- Restored idle screen clock regression introduced in earlier releases.

### Behavior Notes
- HVAC status icons are intentionally excluded from theming:
  - 🔥 Heating icon is always red
  - ❄️ Cooling icon is always blue
- Screen backlight remains brightness-only (hardware limitation).

---

## [v1.2.4] – 2026-01-08

### Fixed
- Attempted fix for idle clock rendering issue.

### Notes
- This release is superseded by v1.3.0 pre-releases due to package validation issues.

---

## [v1.2.3] – 2026-01-06

### Added
- Indoor temperature display on idle screen.
- HVAC status icon support using Ecobee `hvac_action`.

### Improved
- Bubble-free display layout for all voice assistant states.

---
