**CMSI 371** Computer Graphics, Spring 2021

# Assignment 0506
We end our computer graphics journey the way we began: by putting together an animated, interactive 3D scene. But this time, the higher-level library that we will use is the one that we have made—something that, in our field, is sometimes referred to as “eating our own dog food” 🐕

## Background Reading
Pretty much anything is fair game at this point—everything ranging from _three.js_ (to see how “they” designed things) to the textbooks (theoretical, programming, _and_ reference) to the starter code to the additional course website materials. Not much more to say here except to refer back to those sources as needed.

## For Submission
Make two three-dimensional scenes implemented via your 3D library. The specifications are as follows:

### Sandbox Scene
Implement a scene that is very similar to the test scenes you have created so far (in fact it can even be the same scene)—something abstract or random, used to demonstrate or try out certain library features. You’ll see why this is useful later.

### Pitched Scene
The second scene to implement follows the same pattern as before—if anything sounds a lot like the instructions from the very first assignment…well, that’s by design.

#### Have a Pitch
Develop your second scene with a concrete _use case_ in mind—in other words, don’t let it be a meaningless collection of objects (the way the starter code—or your sandbox scene—is 😅). To that end, supply a _pitch.md_ file that frames your scene in some context. Is it the beginnings of a story? The basis for a game? The foundation for a simulation? Setting up a pitch that excites your entire group will seed your ideas and explorations.

Note the use of words like “beginning,” “basis,” or “foundation”—the final result of this assignment doesn’t need to be fully-formed. However, it must be _self-sufficient_: i.e., it might not be feature-complete, but the features that _are_ present are functional and bug-free.

#### Keep Some Motion in the Ocean
The scene must have something that is _autonomously animated_—i.e., one or more things about the scene must change over time even if the user does nothing. This animation must be described in _pitch.md_. (so I know that it is intended behavior)

#### Give the User Something to Do
Conversely, the scene must also have something that is _interactive_—i.e., the user can perform one or more actions that will affect the scene dynamically. Instructions for this interactivity should be described in _pitch.md_. (so I know what to do when I fire up your scene)

#### Get Lit 💡
Give your scene an appropriate lighting scheme and make sure that all objects respond to lighting as intended.

#### Demonstrate that You Have the Technology
To guide your choices on animation and interaction, make sure that your pitched scene uses the following capabilities of your library. You are free to fit the capability to your use case—you may choose to show these either via autonomous animation or interaction, but make sure you _show_ all of them one way or the other without having to change the scene’s source code:
* Ability to change camera position and viewpoint
* Ability to toggle between wireframe and solid rendering
* Ability to toggle between orthographic and perspective projection (you may choose the viewing volume parameters as appropriate for each type of projection)
* A _non-square_ canvas whose aspect ratio matches that of both viewing volumes
* Ability to add and remove objects to/from the scene
* Ability to add and remove objects to/from groups
* Ability to compute lighting in both faceted/flat and smooth styles

#### Be Individually Responsible for a Group (Composite) “Character”
Each individual member of the group must be clearly in charge of or responsible for at least one “character” or object in the scene. The group can collaborate on it but a specific member must have primary responsibility for that object. Concretely speaking, the majority of commits for that character or object’s code must be by the responsible member. As you might expect, this part is to be graded individually.
* The character must be a _composite_ object—i.e., it should use whatever group construct you defined for your library
* The character must have an _internal_ moving part, like a rotating arm, a head that turns, a door that opens, etc. (yes, this is meant to show off your implementation of parent transforms being correctly applied to child objects)

Document the distribution of responsibility by providing a _credits.md_ file that states which character or object was the primary responsibility of which member.

Not all scene objects have to be individual—some aspects may be fully shared by the group. But each member must be in charge of at least one. This ensures that your scene will have, at a bare minimum, at least as many characters/objects as you have group members.

#### Implementation Tips & Notes
* In the process of developing your scene, you might realize that you need to create new shapes or modify/tweak existing ones—well you know how to create them from nothing now, so go right ahead and customize as needed
* Similarly, you might feel like certain refactors or redesigns are called for in your library—feel free to do those
* Further, you might be inspired to improve or add features to your library (texture mapping; improved lighting)—go for it! Information for how to implement those _can_ be found…some of them right in the recommended texts

