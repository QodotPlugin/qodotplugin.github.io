---
layout: default
title: Tips for Veterans
nav_order: 12
---

# Tips for Veterans

This is a list of caviats about the Qodot workflow that is likely to change the way a BSP veteran would map.

## Assets

- Drop a .jpg or .png into your project to add new textures. See [Materials](materials.md) for more info.
- Model support isn't as flexible as something like Source. Each point entity can only display one model in the Trenchbroom editor. See [Entities](entities.md) for more info.

## Gameplay
- With the default Qodot.fgd, you can turn off a brush's collision by making it a func_illusionary. You can add this definition to your own FGD to replicate this behaviour. See [Entities](entities.md) for more info.
- You can combine multiple QodotMap nodes in one Godot scene, and use this to instantiate repetitive/procedural geometry in your Godot scene.
- If you want a feature from a specific game, like Source's `func_breakable_surf`, you'll need to implement it yourself using [Entities](entites.md), or refer to community repositories like [Qodot Entities on Github](https://github.com/RhapsodyInGeek/qodot-entities) for other's creations.

## Geometry

- You don't need to seal your map.
- Although you can intersect brushes and go off-grid, you should avoid it to keep your brushwork clean.
- Clean brushwork still pays off in organiztion, even though they don't generate visleaves.

## Visibility

Godot features four types of culling to hide unused geometry:  
- backface culling
- frustum culling
- occlusion culling (new in Godot 3.4)
- portal culling (new in Godot 3.4)

Qodot 1.9 does not have an automated solution for portal or occlusion culling, as there are many different ways to approach it.

For portal culling, consider splitting the map mesh by grouping brushes, and placing Portal and Room nodes to fit the bounds of each group. See [Rooms and Portals on the Godot Docs](https://docs.godotengine.org/en/stable/tutorials/3d/portals/index.html) to read more.

For occlusion culling, placing an Occluder node between the player and any MeshInstance nodes causing overdraw should improve performance. Occlusion relies on hiding the [AABB](https://docs.godotengine.org/en/stable/classes/class_aabb.html) of each MeshInstance, and it will not cull level geometry if your map is not split into several Trenchbroom groups or QodotMap nodes.

## Optimization

Modern PCs and consoles are far more powerful than when Quake, Half Life, and Half Life 2 were first released. While map optimization is still helpful for all platforms - notably mobile and web - it matters far less if your target platform is only modern desktops and consoles. While you're free to optimize everything as necessary, it's no longer a requirement for all projects like it may have been for previous games.

Try to test your game on different platforms, and use the Godot profiler while developing to check if your map is causing spikes in draw calls, vertices, and video memory.

Here are some tips for map optimization:

- In general, you can apply the SKIP texture to reduce the vertex count.
- When using BakedLightmap, placing SKIP on unseen faces will increase the texture fidelity for lighting data on surrounding visible faces.
- You can reduce (or increase) the lightmap texture size in BakedLightmap's properties, and in your map's MeshInstance using the Lightmap Hint Size property.
- So long as your map remains a StaticBody, your map can have several excess CollisionShapes with nearly zero impact on physics performance.

## Tool Textures

- The only tool textures used in Qodot maps are SKIP and CLIP.
- SKIP works the same as NODRAW.
- The path to these textures are defined in your QodotMap properties, with the QodotMap's Textures Directory as the root. The defaults are "special/clip" and "special/skip".
- SKIP and CLIP are functionally similar: they hide a face from rendering vertices, and they create collision.
	- Clip is useful as an indicator that this is meant to assist with collision
	- Skip identifies a face that shouldn't be seen.
- You can still use a personal TRIGGER texture to indicate brushes that are tied to a custom trigger entity, for the sake of organization and clarity.
- The same goes for other tool textures that aren't included with Qodot, if you'd like to extend its capabilites.

## Footstep Sounds

Godot separates collisions from meshes, so although it is possible, there is no built-in Godot or Qodot solution to get the material from the object you've collided with.

One option is to use Worldspawn Layers to collect brushes under a single StaticBody with a script, that returns specific data when the user calls a method on the StaticBody.

See the Qodot demo scenes for an example of splitting brushes by Worldspawn Layers.

You can also use Solid Classes to replicate the effect of Worldspawn Layers, but you'll lose the ability to tie additional Solid Class behaviour to any of its child brushes, without duplicating classes unnecessarily. See [Entities](entities.md) for more info on creating a Solid Class.
