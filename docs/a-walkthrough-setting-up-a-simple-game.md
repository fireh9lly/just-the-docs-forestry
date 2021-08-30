---
layout: default
has_children: false
title: Walkthrough - setting up a simple game
nav_order: 999
parent: ''
has_toc: false

---
# Walkthrough

The following is a guide for setting up a simple game in VNKit. It's aimed to help those who are **beginners** in both VNKit and Unity get familiar with the system and workflow.

> ### Step 0 - Getting VNKit Set Up
>
> While it's outside of this walkthrough's intent, obviously you will need to have the VNKit package installed in your Unity project before you can use it. See [Setting up VNKit]().

## Step 1 - It starts from a single Node

When you finish setting up VNKit and enter the Story Editor, you'll be faced with the Board Viewer screen. One Node  is already placed for you.

Begin by typing out the first textbox of your story. When you've done that, right click, click 'Add node'. Then type the second textbox of your story. Then drag from the circle connector on the right of the first Node to link it to the second Node.

![](/assets/images/nodes1.gif)

> #### Don't forget:
>
> At any time you can preview your project. You can push Play in the main Unity window, or [set up a Game preview tab in the Story Editor window](https://vnkit.axile.studio/docs/editor-overview/#a-handy-tip--).

## Step 2 - Your first choice

On the second node, press the `+ Add choice` button a few times until you have the number of Choices you want.

![](/assets/images/nodes2.gif)

You'll need somewhere for all those Choices to lead, so make a new Node for each of the Choices to lead to, and link it up. (_Remember - you don't have to insert the new cable into the Node's connector. You can link by dragging the connector anywhere on the body of a node._) Cables coming out of Choices are always yellow.

Now you have a branch!

## Step 3 - Node conditions

We're going to set up a "hub and spoke" structure here - a common shape that allows the player to read through as many options as they choose in any order before continuing. We also want to have the game remember which of these choices the player has seen, so once they have read at least one thing, they can progress to the next part of the story.

Label the answer node for "I have some questions" with something that makes it clear what it is (like "Question hub"). Then fill out the questions the player can ask.

Set up nodes for every answer, and then connect each answer back to the Hub.

![](/assets/images/nodes_fixed.gif)

You'll now set up a _Condition_ for that last answer, so it will only appear when the player has done something.

Give a Condition to the Node that will represent the next part of the story. Immediately, you'll see coloured chips representing variable use appear above your Node. In the previous Node, you'll see the Condition written out. (Remember - this is just as a reference. If you want to change the Condition, you'll have to do it in the "Condition" section of the target node.)

![](/assets/images/nodes_whatsbest.gif)

> #### Tip -
>
> Unlike some other visual novel engines you might be used to, you don't have to specify "`=true`" - just give the name of the variable. If you're checking that something _isn't_ true, you can say "`not (Variable)`". Doing it this way also counts Null values for variables that you haven't set yet - really useful for checking story flags, since you'll only be creating them when you need to use them.

If you don't like the colours of the chips, you can change them in the sidebar:

![](/assets/images/nodes6.gif)

## Step 4 - Setting flags

The choice that allows the player to carry on with the game will now only be visible to the player if they have one of those two variables we specified. Now all we need to do is set those variables.

On the Node leading from the choice, click "Add Action". Click the action "Set Variable". Type in the name of the variable (you can see it in the sidebar), set it to `true`, and then click OK. Now, when the player visits that node, they'll set a flag that unlocks the second choice in the Hub.

![](/assets/images/nodes7.gif)

You can do this for the other choice too.

You have now learned the basics of building branching path narrative games! But there's a lot more you can do with variables and conditions in VNKit...

## Step 5 - Variables - working with arithmetic

#### Incrementing a variable

Astra, in our game, is going to have a value that represents how she feels about us. She'll like us more if we're good students, and less if we mess around.

Making an exact model of the blurry, confusing world of human emotion isn't possible in a computer game (or in science, or pretty much anything else), but we can make something close enough for a video game by representing Astra's feelings as a number. If the number goes up, she likes us more, and if it goes down, she likes us less. We can then create Node structures which check the number, and flow to different places depending on how high it is, letting Astra express her feelings to us in words and actions.

We'll have Astra like us more when we tell her we're ready to use VNKit, so on the Node just after we have done this, we will add an Action and set a variable representing Astra's emotions.

![](/assets/images/nodes_astraaffection.gif)

    SetVariable
    Name: AstraAffection
    Value: AstraAffection+1

We have to say `Value: AstraAffection+1` because VNKit needs to have perfectly unambiguous instructions on which numbers it's supposed to add together - if we instead just said `Value: +1`, it would create an error. What we're trying to do is to add 1 to _what the value was before,_ so we state it like this.

> #### Good practices
>
> It's true that since this is the first point that we can gain `AstraAffection` in the game, we _could_ just set the variable to `1`, but if we wanted to go back and create other ways to get Affection earlier in the game, we'd have to change everything. Doing it this way allows us to create our visual novel with more flexibility.

But if we run the game right now, we'd get an error. It's impossible to add 1 to `AstraAffection` because we haven't told VNKit what `AstraAffection` is to start with. A variable that hasn't been given a value yet equals `null`, a value that represents "nothing". You can think of `null` as like an empty box, or a blank piece of paper - it's impossible to do any arithmetic with `null`, because it isn't even a number. We need to assign a number value to `AstraAffection` so we can use it.

#### Init

We have to set `AstraAffection` before the first point that we are going to use it in the story. Since we might go back and add earlier points, the best place to put it is in a new node before the first Node. We'll set it as the new Start Node. Name it "Init" (short for initialisation) by typing that in the `Node` box. On this Node, we will use another `SetVariable` action and set `AstraAffection` to `0`.

![](/assets/images/nodes_makinginit.gif)

    SetVariable
    Name: AstraAffection
    Value: 0

Now, when the player adds `1` to Astra's affection value, it will be added to `0`, which is a valid operation in VNKit.

## Decrementing a variable

Let's also add an event to our game that causes Astra to like the player character less.

If we wanted to, we could just do the same as what we did above:

    SetVariable
    Name: AstraAffection
    Value: AstraAffection-1

...But this would allow us to go into negative numbers. That could be fine (it's a common way of designing an affection system - where `0` is perfectly neutral, negative numbers express negative feelings and positive numbers express positive feelings) but in our game, **we don't want the number to be able to go below `0`**. (Astra isn't ever going to really _dislike_ the player - she's just going to like us more if we're good students.)

We have to use different syntax to keep the number from going below `0`

    SetVariable
    Name: AstraAffection
    Value: max(AstraAffection-1, 0)

What this does is compare `AstraAffection-1` to `0`, and sets the `AstraAffection` variable to whichever is higher.

While this is a little arbitrary when dealing with a number representing an abstraction, like Affection values, this is important when working with variables relating to physical objects - coins in the player's wallet, chocolate boxes left to give to the boys on Valentine's Day, or bullets in a gun. (What would -3 bullets look like?)

> #### Game design tip - Affection values
>
> Novice designers of romance games often set up points where one choice _increases_ Affection, while another choice _decreases_ it. In games where a player is actively pursuing a certain character, the Affection point value _remaining the same_ is already a punishment on its own. There are compelling games which use increasing/reducing binary choices for a romance mechanic (such as 1997's _Final Fantasy VII_), but these tend to be games where romantic interactions are a minor thread in a game mostly about something else. If you're making a game where romance is your main mechanic, it's best to only reduce affection points when the player _significantly_ upsets the other character. Remember - the player is already 'losing' points by not taking the opportunity to increase them!

## Step 6 - Adding images and sound to your game

Media files you use in VNKit will need to be imported into Unity's inbuilt Resources system before you can use them.

### a) Background

We're going to start by adding a background image to your game.

Close the Story Editor.

![](/assets/images/bg_closeeditor.gif)

In Unity's Project window, navigate to Assets > Resources > VNKit > Backgrounds. This will open up the Backgrounds folder for your game. Drag and drop your background image into the Backgrounds folder, from your file explorer window.

![](/assets/images/bg_bgadd.gif)

> ### For those using pixel art:
>
> In this walkthrough, we're using a photo background, so Unity's default settings are fine. However, if you're making a game using pixel art, you will find that your images are unacceptably blurry.
>
> If you are having this problem, highlight your image in the Project Assets window, then look at the Inspector. Change the Advanced > Filter Mode setting to "Point (no filter)". Your images should now have pixel-perfect scaling.
>
> ![](/assets/images/pointfiltering.PNG)

Once you've added the background image to the Backgrounds folder, you can add it into your game. Re-open the Story Editor (you might need to click on the VNKit Canvas in the Hierarchy window to get the Open Story Editor button back). Go to your first node (the Init), click Add Action, and add:

* The `Hide Textbox` action (_in the "Textbox" section_). When we preview the game, the textbox will display by default, unless we are using Hide Textbox to get it out of our way. This will help us see the position of the assets better. The Fade parameter lets us set a fade time, but don't worry about it for now - this is just for testing.
* The `Wait for input` action (_in the "Variables and events" section_). This will cause the game to wait for a click before progressing onto the next node - if we don't use it, the game will flow straight through into Astra's first line, bringing the textbox straight back up again to block our view. There aren't any parameters on this action.
* The `Set Background` action. (_It's in the Backgrounds section._)

![](/assets/images/fadeut.PNG)

![](/assets/images/nodes_bgpicker.PNG)

Here you can see all of the backgrounds that you have added to the project folders. Click the one you want to use.

The ScaleMode parameter determines how the background will be displayed. _Fit Height_ will fit the background to the height of the screen, and the Width will be ignored. _Fit Width_ displays the image at the same Width as the screen and ignores the height. _Cover_ automatically scales the image to cover the whole of the screen, keeping the aspect ratio intact - this will be the most common parameter for typical projects. (_Note that none of these options distort or stretch the image!_)

The photo we are using here has a tall aspect ratio, while our game is in a wide aspect ratio. Therefore, some of our background is going to be cut off. We can use the Offset parameter to shift the image around so we see the correct part of it.

#### Handling coordinates

The Offset parameter in Set Background allows a background image to be placed at the coordinates on the screen that you choose, using the centre of the image as the reference point, or _anchor_. You can imagine the background as a printed photograph with a drawing pin in the exact centre, and the screen as a notice board - the coordinate you supply is the exact point on the board the pin will be stuck into.

VNKit has two kinds of coordinates that it understands.

The default mode is _relative_ coordinates. Here, each axis extends from -1 to 1, with 0 in the middle. This allows you to place an image on the screen _proportionally_, without having to worry about the exact pixel location. (For example, if you know you want a character's sprite to be displayed about a third of the way across from the left of the screen, you can place the sprite at `X: -0.33`.) The other mode is _absolute_ coordinates. This lets you place an image at an exact pixel value, for when perfect precision is needed.

\[diagram goes here\]

For our background image, we don't need perfect precision - we just want most of the floor to be in shot. So we'll set the coordinates as `X: 0, Y: 0.6`. This gives a good result when the game is previewed:

![](/assets/images/bgoffset-1.png)

This same coordinate system is used for displaying sprites as well. Let's put Astra on the screen.