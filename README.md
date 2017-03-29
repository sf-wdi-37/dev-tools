<!--
Creator: <Name>
Market: SF
-->

![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png)

# Chrome Devtools and Debugging Workshop

### Why is this important?
<!-- framing the "why" in big-picture/real world examples -->
*This workshop is important because:*

finding your errors and fixing them will make you a better developer. The chrome developer tools are designed specifically to help you look carefully through all aspects of your webpage in order to gather information about how it is working. They are an indispensable resource that you should quickly get familiar with.

### What are the objectives?
<!-- specific/measurable goal for students to achieve -->
*After this workshop, developers will be able to:*

- use the console tab to gather diagnostic information about their code (read various error messages and logs of their own creation).
- use the console tab to interact with the JavaScript on the page.
- use the elements tab to view an manipulate the DOM and styling.
- view their sites in mobile mode with the device mode

### Where should we be now?
<!-- call out the skills that are prerequisites -->
*Before this workshop, developers should already be able to:*

- open the developer tools using right click and "inspect element" or using the keyboard shortcut `option`+`cmd`+`i`.
- use `console.log()` to output useful information from their JavaScript files.


## Explore the documentation

[The Chrome Dev tools documentation](https://developers.google.com/web/tools/chrome-devtools/) has recently been updated and improved.


## Console tab

The console is where you see the output from your program. If things are running smoothly, you'll see a bunch of `console.log` messages of your own creation that give you information about the status of the code. You can use these to print values that will give you an idea of whether the values are as expected!

When things aren't going well, you'll have a number of red errors to read, interpret and correct. We'll cover both below.

### Tips for `console.log()`

Tips for console logging:

* Write descriptive log messages.

	```js
	// WORSE
	console.log("test");
	// BETTER
	console.log("inside add button click event - this is ", this);
	```
* Don't reuse the same log message in multiple places; it will be hard to tell where messages came from once we get out of the chrome dev tools.  
* When adding an object to a string log message, use `console.log`'s ability to take multiple comma-separated arguments.  When you give console a string and object/array concatenated (with a `+`), the object/array is converted to a string (poorly, in most cases). When given as a separate value, indicated by adding a comma, the system will print out objects and arrays much more completely.

	```js
	var animals = {a:"aardvark", b:"baboon"};

	// WORSE
	console.log("animals is " + animals);
	// logs "animals is [object Object]"

	// BETTER
	console.log("animals is ", animals);
	// logs "animals is  { a: 'aardvark', b: 'baboon' }"
	```

### Common errors in the console

Read error messages! Sometimes error messages are awesome. Sometimes not so much.  Be aware that in the chrome dev tools console, the right hand side of an error line often shows you the file name and line number that the error came from.

![left side of assignment](https://cloud.githubusercontent.com/assets/6520345/17777475/8b5f2542-6515-11e6-8e75-667f52c99fd9.png)
_The error source above was the `demoFunctions` file, line 10._

This is extremely useful for finding errors and eliminating them!

**[This blog post](https://davidwalsh.name/fix-javascript-errors)** explores a few of the most common errors that you will see display in the console. Here are just a few:

#### Unexpected Token
![uncaught syntax error: unexpected token }](https://cloud.githubusercontent.com/assets/6520345/17763727/74320592-64cf-11e6-8c9d-064e0d0808fd.png)

This error means that there is a symbol that is unexpected somewhere in the code. Sometimes that means that you have an extra `}` as is indicated above. Sometimes it means you're missing a closed bracket or a closed parentheses. In that case, it will tell you that the next symbol it can't properly understand, which can look a little cryptic:

![uncaught syntax error: unexpected token . ](https://cloud.githubusercontent.com/assets/6520345/17763801/eadc52b0-64cf-11e6-92b6-4e5092729c69.png)

Simply look at the line indicated and move backwards to see if there are any unclosed brackets or parentheses nearby.

#### The `variable` is not defined

![uncaught reference error: variableName is not defined](https://cloud.githubusercontent.com/assets/6520345/17764043/9b6f56c6-64d1-11e6-84ae-8469100b9955.png)

This means that you haven't declared a variable before attempting to use it. Make sure that you look through the code at where `variableName` is defined and used. Ensure that you declare it at a scope that is accessible to the place where you later attempt to use it.

#### That's not a function!

![uncaught type error: a is not a function](https://cloud.githubusercontent.com/assets/6520345/17764091/fcb90cc4-64d1-11e6-8475-e94155e85400.png)

This means that you have attempted to run a function on variable `a` which is a number, string, array, or any other data type (but not a function).

#### Improper assignment

![left side of assignment](https://cloud.githubusercontent.com/assets/6520345/17777475/8b5f2542-6515-11e6-8e75-667f52c99fd9.png)

This usually means you've used `=` instead of `===` for comparison! In the example below, it should say `if(combineWords() === word)`

![code generating error above](https://cloud.githubusercontent.com/assets/6520345/17777599/f2e2f680-6515-11e6-9e77-4c70a8012bf9.png)





## Elements tab

### DOM view

![image](https://cloud.githubusercontent.com/assets/6520345/17778696/c8b97bfa-6519-11e6-8565-f561d78282e8.png)



### Styling

![image](https://cloud.githubusercontent.com/assets/6520345/17778767/06500eca-651a-11e6-8515-a90c6eb65825.png)


## Sources tab and `debugger`

`debugger` is a JavaScript tool for debugging! It lets you pause your code on a specific line, wherever you write the keyword `debugger`. While it's paused, you can examine the scope, the call stack, and other useful information.  Across many languages and tools, interactive pauses like this are called "breakpoints".


### Debugger in sources tab

Chrome's "Sources" tab provides a nice Graphical User Interface, or GUI (pronounced "gooey") for the debugger tool.

![image](https://cloud.githubusercontent.com/assets/6520345/17778249/441d6178-6518-11e6-9542-aa84ea13feeb.png)



Here's an example you can use to explore recursion with `debugger`:

```js
	function count(n){
	    console.log('counting down...');
	    console.log(n);
	    debugger;
	    if (n > 0) {
	        count(n-1);
	    } else {
	        console.log('at the bottom!');
	    }
	    console.log('counting up...');
	    console.log(n);
	    debugger;
	}

count(3);
```


## Independent Practice
Refine the skills covered in this workshop with this [training](https://github.com/sf-wdi-37/dev-tools-training)


## Additional Resources
- [Chrome Dev tools documentation](https://developers.google.com/web/tools/chrome-devtools/)
- Google's <a href="https://developers.google.com/web/tools/javascript/index?hl=en">guide to debugging JavaScript with Chrome Dev Tools</a>
