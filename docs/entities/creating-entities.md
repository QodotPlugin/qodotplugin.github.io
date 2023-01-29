---
layout: default
title: Creating Entities
nav_order: 2
parent: Entities
---

# Creating Entity Resources

In Qodot, you define new types of entities by creating a new .tres resource file. Qodot provides 3 resource presets for this:

- QodotFGDPointClass
- QodotFGDSolidClass
- QodotFGDBaseClass

Click the "New Resource" icon in the Inspector:

![](../images/res-inspector.png)

Or right-click the FileSystem and click "Create New Resource":

![](../images/res-filesystem.png)

Either will take you to the resource search screen. Here you can type in the following quick terms to narrow down the type of resource you want to create:

- pointclass
- solidclass
- baseclass

Select the type of class you want to create, hit enter, and name your new file.

# Editing Entity Resources

Find your new resource .tres file in the FileSystem dock and double click it. The Inspector will pop up showing the resource's properties. This is where you edit your entity definition and define its behaviour.

# Class Reference

See [Class Refernece](../class-reference.md) to learn what each property of an entity definition resource does.

# Seeing entity definitions in Trenchbroom

To see the result of your entity definition, it needs to be in an [FGD](/fgd.md), then that FGD must be included when creating/updating a [Game Definition](/game-definition.md) for Trenchbroom. Once these are all satisifed, you should be able to view your entity definition in Trenchbroom.

Keep in mind that point entities are available in the entity browser when the FGD is enabled, but brush entities are only shown when right-clicking a brush to convert it to a brush entity.
