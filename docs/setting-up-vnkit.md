---
layout: default
has_children: false
title: Setting up VNKit
nav_order: 2

---
# Setting up VNKit

> ### ALPHA WARNING!
>
> This page describes something that _will be heavily revised in later versions_. The release version of the software will not be this annoying. Please use this as reference for the Alpha version in the meantime.

#### Getting your Unity project up and running

1. Download and install the [Unity Hub](https://unity3d.com/get-unity/download). 
2. Open the hub and install a version of Unity; the current recommended version is **Unity 2020**.
3. In the Unity Hub, create a new project. When asked what kind of project you want to make, select **2D**.
4. You will have to wait for Unity to create the project, which will take _some time_ (about 2-5 minutes). Take the opportunity to grab a cup of tea, if you like.
5. Download the VNKit package, and extract it to a new folder using whichever software you prefer (e.g. Microsoft's inbuilt Compressed File tool, PeaZip, 7Zip, etc). Once extracted, copy the `studio.axile.vnkit` folder into the Packages folder of your new project. Don't forget - you can quickly open a window for it by selecting your project in the Unity Hub list, then choosing 'Show in Explorer' (Windows)/ 'Reveal in Finder' (Mac).

#### Putting VNKit into your game

1. You will be taken to a new Scene. Create a Canvas inside of your scene. To do this, click the GameObject menu, then find UI>Canvas.
2. Right click on the Canvas that you have just created in the Hierarchy. Select 'Create Empty' from the menu that appears. (_Optional - you may want to rename the Empty to something appropriate, like 'VNKit'.)_
3. While the Empty you have just created is selected, look for the Add Component button in the Inspector window. Click this, and add a StoryFrame. (_You can find this more easily by typing 'story' in the Search box above the component selection window._)
4. You will now need to set the **size** of your VNKit virtual screen. In the RectTransform section on the top half of the Inspector window, put appropriate dimensions for the VNKit virtual screen into the Width and Height boxes. (_Note that this is different to the actual size of your game when on devices - it's a reference size used internally. Your game will display correctly on bigger or smaller screens._) **If you're not sure what to use here, put 1920x1080.**
5. Click on the Canvas object in the Heirarchy, and then look in the Inspector. Check:
   * the Render Mode is set to "Screen Space - Overlay",
   * the Canvas Scaler UI Scale Mode is set to "Scale With Screen Size",
   * the Canvas Scaler Reference Resolution is set to whatever you set your VNKit virtual screen size to in the previous step,
   * the Screen Match mode is set to Expand.
6. Save the Scene.
7. Click the StoryFrame in the Heirachy. In the Inspector, you can now click "Open Story Editor". This will open a new window containing everything you need to build a visual novel with VNKit!