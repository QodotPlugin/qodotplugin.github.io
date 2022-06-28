---
layout: default
title: Frequently Asked Questions
nav_order: 13
---
# FAQ

## When I press build on my QodotMap node, why isn't it loading in Godot?

One of the following is probably the case:
- Somewhere in your filepath, there is a space(probably in texture names).
- Somewhere in your filepath you are using UTF-8 characters
- You are using different filetypes for your textures that aren't listed as allowed. Go into the QodotMap node, under the section Textures, make sure the field "Texture File Extensions" includes the file extensions for your texture. Not all texture file formats will work, as this is dependent upon what texture files Godot can use, though tga, png and jpeg should all work.

## Will Qodot be ported to Godot 4.0?

[See this issue](https://github.com/QodotPlugin/qodot-plugin/issues/148). Additionally, see this comment the creator of Qodot-plugin wrote in Discord:

> ultimately, i'm tired of the pick up engine -> great honeymoon -> oh no it's awful -> try your best -> fuck it go elsewhere cycle; building games should be fun, but these half-assed premade engines suck all of the enjoyment out of it with their endless issues. recently i've been building a rendering/physics testbed from scratch in rust to develop shambler stuff, and that's given me the "hell yes this complex thing i built just works" satisfaction that's been missing from the experience until now.

> i've avoided talking about this because i don't want people to read it as "qodot is dead oh no", but it needs to be said eventually - i've gathered enough knowledge in the course of reinventing wheels that i can't unsee the various ways godot doesn't work for me, so chances are that i'll end up developing this rust testbed into its own proper engine and using that for my own projects.

> though to be very clear: i'm not going anywhere, and am going to keep hacking on quake maps as a modern level format. i might not end up being the person to integrate them with godot 4 when it eventually materializes, but i will be the person to build the library that makes such a thing possible.

As such there's no official plan for Qodot to be ported to Godot 4.0 currently. That said, there have been forks to extend it to Godot 4.0.

- [godot tbloader](https://github.com/codecat/godot-tbloader)
- [qodot-plugin fork](https://github.com/EIRTeam/qodot-plugin/tree/4.0)
