---
layout: default
has_children: false
title: Sprite editor
nav_order: 
published: false

---
# Sprite Editor

The Sprite Editor allows you to configure the characters and visible objects that will appear in your game. Once you've created some sprites in the Sprite Editor, you can add them to your scenes using the **AddSprite** action.

![](/assets/images/new-sprite.png)

The left-hand panel shows a list of sprites already configured in your project. Clicking on one of these will open the sprite in the editor.

The centre panel shows the currently-selected _layer_ of the sprite. For simple sprites you may only want to use one layer, but more complex characters with varying facial expressions, poses, and outfits, may need multiple independent layers to be configured. At the top of this section is the layer name, and an **offset** that can be used to control where the layer's images appear on the sprite; for example, if your character sometimes wears a hat as part of their outfit, your "Hat" layer might have an offset of **X: 0, Y: 450**. Layer offsets are given in pixels, where **0, 0** is the centre of the sprite, **X** goes from left (negative) to right (positive), and **Y** goes from bottom (negative) to top (positive).

Below the offset you can see a list of the **states** (animations) belonging to the layer. You can select a state by clicking on it, or click the "+ Add state" button to add a new state. Right-clicking a state will allow you to rename or delete it.

When a sprite is selected, the right panel will show the basic information belonging to the sprite:

* The sprite's **Name** can be changed here.
* A default **Scale** can be defined; this can be useful if your images are bigger than the size of the (virutal) game window, and need to be shrunk down. 
* An audio **Blip** can be set here, which will play when the game is displaying a line of this character's dialogue (if the _text transition mode_ is set to "Typing"; see the **Config Zone** section). 
* A **Notes** section is provided for general annotations, reminders and developer commentary relating to the character; this will not be visible in-game.
* Underneath the Notes section is a list of **layers**. Layers can be added, removed and reordered here. Layers appearing higher in this list will be displayed on top of lower layers when the game is running. It's not possible to reorder layers at runtime. 
* The **Delete sprite** button will show a confirmation window before deleting the sprite from the game data.
* The **Appearances** section shows a list of boards on which this sprite appears, which can be useful for debugging and analysis.