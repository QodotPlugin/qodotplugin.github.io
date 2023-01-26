---
layout: default
title: Scripting Entities
nav_order: 8
---

# Writing Code for Entities

This guide covers how to add functionality to your entities in GDScript.

Read [Entities](https://qodotplugin.github.io/docs/entities.html) to learn about creating entities, and updating FGD and CFG files to include new entity definitions.

## Adding a script to the entity

Double click an entity definition in the FileSystem, and look for Script Class in the Inspector.

Click on the empty space to add a new script. Any language will work, this guide will assume GDScript.

## Minimum code

Here is the minimum required code for a user script extending a point class:

```
extends Spatial

export(Dictionary) var properties
```

To extend other nodes like `Area` or `StaticBody`:

1. Edit the Node Class property in the Inspector
2. Replace `extends Spatial` with your desired node (`Area`, `StaticBody`, `RigidBody`, `KinematicBody`)

MeshInstance and CollisionShape children are automatically added to all solid classes. They can be disabled by changing Build Visuals to false, and Collision Shape Type to None in the solid class definition.

## Signals

Although you can prepare a .tscn file and instanciate it using the Scene File property, you can connect signals to your entity at runtime.

```
extends Area

export(Dictionary) var properties

func _ready() -> void:
	connect("body_entered", self, "_on_body_entered")

func _on_body_entered(body):
	print(body)
```
