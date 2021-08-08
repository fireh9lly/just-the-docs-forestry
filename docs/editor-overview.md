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
> The changes you make in the Story Editor are **auto-saved** in `Assets/Resources/VNKit` as `Story.json` (and others). Saving your overall Unity project doesn't do anything to save your Story Editor content, so **don't worry about saving the Unity project regularly** unless you are also making changes within the main Unity editor.
>
> Auto-save is triggered when you finish making a change in the editor and then click 'away' from that change. _(ALPHA ALERT – In some rare cases VNKit might not autosave correctly, possibly when you close the window or change tabs; this should never lose more than one small change, but if you do find this happening please report it as a bug.)_
>
> 👉 Please remember to back up your project files regularly! 👈
>
> ### Press X to JSON
>
> Your Story Editor will **automatically load** your project from `Story.json` when you open it from the Unity Inspector window. Doing this also refreshes the Story Editor. If you have made changes to your VNKit project files externally (such as updating the `studio.axile.vnkit` package folder, or editing `Story.json` in a text editor), you will need to close down and reopen the Story Editor to get VNKit to notice. _(ALPHA ALERT_ – _closing and reopening the editor should be your first instinct if you find a display bug or similar problem. Tell us about what you found, though!)_

![](/assets/images/editor-overview.png)

The first thing you will see is the Boards screen. This screen is where you will write, arrange and link the text, images and gameplay of your visual novel.

#### 1. Board list

Allows you to create and manage _Boards_. You can think of Boards as a single surface on which your Nodes are laid out - like a drawing board of index cards, or a whiteboard with a flowchart diagram. You can add a new Board to represent a new part of the story, a new location for the player to visit, a storylet to shuffle into the game, or for any reason that makes sense to you.

The drop-down menu allows you to filter Boards based on Tags.

Clicking `+ Add board` will create a new board.

The Start Board is the board from which your game will begin running. The Start Board's title is displayed with an asterisk `*` next to it.

The board with its title in **_bold italic_** is the board you are currently editing.

#### 2. Reset View

You can view other parts of the board by dragging around on the backing, and by using the mouse wheel to zoom. The board goes on forever, so if you have panned too far away from your story, clicking here will return you to the central coordinate.

#### 3. Board manager

From this menu, you can name the board, change its behaviour and tags, edit and delete it.

The Storylet box allows the board to be summoned with the `Jump to storylet` action in the Action editor. Once checked, you will also be able to set Conditions for the board. When you use the `Jump to storylet` action, it will take you to a random storylet which fits the story's conditions.

Tags let you label boards, and you can use them as a filter in the dropdown menu in the Board list. If a board is a Storylet, you can also jump to it based on its tags. See Storylets for more information. (_not done yet - Ed_)