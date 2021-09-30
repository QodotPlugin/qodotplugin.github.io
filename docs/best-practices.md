---
layout: default
title: Best Practices
nav_order: 10
---

# Best Practices

This document covers several topics including how to:
- Organize your project folders
- Get the most performance out of Qodot
- Get the best quality out of Godot using Qodot
- Avoid development disasters and pitfalls when using Qodot

These are all subject to change over time as we all get more experience using Qodot.

1. TOC
{:toc}

# Tips

## Don't add to Addons
Don’t add files to the `/addons` folder yourself. Your original work can be erased if Godot auto-updates Qodot, or if you ignore the `/addons` folder in a Git repository to save on space.

Instead, create a new folder on `res://` for whatever you’re adding.

## Use .gdignore to ignore Map Autosaves

If you store your .map files in your Godot project directly, Trenchbroom will create a subfolder called `/.autosave` as a sibiling of your map. This can be annoying in Godot since it runs the import process on any new asset. Qodot enables .map as an asset type. Every time Trenchbroom autosaves, Godot will try to index and prepare the new autosave for import. This is mostly an issue when scaling up, as you'll likely want to reduce file indexing times and make it easier to parse the FileSystem dock as the project grows in size.

You can tell Godot to ignore any file by adding an empty file with the name `.gdignore` in the same directory as all files that should be ignored. Adding a .gdignore to any `/.autosave` folder will prevent these maps from triggering the import process.

## Separate your world textures
When you set your project directory in Trenchbroom, it looks for an immediate subfolder called `/textures`. If you just want textures in the game, this is fine:
- Game Path: `C:/Users/Ember/Gamedev/MyQodotProject/`
- Automatically-detected textures path: `C:/Users/Ember/Gamedev/MyQodotProject/textures/`

But this goes against a certain philosophy of organizing files. You can always just search for your textures by looking for "png" in the FileSystem, it's more useful to organize assets by **context** rather than existing metadata that's already inherent to the file.

So there should actually be no one-size-fits-all `/textures` folder. Instead, Trenchbroom just cares about **world** textures. Adding a top-level `/trenchbroom` or `/world` folder to keep level design assets can leverage you to create a structure like this:

```
res://
	/trenchbroom
		/textures
```

This way, your world textures can stay wholly separate from your UI and model textures.

If you go this route, you'll have to adjust your Trenchbroom game path to point to the `/trenchbroom` subfolder inside your Godot project, rather than just the root of your Godot project. It's a bit more complicated, but then it ensures that Trenchbroom will only look inside its designated folder.

Although Trenchbroom can't automatically pickup entity definitions made by Qodot, you can also keep all Qodot-related resources inside this `/trenchbroom` folder for easier organizing. An example of this would be:

```
res://
	/trenchbroom
		/textures
		/enemy_entities
			enemy_base.tres
			enemy_fly_point.tres
			enemy_walk_point.tres
			enemy_heal_solid.tres
		my_game_fgd.tres
```

Again, this is only one example on the principle of organizing by context, not by file extension. This is all completely optional compared to what's described in the beginner's guide.

# Project structure examples

## Basic Texturing
Here’s an example of a folder structure for basic texturing.
```
/textures
	/foliage
		vines.png
		grass.png
```
`/foliage` can be replaced by any group name you’d like. The vines* and grass* textures can be replaced by any name appropriate for the texture you're adding.

Only .png files or ,jpg files are valid. You can’t use both file extensions at the same time per map. You can configure this on a QodotMap node's properties.

## Material Override
Either .material files, or .tres files containing a SpatialMaterial or ShaderMaterial, but not both file extensions at the same time.
```
/textures
	/jungle
		vines.png
		vines.material
		zebra.png
		zebra.material
```

## Automatic PBR Texturing
This format is required for any material using PBR texturing.
```
/textures
	/foliage
		/vines
			vines_normal.png
			vines_displacement.png
			vines_roughness.png
		vines.png
```

In the example above, the only names that can change is the group name, `/foliage`, and the material name referenced anywhere in the above structure: vines.
You can put `/foliage` into more sub-folders if you need, so long as its contents remain the same as far as structure is concerned.

## Storing .map files
To make your project easy to control through a VCS like Git, and to make it easier to send your entire project file to others, it helps to store your .map files inside your Godot project directly.

Because Godot 3.x doesn't have an LOD system or occlusion culling, it depends on the scope and style of your project to determine how you should name .map files to meet the corresponding .tscn that the game switches to. An open-world game may not use the conventional:
```gdscript
get_tree().change_scene("res://levels/jungle.tscn")
```
and instead might load-in and loud-out .tscn files as needed. The specifics of this are entirely up to you as they're nonstandard.

However, for more linear games, you can adopt a system that names .map files by their .tscn filenames.