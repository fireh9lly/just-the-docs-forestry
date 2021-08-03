---
layout: default
has_children: false
title: Node Cheatsheet
nav_order: 3

---
# VNKit - Node Cheatsheet

## Did you say 'Node'?

A _Node_ is the basic building block of a VNKit game.

Nodes can hold the _text_ of your game, such as your characters' dialogue, and choices the player might make during the story. They can also be used to perform _actions_, like displaying images, playing sounds or setting a story flag. Nodes also can contain _conditions_, allowing VNKit to make decisions based on what has happened in the game so far.

Nodes have _connectors_, which link them to other Nodes. These connectors control the order that Nodes will execute. By linking Nodes to each other, you can create a game from a dynamic flow chart, similar to planning a story by arranging index cards.

## Anatomy of a Node

![](https://lh6.googleusercontent.com/yFIC1ZL15zqzJ_ePJjmLJ9EjR9D0Kp3fv64mfgZ82MHzeLZqBq_xZnjvuBgmhROEFqyPpwuKQlW8qN_7JOHFFSzEqmhSGK-IOdj_N8PJs3G0IFPZmWsE2wc9yvBUiWpFU_pBd8XM)

At the top of the Node are the Node's name and ID number. Both can be used to identify the Node when setting up certain actions that point to a specific place, such as hypermaps and jumps. You can also use the Node name for your own reference.

The button to the right of the Node number pops out the _notepad_, which can be used to store notes. The notepad can be hidden by clicking on the button again. If there's a note available to look at, the '...' icon will change to a ' * ' icon.

_Input connectors_ gather together on the top left of the Node (into the loaf-shaped input).

_Output connectors_ come from the dots on the top right of the Node. Nodes can be connected by clicking on the output socket, then dragging the cord to the target Node. (You don't have to link it specifically to an input connector - dragging to anywhere on the target Node is fine.)

**The order of the output connectors is important.** The game checks each connected Node **from top to bottom**, and the story will flow to **the first Node** it checks that has a fulfilled condition. (See **Node Behaviour**).

The _Condition_ box can be used to control the flow of the story. Writing an _expression_ in this box will prevent the story from flowing to the Node unless the game has fulfilled the expression's requirements. See the **Expression Reference** for more on how to write expressions.

For Nodes that represent a line of dialogue, the _Speaker_ box can be used to record the name of the speaking character. This will be displayed just above the textbox in ADV mode, or at the beginning of the line in NVL mode.

The large _Text_ window shows the text that will display at that point in the story. You can use markup here to add font effects, or to display variables. (See **Markup**.)

The _Clear textbox_ toggle is checked by default. It means any text on the Node will replace the text from the previous Node. If this box is empty, the text in this Node will instead be appended to the text of the previous Node. You will want to uncheck this quite often in an NVL format game. In an ADV format game, you will want to leave this box checked most of the time, but unchecking the box is useful if you need to perform actions in the middle of a single text box.

![](https://lh6.googleusercontent.com/f7hSKAimG6wsHmSXyE7JYBQ1MTLZgJe9f0nP839zdhE13Cxscv9xeWz-uvkhGBOhV4SsZzr9Gvx84nnd1z1tyTGaXnhxipimOXiboNI6BAUikufgEpBBn53HWODfScotIbItuiTx)

Next is the _action list_, which shows the actions that will be performed when the story reaches this Node. Actions can be dragged up and down to reorder them using the arrows at the left, or deleted with the X button on the right. Hovering over the action will show its full explanatory text in a tooltip; clicking on it will open the **Action Editor**.

Underneath the action list is the _Add Choices_ button - clicking this will start a list of _choices_ the player can make when they arrive at this Node. The choice text written here will be displayed on a choice menu in-game, and each choice has an outgoing connector on it with an orange line leading to another Node. As with ordinary connectors, choices can have conditions associated with them: if the connected Node has a condition, **the choice will only appear to the player when that condition holds true.** In the example image above, the "Offer extravagant gift" option will only appear if the _preparedExtravagantGift_ variable was set to **true** earlier in the story.

The Choices list shows any conditions that need to be met for a choice to be visible to the player, as a reference. This field cannot be edited. A choice condition must be changed by editing the Condition field on the connected Node.

Finally, any variables the node uses will be indicated by a coloured tab sticking out of the top; you can mouse over this to see the name of the variable, and a list of variables in the board will also appear in the info bar at the right of the screen.

## Node behaviour

When the flow of the story reaches a Node, each of its actions is executed, in order from top to bottom, in a single frame. Therefore, from the player's perspective, every action on a node will execute simultaneously.

The Node's text will be displayed in the game if the _textbox_ is visible, as well as any Speaker name. If the Node has _choices_, they will be displayed in a menu for the player to select.

A Node with nothing on it will not do anything. Control will immediately flow to the first available connected Node. Empty Nodes with outgoing connectors are therefore useful as "hubs" or "selectors" that branch the story depending on variables. (See Node #4 in the below example.)

!\[\](https://lh3.googleusercontent.com/EoZXei52MmiHlfS4OfbNI2yvbvONnyp-4_GfqOp8OjjiwAtqjWmIY54rKocivA8zWOHTTnRhzMem6rewr932SH_8Z5AQ-x2a-UiHBrOfnJxj138TLIpz2NrInafi4zsID7MYoEJX)

If the Node has choices on it, the game will wait for the player to choose one before continuing.

If the Node has no choices but is displaying a textbox on the screen, the game will wait for the player to click on the textbox or the game background in order to continue.

If neither of these are the case, the game will wait for any sprite movements or fades to complete, then move automatically to the next Node. This can be overridden by using the _Wait_ action, which forces the player to wait a specified length of time (in seconds) to see the next Node. This is useful if you want to show the player an entire sprite frame animation before continuining.

## The Action Editor

When you click the **Add action** button on a Node, a list of available actions will open. You can collapse different categories within the Action list using the arrows to the top right of each category. The Action list will remember which categories you have collapsed while you are working on your current project.

The following is a quick reference for available actions. For more detailed information, see **The Action Editor.** (Not done yet! -Ed.)

### Variables and events

_Category for actions that control the game flow._

#### Set variable

Sets a variable, letting your game store information about itself that can be checked later. An essential building block for interactive games.

#### Set profile variable

Set a variable for out-of-story information. Useful for unlocking CG Gallery items, saving options, or horror games where you want to reach through the fourth wall.

#### Show board

Jumps to another board on the project. Useful for changing scenes or chapters.

#### Debug message

Typing a debug message here will send it to the Console when that Node is accessed. Useful for testing your game. You can print variables in Debug messages using markup, too: $Variable

#### Jump to node

Jump to a node. This won't display as a connector. Can be used within a timer to progress the story automatically.

#### Wait

Wait the specified number of seconds before the player can progress the game.

#### Add timer

Creates a timer. The timer configuration window contains its own action editor. After the number of seconds specified has elapsed, the actions chosen from the action editor will execute.

#### Reset timer

Resets the amount of time left before a running timer executes its actions.

#### Cancel timer

Stops a running timer from running, meaning it will not execute its actions.

#### Quicksave

Saves the current game state to Slot 0.

#### Quickload

Loads the game from Slot 0, if there is a file available in that slot.

### UI

_Category for user interface changes._

#### Add popup

Creates a popup window within the UI. The popup runs off its own board.

#### Remove popup

Removes a displayed popup.

#### Add bar

Adds a bar that displays a variable by progressively filling or emptying. Useful for displaying things like hit points, or how characters feel about the player.

#### Add counter sprite

Adds a graphic that represents values by transitioning between multiple states. This can be used to display hitpoints as a series of heart icons, or express a character's feelings about the protagonist as an angry or blushing face.

#### Add text object

Adds text onto the screen. Useful for attaching labels to bars.

#### Set counter value

Sets the current value of a bar or counter sprite.

#### Move UI object

Moves a UI object to a different screen coordinate.

#### Remove UI object

Removes a UI object.

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

Creates a new sprite in the scene. You can specify the "cast member" to use as the sprite, give the sprite a name (useful for reusing the same sprite multiple times in a scene), set their initial _state_ (animation), and optionally give them a fade-in time in seconds.

#### Show sprite

Reveals a sprite that has been hidden, with an optional fade-in time in seconds.

#### Hide sprite

Makes a sprite invisible, with an optional fade-in time in seconds.

#### Flip sprite

Flips a sprite horizontally (set "flipped" to true), or unflips ("flipped" to false).

#### Move sprite

Move a sprite somewhere on the screen. The position can be given in "abosolute" or "relative" coordinates; absolute coordinates correspond to pixel values, and in the relative coordinate system positions are given proportionally to the size of the screen (from -1.0 to +1.0 vertically and horizontally). You can also specify a time for the transition to take, or leave it at 0 to move the sprite instantly.

#### Scale sprite

Scale the sprite, optionally over a number of seconds.

#### Set sprite state

Chooses a new animation state for a sprite. Usually this will be a new expression or pose, but might also be a different outfit.

#### Sprite blend mode

Changes the way a sprite blends into the scene. There are several modes to choose from.

#### Link sprite to node

Set a node ID to jump to when a sprite is clicked on, or set to 0 to clear a sprite's jump target.

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

Hides the textbox. You can optionally specify a fade-out time in seconds.

#### Show textbox

Shows the textbox, if it's been hidden. You can optionally specify a fade-in time in seconds.

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

## Markup

Inside a node's text, you can use a simple form of markup to control formatting. This uses a syntax based on [Markdown](https://daringfireball.net/projects/markdown/):

**Italics:** Use \**asterisks*\*

**Bold text:** Use \*\***double asterisks**\*\*

**Bold italics:** Use \*\*\****triple asterisks***\*\*\*

**Underlining:** Use \_\_<u>double underscores</u>\_\_

**Links:** \[This is a link:23\] will create a link to the node with ID 23, highlighted in blue; when the user clicks the link, the story will jump to node 23. In NVL mode, links will deactivate when clicked on, after which they will look the same as ordinary text. Links are therefore useful for making hypertext interactive fiction. Note: Links only allow you to link elsewhere in the game: they do not allow you to link to external websites.

If you want to use asterisks and underscores in text without accidentally turning them into markup, you can mark them with a backslash like this: \\*. If you want to use a backslash without it affecting how the game understands markup, type a double backslash: \\\\.

You can also add _rests_ to control the speed at which text is displayed (when using the **Typing** text mode). A rest causes the text to pause briefly as it's being shown to the player. You can control the length of the pause (in seconds) by setting the **Rest time** property on the Story Frame.

A rest is marked with a hash character: #. For longer rests, you can use any number of hashes together: ###.

`"I think...### I will be going now."`

You can also use variables in text. To use a variable, write a dollar sign ($) followed by the variable's name.

`"Ah, so your name is $playerName?"`

This works for strings, numbers, booleans (represented as "true" and "false"), arrays (which are written out in square brackets), and even objects (displayed with their values in braces). Stored expressions can also be substituted into text, though will probably look strange.

You can substitute more complex expressions by using the `$` operator and placing the expression in brackets:

`"You found $coinsCollected doubloons already! If you find one more, you'll have $(coinsCollected+1)!"`

## Things to watch out for

### "My conditional branches aren't going in the direction I expect!"

Are your branches in the correct order?

In a branch, VNKit decides which Node to go to by checking the conditions of the Nodes it is connected to from top to bottom, in order. In branches, make sure any Nodes with an empty conditions box are connected _underneath_ Nodes with conditionals. Otherwise, story flow will progress through the Node without conditionals, and the other conditions will not be checked.

Also, check you are using the right expressions:

* Check that you are putting the inequality in front of the equals sign for _greater than and equal to_ and _less than and equal to_ checks - PlayerCash>=300, not PlayerCash=>300.
* Have you accounted for all possible conditions? If you have set up a two-pathed branch for `DatedMiguel > 3` and `DatedMiguel < 3`, what happens if the player has dated him exactly 3 times? A variable that is being subtracted from can go into negative numbers, which can cause unexpected behaviour if the value represents an amount that should stop counting down at 0 - e.g. remaining_apples or playerGoldPieces. Think through the mathematical logic of your branches carefully!
* Be careful using conditions to check for Boolean=false. When a Boolean variable cannot be found by VNKit, it defaults to _null_, not to false. Since you will usually be setting a story flag to True at the same time as you create it, it is usually better practice to check that a story flag has not been set by checking for "not Boolean", which accepts both Boolean=false and Boolean=null.

### "I have a complex project with backstage processes that isn't working as it should."

A good starting point is to add the Debug message action to every node that is potentially suspect. The Debug message action will push a message to Unity's console every time the node is active, which will make it easier to see if something is going wrong. If you are debugging a loop process, make sure the Collapse button is not selected, so you can see the Debug messages appear in the order your project creates them.

### "My project where I have chained over a hundred empty Conditional hubs together seems to freeze for a couple of seconds."

Each node takes one frame to run, so an extremely complex hub/selector structure may end up creating a tiny delay. In a situation where you were checking 60 conditionals in successive empty nodes, this delay could last 1 second. We think this is unlikely to cause any problems for most developers using VNKit as intended, but if it is giving you issues, please contact us. However, if you're reaching this limitation a lot, it is more likely that you are trying to do something that VNKit simply isn't very good at doing, and you would have better performance using a conventional scripting language.