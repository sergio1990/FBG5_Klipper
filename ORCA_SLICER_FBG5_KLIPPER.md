# Orca Slicer Configuration (FBG5 + Klipper)

This document captures the active Orca Slicer printer profile for the Flying Bear Ghost 5 (FBG5) running Klipper, based on the current Orca UI configuration and this repository's Klipper macros.

## Profile Identity

- Profile name: `Klipper Flying Bear Ghost 5 0.4 nozzle`
- Printer type: Cartesian
- Firmware flavor: Klipper
- Nozzle diameter: 0.4 mm
- Filament diameter: 1.75 mm
- Bed size (X/Y): 250 x 210 mm
- Build height (Z): 200 mm
- Origin: Front-left

## Basic Information Tab

### Printable Space

| Setting | Value |
|---|---|
| Printable area | Set in Orca profile (matches 250 x 210 bed) |
| Excluded bed area | `0x0` |
| Printable height | `200 mm` |
| Support multi bed types | `Off` |
| Nozzle volume | `130 mm^3` |
| Best object position | `X 0.50, Y 0.50` |
| Z offset | `0 mm` |
| Preferred orientation | `0 deg` |

### Advanced

| Setting | Value |
|---|---|
| G-code flavor | `Klipper` |
| Pellet Modded Printer | `Off` |
| Disable set remaining print time | `Off` |
| G-code thumbnails | `300x300/PNG` |
| Use relative E distances | `On` |
| Use firmware retraction | `Off` |
| Time cost | `0.2 money/h` |

### Cooling Fan

| Setting | Value |
|---|---|
| Fan speed-up time | `0 s` |
| Fan kick-start time | `0 s` |
| Only overhangs | `On` |

### Extruder Clearance

| Setting | Value |
|---|---|
| Radius | `67 mm` |
| Height to rod | `54 mm` |
| Height to lid | `140 mm` |

## Machine G-code Tab

### Machine start G-code

```gcode
START_PRINT BED=[hot_plate_temp_initial_layer] EXTRUDER=[nozzle_temperature_initial_layer] MESH=default
```

### Machine end G-code

```gcode
END_PRINT
```

### Printing by object G-code

Leave empty.

### Before layer change G-code

```gcode
;BEFORE_LAYER_CHANGE
;[layer_z]
```

### Layer change G-code

```gcode
;AFTER_LAYER_CHANGE
;[layer_z]
```

### Time lapse G-code

Leave empty (unless timelapse-specific macros are added).

## Extruder 1 Tab

### Size and Position

| Setting | Value |
|---|---|
| Nozzle diameter | `0.4 mm` |
| Layer height min | `0.12 mm` |
| Layer height max | `0.28 mm` |
| Extruder offset | `X 0 mm, Y 0 mm` |

### Retraction

| Setting | Value |
|---|---|
| Length | `2 mm` |
| Extra length on restart | `0 mm` |
| Retraction speed | `40 mm/s` |
| Deretraction speed | `40 mm/s` |
| Travel distance threshold | `1 mm` |
| Retract on layer change | `Off` |
| Retract on top layer | `On` |
| Wipe while retracting | `Off` |
| Wipe distance | `2 mm` |
| Retract amount before wipe | `0 %` |

### Z-Hop

| Setting | Value |
|---|---|
| On surfaces | `All Surfaces` |
| Z-hop type | `Normal` |
| Z-hop height | `0 mm` |
| Traveling angle | `3 deg` |
| Only lift Z above | `0 mm` |
| Only lift Z below | `0 mm` |

### Retraction When Switching Material

| Setting | Value |
|---|---|
| Length | `0 mm` |
| Extra length on restart | `0 mm` |

## Motion Ability Tab

### Advanced

| Setting | Value |
|---|---|
| Emit limits to G-code | `On` |

### Speed Limitation

| Setting | Value |
|---|---|
| Maximum speed X | `150 mm/s` |
| Maximum speed Y | `150 mm/s` |
| Maximum speed Z | `5 mm/s` |
| Maximum speed E | `15 mm/s` |

### Acceleration Limitation

| Setting | Value |
|---|---|
| Maximum acceleration X | `3000 mm/s^2` |
| Maximum acceleration Y | `3000 mm/s^2` |
| Maximum acceleration Z | `30 mm/s^2` |
| Maximum acceleration E | `2000 mm/s^2` |
| Maximum acceleration for extruding | `1000 mm/s^2` |
| Maximum acceleration for retracting | `1000 mm/s^2` |
| Maximum acceleration for travel | `5000 mm/s^2` |

### Jerk Limitation

| Setting | Value |
|---|---|
| Maximum jerk X | `10 mm/s` |
| Maximum jerk Y | `10 mm/s` |
| Maximum jerk Z | `2 mm/s` |
| Maximum jerk E | `2.5 mm/s` |

## Klipper Macro and Limits Alignment

- `START_PRINT` expects `BED` and `EXTRUDER` parameters, with optional `MESH`.
- `END_PRINT` is defined in `macroses.cfg`.
- Slicer speed and acceleration limits match `printer.cfg` machine limits:
  - `max_velocity: 150`
  - `max_accel: 3000`
  - `max_z_velocity: 5`
  - `max_z_accel: 30`
  - `max_extrude_only_velocity: 15`
  - `max_extrude_only_accel: 2000`
