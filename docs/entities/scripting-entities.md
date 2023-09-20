---
layout: default
title: Scripting Entities
nav_order: 8
parent: Entities
---

# Scripting Entities

This guide covers how to add functionality to your entities in GDScript for Godot 3.X.


1. TOC
{:toc}

# Prerequisites

You should know how to create entity definitions. Read [Creating Entities](https://qodotplugin.github.io/docs/entities/creating-entities.html) for more information.

# Syntax Disclaimer

This guide currently only covers Godot 3.X GDScript syntax. In the future Godot 4.X GDScript syntax will be available. [You can contribute your own translations of these examples on GitHub](https://github.com/QodotPlugin/qodotplugin.github.io/issues/new).

# Adding a script to an entity

To add a script to an entity, double click your entity definition in the FileSystem to open it in the Inspector.

Go to the Script Class property. You can either click on New Script and pick a language, or drag a script file (.gd, .cs, .gdnative) to the resource slot.

New script saves a script subresource to your entity definition.

## Point classes

Here is the required code for a user script extending a default point class:

```
extends Spatial

export(Dictionary) var properties
```

To extend other nodes like `Light` or `AudioStreamPlayer`:

1. Edit the entity definition's Node Class in the Inspector
2. Replace `extends Spatial` with the same node name

## Brush classes

Here is the required code for a user script extending a default brush class:

```
extends StaticBody

export(Dictionary) var properties
```

To extend other nodes like `Area` or `RigidBody`:

1. Edit the entity definition's Node Class in the Inspector
2. Replace `extends StaticBody` with the same node name

A brush class can extend any node that inherits `CollisionObject`. These nodes include:

- `Area`
- `StaticBody`
- `RigidBody`
- `KinematicBody`
- `VehicleBody`
- `DynamicBone`

Other node types will make its child CollisionShape redundant.

The rest of this guide applies to both entity types.

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

Note
{:label :label-blue}
If your signals aren't sending, check that you've updated your entity definition's Node Class with a name that matches your `extends`, and that you've rebuilt your map. Make sure that any contact reporting properties are set as needed at runtime, using the `_ready()` function.

## Groups

If you need to access your entity at runtime, but don't know how to reliably find it in the SceneTree, you can use groups to access that node regardless of hierarchy.

```
func _ready():
	add_to_group("Enemies")
```

This creates an array which can be accessed or iterated through to get all nodes in the group.

```
var enemies: Array = get_tree().get_nodes_in_group("Enemies")
for enemy in enemies:
	enemy.respawn()
```

## Comparing Class Properties

If you've placed multiple entities, but you want to assign one of them with unique data, you can add a Class Property to your entity definition.

Then, after updating your [FGD](fgd.md) for both Qodot and Trenchbroom, you can set a value for the new class property in Trenchbroom.

This value will appear in the `properties` Dictionary on build.

To compare values between entities of the same type, use the same group method as before, and check their properties as you iterate through the grouped nodes.

```
for player in get_tree().get_nodes_in_group("Players"):
	if "role" in player.properties:
		if player.role == "mage":
			print("player is a mage")
			break
```
