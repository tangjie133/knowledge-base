---
title: Frequently Asked Questions
category: faq
tags: [faq, general]
---

# Frequently Asked Questions

## How to install the library?

### Arduino IDE

1. Sketch → Include Library → Add .ZIP Library
2. Select downloaded file
3. Restart IDE

### PlatformIO

Add to `platformio.ini`:

```ini
lib_deps = your-library-name
```

## What hardware is supported?

Supported:
- Arduino Uno/Nano/Mega
- ESP32
- ESP8266
- STM32

Not supported:
- Arduino Due (incompatible)

## How to report bugs?

Please include:
1. Library version
2. Hardware platform
3. Minimal code to reproduce
4. Expected vs actual behavior
5. Serial monitor output

## Performance is slow

Optimization tips:
1. Reduce Serial.print in loops
2. Use non-blocking delays
3. Check for memory leaks
4. Increase buffer sizes

Example:

```cpp
// Bad: blocking
void loop() {
  Serial.println("Reading...");
  delay(1000);
}

// Good: non-blocking
unsigned long lastRead = 0;
void loop() {
  if (millis() - lastRead > 1000) {
    // do work
    lastRead = millis();
  }
}
```
