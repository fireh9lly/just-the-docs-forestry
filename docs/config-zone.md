---
layout: default
has_children: false
title: Config Zone
nav_order: 
parent: ''
has_toc: false

---
# Config Zone

The Config Zone is the area of the editor where most of your game's settings are managed. (**Alpha alert** – this section will probably change a lot.)

Configurable here are:

* **Default save file image:** This is the image that will be shown on _Save slots_ when a save file is present in the slot. (**Alpha alert –** In future save slots will be able to optionally show screenshots for easier recognition of save files.)
* **Scrollbar handle:** This is the image used for the scrollbar handle, displayed at the right-hand side when a node's text is too long to fit inside the textbox.
* **Default dialogue blip:** This is the "blip" sound played when text is being shown using the _Typing_ transition. This sound can be overridden for individual characters using the [Sprite editor](/docs/sprite-editor.html).
* **Default font:** This is the default font used for textboxes and text objects. This must be a TextMesh Pro font asset: see the [TextMesh Pro documentation on font asset creation](http://digitalnativestudios.com/textmeshpro/docs/font/) for more details.
* **Font size:** The default font size for textboxes and text objects.
* **Textbox rect:** This is the position and size for the default textbox. Other textboxes with different geometry can be configured in the [UI editor](/docs/ui-editor.html).
* **Textbox background:** This is the background image for the default textbox.
* **Textbox border:** These are the border sizes for the default textbox, so its background image can be used as a [nine-slice](https://en.wikipedia.org/wiki/9-slice_scaling).
* **Rest time:** This is the time (in seconds) the textbox should pause when encountering a rest symbol (`#`) in the text. (**Alpha alert** **–** currently this only works with the _Typing_ transition mode).
* **OnStart event:** This is a sequence of actions that runs when the game starts.
* **OnStoryFrameClose event:** This event runs whenever the main StoryFrame is closed.
* **OnQuit event:** This event runs when the game quits, if a StoryFrame is onscreen at the time. The **OnStoryFrameClose** event will also run beforehand.