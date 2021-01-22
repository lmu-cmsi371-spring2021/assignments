**CMSI 371** Computer Graphics, Spring 2021

# Assignment 0204
We start our computer graphics journey by learning how to do it through a higher-level library that is made by someone else—in this case [three.js](https://threejs.org). The spirit of this assignment is very much “have fun and see what you can do,” under the premise that in doing so, you’ll start learning some core computer graphics concepts.

## Background Reading
Most of our source material for working with “their” library is the [documentation of that library itself](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene). After you get the basics, expanding your knowledge becomes a matter of getting to know the various geometries and materials that are available to you. You will then primarily want to learn about [Object3D](https://threejs.org/docs/api/en/core/Object3D.html)—so that you get to know the range of things that most scene objects have in common—and [Group](https://threejs.org/docs/api/en/objects/Group.html)—so that you can put together multiple objects in a way that lets them behave as a single, composite object.

Finally, _helper_ objects are available for “breaking the fourth wall” (and for understanding what’s going on in a visual way). Helpers provide supplementary objects to your scene to help you see [axes](https://threejs.org/docs/index.html#api/en/helpers/AxesHelper) or [cameras](https://threejs.org/docs/index.html#api/en/helpers/CameraHelper), to name a few.

Of course, you can learn more than this, but those are the fundamentals that will allow you to meet the specifications of this assignment.

### Mathematical/Theoretical Foundations Preview
The concepts that we are discovering via three.js are addressed in less technology-specific (but more mathematical) terms in the [Shirley book](https://brightspace.lmu.edu/d2l/le/content/130175/viewContent/1411955/View). These may be hard to read right now because Shirley doesn’t separate the concept from the theory—the book alternates between describing an idea then dives right into the mathematics for implementing that idea. However, if you want a taste of how three.js does what it does under the hood, give these a scan:
- Meshes and scenes: Sections 12.1–12.3
- Animation and motion: Sections 17.1–17.5
- Approaches to interaction: Chapter 19

## For Submission
Make a first pass at a three-dimensional scene implemented via three.js. To keep the scene from being too open-ended (which paradoxically may limit your creativity or productivity), the following criteria must be met by the scene:

### Have a Pitch
Give the scene a concrete _use case_—in other words, don’t let it be a meaningless collection of objects (the way the starter code is 😅). To that end, supply a _pitch.md_ file that frames your scene in some context. Is it the beginnings of a story? The basis for a game? The foundation for a simulation? Setting up a pitch that excites your entire group will seed your ideas and explorations.

Note the use of words like “beginning,” “basis,” or “foundation”—the final result of this assignment doesn’t need to be fully-formed. However, it must be _self-sufficient_: i.e., it might not be feature-complete, but the features that _are_ present are functional and bug-free.

### Keep Some Motion in the Ocean
The scene must have something that is _autonomously animated_—i.e., one or more things about the scene must change over time even if the user does nothing. This animation must be described in _pitch.md_. (so I know that it is intended behavior)

### Give the User Something to Do
Conversely, the scene must also have something that is _interactive_—i.e., the user can perform one or more actions that will affect the scene dynamically. Instructions for this interactivity should be described in _pitch.md_. (so I know what to do when I fire up your scene)

_Your autonomous animations and interactivity must be **different** from the ones already demonstrated in the starter code. (I hope that needs no explanation!)_

### Build Something to Call Your Own
Each individual member of the group must be clearly in charge of or responsible for at least one “character” or object in the scene. The group can collaborate on it but a specific member must have primary responsibility for that object. Concretely speaking, the majority of commits for that character or object’s code must be by the responsible member.
* Document the distribution of responsibility by providing a _credits.md_ file which states which character or object was the primary responsibility of which member
* Not all scene objects have to be individual—some aspects may be fully shared by the group. But each member must be in charge of at least one. This ensures that your scene will have, at a bare minimum, at least as many characters/objects as you have group members
* Each group member’s character must have a _composite_ aspect: i.e., it should be internally made of more than one mesh, but can be manipulated or operated on as if it were a single object (_cough cough_ [Group](https://threejs.org/docs/api/en/objects/Group.html) _cough cough_ …or if you’re a little more adventurous, look at [Skeleton](https://threejs.org/docs/index.html#api/en/objects/Skeleton))
* As such, simple elements such as a flat planes, spheres, cubes, or other single-mesh aspects should be shared group responsibilities. Don’t take individual credit for any of those—they’re too simple!

### Set Your Priorities
As important as the above aspects that your scene needs to fulfill are the aspects that you might be excited about but do _not_ have to implement for this scene. You will not get extra credit—for this assignment—for implementing lighting, texture mapping, 3D file loading, or anything else, for that matter, that falls outside the scope of what is described above. You can go there, but if you do, do it solely because you’re interested or want to try things out for the sake of trying things out. We will expand to them in later assignments.

A meticulously rendered 3D model with texture mapping and lights/shadows that just sits there doing nothing will get a lower grade than a moving, dynamic scene consisting of cubes, spheres, and cones. You _may_ implement such features, but for this assignment, do them because you _want_ to and not because you intend to bump up your grade.

## Operational Directives/Suggestions
- The starter code has a preliminary organization and structure, and is also provided as a React app—you may modify any or all of these. The only condition is that you deliver a standalone web application that uses three.js. Of course, if you move away from a React app, make sure you provide clear and complete documentation on how to get your scene to run
- Don’t let the “characters are an individual responsibility” aspect throw you off from working on the _entire_ scene as a group. By and large, a group that works effectively together will have the most successful scene. The individual character aspect merely lets each group member have something they can call their own, reflecting individual interests and emphasis. By all means still collaborate with each other on your characters—help each other, within reason, to bring their best to the overall scene
- Although you have access to an individual three.js playground where you can try things out, make sure to isolate that work only to experiments and exploration. Any work that now directly stems from what your group decides for you scene should be done _on your group repository_ so that all commits are reported there. Doing work on the individual playground then copying files wholesale to the group repository only loses the granularity and incremental changes that you make along the way

## How to Turn it In
Commit the following to your repository:
* The complete scene code, organized such that individual-responsibility characters/objects are in clearly-indicated distinct files or folders
* _pitch.md_, including your use case, description of the autonomous animation(s), and instructions for how to interact with your scene
* _credits.md_, listing the characters/objects that are individually owned
* If needed, instructions for how to run your scene (if it is no longer a React app)

## Specific Point Allocations
This assignment is scored according to outcomes _1b_, _1c_, _2a_, _2b_, _3a_, _3c_, and _4a_–_4f_ in the [syllabus](http://dondi.lmu.build/spring2021/cmsi371/cmsi371-spring2021-syllabus.pdf). For this particular assignment, graded categories are as follows:

| Category | Points | Outcomes |
| -------- | -----: | -------- |
| _pitch.md_ provides all requested information | 15 points total | _1c_, _3a_, _3c_, _4b_, _4c_ |
| • Description of use case | 5 points | |
| • Description of autonomous animation | 5 points | |
| • Interaction documentation | 5 points | |
| _credits.md_ lists all group members and what they individually took point on | 10 points | _3a_, _4b_, _4c_ |
| Autonomous animation meets specifications | 25 points total | _2a_, _2b_, _3c_, _4a_–_4d_ |
| • Aligns with use case | 5 points | |
| • Differs from startup code | deduction only | |
| • Implemented correctly and well | 20 points | |
| User interaction meets specifications | 30 points total | _2a_, _2b_, _3c_, _4a_–_4d_ |
| • Aligns with use case | 5 points | |
| • Differs from startup code | deduction only | |
| • Implemented correctly and well | 25 points | |
| Composite characters/objects meet specifications | 20 points total | _1b_, _1c_, _3c_, _4a_–_4d_ |
| • Aligns with use case | 5 points | |
| • Implemented correctly and well | 15 points | |
| Hard-to-maintain or error-prone code | deduction only | _4b_ |
| Hard-to-read code | deduction only | _4c_ |
| Version control | deduction only | _4e_ |
| Punctuality | deduction only | _4f_ |
| **Total** | **100** |

For non-code deliverables, we reinterpret outcomes _4b_ and _4c_ in this assignment to represent the clarity, polish, and effectiveness of how you document your scene and its features.

Note that inability to compile and run any code to begin with will negatively affect other criteria, because if we can’t run your code (or commands), we can’t evaluate related remaining items completely.
