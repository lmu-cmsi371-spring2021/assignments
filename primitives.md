**CMSI 371** Computer Graphics, Spring 2021

# Assignment 0311
Our last assignment before we plunge into our own 3D library is focused on having you spend some time on the primitive side of graphics, in order to gain an appreciation for what it takes to implement these lower-level graphics operations.

## Background Reading
The entire [Pixar in a Box](https://www.khanacademy.org/computing/pixar) collection from Khan Academy is awesome, but in particular, you will want to look at these:
* [Color Science](https://www.khanacademy.org/computing/pixar/color) as a whole provides some key background information on color
* [RGB color model](https://www.khanacademy.org/computing/pixar/color/color-101/v/color-2) within that sequence, and its accompanying practice exercise, gives you the most direct information relating to this assignment

In the Shirley/Marscher textbook ([available on Brightspace](https://brightspace.lmu.edu/d2l/le/content/130175/viewContent/1411955/View)), you can get deeper treatment of this material and some future course content with _Chapter 3: Raster Images_.

To sharpen your “color intuition,” try out the [What the Hex](http://yizzle.com/whatthehex/) game.

And finally, if you want to learn more about the 2D drawing capabilities of the `canvas` element, try out this [tutorial from the Mozilla Developer Network](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial). There are also many other resources on `canvas` that can be found on the web.

## Primitives
The _primitives_ sample code shown in class is part of the starter code in this repository. It will be best to fully collaborate on this one as a group—try to spend a non-zero amount of time writing code together over a screenshare. Take turns being the sharer/driver, using commits and pushes to keep everyone in sync. You don’t have to work this way _all_ of the time but you should spent _some_ time in this mode so that everyone can get in sync on how to write the code.

For this portion of the assignment, choose and submit one of the following primitives-implementation options. They vary in difficulty; higher total points are provided for the harder ones. This isn’t guaranteed extra credit—it will only work out that way if you perform the requested task well. If you attempt a high-difficulty task but struggle mightily with it, you’ll still get scores below 100, so choose wisely. A well-done “Dye Hard” can still net you a high score and a janky “Dye Hard with a Vengeance” can end up not-so-great for you.

For these exercises, don’t worry about the usual primitive concern of minimizing operations and restricting calculations to just integers. Compute as needed, and with floating point arithmetic.

Whatever your choice, make sure that the _Primitives_ section of the demo application visually demonstrates the enhancement that you implemented.

### Dye Hard: Radial Gradient
_Implement a two-color radial gradient for rectangles:_ Modify the `fillRect` function in the _primitives_ module so that it interprets the first two colors (`c1` and `c2`), when present, as filling the given rectangle with a _radial gradient_ emanating from its center to the smaller of its two dimensions.

For example, the radial gradient a 100×40 rectangle will have a radius of 20 pixels; the radial gradient for a 30×98 rectangle will have a radius of 15 pixels.

Your new implementation may ignore the three- or four-color case: instead, just call the two-color case all the time, disregarding the extra color arguments.

_Hint:_ The overall structure of the fill does not have to change. It’s only the color calculation that needs modification.

### Dye Harder: Two-Color Polygon Fill 🌈
_Implement a linear two-color gradient for polygons:_ Modify the `fillPolygon` function in the _primitives_ module so that it accepts _two_ colors. The resulting polygon should be painted with a linear gradient from the first color at the polygon’s uppermost _y_-coordinate to the second color at the polygon’s bottom _y_-coordinate.

### Dye Hard with a Vengeance: Multicolor Polygon Fill 🧠💫 _Best Value!_…if you can do it ✨🧐
_Implement a multipoint linear gradient for polygons:_ Modify the `fillPolygon` function in the _primitives_ module so that its third argument is expected to be an _array_ of colors, one color per vertex. The resulting polygon should be painted such that each vertex is painted with exactly the color that positionally corresponds to it in the given arrays, with every other pixel transitioning smoothly across these colors.

Yes, this is not unlike the `vertexColors` feature in three.js geometry and material objects.

_Hint:_ The approach to this gradient is similar to the one for the original four-color rectangle gradient. Calculate vertical gradients based on the vertices’ _y_-coordinates, then as the algorithm scans across a row of pixels, perform a horizontal gradient from the color on the left side to the color on the right.

_Protip:_ Because there should be a one-to-one correspondence between the vertices and colors, you’ll want to enhance the `Edge` object so that it holds the vertices _and_ the corresponding colors of each edge in the polygon.

## Image Processing Filters
The _nanoshop_ and _nanoshop-neighborhood_ sample code shown in class is also part of this repository’s starter code.

### Live Free (of other pixels) or Dye Hard: Two Single-Pixel Filters
Add two (2) single-pixel filters of your own design to the _nanoshop_ module. Modify the accompanying _NanoshopDemo_ component to use these new filters.

### A Good Day (in the neighborhood) to Dye Hard: Two Neighborhood-Pixel Filters
Add two (2) neighborhood-pixel filters of your own design to the _nanoshop-neighborhood_ module. Modify the _NanoshopNeighborhoodDemo_ component to use these new filters.

Note you’ll end up with a grand total of four (4) new filters, across the two types. For the _nanoshop-neighborhood_ additions, make sure that your filters _do_ use the neighborhood pixels when computing the filtered color. A “neighborhood” filter that bases its calculations solely on the central pixel will not get credit.

## Extra Credit: Your Own 2D Canvas Drawing
You might recall that three.js creates a `canvas` element to do its 3D work. The image processing filter examples use the `canvas` element in _2D_ mode. All of the code is there (written by a former student) and if you like, you can write some new code so that the scene being drawn is different. By and large, the Mozilla Developer Network’s [`canvas` tutorial](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial) is enough to get a start.

## How to Turn it In
Commit the following to your repository:
- One (1) chosen primitive enhancement
- Two (2) single-pixel filters
- Two (2) neighborhood-pixel filters
- Corresponding modifications to the web application code that demonstrate these improvements
- (optionally) Code that creates a different `canvas` image for the filters
