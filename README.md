# Reach Project Emulator For GTA 6

Tracking updates, research, and development progress for the Reach Project GTA 6 emulator.

## Current Status
- **Status:** Early development (emulator files are not yet released).
- **Performance:** Running at ~15 FPS.
- **Graphics:** Drawings and rendering are working well.
- **Audio:** Still in progress and needs further work.

## Update Log
- **Initial Milestone:**
  - Confirmed stable execution at **15 FPS**.
  - Verified **drawings and rendering** pipeline is functioning properly.
  - Identified **audio** subsystem as the next area requiring work.

## FAQ
**Q: How do I access it, and where are the files?**  
**A:** I am waiting until I get it running at least at **30 FPS** before releasing the files.

## Planned Layout

```text
Reach-Project-Emulator-For-GTA-6/
├── README.md                  # Architecture overview, build steps, & groundwork status table
├── LICENSE                    # MIT, GPL-3.0, or AGPL
├── CMakeLists.txt / .sln      # Build configuration
├── src/
│   ├── main.cpp               # CLI / launcher entry point (path to unpacked package)
│   ├── loader/                # Executable mapper & import resolver
│   │   ├── pe_loader.cpp      # Maps sections, relocations, TLS, and exception tables
│   │   └── import_table.cpp   # Binds console DLL imports to shims
│   ├── kernel/                # OS & runtime modules
│   │   ├── kernelx.cpp        # Memory allocation, threading, fibers, synchronization
│   │   ├── xgameruntime.cpp   # Runtime initialization, task queues, user/storage stubs
│   │   └── win32_shims.cpp    # Win32 API subset
│   ├── gpu/                   # PC D3D12 / Vulkan backend
│   │   ├── d3d12_xs.cpp       # Device, command queue, & descriptor heap mapping
│   │   └── swapchain.cpp      # Present / frame pacing bridge
│   ├── shader/                # Shader decoder / translator
│   │   ├── rdna2_decoder.cpp  # Parses precompiled shader microcode
│   │   └── spirv_dxil.cpp     # Emits DXIL or SPIR-V
│   └── vfs/                   # Virtual file system & I/O redirection
├── tests/                     # Unit tests
│   ├── test_pe_loader.cpp     # Tests for executable mapping & import resolution
│   └── test_hle_stubs.cpp     # Tests for memory & runtime calls
└── docs/
    └── ARCHITECTURE.md        # Notes on ABI & memory layout
