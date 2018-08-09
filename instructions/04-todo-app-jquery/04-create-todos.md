---
title: Create New Todos
description: |
  To create new todos, we need to add a listener on the `form` for the `submit` event
tags:
  - jQuery
  - Basic Javascript
---

# Create new Todos

To create new todos, we need to add a listener on the `form` for the `submit` event:

```js
// put this at the bottom of your JavaScript section
$("form").on('submit', submitTodo);
```

Now, let's create the `submitTodo` function in our JavaScript section:

```js
function submitTodo(event) {
  // stop the form from doing the default action, submitting...
  event.preventDefault();

  var title = $("#new-todo").val();

  createTodo(title);

  $("#new-todo").val(null);
  updateCounters();
}
```

Inside the `submitTodo` function, we call a `createTodo` function that takes a `title` argument:

```js
function createTodo(title) {
  var checkboxId = "todo-" + nextTodoId();

  var listItem = $("<li></li>");
  listItem.addClass("todo");

  var checkbox = $('<input>');
  checkbox.attr('type', 'checkbox');
  checkbox.attr('id', checkboxId);
  checkbox.val(1);
  checkbox.on('change', toggleDone);

  var space = document.createTextNode(" ");

  var label = $('<label></label>');
  label.attr('for', checkboxId);
  label.html(title);

  listItem.append(checkbox);
  listItem.append(space);
  listItem.append(label);

  $("#todolist").append( listItem );

  updateCounters();
}

function nextTodoId() {
  return $(".todo").length + 1;
}
```

And now we can create new todos, yay! :)

Make a couple of todos and check and uncheck them.

Let's commit our changes:

```bash
$ git add .
$ git commit -m 'create todos'
```
