---
layout: default
title: Entities
nav_order: 7
has_children: true
---

# Entities

Entities (also known as Classes) tie Godot functionality to 3D positions and marked brushes in your map file.

1. TOC
{:toc}

# Intro to Entities

Entites significantly extend Qodot's abilities as a level editing tool. They allow the placement of Godot scenes and complex node structures within level geometry.

# Prerequisites

Before continuing, you should know how to place Point Entities and Brush Entities in your map editor.

Read the [Trenchbroom manual - Creating Entities](https://trenchbroom.github.io/manual/latest/#creating_entities) for more information.

If you don't have any entities to place in your current game, make a New Map for Quake or any other preset game to follow along with the manual.

# Entity Types

In Qodot, there are three types of entities that users can create:
- Point Class
- Solid Class
- Base Class

## Point Class

A point class is an object with a position in 3D space. Referred to as a Point Entity in Trenchbroom.

In Qodot, a point class can be any single node, or an instance of a scene file (.tscn).

Similar to their functionality in Quake and Source games, point classes can represent common game objects such as spawnpoints, hazards, lights, and collectable items.

## Solid Class

A solid class is a brush separated from the static world geometry. Often referred to as a Brush Entity.

By default, they are built as with a MeshInstance child and CollisionShape child. Unlike the static world geometry, they are kept as a different node than WorldSpawn, and the node type can be changed.

Solid classes can behave as any kind of CollisionObject. This includes `Area`, `StaticBody`, `RigidBody`, and `KinematicBody`.

## Base Class

A base class stores properties shared by multiple classes. They are another layer of abstraction, and are not required for an entity to function.

They help encapsulate repeating properties between multiple entities. You can practice code safety with base classes; They ensure all entities sharing the same base class inherit the same properties.

# Entity definitions and Godot resources

The three entity types can be defined and saved as Godot .tres resource files. This is how user data is stored in Qodot.

A resource file that stores any of the three classes is called an *Entity Definition*. Each .tres file contains data describing an entity.

The following resource templates are installed with Qodot to let you create entity definitions upon creating a New Resource. These resource templates are:
- QodotFGDPointClass
- QodotFGDSolidClass
- QodotFGDBaseClass

# The next step

Read [Creating Entities](/creating-entities.md) to learn about making your own entity definitions, including point entities.

See [Scripting Entities](/scripting-entities.md) to learn how to create a solid class that responds to collisions.
