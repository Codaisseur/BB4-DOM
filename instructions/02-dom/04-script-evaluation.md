---
title: Script Evaluation Order
---

# Script Evaluation Order

So far today we've been typing JS straight into the console. Now we're going to create an HTML file that contains some JS. Take the following HTML and put it in a new file. 

```html
<html>
    <head>
        <title>Lots of scripts!</title>
        <script>
            console.log('head', document.getElementById('header-id'));
            document.addEventListener('DOMContentLoaded', function() {
                console.log('DOMContentLoaded', document.getElementById('header-id'))
            });
        </script>
    </head>
    <body>
        <script>
            console.log('body top', document.getElementById('header-id'))
        </script>
        <h1 id="header-id">HEADER</h1>
        <script>
            console.log('body bottom', document.getElementById('header-id'))
        </script>
    </body>
</html>
```

Read the scripts carefully. Try to figure out what they're trying to do, and then try to predict in which order the `console.log` statements will be called and what they will print.

When you're ready, open the HTML file in the browser. Check the DevTools console to see if you were right.

> To open a local file in the browser type the following command:
>
> - on Ubuntu: `xdg-open <file>`
> - on Mac OS: `open <file>`
> - on Windows: `start <file>`

What this example should illustrate several things:

1. Scripts are evaluated in order of appearance in the HTML. 
1. Scripts cannot access parts of the DOM that are appear *after* them in the HTML.
1. Scripts can register an event listener to be called after the HTML has been fully parsed into the DOM. This event type is called `DOMContentLoaded`.