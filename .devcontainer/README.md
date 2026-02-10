# Devcontainer Configuration for Verilog Development

This devcontainer provides a minimal Verilog development environment with the OSS CAD Suite.

## Features

- **Base Image**: Debian Bookworm Slim (minimal)
- **OSS CAD Suite**: Latest release from [YosysHQ/oss-cad-suite-build](https://github.com/YosysHQ/oss-cad-suite-build/releases)
- **Verilog Tools**: Yosys, Verilator, IceStorm, nextpnr, and more from OSS CAD Suite
- **VS Code Extensions**: 
  - Verilog/SystemVerilog language support
  - TerosHDL for advanced HDL development
  - WaveTrace for waveform viewing

## Usage

1. Open this repository in VS Code
2. When prompted, click "Reopen in Container" or run the command "Remote-Containers: Reopen in Container"
3. The container will be built automatically and the OSS CAD Suite will be installed
4. All tools from OSS CAD Suite are available in the PATH by default

## Available Tools

The OSS CAD Suite includes:
- Yosys (Verilog synthesis)
- Verilator (Verilog simulator and lint tool)
- IceStorm (FPGA toolchain for Lattice iCE40)
- nextpnr (FPGA place and route)
- And many more HDL tools

Verify installation with:
```bash
yosys --version
verilator --version
```

## Customization

You can modify the Dockerfile to:
- Change the base image to Alpine if you prefer (change `FROM debian:bookworm-slim` to `FROM alpine:latest`)
- Add additional system packages
- Configure different OSS CAD Suite versions

You can modify devcontainer.json to:
- Add or remove VS Code extensions
- Change editor settings
- Add custom features
