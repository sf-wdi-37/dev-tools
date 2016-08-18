<!--
Creator: <Name>
Market: SF
-->

![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png)

# Chrome Devtools and Debugging Workshop

### Why is this important?
<!-- framing the "why" in big-picture/real world examples -->
*This workshop is important because:*

To better make progress as a developer, you need to be able to find your errors and fix them. The chrome developer tools are designed specifically to help you look carefully through all aspects of your webpage in order to gather information about how it is working. They are an indispensable resource that you should quickly get familiar with.

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



## Console tab

### Common errors in the console

Read error messages! Sometimes error messages are awesome. Sometimes not so much.  Be aware that in the chrome dev tools console, the right hand side of an error line often shows you the file name and line number that the error came from.


![uncaught syntax error: unexpected token }](https://cloud.githubusercontent.com/assets/6520345/17763727/74320592-64cf-11e6-8c9d-064e0d0808fd.png)

This error means that there is a symbol that is unexpected somewhere in the code. Sometimes that means that you have an extra `}` as is indicated above. Sometimes it means you're missing a closed bracket or a closed parentheses. In that case, it will tell you that the next symbol it can't properly understand, which can look a little cryptic:

![uncaught syntax error: unexpected token . ](https://cloud.githubusercontent.com/assets/6520345/17763801/eadc52b0-64cf-11e6-92b6-4e5092729c69.png)

Simply look at the line indicated and move backwards to see if there are any unclosed brackets or parentheses nearby.

![uncaught reference error: variableName is not defined](https://cloud.githubusercontent.com/assets/6520345/17764043/9b6f56c6-64d1-11e6-84ae-8469100b9955.png)
This means that you haven't declared a variable before attempting to use it. Make sure that you look through the code at where `variableName` is defined and used. Ensure that you declare it at a scope that is accessible to the place where you later attempt to use it.

![uncaught type error: a is not a function](https://cloud.githubusercontent.com/assets/6520345/17764091/fcb90cc4-64d1-11e6-8475-e94155e85400.png)






[This blog post](https://davidwalsh.name/fix-javascript-errors) explores a few of the most common errors that you will see display in the console.

## Elements tab


## Explore the documentation

[The Chrome Dev tools documentation](https://developers.google.com/web/tools/chrome-devtools/) has recently been updated and improved.




# DEBUGGING

_The error source above was script.js, line 18._

## Tips for `console.log()`

Tips for console logging:

* Write descriptive log messages.

	```js
	// WORSE
	console.log("test");
	// BETTER
	console.log("inside add button click event - this is ", this);
	```
* Don't reuse the same log message in multiple places; it will be hard to tell where messages came from once we get out of the chrome dev tools.  
* When adding an object to a string log message, use a comma instead of a plus sign.  When you use a plus sign, the object is converted to a string (poorly, in most cases). With the comma, the object is not converted.

	```js
	var animals = {a:"aardvark", b:"baboon"};

	// WORSE
	console.log("animals is " + animals);
	// logs "animals is [object Object]"

	// BETTER
	console.log("animals is ", animals);
	// logs "animals is  { a: 'aardvark', b: 'baboon' }"
	```


## Using `debugger`

`debugger` is a JavaScript tool for debugging! It lets you pause your code on a specific line, wherever you write the keyword `debugger`. While it's paused, you can examine the scope, the call stack, and other useful information.  Across many languages and tools, interactive pauses like this are called "breakpoints".


### Chrome Dev Tools

Chrome's "Sources" tab provides a nice Graphical User Interface, or GUI (pronounced "gooey") for the debugger tool.


> ![chrome dev tools sources tab](img/sources.png)

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

If you'd like your dev tools in a separate window from your browser, click and hold the dev tools positioning icon to undock them.  

<img src="img/undock.png" width="300px" alt="dev tools positioning">

<!-- ### Node.js

Since Node.js is built on the same JavaScript engine Chrome uses (called "V8"), we can also use `debugger` when running a file from the terminal with Node.js:

```bash
node debug script.js
```

You don't have a GUI in the Terminal, so you'll have to enter debugger text commands. A full list of commands and more information on how to use `debugger` with Node.js is avaiable in the <a href="https://nodejs.org/api/debugger.html">Node.js debugger documentation</a>. -->

## Using Conditional Breakpoints in Chrome Dev Tools

Chrome dev tools also lets you set "conditional breakpoints" that pause whenever some trigger occurs, like "pause whenever a click event fires" or "pause whenever a request is made". You set these through the Sources tab, in the breakpoint dropdowns.  More details (and images!) are available in Google's <a href="https://developers.google.com/web/tools/javascript/breakpoints/add-breakpoints?hl=en#create-conditional-breakpoints">how to add breakpoints</a>.

## More Resources

* Google's <a href="https://developers.google.com/web/tools/javascript/index?hl=en">guide to debugging JavaScript with Chrome Dev Tools</a>


## Drills!


Clone this repository! Solution in solution branch.

The code in scripts/app.js has comments that list some problems with the sample project website. There are currently some bugs, but it should look like this:

<img src="img/result.png" width="60%" alt="count es and link a lot site screenshot">

Update the project code to fix the problems described in the comments. Note: the last one (alerting 0-4) is a stretch.


## Independent Practice
Refine the skills covered in this workshop with this [lab](#)

## Closing Thoughts
- review objectives & hierarchy of importance
- look ahead & link to future workshops
- clarify expectations and what developers should know by now
- reiterate “the why” with a perspective of your intentions
- create an active recall
- Check for understanding

## Additional Resources
- [Chrome Dev tools documentation](https://developers.google.com/web/tools/chrome-devtools/)
