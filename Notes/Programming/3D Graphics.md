Computers can generate images which look 3D, but in reality, are only *two dimensional images* which are drawn on your monitor. How do computers do that?
# Basics
Most programs define objects as a *list of triangles*. You can create a cube out of *several smaller triangles.* For example, we can draw a *rectangle* by drawing *two triangles next to each other*.

Most programs utilize your GPU (Graphics Processing Unit) to draw the triangles.
- You can write programs which utilize the CPU (Central Processing Unit) to draw onto the screen. This is not the best approach, since the GPU is designed for that sole purpose.
- The original DOOM (1993) used Software Rendering to draw the world.

Using SDL, we can define points, lines, and triangles to draw object onto the screen. This will use the CPU.
- If we want to utilize the GPU, we will have to use a graphics library, like OpenGL or Vulkan
	- OpenGL is more beginner friendly (more functions, large backlog of projects, more documentation), but Vulkan gives you more freedom to optimize and design the whole rendering pipeline.

## Mathematical background
We want to describe our objects as a list of triangles. We will use vectors to define the points on the screen. We will use vector arithmetic to move the points in world space, and use matrix multiplication to project the points onto the screen.

### Points
A *triangle* is made up of three *points*. Let us define a simple triangle.
We first need the three points. Let them be $A, B,$ and $C$.
Since we want to make a 3D graphics engine, all of our points will be in three dimensional space; they will have three coordinates, like:

$$A = (a_1, a_2, a_3)$$
But, for demonstration purposes, let's just look at a triangle in 2D space.
Our triangle will be $T_{ABC}$, where:
$$A=(1,1),B=(5, 2),C=(2,4)$$
![[Screenshot from 2025-11-28 14-55-44.png]]We can easily draw this triangle on a piece of paper, or in a program like "Geogebra".

Drawing a rectangle, as we have discussed, can be achieved by defining two triangles.
Our rectangle will be: $R = (T_A,T_B)$, where the triangles' poin[ts are defined in a counter-clockwise fashion. $T_A = (A,B,C), T_B = (B,C,D).$
![[Screenshot from 2025-11-28 16-15-25.png]]
The way in which we define the points is important. We will look at that problem later.
### Vectors
When we talk about *vectors*, some people picture an *arrow* going from one point to another.
In reality, a *vector* can be defined by just a single *point.* The vector has the same number of coordinates as the point it is pointing at.
We formally define a vector by its coordinates:
$$\displaystyle \underline{v}=(p_1, p_2, \dots, p_n)$$
, where $n$ is the number of dimensions.
A three dimensional vector would look like this: $\underline{v} = (p_1, p_2, p_3).$

In our example image, the point $A$ defines a two dimensional vector, let us call it $\underline{a}$.
![[Screenshot from 2025-11-28 16-27-11.png]]
So this vector would be:
$$
\textbf{a} = \underline{a} = (2,1) = 
\begin{pmatrix}
2
\\
1
\end{pmatrix}
$$
_Note: we can also write the vector in $\textbf{bold}$, and describe the coordinates in a column vector._