### Assess Your Design
One reason for asking you to implement _two_ scenes is to allow you to assess your design choices. Does your design effectively hide boilerplate code? How much code has to be repeated across scenes? How much of the scene code is genuinely specific to the actual scene being built?

Provide a _commentary.md_ file that looks back on your design choices and answers at least these questions:
1. What aspects of defining a 3D scene are successfully handled by your library behind the scenes?
2. What aspects are _not_ handled behind the scenes? (i.e., the dev user needs to write code for them)
3. How much code for using your library is the same at the application level, regardless of the specific scene?
4. What aspects of your design would you keep, if you got a chance to do this library over?
5. What aspects of your design would you change?

### Extra Learnings
A few aspects of the graphics pipeline remain, but they are difficult to apply at our level because WebGL performs these operations for us “for free.” As such, asynchronous videos will be prepared for the following topics:
1. Clipping
2. Hidden surface removal

When those videos are posted to Brightspace, all you need to do is watch them. Brightspace will know if you have, and that’s what I’ll check to determine the score for this section.

### Extra Yearnings
An open-ended pool of points can be awarded for extra credit if your 3D library implements features above and beyond the baseline for this part of the course. This is open-ended precisely because the possibilities are open-ended. Some parameters:
* The feature cannot be something for which you have already received extra credit
* Extra credit can be group or individual, and for the latter it must be very clear (either via the commit log or mutual acknowledgement by group members) that the extra feature was predominantly worked on by that individual
* Make sure that the fundamentals (the other specifications requested earlier) are handled sufficiently before even _thinking_ about aiming for these “extra yearnings”—I reserve the right to withhold extra credit if this is attempted but something more basic has not been handled well

Examples or possibilities include:
* A more advanced/sophisticated lighting model
* Non-trivial new material characteristics
* Texture mapping
* Shadows
* Reflection
* Blending

…and many more!

What won’t count:
* New shapes—at this point these should be pretty straightforward to generate, and even if they require additional programming, these computations are independent of the core graphics pipeline (unike the capabilities listed above)
* File import/export—this was available for extra credit earlier but, like shapes, they are outside the core graphics pipeline so if you haven’t implemented this yet, the ship has sailed
* Test suite—same reasoning…I’m not one to discourage automated testing but this is also outside the central flow of graphics calculations

…so note that the priority here isn’t just any additional feature, but those that involve expansion or enhancement of the graphics pipeline itself.

### Statement of Work Retrospective
* Reflect on your overall group graphics work for the entire “Our Own Library” sequence in a _group-retrospective.md_ document. Describe what each group member worked on through all of the assignments as well as this last pair of scenes
* Write an individual email directly to me stating anything that you prefer not to include in the shared _statement-of-work.md_—even if you have nothing to add, _write to me anyway_, so I know that you didn’t miss a chance to speak up. So that I don’t miss it, use the subject line “CMSI 371 _group name_ individual statement of work”

The points for this deliverable pertain to _submission only_ and not its content. If warranted, individual adjustments to final grades may be made based on the information provided in these items.

### No More “One More Thing”
Five-member groups do not have an additional “one more thing” item for this assignment, but given that every member is supposed to be individually responsible for at least one composite character/object in the scene, the expectation is that five-member scenes will be a notch richer by virtue of having one more item in the scene that is a composite with internal component movement.

