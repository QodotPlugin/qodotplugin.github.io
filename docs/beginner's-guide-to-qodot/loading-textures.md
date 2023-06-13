---
layout: default
title: Loading Textures in Trenchbroom
nav_order: 5
parent: Beginner's Guide to Qodot 
---

# Loading Textures in Trenchbroom

This guide covers managing textures between Godot and Trenchbroom, to allow brushes to build with textures.

Read the Trenchbroom manual to learn more about applying textures to brushes in Trenchbroom.
- [Applying textures in Trenchbroom](https://trenchbroom.github.io/manual/latest/#working_with_textures)
- [Managing texture collections in Trenchbroom](https://trenchbroom.github.io/manual/latest/#texture_management)

1. TOC
{:toc}

# Using Generic

This assumes you want to setup textures as fast as possible for use in Qodot by overwriting the Generic game definition in Trenchbroom.

You'll need a `res://textures` folder to hold map textures. These textures will be read from both Godot and Trenchbroom.

1. Open Trenchbroom
2. Click "New Map"
3. Go to "Preferences"
4. Click "Generic"
5. Set Game Path to your Godot project directory
6. In your Trenchbroom map, enable the texture collection `/textures`
7. In Godot, set the Textures Dir of your QodotMap node to your /textures folder
8. Click Build Map to see the results

Note
{: .label .label-blue }
Both the file path and texture name cannot contain UTF-8 characters or spaces.

# Using a Game Definition

This is effective if you have multiple projects using Qodot, or if you need to use any entity definitions.

1. Create a [Game Definition](../entities/game-definition.html)
2. Open Trenchbroom
3. Click "New Map"
4. Go to "Preferences"
5. Click your game's name
6. Set Game Path to your Godot project directory
7. In your Trenchbroom map, enable the texture collection `/textures`
8. In Godot, set the Textures Dir of your QodotMap node to your /textures folder
9. Click Build Map to see the results

If you need more guidance on these steps, consider reading the page on [Game Definitions](../entities/game-definition.html) to create a personalized Trenchbroom setup for your project.

# The Next Step

Congratulations! You've completed the Beginner's Guide to Qodot. From having completed this guide, you should be able to build maps in Qodot and apply textures from Trenchbroom to Godot geometry.

Here are some common next steps for developers:

| Next step | Link |
| :------------------------------------------------------------------ | :------------------------- |
| Apply materials and shaders to brushes: | [Textures](../materials.md) |
| Place Godot scenes using Trenchbroom: | [Entities](../entities) |
| Prepare a project for scaling up: | [Best Practices](../best-practices.md) |
