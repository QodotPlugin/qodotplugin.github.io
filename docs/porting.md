---
layout: default
title: Porting
nav_order: 8
---

1. TOC
{:toc}

# Porting

Porting a map means you don't have to make the geometry yourself. On a less-comical note, porting allows you to re-experience maps from other games in the Godot engine. Qodot was made for porting Quake 1 maps, but it also is capable of porting:

- Standard
- Valve
- Quake
- Quake 2
- Quake 3
- Quake 3 (Legacy)
- Hexen 2
- Daikatana

Qodot supports the full range of Quake-derived texture formats.

# Prerequisites

Before starting to import a map into Qodot, it's important to check if you have the following:  
- A Trenchbroom .cfg that supports your specific game.
- A .map that doesn't crash Trenchbroom when saving or loading, using your game's .cfg.  
- Textures as .wad or image files.  
- All .fgd files used to define the map's entities.

## How to get around missing prerequisites

If you don't have a game config for your ported game, even after searching community forums, try loading it into other game definitions. You can read the [Trenchbroom Manual](https://trenchbroom.github.io/manual/latest/#game_configuration_file_syntax) for more info on creating a .cfg file from scratch.

If your map cannot be loaded or saved properly, you may need to try other game definitions in Trenchbroom. It can help to compare the .map file structure to other .map files which can load correctly in Trenchbroom.

If your map is missing .fgd files, you will be missing out on the map's entities. You can build the map with Qodot anyways, and any issues with missing/wireframe geometry can be solved by deleting any `undefined` entities in the .map.

If you don't have the map's textures, you can re-texture the map geometry with .png and .jpg/.jpeg files as shown in [Texturing your map](#texturing-your-map).
