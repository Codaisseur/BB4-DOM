---
title: Update Counters
description: Update the stats on your todo lists
tags:
  - jQuery
  - Basic Javascript
---

# Update total number of todos

View the page in your browser and look in the footer of the todo list. The total number of todos is off by one (1 instead of 2). Let's fix this by adding a little bit of JavaScript.

At the bottom of the HTML file, a `<script>` block _just_ above the closing `</body>` tag is already present.

Add the following JavaScript in there.

```html
<script>
  $("#total-count").html($(".todo").length);
</script>
```

The above script gets the element that contains the counter by its id, then gets all the todo items from the list and puts the length of that Array inside the counter element.

Now, when you reload the HTML file in your browser, it should update the counter to `2`.

Let's commit our changes:

```bash
$ git add .
$ git commit -m "Update total todos counter"
```

Let's make it more accessible in a `function` call now, so we can reuse it, and add the other counters in there too:


```js
function updateCounters() {
  var todoCount = $(".todo").length;
  var completedCount = $(".completed").length;

  $("#total-count").html(todoCount);
  $("#completed-count").html(completedCount);
  $("#todo-count").html(todoCount - completedCount);
}

updateCounters();
```

Let's commit our changes:

```bash
$ git add -p
$ git commit -m "Update all todo counters"
```
