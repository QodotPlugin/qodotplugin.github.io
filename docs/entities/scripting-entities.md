---
layout: default
title: Scripting Entities
nav_order: 8
---

# Writing Code for Entities

This guide covers how to add functionality to your entities in GDScript.

Read [Entities](https://qodotplugin.github.io/docs/entities.html) to learn about creating entities, and updating FGD and CFG files to include new entity definitions.

1. TOC
{:toc}

## Syntax Disclaimer

This guide currently only covers Godot 3.X GDScript syntax. In the future Godot 4.X GDScript syntax will be available. [You can contribute your own translations of these examples on GitHub](https://github.com/QodotPlugin/qodotplugin.github.io/issues/new).

## Adding a script to an entity

Double click an entity definition in the FileSystem, and look for Script Class in the Inspector.

Click on new script and pick a language.

## Minimum code

Here is the required code for a user script extending a point or brush class:

```
extends Spatial

export(Dictionary) var properties
```

To extend other nodes like `Area` or `AudioStreamPlayer`:

1. Edit the entity definition's Node Class in the Inspector
2. Replace `extends Spatial` with the same node name

## Brush classes

For brush classes, any node that inherits `CollisionObject` is valid, as long as it can accept a child CollisionShape. Some common nodes include:

- `Area`
- `StaticBody`
- `RigidBody`
- `KinematicBody`

MeshInstance and CollisionShape children are automatically added to all brush entities. They can be disabled by changing Build Visuals to false, and Collision Shape Type to None in the solid class definition.

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

Remember to update your entity definition's Node Class with a name that matches your `extends`.

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