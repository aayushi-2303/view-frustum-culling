# View Frustum Based Culling

A video demo of FPS gains from view-frustum based culling, implemented on top of Prime Engine for Csci522 - Game Engine Development, at the University of Southern California. The video can also be accessed using this link:

https://youtu.be/FUnLHhv-rFY

## Project description

The goal of this project was to implement vertex culling based on the view-frustum of the camera, using Axis-Aligned Bounding Box collision tests. The source code for the Engine is under copyright and thus unable to be distributed, so I have enclosed a video to demonstrate the resulting FPS gains.

This project involved several working parts. The first step was to create and visualize a bounding box around the meshes. This involved finding the min and max x,y,z coordinates of the Imrod mesh and defining the edges of the box using those. These coordinates also had to be converted from model space to world space using the matrix transformation with the world matrix. Visualizing these boxes was a function call to a simple line renderer, and can be seen in the video as the red lines surrounding the meshes.

The second part was to build plane equations based on camera transforms and camera FOV. I extracted the plane coefficients from the world-view projection matrices based on an article by Gil Gribb and Klaus Hartmann from the University of Otago (article referenced below).

The third and most important part is the actual collision test. This was fairly simple once the plane equations had been built and the AABB points defined in world space - all it took was checking the AABB edge points and testing which side of each of the 6 planes they were on by checking the D value of the plane equation. If all of the edge points are outside the bounding box, the mesh is not in the FOV of the camera and subsequently culled out.

## Built With

* [PrimeEngine](https://sites.google.com/site/artemscode/home) - Many thanks to Artem Kovalovs, instructor of Csci522 for allowing us to build on top of his engine
* C++

## Acknowledgments 

* Many thanks to Gil Gribb and Klaus Hartmann, authors of [this article](http://www.cs.otago.ac.nz/postgrads/alexis/planeExtraction.pdf) from the University of Otago for essential information regarding extraction of plane coefficients.
