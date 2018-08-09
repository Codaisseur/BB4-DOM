---
title: Manipulating the DOM
---

# ✍️ Manipulating to the DOM

We saw how to get references to HTML elements in the page. Once you have that you can start modifying the DOM in different ways:

## ⚡ Change properties on HTML elements  
 
The HTML elements in the DOM are JavaScript objects with different properties. The properties are represented with keys and values just like ordinary JavaScript objects.

<div>
<a id="test-link-123" href="#" style="font-size: 2em">I'm a link!</a>
</div>

The id for this link is `test-link-123`. Try finding (getting a reference to) the link element, by typing in the DevTools console using:

+ `document.getElementById`
+ `document.querySelector` (remember that this function takes a CSS selector)

```js
// In your console try:
var linkElement = ... // use getElementById or querySelector to select the link element
console.log(linkElement) 

// have a look at some of the properties of this link
linkElement.innerText
linkElement.href
linkElement.style
```

Let's change some of the properties of the link by `reassigning` them

```js
// Try these one by one
linkElement.innerText = "I have changed the innerText!"
linkElement.style.backgroundColor = "red"

linkElement.innerHTML = '<h1>Header inside my link</h1>';
```
> ✍️ DIY:  
> Try to change the font-size of the link by reassigning the style\["font-size"\] property of the linkElement. Make sure to assign it a value ending with `px` or `em`. 

## ☎️ Call methods on HTML elements  

Because HTML elements in the DOM are JavaScript objects you can call methods on them. The elements in the DOM have a lot of methods already built in. 
Let's try it with this link. 

<div>
<a id="test-link-456" href="#" style="font-size: 2em">I'm another link!</a>
</div>

Its id is `test-link-456`.

```js
// In your console try:
var linkElement = ... // use getElementById or querySelector to select the link element
console.log(linkElement) 

// let's call some methods on this element. What do you think they will do?
linkElement.removeAttribute("href")
linkElement.click()
linkElement.hasAttribute("href")
linkElement.cloneNode()
```

> ✍️ DIY:  
> Try the above methods out in your javascript console!

## 🆕  Creating new HTML elements

We saw how to manipulate existing HTML elements on our page. Now lets create some new elements on the page using JavaScript. Check the following example:

```js
// create a new div element 
const newDiv = document.createElement("div"); 
// and give it some content 
const newContent = document.createTextNode("Hi there and greetings!"); 
// add the text node to the newly created div
newDiv.appendChild(newContent);  
```

This seems a bit roundabout, but it's the *official* way to create an element and adding text inside it. Run this code in the console. Do you see anything happen? Where is the `<div>`? By calling `document.createElement` we can create HTML without showing it anywhere. This can be useful in some rare cases. If we want to show it, we have to add it as a child to an existing HTML element. We can do this several ways.

```js
var someExistingElement = document.getElementById(...);
// Similar to what we saw when adding the text node in the previous snippet.
someExistingElement.appendChild(newDiv);
// or replace an existing child element
someExistingElement.replaceChild(newDiv, oldChildToBeRemoved);
// or using this very flexible function
someExistingElement.insertAdjacentElement('beforeend', newDiv);
```

> ✍️ DIY:  
> Try appending the `newDiv` from before to the following block, whose id is `append-greeting-id`.

<div id="append-greeting-id" style="border: 1px solid black; padding: 0.5rem;">
<h4>Append the greeting here:</h4>
</div>

