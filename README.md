# Snapmaker U1 — Klipper Configuration

> **Use at your own risk.** This configuration has been extensively tested on my U1 with no issues, but I accept no responsibility for any damage to your printer.

This configuration optimizes the TMC2240 settings for the integrated XY stepper motors, enabling higher speeds and accelerations during tool changes.

## Key Changes from Defaults

- **TMC2240 XY motors:** Custom chopper tuning (`TBL`, `TOFF`, `HEND`, `HSTRT`, `TPFD`, `VHIGHFS`, `VHIGHCHM`, `PWM_*`) for improved high-speed performance
- **Max acceleration:** 25,000 mm/s²
- **Max XY velocity:** 1,000 mm/s
- **Tool change acceleration:** 25,000 mm/s²
- **Tool change speed (fast):** 800 mm/s
- **Sensorless homing:** TMC2240 (XY) and TMC2209 (Z) with reduced homing current
- **Input shaper (MZV):** X = 54 Hz, Y = 47.5 Hz

## Requirements

Before using this config, ensure:

1. Tool dock positions are calibrated correctly
2. Belt tension is correct
3. Full printer calibration has been completed
4. Tool changes work reliably with the stock configuration

## Installation

1. Back up your existing `printer.cfg`
2. Copy `printer.cfg` to `/userdata/printer_data/config/printer.cfg` on your U1
3. Restart Klipper
4. Re-run bed mesh calibration (`BED_MESH_CALIBRATE`) — the placeholder mesh in this file must be replaced with data from your printer

## Test Setup

| Component | Version                             |
|-----------|-------------------------------------|
| Printer   | U1 (Kickstarter, without top cover) |
| Firmware  | v1.3.0-paxx12-xx (extended)         |
| Slicer    | Snapmaker OrcaSlicer 2.3.1          |

## Notes

- The TMC2240 driver temperature readout is unreliable. When active it may read ~20°C higher than the actual value.
- The bed mesh in `SAVE_CONFIG` is a placeholder — replace it with your own calibration data.
- `[include extended/klipper/*.cfg]` requires the extended Snapmaker Klipper firmware.
- v1.1.1 requires **Snapmaker OrcaSlicer 2.2.4+** or Snapmaker App 2.2.3+.
- v1.1.1 adds heated bed flatness deviation detection and new filament presets (PETG HF, TPU 95A HF).
- v1.3.0 recommended to use it with **Snapmaker Orca V2.3.1+** or Snapmaker App V2.3.2+.
- v1.3.0 adds support for multiple nozzle diameters (0.2mm / 0.4mm / 0.6mm / 0.8mm)
- v1.3.0 improves the AI defect detection model, optimizes pogo pin continuity detection logic, improves extrusion flow calibration and updated built-in parameters 
