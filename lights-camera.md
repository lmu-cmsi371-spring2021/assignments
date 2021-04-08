**CMSI 371** Computer Graphics, Spring 2021

# Assignment 0420
This assignment seeks to wrap up the single-frame visual/rendering aspects of your 3D scene.

## Background Reading
As one might expect, the [Shirley/Marscher](https://brightspace.lmu.edu/d2l/le/content/130175/viewContent/1411955/View) text continues to be our go-to source for theoretical and mathematical material. Specific to this assignment, you might find these useful:
* _Chapter 2: Miscellaneous Math_ Section 2.4.4 describes the _cross product_ in detail
* _Chapter 7: Viewing_ talks about projection and the camera
* _Chapter 20: Light_ and _Chapter 24: Global Illumination_ have additional detailed background on lighting

For cross product, the operation itself has been implemented for you in the already-provided `Vector` class. What you want to do is use that function at the right time with the right values.

Closer to the code, [Real-Time 3D Graphics with WebGL 2](https://brightspace.lmu.edu/d2l/le/content/130175/viewContent/1411963/View) has multiple points of interest as well:
* _Projection Transform_ and _Perspective Division_ talk about the concepts behind projection, with _The Projection Matrix_ and successive sections walking you through the authors’ own approach to a matrix library and implementing projection
* _The Camera Matrix_ and succeeding sections provide a similar walk-through, but for “cameras”
* Finally, the _Lights_ section spells out how to implement lighting in the shaders. As a bonus, you get additional review on GLSL and more conceptual reinforcement of how computer systems model/handle lighting

Depending on what style works better for you, [GLSL Essentials](https://brightspace.lmu.edu/d2l/le/content/130175/viewContent/1411966/View) has equivalents to these as well, emphasizing GLSL rather than mathematics (which is assumed to be understood by the reader—they show what you can do with matrices in GLSL but assume that you know what’s _in_ the matrices):
* _Section 3: Vertex Shaders_ walks through things end to end. The _Drawing a simple geometry sample_ subsection starts with some sample shader code for how matrices would be used
* With that subsection, “Simple Lighting” walkthrough reviews lighting one more time and provides shader code as well

The two programming books combined give you two similar but separate examples for projection, camera, and lighting implementation, with the same concepts but written in different ways and with different emphases. Pick whatever speaks to your group best—they all lead you in the right direction. And feel free to read further, too.

If you wish to go above and beyond, the [red](https://brightspace.lmu.edu/d2l/le/content/130175/viewContent/1411988/View) and [orange](https://brightspace.lmu.edu/d2l/le/content/130175/viewContent/1411992/View) books go into even greater depth. In particular, Chapter 12 of the orange book describes multiple lighting approaches, culminating in the “ÜberLight” model (with complete shader code!) once used in Pixar’s RenderMan software.

## For Submission
We forge ahead with our 3D library by building out the remaining basics—something commonly called the “fixed function” pipeline. Many more features are possible, of course—texture mapping, fog, shadows, reflection, refraction, different types of material—but they all would build upon what’s here with additional computations in the shader code driven by additional information in your scene graph. But we’ll stop with the following features for now.

### Previously on…: Project the Matrix
Extended from the earlier assignment, your library should now use its orthographic or perspective projection matrices to break out of that normalized device coordinates (NDC) 2×2×2 cube. Integrate a projection matrix into your shader so that you can have full access to a world space that is determined by _you_ rather than WebGL/GLSL. (well, NDC is still there but you’re adding a layer that pushes it under the hood)

### The New Normal
Add support for normal vectors in your shape objects. You may use any technique for generating them, including (correctly) using the functions given to you or writing code of your own. Allow variations that will produce either a faceted or smooth look—the faceted look is achieved by ensuring that every vertex in a triangle has the same normal vector. The smooth look is achieved by giving each vertex a different normal, typically the average of the normals of the triangles that use it. You want to do this because you will then set up…

### Lights!
Implement a lighting model for your 3D framework, using it in your scene-in-progress and enhancing your shaders accordingly. You can go beyond the basics from class or the programming book sections if you wish (e.g., the ÜberLight model described in Chapter 12 of the orange book).

### Camera!
Implement the camera “look-at” transformation matrix in your matrix library and integrate it into your 3D framework. Model and use a camera in your 3D scene. Note that, at this point, you now have full scene layout and navigation capabilities.

### Action...Almost
Your “tester” web app should start evolving toward your final scene at this point, because by the time you implement the features above, you will have nearly everything you’ll need. The scene doesn’t have to be finished, but there should be enough there to demonstrate that you do have projection, lighting, and a camera.

### “One More Thing”
If you’re in a five-member group, implement per-vertex coloring as well. The basics are already in the starter code—just adapt that into your framework, similar to the work done in [Assignment 0406a](https://github.com/lmu-cmsi371-spring2021/assignments/blob/main/static-3d-scene.md).

## Extra Credit: Texture Mapping
Groups that implement texture mapping in their respective libraries will get extra credit. This is spelled out step by step in the sections from _Textures_ onward in [Real-Time 3D Graphics with WebGL 2](https://brightspace.lmu.edu/d2l/le/content/130175/viewContent/1411963/View). Virtually all of the code is there; this is extra credit primarily because it’s uncertain whether there will be time to cover this fully in class, so doing this successfully will involve some self-study. General outline:
* Learn how to load image data from JavaScript into WebGL
* Add texture coordinates as yet another property for your 3D objects to store
* Use the `texture` function in GLSL to map a texture’s pixels onto a fragment

## How to Turn it In
Commit the following to your repository:
- [Matrix use in projection](#previously-on-project-the-matrix)
  * Orthographic or perspective projection can be applied to the scene (thus breaking it out of the NDC 2×2×2 space)
- [Normal vectors](#the-new-normal)
  * Functions for computing normal vectors from a geometry
  * Allow for either faceted (one normal per triangle) or smooth (one normal per vertex) looks
  * Normals are stored with 3D objects
  * Pass normal vectors into GLSL
  * Use normal vectors to perform…
- [Lighting calculations](#lights)
  * Model light sources in your scene framework
  * Pass light source data into GLSL
  * Use light source data to determine colors
- [Camera support](#camera)
  * Add the camera “look-at” matrix to your matrix library
  * Model a camera in your scene framework
  * Integrate the camera transform in your shader code
- [Scene-in-progress](#actionalmost)
  * Demonstrate your 3D library’s features thus far
- For five-member groups: [Per-vertex coloring](#one-more-thing)
- (extra credit) [Texture mapping](#extra-credit-texture-mapping)

## Specific Point Allocations
This assignment is scored according to outcomes _1b_, _1c_, _2a_, _2c_, _3a_, _3c_, _3d_, and _4a_–_4f_ in the syllabus. For this particular assignment, graded categories are as follows—points with parentheses indicate differences between four- and five-member groups. The “Matrix use in projection” points are part of [Assignment 0406b](https://github.com/lmu-cmsi371-spring2021/assignments/blob/main/matrix-library.md)’s total so they are not in this table:

| Category | Points | Outcomes |
| -------- | -----: | -------- |
| Normal vectors | 30 (23) points total | _1b_, _2c_, _4a_–_4d_ |
| • Computed correctly | 10 points | |
| • Faceted and smooth looks are possible | 5 points | |
| • Stored with 3D objects | 9 (5) points | |
| • Passed into GLSL | 6 (3) points | |
| Lighting | 40 points total | _1c_, _2c_, _3c_, _3d_, _4a_–_4d_ |
| • Modeled in the scene | 10 points | |
| • Passed into GLSL | 10 points | |
| • Correctly combined with normal vectors to determine colors | 20 points | |
| Camera | 20 points total | _1c_, _2a_, _3a_, _3c_, _3d_, _4a_–_4d_ |
| • “Look-at” implemented correctly by the matrix library | 10 points | |
| • Modeled in the scene | 7 points | |
| • Correctly used by shader code | 3 points | |
| Scene-in-progress effectively shows 3D library features | 10 points | _1c_, _4a_–_4d_ |
| (5-member groups only) Per-vertex coloring | n/a (7) points total | _1b_, _2c_, _3c_, _3d_, _4a_–_4d_ |
| • Stored with 3D objects | n/a (4) points | |
| • Passed into GLSL | n/a (3) points | |
| Texture mapping | extra credit | _1b_, _2c_, _3c_, _3d_, _4a_–_4d_ |
| Hard-to-maintain or error-prone code | deduction only | _4b_ |
| Hard-to-read code | deduction only | _4c_ |
| Version control | deduction only | _4e_ |
| Punctuality | deduction only | _4f_ |
| **Total** | **100** |

Per-vertex coloring is most closely related to how normal vectors are stored and passed into GLSL, which is why the point shift is focused on those items. Four-member groups can view that as a clue on how normal vectors can be implemented since vertex colors are already implemented (in a raw, unrefined manner) in the “Less Bare Bones” starter code.

Note that inability to compile and run any code to begin with will negatively affect other criteria, because if we can’t run your code (or commands), we can’t evaluate related remaining items completely.
