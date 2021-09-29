---
layout: default
title: Geometry
nav_order: 8
---

1. TOC
{:toc}

# Geometry

This is a miscelaneous category for features related to mapping that generally apply to all projects. You should read [Beginner's Guide to Qodot](/docs/beginner's-guide-to-qodot/) before reading this page.

# Clipping

Clipping is a unique feature that allows a QodotMap to build collisions without any mesh geometry. You can choose one texture in your project directory to act as your "clip" texture.

In the Clip Texture property, add the subfolder and image name for your clip texture without the file extension. For example, if you have this for your Godot folder structure:

```
res://
	/textures
		/special
			clip.png
```

You can set clip.png as the clip texture by adding `/special/clip` into the Clip Texture field of a QodotMap.

# Scale

Having a well-defined ratio from Quake units to the ones used by your game is important - it can make it easier to reason about the layout of your maps, and having your object scale translate properly to the equivalent real-world measurement will result in more accurate physics simulation.

The *Inverse Scale Factor* property on a QodotMap node determines the ratio between Quake units (used in TrenchBroom and other editors) to Godot's metric coordinate system. All Quake coordinates are divided by this value to create Godot coordinates during build.

As the metric used by map files varies game-by-game, this setting is dependent on your assets, game logic and physics simulation, and will have to be decided on a case-by-case basis. The table below lists some common examples, as well as reasoning for their usage.

|              Name | Inverse Scale Factor |     1qu |    2qu |    4qu |    8qu |   16qu | Notes |
| ----------------: | :------------------- | :------ | :----- | :----- | :----- | :----- | :---- |
|  .map Passthrough |                    1 |       1 |      2 |       4|      8 |     16 | 1:1 with map file, Godot grid corresponds to TrenchBroom grid. Will result in very large geometry by Godot standards. |
|     Qodot Default |                   16 |  0.0625 |  0.125 |   0.25 |    0.5 |    1.0 | 'Best effort' mapping from Quake 1 environments to metric. |
|          Uradamus |                   40 |   0.025 |   0.05 |    0.1 |    0.2 |    0.4 | Artist-friendly setting with tidy fractional numbers. |
| Valve Environment |       52.49343832021 | 0.01905 | 0.0381 | 0.0762 | 0.1524 | 0.3048 | Half Life 1/2 environment metric. |

# Advanced Geometric Shapes

Trenchbroom maps are built on a grid, so trying to create curves, arches, and tunnels can be challenging. Luckily, [Quake Builder](https://www.youtube.com/channel/UCMkmAYBVLAC9jGIUD4LjacA) is a YouTube channel with a wide array of videos that cover advanced mapping topics in Trenchbroom.

As of writing, here is a full list of every advanced geometry topic that [Quake Builder](https://www.youtube.com/channel/UCMkmAYBVLAC9jGIUD4LjacA) has covered:

- [Curves](https://youtu.be/NmEfbds-CFk)
- [Angular Steps](https://www.youtube.com/watch?v=Wi9YjbLpjIA)
- [Arches](https://www.youtube.com/watch?v=fTwe2lEu95s)
- [Terrain/Displacements](https://www.youtube.com/watch?v=Nhx4VEZUr80)
- [Clipping](https://youtu.be/pIFaiRCqres)
- [Tunnels with Curves](https://www.youtube.com/watch?v=E27I6JCn9jw)
- [Spiral Staircases](https://www.youtube.com/watch?v=k-5itcvV8uM)
