---
layout: default
has_children: true
title: nothings (please leave in drafts)
nav_order: 
parent: ''
has_toc: false
published: false

---
> Sweet nothings
>
> `null`, `0`, and `false` all represent things that aren't there, but they're all different. This short guide will help you distinguish between different kinds of nothing.
>
> * `null` is just nothing - it's not anything. It's like a blank page with nothing written on it.
> * `0` is a number, so even if it means you don't have any of something, we can still add things to it, subtract from it, and multiply by it. (But not divide by it!)
> * If a variable is `false`, it means the variable is a Boolean - a Boolean is a variable that can be either `true` or `false` and nothing in between - and that it's currently `false`. It's like a lightswitch, currently in the 'OFF' position.
> * `NaN` means 'not a number'. It is a special kind of nothing that you will get if you try dividing a number by `0`, doing arithmetic with things that are not numbers, and other things that don't make sense. `NaN` isn't useful in programming logic. If you try to save a `NaN` value in a VNKit project, VNKit will produce an error and refuse to save. 