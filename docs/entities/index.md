---
layout: default
title: Entities
nav_order: 7
has_children: true
---

# Entities
Entities tie Godot functionality to 3D positions and marked brushes in your map file.

This page is a WIP, currently in the process of being broken into succinct subpages.

1. TOC
{:toc}

# Index of Subpages

- [Intro to Entities](intro.md)
- [Creating Entities](creating-entities.md)
- [FGDs](fgd.md)
- [Game Definitions](cfg.md)
- [Scripting Entities](scripting-entities.md)

# Old Tutorials

The headers below will eventually be moved/edited to another page.

## Models in Trenchbroom
You can display a model in TrenchBroom over a Point Class definition. You can then set up the equivalent model in Godot.

### Requirements

- The model has to be an .obj
- You have to create an entity definition for this model specifically in your game’s FGD.
- You have to enable `obj_neverball` in your Trenchbroom Game Config with this line: `"modelformats": [ "obj_neverball" ]`.
- You cannot swap models in and out of Trenchbroom like you can with Source.
- The support for scaling models in Trenchbroom is coming soon, but know that old Trenchbroom versions don't support scaling models.

### Setup

You can add a **Meta Properties** in your point entity definition with model as the key and the relative path of your .obj file as the value.

Example: `key: model value: "entities/models/my_model.obj"`

Warning
{: .label .label-red }
Add quotes surrounding your value, or TrenchBroom will crash when placing your entity class.

Now that you’ve done this, you also need to update your game config every time your FGD changes. You can repeat the process for exporting a game config from earlier to overwrite the entire folder.

## Entity creation examples

After every entity you create, there are 3 steps to ensure that Trenchbroom and QodotMap are aware of its existence. You can do these in a batch, or one-by-one.

1. Update your game's FGD to hold a new entity definition, featuring your new .tres file(s).
2. Re-export your Trenchbroom game config with your updated FGD included.
3. Add your FGD to a QodotMap's *Entity Fgd*, either directly, or as a *Base Fgd File* inside another FGD.

### Placing scenes with point entities

In this example, I’m going to make a point entity that will spawn a Godot scene, containing a tree with collision.

Start by making own point entity: right click on a folder in Filesystem, and click _Create New Resource_. Search for “Qodot” and you should get a list of resources to extend.

![](../images/point-entity.png)

In my case, I just want to set the origin of my .tscn, so I’m choosing QodotFGDPointClass. I don’t need it to be a solid brush or an abstract base class.
I named mine prop_tree.tres

![](../images/point-prop-tree.png)

I’m going to prepare a tree scene that I want the prop_tree.tres to represent.
Here’s my tree scene, it’s a StaticBody so the player collides with it, but you can have any type of node here instead to make up this entire scene.

![](../images/point-scene-tree.png)

I’ll save it next to the .tres so it’s easy to find and update both files representing the same entity.

![](../images/point-save-next.png)

Now I can double click on the .tres. I’m going to set the Scene File to the tree scene:

![](../images/point-scene-file.png)

Notice I only needed to change the Scene File and the Classname in this .tres. Everything else is optional.

Now we can include this entity in a new FGD file. That way, Qodot can parse all of our game’s objects, and we can load them into Trenchbroom as well. This is covered earlier in the [Creating an FGD file](#creating-an-fgd-file) section.

To learn more about working with props and entities, read the [Qodot Wiki page on Entities.](https://github.com/Shfty/qodot-plugin/wiki/4.-Entities)

### Creating a Brush Entity / Solid Class

Create a new Solid Entity resource by searching for "solid".

![](../images/solid-search.png)

Although not necessary, it helps to organize entities by which category they fall into, since they otherwise share the file extension of .tres.

![](../images/solid-save.png)

Here you get several options to customize a solid class.

![](../images/solid-properties.png)

Our goal will be to give the solid class a name and then to print that name.

Notice that unlike the point entity, we don't have a place to add a .tscn file like before. We are only given a place to hold a script.

Now that we've created a new entity class, we can add it to our game's FGD.

![](../images/solid-fgd.png)

Then update the configuration for Trenchbroom using the FGD resource by clicking Export File.

Now we can go back into Trenchbroom and try to create a solid class.

When loading up a map for your game config, first check that you're using your game's FGD and not Qodot's by clicking your game's name:

![](../images/solid-fgd-check.png)

## Qodot's Demo Entities

Although you are given some entity definitions through `Qodot.fgd`, such as
- Light
- Breakable
- Ball
- Detail
- Wall

These example entities have limited functionality. They exist as an example of what can be done, and to port over some functionalities from Quake.

However, there are some entities you have to include in an FGD for your map's worldspawn geometry to build:

- worldspawn_solid
- worldspawn_base
- group_solid

Consider creating your own entities instead.

# Report issues with this page

If you aren't seeing information you need on this page, please [flag an issue on the github repository.](https://github.com/DeerTears/DeerTears.github.io/issues) This is the most complicated page of all and it needs the most attention.
