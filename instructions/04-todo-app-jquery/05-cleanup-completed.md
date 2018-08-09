---
title: Clean Up Completed Todos
description: Add a link to clean up completed todos
tags:
  - jQuery
  - Basic Javascript
---

# Clean Up Completed Todos

To clean up the done todos, we can add a link to the footer:

```html
<div class="footer">
  Todo: <span id="todo-count">1</span> •
  Done: <span id="completed-count">0</span> •
  Total: <span id="total-count">1</span> •

  <a href="#" id="clean-up">Clean up</a>
</div>
```

And then add the following function to clean them up:

```js
function cleanUpDoneTodos(event) {
  event.preventDefault();
  $.when($(".completed").remove())
    .then(updateCounters);
}
```

And add a `click` listener:

```js
// put this at the bottom of your JavaScript section
$("#clean-up").on('click', cleanUpDoneTodos);
```

Now, when you click the link, it should clean up the completed todos!

Let's commit our changes:

```bash
$ git add .
$ git commit -m 'cleanup completed todos link'
```
