---
layout: default
---

# Worhol

this games was a 3 person game jam built for UCI's Summer game jam as well as Extra Credit's 
Awesome Per Second game jam. [This ](https://github.com/GDFauxtrot/AwesomePerSecond)is the original git repo from the jam, and [here](https://github.com/Ittaimann/Worhol) is a forked one on my personal github account for me to fix a couple things.

*image of game*
![alt](https://ittaimann.github.io/Capture.png)



The original concept for the game was rolling around a museum destroying as many pieces as possible. Meaning we had to implement a quick way to destroy museum object as well as make proper feedback for rolling and smashing said objects.

Finding a way to mas create destructible objects was our initial big hurdle given to me. Initial ideas were implementing gpu based voxel destruction such and gpu based physics such as the one in [Nvidia's GPU gems 3](https://developer.nvidia.com/gpugems/GPUGems3/gpugems3_ch29.html). However we found that there really wasn't enough time for a game jam, so we opted instead to use blenders cell fracture tool. This let us quickly split up models and generate multiple meshes that we could then apply physics to. Suprisingly could actually handle most of the physics calculations well enough and we just cell fractured any model we wanted in the game.

Next was making sure that smashing and moving was fun. Rolling a marble around can be fun, but we definitly felt like we could make it better have a better sense of speed. To do this, I wrote a shader to do vertex animation that could stretch out our rolling sphere opposite of the direction the player would move. I did this by passing the sphere's velocity vector into the shader and checking the spheres normals and velocity via dot product. Based on the direction I started to slowly refined the animation until I could put it in the game.

Another thing we wanted is for our smash to look visually strong. In my mind our sphere wouldn't cause an explosion or anything but needed to have a visual effect. I decided to try and create a distortion wave originating from where our character would smash into the ground. I initially just did a grab pass and add perlin noise to the resulting texture, but found it really disoreting. Players rolling into it would lose the ability to see the player charater. To remedy that, I created a fresnel shader, and would only add noise where the rim would begin, keeping our player clear in sight.

Finally we really wanted to make the game look good. A mueseum has a very particular look that works really well for reflections and nice lighting, so I added unity's post processing effects onto the game, though I may have gone to far on some of it. 