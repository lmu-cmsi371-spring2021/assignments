**CMSI 371** Computer Graphics, Spring 2021

# Assignment 0406b
This aspect of your 3D framework adds major flexibility to your 3D objects through the power of vectors and matrices.

## Background Reading
This assignment’s supporting content is virtually all mathematical—[Shirley/Marscher](https://brightspace.lmu.edu/d2l/le/content/130175/viewContent/1411955/View) here we go:
* _Chapter 2: Miscellaneous Math_
* _Chapter 5: Linear Algebra_
* _Chapter 6: Transformation Matrices_

The sample code includes a [vector](https://github.com/dondi/bazaar/tree/master/vector) implementation with accompanying test suite. It will be useful to understand this code well before going all Morpheus (or Neo?) on your own.

## For Submission: Enter the Matrix
This assignment focuses on implementing matrix transformations—the core geometric engine of any graphics pipeline. The core functionality should be a distinct, independent module, with the 3D object framework from the companion assignment meant to use this module to round out the “version 1” functionality of a rudimentary scene library.

### Build the Matrix
Design and implement a computer graphics matrix library with an accompanying suite of unit tests. As with the 3D object framework, no specific design is mandated. However, the following capabilities should be provided:
- A basic matrix object that initializes, by default, to the identity matrix
- Matrix multiplication
- Collection of 3D matrix implementations
  * 3D translation
  * 3D scale
  * 3D rotation about on an arbitrary axis (you may refactor the sample code to fit your matrix object implementation)
  * Orthographic projection
  * Perspective (frustum) projection
- Conversion/convenience functions to prepare the matrix data for direct consumption by WebGL and GLSL

Note that there are enough matrix categories to go around individually, so this is what constitutes the individual credit: each group member will take individual point on one of the above matrix types. Supply a _matrix-credits.md_ file that identifies the specific matrices (and [accompanying tests](#test-the-matrix)) for which each individual group member was primarily responsible.

_All_ of these matrices are required, so matrices that aren’t an individual responsibility will reside with the group.

Need some inspiration? Think of yourself as [taking control of your vertices the way Neo controls a hail of bullets](https://www.youtube.com/watch?v=dEn9vzW0Lc4)🕴

### Test the Matrix
This item is sufficiently important to deserve its own section:
- A unit test suite based on [Jest](https://jestjs.io) (courtesy of React)

The reason for the test suite’s importance is the reality that the aforementioned matrix functionality is fairly cut-and-dried; it will not be hard to find implementations on the web and in the textbook. Thus, what makes _your_ implementation different will be the specific design choices that you make for your library _and its test suite_. Use the test suite’s coverage to demonstrate your understanding of matrices and transformations.

Like the matrix implementations themselves, responsibility for tests is individualized, corresponding to the matrix that a particular group member took point on. Matrix types that are implemented by the group are the responsibility of the group.

### Apply the Matrix
Armed with your newly-minted matrix library, enhance your 3D framework from Assignment 0330a in the following ways:
- Give your 3D objects an _instance transformation_: A per-object composition of rotate, scale, and translate matrices that will let you position objects in the scene and within groups. This matrix will be sent to the vertex shader—they are just _stored_ in JavaScript, but GLSL will perform the actual transformation (as it should—that’s why we have graphics hardware!) …note that five-member groups are asked to [do both](#one-more-thing)
- The 3D object grouping functionality from the companion assignment gets most of its power from the instance transformation: a 3D object group’s members _build their instance transformations on top of the parent’s_. This is the secret to how composite objects “stay together” when the full group is repositioned, rotated, or scaled
- Don’t forget that 3D object groups are _trees_ and can go arbitrarily deeply (e.g., you can group fingers with a palm to form a hand; that hand can be added to an arm; that arm can be added to a body, etc.), so the instance transformations should compose accordingly as well

The key idea here is to have, after this portion is done, a complete “construction set” of sorts for creating, composing, and now transforming your scene objects in a manner that is limited solely by your imagination.

### Project the Matrix
The second major capability afforded by your matrix library will now be the ability to break out of that 2×2×2 cube thanks to the availability of projection matrices. Do take advantage of them when ready in your stub scene drawing code.

### Use the Matrix
Once you reach this point, you now have all of the pieces needed to create a _complete 3D scene_ from your 3D object and matrix framework (the companion assignment, by itself, is unable to change objects once they are created—that’s why it’s static; this assignment makes it dynamic). Use instance transformations to position, rotate, and resize the objects in your scene. Use the composite/group ability to build more complex objects that transform as a unit. Modify these transformations by calling `requestAnimationFrame` repeatedly, changing the matrices, then re-rendering the scene. Welcome to the foundational technologies behind [bullet time](https://www.youtube.com/watch?v=I1ZbUs1xwes).

### “One More Thing”
If you’re in a five-member group, you will implement one more matrix-related function in your 3D object framework: the ability to _morph_ the vertices “in-place.” This is simply the ability to multiply a transform matrix to every vertex in a shape _in JavaScript_, so that the _vertex coordinates themselves_ are permanently transformed. It’s a nice-to-have—it allows you to separate your transformation of an object into smaller steps. For example, you might want to scale a sphere so that it looks more egg-like, and then think of yourself as re-scaling that egg in the instance transformation for dynamic/animation purposes.

Mathematically, multiple transformation steps all become one matrix anyway so four-member groups aren’t missing out functionality-wise. But the availability to pre-morph the vertices of an object based on a transformation is convenient if it’s there, and for five-member groups, it _has_ to be there.

### Extra Credit: JSON Representation
The pros use tools to create their 3D objects and scenes—for extra credit, you can take a stab at implementing this capability.

Separate your 3D scene from the code by allowing it to be represented in JSON. Find a way to express and process the scene such that one or more of these capabilities is present:

- Objects at different levels of abstraction (3D object, polygon mesh, mesh maker) are supported
  * Mesh maker functions can be called in order to create an object programmatically
  * Alternatively, custom vertices and faces may be listed directly
- Properties that define a current instance transformation are available
- Environment settings such as a viewing volume and projection type can be specified

This functionality is somewhat open-ended so extra credit will be given commensurate with how much is (correctly) implemented.

## How to Turn it In
Commit the following to your repository:
- [Matrix object/library](#build-the-matrix)
  * Default to identity matrix
  * Matrix multiplication implementation
  * 3D matrix collection (mostly individual responsibility)
  * Conversion/convenience functions to work with WebGL and GLSL
- [Matrix test suite](#test-the-matrix)
  * Test responsibility aligns with implementation responsibility (i.e., if the group implemented something, the group should implement the tests; if an individual took point on something, the individual should take point on the tests)
  * _matrix-credits.md_ file documents who did what matrix
- [Matrix use in 3D objects](#apply-the-matrix)
  * 3D objects maintain an instance transformation
  * 3D object groups compose children’s instance transformations recursively
  * For five-member groups: [3D objects can transform vertices in JavaScript](#one-more-thing)
- [Matrix use in projection](#project-the-matrix)
  * Orthographic or perspective projection can be applied to the scene (thus breaking it out of the 2×2×2 space)
- (extra credit) Ability to [represent a scene in JSON](#extra-credit-json-representation)

## Specific Point Allocations
This assignment is scored according to outcomes _2a_, _2b_, _3a_, _3c_, _3d_, and –4a_–_4f_ in the syllabus. For this particular assignment, graded categories are as follows—points with parentheses indicate differences between four- and five-member groups:

| Category | Points | Outcomes |
| -------- | -----: | -------- |
| Matrix object/library | 30 (26) points total | _2a_, _2b_, _4a_–_4d_ |
| • Default to identity matrix | 2 points | |
| • Matrix multiplication is implemented | 8 points | |
| • Group-based 3D matrix (group’s choice) | 4 (n/a) points | |
| • Individual-responsibility 3D matrix | 8 points | |
| • Matrix data converts to WebGL and GLSL | 3 points | |
| • Implemented correctly and well | 5 points | |
| Matrix test suite | 25 (21) points total | _2a_, _2b_, _4a_–_4d_ |
| • Default identity tested correctly and well | 1 point | |
| • Default identity test has sufficiently high coverage | 1 point | |
| • Multiplication tested correctly and well | 4 points | |
| • Multiplication test has sufficiently high coverage | 4 points | |
| • Group matrix tested correctly and well | 2 (n/a) points | |
| • Group matrix test has sufficiently high coverage | 2 (n/a) points | |
| • Individual matrix tested correctly and well | 4 points | |
| • Individual matrix test has sufficiently high coverage | 4 points | |
| • WebGL and GLSL conversion tested correctly and well | 2 points | |
| • WebGL and GLSL conversion test has sufficiently high coverage | 1 point | |
| • _matrix-credits.md_ lists individual matrix assignments | deduction only if not fulfilled | |
| Matrix use in 3D objects | 30 (38) points total | _2a_, _3a_, _3c_, _3d_, _4a_–_4d_ |
| • Maintain an instance transformation | 10 points | |
| • Groups compose instance transformations | 15 points | |
| • (5-member groups only) Vertices can be transformed in-place | n/a (8) points | |
| • Implemented correctly and well | 5 points | |
| Matrix use in projection | 15 points total | _2b_, _3c_, _3d_, _4a_–_4d_ |
| • Ability to use orthographic or perspective projection | 10 points | |
| • Implemented correctly and well | 5 points | |
| JSON representation of scene | extra credit | _4a_–_4d_ |
| Hard-to-maintain or error-prone code | deduction only | _4b_ |
| Hard-to-read code | deduction only | _4c_ |
| Version control | deduction only | _4e_ |
| Punctuality | deduction only | _4f_ |
| **Total** | **100** |

Note how there is a one-to-one shift of tasks here: four-member groups will need to implement one of the matrix types as a group but five-member groups don’t, while five-member groups have to implement JavaScript-side transformations but four-member groups don’t. Thus, the point allocation shifts from one to the other depending on the size of your group, but the totals stay the same.

Note that inability to compile and run any code to begin with will negatively affect other criteria, because if we can’t run your code (or commands), we can’t evaluate related remaining items completely.
