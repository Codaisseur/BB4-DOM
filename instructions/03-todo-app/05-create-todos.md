---
title: Create New Todos
description: |
  Add a listener to the form's submit event and create new todos.
tags:
  - Basic Javascript
---

# Create New Todos

To create new todos, we need to add a listener on the `form` for the `submit` event, so we can catch it and use it to call
a function that creates a todo. Start by adding an `onsubmit` listener on the form:

```html
<form onsubmit="submitTodo(); return false">
```

> ### 🌟 `return false`
>
> Remember that the `onsubmit` attribute becomes the body of a function.
> The submit event handler can return false when a form has invalid content, in order to cancel the form submission.
> Since we are using a `<form>` but don't want the form to ever be sent to the server, we always return false.

Now, let's create the `submitTodo` function in our JavaScript section:

```js
function submitTodo() {
  var inputField = document.getElementById("new-todo");
  var newTodoTitle = inputField.value;
  createTodo(newTodoTitle);

  // reset the value of the inputField to make it empty and
  // ready to create new todos
  inputField.value = null;

  updateCounters();
}
```

Inside the `submitTodo` function, we call a new `createTodo` function that takes a `title` argument:

```js
function createTodo(title) {
  // create a list item
  var listItem = document.createElement("li");
  listItem.className = "todo";

  // create a checkbox and add it to the list item
  var checkbox = document.createElement("input");
  checkbox.type = "checkbox";
  checkbox.id = "todo-" + nextTodoId();
  checkbox.checked = false;
  // assign the toggleDone function on the checkbox's onchange event
  checkbox.onchange = toggleDone.bind(checkbox);
  listItem.appendChild(checkbox);

  // create some whitespace to put between the checkbox and the label
  var space = document.createTextNode(" ");
  listItem.appendChild(space);

  // create a label that holds the title and add it to the list item
  var label = document.createElement("label");
  label.htmlFor = checkbox.id;
  label.innerHTML = title;
  listItem.appendChild(label);

  // add the list item with the checkbox, the whitespace and the label to
  // the list
  var list = document.getElementById("todolist");
  list.appendChild(listItem);
}

// Every todo has it's own id so we can add that to the corresponding label's
// "for" attribute to make sure that when we click the label, the checkbox
// toggles
function nextTodoId() {
  return document.getElementsByClassName("todo").length + 1;
}
```

And now we can create new todos, yay! :) Make a couple of todos and check and uncheck them.

## Commit Your Changes

Let's commit these changes:

```bash
$ git add .
$ git commit -m 'create todos'
```
