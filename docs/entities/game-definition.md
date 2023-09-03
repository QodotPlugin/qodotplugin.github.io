---
layout: default
title: Game Definition
nav_order: 7
parent: Entities
---

# Game Definition

A game definition (.cfg) is a file that points to the location of [FGDs](fgd.md) and [Textures](../textures.md) used in your project. They are used by editors like [Trenchbroom](https://trenchbroom.github.io/) to separate the entities and textures available to different games.

It is highly recommended you create a game definition for your Godot project to best integrate it with Trenchbroom and other editors.

1. TOC
{:toc}

## Making a Game Definition Folder

On a new installation of Qodot, `qodot_trenchbroom_config.tres` is provided in the folder `res://addons/qodot/game_definitions`.

To generate a new game definition, double-click `qodot_trenchbroom_config.tres` to open it in the Inspector.

Read [Config Folder Properties](#config-folder-properties) to see the options available when creating a game definition.

## Setting Trenchbroom Game Path

Once you setup and export your game definition folder, Trenchbroom will need a path to your project directory to read textures.

To set your project directory for your game definition:
1. Launch Trenchbroom
2. Click "New Map..."
3. Click "Open preferences..."
4. Find your game in the preferences list
5. Click the "..." next to "Game Path"
6. Select your Godot project folder from your file system
7. Click "Apply"

You can now create a new map with your Godot project as the game type.

## Config Folder Properties

Double-clicking `qodot_trenchbroom_config_folder.tres` lets you view these properties in the Inspector.

This tool is best for first-time setup with trenchbroom. It is also useful when updating properties in the game definition.

**Export File**

A button that creates the necessary folder and files for Trenchbroom to read your game definition.

Exporting also updates any existing definition with the same name. You can press Export File multiple times to update your definition.

Updating like this is necessary to see changes like an updated FGD, a new icon, or new brush/face tags.

**Trenchbroom Games Folder**

A filepath that should point to your computer's Trenchbroom installation. This location depends on your OS.

| Platform | Location |
| -------- | ---------|
| Windows | Trenchbroom\games\ |
| macOS | TrenchBroom.app/Contents/Resources |
| Linux | /share/trenchbroom |

For Windows and Linux, this folder should be prefixed by where you unzipped/installed Trenchbroom to.

If you can't write to your installation folder, you can also use the user data folder for your OS as shown belopw:

| Platform | Location |
| -------- | ---------|
| Windows | %AppData%\Roaming\TrenchBroom |
| macOS | ~/Library/Application Support/TrenchBroom |
| Linux | ~/.TrenchBroom |

**Game Name**

The name associated with new map files for your game, and the name that appears in the Trenchbroom games list. Defaults to "Qodot".

Note
{: .label .label-blue }
If you are using Qodot between multiple projects, make sure this name is unique to avoid overwriting definitions from other projects.

**Icon**

The image that appears in Trenchbroom's game selection list.

Note
{: .label .label-blue }
Your project needs an `icon.png` file to generate a game definition. If one is missing, you need to re-add `res://icon.png` to your project and restart Godot.

**Game Config File**

See [Config File Properties](#config-file-properties) for more information. Editing this file is not necessary unless you need to include new brush tags or face tags.

**FGD Files**

A list of all [FGDs](fgd.md) to include with this game definition.

## Config File Properties

Double-clicking `qodot_trenchbroom_config_file.tres` lets you view these properties in the Inspector.

This resource is best used to update specific details of the CFG, not for first-time setup.

**Export File**

Update the .cfg file listed in Target File.

**Target File**

The path to the .cfg file representing your project.

*Windows Example:* `C:\Users\<username>\Documents\Trenchbroom\games\MyGame.cfg`

**Game Name**

The name that becomes associated with the map file, and the name that appears in the Trenchbroom games list. Defaults to "Qodot".

**Brush Tags**

An array holding brush tag resources, which lets brushes take on unique rendering properties in Trenchbroom.

By default, this is loaded with trigger_tag.tres and detail_tag.tres. Any brush entities with the name `trigger_` will be transparent.

**Face Tags**

An array holding face tag resources, which lets faces take on unique rendering properties in Trenchbroom.

By default, this is loaded with clip_tag.tres and skip_tag.tres. Any faces with the texture `skip` or `clip` will be transparent.

**Face Attrib Surface Flags**

Only compatible with Quake 3, not well supported by Qodot.

**Face Attrib Content Flags**

Only compatible with Quake 3, not well supported by Qodot.

**FGD Filenames**

An array that holds FGD resources. This is another way to update the FGD list for your game definition.
