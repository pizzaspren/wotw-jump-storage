# Jump Storage
These are my observations around GlideJumps and similar interactions in Ori and the Will of the Wisps.
**The information here has not been verified by anyone else, so take everything with a grain of salt**
<img src="https://raw.githubusercontent.com/ori-community/wiki/refs/heads/main/assets/images/ori_shrug.png" alt="Alt Text" width="20" height="20">

# What is Jump Storage
Jump Storage refers to an interaction between abilities that allows Ori to jump mid-air even without Double Jump.
In that sense, you are "storing" the basic jump to use at a later point in time.

![Jump storage example](/assets/LedgeGlideJump.gif)

## First things first

### Jumping

Ori is only allowed to perform the basic jump in three situations:
* Ori is standing on solid ground.
* Ori is falling down and still has [Coyote time](https://en.wiktionary.org/wiki/coyote_time) remaining. Also known as a Coyote Jump.
* Ori is treading water on the surface.

### Coyote jumps

Ori and the Will of the Wisps has 0.2 seconds of Coyote time, meaning that players can still jump during a few
frames right after walking off a ledge. 

In the following GIF, Ori is jumping *just after* walking off the edge. But it's within the 0.2s coyote time so
the jump goes through. 

![Coyote Frames Jump](/assets/CoyoteJump.gif)

To be more specific, the remaining coyote time is decreased on every frame. The code in charge of jump logic
resets it to the default value of 0.2 seconds on every frame, as long as Ori is standing on solid ground.
This is important for Jump Storage.

### Water jumps

This kind of jump is a bit peculiar; Ori is allowed to jump out of the water but it does not refresh the coyote
time.

*(Work in Progress)* 

# What makes Jump Storage possible

All the Jump Storage setups so far follow the same approach:

1. Refresh the coyote time by standing on solid ground.
2. *(Unconfirmed)* Pause the jump logic while Ori still has coyote time remaining.
    * This can be a single step or a combination of steps.
    * *(Unconfirmed)* All known setups also disable jumping altogether, maybe as the cause or the consequence of pausing the jump logic.
3. Move Ori to a desired airborne position, with Ori starting to fall down.
4. *(Unconfirmed)* Unpause the jump logic.
5. Perform a coyote jump within the remaining coyote time.

In summary, the setups are pausing the coyote time being decreased in exchange for not being able to jump.
Once Ori has reached the desired position, jumps are re-enabled and a coyote jump is performed.


## Known ways to store a jump

For a full list of known setups and step-by-step guides, read [the examples page](/Jump_Storage_Examples.md).

1. Using **Glide**.
    * Hold down **Glide** before walking off a ledge.
    * Hold down **Glide** before jumping.
    * While moving sideways, jump and hold down **Glide** before the coyote frames expire.
2. Using **Spike** (Spear).
    * The jump is stored until Ori finishes turning around. Roughly after the spear starts traveling.
3. Using **Bash**.
    * Holding **Bash** on enemies that are small and on the ground does not update coyote frames.
    * Tall enemies like Gorlek Miners can still be bashed if Ori is mostly centered beneath them. However, this requires taking contact damage.
4. Use **Water Dash** to go into water while standing on ground.
    * The game won't update the coyote frames until you leave the water.
5. Use **Burrow** to go into sand while standing on ground.
    * The game won't update the coyote frames until you leave the sand.

## Moving around with a stored jump

If you're storing a jump for later, you will probably want to reach a state where Ori is slowly gliding down.
Because you can't jump in water nor sand, you will eventually have to be in the air to use the jump.

***Landing on the ground or touching any walls while Gliding will immediately cancel your stored jump.***

That being said, you have several options for moving Ori while 

* In air you must hold **Glide** until you want to use the stored jump. This is the only known way so far to keep the stored jump for a long time. Additionally, you can also use the following abilities *while holding Glide*.
    * Spear (Spike).
    * Grenade (Light Burst).
    * Flap.
    * Blaze.
    * Flash.
    * Sentry.
* In water, you can do whatever you want as long as you don't leave water.
    * To go into air for the jump, you must first hold **Glide** and exit the water using **WaterDash**. 
* In sand, you can do whatever you want as long as you don't leave sand.
    * To go into air for the jump, you must first hold **Glide** and exit the sand.
    * If you are leaving sand by going up, you will need to use **Burrow** to go high above the ground. This prevents Ori from standing on the ground right away and ruining your stored jump.
    * If you are leaving sand by going down, you don't need anything special. 


## Using the stored jump

Using the stored jump is the same as doing a Coyote Jump. However, instead of running off a ledge you will
*usually* be releasing **Glide** once Ori is slowly gliding down. As a reminder, you can perform a coyote
jump when Ori is falling down and you still have coyote frames available.

1. Slowly glide down. 
2. Release **Glide**.
3. Press **Jump** before your coyote frames expire.

If you managed to preserve the stored jump and you time the jump correctly, Ori will perform a basic jump
mid-air.

![Jump storage example](/assets/LedgeGlideJump.gif)

If you fail to initially store the jump, lose the jump storage along the way, or mistime the exit jump:
   * If you don't have any extra jumps (Double Jump, Triple Jump, ...), Ori will fall down normally.
   * If you have extra jumps, Ori will curl into a ball and use one of the extra jumps.

![Failed Glide Jump with double jump](/assets/FailedGlideJump.gif)
