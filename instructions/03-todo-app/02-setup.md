---
title: Project Setup
description: |
  Get started building your Todo App
tags:
  - HTML
  - CSS
---

# Project Setup

Now that you know about the DOM, let's start setting up the project.

You are going to be using the following HTML document source. Add this content to a new file called `index.html` and put it in a new folder, for example `~/Code/JavaScript/todojs`:

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>TodoList</title>
  <style>
    body {
      font-family: Helvetica, Arial, sans-serif;
      font-size: 18px;
    }

    .container {
      margin: 20px auto;
      width: 500px;
      border: 1px solid #e6e6e6;
      border-radius: 3px;
    }

    h1 {
      text-align: center;
    }

    form {
      padding: 0 0 20px;
    }

    input#new-todo {
      display: block;
      width: 478px;
      border-radius: 3px;
      border: 1px solid #e6e6e6;
      padding: 10px;
      font-size: 18px;
    }

    ul#todolist {
      list-style: none;
      margin: 0;
      padding: 0;
    }

    ul#todolist li {
      padding: 5px;
      border: 1px solid #e6e6e6;
      border-radius: 3px;
    }

    ul#todolist li:hover {
      background-color: #e6e6e6;
    }

    ul#todolist .todo.completed label {
      text-decoration: line-through;
      color: #999;
    }

    .footer {
      margin-top: 10px;
      background: #323232;
      color: #e6e6e6;
      padding: 5px;
      border-bottom-left-radius: 3px;
      border-bottom-right-radius: 3px;
    }

    .footer a:link,
    .footer a:hover,
    .footer a:visited {
      color: #e6e6e6;
      text-decoration: none;
    }

    .footer a:hover {
      text-decoration: underline;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>TodoList</h1>

    <form>
      <input type="text" id="new-todo" placeholder="What needs to be done?">
    </form>

    <ul id="todolist">
      <li class="todo">
        <input id="todo-1" type="checkbox">
        <label for="todo-1">Sweep the floor</label>
      </li>
      <li class="todo completed">
        <input id="todo-2" type="checkbox" checked>
        <label for="todo-2">Dust the vases</label>
      </li>
    </ul>
    <div class="footer">
      Todo: <span id="todo-count">1</span> •
      Done: <span id="completed-count">0</span> •
      Total: <span id="total-count">1</span>
    </div>
  </div>

  <script>
  	// JavaScript code comes here...
  </script>

</body>
</html>
```

If you open that file in Chrome, you should see something similar to this:

[![](https://cd.sseu.re/20161018-q96by.png)](https://cd.sseu.re/20161018-q96by.png)






## Commit Your Changes

Go into the project folder and initialize a new git repository:

```bash
$ cd ~/Code/JavaScript/todojs
$ git init
```

Add the `index.html` file to git and commit it's initial state:

```bash
$ git add index.html
$ git commit -m "Static HTML template with CSS"
```

Next create a Github repository and push the code there:

```bash
$ git remote add origin git@github.com...
$ git push -u origin master
```
