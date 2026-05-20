# jphein/GDK-Proton Fork

> **Status: Archive / Not Recommended.** WineGDK is the working path for Minecraft Bedrock on Linux. GDK-Proton is not recommended for Minecraft 1.26.20+ (causes crashes, per upstream maintainer ChristopherHX). This fork is kept as a reference.

Fork of [Weather-OS/GDK-Proton](https://github.com/Weather-OS/GDK-Proton) for running Minecraft Bedrock Edition on Linux via Lutris.

## Purpose

Testing Minecraft Bedrock with the Proton-based approach (GDK-Proton bundles WineGDK + DXVK + Steam Runtime as a Proton distribution). Part of the [minecraft-bedrock-linux](https://github.com/jphein/minecraft-bedrock-linux) project.

## Current Status

**WineGDK is now the recommended and working path.** Minecraft Bedrock Edition renders and runs correctly under plain WineGDK.

### Resolution of the black screen issue

The black screen originally attributed to bgfx / D3D11 draw call issues ([minecraft-bedrock-linux#4](https://github.com/jphein/minecraft-bedrock-linux/issues/4)) was caused by **using the wrong game binary** -- version 1.26.3 instead of the correct 1.26.21. With the correct binary, the game renders properly under WineGDK.

### Why not GDK-Proton?

ChristopherHX (upstream WineGDK maintainer) has explicitly stated: **do not use the current GDK-Proton** -- it causes crashes on Minecraft 1.26.20 and later. The GDK-Proton approach bundles additional layers (DXVK, Steam Runtime) that introduce instability with newer Minecraft versions. Plain WineGDK avoids these issues.

### Previous testing (for reference)

The following configurations were tested before the root cause was identified. All produced a black screen due to the wrong game binary, not due to GDK-Proton itself:

- GDK-Proton + DXVK (default)
- GDK-Proton + wined3d (`PROTON_USE_WINED3D=1`)
- GDK-Proton + WINE_DISABLE_VULKAN_OPWR
- Plain WineGDK with various D3D11 backends

## Recommended Path

Use **WineGDK** directly (not through GDK-Proton):

- Repository: [jphein/WineGDK](https://github.com/jphein/WineGDK)
- Setup scripts: [jphein/minecraft-bedrock-linux](https://github.com/jphein/minecraft-bedrock-linux)

Ensure you are using the correct game binary version (1.26.21+, not 1.26.3).

## Changes from upstream

No source changes. This fork tracked upstream for testing against our NVIDIA Wayland setup.

## Related repos

- [jphein/minecraft-bedrock-linux](https://github.com/jphein/minecraft-bedrock-linux) -- Main project: scripts, stubs, documentation
- [jphein/WineGDK](https://github.com/jphein/WineGDK) -- Our WineGDK fork (plain Wine + GDK patches) **[recommended]**
- [Weather-OS/GDK-Proton](https://github.com/Weather-OS/GDK-Proton) -- Upstream
- [LukasPAH/GDK-Proton-Custom](https://github.com/LukasPAH/GDK-Proton-Custom) -- Community fork with additional fixes

## System tested on

- Ubuntu 24.04, kernel 6.8.0-111
- NVIDIA GTX 1650 (TU117), driver 595.58.03
- Wayland (GNOME) + XWayland

---

*See upstream README below for GDK-Proton build instructions and component list.*
