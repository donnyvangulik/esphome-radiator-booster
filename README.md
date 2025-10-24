# Radiator Booster (ESPHome)

An ESPHome-based controller for a 4-wire PWM fan with temperature-driven curves, manual override, and USB-PD 12 V enable.

- **Board:** Adafruit Feather ESP32-S3 (no PSRAM)
- **Firmware:** ESPHome
- **Features:**
  - Heating & cooling logic with hysteresis + EMA smoothing
  - Temperature → PWM curve (**10% @ 27.5 °C → 80% @ 50 °C**)
  - Manual PWM override slider + “Return to Auto” button
  - RPM feedback via tach (pulse_meter)
  - Safe secrets handling

## Getting started

## Where to buy

Radiator Booster controller board:

- TinyTronics — Radiatorventilator USB‑PD Controller (ESP32‑S3): https://www.tinytronics.nl/nl/domotica/sensoren/klimaat/radiatorventilator-usb-pd-controller-esp32-s3



> **Hardware requirement:** You'll need a **USB‑PD charger** capable of delivering **12 V** (≥ 2 A recommended) and a USB‑C cable.


1. **Clone:**
   ```bash
   git clone https://github.com/<you>/radiator-booster.git
   cd radiator-booster
   ```

2. **Secrets:**
   ```bash
   cp esphome/secrets.example.yaml esphome/secrets.yaml
   # Edit Wi-Fi credentials inside esphome/secrets.yaml
   ```

3. **Validate (ESPHome >= 2025.6.0):**
   ```bash
   pipx run esphome compile esphome/radiator-booster.yaml  # or: esphome config ...
   ```

4. **Upload (USB):**
   ```bash
   pipx run esphome run esphome/radiator-booster.yaml
   ```

5. **Home Assistant:** Add via ESPHome integration, then import the Lovelace example from `docs/dashboard-example.yaml`.

## Hardware

See `hardware/wiring-diagram.png` and `esphome/radiator-booster.yaml` pin comments.

## Configuration

- **Heating curve:** linear 10% at 27.5 °C → 80% at 50 °C (editable via `Ts1`, `Ts2` sliders).
- **Cooling curve:** independent reversed ramp (`Ts1_cool` → `Ts2_cool`).
- **Manual override:** slider sets duty when >0%. “Return to Auto” clears override.

## Development

- CI validates the config on PRs (see `.github/workflows/validate-esphome.yml`).
- Versioning uses **Keep a Changelog** + SemVer in `CHANGELOG.md`.

## License

MIT — see `LICENSE`.
