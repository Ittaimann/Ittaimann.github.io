---
layout: default
---

# GPU based fire

[Link to the repo](https://github.com/Ittaimann/GPU_Fire)

This one was so much fun. My project in advanced graphics class allowed us to choose whatever we wanted for our final project and my team were between a geometry shader or a computer shader inside of unity.

Getting information on a computer shader (especially for particle physics) was much more difficult than I expeceted, there was one blog a lot of people online would point to that had been taken down maybe a year before this project so I hit a lot of initial dead ends. Eventually I found a github repo that I had to disect in order to understand the CPU and GPU side code and communication

Essentially you need to create a buffer of structs that gets passed into a kernel function for the GPU. From there you also need to create a proper shader to render the particle  that also has access to the buffer for information.

I would spawn in 256 particles per frame based on verticies on a sphere and experimented a lot. occluding back facing particles, using different kinds of GPU side noise, different colors based on position, and just generally how far we could push the particles.

On the GPU side we would Essentially spawn in particles and have them move up (because thats what fire does) along with movement on the x and y axis based on some noise functions. Initially I liked the simplex noise look, but ultimatley went with 3d perlin noise which looked a bit more realistic. The noise was GPU side generated as I didn't want to worry about a cpu bottle neck, and the code was pulled from an outside repo. The frustrating part was that a week later I actually found a proper tutorial on generating deterministic random numbers on a gpu.

After all that, I just kept experimenting with numbers until we felt like the fire actually looked pretty good. I was extremely happy with how this project turned out and its been by far my favorite graphics class project.