---
title: Toggle Completed State
description: |
  Now we are going to toggle the completed state of the todos. Add the function below to your `<script>` section.
tags:
  - jQuery
  - Basic Javascript
---

# Toggle Completed State

Now we are going to toggle the completed state of the todos. Add the function below to your `<script>` section.

```js
function toggleDone() {
  var checkbox = this;

  $(checkbox).parent().toggleClass("completed");
}
```

Let's commit our changes:

```bash
$ git add .
$ git commit -m "Toggle done state function"
```

To trigger this function, we are going to take the check boxes and **_listen_ for their `change` events**.

Register a `change` event listener on your check boxes:

```js
// put this at the bottom of your JavaScript section

$(document).ready(function() {
  $("input[type=checkbox]").on('change', toggleDone);
});
```

> The `ready` function in jQuery lets us easily register an event handler for the `DOMContentLoaded` event.

Now it is also a good moment to move that call to `updateCounters()`.  Remove the function call that is beneath the function declaration, and paste it into that ready-event listener on the document:

```js
$(document).ready(function() {
  $("input[type=checkbox]").on('change', toggleDone);
  updateCounters(); // Just add this line
});
```
Let's commit our changes:

```bash
$ git add .
$ git commit -m "Bind done toggle to checkbox onchange event"
```

Now, when you click a check box, it should toggle the completed state of your todo.
