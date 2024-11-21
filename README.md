# 🎨 p5.js Cheatsheet for beginners

*If you like this cheatsheet, please give me a star ⭐️ on [GitHub](https://github.com/suroot/p5js-cheatsheet)!*

Version 1.0

By Tianyu (Sky) Lu  
@ UW-Madison CS402 Introducing Computer Science to K-12 Students, Fall 2024  
tlu83@wisc.edu  
11/20/2024  

**Released under** [![CC BY-SA 4.0](https://mirrors.creativecommons.org/presskit/buttons/80x15/svg/by-sa.svg)](https://creativecommons.org/licenses/by-sa/4.0/)

Note: This cheatsheet is designed for K-12 students, so some terminology is **intentionally simplified** (even "unprofessional") to be easy to understand.

# 🔰 JavaScript Programming Basics

## 🔤 Variable Types

1. `number`: a number, can be an integer or a decimal.  
   Examples: `1`, `2`, `3.14`, `-10`, `0.001`, etc.

2. `string`: a sequence of character(s) enclosed by quotes. We do not distinguish between character and string in javascript, so a single character is also a string.  
   Examples: `"Hello"`, `"123"`, `'a'`, `'🦁'`, etc.

3. `array`: a collection of values, enclosed by square brackets. Values can be of any type, you can even put different types of values (even arrays!) in the same array.  
   Examples: `[1, 2, 3]`, `["a", "b", "c"]`, `["🦁", "🐯", "🐻"]`, `[1, 'a', ['b', 'c']]`, etc.

## 📝 Variable Declaration

In javascript, we use `let` to declare a variable.

```javascript
let a = 1;
let b = "Hello";
let c = [1, 2, 3];
```

# 📚 Function Blocks

## 🌟 Essential Function Blocks

1. `function preload() { }`

   Load images, sounds, or files before setup. Your sketch waits for everything to load.

   ```javascript
   let myImageFromFile;
   let myImageFromWeb;
   let mySoundFromFile;
   let mySoundFromWeb;
   function preload() {
     // Load things before your sketch starts
     myImageFromFile = loadImage("/assets/cat.jpg");  // Load an image from assets folder
     myImageFromWeb = loadImage("https://upload.wikimedia.org/wikipedia/commons/thumb/5/5e/Domestic_Cat_Face_Shot.jpg/320px-Domestic_Cat_Face_Shot.jpg");  // Load an image from a web URL
     mySoundFromFile = loadSound("/assets/meow.mp3");  // Load a sound from assets folder
     mySoundFromWeb = loadSound("https://upload.wikimedia.org/wikipedia/commons/0/0c/Meow_domestic_cat.ogg");  // Load a sound from a web URL
   }
   ```

2. `function setup() { }`

   This is where you set up your canvas. It runs **once** at the start.

   ```javascript
   function setup() {
     createCanvas(400, 400);  // Make a canvas
     background("white");  // Set background color
     // Any other one-time setup goes here
   }
   ```

3. `function draw() { }`

   This **repeats** over and over, creating animation. It's like a movie loop!

   ```javascript
   function draw() {
     circle(mouseX, mouseY, 20);  // Drawing follows your mouse
   }
   ```

   ```javascript
   function draw() {
     background(220);  // Clear canvas each frame
     rect(frameCount % width, 200, 50, 50);  // Moving square
   }
   ```

## 🎯 Event Function Blocks

0. Built-in global variables:
- `mouseX`: latest horizontal position of the mouse
- `mouseY`: latest vertical position of the mouse
- `key`: latest key that is pressed

1. `function mousePressed() { }`

   Runs whenever you click your mouse.

   ```javascript
   function mousePressed() {
     // Do something when mouse is clicked
     fill(random(255), random(255), random(255));  // Random color
     circle(mouseX, mouseY, 50);  // Draw circle where clicked
   }
   ```

2. `function keyPressed() { }`

   Runs whenever you press a keyboard key.

   ```javascript
   function keyPressed() {
     // Do something when a key is pressed
     if (key === 'c') {
       background(random(255), random(255), random(255));  // Clear canvas with random color when 'c' is pressed
     }
   }
   ```

## 💡 Tips for Using Function Blocks

0. **In the function block!
You MUST write all the codes inside the function blocks!**

1. **Order Matters!**
   - `preload()` runs first
   - Then `setup()` runs once
   - Then `draw()` runs over and over
   - Event functions run when triggered

2. **When to Use Background()**
   - In `setup()`: Sets initial background
   - In `draw()`: Clears screen each frame
   - Not using it: Drawings stay forever

3. **Variables and Function Blocks**
   - Variables outside blocks: Available everywhere
   - Variables inside blocks: Only available in that block
   - Use `let` to create variables

4. **Common Mistakes to Avoid**
   - Don't put `createCanvas()` in `draw()`
   - Don't forget `background()` for animations
   - Remember that `draw()` repeats forever

# 🎬 Canvas Setup Methods

1. `createCanvas(width, height)`

   Creates a drawing canvas of specified width and height in pixels.

   Parameters:
   - `width`: **number**, the width of the canvas
   - `height`: **number**, the height of the canvas

   ```javascript
   createCanvas(400, 400);  // Creates a square canvas 400x400 pixels
   createCanvas(800, 400);  // Creates a wide rectangle canvas 800x400 pixels
   ```

2. `background(color)` or `background(r, g, b)`

   Sets the background color of the canvas.

   Parameters:
   - `color`: the color of the background
     - **string**: a color name, e.g., `"white"`, `"skyblue"`, `"red"`, `"green"`, `"blue"`, etc.
     - **number**: a hex color code, e.g., `#FFFFFF` for white, `#0000FF` for blue, `#FF0000` for red, etc.
   - `r`, `g`, `b`: the separate RGB values of the background color
     - `r`: **number**, the **R**ed value of the background color, range from 0 to 255
     - `g`: **number**, the **G**reen value of the background color, range from 0 to 255
     - `b`: **number**, the **B**lue value of the background color, range from 0 to 255

   ```javascript
   background("skyblue");  // Makes a blue sky colored background
   background("#FFFFFF");  // Makes a white background
   background(255, 192, 203);  // Makes a pink background
   ```

# 🎨 Drawing Methods

*Note: In the following methods, we use* **400x400** *canvas as an example.*

## ✨ Style Setting Methods

The style setting methods works differently in two cases:
   - If you never used the method before: it will set the setting for all shapes.
   - If you have already used the method before: it will set the setting for **shapes that will be drawn later** (it will not affect the shapes that have already been drawn).

1. `fill(color)` or `fill(r, g, b)`

   Sets the fill color for shapes.

   Parameters:
   - `color`: the color of the background
     - **string**: a color name, e.g., `"white"`, `"skyblue"`, `"red"`, `"green"`, `"blue"`, etc.
     - **number**: a hex color code, e.g., `#FFFFFF` for white, `#0000FF` for blue, `#FF0000` for red, etc.
   - `r`, `g`, `b`: the separate RGB values of the background color
     - `r`: **number**, the **R**ed value of the background color, range from 0 to 255
     - `g`: **number**, the **G**reen value of the background color, range from 0 to 255
     - `b`: **number**, the **B**lue value of the background color, range from 0 to 255

   ```javascript
   fill("red");
   circle(100, 100, 50);  // Draws a circle with red fill
   ```

   ```javascript
   fill("#0000FF");
   circle(200, 200, 50);  // Draws a circle with blue fill
   ```

   ```javascript
   fill(255, 192, 203);
   circle(300, 300, 50);  // Draws a circle with pink fill
   ```

2. `stroke(color)` or `stroke(r, g, b)`

   Sets the outline color for shapes.

   Parameters:
   - `color`: the color of the background
     - **string**: a color name, e.g., `"white"`, `"skyblue"`, `"red"`, `"green"`, `"blue"`, etc.
     - **number**: a hex color code, e.g., `#FFFFFF` for white, `#0000FF` for blue, `#FF0000` for red, etc.
   - `r`, `g`, `b`: the separate RGB values of the background color
     - `r`: **number**, the **R**ed value of the background color, range from 0 to 255
     - `g`: **number**, the **G**reen value of the background color, range from 0 to 255
     - `b`: **number**, the **B**lue value of the background color, range from 0 to 255

   ```javascript
   stroke("blue");
   circle(100, 100, 50);  // Draws a circle with blue outline
   ```

   ```javascript
   stroke(255, 0, 0);
   circle(200, 200, 50);  // Draws a circle with red outline
   ```

3. `strokeWeight(weight)`

   Sets how thick lines are (including outlines).

   Parameter:
   - `weight`: **number**, the weight of the lines, default is 1. If you set it to 0, the outline will not be drawn. Otherwise, the larger the number, the thicker the line.

   ```javascript
   strokeWeight(10);  // Makes thick lines
   circle(200, 200, 50);  // Draws a circle with thick outline
   ```

   ```javascript
   strokeWeight(1);  // Makes thin lines
   line(100, 100, 300, 300);  // Draws a thin line
   ```

## 📐 Basic Shape Methods

1. `circle(x, y, size)`

   Draws a circle centered at position (x,y) with given diameter.

   Parameters:
   - `x`: **number**, the horizontal position of the circle center
   - `y`: **number**, the vertical position of the circle center
   - `size`: **number**, the size of the circle (diameter)

   ```javascript
   circle(200, 200, 50);
   circle(100, 100, 100);
   ```

2. `rect(x, y, width, height)`

   Draws a rectangle with top-left corner at (x,y).

   Parameters:
   - `x`: **number**, the horizontal position of the rectangle top-left corner
   - `y`: **number**, the vertical position of the rectangle top-left corner
   - `width`: **number**, the width of the rectangle
   - `height`: **number**, the height of the rectangle

   ```javascript
   rect(100, 100, 200, 100);
   rect(150, 150, 50, 50);
   ```

3. `ellipse(x, y, width, height)`

   Draws an oval centered at position (x,y).

   Parameters:
   - `x`: **number**, the horizontal position of the oval center
   - `y`: **number**, the vertical position of the oval center
   - `width`: **number**, the width of the oval
   - `height`: **number**, the height of the oval

   ```javascript
   ellipse(200, 200, 100, 50);  // Draws a wide oval
   ellipse(200, 200, 50, 100);  // Draws a tall oval
   ```

4. `arc(x, y, width, height, start, stop)`

   Draws part of a oval.

   Parameters:
   - `x`, `y`: **number**, the (x,y) coordinates of the oval center
   - `width`, `height`: **number**, the width and height of the oval
   - `start`, `stop`: **number**, the start and stop angles of the arc, in radians

   ```javascript
   arc(200, 200, 100, 50, 0, PI);  // Draws a smile shape
   arc(200, 200, 100, 50, PI, TWO_PI);  // Draws an upside-down smile
   ```

   If you do not know what **radian** is, that's totally fine! **Radian** is a way to measure the angle of the arc, just like **degree**. You can use the following formula to convert degree to radian:
   $$
   \text{radian} = \frac{\text{degree}}{180} \times \text{PI}
   $$

   ```javascript
   arc(200, 200, 100, 50, 0/180 * PI, 180/180 * PI);  // Draws a smile shape
   arc(200, 200, 100, 50, 180/180 * PI, 360/180 * PI);  // Draws an upside-down smile
   ```

5. `point(x, y)`

   Draws a single point.

   Parameters:
   - `x`, `y`: **number**, the (x,y) coordinates of the point.

   ```javascript
   point(200, 200);  // Draws a dot in the center
   point(mouseX, mouseY);  // Draws a dot at mouse position
   ```

6. `line(x1, y1, x2, y2)`

   Draws a straight line between two points.

   Parameters:
   - `x1`, `y1`: **number**, the (x,y) coordinates of the line start point
   - `x2`, `y2`: **number**, the (x,y) coordinates of the line end point

   ```javascript
   line(100, 100, 300, 300);  // Draws a diagonal line from top-left to bottom-right
   line(0, 200, 400, 200);  // Draws a horizontal line across the middle
   ```

7. `triangle(x1, y1, x2, y2, x3, y3)`

   Draws a triangle connecting three points.

   Parameters:
   - `x1`, `y1`: **number**, the (x,y) coordinates of the first point
   - `x2`, `y2`: **number**, the (x,y) coordinates of the second point
   - `x3`, `y3`: **number**, the (x,y) coordinates of the third point

   ```javascript
   triangle(200, 100, 100, 300, 300, 300);  // Draws a triangle pointing up
   triangle(100, 100, 300, 100, 200, 300);  // Draws a triangle pointing down
   ```

## ✍️ Text Methods

1. `text(message, x, y)`

   Draws text at position (x,y).

   Parameters:
   - `message`: **string**, the text message to be displayed.
   - `x`, `y`: **number**, the (x,y) coordinates of the text position (bottom-left corner of the text).

   ```javascript
   text("Hello!", 200, 200);  // Writes "Hello!" in the middle
   text("World!", 100, 100);  // Writes "World!" in top-left
   ```

2. `textSize(size)`

   Changes how big the text is.

   Parameter:
   - `size`: **number**, the size of the text, default is 12. The larger the number, the bigger the text.

   ```javascript
   textSize(10);
   text("Hello!", 200, 200);
   ```

   ```javascript
   textSize(64);
   text("World!", 100, 100);
   ```

3. `textAlign(alignment)`

   Changes how text lines up with its position.

   Parameters:
   - `alignment`: **string**, the horizontal alignment of the text.
     - `LEFT`: left-aligns the text at the given position.
     - `CENTER`: centers the text at the given position.
     - `RIGHT`: right-aligns the text at the given position.

   ```javascript
   textAlign(LEFT);
   text("[二二二]", 200, 200);
   ```

   ```javascript
   textAlign(CENTER);
   text("[二二二]", 200, 200);
   ```

   ```javascript
   textAlign(RIGHT);
   text("[二二二]", 200, 200);
   ```

4. `textFont(font)`

   Changes the text font.

   Parameters:
   - `font`: **string**, the name of the font.

   ```javascript
   textFont("Arial");
   text("Hello!", 200, 200);
   ```

   ```javascript
   textFont("Comic Sans MS");
   text("Hello!", 200, 200);
   ```

5. `textStyle(style)`

   Makes text bold, italic, or normal.

   Parameters:
   - `style`: **string**, the style of the text.
     - `NORMAL`: makes the text normal.
     - `ITALIC`: makes the text italic.
     - `BOLD`: makes the text bold.
     - `BOLDITALIC`: makes the text bold and italic.

   ```javascript
   textStyle(BOLD);
   text("Hello!", 200, 200);
   ```

   ```javascript
   textStyle(ITALIC);
   text("Hello!", 200, 200);
   ```

# 📦 Object Methods

## 🖼️ Image Methods

1. `loadImage(link)`

   Loads an image to use in your sketch.  
   **You must load the image in `preload()` before using it.**

   Parameters:
   - `link`: **string**, the link of the image to be loaded. Two links are supported:
     - **local link**: the link of the image in the assets folder, e.g., `/assets/cat.jpg`.
     - **web link**: the link of the image in the web, e.g., `https://upload.wikimedia.org/wikipedia/commons/thumb/5/5e/Domestic_Cat_Face_Shot.jpg/320px-Domestic_Cat_Face_Shot.jpg`.

   ```javascript
   let img;
   function preload() {
     img = loadImage("/assets/cat.jpg");  // Load an image from assets folder
   }
   ```

2. `image(img, x, y)`

   Draws an image at position (x,y) (top-left corner of the image).

   Parameters:
   - `img`: **image**, the image **object** to be drawn.
   - `x`, `y`: **number**, the (x,y) coordinates of the image position (top-left corner of the image).

   ```javascript
   let img;
   function preload() {
     img = loadImage("https://upload.wikimedia.org/wikipedia/commons/thumb/5/5e/Domestic_Cat_Face_Shot.jpg/320px-Domestic_Cat_Face_Shot.jpg");  // Load an image from a web URL
   }

   function draw() {
      background("white");
      image(img, mouseX, mouseY);  // Makes image follow mouse
   }
   ```

3. `image(img, x, y, width, height)`

   Draws an image with custom size.

   Parameters:
   - `img`: **image**, the image **object** to be drawn.
   - `x`, `y`: **number**, the (x,y) coordinates of the image position (top-left corner of the image).
   - `width`, `height`: **number**, the width and height of the image.

   ```javascript
   let img;
   function preload() {
     img = loadImage("https://upload.wikimedia.org/wikipedia/commons/thumb/5/5e/Domestic_Cat_Face_Shot.jpg/320px-Domestic_Cat_Face_Shot.jpg");  // Load an image from a web URL
   }

   function draw() {
      background("white");
      image(img, mouseX, mouseY, 100, 100);
   }
   ```

4. `tint(color)` or `tint(r, g, b, alpha)`

   Colors the images you draw.

   Parameters:
   - `color`: the color of the tint
     - **string**: a color name, e.g., `"white"`, `"skyblue"`, `"red"`, `"green"`, `"blue"`, etc.
     - **number**: a hex color code, e.g., `#FFFFFF` for white, `#0000FF` for blue, `#FF0000` for red, etc.
   - `r`, `g`, `b`: the separate RGB values of the tint color
     - `r`: **number**, the **R**ed value of the tint color, range from 0 to 255
     - `g`: **number**, the **G**reen value of the tint color, range from 0 to 255
     - `b`: **number**, the **B**lue value of the tint color, range from 0 to 255
     - `alpha`: **number**, the transparency of the image, range from 0 to 255, default is 255 (fully opaque).

   ```javascript
   let img;
   function preload() {
     img = loadImage("https://upload.wikimedia.org/wikipedia/commons/thumb/5/5e/Domestic_Cat_Face_Shot.jpg/320px-Domestic_Cat_Face_Shot.jpg");  // Load an image from a web URL
   }

   function draw() {
      background("white");
      image(img, 50, 50);
      tint("yellow");
   }
   ```

   ```javascript
   let img;
   function preload() {
     img = loadImage("https://upload.wikimedia.org/wikipedia/commons/thumb/5/5e/Domestic_Cat_Face_Shot.jpg/320px-Domestic_Cat_Face_Shot.jpg");  // Load an image from a web URL
   }

   function draw() {
      background("white");
      image(img, 50, 50);
      tint(255, 255, 255, 126); // Makes image semi-transparent
   }
   ```

# 🛠️ Other Useful Methods

## 🎲 Random Methods

1. `random(max)`

   Gives a random number between 0 and max (not including max).

   Parameter:
   - `max`: **number**, random number should be less than this number.

   ```javascript
   circle(random(400), 200, 50);  // Draws circle at random X position
   circle(200, 200, random(100));  // Draws circle with random size
   ```

2. `random(min, max)`

   Gives a random number between min and max (not including max).

   Parameters:
   - `min`: **number**, random number should be equal to or greater than this number.
   - `max`: **number**, random number should be less than this number.

   ```javascript
   circle(200, random(100, 300), 50);  // Draws circle at random Y position between 100 and 300
   ```

3. `random(array)`

   Gives a random element from an array.

   Parameter:
   - `array`: **array**, the array to choose a random element from.

   ```javascript
   let animals = ['🦁', '🐯', '🐻', '🐶', '🐱', '🐹', '🐰', '🦊', '🐼', '🐸', '🐵'];
   text(random(animals), 200, 200);
   ```

## 🔁 Drawing Loop Control Methods

1. `noLoop()`

   Stops the program from continuously drawing.

2. `loop()`

   Restarts the program to continuously draw.
