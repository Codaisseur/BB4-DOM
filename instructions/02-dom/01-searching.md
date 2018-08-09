---
title: Searching the Page
---

# The DOM

When the browser reads an HTML file, it creates a tree-like structure of nodes. A node is a branching point containing more nodes. This tree structure is called the DOM tree, or the document object model. You can inspect the DOM to find out any information about the page. Let's have a look at how to do that.

## 🔍 Searching the DOM

Let's say we want to change some text on the page. With JavaScript in your browser, you can access and manipulate the HTML in your document. Before we can manipulate anything we need to get a reference to it first. JavaScript that runs inside the browser has access to the *root* element of the current page using a variable named `document`. Using this variable you can start searching for other elements on the page. Here are some examples.

```js
// select something with the id "flower"
// getElementById is singular it will only return 1 element
document.getElementById("flower");

// select all the paragraphs on a page (returns a collection)
document.getElementsByTagName("p");

// select all tags with the class name "LessonPage" (returns a collection)
document.getElementsByClassName("LessonPage")

// select something based on a CSS selector with querySelector methods

// Select the first element with a class 'LessonPage'
// querySelector is singular it will only return 1 element
document.querySelector('.LessonPage')

// Select all divs with the 'MuiGrid-item-1068' class (returns a collection)
document.querySelectorAll('div.MuiGrid-item-1068');
```

<p id="has-id" style="font-size: 2em">🆔 I Have an ID 🆔</p>

> Go ahead and run some of these in the DevTools JavaScript Console. **They might not all return elements**, because the page might not contain any elements that match the request. So, **play around with the arguments** to find something that does exist. Use the HTML explorer in DevTools to see which elements are available.

## Assign the results of your search to a variable

You might want to assign the results of your search for HTML elements to a variable so you can use it somewhere else in your program. 

```js
const paragraphs = document.getElementsByTagName("p");

console.log(`We have ${paragraphs.length} paragraphs on this page`)
```

> ⚠️ Warning ⚠️ 
>
> `document.getElementsByClassName`, `document.getElementsByTagName`, `document.querySelectorAll` return a collection but they are **not** Arrays
> 
> `getElements` methods return an `HTMLCollection`.   
> `querySelector` methods return a `NodeList`.  
> 
> They do not have a lot of the normal array methods like `push`, `pop`, `map`, `filter` etc.
>
>```js
> const paragraphsHTMLCollection = document.getElementsByTagName("p");
> const error = paragraphsHTMLCollection.pop() // TypeError: paragraphsHTMLCollection.pop is not a function
>```
> 
> Want to make an convert a HTMLCollection or a Nodelist to an Array? Use `Array.from()`  
>
>```js
> const paragraphsHTMLCollection = document.getElementsByTagName("p");
> 
> const paragraphsArray = Array.from(paragraphsHTMLCollection)
> const lastParagraph = paragraphsArray.pop() // works!  
> console.log(lastParagraph) 
>```


## More information

Now that you've experimented a bit with functions that search the DOM, you have some idea of how they work. But there is always way more than meets the eye. Where is the *documentation*, you might ask. The answer is almost always the [MDN Web Docs](https://developer.mozilla.org/).

Just like browser DevTools, you and MDN are going to become intimate friends. Although the relationship is a bit one-sided. Try reading the documentation for the functions you just used to see how much of it you understand. For example [`document.getElementById`](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementById). Most functions contain examples. In short: 

> MDN is super useful!