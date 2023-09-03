---
layout: default
title: Beginner's Guide to Qodot
nav_order: 2
has_children: true
---

# Beginner's Guide to Qodot

Welcome! If you get stuck at any time, feel free to ask us on the [Qodot Discord](https://discord.gg/c72WBuG).

Keep in mind, there are two versions of Qodot:
- Qodot 4: [Github](https://github.com/QodotPlugin/qodot/), [Assetlib](https://godotengine.org/asset-library/asset/1631)
- Qodot 3 (Legacy): [Github](https://github.com/QodotPlugin/qodot-plugin/), [Assetlib](https://godotengine.org/asset-library/asset/446)

Qodot 3 (legacy) instructions will be kept separate if they differ from Qodot 4.

# Qodot 4 Setup

## Installation
1. [Use Godot Engine .NET / mono build](https://godotengine.org/download/). **You can still use GDScript with .NET build.**
![godot_dl](https://github.com/QodotPlugin/Qodot/assets/47726614/7a831e4b-dc85-43d5-bb70-e4369d7650da)
2. [Download 7.0 .NET SDK](https://dotnet.microsoft.com/en-us/download) and run the 7.0 SDK installer.
![dotnet_dl](https://github.com/QodotPlugin/Qodot/assets/47726614/18d82487-c66b-47d8-83fc-bc7322720d85)
3. Search for "Qodot" in the Assetlib, or download the latest release from [Qodot 4 Github](https://github.com/QodotPlugin/qodot/).
4. Download and install the plugin. `/qodot/textures` can be ignored to save on filesize and import time.
5. In your Godot Project, go to Project > Tools > C# > Create C# Solution.
![csharpsol](https://github.com/QodotPlugin/Qodot/assets/47726614/6f6f71f7-0db0-4ae9-9acb-81827706675b)
6. Build your C# scripts by pressing <kbd>Alt</kbd> + <kbd>B</kbd>, or click the square *Build* button in the top-right corner.
![image](https://github.com/QodotPlugin/Qodot/assets/47726614/af88e7a0-a6da-43dd-bc8f-50b6877a799a)
7. Go to Project > Project Settings > Plugins, then enable Qodot.

## Troubleshooting

If plugin errors appear when you enable the plugin, restart the engine first. If any plugin errors persist after a restart, please [make an issue](https://github.com/QodotPlugin/Qodot/issues/new).

To bring back the "Full Build" toolbar, press <kbd>Alt</kbd> + <kbd>B</kbd> and re-select your QodotMap node.

# Qodot 3 Setup

## Prerequisites
- The latest build of Godot 3.x, mono not required.

## Installation
1. Search for "Qodot" in the Assetlib, or download the latest release from [Qodot 3 Github](https://github.com/QodotPlugin/qodot-plugin/).
2. Download and install the plugin. `/qodot/textures` can be ignored to save on filesize and import time.
3. Go to Project > Project Settings > Plugins, then enable Qodot.

## Using Qodot

To get started with Qodot, you can read:

1. [Building Maps](building-maps.md) to learn the absolute basics of building maps using Qodot.
2. [Loading Textures](loading-textures.md) to learn how to connect Trenchbroom to Godot and apply your Godot project's textures to geometry using Trenchbroom.

By completing the beginner's guide, you will be able to build and texture maps for Godot using Trenchbroom.
