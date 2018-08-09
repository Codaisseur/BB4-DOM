---
title: Todo App with jQuery
description: |
  In this lesson, you will use a JavaScript framework called jQuery to do some of the heavy lifting for you.
tags:
  - jQuery
  - Basic Javascript
sections:
  - 01-setup
  - 02-update-counters
  - 03-toggle-completed
  - 04-create-todos
  - 05-cleanup-completed
  - 06-http-requests
---

# Todo App with jQuery

We're about to re-write our Todo-app using jQuery. Ever since the second browser started supporting JavaScript in 1996 (Internet Explorer 3!), there have been differences between them. The DOM was not the same, the entire language was not the same. Even when browser vendors started trying to standardize, many differences remained. The reasons jQuery became so popular were:

+ *Querying* elements with CSS selectors
+ Cross browser compatibility

Making cross-browser websites is still hard, but much easier than it was in the early days of the internet. jQuery is still useful when you want to support older browser. Since supporting old browsers can mean making more money by serving more customers, you will still find jQuery in many web projects.

```js
// You can do this in browsers, nowadays
document.querySelectorAll('input[type=text]');
// ...thanks to the fact that jQuery introduced it first
$('input[type=text]');
```

The signature `$` function tells us we're speaking jQuery. 

# jQuery for new projects

When deciding to use jQuery for a new project, you should consider the amount of functionality you actually need from it. The website called [youmightnotneedjquery](http://youmightnotneedjquery.com/) can give you some guidance.