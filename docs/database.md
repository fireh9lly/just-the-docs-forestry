---
layout: default
has_children: false
title: Database
nav_order: 
parent: ''
has_toc: false

---
# Database

The database allows you to describe _data tables_: lists of similar entities your game. Data tables can be used to store information about characters, items, clues, or any other type of object that might appear in your game. Data tables are useful for viewing and editing this information in a central place.

![](/assets/images/spell-list.png)

On the left-hand side of the window is a list of tables defined in the database. Clicking one of these will open it in the editor.

At the top of the main panel you can see the table's name, followed by the **+Add field** button. This will add a new _field_ – essentially the same as a variable – to the table. You can set the field's **Name** and **Type** (integer, float, string, array, object, or stored expression), or remove it with the **X** button at the right. Be careful when editing the field list: changing the type of the field will destroy any existing data. 

Below the field list is the **+ Add row** button, which adds a new row to the end of your data table. (**Alpha alert**: Table rows can't be reordered currently.)

**Remember** that data stored in the database is _immutable_: it can't be changed during the game. If you need modify something defined in a data table, the best way is to make a copy of the data by storing it in a variable; you will then be able to modify the variable like any other.