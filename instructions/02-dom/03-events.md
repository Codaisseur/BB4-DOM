---
title: Listening for Events
---

# 👂 Listening for Events

We can now read from and write to the DOM. But reading and writing a few times doesn't make the page interactive. In order to make it interactive, we have to respond to *events*. An event is something interesting that happened on the page, like: "someone clicked on a button!". There are [lots of events](https://developer.mozilla.org/en-US/docs/Web/Events). 

Let's see what events are getting fired in our browser. Open your javascript console and use this command

```javascript
monitorEvents(document.body)
```

See if you can make the following events happen:

- mousemove
- mousedown
- click
- dblclick

When you're done use this command to stop cluttering your console

```javascript
unmonitorEvents(document.body)
```

# 🎬 Reacting to events

Now let's look at the three ways you can respond to these events. Reacting to events requires two things:

1. An `event listener` that listens for a specific event on a specific element
2. An `event handler` a javascript function that gets called when the event we are listening for gets fired

We can use add these two requirements to our page in multiple ways:

## HTML `on<event>` attributes

You can add JavaScript code inside your HTML to respond to events. Take a look at this button's HTML:

<div>
<button id="onclick-button" onclick="alert(1)" style="font-size: 1.5em; padding: 1em">Inspect this button</button>
</div>

In DevTools you should be able to see an attribute on the `<button>` element called `onclick`. The value of that attribute is some JavaScript code that gets executed when you click on the button. Try it out. 

You can add these *event listeners* to your HTML by giving the appropriate elements an attribute starting with `on` and followed by the event name (e.g. `onclick`, `onchange`, or `onsubmit`).

> ✍️ **Important:** the text value of the HTML element's attribute is a bit of JavaScript code. When the browser parses the HTML, that code becomes the body of a JavaScript function.

To illustrate the previous point. Retrieve the big button using the DOM and look at the `onclick` property. Run the following snippet in the console.

```js
const button = document.getElementById('onclick-button');
// this returns the source code of the function
button.onclick.toString();
```

You should see the source code of the function that the browser created. The code in the attribute has been wrapped inside an event handler function. Did you notice that the function has an argument with name `event`? Hmmm, let's see what that's all about. Run this code in the console to change the `onclick` attribute. We'll give it code to print the value of that `event` parameter to the console.

```js
button.setAttribute('onclick', 'console.log(event)');
```

Now click the button and see what the console says...

> Similar to the `click` event type, there are events that respond to all kinds of user actions. Move your mouse over the following block to see what happens. Then inspect it and look for the `on<event>` attribute responsible for that behavior.
> 
> <div onmouseover="this.innerText = +this.innerText + 1" style="border: 1px solid black; padding: 0.5rem; font-size: 2rem; width: 3em; margin-left: auto; margin-right: auto; text-align: center">0</div>

## The Event object

Before presenting the other ways to respond to events, we should take a moment to look at the event object. That's the object we just printed to the console in the previous step. 

When 'something interesting' happens on a web-page, the event object describes what that something is. Our functions that we make to respond to events always receive that object as a first parameter. The event object gives us access to useful information about the event. The one you'll probably use the most is [`Event.target`](https://developer.mozilla.org/en-US/docs/Web/API/Event/target) which gives you access to the HTML element on which the event was triggered. In our example, that means the `<button>` element.

# JavaScript `on<event>` properties

Inspect the following button to see the `onclick` attribute and then try clicking on it. Everything behaves as expected, right?

<div>
<button id="onclick-button2" onclick="console.log('I was here first')" style="font-size: 1.5em; padding: 1em">Another button</button>
</div>

The console contains the text we expected. Now what do you expect to happen when you run the following code and click the button again?

```js
const button2 = document.getElementById('onclick-button2');
button2.onclick = function(event) {
    console.log('I was here second');
}
```

When we assigned a function to the `onclick` property, it took precedence over the code HTML attribute. So, when the browser reads our page it initializes the DOM element for our button with an `onclick` *property* based on the `onclick` *attribute*. But afterwards we can change the property directly and we can forget about the attribute.

> ✍️ This raises an important distinction between *attributes* and *properties*. Attributes are the name & value pairs in our HTML code, and properties are part of JavaScript objects. We can read and write attributes with `getAttribute(name)` and `setAttribute(name, value)` respectively. 
> 
> Meanwhile properties on our DOM elements can be read and assigned like any other JavaScript object.

Sometimes HTML attributes have a corresponding property with the same name, which can cause confusion if you don't know the difference.

# Responding to events using `addEventListener`

The biggest disadvantage of using `on<event>` attributes and properties is that you can only have *one* event handler per element. With `addEventListener` we can add as many as we want.

<div>
<button id="onclick-button3" style="font-size: 1.5em; padding: 1em">Listen to me!</button>
</div>

Run this code in DevTools console:

```js
const button3 = document.getElementById('onclick-button3');
button3.addEventListener('click', function(event) {
    console.log('Event listener 1');
});
button3.addEventListener('click', function(event) {
    console.log('Event listener 2');
});
```

Note that we use the name of the event type we want to respond to as the first parameter. In our case `click`. You can specify any event name from the long list of options. Just make sure you specify the name and leave out the `on` prefix. That prefix is only used for the attribute and property names.

In addition to the ability to add multiple functions, the `addEventListener` method can also take a lot of advanced options that we won't go into now. Also, a small detail [taken from MDN](https://developer.mozilla.org/en-US/docs/Web/Guide/Events/Event_handlers):

> When discussing the various methods of listening to events,
> 
> + event listener refers to a function or object registered via EventTarget.addEventListener(),
> + whereas event handler refers to a function registered via on... attributes or properties.

# Event bubbling

Imaging we have a link and inside the link we have an image. If we're interested in responding to clicks on the link, should we add an event listener to the image, or to the link? The link doesn't really have much of UI, so the user will probably click on the image.

<div>
<a id="link-with-image" href="https://www.google.com/search?q=Don%27t+click+this+link+yet" target="_blank">
<img id="image-inside-link" src="https://78.media.tumblr.com/avatar_06219884487d_128.pnj">
</a>
</div>

See that image? It's surrounded by an `<a>` element. If you click it now you'll open up a new page. Now let's add some event listeners.

```js
document.getElementById('link-with-image').addEventListener('click', function(event){
    event.preventDefault();
    console.log('link clicked, target is ', event.target);
});
document.getElementById('image-inside-link').addEventListener('click', function(event){
    console.log('image clicked, target is ', event.target);
});
```

If you click on it now you'll see that *both* event listeners get called. First the image and then the event *bubbles* up (get it? just like bubbles in water) to the parent component (the link). In both cases the `event.target` points to the original element that was clicked. Event bubbling is always happening. Each event bubbles all the way to the root of the document, whether you're listening for them or not.

> ✍️ Teacher's note: Did you see the `event.preventDefault()`? That's used to stop the link from actually sending the user to the URL specified in the `href`. Some events have default behavior associated with them. Like: clicking on a link, clicking on a submit button on a form etc. By calling `preventDefault` on an event object you can *prevent* that behavior from happening.