# jphein/GDK-Proton Fork

Fork of [Weather-OS/GDK-Proton](https://github.com/Weather-OS/GDK-Proton) for running Minecraft Bedrock Edition on Linux via Lutris.

## Purpose

Testing Minecraft Bedrock with the Proton-based approach (GDK-Proton bundles WineGDK + DXVK + Steam Runtime as a Proton distribution). Part of the [minecraft-bedrock-linux](https://github.com/jphein/minecraft-bedrock-linux) project.

## Status

GDK-Proton produces the same black screen as plain WineGDK on NVIDIA GPUs. The root cause is in bgfx (Minecraft's rendering layer), not in the D3D11 implementation — both wined3d and DXVK show identical behavior (zero draw calls). See [minecraft-bedrock-linux#4](https://github.com/jphein/minecraft-bedrock-linux/issues/4).

### Tested configurations (all black screen)
- GDK-Proton + DXVK (default)
- GDK-Proton + wined3d (`PROTON_USE_WINED3D=1`)
- GDK-Proton + WINE_DISABLE_VULKAN_OPWR

### What works
- Game launches with audio
- MangoHUD overlay visible (confirming DXVK swap chain works)
- D3D11 resources created successfully

## Changes from upstream

No source changes yet. This fork tracks upstream for testing against our NVIDIA Wayland setup.

## Installation via Lutris

The `lutris-installer.yaml` in [minecraft-bedrock-linux](https://github.com/jphein/minecraft-bedrock-linux) configures Lutris to use a local GDK-Proton build.

## Related repos

- [jphein/minecraft-bedrock-linux](https://github.com/jphein/minecraft-bedrock-linux) — Main project: scripts, stubs, documentation
- [jphein/WineGDK](https://github.com/jphein/WineGDK) — Our WineGDK fork (plain Wine + GDK patches)
- [Weather-OS/GDK-Proton](https://github.com/Weather-OS/GDK-Proton) — Upstream
- [LukasPAH/GDK-Proton-Custom](https://github.com/LukasPAH/GDK-Proton-Custom) — Community fork with additional fixes

## System tested on

- Ubuntu 24.04, kernel 6.8.0-111
- NVIDIA GTX 1650 (TU117), driver 595.58.03
- Wayland (GNOME) + XWayland

---

*See upstream README below for GDK-Proton build instructions and component list.*
