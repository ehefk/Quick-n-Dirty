# Quick and dirty guide to Poiyomi Pro Dissolve Anim Sliders

## Why? Because having lots of meshes is far more of a resource hog than just a bunch of materials.  These shaders are highly optimized and you'll save everyone some frames.

### (Keep in mind, this shader package gets frequent updates, so the way this works may end up changing in the near future, but the capability will almost certainly remain, and I'll try to keep this page up-to-date.  It will probably get shorter and easier)

**The version used here is 7.0.81 with unity 2018 (for VRChat).**

![](https://i.gyazo.com/f4469f6db357a694b64f0655c584ceca.png)

## TLDR:  

### Shaders effect the entire mesh, but the "clock" icon in the shader UI acts as a mask for animating individual materials.

---

In the demonstration, we're using 4 materials that make up this avatar's outfit but you can use all 10 sliders.

Reminder before you start, make sure the rendering preset is on "Cutout" or this won't work at all.

![](https://i.gyazo.com/954c596c2fb1196c5c81c7179471d244.png)

The way this works is each "Dissolve Alpha" slider goes from -1 to 1.

![](https://i.gyazo.com/6498d77420409f161efb0c72309af212.png)

Depending on what the initial "Dissolve Alpha" value is for that material, you can have a variety of outfit combinations on your mesh.

![](https://i.gyazo.com/4d7d10df91c98ce34c91f124ce15bb90.png)

Keep in mind, the magic doesn't happen until you "Lock in the shader" at the very top, and **you can't test any animations until after you mark each material's slider to animate,** (so you might want to start with only 2 or 3 materials to make sure you're doing it right).

*LOCK IN TO SEE ANIMATIONS*
![](https://i.gyazo.com/02c3fa20ef4ce344f06327f2f7a0ad15.png)

Here's what I mean.
All 4 materials unlocked, *even with the clock on the sliders nothing happens on the animation clip:

![](https://i.gyazo.com/2df1472d31dd8a1724e634dd7e407852.png)

Locked the hoodie, it dissappears:

![](https://i.gyazo.com/fbf08eded053d4f215705a452c0a50b7.png)

Locked the tank top, it now appears:

![](https://i.gyazo.com/a80556c0ec791ad08d56fbde3fc45eb1.png)

Also note that if a material's dissolve starts at 0, then sliding into negative territory has no effect.  
-- The negative values are for when a material's initial "dissolve alpha" is positive.

In my example here, I have a top and bottom that I want to dissolve and undissolve together so I set their initial "dissolve alpha" to 0 and 1, respectively.

The other default dissolve setting you'll want to configure is the "Dissolved Color," which must be set to Alpha = 0 using the color picker if you want it to be fully transparent but can be whatever you want.

![](https://i.gyazo.com/63008823a24f07df89757f71158a2ac7.png)

In my above example, the main "Dissolve Alpha" slider is set to 0 on the AnimeHoodie and AnimeSweats materials and 1 on the hidden materials (in this case the tanktop and lowrise).

Animate these properties like you normally would, setting the Dissolve Alphas between -1 and 1 in your keyframes and you're good to go!

Protip: if you happen to be new to animating in unity, like I was when starting this you'll find out you can't copy/paste the properties into a new animation clip, but you can duplicate each clip, **then drag each one** onto your test avatar in the scene for testing.

When you're adding the Dissolve Alpha Properties you'll notice that some say "ANIMATED" - don't touch those, they're used by the compiled shader during optimization.

![](https://i.gyazo.com/ebb82d06e229620eef6bfa37bf547122.png)

Don't forget to right-click the desired slider for each material to use.  You should have 1 clock on each material.  

![](https://i.gyazo.com/cb0b21d67eeedaa7d1f3c12bfd275cda.png)

If you're new to poiyomi Pro, please note that you absolutely have to use the "Lock-in optimized shader" for the animations to work properly in game, NOT TO MENTION, locking in builds a highly optimized shader for each material, which benefits everyone who sees it.

That's it!  You can experiment with this in all kinds of ways, such as dissolving between colors or hiding accessories.
