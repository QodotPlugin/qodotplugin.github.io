---
layout: default
title: Class Reference
nav_order: 20
---

# Class Reference

This class reference is incomplete. You can help complete it by [making an issue on GitHub](https://github.com/QodotPlugin/qodotplugin.github.io/issues/new) or [contributing to the class reference directly](https://github.com/QodotPlugin/qodotplugin.github.io).

1. TOC
{:toc}

# Trenchbroom Settings

These classes enable various Trenchbroom features for use in your game.

## TrenchbroomTag

**Tag Name**

**Tag Attributes**

An array of strings determining the in-editor appearance of brushes/faces that match this tag.

Current available attributes:
- `_transparent` makes the face semi-transparent

**Tag Match Type**

Detemines how the tag is matched.

Type | Description
--|--
`TEXTURE` | Tag applies to any face with a texture matching the texture name.
`CONTENT_FLAG` | Tag applies to any brush with a content flag matching the tag pattern.
`SURFACE_FLAG` | Tag applies to any face with a surface flag matching the tag pattern.
`SURFACE_PARAM` | Tag applies to any face with a special surface param. [See Trenchbroom Manual for more info.](https://trenchbroom.github.io/manual/latest/#special_brush_face_types)
`CLASSNAME` | Tag applies to any brush entity with a class name matching the tag pattern.

**Tag Pattern**

A string that filters the specific flag, param, or classname to use. `*` can be used as a wildcard to include multiple options.

Example: `trigger_*` for the Classname match type will apply to all brush entities with the `trigger_` prefix.

**Texture Name**

A string that filters the specific texture to apply this tag with. Only applies for the Texture tag match type.

## QodotTrenchbroomConfigFolder

**Export File**

**Trenchbroom Games Folder**

**Game Name**

**Icon**

**Fgd Files**

**Brush Tags**

**Face Tags**

**Face Attrib Surface Flag**

Creates a map-wide boolean that can be applied to any face in Trenchbroom's face editor. Surface flags mark a face with a specific property, usually for rendering purposes.

Quake 2 uses these for visual effects like "light", "warp", "moving", "nodraw", "sky", and more. Read more about Face Attributes in the [Trenchbroom Manual](https://trenchbroom.github.io/manual/latest/#face_attribute_editor).

**Face Attrib Content Flag**

Creates a map-wide boolean that can be applied to any face in the face editor. Content flags mark a brush with a specific property, usually for gameplay.

Quake 2 uses these for gameplay elements like "playerclip", "monsterclip", "water", "lava", "slime", "mist", and more. Read more about Face Attributes in the [Trenchbroom Manual](https://trenchbroom.github.io/manual/latest/#face_attribute_editor).

![](https://trenchbroom.github.io/manual/latest/images/FaceAttribsEditor.png)

# Trenchbroom and Qodot Shared

These entities are read between both Trenchbroom and Qodot to represent the same core data.

## QodotFGDFile

**Fgd Name**

Reserves a namespace for your entity definitions in Trenchbroom under this name.

Note
{: .label .label-blue }
Trenchbroom will throw an error if you use two FGDs with the same Fgd Name. If you have Qodot.fgd as a base, make sure to change your own Fgd Name to something else.

**Entity Definitions**

An array containing Entity Definition resources.

Note
{: .label .label-blue }
Trenchbroom will fail to load any entity definitions missing a classname.

## QodotFGDClass

**Classname** - The name for this class in Trenchbroom.

**Description** - A short description that displays in Trenchbroom when this entity is selected.

**Qodot Internal** - Hides the entity in Trenchbroom's entity browser.

Qodot can still refer to this entity for building other entities (like base entities). Base Entities are already hidden in Trenchbroom by default, for most situations you can leave this off.

**Base Classes** - An array of template entities to inherit properties from.

This determines the parent entities for this class, where this entity gets all the class properties, meta properties, and property descriptions from its parents.

**Class Properties** - A dictionary of properties.

Once exported to the Trenchbroom game config, the dictionary values are written by editing entities in Trenchbroom, and read by accessing `properties` on a QodotEntity once the map is built.

You can also set default values for your properties by repeating this process in Meta Properties, matching the key names and value datatypes from this dictionary.

**Class Property Descriptions** - A dictionary of descriptions for each property, visible in Trenchbroom.

Ensure the description's key matches the property's key. Description values can only be strings.

**Meta Properties** - Editor-specific properties, such as the default color and size used to represent this class.

Add an entry with a matching key to an existing property, set the value to the same data type, and whatever value is present will become the default. Only one meta property is read per class property.

**Node Class** - The type of Godot node to spawn at this location.

### QodotFGDPointClass

**Scene File** - The .tscn Godot scene that spawns in place of QodotEntity. The easiest way to spawn a specific node at a specific point.

Scene File takes priority over every other option here, especially if there's already a script attached to the .tscn file.

**Script Class** - The script to attach to your entity's root node.

This is ideal for spawning nodes without a .tscn file. If you want to access this entities' Class Properties, add a script here that `extends QodotMap` and accesses `properties["key_name"]`.

You can extend other Spatial-derived node types too, and add necessary children (CollisionShape, MeshInstance) through code, but you lose out on the ablity to access `properties`. You can fix this by always choosing to extend `QodotEntity` and adding more complex nodes like Area and RigidBody as children through code.

Make sure to update Node Class so it matches the the script's `extends`!

**Node Class** - The type of node to spawn at this location. This property should match the `extends` of your Script Class. You can ignore this property if you're using a Scene File.

With those properties covered, there's a few tricks you can use to get more specific results.

If you want to create an RigidBody node without a .tscn using a point entity, extending `RigidBody` in thes script prevents you from accessing the class property values set in Trenchbroom. However, extending `QodotEntity` prevents you from accessing the functions and signals of a RigidBody.

You can get around this by extending `QodotEntity` and using `var body = RigidBody.new()` and `add_child(body)` to add more complex nodes as children, while still having access to the `properties` dictionary. This can be repeated for other children like MeshInstance and CollisionShape.

### QodotFGDSolidClass

Solid classes can have multiple brushes (select multiple brushes when making the entity) so these properties apply to the solid class as a single object, not to each brush individually.

**Spawn Type** - Changes how the QodotMap arranges these brushes in its node hierarchy.

There are 4 settings:
- Worldspawn
- Merge Worldspawn
- Entity
- Group

**Build Visuals** - Makes the solid class visible when checked.

You may want to disable this for invisible triggers and other gameplay-related solid classes.

**Node Class** - Sets the node type of the solid class root.

If you're adding a Script Class, this value should match the `extends` of the script.

Setting this to RigidBody and setting Spawn Type to Entity changes these brushes from static geometry into physics objects.

**Collision Shape Type** - Changes how collision is built.

- None
- Convex
- Concave

Convex creations a CollisionShape for each brush, depending on the Spawn Type. Entity creates an outer hull, Group creates individual shapes for each brush. Convex is a good bet for most situations.

Concave allows for concave brush geometry, or if you chose Entity and want a single concave CollisionShape to make up your solid class. 🚧

**Script Class** - The script applied to the entity's root.

Although `QodotFGDSolidClass` is a class you can extend from, this is meant as a Qodot internal to build solid classes. This does not extend QodotEntity, and will not give you access to `properties`.

# Class Property Data Types

You can define properties for entities in the Class Properties dictionary. The "key" for each dictionary entry should be a String. The "value" can only be one of these 8 data types:

- Bool
- Int
- Float
- String
- Vector3
	- Stored as a string in the form X Y Z
- Color
	- Stored as a string in the form R G B
- Dictionary
	- Used for defining a set of choice key strings and their associated values
	- Will display a dropdown in compatible editors
	- Available Dictionary value types haven't been thoroughly tested
- Array
	- Used for bitmask flag properties
	- Will display a grid of checkboxes in Trenchbroom
	- Used in Quake to indicate which entities spawn on different difficulties - easy, medium, hard
	- Each entry in the array should be an array, with three elements: `[name: String, value: bool/float/int/String, default: same type as value]`

## Note on Arrays

When you add an Array as a class property, it must contain other Arrays, with each Array creating one flag. These flag Arrays must have 3 items: Name, Value, and Default value.

Name must be a String.

Value is traditionally a bool, but it can also be a float, int, or String. Qodot parses all these data types as Strings in the end, which will change how you will be [Accessing Class Properties in Code](#accessing-class-properties-in-code).

The default value can be the previous data type, or even `null`. It is not read by Qodot, just the regular Value.
