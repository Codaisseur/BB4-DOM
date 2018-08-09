---
title: HTTP Requests
---

# Storing and loading data from a server

In its current state, our TODO app is not very useful. The moment we close the browser, we lose all our data. We need to *persist* the data. We're interested in storing it in a central location. That way we can always get to it from any of our devices. For us, that's going to be the server.

A server is a role, **not** a type of machine. For us the client is the browsers, and the server is a web server. Web servers are applications that receive and answer requests in HTTP. The server code, including all our own code for validation and persistence, are called the back-end. The HTTP server code that responds to requests by other applications (rather than humans) is called the API.

# Ajax

Browsers fetch HTML pages, CSS files, images, and everything else, using HTTP. It's the fundamental means of communication of the web. Our JavaScript code can also request data using HTTP. This is called AJAX (Asynchronous JavaScript and XML). Using jQuery, and Ajax request can look as simple as:

```js
$.getJSON('/todos', function(data) { console.log('We just received this: ' + data) });
```

Try running that code in your DevTools on our Todo app page (where jQuery is already loaded). You should see an error like this:

<img src="https://cd.sseu.re/TodoList_-_Google_Chrome_2018-03-11_15.43.16.png"/>

When serving HTML directly from the filesystem, we're not allowed to make Ajax requests to the filesystem. Let's try it again, but let's call a demo API that actually supports HTTP.

```js
$.getJSON('https://jsonplaceholder.typicode.com/posts/1', console.log);
```

> Note how we didn't create an anonymous function. We simply used `console.log` as the callback. You can always pass a reference to a function instead of an anonymous function, you just have to make sure that the function signature is appropriate.

Did you see the response data printed in the console? We can get even more information by going to the **Network** tab of our DevTools. Every HTTP request performed on the current page is recorded in the list. 

<img src="https://cd.sseu.re/TodoList_-_Google_Chrome_2018-03-12_08.53.03.png"/>

Familiarize yourself with the available options. They will be immensely useful when making web-apps with backends.

## Errors

What if the server is having problems, or we made a mistake when calling our API? This is how we can handle errors in our Ajax request.

```js
$.getJSON('https://jsonplaceholder.typicode.com/posts/xxx', console.log)
    .fail(function(jqXHR, status, err) {
        console.warn("Something bad happened. HTTP status " + jqXHR.status);
    });
```

## Doing multiple calls

Doing more than one Ajax call could just be a matter of doing two `$.getJSON` calls in sequence. But what if the second call needs data from the result of the first?

```js
function handleError(jqXHR, status, err) {
    console.warn("Something bad happened. HTTP status " + jqXHR.status);
}
$.getJSON('https://jsonplaceholder.typicode.com/posts/5', function(data) {
    $.getJSON('https://jsonplaceholder.typicode.com/users/' + data.userId, function(data) {
        console.log("user data belonging to post:", data);
    }).fail(handleError);
}).fail(handleError);
```

This is called nesting your callbacks. The deeper the nesting the harder your code becomes to read. Soon we'll be covering ways to make this type of code more readable.