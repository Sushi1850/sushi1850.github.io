---
layout: projectInformation
title:  "Trash Pandamonium"
summary: "My contribution to Trash Pandamonium"
thumbnail: /assets/img/posts/TPBoxArt.png
permalink: /projects/TrashPandamonium/
---

This project was built with Unreal Engine 5 (Blueprints), click <a href="https://store.steampowered.com/app/2900780/Trash_Pandamonium/" target="_blank">here</a> to check out trash pandamonium on steam!!!<br>

Check out the trailer!!!
<iframe width="300" height="200"
src="https://www.youtube.com/embed/fw-PuQP9USE">
</iframe>

<h1>Respawn</h1>

<h3>When a player falls off the platform, the player will be translated upwards and towards a respawn point. Later on, I implemented a seagull that would spawn, pick up the player, rotate towards the respawn point, fly over to the respawn point, drop the player off, and fly upwards afterward.</h3>

The way I implemented this functionality is that whenever a player touches an out-of-bounds barrier, the player will lose the ability to input any buttons except the pause button by overriding the input mapping of the player. Next, I use two float timelines, one for translating the player upwards, which is just the respawn point with a higher y-axis, and the other to translate the player to the respawn point while keeping the higher y-axis. Afterwards, the player will be dropped onto the field and will be able to use input again.

The seagull works similar to the player but with a slightly higher y-axis, so that the seagull will appear above the player. When a player falls off, the seagull will spawn to the left of the player and will fly downward. This is done by using a float timeline that will translate the seagull from the spawn location to the player location. Once it reaches the player, the seagull will rotate and face the respawn point, then move towards the respawn point. After the seagull has translated to the respawn point, it will rotate upward while heading towards its forward vector to simulate it flying away.

<html>
    <body>
        <video width="300" height="200" controls>
            <source src="../../assets/video/Respawn.mp4" type="video/mp4">
        </video>
    </body>
</html>
<br><br>

<h1>Cars</h1>

<h3>In the cityscape map only, cars will spawn outside of the map, drive across the city, and despawn after the timeline has ended. The car has collision detection with the player and will apply hit-stun and stop to the vehicle and the player. I added headlights to the cars to give them more detail. Lastly, I implemented an algorithm where the cars will only spawn up to twice per lane before switching lanes and having the car spawn in the other lane.</h3>

With the cars, I used a float timeline to translate it across the road with a fixed starting location and end location. I was able to spawn the cars from an event track timeline, which will randomly spawn the cars either in the top or bottom lane. The algorithm that I used to only allow two cars to spawn on a lane before switching to the other lane is that whenever a car spawns on a specific lane, it will store this knowledge in an array. Once the array reaches the limit per car that can spawn continuously, it will check all the knowledge of the past vehicle to see which lane it has spawned in. If all of the cars spawn on the top lane, then the next car will guarantee to spawn on the bottom lane, and vice versa, then clear the array for the next set of cars.

The collision with the cars will only be activated when it comes into contact with the player mesh and will ignore all other items and objects in the game. This is so that the car can apply damage to the player and enable hit stun and hit stop. Also, the headlights are built with an Unreal Engine 5 cone light with high intensity.

<html>
    <body>
        <video width="300" height="200" controls>
            <source src="../../assets/video/Cars.mp4" type="video/mp4">
        </video>
    </body>
</html>
<br><br>

<h1>Garbage Truck</h1>

<h3>Similar to the cars, the garbage truck will have the same functionality as the cars but will only appear during an event and will dump out scraps onto the road. I added rotating caution lights and a headlight to the garbage truck.</h3>

The only difference between the garbage truck and the cars is that it has to dump out scraps at the rear. This is done with an event track timeline that will trigger scrap spawn at the end of the garbage truck. Also when the garbage is about to spawn, all cars are disabled and will not spawn until the garbage truck event has ended.

