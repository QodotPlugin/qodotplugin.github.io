---
layout: default
title: Tips for Veterans
nav_order: 12
---

# Tips for Veterans

This is a list of caviats about the Qodot workflow that is likely to change the way a BSP veteran would map.

## Performance

Like many engines, Godot features three types of culling to hide unused geometry:  
- backface culling
- frustum culling
- occlusion culling (new in Godot 3.4)

Qodot also doesn't create vertices for faces completely covered-up by other worldspawn brushes.

While it's possible to use Godot's occlusion culling with Qodot, there is not yet any official integration. This may change in future Qodot versions.

Here are a few other caviats about performance that is likely to change how you map for Qodot:

- There are no automated visibility checks built into your map. There is no VIS step like there was in Quake, GoldSrc, and Source.
- Although VisLeaves aren't generated with a map anymore, you should still keep your brushwork clean for better organization.
- You can split your map meshes by grouping brushes together.
- You can turn off collision of a brush by making it a func_illusionary.
- The detail levels for GoldSrc's func_details are no longer needed; you can prevent brushes from splitting the vertices of adjacent faces by giving them different materials, or by grouping the adjacent brushes into unique groups.
- Modern discrete GPUs and their drivers have much more power these days; maps made for games on desktop PCs don't need to be ruthlessly optimized as early-era BSP mapping often necessitated.
- You don't have to seal your map.
- Covering a map with SKIP and painting textures onto individiual faces still contains minor benefits to performance.
- You can combine multiple QodotMap nodes in one Godot scene, and use this to instance repetitive geometry in your Godot scene.
- If you want a feature from a specific game, like func_breakable_surf, you need to implement it using Entities.
- In Godot, there is no serious performance loss from having excess CollisionShapes generated in a map.

## Tool Textures

- The only tool textures used in Qodot maps are Skip and Clip.
- Skip works the same as Nodraw.
- The path to these textures are defined in your QodotMap properties, with the Textures Directory as the root. The defaults are "special/clip" and "special/skip".
- No unique functionality is gained from applying a special texture to once face.
- Skip and Clip are functionally similar: they hide a face from rendering vertices, but they also create collision.
	- Clip is useful as an indicator that this is meant to assist with collision
	- Skip identifies a face that shouldn't be seen.
- You can still use a personal Trigger texture to indicate brushes that are tied to a custom trigger entity, for the sake of organization and clarity.

## Godot separates collisions from meshes

- Getting footstep sounds from the material you're walking on is possible, but not included as a feature in Qodot.
- You can use Worldspawn Layers to collect brushes under a single, `class_name`d StaticBody, letting you organize brushes by the sound they should make, or how the player's physics should respond to different Worldspawn Layers. See the Qodot demo scenes for more info.
- You can use Solid Classes to replicate the effect of Worldspawn layers.

## Assets

- Adding new entities and textures is much easier, no need to compress into a VTF and provide metadata.
- Model support isn't as flexible as source: one model per point entity.
