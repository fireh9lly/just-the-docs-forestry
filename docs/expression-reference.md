---
layout: default
has_children: true
title: Expression reference
nav_order: 

---
# Expression reference

In VNKit, you use _expressions_ to write your game's variables and implement conditional branching. Most expressions are simple to understand and write, but they can be combined to allow for more complex effects.

Expressions are used in the Set variable action, in the Condition box on the node editor, and in a few other places.

## Simple expressions

Expressions are built up out of _values_ and _operators_. Values come in five basic types:

* **Numbers.** Numbers can be positive or negative and written with or without a decimal point. Numeric values can be used to represent a character's opinion of the player, statistics like health points or courage, money, or a score.
* **Strings.** A string is a piece of text enclosed in double quotes (""). If you want to put double-quotes _inside_ a string, you have to write them with a backslash like this: \\"

  "You shout \"Hey!\", but all you hear is an echo."
* **Booleans.** These can either be true or false. Boolean variables are often used to remember choices the player has made or scenes that have elapsed, so they can affect the story later; this type of variable is often known as a "flag" or a "switch".
* **Arrays.** These are lists that can contain other values. You create them using squackets, like this: `["garlic", "lemon juice", "oregano"]`

  Arrays can contain any kind of data, including other arrays. You can think of an array as a numbered list, where the first entry in the list is numbered 0. To get an individual element stored in an array, use the name of the array followed by the index number, in square brackets, of the element you want.

  `ingredients[0] -> "garlic"`

  `ingredients[1] -> "lemon juice"`

  `ingredients[2] -> "oregano"`

  Arrays can be useful for storing player inventories, or lists of locations or clues.
* **Objects ##TODO**
* **Stored expressions ##TODO**
* **Null.** A value that represents nothing. This shows up when reading a variable that doesn't exist, when accessing an array element that doesn't exist, and more generally when you least expect it.

There are also _variables_ and _functions_; variables can store any of these five types, and functions can return them.

