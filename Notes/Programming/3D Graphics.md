Computers can generate images which look 3D, but in reality, are only two dimensional images which are drawn on your monitor. How do computers do that?

# Basics

Most programs define objects as a list of triangles. You can create a cube out of several smaller triangles. For example, we can draw a rectangle by drawing two triangles next to each other.

Most programs utilize your GPU (Graphics Processing Unit) to draw the triangles.
- You can write programs which utilize the CPU (Central Processing Unit) to draw onto the screen. This is not the best approach, since the GPU is designed for that sole purpose.
- The original DOOM (1993) used Software Rendering to draw the world.

Using SDL, we can define points, lines, and triangles to draw object onto the screen. This will use the CPU.
- If we want to utilize the GPU, we will have to use a graphics library, like OpenGL or Vulkan
	- OpenGL is more beginner friendly (more functions, large backlog of projects, more documentation), but Vulkan gives you more freedom to optimize and design the whole rendering pipeline.

## Mathematical background
We want to describe our objects as a list of triangles. We will use vectors to define the points on the screen. We will use vector arithmetic to move the points in world space, and use matrix multiplication to project the points onto the screen.

### Points
A triangle is made up of three points. Let us define a simple triangle.
We first need the three points. Let them be $A, B,$ and $C$.
Since we want to make a 3D graphics engine, all of our points will be in three dimensional space; they will have three coordinates, like:

$$A = (a_1, a_2, a_3)$$
But, for demonstration purposes, let's just look at a triangle in 2D space.
Our triangle will be $T_{ABC}$, where:
$$A=(1,1),B=(5, 2),C=(2,4)$$
![[Screenshot from 2025-11-28 14-55-44.png]]We can easily draw this triangle on a piece of paper, or in a program like "Geogebra".