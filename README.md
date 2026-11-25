
# Q :How Do I Access, and where is the files.
# A : I wait until i atleast get it on 30 fps before giving the files

Reach-Project-Emulator-For-GTA-6/
├── README.md                  # Architecture overview, build steps, & Groundwork status table
├── LICENSE                    # MIT, GPL-3.0, or AGPL (prevents ambiguity)
├── CMakeLists.txt / .sln      # Clean, reproducible build configuration
├── src/
│   ├── main.cpp               # CLI / launcher entry point (takes path to unpacked XVC/package)
│   ├── loader/                # [2.0 pts] PE/XEX2/GDK executable mapper & import resolver
│   │   ├── pe_loader.cpp      # Maps sections, relocations, TLS, and exception tables
│   │   └── import_table.cpp   # Binds console DLL imports to HLE shims
│   ├── kernel/                # [2.0 pts] Scarlett OS & GDK HLE modules
│   │   ├── kernelx.cpp        # VirtualAlloc/XMem, threading, fibers, synchronization primitives
│   │   ├── xgameruntime.cpp   # XGameRuntimeInitialize, task queues, user/storage stubs
│   │   └── win32_shims.cpp    # Console-specific Win32 API subset
│   ├── gpu/                   # [3.2 pts] D3D12.X -> PC D3D12 / Vulkan backend
│   │   ├── d3d12_xs.cpp       # Xbox D3D12 device, command queue, & descriptor heap mapping
│   │   └── swapchain.cpp      # Present / frame pacing bridge to Windows HWND
│   ├── shader/                # [2.8 pts] RDNA2 (GFX10.3) shader lifter / translator
│   │   ├── rdna2_decoder.cpp  # Parses precompiled console shader microcode / DXBC-X
│   │   └── spirv_dxil.cpp     # Emits PC DXIL or SPIR-V
│   └── vfs/                   # Virtual file system & DirectStorage / Win32 I/O redirection
├── tests/                     # Crucial for the scout's "tests" check!
│   ├── test_pe_loader.cpp     # Unit tests for PE mapping & import resolution
│   └── test_hle_stubs.cpp     # Tests for XMem / XGameRuntime calls
└── docs/
    └── ARCHITECTURE.md        # Notes on Scarlett HLE ABI & memory layout