## How to Turn it In
Commit the following to your repository:
* The [sandbox scene](#sandbox-scene)
* The [pitched scene](#pitched-scene), fulfilling [all](#demonstrate-that-you-have-the-technology) of [the](#keep-some-motion-in-the-ocean) [given](#give-the-user-something-to-do) [specifications](#get-lit-)—its code should be organized such that [individual-responsibility characters/objects](#be-individually-responsible-for-a-group-composite-character) are in clearly-indicated files or folders
* [_pitch.md_](#have-a-pitch), including your use case, description of the [autonomous animation(s)](#keep-some-motion-in-the-ocean), and instructions for how to [interact with your scene](#give-the-user-something-to-do)
* _credits.md_, listing the articulated composite characters/objects that are [individually led](#be-individually-responsible-for-a-group-composite-character)
* If needed, instructions for how to run your scene (if it is no longer a React app)
* _commentary.md_, containing [thoughts on your library’s design](#assess-your-design)
* Visits to Brightspace to log viewings of the [two asynchronous videos](#extra-learnings) (when available)
* [_group-retrospective.md_](#statement-of-work-retrospective), describing the roles and contributions of each group member through all of the “our own library” assignments
* [Individual email](#statement-of-work-retrospective) with the requested title and comment (even if there is nothing to add to _group-retrospective.md_)

## Specific Point Allocations
This assignment is scored according to outcomes _1b_, _1c_, _2a_–_2d_, _3a_, _3c_, _3d_, and _4a_–_4f_ in the [syllabus](http://dondi.lmu.build/spring2021/cmsi371/cmsi371-spring2021-syllabus.pdf). For this particular assignment, graded categories are as follows:

| Category | Points | Outcomes |
| -------- | -----: | -------- |
| Sandbox scene is provided | 10 points | _1b_, _1c_, _2a_–_2c_, _3a_, _3c_, _3d_, _4a_–_4d_ |
| _pitch.md_ is submitted with requested information | 9 points total | _1c_, _3a_, _3c_, _4b_, _4c_ |
| • Description of use case | 3 points | |
| • Description of autonomous animation | 3 points | |
| • Interaction documentation | 3 points | |
| Pitched scene autonomous animation meets specifications | 12 points total | _1b_, _1c_, _2a_–_2c_, _3a_, _3c_, _3d_, _4a_–_4d_ |
| • Aligns with use case | 4 points | |
| • Differs from startup code | deduction only | |
| • Implemented correctly and well | 8 points | |
| Pitched scene user interaction meets specifications | 12 points total | _1b_, _1c_, _2a_–_2c_, _3a_, _3c_, _3d_, _4a_–_4d_ |
| • Aligns with use case | 4 points | |
| • Differs from startup code | deduction only | |
| • Implemented correctly and well | 8 points | |
| Pitched scene implements a lighting model | 12 points total | _2c_ |
| • Aligns with use case | 4 points | |
| • Implemented correctly and well | 8 points | |
| Pitched scene demonstrates technical milestones | 50 points total | _1b_, _1c_, _2a_–_2c_, _3a_, _3c_, _3d_, _4a_–_4d_ |
| • Change camera position and viewpoint | 7 points | |
| • Toggle between wireframe and solid rendering | 7 points | |
| • Toggle between orthographic and perspective projection | 7 points | |
| • Non-square canvas with matching aspect ratio | 7 points | |
| • Add/remove objects to/from scene | 7 points | |
| • Add/remove objects to/from groups | 7 points | |
| • Perform both flat/faceted and smooth lighting | 8 points | |
| **Individual:** Composite characters/objects meet specifications | 45 points total | _1b_, _1c_, _2a_, _3a_, _4a_–_4d_ |
| • Aligns with use case | 5 points | |
| • Uses your library’s group/composite mechanism | 10 points | |
| • Demonstrates an _internal_ moving part | 20 points | |
| • Implemented correctly and well | 10 points | |
| _credits.md_ lists all group members and what they individually took point on | 10 points | _3a_, _4b_, _4c_ |
| (if different from starter code) Instructions for running the app are provided | deduction only | |
| _commentary.md_ sufficiently reflects on design choices | 10 points | _3a_, _4b_, _4c_ |
| **Individual:** Asynchronous videos viewed on Brightspace | 20 points total | _2d_ |
| • Clipping | 10 points | |
| • Hidden surface removal | 10 points | |
| Group retrospective is submitted with requested information | 10 points total | |
| • _group-retrospective.md_ | 5 points | |
| • Individual email | 5 points | |
| Additional graphics pipeline features | extra credit | _1b_, _1c_, _2a_–_2c_, _3a_, _3c_, _3d_, _4a_–_4d_ |
| Hard-to-maintain or error-prone code | deduction only | _4b_ |
| Hard-to-read code | deduction only | _4c_ |
| Version control | deduction only | _4e_ |
| Punctuality | deduction only | _4f_ |
| **Total** | **200** |

For non-code deliverables, we reinterpret outcomes _4b_ and _4c_ in this assignment to represent the clarity, polish, and effectiveness of how you document your scene and its features.

Note that inability to compile and run any code to begin with will negatively affect other criteria, because if we can’t run your code (or commands), we can’t evaluate related remaining items completely.
