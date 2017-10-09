# Conditional love

## Objectives

1. Understand how String comparisons work.
2. Take input from a user in p5  
3. Manipulate strings with built in methods

## User input

Any non-trivial application will have to take input from users. To accomplish this in p5 takes a little bit of setup. In this application, we'll build a small quiz that teaches users about its creator.

This means we'll need to take in user input, which requires one more library - p5.dom. Get started by typing `git clone https://github.com/Jastor11/javascript-conditional-love.git` and then `cd javascript-conditional-love` into your terminal.

Your `index.html` file should look like this:

```html
<!DOCTYPE html>
<html lang="en-us">
  <head>
    <meta charset="utf-8">
	  <title>p5 Project</title>
	  <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.5.7/p5.js"></script>
	  <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.5.14/addons/p5.dom.min.js" ></script>
    <script type="text/javascript" src="sketch.js"></script>
  </head>
  <body>

  </body>
</html>
```

Your `sketch.js` file should start off like this:

```javascript
var input

function preload(){}

function setup() {
  createCanvas(800, 600)
}

function draw() {
  background('white')
  textSize(16)
  text('Conditional Love', 350, 25)
}
```

If you preview your `index.html` file you'll see that we've been able to place text on the screen using the `text()` function.

Next, we'll update our setup function to display an input. We can grab the value by using  `input.value()`.

```javascript
var input

function preload(){}

function setup() {
  createCanvas(800, 600)
  input = createInput()
  input.position(350, 140)  
}

function draw() {
  background('white')
  textSize(16)
  text('Conditional Love', 350, 25)
  text('You entered: ' + input.value(), 350, 190)
}
```

Type something into the input and see what happens. Cool!

Now that we have that working, let's build out our quiz.

But before we get this application working, we'll need to know a little bit about how strings work.

## Strings

Strings are a collection of letters, numbers and punctuation. You can write anything in a string as long as you put single or double quotation marks around it (ex. `"I'm a string of characters."` or `'@#$%okhaibai'`).

We see string data types in things like text messages, word documents, or blog posts, among many others.

## Concatenation

Concatenation is Latin for 'to combine together'. In Javascript, this is the name we give to combining strings together.

To add strings to each other, we use the plus sign operator `+`. This adds whatever is on the right side of the `+` to whatever was on the left side. ***Be careful*** with spaces!

```javascript
"george" + "michaels" // georgemichaels

var song = "careless"

song + " " + "whispers" // careless whispers
```

## Comparing strings

Comparing two string values can be tricky. There are a few points that need to be considered.

To compare whether two strings are the same, we can use the triple equals sign `===`.

```javascript
var secret = 'cheese is yummy'

secret === 'cheese is yummy' // true

'happiness' === 'money' // false
```

***Beware!*** Capital letters and lower case letters are NOT the same.

```javascript
"Yelling." === "YELLING." // false

var mood = "I LIKE NETFLIX"

mood === "i like netflix" // false
```

Also, the type of data being compared matters. Comparing Numbers and Strings with `===` will evaluate to false.

```javascript
9 === "9" // false
"1" === "one" // false
"42" === "42" // true
```

## String Methods

In Javascript, we can convert a string to all caps by using .toUpperCase(), and .toLowerCase() (ex. `'HELLO'.toLowerCase() // 'hello'`) to convert any string to all lowercase. These are called String Methods.

```javascript
"i like turtles".toUpperCase() // "I LIKE TURTLES"
"TOY STORY 2 WAS ONLY OK.".toLowerCase() // "toy story 2 was only ok."

var allCaps = "YO!"

allCaps.toLowerCase() === "yo!" // true

var shush = 'quietly clean up your area'

shush.toUpperCase() === 'QUIETLY CLEAN UP YOUR AREA.' // true
```

## The application

WHEW. Ok, that was a lot. Don't worry about trying to remember all of this. Refer back to this guide whenever you get to something you don't remember how to do.

Let's go ahead and bring everything together. Add a conditional statement to the `draw()` function so to check whether the user's input is `===` to the correct answer and display different values accordingly.

```javascript
var input

function setup() {
  createCanvas(800, 600)
  input = createInput()
  input.position(350, 140)  
}

function draw() {
  background('white')
  textSize(16)
  text('Conditional Love', 350, 25)
  text('Who is my favorite pop star?', 350, 80)
  text('You entered: ' + input.value(), 350, 190)

  if ( input.value() === "Shakira" ) {
    text('You answered correctly!', 350, 250)
  } else {
    text('Your answer is incorrect.', 350, 250)
  }
}
```

# Adding Images and Next Steps

Pretty nice. We could definitely spice this up a little bit though. First, let's declare the variables `noImg, yesImg, and correctQuestions`  and define a `preload()` function. Inside the `preload()` function, load in the two images in the current directory.

Then, we'll check to see what round it is, and display different images for correct and incorrect answers.

```javascript
var input
var noImg
var yesImg
var correctQuestions = 0

function preload(){
  noImg = loadImage('drake-meme-no.png')
  yesImg = loadImage('drake-meme-yes.png')
}

function setup() {
  createCanvas(800, 600)
  input = createInput()
  input.position(350, 140)  
}

function draw(){
  background('white')
  textSize(16)
  text('Conditional Love', 350, 25)
  text('Who is my favorite pop star?', 350, 80)    
  text('You entered: ' + input.value(), 350, 190)

  if ( input.value() === "Shakira" ) {
    image(yesImg, 0, 0, 300, 300)
    text('You answered correctly!', 350, 250)
  } else {
    image(noImg, 0, 0, 300, 300)
    text('Your answer is incorrect.', 350, 250)
  }      
}
```

Well, would you look at that.

We still have some problems to solve, though. Right now, if the user doesn't capitalize their answer, they'll be incorrect. Also, we have no way of adding more questions for different rounds.

Let's take care of that.

## Instructions

- Task \#1: Use string methods to ignore capitalizations for user input.
- Task \#2: Add multiple questions using if/else statements. Those questions should tell the user a few things about you.
- Task \#3: Add more images and display them when questions in later rounds are answered correctly.
- Task \#4: Build your own final scene when the user completes the quiz.
