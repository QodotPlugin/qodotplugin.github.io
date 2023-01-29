---
layout: default
title: FGD Files
nav_order: 7
parent: Entities
---

# FGD Files

FGD (or Forge Game Data) is a data structure used by Quake for storing data about [Entities](index.md).

1. TOC
{:toc}

# Class Reference

See [Class Reference for FGD](../class-reference.md#fgd).

# How Qodot uses FGD files

FGD files are used in two ways by Qodot:

1. Qodot writes FGD files to your Trenchbroom games folder when you create a [Game Definition](/game-definition.md).
2. QodotMap reads through all FGDs in the FGD list, looking for matching entity classnames in the map file. This is how Qodot matches map entities to Godot nodes and scenes.

# Creating a new FGD

This guide will cover how to create a new FGD file.

## Prerequisites

You'll need to provide [Entity Definitions](/creating-entities.md), otherwise there is no point in having an FGD for your [Game Definition](/game-definition.md).

## Steps

1. Right click the FileSystem and click New Resource.
2. Search for "FGDFile" and select it.
3. Name the file, retaining the .tres suffix.

It helps to add "fgd" to the filename your FGD resources for clarity.

# Editing an FGD

Double click the FGD resource in the FileSystem to open up a window in the Inspector. See [FGD Properties](#fgd-properties) for more info on each property.

## Adding entity definitions

1. Increase the size of the Entity Definitions array
2. Drag-and-drop the new entity resource into the array
3. Save your FGD resource

Note
{: .label .label-blue }
All FGDs start with some entities by default, but some are necessary to build map geometry with groups. These are `worldspawn_solid`, `worldspawn_base`, and `group_solid`. These must be present in either your entity definitions, or in the definitions of a base FGD file.

## Saving an FGD

When saving the current scene with <kbd>Ctrl</kbd> + <kbd>S</kbd>, all affected resources are also saved. You can save just the FGD as it's open by clicking the Save icon at the top of the Inspector.

# Adding an FGD to a Game Definition

If you don't have a game definition, read the [Game Definition](/game-definition.md) page to learn how to create one.

1. Open `config_folder.tres` and add your FGD to the FGD list
2. Click Export File in the Inspector
3. Press <kbd>F6</kbd> in Trenchbroom to refresh entity collections
