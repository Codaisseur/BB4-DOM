---
title: Update Counters
description: |
  Update the Todo counters by finding them in the DOM and replacing their contents
tags:
  - Basic Javascript
  - HTML
---

# Update Counters

> We will update the Todo counters by finding them in the DOM and replacing their contents.

## Updating total number of todos

View the page in your browser and notice how in the footer of the todo list, the total number of todos is off by one (1 instead of 2). Let's fix this next by adding a little bit of JavaScript.

At the bottom of the HTML file, there is a `<script>` block just above the closing `</body>` tag. Add the following JavaScript in there:

```html
<script>
  // select the element containing the count
  var totalCount = document.getElementById('total-count');

  // count the number of todo's by their class name
  var totalTodos = document.getElementsByClassName("todo").length;

  // update the HTML inside the counter element
  totalCount.innerHTML = totalTodos;
</script>
```

The above script gets the element that contains the counter by its id, then gets all the todo items from the list and puts the length of that node list inside the counter element.

Now, when you reload the HTML file in your browser, it should update the counter to `2`:

[![](https://cd.sseu.re/20161018-jkh4u.png)](https://cd.sseu.re/20161018-jkh4u.png)

## Commit Your Changes

Let's commit these changes:

```bash
$ git add .
$ git commit -m "Update total todos counter"
```

## Refactoring `updateCounters()`

Let's make it more accessible in a `function` call now, so you can reuse it, and add the other counters in there too:

```js
function updateCounters() {
  // Total number of todos
  var totalCount = document.getElementById('total-count');
  var totalTodos = document.getElementsByClassName("todo").length;
  totalCount.innerHTML = totalTodos;
}

updateCounters();
```

## Adding all the counters

Now, add the code for the other counters as well (Todo, Done and Total):

```js
function updateCounters() {
  // Total number of todos
  var totalCount = document.getElementById('total-count');
  var totalTodos = document.getElementsByClassName("todo").length;
  totalCount.innerHTML = totalTodos;

  // Total number of completed todos
  var completedCount = document.getElementById('completed-count');
  var completedTodos = document.getElementsByClassName("completed").length;
  completedCount.innerHTML = completedTodos;

  // Total number of uncompleted todos
  var todoCount = document.getElementById('todo-count');
  var uncompletedTodos = totalTodos - completedTodos;
  todoCount.innerHTML = uncompletedTodos;
}
```

## Commit Your Changes

Let's commit these changes:

```bash
$ git add .
$ git commit -m "Update all todo counters"
```
