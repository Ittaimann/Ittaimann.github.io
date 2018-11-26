---
layout: default
---

# Crackers and Cheese

[Here is the Repo](https://github.com/Ittaimann/crackers-and-cheese)

This was another game for a class called multiplayer game systems, which let us make any multiplayer games we wanted as long as they were multiplayer. The idea for this one was a take on a ps2 game called Cookies and Cream where two players would run through a level cooperatively.

I primarily wanted to work on shader work for this and wanted to mimic an effect that I had seen in a TV show called Chowder. The idea is that textures would be maped via screen space and not on the model themselves, so it would look like they had been cut out or that the colors and texture were on a seperate layer.

Initially this shader was done via a vertex shader where I would just slap the texture in screen space onto the model. The problem is that its a 3d game and having no shadows or ligthing made it hard to judge the distance while platforming. I then switched to using a surface shader which is Unity's way of giving a lot of the lighting and metallic attriubtes directly in the shader easily. So I gave it a lambert lighting surface (given by unity). Now the cutout texture looked to dark, the shadows don't make the pattern pop. To fix that I used the emission attribute in the surface shader and there, there is shadows and the texture pops. When the player moved the texture underneath moved seperatly and I pretty much got the exact effect I wanted. 