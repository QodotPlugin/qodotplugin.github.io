---
layout: default
title: Graphics
nav_order: 9
---

# Graphics
One of the main benefits to using Qodot is that you can apply level design theory from the quake-era of games while using Godot’s many graphical features to make the game stand out visually.

This section does **not** cover how to [Apply Textures](/docs/beginner's-guide-to-qodot/applying-textures.html) or how to [Apply PBR and Shader Materials](/materials.md) to surfaces.

Instead, this section covers how to integrate your Qodot geometry with Godot's graphical systems.

1. TOC
{:toc}

## Lighting
Godot 3.x comes with several lighting options:
-   Dynamic lighting
-   GIProbe
-   BakedLightmap

### Comparison of Lighting Methods

| Benefit | Dynamic Lighting | BakedLightmap | GIProbe |
| :------ | :--------------: | :-----------: | :-----: |
| Optimized for low-end GPUs | ✅ | ✅ |    |
| Updates in realtime | ✅ |    | ✅ |
| Uses bounced light |    | ✅ | ✅ |
| Minimizes project filesize | ✅ |   |   |
| Photorealistic quality |    | ✅ | ✅ |

### Baked Lightmaps

Qodot supports Godot's static lighting pipeline via a UV2 unwrap option available in the action menu of a QodotMap:

#### Lightmap Volumes

In order to bake static lighting for your map in Godot, it must be covered with a set of BakedLightmap volumes. How many are necessary will depend on the side of your map and number of lights- if you try to bake too much at once the editor will crash, so larger maps will need to be split into multiple volumes.

There are some limitations to be mindful of when doing this:
- Each mesh can only be affected by a single lightmap volume
	- Meshes overlapping multiple BakedLightmap volumes will draw from whichever one is lower in the scene tree
- If using BakedLightmap volumes, each will need to have its `Image Path` property set to a different folder
	- Lightmaps are saved alongside the scene file by default, which causes overwrites
- The editor will only update multiple lightmap volumes on scene reload
	- Be sure to save and reload your scene after baking multiple volumes in order to see correct results

#### Lighting Behaviours

- Energy vs Indirect Energy
  - Energy is used for dynamic lighting
  - Energy and Indirect energy both contribute to static lighting if `Bake Mode` is set to `All`

- Light Settings
  - Bake Indirect is used to supplement dynamic direct lighting with baked indirect lighting
    - Results in a hybrid baked + dynamic light
  - Bake All is used to bake both direct and indirect lighting
    - Dynamic lights set to Bake All must have all their render layers disabled for correct results

#### ConeTrace vs RayTrace

- ConeTrace
	- More accurate to dynamic lighting system
	- Similar metrics, so light settings are easily transferable
	- Shorter bake times on account of a simpler algorithm
	- Global illumination / sky lighting
		- Activated by setting `Propagation` to 1
		- Controlled by baked directional lights
- RayTrace
    - Better quality overall
	- More accurate to real-world light behavior
	- Metrics are incompatible with dynamic lighting system
	- Requires more art time to refine

Some unexpected behavior with certain light types is that spotLight uses both Energy and Indirect energy for baked lighting in RayTrace mode.

Using a Node as the parent of a BakedLightmap will break it out of the scene hierarchy, this allows the user to group meshes and lights together for baking in isolation.

#### Tips on Baked Lightmaps

Godot's lightmap process will crash if too many lights or meshes are used. Grouping rooms into Trenchbroom groups rather than a single worldspawn is recommended for baking lights on larger maps/

Be sure to save often or use version control software like Git to avoid loss of work.

Larger maps should be saved as .scn instead of .tscn in order to minimize saving and loading overhead

### Dynamic Lighting

While there’s a limit to 8 dynamic lights per surface, you can switch their bake mode to “all” so they’re only contributing to static lighting in a BakedLightmap.

Because of the 8 dynamic light limit, you’ll have to split these lights apart in some way, or add a BakedLightmap node to render these lights as static.

### GIProbe
GIProbe provides scenes with realtime, indirect light bounces. Using the surrounding area of a GIProbe node, it can determine how nearby objects should bleed light onto eachother. If you have a big red ball in the middle of a white room, the red of the ball will indirectly appear on the white walls.

The method used in Godot 3.x’s GIProbe is _Monte Carlo Based Global Illumination_.
GDQuest’s video tutorial on using GIProbe is really handy if you’re looking for a guide to get started with using it:
https://www.youtube.com/watch?v=lPngD4uzWVc

In Godot 4, _Signed Distance Field Global Illumination_ is coming as another global illumination option on top of the current Monte Carlo method.

### BakedLightmap
If you’re used to mapping for Quake, GoldSrc, Source, or Source 2, BakedLightmap is your light.exe / vrad.exe equivalent.

Make sure you have UV2 unwrapped in the QodotMap settings, Qodot can provide this UV2 unwrap for you.

Use multiple BakedLightmap nodes to split your map up into sections to allow for modular edits to your lighting.

## Reflections
There are two main methods you can achieve reflections in Godot 3.x:
-   Screen space reflections
-   ReflectionProbes

### Comparison of Reflection Methods

| Benefit | ReflectionProbe | SS Reflections |
| :------ | :-------------: | :------------: |
| Optimized for low-end GPUs | ✅ |    |
| Increases project filesize | ✅ |    |
| Updates in realtime |    | ✅ |
| Minimizes project filesize |   | ✅ |

### ReflectionProbe
Reflection probes provide pre-calculated reflections of an area to appear on shiny surfaces. For indoor scenes especially, this is significantly more accurate than letting the sky colour/texture determine the reflections shown on a shiny object.

The official docs for Godot 3 stable have a step-by-step tutorial on using reflection probes: [https://docs.godotengine.org/en/stable/tutorials/3d/reflection_probes.html](https://docs.godotengine.org/en/stable/tutorials/3d/reflection_probes.html)

Reflection probes are not volumetric, they work best in square rooms. You can fake a lot of reflection detail in non-boxy areas by enabling screenspace reflections in your WorldEnvironment.

Reflections are planned to improve greatly in Godot 4.0, where a much faster, approximate, and smoother-looking screenspace reflection method replaces the old screenspace reflections. You can read more about it in the official Godot Engine news post here:
https://godotengine.org/article/vulkan-progress-report-7
