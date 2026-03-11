---
title: Sensor Not Reading Data
category: troubleshooting
tags: [sensor, hardware, troubleshooting, dfrobot]
---

# Sensor Not Reading Data

## Problem

The sensor is set up and detecting presence, but not reading respiration and heart rate.

## Solutions

### 1. Check Firmware Version

Requires firmware v2.0+ for HR/respiration features.

```cpp
void setup() {
  Serial.begin(115200);
  sensor.begin();
  
  String version = sensor.getVersion();
  Serial.print("Firmware: ");
  Serial.println(version);
}
```

### 2. Enable Features

```cpp
void setup() {
  sensor.begin();
  sensor.enableHeartRate();
  sensor.enableRespiration();
}
```

### 3. Check Placement

- Distance: 0.5 - 2 meters
- Direction: Face chest directly
- Avoid: Metal objects nearby

### 4. Calibration

First use requires 30-second calibration:

```cpp
void setup() {
  sensor.begin();
  sensor.enableHeartRate();
  
  Serial.println("Calibrating...");
  while (!sensor.isCalibrated()) {
    delay(100);
  }
  Serial.println("Done!");
}
```

## Still Not Working?

Check power supply (stable 5V) and try different USB cable.
