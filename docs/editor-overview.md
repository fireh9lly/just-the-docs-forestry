---
layout: default
has_children: false
title: Editor overview
nav_order: 3

---
# Editor overview 

Once you click "Open Story Editor", you will be in VNKit's Story Editor. The bulk of work on your game will take place in this window - you will not have to use Unity's menus much.

> #### Before we go on -
>
> ### An important note about saving your story
>
> The changes you make in the Story Editor are auto-saved in {VNKit path goes here}, as `Story.json` (and others). These changes aren't linked to when you save your overall Unity project. 
>
> Auto-save is triggered when you finish editing some text in the editor and click elsewhere in the editor. VNKit can't see clicks that close the window, so if you are losing work you just did, make sure to click on another text box before you close the Editor.

> #### Press X to JSON
>
> Your Story Editor will automatically load your project from `Story.json` when you open it from the Unity Inspector window. Doing this also refreshes the Story Editor. If you have made changes to your VNKit project files externally (such as updating the `studio.axile.vnkit` package folder, or editing `Story.json` in a text editor), you will need to close down and reopen the Story Editor to get VNKit to notice. _(ALPHA ALERT - closing and reopening the editor should be your first instinct if you find a display bug or similar problem. Tell us about what you found, though!)_