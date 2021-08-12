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

Step 3 - Variables and expressions 

We're going to set up a "hub and spoke" structure here - a common shape that allows the player to read through as many options as they choose in any order before continuing. We also want to have the game remember which of these scenes we have seen, so once the player has seen all of them, they can progress to the next part of the story.

Set up nodes for every answer, and then loop each answer back to the node itself.