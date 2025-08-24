# Jump Storage (aka GlideJump)
These are my observations around GlideJumps and similar interactions in Ori and the Will of the Wisps.
**The information here has not been verified by anyone else, so take everything with a grain of salt**
<img src="https://raw.githubusercontent.com/ori-community/wiki/refs/heads/main/assets/images/ori_shrug.png" alt="Alt Text" width="20" height="20">

# What is Jump Storage
Jump Storage is what I've decided to call a group of interactions that allow Ori to jump mid-air without
the need for a Double Jump. In the community, these are more commonly known as GlideJumps because most of
the time you would be using Glide to achieve Jump Storage and move around while keeping it active.

![Standing Glide Jump](/assets/StandingGlideJump.gif)

## What makes Jump Storage possible
Let's imagine that the game engine gives Ori a property called `onGround`.
  - This property is `True` whenever Ori is standing or walking on solid ground.
  - This property is `False` whenever Ori is in the air (because the player jumped, ran off a ledge, got knocked back, used an ability that lifts Ori up, ...).

Let's then say that the game engine allows Ori to perform the basic jump whenever `onGround` is `True`,
and additional double jumps when `onGround` is `False` and the player has leftover jumps.
If the player has no extra jumps, Ori cannot jump mid-air.

The different ways to achieve Jump Storage manage to trick the game engine into thinking that `onGround`
is `True` even when Ori is not standing on solid ground. This allows the player to jump once mid-air
(using the basic jump) before the game realizes that Ori is actually in the air.

## How to store a jump

The difficult part about tricking the game engine into thinking that Ori is still on the ground is figuring
out *when* the game engine decides that you're no longer touching the ground. These are the known methods
that allow you to go airborne without actually updating Ori:

1. Holding down **Glide** before jumping.
2. Holding down **Glide** *right after* jumping, while moving. This one is weird.
3. Holding down **Glide** when walking off a ledge.
4. Throwing out a **Spike** (Spear), until Ori finishes turning around.
5. **Bash**ing an enemy that's *not too far** above the ground. 
6. Using **Water Dash**** while standing on ground.
7. Using **Burrow**** while standing on ground.

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
Make sure you hold down Glide when you want to exit into the air again.
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


### Jumping and Coyote Time

The jump off a stored jump should be a frame-perfect trick because the game engine updates the grounded status on the
same frame as you release Glide. However, Ori and the Will of the Wisps has [Coyote frames](https://en.wiktionary.org/wiki/coyote_time).

In the following GIF, Ori is jumping just *after* walking off the edge. But it's within the coyote time so the jump goes through. 

![Coyote Frames Jump](/assets/CoyoteJump.gif)

This mechanic allows players to jump during a couple of frames right after walking off a ledge.
In the case of Jump Storage, this acts in the same way: The engine thinks Ori just walked off a
ledge because it lost the grounded property and is now airborne.

