---
layout: default
has_children: false
title: Node Overview
nav_order: 98

---
# Node Cheatsheet

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

![](https://lh3.googleusercontent.com/EoZXei52MmiHlfS4OfbNI2yvbvONnyp-4_GfqOp8OjjiwAtqjWmIY54rKocivA8zWOHTTnRhzMem6rewr932SH_8Z5AQ-x2a-UiHBrOfnJxj138TLIpz2NrInafi4zsID7MYoEJX)

If the Node has choices on it, the game will wait for the player to choose one before continuing.

If the Node has no choices but is displaying a textbox on the screen, the game will wait for the player to click on the textbox or the game background in order to continue.

If neither of these are the case, the game will wait for any sprite movements or fades to complete, then move automatically to the next Node. This can be overridden by using the _Wait_ action, which forces the player to wait a specified length of time (in seconds) to see the next Node. This is useful if you want to show the player an entire sprite frame animation before continuining.

## The Action Editor

By clicking `Add action`, it will open the Action Editor. The Action Editor allows your Node to do actions that change the game. For more on this, see the Action Editor. _(Fix this!)_

## Markup

Inside a node's text, you can use a simple form of markup to control formatting. This uses a syntax based on [Markdown](https://daringfireball.net/projects/markdown/):

* **Italics:** Use `*asterisks*`.
* **Bold text:** Use `**double asterisks**`.
* **Bold italics:** Use `***triple asterisks***`.
* **Underlining:** Use `__double underscores__`.
* **Links:** \[This is a link:StartOfBoard\] will create a link to the node with the name `StartOfBoard`, highlighted in blue; when the user clicks the link, the story will jump to the node. In NVL mode, links will deactivate when clicked on, after which they will look the same as ordinary text. Links are therefore useful for making hypertext interactive fiction. Note: Links only allow you to link elsewhere in the game: they do not allow you to link to external websites.

If you want to use asterisks and underscores in text without accidentally turning them into markup, you can mark them with a backslash like this: `\*`. If you want to use a backslash without it affecting how the game understands markup, type a double backslash: `\\`.

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

* Check that you are putting the inequality in front of the equals sign for _greater than and equal to_ and _less than and equal to_ checks - `PlayerCash>=300`, not `PlayerCash=>300`
* Have you accounted for all possible conditions?
  * If you have set up a two-pathed branch for `DatedMiguel > 3` and `DatedMiguel < 3`, what happens if the player has dated him exactly 3 times? Use _greater than or equal to_ `>=` or _less than or equal to_ `<=` to avoid problems like this.
  * A variable that is being subtracted from can go into negative numbers. If the value represents an amount that doesn't make sense for it to go lower than 0 - e.g. `playerGoldPieces`, `numberOfGummyWorms` - this can cause unexpected behaviour. For numbers like this, it's best to use `max(ArrowsInQuiver -1, 0)` instead of `ArrowsInQuiver -1`.
* Be careful using conditions to check for `Boolean=false`. When a Boolean variable cannot be found by VNKit, it defaults to _null_, not to false. Since you will usually be setting a story flag to True at the same time as you create it, it is usually better practice to check that a story flag has not been set by checking for `not Boolean`, which accepts both `Boolean=false` and `Boolean=null`.

### "I have a complex project with backstage processes that isn't working as it should."

A good starting point is to add the Debug message Action to every node that is potentially suspect. The Debug message Action will push a message to Unity's console every time the node is active, which will make it easier to see if something is going wrong. If you are debugging a loop process, make sure the Collapse button is not selected, so you can see the Debug messages appear in the order your project creates them.

### "My project where I have chained over a hundred empty Conditional hubs together seems to freeze for a couple of seconds."

Each node takes one frame to run, so an extremely complex hub/selector structure may end up creating a tiny delay. In a situation where you were checking 60 conditionals in successive empty nodes, this delay could last 1 second. We think this is unlikely to cause any problems for most developers using VNKit as intended, but if you're reaching this limitation a lot, you are probably doing something experimental with VNKit that it was not designed to do. (And you probably know it.)