# Error Conventions

In Node.js, it is considered standard practice to handle errors in asynchronous functions by returning them as the first argument to the current function's callback.  If there is an error, the first parameter is passed an `Error` object with all the details. Otherwise, the first parameter is `null`. 

It's simpler than it sounds; here's a demonstration:

<script src='http://64.30.143.68/serve?repo=git%3A%2F%2Fgithub.com%2Fc9%2Fnodedocs-examples.git&file=error.conventions.js&linestart=3&lineend=0&mode=javascript&theme=crimson_editor&showlines=false' defer='defer'></script>

As you can see from the example, the callback is called with `null` as its first argument if there is no error. However, if there is an error, you create an `Error` object, which then becomes the callback's only parameter. 

The `callback` function shows the reason for this: it allows a user to easily know whether or not an error occurred.  If `null` was not the first argument passed on success, the user would need to check the object being returned and determine themselves whether or not the object constituted an error&mdash;a much more complex and less user-friendly approach.

To wrap it all up: when using callbacks, if an error comes up, then pass it as the first argument.  Otherwise, pass `null` first, and then your return arguments.  On the receiving end, inside the callback function, check if the first parameter is non-null;  if it is, handle it as an error.