---
title: Toggle Completed State
description: |
  Toggle the completed state of your Todos
tags:
  - Basic Javascript
---

# Toggle Completed State

Now we are going to toggle the completed state of the todos when we click the todos' checkboxes. Add the function below to your `<script>` section.

```js
function toggleDone() {
  var checkbox = this;

  // check the checked status of the checkbox
  if (checkbox.checked) {
    // the "completed" class is set on the parent element, the <li>
    checkbox.parentElement.className = "todo completed";
  } else {
    checkbox.parentElement.className = "todo";
  }

  updateCounters();
}
```

Let's commit our changes:

```bash
$ git add .
$ git commit -m "Toggle done state function"
```

To trigger this function, we are going to take the check boxes and **_listen_ for their `change` events**.

Add an `onchange` HTML attribute to all your check boxes:

```html
<input id="todo-1" type="checkbox" onchange="toggleDone.bind(this)();">
 ```

```html
<input id="todo-2" type="checkbox" checked="checked" onchange="toggleDone.bind(this)();">
```

Now, when you click a check box it should toggle the completed state of your todo.


## Commit Your Changes

Let's commit these changes:

```bash
$ git add .
$ git commit -m "Bind done toggle to checkbox onchange event"
```
