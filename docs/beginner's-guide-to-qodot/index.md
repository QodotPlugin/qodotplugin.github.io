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

This guide assumes you will be using Qodot 4.

Qodot 3 (legacy) instructions will be kept separate if they differ from Qodot 4.

# Qodot 4 Setup

## Prerequisite Steps
1. [Use Godot Engine .NET / mono build](https://godotengine.org/download/).
2. [Download .NET SDK for your OS](https://dotnet.microsoft.com/en-us/download), **must be .NET SDK 7.0 or higher**.
3. Run the .NET SDK installer, ensure it completes successfully.

## Installation
1. Open any Godot project with the mono engine.
2. Search for "Qodot" in the Assetlib, or download the latest release from [Qodot 4 Github](https://github.com/QodotPlugin/qodot/).
3. Download and install the plugin. `/qodot/textures` can be ignored to save on filesize and import time.
4. Go to Project > C# > Create C# Solution. Then click *Build* in the top-right corner.
5. Go to Project > Project Settings > Plugins, then enable Qodot.

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
