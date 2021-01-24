# Quick and dirty guide to Poiyomi Pro Dissolve Anim Sliders

## Keep in mind, this shader package changes frequently, so the way this works may end up changing in the near future, but the capability will almost certainly remain.

**The version used here is 7.0.81 with unity 2018 (for VRChat).**

![](https://i.gyazo.com/f4469f6db357a694b64f0655c584ceca.png)

## TLDR:  

### Shaders effect the entire mesh, but the "clock" icon in the shader UI acts as a mask for animating individual materials.

---

In the demonstration, we're using 4 materials that make up this avatar's outfit but you can use all 10 sliders.

Reminder before you start, make sure the rendering preset is on "Cutout" or this won't work at all.

![](https://i.gyazo.com/3b5a0d184febec873db8573fecfa4400.png)

The way this works is each "Dissolve Alpha" slider goes from -1 to 1.

Depending on what the initial "Dissolve Alpha" value is for that material, you can have a variety of outfit combinations on your mesh.

Keep in mind, the magic doesn't happen until you "Lock in the shader" at the very top, so you can't really test any animations until after you mark each material's slider to animate, (so you might want to just start with 1 or 2 materials to make sure you're doing it right).

*LOCK IN TO SEE ANIMATIONS
![](https://i.gyazo.com/803772d58bb46aea049784d3ee14816d.png)

Here's what I mean.
All 4 materials unlocked, *even with the clock on the sliders nothing happens on the animation clip:

![](https://i.gyazo.com/25e4ac4355aab021781da3f1459caf45.png)

Locked the hoodie, it dissappears:

![](https://i.gyazo.com/0d4c610680dba85a0aee9daef7a7ead8.png)

Locked the tank top, it now appears:

![](https://i.gyazo.com/c36a445c853530fc454629756afe75a8.png)

Also note that if a material's dissolve starts at 0, then sliding into negative territory has no effect.  
-- The negative values are for when a material's initial dissolve value is positive.

In my example here, I have a top and bottom that I want to dissolve and undissolve together so I set their dissolve alpha to 0 and 1, respectively.

The other default dissolve setting you'll want to configure is the "Dissolved Color," which must be set to Alpha = 0 using the color picker if you want it to be fully transparent but can be whatever you want.

![](https://i.gyazo.com/c505688434a9997ad5169f915b15ccd4.png)

The main "Dissolve Alpha" slider is set to 0 on the Hoodie and Sweats materials and 1 on the hidden materials (in this case "tank top" and "low rise").

Next, you'll want animate these properties like you normally would. 

Set the Dissolve Alphas between -1 and 1 in your keyframes and you're good to go!

Protip: if you happen to be new to animating in unity, like I was when starting this you'll find out you can't copy/paste the properties into a new animation clip, but you can duplicate each clip, **then drag them** onto your test avatar in the scene.

When you're adding the Dissolve Alpha Properties you'll notice that some say "ANIMATED" - don't touch those, they're used by the compiled shader during optimization.

![](https://i.gyazo.com/ebb82d06e229620eef6bfa37bf547122.png)

Don't forget to right-click each slider on each material so the 'clock icon appears.'  

If you're new to poiyomi Pro, please note that you absolutely have to use the "Lock-in optimized shader" for the animations to work properly in game, NOT TO MENTION, locking in builds a highly optimized shader, which benefits everyone who sees it.

That's it!  You can experiment with this in all kinds of ways, such as dissolving between colors or hiding accessories.
