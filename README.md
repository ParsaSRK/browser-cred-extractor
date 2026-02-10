# Windows Browser Credential Access (Security Research)

## Overview

This project is a **red team / security research tool** demonstrating how locally
stored browser credentials can be accessed and decrypted on **Windows systems**
when executed with **authorized access**.

It models a **post-compromise credential access scenario** commonly evaluated
during authorized penetration testing, red team engagements, and training labs.

Authorized use only.
Execute only on systems you own or have explicit permission to test.

---

## Scope

- Platform: Windows
- Context: Local execution with user-level permissions
- Focus: Browser credential storage and decryption
- Out of scope:
  - Privilege escalation
  - Persistence
  - Lateral movement

---

## Technical Notes

- Interfaces with browser credential databases
- Uses platform-specific cryptographic services
- Decryption routines execute in the local Windows environment
- Some cryptographic operations depend on system-specific APIs
- Network handling is modular and intended for controlled lab setups

---

## Dependencies

### Runtime Dependencies

- Windows API
- LibSodium
- SQLite3

### Build Dependencies

- CMake
- Windows-compatible compiler toolchain

---

## Cross-Compilation Setup (Linux → Windows)

### Debian-based systems

    sudo apt install binutils-mingw-w64-x86-64 \
                     gcc-mingw-w64-x86-64-win32 \
                     gcc-mingw-w64-base \
                     mingw-w64-common \
                     mingw-w64-x86-64-dev

### Arch-based systems

    sudo pacman -S mingw-w64-binutils \
                 mingw-w64-crt \
                 mingw-w64-gcc \
                 mingw-w64-headers \
                 mingw-w64-winpthreads

---

## Build Configuration

The project is configured using CMake with compile-time parameters.

### Configuration Flags

- -DHOSTNAME : Target host (IP or hostname)
- -DPORT     : HTTP port (default: 80)
- -DPATH     : HTTP endpoint path (default: /)

### Example Configuration

    cmake -B build \
      -DHOSTNAME="192.168.1.1" \
      -DPORT=5656 \
      -DPATH="/app"

### Build

    cmake --build build

---

## Legal & Ethical Notice

This project is intended solely for **security research and authorized testing**.
Unauthorized use may violate applicable laws and organizational policies.

---

## Status

Maintained as a security research and red team training reference.
