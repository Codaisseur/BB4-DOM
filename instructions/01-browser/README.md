---
title: Rediscover the Browser
description: |
  Learn to become a browser power-user.
---

# Inspect the page

Your browser is a complex piece of software. It takes HTML and CSS and produces a working, interactive web-page. Let's have a look under the hood.

Since you're probably using Chrome to read this right now: Simply **right-click** on the following box to open the context menu, and then choose **'Inspect'**.

<div style="padding: 1rem; border: 2px solid black; border-radius: 1rem; width: 7rem; margin: auto; text-align: center">
  Inspect Me!!
  <div style="display: none">HELLO! IF YOU CAN READ THIS THEN YOU'RE PROBABLY LOOKING AT THE HTML IN CHROME DevTools!!</div>
</div>

When inspecting the element you'll be looking at the HTML structure of the current page. The element that your mouse pointer was pointing at when you clicked on *inspect* should be highlighted in the window. Now open/expand that element and keep going until you find a secret hidden message!

<img src="https://cd.sseu.re/Developer_Tools_-_http___solutiondriven.nl_3000_courses_beginner-bootcamp_04-dom-jquery-ajax_01-browser_2018-03-09_11.39.15.png"/>

# Meet Chrome DevTools

When you complete the previous step you'll be looking at and using the Chrome DevTools (which stands for... Developer Tools). **You and DevTools should become good friends. 👫** Learning to use DevTools early and often will make your life as a developer *much* easier. The first thing we did was explore the HTML structure. You may have noticed you can also see all the CSS rules for each element. We will be using DevTools for the rest of this course... as well as the rest of our lives as developers.

> All modern browsers have similar tools for inspecting pages and helping general web-development.
>
> 🌟 How to open DevTools in other browsers
>
> **Chrome Console Keyboard Shortcuts**
>
> + 🍎 Mac Users: <kbd>Cmd</kbd> + <kbd>Opt</kbd> + <kbd>J</kbd>
> + 🐧 Ubuntu Users: <kbd>CTRL</kbd> + <kbd>Shift</kbd> + <kbd>J</kbd>
>
> **Firefox Keyboard Shortcuts**
>
> + 🍎 Mac Users: <kbd>Cmd</kbd> + <kbd>Opt</kbd> + <kbd>K</kbd>
> + 🐧 Ubuntu Users: <kbd>CTRL</kbd> + <kbd>Shift</kbd> + <kbd>K</kbd>
>
> **Safari Console Keyboard Shortcuts**
>
> + 🍎 Mac Users: <kbd>Cmd</kbd> + <kbd>Opt</kbd> + <kbd>C</kbd>

# JavaScript Console

At the top of the DevTools window there's also an item labelled **Console**. The console is a place where you can write JavaScript and the browser will run it once you finish the code and press enter. These days all browsers know how to run JavaScript!

<img src="https://cd.sseu.re/Developer_Tools_-_http___solutiondriven.nl_3000_courses_beginner-bootcamp_04-dom-jquery-ajax_01-browser_2018-03-09_11.47.09.png"/>

Let's look at an example to display a dialog box. First type the code in charge of doing that in the console:

[![](https://cd.sseu.re/20170121-3l23u.png)](https://cd.sseu.re/20170121-3l23u.png)

When you press enter, you should see dialog box appear:

[![](https://cd.sseu.re/20170121-r5jsw.png)](https://cd.sseu.re/20170121-r5jsw.png)

# Meet the DOM

You might not have been aware, but when you used `window.alert` you were using the **DOM**. It stands for *Document Object Model*. The DOM is how JavaScript interacts with the page and the rest of the browser. Our code would be useless if it could not interact with the page.
