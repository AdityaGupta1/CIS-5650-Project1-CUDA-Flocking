**University of Pennsylvania, CIS 565: GPU Programming and Architecture,
Project 1 - Flocking**

* Aditya Gupta
  * [GitHub](https://github.com/AdityaGupta1), [LinkedIn](https://www.linkedin.com/in/aditya-gupta1/), [3D renders](https://www.instagram.com/sdojhaus/)
* Tested on: Windows 10, i7-10750H @ 2.60GHz 16GB, NVIDIA GeForce RTX 2070 8GB (personal laptop)
  * Compute capability: 7.5

## Introduction

*Boids* is a simulation in which particles representing birds or fish (boids) move around the simulation space according to three rules:

1. *cohesion* - Boids move towards the perceived center of mass of their neighbors.
2. *separation* - Boids avoid getting to close to their neighbors.
3. *alignment* - Boids generally try to move with the same direction and speed as their neighbors.

Some example simulations:

|![](images/captures/5k.gif)|
|:--:|
|*5,000 boids*|

|![](images/captures/50k.gif)|
|:--:|
|*50,000 boids*|

|![](images/captures/500k.gif)|
|:--:|
|*500,000 boids*|

## Implementation and Performance

A naive implementation could have each boid check every other boid to determine its new velocity, for which the runtime increases exponentially. Especially on the CPU, this quickly leads to severe performance limitations. However, optimizations can be made:

- Using the GPU allows for significant parallelization, which confers a massive speedup by itself.
- Constructing a uniform grid data structure reduces each boid's neighbor checks from O(n) to O(1).
- Rearranging buffer layouts for more contiguous memory access further increases performance.

### (TODO: performance, graphs, etc.)