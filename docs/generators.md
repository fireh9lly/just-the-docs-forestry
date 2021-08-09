---
layout: default
has_children: false
title: Generators
nav_order: 
parent: ''
has_toc: false

---
# Generators

The generator editor is used for creating _generators_, which can be used for drawing random numbers or picking words/phrases from a list. There are four types of generators available:

* **DiceGenerator:** This is used to generate random integers (whole numbers) by rolling a number of dice and adding them together. You can also add a flat modifier to the final roll.
* **ShuffleGenerator:** This generates a series of numbers between a defined minimum and maximum value, with no repeats (when the generator runs out of unused numbers, the order is shuffled and starts again from the beginning). This roughly simulates a deck of cards.
* **StringTable:** This is a list of string values that can be generated randomly (_Random_ mode), in an ordered sequence (_Sequential_) or in a shuffled sequence (_Shuffle_). You could use this to easily set up a character who barks a few random lines, without creating a complex network of nodes or variables to track which lines they've said recently.
* **NumberTable:** This is a list of numbers that can be generated in _Random_, _Shuffle_ or _Sequential_ mode, in the same way as a StringTable.

To use a generator in-game, call the `generate()` function with the name of the generator; see the [Expression reference](/docs/expression-reference/ "Expression reference") for more details.