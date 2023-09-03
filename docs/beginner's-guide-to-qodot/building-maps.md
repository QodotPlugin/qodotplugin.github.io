---
layout: default
title: Building Maps
nav_order: 4
parent: Beginner's Guide to Qodot 
---

{:toc}

If you don't have any map files or textures, and want to fully setup your Godot project with your Trenchboom editor, read the page on [Trenchbroom Setup](qodotplugin.github.io/docs/beginner's-guide-to-qodot/trenchbroom-setup.html) first. Otherwise, continue reading.

# Building Maps

## Building Basic Geometry

- With the plugin [installed and enabled](https://qodotplugin.github.io/docs/beginner's-guide-to-qodot/), Add a .map file to your project. It will import as a visible resource in your FileSystem dock.

![](../../images/install-map.png)

- Add a QodotMap node from the *Add Node* menu, or press <kbd>Ctrl</kbd> + <kbd>A</kbd> and type "QodotMap".

- Select QodotMap, then go to the Inspector. Click the folder icon in the *Map File* property and choose your map file.

![](../../images/install-qodotmap.png)

- Hit Full Build in the toolbar. (If Full Build isn't visible, check you're running the C# build and press <kbd>Alt</kbd> + <kbd>B</kbd>.

![](../../images/install-fullbuild.png)

Your map geometry is now in Godot!

![](../../images/install-final.png)

### Build Troubleshooting

If your map isn't building, try the following solutions:

- Check the console for errors and post a screenshot of your editor window to the community.
- Check that your map or textures doesn't use spaces or UTF-8 exclusive characters.

# Loading Textures

This assumes your map already has textures. If you're starting from scratch, and want to unite your Godot project with your Trenchboom editor, read the page on [Trenchbroom Setup](qodotplugin.github.io/docs/beginner's-guide-to-qodot/trenchbroom-setup.html).

## Using Loose Textures

If your map already has textures, make sure your Godot project has access to the same folder names used in the map. You can copy the map's loose textures into a folder, such as `res://textures`.

Then, set  *Base Textures Dir* to the folder with your map's loose textures.

![image](https://github.com/QodotPlugin/qodotplugin.github.io/assets/47726614/41f6c99a-07a9-4fa6-a89f-ac06ce0b4b42)

## Using WADs

Add a .WAD file to your project. As long as Qodot enabled, it will be imported as a Godot resource. You can check its contents by double clicking the resource in FileSystem to reveal a Dictionary of textures.

Select your QodotMap, then scroll down to *Texture WADS* and add an element to the Array.

![image](https://github.com/QodotPlugin/qodotplugin.github.io/assets/47726614/8e6f4408-9c22-4636-b861-e775b76daa4d)

Drag and drop the .WAD file onto the Array, or click *Load* and pick the .WAD file from the file browser.
