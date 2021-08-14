---
layout: default
has_children: false
title: Walkthrough - setting up a simple game
nav_order: 101
parent: ''
has_toc: false

---
# Walkthrough

The following is a guide for setting up a simple game in VNKit. It's aimed to help those who are beginners in both VNKit and Unity get familiar with the system and workflow.

> ### Step 0 - Getting VNKit Set Up
>
> While it's outside of this walkthrough's intent, obviously you will need to have the VNKit package installed in your Unity project before you can use it. See [Setting up VNKit]().

## Step 1 - It starts from a single Node

When you finish setting up VNKit and enter the Story Editor, you'll be faced with the Board Viewer screen. One Node  is already placed for you.

Begin by typing out the first textbox of your story. When you've done that, right click, click 'Add node'. Then type the second textbox of your story. Then drag from the circle connector on the right of the first Node to link it to the second Node!

![](/assets/images/nodes1.gif)

> #### Don't forget:
>
> At any time you can preview your project. You can push Play in the main Unity window, or [set up a Game preview tab in the Story Editor window](https://vnkit.axile.studio/docs/editor-overview/#a-handy-tip--).

## Step 2 - Your first choice

On the second node, press the `+ Add choice` button a few times until you have the number of Choices you want.

![](/assets/images/nodes2.gif)

You'll need somewhere for all those Choices to lead, so make a new Node for each of the Choices to lead to, and link it up. (_Remember - you don't have to insert the new cable into the Node's connector. You can link by dragging the connector anywhere on the body of a node._)

Now you have a branch!

## Step 3 - Variables and conditions

We're going to set up a "hub and spoke" structure here - a common shape that allows the player to read through as many options as they choose in any order before continuing. We also want to have the game remember which of these choices the player has seen, so once they have read at least one thing, they can progress to the next part of the story.

Label the answer node for "I have some questions" with something that makes it clear what it is (like "Question hub"). Then fill out the questions the player can ask.

Set up nodes for every answer, and then connect each answer back to the Hub.

![](/assets/images/nodes4.gif)

You'll now set up a condition for that last answer, so it will only appear when the player has done everything.

Give a condition to the Node that will represent the next part of the story. Immediately, you'll see coloured chips representing variable use appear above your Node. In the previous Node (you may have to click on it to refresh it), you'll see the condition written out as a reference.

![](/assets/images/nodes5.gif)

> #### Tip -
>
> Unlike some other visual novel engines you might be used to, you don't have to specify "`=true`". Just give the name of the variable if it has to be true before the Node will show up. If the variable needs to be False or Null (_null_ is for when the variable does not represent anything, most likely because you haven't set it to anything yet), you can just say "`not (Variable)`".