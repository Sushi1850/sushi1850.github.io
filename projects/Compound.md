---
layout: projectInformation
title:  "Compound"
summary: "My contribution to Compound"
thumbnail: /assets/img/gallery/Compound/Compound.png
permalink: /projects/Compound/
---

This project was built with GameMaker 2, click <a href="https://kimball-brooksby.itch.io/compound" target="_blank">here</a> to check out Compound on Itch.io!!!<br>

<h1>Doors</h1>

<h3>The player can interact with certain doors without a keycard, but some of the doors require a keycard to open.</h3>

I used a timeline to achieve the rotation on the door. I have a collision around the door that detects the wanderer and will open for it and close it after it passes through the door.<br><br>

<h1>Cinematic Ending</h1>

<h3>The cinematic ending is done by a sequencer that triggers when the player has successfully beats the game</h3>

By using the tracks of the sequencers, I control the doors, lights, camera, and elevator to move in a cinematic view to end the game on a cliff hanger.<br><br>

<h1>Enemy AI</h1>

<h3>I create both of the enemies, wanderer and shambler, that will aggro towards the player when in view and attack them.</h3>

I created the enemies with an Unreal Engine 5 behavior tree and blackboard to keep track of the enemy state. Shamblers will move to a random location which allows them to move around the map when not aggro. The wanderer will move around the map clockwise with a fixed route. Both of the enemies will behave similarly when they see the player, they will chase them until they can no longer see them but will remember their last known location and move to it to check around it, if the player is nowhere to be seen then they return to their original behavior. Enemies can also hear the footsteps of the player when near.<br><br>

<h1>Health UI</h1>

<h3>The player will know how much health they have by seeing blood around the border of the screen. The more red and blood their is, the less health they have.</h3>

I used a UI interface to lock an image of blood around the screen. I adjust the opacity of the image depending on the player health.<br><br>

<h1>Items</h1>

<h3>Some of the items that I made for the game includes: pistol, keycards, all three stims, axe, medkit, and gnome keys</h3>

Each of the items can be compounded into a better version of its self. This helps benefit its effect when used.

The pistol will fire a bullet when the gun is loaded. Instead of spawning a bullet and allowing Unreal Engine 5 projectile movement to handle it, I used line tracing to detect if the pistol is aimed at a shambler, which will deal damage if lined up correctly.

Keycards are simply an object that once in the inventory, the player can open doors that require the keycard to open.

The three stims consist of speed, strength, and stealth. The speed increases the player's movement, works with crouch and sprint, strength increases the damage of the axe towards the shambler, and stealth reduces the range of the player's footstep.

The axe will deal damage when swung at a shambler that is in range with a collision box in front of the player. Another utility of the axe is breaking certain walls which is detected by the compound level of the axe.

The medkits will heal the person's health when used. The higher the level it is, the more it will heal the player.

The gnome keys are an item for an easter egg. Play the game to find out!!! :)<br><br>