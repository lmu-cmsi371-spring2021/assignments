**CMSI 371** Computer Graphics, Spring 2021

# Assignment 0218
Now that we have a little more knowledge under our belt, we do a “remix” and take another pass at building an application using a higher-level library that is made by someone else—in this case [three.js](https://threejs.org). This is still a lot about “have fun and see what you can do,” but making use of additional core computer graphics concepts.

## Background Reading
Documentation continues to be centered on [three.js](https://threejs.org/docs/) but, as introduced in class, [three.js Fundamentals](https://threejsfundamentals.org) also provides a number of useful walkthroughs as long as you keep an eye out for occasional deprecated code references. In particular, the [Custom BufferGeometry page](https://threejsfundamentals.org/threejs/lessons/threejs-custom-buffergeometry.html) will be of most direct use in terms of code, alongside the official three.js [BufferGeometry reference page](https://threejs.org/docs/#api/en/core/BufferGeometry) in case there have been updates to the API since the fundamentals page was last written.

The [Custom Geometry page](https://threejsfundamentals.org/threejs/lessons/threejs-custom-geometry.html), though referring to a now-deprecated portion of three.js, still works well in terms of walking through how a proper 3D geometry is built.

Finally, you may find it useful to temporarily switch to [MeshNormalMaterial](https://threejs.org/docs/#api/en/materials/MeshNormalMaterial) for quick, easy visualization of a geometry’s normal vectors (we’ll talk about those more in class).

A more conceptual take on [3D Object Modeling](http://dondi.lmu.build/share/cg/3d-object-models-v03.pdf) can also be found on the course website.

### Side Trip: Tweened Animation and Easing Functions
Completely supplementary, with the addition of the [createjs/TweenJS](https://www.createjs.com/tweenjs) library to the sample code, are the following readings on _tweened animation_—the technique of automatically calculating intermediate positions based on a starting and ending value. The recognized pioneer and expert here is Robert Penner, who has released his [book chapter on tweening and easing](http://robertpenner.com/easing/penner_chapter7_tweening.pdf) for free on the web. There is also Gilmore Davidson’s online presentation called [Ease Yourself Into Animation](http://gilmoreorless.github.com/sydjs-preso-easing/)—although some of its code/technology references are dated, the core concepts and presentation approach remain pretty solid. Finally, TweenJS provides a [visual demonstration](https://www.createjs.com/demos/tweenjs/tween_sparktable) of its tweening functions—and of course, you can always write your own.

## For Submission
With your new team, come up with an updated or remixed take at a three-dimensional scene implemented via three.js. You may carry over some code from your previous application but make sure to fulfill this new set of criteria:

### Remix/Reboot/Repeat Your Pitch
As before, give the scene a concrete _use case_—in other words, don’t let it be a meaningless collection of objects (the way the starter code is 😅). What’s different this time is that you’ve done this once before, so you may mix and match ideas from your previous teams as desired. You can also start over completely if you wish.

In any case, make sure your idea fits well with the technical requirements listed below—they are more specific so some prior idea may need to be tweaked. You’ll want a use case that naturally/organically benefits from having lights, textures, adding/removing objects, collision detection, and custom geometries. Supply a new _pitch.md_ file that frames your scene in some context.

(And if you already did some of this in the prior program, then good for you! As mentioned in the earlier assignment, these were optional then but if you did them anyway, you will reap the benefits now)

### Lights and Textures
These were optional previously, but now you definitely want to implement these. Give your scene an appropriate lighting scheme; switch your materials to those that respond to light; and texture-map at least three (3) objects in your scene.

Make sure to acknowledge the sources of any textures that you use—a comment in the code near the place where you use the texture image will suffice.

### [The Hokey-Pokey](https://www.youtube.com/watch?v=pJjgxXCkMYk)
Take animation and interaction to the next level by implementing a couple of very common behaviors as either autonomous animation or user interaction. These can be implemented as separate behaviors or integrated into one Dazzling Display of Dimensional Derring-Do.

These behaviors may benefit from some preset animations, but as you might have realized, programming those into the `animate` function can get very labor-intensive. To lessen this tedium, a helper library called [TweenJS](https://www.createjs.com/tweenjs) has been added to the starter code. The library makes animation code more declarative and also allows concurrent independent animations to take place. This doesn’t really help with the specific behaviors here but may make for some entertaining visuals _upon_ performing those behaviors.

#### “You Put an Object In, You Take an Object Out…”
Implement _dynamic_ addition and removal of meshes or groups to/from your scene, either via autonomous animation or user interaction. In other words, don’t just set up your scene and let it go; come up with a scenario which requires that an object be added to your scene in the middle of the action. Have another scenario that removes an object as well—perhaps the same object that was added previously.

As always, the addition and removal must make sense in the context of your overall use case, so do make sure to tailor your use case such that these actions are a natural part of your pitch. Examples include autonomous objects that enter or leave the scene at random or having a user manually add or remove objects at will. Maybe projectiles are launching from somewhere then disappear when they hit the ground (see the next behavior). Or perhaps you have a naturalistic setting where plants grow or animals emerge. In any case, make sure that your scene graph doesn’t stay fixed for the life of your application.

Document your additional and removal behavior in _pitch.md_ so that it’s clear that the behavior is intentional.

#### “…And You Shake it All About…”—Crash and Learn
Implement at least one instance of _collision detection_—i.e., a behavior where contact between two objects in the scene changes what is currently going on. The collision may be a result of autonomous animation or user interaction. For example, you might have an independently-moving object that changes direction when it hits something. Alternatively, the user might be able to get objects to change color or texture when they touch. Or finally, perhaps your scene has a genuine “floor” and objects do not fall past it.

The collision implementation must genuinely result from detecting some kind of contact between the objects. In other words, don’t “fake” a collision through hardcoded thresholds or scripted animations that are pre-programmed to just happen to look like objects interacting with each other. The detection mechanism doesn’t need to be very sophisticated—as you might guess, [fully generalized object interaction](https://en.wikipedia.org/wiki/Rigid_body_dynamics) can be quite involved. When the objects themselves are pliable, elastic, or fluid, things get even more gnarly. That isn’t what’s expected here: keep it simple.

Not all objects have to be interactive in this way—again, that’s a general case which is beyond the scope of this assignment. Just pick a subset and build your logic around those. The rest of the scene can go on ignoring each other 🧐

As mentioned earlier, you may also combine all of these behaviors into one meaningful scenario for your use case. For example, a collision might remove the collided object from the scene. Alternatively, a collision may add new objects. That approach will satisfy these technical requirements just fine.

Document your collision behavior in _pitch.md_ so that it’s clear the behavior is intentional.

### Bespoke for Yourself: Make Your Own Geometry
As before, each individual member of the group must be clearly in charge of or responsible for at least one “character” or object in the scene. Collaboration is OK but most of the work (best evidenced by commits) must be clearly done by a specific developer. A _credits.md_ file should again list which character or object was the primary responsibility of which member.

For this round, in addition to having a composite ([Group](https://threejs.org/docs/#api/en/objects/Group)/[Skeleton](https://threejs.org/docs/#api/en/objects/Skeleton)) aspect, your individual-responsibility object must also include a mesh with _a custom geometry_. In addition to the documentation linked above, the starter code in this repository provides a simple example for such a beast.

To avoid just any scattershot conglomeration of randomized vertices, your customized mesh should have the following characteristics:
* It must be informed by your pitch—avoid a custom geometry for the sake of it; think through your use case and your object, and come up with a custom geometry that fits well with them
* It must not be easily replicable through any single pre-made geometry nor through straightforward translation, rotation, or scaling of these shapes (watch out—the extrude and lathe geometries can be surprisingly flexible)
* It must have at least six (6) non-coplanar triangles (in case that seems intimidating: note that this is on the same level as a cube)
* It must make an appropriate choice between a faceted look (e.g., cubes, polyhedra, etc.) and a smooth look (e.g., spheres, cylinders, cones, etc.)
* It must have at least one of the following:
    * Per-vertex texture coordinates (demonstrable by using a `map` with your material)
    * Per-vertex colors (demonstrable by setting `vertexColors: true` on your material)

Note that although the end product is almost always the same—arrays of vertices, colors, texture coordinates—_how_ those arrays are built can vary widely. You can flat-out just list the numbers—not a bad exercise in limited amounts, but doesn’t scale well; that’s why we have 3D modeling applications and scanners! You can have some base values then generate the rest algorithmically. You can have a fixed set of vertices then programmatically arrange/copy/index them as needed. Or you can go fully computational and calculate something based on some set of parameters. A level of randomization may be appropriate…but don’t get completely random.

### Bells and Whistles v2
With custom geometries, lighting, and textures, you now have the main building blocks that power most entry-to-mid-level 3D applications. What’s left? Within reach are [shadows](https://threejsfundamentals.org/threejs/lessons/threejs-shadows.html) and [fog](https://threejsfundamentals.org/threejs/lessons/threejs-fog.html). For interaction, you can look into [3D picking](https://threejs.org/docs/#api/en/core/Raycaster). For modeling, you can look into [skeletons](https://threejs.org/docs/#api/en/objects/Skeleton) with a [skinned mesh](https://threejs.org/docs/#api/en/objects/SkinnedMesh). And finally, you can look ahead by exploring [ShaderMaterial](https://threejs.org/docs/#api/en/materials/ShaderMaterial)—a material where you directly program vertex and coloring calculations.

Feel free to explore, but once again, don’t obligate yourself to go there. After this assignment, we will go under the hood to see how even these basics are done in the first place. That will help make the advanced features easier to pick up.

## Operational Directives/Suggestions
These remain the same as for the previous assignment:
- The starter code has a preliminary organization and structure, and is also provided as a React app—you may modify any or all of these. The only condition is that you deliver a standalone web application that uses three.js. Of course, if you move away from a React app, make sure you provide clear and complete documentation on how to get your scene to run
- Don’t let the “characters are an individual responsibility” aspect throw you off from working on the _entire_ scene as a group. By and large, a group that works effectively together will have the most successful scene. The individual character aspect merely lets each group member have something they can call their own, reflecting individual interests and emphasis. By all means still collaborate with each other on your characters—help each other, within reason, to bring their best to the overall scene
- Although you have access to an individual three.js playground where you can try things out, make sure to isolate that work only to experiments and exploration. Any work that now directly stems from what your group decides for you scene should be done _on your group repository_ so that all commits are reported there. Doing work on the individual playground then copying files wholesale to the group repository only loses the granularity and incremental changes that you make along the way

## How to Turn it In
Commit the following to your repository:
* The complete scene code, organized such that individual-responsibility characters/objects are in clearly-indicated distinct files or folders
* _pitch.md_, including your use case and descriptions of addition, removal, and collision behaviors
* _credits.md_, listing the characters/objects that are individually owned
* If needed, instructions for how to run your scene (if it is no longer a React app)

## Specific Point Allocations
This assignment is scored according to outcomes _1b_, _1c_, _2a_–_2c_, _3a_, _3c_, and _4a_–_4f_ in the [syllabus](http://dondi.lmu.build/spring2021/cmsi371/cmsi371-spring2021-syllabus.pdf). For this particular assignment, graded categories are as follows:

| Category | Points | Outcomes |
| -------- | -----: | -------- |
| _pitch.md_ provides all requested information | 6 points total | _1c_, _3a_, _3c_, _4b_, _4c_ |
| • Description of use case | 2 points | |
| • Description of addition/removal behavior | 2 points | |
| • Description of collision detection behavior | 2 points | |
| _credits.md_ lists all group members and what they individually took point on | 4 points | _3a_, _4b_, _4c_ |
| Lighting is implemented | 12 points total | _2c_, _4a_–_4d_ |
| • Well-chosen lights are included in the scene | 6 points | |
| • Scene objects use materials that use lights | 6 points | |
| At least three (3) objects use texture mapping | 12 points total | _2c_, _4a_–_4d_ |
| • Texture creators/sources are acknowledged | deduction only | |
| Some objects get added to the scene on the fly | 10 points total | _1c_, _4a_–_4d_ |
| • Aligns with use case | 2 points | |
| • Implemented correctly and well | 8 points | |
| Some objects get removed from the scene on the fly | 10 points total | _1c_, _4a_–_4d_ |
| • Aligns with use case | 2 points | |
| • Implemented correctly and well | 8 points | |
| Some collision detection is implemented | 20 points total | _2a_, _2b_, _3c_, _4a_–_4d_ |
| • Aligns with use case | 2 points | |
| • Logic genuinely uses object positions and state | 8 points | |
| • Implemented correctly and well | 10 points | |
| Composite characters/objects meet specifications | 26 points total | _1b_, _1c_, _3c_, _4a_–_4d_ |
| • Aligns with use case | 2 points | |
| • Not easily replicable | 6 points | |
| • At least six (6) non-coplanar triangles | 6 points |
| • Looks appropriately faceted or smooth | 6 points |
| • Includes and makes use of either texture coordinates or vertex colors | 6 points | |
| Hard-to-maintain or error-prone code | deduction only | _4b_ |
| Hard-to-read code | deduction only | _4c_ |
| Version control | deduction only | _4e_ |
| Punctuality | deduction only | _4f_ |
| **Total** | **100** |

For non-code deliverables, we reinterpret outcomes _4b_ and _4c_ in this assignment to represent the clarity, polish, and effectiveness of how you document your scene and its features.

Note that inability to compile and run any code to begin with will negatively affect other criteria, because if we can’t run your code (or commands), we can’t evaluate related remaining items completely.
