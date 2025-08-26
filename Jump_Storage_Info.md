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

## What makes Jump Storage possible

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

1. Hold down **Glide** before walking off a ledge.
2. Hold down **Glide** before jumping.
3. While moving sideways, jump and hold down **Glide** before the coyote frames expire.
4. Throw out a **Spike** (Spear), until Ori finishes turning around.
5. **Bash** an enemy that's *not too far** above the ground. 
6. Use **Water Dash**** while standing on ground.
7. Use **Burrow**** while standing on ground.

# WIP below this line

*This is difficult to judge. It depends on how far off the ground Ori is while bashing. Basically, if
the enemy is small and you are both on the ground you're good. For tall enemies like Gorleks you need
to be directly beneath the center point of the enemy, which means you need to take contact damage.

**The game engine doesn't care about updating your grounded status while you're in water or in sand.
Therefore, as long as you enter water or sand while the engine thinks you're grounded you can move around
freely without losing the grounded status.

## Moving around with a stored jump

You can use the following abilities while holding down **Glide** without losing the stored jump:
* Spear (Spike)
* Grenade (Light Burst)
* Flap
* Blaze
* Flash
* Sentry

In water and in sand you can use anything and nothing, since the game won't update your status regardless.
Make sure you hold down Glide before going into the air again, as you will lose the grounded status
as soon as you exit to the surface. On water you can also safely tread the surface without losing the
jump storage.
* Water Dash
* Bash (in water, because you can't bash in sand)
* Burrow

## How to use a stored jump

At any point after the peak of the jump, release the **Glide** button and *immediately* press **Jump**.
If you timed it correctly, Ori will jump with the same animation as a basic jump.

If you have multiple jumps and see Ori curl into a ball, you either lost the jump storage or mistimed the
exit jump.

Successful:

![Standing Glide Jump](/assets/StandingGlideJump.gif)

Failed:

![Failed Standing Glide Jump](/assets/StandingGlideJump_Failed.gif)



