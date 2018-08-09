---
title: Clean up Completed Todos
description: |
  Add a link to the footer to clean up completed todos.
tags:
  - Basic Javascript
---

# Clean up Completed Todos

To clean up the done todos, we can add a link to the footer:

```html
<div class="footer">
  Todo: <span id="todo-count">1</span> •
  Done: <span id="completed-count">0</span> •
  Total: <span id="total-count">1</span> •

  <!-- link to clean up todos that are done -->
  <a href="#" onclick="cleanUpDoneTodos(); return false">Clean up</a>
</div>
```

And then add the following function to clean up the done todos when we click
the link:

```javascript
function cleanUpDoneTodos() {
  var list = document.getElementById("todolist");
  var doneItems = document.getElementsByClassName("completed");

  // Reverse loop through the done todo items so we can remove them without changing the index of the remaining items when we remove them
  for (var i = doneItems.length; i > 0; i--) {
    list.removeChild(doneItems[i-1]);
  }

//   updateCounters();
}

```

Now, when you click the link, it should clean up the completed todos!

### Commit Your Changes

Let's commit these changes:

```bash
$ git add .
$ git commit -m 'Cleanup completed todos link'
```
