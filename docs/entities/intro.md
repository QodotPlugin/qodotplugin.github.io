---
layout: default
title: Intro to Entities
nav_order: 1
parent: Entities
---

# Intro to Entities

1. TOC
{:toc}

## Entity Types

There are three main types of entities:
- Point Classes
- Solid Classes
- Base Classes

## Point Classes

A point class is a single position in 3D space. Often referred to as Point Entities.

A point class can either be a single node with a script attached, or an instantiated scene file (.tscn) placed at the point's location.

Point classes work well when placing objects that won't change in size.

## Solid Classes

Solid classes are brushes separated from the static world. Often referred to as Brush Entities.

Solid classes can behave as any kind of CollisionObject. This includes `Area`, `StaticBody`, `RigidBody`, and `KinematicBody`.

By default, they are given a CollisionShape child with a ConcaveShape resource matching their brush vertices.

## Base Classes

Base classes store properties shared by multiple classes. A base class does not function on its own, and it is is never required for any entity definition.

Base classes are helpful at encapsulating repeating properties between multiple entities. You can assure some code safety practices (like duck typing) by ensuring a certain group of entities all share similar properties.
