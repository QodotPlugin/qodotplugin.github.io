---
layout: default
title: FGD Files
nav_order: 7
parent: Entities
---

# FGD Files

FGD (or Forge Game Data) is a data structure originated in Quake for storing entities.

A game definition needs an FGD to place point entities, convert brushes to brush entities, and inherit components from base entities.

It is recommended you create a new FGD for your Godot project to go with your game definition.

## Creating a new FGD

1. Right click the FileSystem and click New Resource.
2. Search for "FGDFile" and select it.
3. Name the file, retaining the .tres suffix.

It helps to add "fgd" to the name your FGD resources for clarity.

## Editing the FGD

Double click the FGD resource in the FileSystem to open up a window in the Inspector.

## Adding new entity definitions

1. Increase the size of the Entity Definitions array
2. Drag-and-drop the new entity resource into the array
3. Save your FGD resource

## Saving an FGD

When saving the current scene with <kbd>Ctrl</kbd> + <kbd>S</kbd>, all affected resources are also saved. You can save just the FGD as it's open by clicking the Save icon at the top of the Inspector.

## Updating a Game Definition with a modified FGD

1. Open `config_folder.tres` and add your FGD to the FGD list
2. Click Export File in the Inspector
3. Press <kbd>F6</kbd> in Trenchbroom to refresh entity collections
