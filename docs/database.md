---
layout: default
has_children: false
title: Database
nav_order: 
parent: ''
has_toc: false
published: false

---
# Database

The database allows you to describe _data tables_: lists of similar entities your game. Data tables can be used to store information about characters, items, clues, or any other type of object that might appear in your game. The benefit of using a data table is that the this information can be easily viewed and edited in a central place.

Data stored in the database is _immutable_: it can't be changed during the game. If you need to store a modified version of something defined in a data table, the best way is to store it in a variable, which will make a copy of the data.