* **Variables** are created by the "Set variable" action, and can contain anything. You'll use variables all the time for tracking important story information; they're saved when the player saves the game.
  ![](https://lh4.googleusercontent.com/USVYdqMR8iS41xLNj06jp0iM_dypE64xK6nqqx-pmP-wLr--k6gAEX7SnRBBClUSn_xUW6gRHZOC5lFIkpZ1cUtQMNycBpvbYi_Ad_92lf7KvIFnBME8qxDGTXoxh1p36YktOu-L =319x123)
* **Functions** are special operations built into VNKit. To call a function, use its name followed by a set of brackets. The brackets contain the _parameters_ (values) you want to give to the function. Examples:

  `round(2.4)` -> This returns 2.

  `push(array, 10)` -> This puts the number 10 on the end of the array called array.

  `max([4, 5, 6])` -> This returns 6, the highest value in the array \[4, 5, 6\].

  A full list of available functions is given in the **Functions** section below.

## Comparisons

Comparisons are an important part of using expressions in conditionals. All comparison operations return a boolean value, which means you can use a Set variable action to store the result of a comparison if you need it later.

The following comparison operators are available:

`a = b`

Tests if two values are equal. This can be used with numbers, strings, and booleans.

`a <> b`

Tests if two values are unequal. This can be used with numbers, strings, and booleans.

`a > b`

Tests if a is greater than b. This can be used with numbers.

`a < b`

Tests if a is less than b. This can be used with numbers.

`a >= b`

Tests if a is greater than or equal to b. This can be used with numbers.

`a <= b`

Tests if a is less than or equal to b. This can be used with numbers.

`a and b`

Tests if a is true and b is true. This can be used with any two values, not just booleans: null and the number 0 will be interpreted as false, and all other values will be interpreted as true.

`a or b`

Tests if either a or b are equivalent to true.

## Negation

**not** can be used to negate a boolean value (other types will be interpreted as booleans, using the rules above).

`not true` -> false

`not false` -> true

`not 0` -> true

`not 135` -> false

## Arithmetic

`a + b`

Adds a and b together. This can be used with numbers but also works for adding strings together. If either a or b is a string, both values will be converted to strings and added together, giving a string.

`a - b`

Subtracts b from a. This can be used with numbers.

`a * b`

Multiplies a by b. This can be used with numbers.

`a / b`

Divides a by b. This can be used with numbers.

Arithmetic operations happen in BODMAS/PEMDAS order, so an expression like

10 + 100 / 5

gives the result 30, not 22. You can control the order of operations by using brackets:

`(10 + 100) / 5`

gives the result 22, not 30.

## Dice

You can also use tabletop-style dice notation in expressions: for example,

`2d6`

will return the result of rolling two six-sided dice, added together. For complex dice expressions you may need to use the roll function described below.

## Compound expressions

You can chain expressions together to compose more complex tests, using brackets if necessary to provide clarification. For example:

`not stress > 20 and not boltIntroSceneDone and gameDay >= 5`

Check conditions for triggering Bolt's introduction scene. The player can only encounter him if their `stress` is equal to or lower than `20` and it is `5` days or more since the beginning of the game. However, they also shouldn't get the scene if they have already seen it. We can make the scene set the `boltIntroSceneDone` flag (a boolean variable) to `true` when it finishes, and confirm the flag is not set before initiating the scene.

`ceil(roll(3, 6) / 2) <= astraAffection`

Rolls three six sided dice, divides the result by 2, rounds it up, and returns true if the result is less than or equal to Astra's current affection level.

`min(\[rowleyHealth, winifredHealth, obericHealth\]) < 250 and find(statusEffects, "curse") = null`

In this example, we only want to summon the Vitæ Spirit from Chapter 1 if the health of any three characters has fallen below 250, and the party is not currently under a "curse" effect.

## **Function list**

### **call(e)**

Calls (evaluates) the stored expression `e` and returns the result.

### **ceil(n)**

Rounds the number `n` _up_ to the nearest integer. Negative values will be rounded towards zero. Returns a number.

### **date()**

Returns the current date, in the local timezone, as an array in the following format:

`d[0]` -> Year

`d[1]` -> Month

`d[2]` -> Day

### **dateTime()**

Returns the current date and time, in the local timezone, as an array in the following format:

`d[0]` -> Year

`d[1]` -> Month

`d[2]` -> Day

`d[3]` -> Hour

`d[4]` -> Minute

`d[5]` -> Second

### **dateUTC()**

Returns the current date and time, in the UTC timezone, as an array in the following format:

`d[0]` -> Year

`d[1]` -> Month

`d[2]` -> Day

`d[3]` -> Hour

`d[4]` -> Minute

`d[5]` -> Second

### **find(a, v)**

Searches the array `a` for the value `v` and returns its index (position) in the array. The first element is at index 0.

If `a` does not contain `v` then the result is `null`; this can be useful to check whether an array contains a particular value.

`find(["red", "green", "blue"], "green")` -> Returns 1.

`find(["red", "green", "blue"], "purple")` -> Returns null.

### **floor(n)**

Rounds the number `n` _down_ to the nearest integer. Negative values will be rounded away from zero. Returns a number.

### **generate(string)**

Returns a value from the Generator with the given name. Generators are created and managed using the Generator Editor.

### **getTimer(string)**

Returns the current value of a timer with the given name. If the timer does not exist or has finished, this function returns `null`.

### **len(value)**

Returns the number of elements in an array, or the length of a string (the number of characters in the string).

### **insert(array, index, value)**

Creates a new copy of the array **array**, with the **value** inserted at the position **index**. The value is placed immediately before the current element in that position (if any), so

`insert(array, 0, "bees")`

will make a copy of `array`, place the string `"bees"` at the start, and return the new copy.

If `index` is less than `0` or greater than the size of `array`, the return value will be the same as `array`. If `index` is equal to `length(array)` then `value` will be placed at the end of the new copy of `array`.

### **max(number0, number1, number2...)**

### **max(array)**

Returns the highest of a list of numbers, or the highest number in an array.

You can use this to prevent a value going under a minimum threshold, like this:

![](https://lh3.googleusercontent.com/Kx2lEYi2AHQ9kHSHuzQzZnXsFbAbp5iOR_yVj5cukG8bSZdW8JNr14j6gUj2Y92Civu7RR86r-k8SG5LAqBXqtsTYs9dXBv6YxoAA3qMoTAsVE3MGBCn4AhpEjCfos2PITED8jZE =385x133)

### **min(number0, number1, number2...)**

### **min(array)**

Returns the lowest of a list of numbers, or the lowest number in an array.

You can use this to prevent a value going over a maximum threshold, like this:

![](https://lh3.googleusercontent.com/MKUBdL4YZiAW05RlB6ZdJxQmkSPxpXfd7-VAX9cknEiuiKSRIfMzSrerTfsE3dl9_MfI4U6MpOWHubY6mwMb5BSWL-g_S46BRu9wxcL-sdNzKh4pCsMaOU1KFAaFQNMuFTtk-Jvj =385x133)

### **pop(array)**

Returns a new copy of `array` with one value removed from the end. If **array** is empty this will return an empty array.

### **push(array, value)**

Returns a new copy of `array` with `value` added to the end.

### **remove(array, index)**

Creates a new copy of `array` with the value at `index` removed. `index` must be a number (non-integer numbers will be rounded down). If `index` is less than `0` or greater than `length(array)-1`, the return value will be the same as `array`..

### **roll(dice, sides)**

### **roll(sides)**

Rolls a number of dice, adds them up, and returns the result.

### **round(number)**

Rounds a number to the nearest whole number. Numbers ending in `.5` will be rounded up.

### **time()**

Returns the current real-world time, in the local timezone, as an array in the following format:

`t[0]` -> Hour

`t[1]` -> Minute

`t[2]` -> Second

### **timeSince(t)**

Returns the real-world time elapsed since the time t, in the local timezone. t is an array in the following format:

`t[0]` -> Year

`t[1]` -> Month

`t[2]` -> Day

`t[3]` -> Hour (Optional)

`t[4]` -> Minute (Mandatory if hour is specified)

`t[5]` -> Second (Optional)

The return value is in the same format (with all optional values filled).

### **utc()**

Returns the current real-world time, in the UTC timezone, as an array in the following format:

`t[0]` -> Hour

`t[1]` -> Minute

`t[2]` -> Second

### **utcSince(t)**

Returns the real-world time elapsed since the time `t`, in the UTC timezone. `t` is an array in the following format:

`t[0]` -> Year

`t[1]` -> Month

`t[2]` -> Day

`t[3]` -> Hour (Optional)

`t[4]` -> Minute (Mandatory if hour is specified)

`t[5]` -> Second (Optional)

The return value is in the same format (with all optional values filled).