<html>
    <body>
        <video width="300" height="200" controls>
            <source src="../../assets/video/GarbageTruck.mp4" type="video/mp4">
        </video>
    </body>
</html>
<br><br>

<h1>Hit Stop and Hit Stun</h1>

<h3>This functionality will only be triggered with any damage towards a player such as vehicles, other players, and any objects that inflict damage</h3>

For the hit stop, I used two functions: start hit stop and end hit stop. When a player takes damage, it triggers a hit stop immediately, which will freeze the player with player time dilation by setting it to 0, and it will also call the end hit stop with a set timer by function name, where it will call the function after a timer has reached 0. In the end hit stop, it will change the time dilation back to 1, which will unfreeze the player and allow the player to move again.

<html>
    <body>
        <video width="300" height="200" controls>
            <source src="../../assets/video/HitStopAndHitStun.mp4" type="video/mp4">
        </video>
    </body>
</html>
<br><br>

<h1>Hexagon Boost Pad</h1>

<h3>This is a hexagon pad that will accomulate the player progress and will reward the player scraps when the pad reaches 100%</h3>

This boost pad will record the progress of a player when coming into contact with the pad uncontested. I used Unreal Engine 5 collision detection to detect when the player comes into contact with the pad. I used an array to keep track of which player in on the pad and use a float track timeline to handle the progress bar. The progress of the pad will only increase if the player is the only one standing on it. If another player makes contact with the pad then the progress will be in contest mode. If the other player leaves, the progress will continue, else they will be in a contest state until one player leaves. If the player holding the zone leaves, the progress will slowly decrease until none is left then will calculate the progress for the player that stands on the pad.

<html>
    <body>
        <video width="300" height="200" controls>
            <source src="../../assets/video/BoostPad.mp4" type="video/mp4">
        </video>
    </body>
</html>
<br><br>

<h1>Urchin Item</h1>

<h3>This pickupable item only spawns in the beach map. The urchin will expand upon contact when thrown onto a surface and will damage player when in range</h3>

The urchin item has a small chance to spawn within the scrap on the beach. This item will be the color blue and can be picked up by a player, simply by coming into contact with it. When pickup, the item will appear on the raccoon's hand to show the player that they can throw an urchin. When thrown, the urchin will detect any objects that come into contact. Once it comes into contact with any object, the urchin will expand and change color to red and will inflict any damage on the player when touched.

<html>
    <body>
        <video width="300" height="200" controls>
            <source src="../../assets/video/UrchinItem.mp4" type="video/mp4">
        </video>
    </body>
</html>
<br><br>

<h1>Interactive Objects</h1>

<h3>Here are some interactive objects that I made: Cactus spikes and a beach ball</h3>

Cactus spikes are triggered when any player attacks a cactus. I paired-program with another programmer and we decided to use the player that attacked the cactus forward vector to spawn the spikes and allow it to travel at a constant velocity for a short time before despawning. The cactus will only be on the mesa map.

Lastly, a beach ball that will be launch upwards by vector calculation of the player to simulate a beach ball having physics when attacked. It will only spawn on the beach map.

<html>
    <body>
        <video width="300" height="200" controls>
            <source src="../../assets/video/InteractiveObjects.mp4" type="video/mp4">
        </video>
    </body>
</html>
<br><br>

<h1>Player Swap Event</h1>

<h3>In the mesa map, there is a slight chance for an event that will swap player locations randomly</h3>

I implemented the player swap by adding each character location into an array and randomizing it. Once it is randomized, I would pick the first index of the array and check if it is the current location of the player, if it is then pick the next element in the array, otherwise set that to the new location where the player will be teleported to and remove it from the list.

<html>
    <body>
        <video width="300" height="200" controls>
            <source src="../../assets/video/PlayerSwapEvent.mp4" type="video/mp4">
        </video>
    </body>
</html>
<br><br>

<h1>Other Contributions</h1>

Other contributions that I made for the game that were changed includes: Dens, Input Mapping for Controllers, Dash, Movement.