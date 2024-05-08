---
layout: projectInformation
title:  "Trash Pandamonium"
summary: "My contribution to Trash Pandamonium"
thumbnail: /assets/img/posts/TPBoxArt.png
permalink: /projects/TrashPandamonium/
---

This project was built with Unreal Engine 5 (Blueprints)

<h1>Respawn</h1>

<h3>When a player falls off the platform, the player will be translated upwards and towards a respawn point. Later on, I implemented a seagull that would spawn, pick up the player, rotate towards the respawn point, fly over to the respawn point, drop the player off, and fly upwards afterward.</h3>


The way I implemented this functionality is whenever a player touches an out-of-bounds, the player will loses the ability to input any buttons except the pause button by overriding the input mapping of the player. Next, I use two float timelines, one for translating the player upwards which is just the respawn point with a higher y-axis, and the other is used to translate the player to the respawn point while keeping the higher y-axis. Afterwards, the player will be drop onto the battefield and will be able to use input again.

The seagull works similar to the player but with a slightly higher y-axis so that the seagull will appear above the player. When a player falls off, the seagull will spawn to the left of the player and will fly downwards to player. This is done by using a float timeline that will translate the seagull from the spawn location to the player location. Once it reaches the player, the seagull will rotate and face the respawn point then move towards the respawn point. After the seagull has translated to the respawn point, the seagull will rotate upwards while heading towards its forward vector to simulate it flying away.


<h1>Cars</h1>

<h3>In the cityscape map only, cars will spawn outside of the map, drive across the city, and despawn after the timeline has ended. The car has collision detection with the player and will apply hit stun and stop to the vehicle and the player. I added headlights to the cars to give it detail. Lastly, I implemented an algorithm where the cars will only spawn up to 2 times per lane before switching restricting the lane and having the car spawn in the other lane.</h3>

With the cars, I used a float timeline to translate it across the road with a fix starting location and end location. I able to spawn the cars from a event track timeline which will randomly spawn the cars either in the top or bottom lane. The algorithm that I used to only allow 2 cars to spawn on a lane before switching to the other lane is whenever a car spawn on a specific lane, it will store this knowledge into an array. Once the array reaches the limit per car that can spawn continuously, it will check all the knowledge of the past vehicle of which lane it has spawn in. If all of the cars spawn on the top lane then the next car will guarntee to spawn on the bottom lane and vice versa then clear the array for the next set of cars.

The collison with the cars will only be activated when it comes into contact with the player mesh and will ignore all other items and objects in the game. This is so that the car can apply damage to the player and enable hit stun and hit stop the player.\

The headlights are built with Unreal Engine 5 cone line with high intensity.


<h1>Garbage Truck</h1>

<h3>Similar to the cars, the garbage truck will have the same functionality as the cars but will only appear during an event and will dump out scraps onto the road. I added rotating caution lights and headlight to the garbage truck.</h3>

The only difference between the garbage truck and the cars is that it has to dump out scraps at the rear. This is done with an event track timeline that will trigger scrap spawn at the end of the garbage truck. Also when the garbage is about to spawn, all cars are disable and will not spawn until the garbage truck event has ended.

