---
title: Web Design Playground
description: |
  In this lab, you'll build a little app that lets people experiment with different fonts, colors and spacing in a web page.
tags:
  - jQuery
  - HTML
  - CSS
  - Basic Javascript
---

# Web Design Playground

In this lab, you'll build a little app that lets people experiment with different fonts, colors and spacing in a web page.

## HTML source

Start by creating this HTML document:

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>Web design playground</title>
  <style>
    #container {
      margin: 20px auto;
      width: 70%;
    }
    h1 {
      font: bold 25px helvetica, arial, sans-serif;
      text-align: center;
    }
    h2 {
      font: bold 20px helvetica, arial, sans-serif;
    }
    #canvas {
      border: 1px dashed #000;
      padding: 10px;
      font: 16px/18px "times new roman", times, serif;
    }
    #controls {
      display: -webkit-flex;
      display: flex;
    }
    .control {
      width: 33%;
    }
    .control ul {
      list-style: none;
      padding: 0;
    }
  </style>
</head>
<body>
  <div id="container">
    <h1>Color and font playground</h1>

    <form>
    <div id="controls">
      <div class="control">
        <h2>Font</h2>
        <ul>
          <li><label><input type="radio" name="fontname" value="arial"> Arial</label></li>
          <li><label><input type="radio" name="fontname" value="courier"> Courier</label></li>
          <li><label><input type="radio" name="fontname" value="georgia"> Georgia</label></li>
          <li><label><input type="radio" name="fontname" value="times" checked> Times New Roman</label></li>
          <li><label><input type="radio" name="fontname" value="verdana"> Verdana</label></li>
        </ul>
      </div>
      <div class="control">
        <h2>Color</h2>
        <p>Text: <input id="textcolor" type="text" name="textcolor" value="#000" size="7"></p>
        <p>Background: <input id="bgcolor" type="text" name="bgcolor" value="#fff" size="7"></p>
      </div>
      <div class="control">
        <h2>Spacing</h2>
        <p>Text size: <input id="textsize" type="text" name="textsize" value="16" size="5"></p>
        <p>Line height: <input id="lineheight" type="text" name="lineheight" value="18" size="5"></p>
        <p>Padding: <input id="textpadding" type="text" name="textpadding" value="10" size="5"></p>

      </div>
    </div>
    </form>

    <div id="canvas">
      Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
    </div>

  </div>
<script>
// JavaScript goes here.
</script>
</body>
</html>
```

Add the above source to a new file called `index.html` and put it in a new
folder: `~/Code/JavaScript/playground-jquery`. Save that into a Git repository,
following the same steps you took in previous lessons.

View `index.html` in your web browser. You'll see three sections -- font, color, spacing --
with various parameters you can tweak. Then you'll see some sample "lorem ipsum" text, in an
area we'll call the "canvas."

Try clicking the font names and entering different values in the color and spacing sections.
Nothing happens yet. Your task is to implement these, so that changing the font/color/spacing
controls will update the canvas with the appropriate CSS styles.

## Adding jQuery

To add jQuery, add the following to the `<head>` of the HTML document, under the closing
`</style>` tag:

```html
<script src="https://code.jquery.com/jquery-2.2.3.min.js" integrity="sha256-a23g1Nt4dtEYOj7bR+vTu7+T8VP13humZFBJNIYoEJo=" crossorigin="anonymous"></script>
```

Save into Git, as always.

## Adding an onready handler

All of our JavaScript logic will go at the bottom of the page, where you see "JavaScript goes here."
Replace that with this code:

```js
$(document).ready(function() {
  // Code here will run when the page has loaded.
});
```

This gives you a place to put the JavaScript to execute when the page loads.

## Implementing the "Font" radio buttons

With that infrastructure out of the way, let's tackle the first feature: font changing. The goal is
to change the font of `<div id="canvas">` depending on which font is selected in the "Font" section.
These are called radio buttons -- UI elements that are used when there's a list of mutually
exclusive options.

To make the radio buttons respond to user input, we first select them:

```js
$('input[type=radio][name=fontname]')
```

This means "select all `<input>` tags that have a 'type' attribute equal to 'radio' and a 'name'
attribute equal to 'fontname'."

Then we use jQuery's `change()` method to provide a callback. First, let's just make sure we have
the syntax right, by using `console.log()`. Put this in the `ready()` handler:

```js
$('input[type=radio][name=fontname]').change(function(e) {
  console.log(e.target.value);
})
```

Save the document and reload the page in your browser. Make sure the JavaScript console is open,
and click the font names. Each time you click on a font, you should see a font code (like "arial")
appear in the console.

It's a good idea to start with baby steps like this -- using `console.log()` each step of the way --
to ensure that everything is working so far. It's like constructing a building. First, you make the beams
that support everything, and you test them to make sure they can support a lot of weight, before adding
walls and everything else.

Now that we've confirmed the `change()` handler is working, we can change it to do the proper logic.
Specifically, we want to change the CSS font style, for `<div id="canvas">`, to whatever font has
been selected. Here's how to do it:

```js
$('#canvas').css('font-family', e.target.value);
```

Put that in the event handler, then save the page and reload it. Clicking the font names should now
change the font of the canvas dynamically. Nice!

## Implementing the color changer

The "Color" section uses `<input type="text">` instead of `<input type="radio">` -- but the logic is
basically the same. We want to change the color of the #canvas text to whatever color (a hex value)
has been specified in the "Text:" `<input>`. Note this `<input>` has an ID: `textcolor`.

Here's how we can do it:

```js
$('#textcolor').change(function(e) {
  $('#canvas').css('color', e.target.value);
});
```

As with the font name radio, this translates to: "Whenever the value of #textcolor changes, update
the CSS 'color' of #canvas to whatever value is in #textcolor."

Save that, reload the page, and test it. Note that the `change()` event doesn't fire until you
click *away* from the form element. So you'll need to enter a new color, then click outside the input
element (or hit the Tab key), for `change()` to be called.

## Implementing the other controls

The other controls all follow the same logic: just add a handler to each input element that makes the
appropriate CSS change to `#canvas`. Here is a cheat sheet of the CSS properties you'll want to set:

