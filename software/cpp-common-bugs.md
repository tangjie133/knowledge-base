---
title: Common C++ Bugs and Fixes
category: bugfix
tags: [cpp, bug, common]
---

# Common C++ Bugs and Fixes

## Assignment Typo

### Problem

Copy-paste error in array assignment:

```cpp
// WRONG:
sendBuf[0] = x >> 8 & 0xff;
sendBuf[1] = x & 0xff;
sendBuf[2] = y >> 8 & 0xff;
sendBuf[3] = y & 0xff;
sendBuf[4] = z >> 8 & 0xff;
sendBuf[5] = y & 0xff;  // BUG: should be z
```

### Fix

```cpp
// CORRECT:
sendBuf[5] = z & 0xff;
```

## Variable Name Typos

| Wrong | Correct |
|-------|---------|
| `recieve` | `receive` |
| `seperate` | `separate` |
| `occured` | `occurred` |

## Comparison vs Assignment

```cpp
// Wrong
if (x = 5) { }  // Always true!

// Correct
if (x == 5) { } // Comparison
```

## Off-by-One Error

```cpp
// Wrong
for (int i = 0; i <= 10; i++) {
  array[i] = i;  // array[10] is out of bounds!
}

// Correct
for (int i = 0; i < 10; i++) {
  array[i] = i;
}
```
