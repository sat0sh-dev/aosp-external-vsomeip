# vsomeip for AOSP

Phase 4: SOME/IP integration

## Overview

This module provides vsomeip (SOME/IP implementation) for AOSP builds.

**Upstream**: https://github.com/COVESA/vsomeip

## Libraries

| Library | Description |
|---------|-------------|
| libvsomeip3.so | Core functionality (required) |
| libvsomeip3-cfg.so | Configuration module (JSON) |
| libvsomeip3-sd.so | Service Discovery |
| libvsomeip3-e2e.so | End-to-End protection |

## Dependencies

- Boost >= 1.66.0 (system, thread, filesystem)
- C++17

## Directory Structure

```
external/vsomeip/
├── Android.bp                    # Build configuration
├── interface/vsomeip/            # Public headers
└── implementation/
    ├── configuration/
    ├── endpoints/
    ├── message/
    ├── routing/
    ├── runtime/
    ├── service_discovery/
    └── e2e_protection/
```

## Setup

1. Clone vsomeip from https://github.com/COVESA/vsomeip
2. Copy `interface/` and `implementation/` directories
3. Build with AOSP

## Build

```bash
# In AOSP build environment
m libvsomeip3
```

## Configuration

Configuration file: `/product/etc/vsomeip/vsomeip.json`

Example:
```json
{
    "unicast": "192.168.0.1",
    "logging": {
        "level": "debug",
        "console": "true"
    },
    "applications": [
        { "name": "service-sample", "id": "0x1277" }
    ],
    "routing": "service-sample"
}
```

## References

- [vsomeip GitHub](https://github.com/COVESA/vsomeip)
- [SOME/IP Protocol Specification](https://www.autosar.org/standards/foundation)