* font-family
* color
* background-color
* font-size
* line-height
* padding

Note that `font-size`, `line-height` and `padding` values should be in pixels! So you'll need to append
`'px'` to the integer value before passing to the `css()` method.

## Extra adventures

If you finish early and want to make your app even better, here are some extra challenges.

* Each one of those event handlers has `$('#canvas')`, which means "retrieve the element with ID #canvas."
It's a bit wasteful to look it up every time -- you're making the browser do extra work that it doesn't
necessarily need to do, because the element never changes. Try improving this by retrieving
`$('#canvas')` at time of page load, and saving it into a `canvas` variable. Then change your event
handlers to use the `canvas` variable instead of looking it up.

* Technically this page has some duplicated data: the `<style>` section contains the initial font,
colors and padding for `#canvas`. It's generally a good idea to remove duplication in your code,
so that all data lives in only a *single* place. This is called the "Don't Repeat Yourself" principle.
See if you can remove the duplication. (Hint: try setting the styles in JavaScript at time of page load,
based on the initial form values.)

* As mentioned earlier, for `<input type="text">` elements, jQuery's `change()` event only gets called
when the element loses focus -- that is, when the user clicks (or tabs) away from the element. See if
you can figure out how to change the styles *immediately* when the user types into the `<input>` elements,
rather than waiting until the user clicks away. (Hint: look at the jQuery `keydown()` method.)

* At the moment, all of the `<input type="text">` elements -- text color, padding, etc. -- allow you to
enter *any* crazy value! It would be a nicer user experience if the app disallowed invalid values. Try to
add validation. As a first step, validate the data; if it's invalid, don't change the CSS. Then, once
you've implemented that, display an error message if the data is invalid. Make sure to clear the error message
if the user types in different data. (Hint: you can use a regular expression to validate the color hex values.)

* Try adding the font "Impact" to the list of available fonts. (You probably have this installed on your computer,
but if you don't, then it won't work! In that case, pick a different font that you *do* have installed.)

* Try adding some extra controls: a checkbox for underlining the text (`'text-decoration'` = `'underline'` vs. `'none'`),
a checkbox for toggling small caps (`'font-variant'` = `'small-caps'` vs. `'normal'`), and a checkbox for bolding the
text (`'font-weight'` = `'bold'` vs. `'normal'`). And if you know other CSS properties you'd like to include, try those
too!

* `<input type="range">` can be a nicer UI for selecting numeric values -- it's represented as a nice sliding scale.
Try converting the numeric inputs (text size, line height and padding) to use `<input type="range">`.

* Add a way to "export" the user's font/color/spacing preferences as CSS. For example, make an "export CSS" button
that displays the current preferences as properly formatted CSS, at the bottom of the page.
