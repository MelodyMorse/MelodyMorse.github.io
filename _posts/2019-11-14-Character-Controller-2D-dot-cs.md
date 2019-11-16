---
layout: post
title: Character Controller 2D dot cs
categories: Tools
img: characterControllerGizmo.PNG
---

I was inspired to do a little work on Brackey's 2D Character controller that I think makes the script more user friendly

The main modification I made were the fields the game designer fills out in the inspector.  In the original version a field named JumpForce determines the amount of vertical velocity added to the Rigidbody2D when the player jumps.  My version has a field named jumpHeight instead.  This makes it easier to get the precise jump height the game designer wants without so much trial and error.  Putting a 3 in this field results in a jump 3 units high. The jump remains jumpHeight units high regardless of the gravity scale.

In the original version runSpeed was a field on the PlayerMovement script.  This was a quirk of how Brackey’s accompanying tutorial was set up. In my version there is a runSpeed field on the CharacterController2D script instead so the script becomes a one stop shop in the inspector for tweaking how the player moves.  The PlayerMovent script is only used to get input.

{% include CaptionedImage.html url="/images/characterControllerDrawerOriginal.PNG" description="Original version" %}
{% include CaptionedImage.html url="/images/characterControllerDrawerNew.PNG" description="My modification" %}

Lastly, I designed a custom gizmo for the character controller that displays the projected jump arc of the player at full speed.  One of the reasons I made my modifications was to make it easier to build levels with a specific jump arc in mind, so I thought it important to have a visual aid in the scene view for level creation

{% include CaptionedImage.html url="/images/characterControllerGizmo.PNG" description="Gizmo showing jump arc" %}

#### What Did I Learn?

In short, that Brackey’s character controller still isn’t adequate for the platformer I eventually want to make.  He designed the character with a CircleCollider2D on the bottom half.  This was at least partly to handle slopes easily, but it makes it so that the player slips off of edges.  There’s also some quirks that come with using Unity’s colliders for a 2D platformer: Getting stuck on platforms and stuff like that.  There are fixes you can do using physics materials, but the process just kinda feels like a hack to me

#### What’s next?

Use math to create my own system of physics and checking for collisions. The game I have in mind would just be complicated by all the bells and whistles of Unity’s 2DPhysics system and I’ll get the control I want more easily just by managing that stuff myself

#### Links
[Original version repo](https://github.com/Brackeys/2D-Movement)

[Fork with my modifications](https://github.com/MelodyMorse/2D-Movement)

[Brackey’s accompanying tutorial](https://www.youtube.com/watch?v=dwcT-Dch0bA&t=289s) 

[Sunnyland Assets](https://assetstore.unity.com/packages/2d/characters/sunny-land-103349?aid=1101lPGj&cid=1101l6H2CqBR&utm_source=aff) 
