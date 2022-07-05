---
layout: default
title: Frequently Asked Questions
nav_order: 13
---
# FAQ

1. TOC
{: toc}

# Frequently asked questions

## When I press build on my QodotMap node, why isn't it loading in Godot?

One of the following is probably the case:
- Somewhere in your filepath, there is a space(probably in texture names).
- Somewhere in your filepath you are using UTF-8 characters
- You are using different filetypes for your textures that aren't listed as allowed. Go into the QodotMap node, under the section Textures, make sure the field "Texture File Extensions" includes the file extensions for your texture. Not all texture file formats will work, as this is dependent upon what texture files Godot can use, though tga, png and jpeg should all work.

## Will Qodot be ported to Godot 4.0?

[See this issue](https://github.com/QodotPlugin/qodot-plugin/issues/148). Shifty the creator of Qodot has no official plan for Qodot to be ported to Godot 4.0 currently. That said, there have been forks to extend it to Godot 4.0.

- [godot tbloader](https://github.com/codecat/godot-tbloader)
- [qodot-plugin fork](https://github.com/EIRTeam/qodot-plugin/tree/4.0)
