---
layout: default
has_children: false
title: The Action Editor - Action List
nav_order: 98

---
# The Action Editor

When you click the **Add action** button on a Node, a list of available actions will open. You can collapse different categories within the Action list using the arrows to the top right of each category. The Action list will remember which categories you have collapsed while you are working on your current project.

The following is a quick reference for available actions. For more detailed information, see **The Action Editor - Overview.** _(Not done yet! -Ed.)_

### Variables and events

_Category for actions that control the game flow._

#### Set variable

Sets a variable, letting your game store information about itself that can be checked later. An essential building block for interactive games.

The variable _name_ can be one of three things:

* The name of a global variable. This must be a single word (no spaces). Capital letters and underscores are allowed as part of the name. Numbers may be used as long as the first character of the name is not a number.
* An _array accessor_. This should be the name of an array variable followed by a number in square brackets, like this:  
  `arrayVariable[5]`  
  If the variable does not contain an array, the system will raise an error. **Remember** that the _first_ element of the array is numbered _zero_.
* An _object accessor_. This should be the name of an object variable followed by a dot, and then the name of one of the object's attributes, like this:  
  `objectVariable.attribute`  
  If the variable does not contain an object, the system will raise an error.

> ### Wait, what?
>
> * _Global variables_ are variables that apply to 'the game' - a more poetic way of thinking about them is that global variables apply to the 'it' used in the phrase 'it's raining'. They're useful for tracking most game variables, like story flags and player stats, and might be the only variable type necessary for a visual novel that does not use complex game mechanics.
> * An _array accessor_ represents a position in a numbered list. If you have to remember data that is stored in _a specific order_ (e.g. items in the player's inventory), you can use an array accessor to store it in an array, at the list position you want (e.g.  `Name: inventory[3]/ Value: Milk` would mean "put Milk in Inventory Slot 3").
> * An _object accessor_ lets you change part of an _object_ - a bundle of different attributes referred to by name. This is a useful way of organising variables - e.g. `Name: playerchar.stress/ Value: 50` makes it clear that the variable is to do with the player character.

#### Set profile variable

Set a variable for out-of-story information. Useful for unlocking CG Gallery items, saving options, or horror games where you want to reach through the fourth wall.

#### Set system variable

Set a variable for system information. This can be used for configuration options like the player's preferred audio volume and screen settings.

#### Jump to board

Jumps to another board on the project. Useful for changing scenes or chapters.

#### Jump to storylet

Jumps to a randomly-selected storylet. Boards can be marked as storylets using the Board Editor, and also given tags and conditions to control which storylets are available to the player at any given time.

#### Jump to node

Jumps directly to the node with the given name, within the current board. This won't display as a connector. Can be used within a timer to progress the story automatically.

#### Debug message

Typing a debug message here will send it to the Console when that Node is accessed. Useful for testing your game. You can print variables in Debug messages using markup, too: $Variable

#### Disable text skip

This prevents the user clicking to skip the text reveal on the current node.

#### Wait

Wait the specified number of seconds before the player can progress the game.

#### Wait for input

Waits until the user clicks a mouse button before continuing. This can be useful if you need to wait for a click on a node that doesn't display text.

#### Add timer

Creates a timer. The timer configuration window contains its own action editor. After the number of seconds specified has elapsed, the actions chosen from the action editor will execute. If the player jumps to another board, the timer will be cancelled. Timers can also be marked _count up_, which can be used as a kind of stopwatch.

#### Add global timer

Creates a global timer. This is similar to **Add timer**, except that the timer is not cancelled when the user transitions to another board.

#### Reset timer

Resets the amount of time left before a running timer executes its actions.

#### Cancel timer

Stops a running timer from running, meaning it will not execute its actions.

#### Quicksave

Saves the current game state to Slot 0.

#### Quickload

Loads the game from Slot 0, if there is a file available in that slot.

#### Save to current slot

Saves the game to the current save slot. The current save slot is stored as a number in the global variable `_saveSlot`. This can be useful when creating custom save screens.

#### Load from current slot

Loads the game from the current save slot. The current save slot is stored as a number in the global variable `_saveSlot`. This can be useful when creating custom save screens.

#### Delete from current slot

Deletes the save data in the current save slot. The current save slot is stored as a number in the global variable `_saveSlot`. This can be useful when creating custom save screens.

### UI

_Category for user interface changes._

#### Add popup

Creates a popup window within the UI. The popup runs its own board, independently of the main window.

#### Remove popup

Removes a popup from the screen. The board running inside the popup will stop immediately.

#### Add layout

Adds a _layout_ to the UI. Layouts can be defined using the **UI Editor**.

#### Add bar (!)

Adds a bar that displays a variable by progressively filling or emptying. Useful for displaying things like hit points, or how characters feel about the player.

#### Add counter sprite (!)

Adds a graphic that represents values by transitioning between multiple states. This can be used to display hitpoints as a series of heart icons, or express a character's feelings about the protagonist as an angry or blushing face.

#### Add text object

Adds a text label to the UI.

#### Set counter value (!)

Sets the current value of a bar or counter sprite.

#### Move UI object

Moves a UI object to a different screen coordinate.

#### Set UI object state

Marks a UI object as _active_ or _inactive_. An inactive object cannot be interacted with, and may display differently.

#### Remove UI object

Removes a UI object.

#### SetCursor

Changes the cursor to a custom image.

### Backgrounds

_Category for images that display over the whole screen, behind the sprites._

#### Add background layer

Places an image on the background, on top of any background layers you already have.

#### Remove background layer

Removes a layer from the background.

#### Clear background

Takes away all background layers at once.

#### Fade in background

Fades in the background.

#### Fade out background

Fades out the background.

#### Move background layer

Moves a background layer - useful for anime-style panning.

#### Rotate background layer

Rotates a background layer.

#### Scale background layer

Scales a background layer - useful for Ken Burns zooms.

#### Set background

Places an image on the background.

### Sprites

_Category for images that move around in front of the background. Can use frame animation._

#### Add sprite

Creates a new sprite in the scene. You can specify which set of animations to use for the sprite (configured using the **Sprite Editor**), give the sprite a name (useful for reusing the same sprite multiple times in a scene), set their initial _state_ (animation), and optionally give them a fade-in time in seconds.

#### Show sprite

Reveals a sprite that has been hidden, with an optional fade-in time in seconds.

#### Hide sprite

Makes a sprite invisible, with an optional fade-in time in seconds.

#### Show all sprites

Reveals all the sprites in the scene, with an optional fade-in time in seconds.

#### Hide all sprites

Makes all the sprites in the scene invisible, with an optional fade-in time in seconds.

#### Flip sprite

Flips a sprite horizontally (set "flipped" to true), or unflips ("flipped" to false).

#### Move sprite

Move a sprite somewhere on the screen. The position can be given in "absolute" or "relative" coordinates; absolute coordinates correspond to pixel values, and in the relative coordinate system positions are given proportionally to the size of the screen (from -1.0 to +1.0 vertically and horizontally). You can also specify a time for the transition to take, or leave it at 0 to move the sprite instantly.

#### Scale sprite

Scale the sprite, optionally over a number of seconds.

#### Set Sprite Z Index

The z-index is a number that can be used to control how sprites overlap with each other. Sprites with a higher z-index will overlap sprites with a lower z-index. All sprites will always appear in front of the background and behind the UI.

#### Set sprite state

Chooses a new animation state for a sprite. Usually this will be a new expression or pose, but might also be a different outfit. You can use _quicksets_ in the **Sprite Editor** to define collections of states for use with this action.

#### Set sprite layer state

Chooses a new animation state for a single layer of a sprite. This could be used to change a facial expression or a single piece of clothing.

#### Sprite blend mode

Changes the way a sprite blends into the scene. There are several modes to choose from.

#### Link sprite to node

Set a node ID to jump to when a sprite is clicked on, or set to 0 to clear a sprite's jump target.

#### Attach sprite

Links a sprite to another sprite. When the "parent" sprite moves, the "child" sprite will move with it, and if the parent sprite is removed from the scene, the child sprite will also disappear.

#### Detach sprite

Detaches a sprite that was previously attached to another sprite, making it independent again.

#### Link sprite to node

Sets the _link target_ of a sprite. This is the name of a node in the current board, which the game will jump to when the sprite is clicked on.

#### Remove sprite

Deletes a sprite from the scene.

### Audio

_Category for audio._

#### Play sound

Play an audio file. The file should be the name (with no extension) of an audio file stored in the Resources/Sfx directory.

#### Play music

Plays an audio file as background music. The file should be the name (with no extension) of an audio file stored in the Resources/Music directory. You can set the desired volume and fade-in time, and choose whether the music should loop. Only one music track can play at a time.

#### Stop music

Stops the currently-playing music track, if any. You can optionally set a fade-out time here.

### Textbox

_Category for textbox actions._

#### Hide textbox

Hides the main textbox. You can optionally specify a fade-out time in seconds.

#### Show textbox

Shows the main textbox, if it's been hidden. You can optionally specify a fade-in time in seconds.

#### Textbox position

Tell VNKit where the textbox should display.

### Hypermaps

_Category for interactive, clickable backgrounds._

#### Engage hypermap

Opens the hypermap builder, allowing a dynamic, clickable background to be created by layering a multicoloured image on top of the background that serves as a key to which areas are interactive. You can also set an 'activated' version of the background to change clickable areas when moused over. By clicking a colour on the hypermap, you can type in a node address for each click of that colour.

#### Remove hypermap

Removes the hypermap, preventing the background from being clickable.

### Backstage

_Category for node flows that carry on separately to what the player is currently doing. This is a powerful feature making it possible to create different kinds of gameplay in your visual novel._

#### Start backstage process

Starts a backstage process from the specified node.

#### Pause backstage process

Pauses a backstage process. It can be resumed later.

#### Resume backstage process

Resume a paused backstage process from the node where it was initially paused.

#### Stop backstage process

Stops a backstage process. If you need to run it again, you will need to create another Start backstage process action.