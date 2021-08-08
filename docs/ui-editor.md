---
layout: default
has_children: false
title: UI editor
nav_order: 

---
# UI Editor

The UI Editor is used for creating your visual novel's interface by defining _layouts_ made up of UI objects.

![](/assets/images/ui-editor.png)

To get started, hit the **+Create layout** button at the left. You will then see a screen similar to the image above.

In the centre of the window is the _canvas_, which is where you will place the layout's objects – buttons, images, text labels, and others. By default, the canvas shows a layout sized to fill the whole (virtual) screen, scaled by 50% to make it easier to work with. You can adjust the size of the layout using the infobox at the right. 

In the infobox, you can see the basic information for the layout: its **Name**, **Size**, and a button marked **Don't save**. This last option is only important for a small number of layouts: if **Don't save** is checked, the layout will be ignored when the player saves the game (all other UI objects on the screen will be recorded in the save file, and restored to their exact places when the player loads the game later). This can be useful when making a save/load screen.

Two **events** (lists of actions) are defined underneath here: the actions in _OnCreate_ are executed when the layout appears on screen, and the actions in _OnRemove_ run when the layout is destroyed (by a **Remove UI Object** action, or the game transitioning to a new board, or the player closing the game). Clicking these buttons will open a popup window to edit the events.

Next are the buttons for creating new UI objects: 

* **Images** can be used as backgrounds for other objects, or to show information. These can have a _border_ defined, which allows for "[nine-slicing](https://en.wikipedia.org/wiki/9-slice_scaling 'Wikipedia page for "9-slice scaling"')" – a technique for cutting an image into rectangular sections so it can be used for creating flexible interface elements. An image can also have a list actions defined, which will execute when the player clicks on the image.
* **Text objects** are floating labels that can be used to display text or numeric information. Text objects support _expression subsitution_, so they can be used to display variables that dynamically update. They can also have their font and font size configured, a colour and highlight (used when the cursor hovers over the text) assigned, an optional shadow, and **OnClick** and **OnHover** events defined.
* **Buttons** are similar to images but have an embedded text string, and can have additional images defined to be displayed in response to the cursor hovering over the button, and the mouse being clicked/held on the button. Buttons have an action list to respond to player clicks.
*  The **Textbox** is one of the most important parts of VNKit, and is used for displaying dialogue and descriptions as part of the normal flow of the story. Only the newest textbox will be "active" at any time. As well as its text parameters and background image, the textbox can also have its **Story mode** defined: this may be _ADV_ ("adventure") or _NVL_ ("novel") mode, which give different presentation styles for your story. By using multiple layouts, you can create a game that mixes both styles.
* **Save slots** are only used when making save/load screens. They have a **Mode** (this can be "Save" or "Load" depending on the type of screen they're being used for), and a **Slot number** which corresponds to the save slot they will be connected to. In-game, this slot number is used together with a hidden "magic variable" called `_saveSlotOffset` (a number) to allow for paginated save/load screens.

Objects can also be reordered by dragging them up and down on the object list, which is useful for controlling which objects are drawn in front of and behind each other.