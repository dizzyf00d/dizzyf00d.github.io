---
layout: post
title: Valve’s Gamescope
description: Valve’s Gamescope the Micro-Compositor Revolutionizing Gaming
summary: A blog post about Valve’s Gamescope, the Micro-Compositor Revolutionizing Gaming.
tags: linux wayland x11 valve
---

# Valve’s Gamescope: The Micro-Compositor Revolutionizing Gaming
Valve’s Gamescope is a micro-compositor that has been making waves in the gaming industry. Born out of the former SteamCompMgr, Gamescope focuses on optimized game presentation with efficient Wayland usage and various optimizations to reduce frame latency.

## What is Gamescope?
Gamescope is a micro-compositor that was formerly known as steamcompmgr. It is designed to deliver the best gaming performance atop Wayland, including working as a nested compositor on a regular Linux desktop.

## How does it work?
Gamescope gets game frames through Wayland by way of Xwayland, so there’s no copy within X itself before it gets the frame. It can use DRM/KMS to directly flip game frames to the screen, even when stretching or when notifications are up, removing another copy. When it does need to composite with the GPU, it does so with async Vulkan compute, meaning you get to see your frame quick even if the game already has the GPU busy with the next frame.

## Benefits of Gamescope
One of the key benefits of Gamescope is that it runs on top of a regular desktop, a ‘nested’ use case that steamcompmgr didn’t support. Because the game is running in its own personal Xwayland sandbox desktop, it can’t interfere with your desktop and your desktop can’t interfere with it. You can spoof a virtual screen with a desired resolution and refresh rate as the only thing the game sees, and control/resize the output as needed.

## Compatibility
Gamescope runs on Mesa + AMD or Intel, and could be made to run on other Mesa/DRM drivers with minimal work. AMD requires Mesa 20.3+, Intel requires Mesa 21.2+1. For NVIDIA’s proprietary driver, version 515.43.04+ is required (make sure the nvidia-drm.modeset=1 kernel parameter is set).

## Launch Options
Here are some examples of launch options for Valve’s Gamescope micro-compositor:

* **Running Steam with Gamescope**: You can force Steam to run using Gamescope by using the following command:
  ```gamescope -e -- steam```
The -e flag tells Gamescope to enable Steam Integration.

* **Running games from Steam with Gamescope**: You can also run games from Steam using Gamescope by adding the following to the game’s launch options:
  ```gamescope -- %command%```

* **Enabling AMD FidelityFX Super Resolution (FSR)**: With Gamescope, there is now the `-U` launch argument for enabling the FSR upscaling as well as `--fsr-sharpness` for enabling FSR sharpness support.

* **Running Gamescope in a nested session**: After building, you can launch it directly on a VT or from another Wayland/X11 session in nested mode. For example, to start Steam with it, you can use:
  ```gamescope -e -- steam -tenfoot -steamos```

* **Keyboard shortcuts**: There are several keyboard shortcuts available in Gamescope:
  * ```Super + F```: Toggle fullscreen.
  * ```Super + N```: Toggle nearest neighbour filtering.
  * ```Super + U```: Toggle FSR upscaling.
  * ```Super + Y```: Toggle NIS upscaling.

Please note that these commands should be run in a terminal or command line interface.