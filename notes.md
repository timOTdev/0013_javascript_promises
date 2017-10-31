# Creating Promises 
- With Udacity
- Instructor: Cameron Pittman
- Started 11/31/2017

# Lesson 1: Creating Promises
## 1.Course Introduction
- Many ways to handle async requests
- Promises are the preferred way to get data
- Easy error handling, flexibility, and intuitive syntax
- We will learn about exoplanets also

## 2.Callbacks vs Promises
- Asynchronous works with an unknown amount of time
- Returns comes back at random times
- Network, events, threads are asynchronous
- Promises are the best of handle async code

## 3.Callbacks vs Thens
- Callbacks are the default technique for async work
- Handling errors is a big issue
- It's our job to have an error handling strategy
- We don't want a million callbacks to handle multiple errors
- Pyramids of Dooms are more difficult to debug
- These are basically nested callbacks within callbacks
- Promises have easier syntax to follow:
```js
var sequence = get('example.json')
.then(doSomething)
.then(doSomethingElse);
```

## 4.Course Map
- 4 stages in the course
1. Wrapping - learning syntax of constructing a promise
2. Thening - handling responses
3. Catching - handling errors
4. Chaining - putting promises together
- [Jake Archibald's site on promise](https://developers.google.com/web/fundamentals/primers/promises)
- 4 States a promise can have
- Definitions:
    - Fulfilled (Resolved): It worked
    - Rejected: It didn't work
    - Pending: Still waiting
    - Settled: Something happened

## 5.Promise Timeline
- Imagine and event fires before the event listener is set
- The listener never gets called
- With promises, setting an action for resolution value will still work when a promise resolves
- A promise can only settle once, the second resolve will not work in the constructor
- Promise in a main thread is potentially blocking of other work to do
- A promise constructor:
```js
new Promise(function(resolve, reject) {
    resolve('hi'); // works
    resolve('bye'); // can't happen a second time
})
```

## 6.Quiz:Async Scenarios
- You should work with promises when working with data from an AJAX request
- Or when working with messages between you and a web worker

## 7.Syntax
- This is the wrapping statge
- You can set a promise on a variable or just have it run immediately
- If a promise is passed, the promise gets executed first
```js
var promise = new Promise(function(resolve[, reject]) {
    var value = doSomething();
    if (thingWorked) {
        resolve(value);
    }
    else if (somethingWentWrong) {
        reject();
    }
}).then(funtion(value) {
    // success!
    return nextThing(value);
}).catch(rejectFunction);
```
- A real example:
```js
new Promise(function(resolve, reject) {
    var img = document.createElement('img');
    img.src = 'image.jpg';
    img.onload = resolve;
    img.onerror = reject;
    document.body.appendChild(img);
})
.then(finishLoading)
.catch(showAlternateImage);
```
- Resolve chains with .then(), reject() chains with .catch()
- .catch() also chains if there's an error in the call

## 8.Quiz:Write Your First Promise
- Work in the core folder
- `this` keyword refers to the global object (window)
```js
<body>
	<h1>Did the promise finish?</h1>
	<div class="completion">Not yet</div>
	<script>
		function wait(ms) {
			/*
			Your code goes here!

			Instructions:
			(1) Wrap this setTimeout in a Promise. resolve() in setTimeout's callback.
			(2) console.log(this) inside the Promise and observe the results.
			(3) Make sure wait returns the Promise too!
			 */
			return new Promise (function(resolve) {
				console.log(this);
				window.setTimeout(function() {
					resolve();
				}, ms);
			});
		};

		/*
		Uncomment these lines when you want to test!
		You'll know you've done it right when the message on the page changes.
		 */
		var milliseconds = 2000;
		wait(milliseconds).then(finish);


		// This is just here to help you test.
		function finish() {
			var completion = document.querySelector('.completion');
			completion.innerHTML = "Complete after " + milliseconds + "ms.";
		};
	</script>
</body>
```
## 9.Quiz:Wrapping readyState
- We are learning about state changes
- We are emulating jQuery's .ready() except it is document.readyState
- There are 3 states with document.readyState
1. Loading
2. Interative - loading subresponses
3. Complete - loaded everything
- We don't need to worry about error handling
```js
<body>
	<h1>Are you doing work when the document is ready?</h1>
	<h3>Your wrapper should resolve before the huge image finishes loading. Turn on <a href="https://developers.google.com/web/tools/chrome-devtools/profile/network-performance/network-conditions">network throttling</a> to test.</h3>
	<div class="completion">Wrapper hasn't resolved yet!</div>
	<img class="responsive" src="San_Francisco_Market_Street_between_4th_and_5th_St.jpg" height="2448" width="3264" alt="SF Market Street">
	<p><a href="https://commons.wikimedia.org/wiki/File:San_Francisco_Market_Street_between_4th_and_5th_St.jpg">Photo: Andreas Praefcke (Own work) [GFDL (http://www.gnu.org/copyleft/fdl.html) or CC BY 3.0 (http://creativecommons.org/licenses/by/3.0)], via Wikimedia Commons</a></p>
	<script>
		function ready() {
			/*
			
			Instructions:
			(1) Set network throttling.
			(2) Wrap an event listener for readystatechange in a Promise.
			(3) If document.readyState is not 'loading', resolve().
			(4) Test by chaining wrapperResolved(). If all goes well, you should see "Resolved" on the page!

			Make sure you return the Promise!
			 */

			 return new Promise(function(resolve) {
				 function isReady() {
					 if (document.readyState !== 'loading') {
						 resolve();
					 }
				 }
				document.addEventListener('readystatechange', isReady);
				isReady();
			 });
				
		};

		/*
		Don't forget to test your code!
		Call wrapperResolved when the DOM is ready.
		 */
		ready()
		.then(wrapperResolved);

		// Just here for your testing
		function wrapperResolved() {
			var completion = document.querySelector('.completion');
			completion.innerHTML = "Resolved!";
		};
	</script>
</body>
```
## 10.IMPORTANT! Working with Exoplanet Explorer
## 11.Quiz:Wrap an XHR
## 12.Web Technologies
## 13.Quiz:Fetch API
## 14.What Happens Next?

# Lesson 2: Chaining Promises
## 1.Quiz:Fetch and Show First Planet
## 2.Error Handling Strategies
## 3.Quiz:Chained Thenables
## 4.Quiz:Series vs Parallel Requests
## 5.Array Methods and Promises
## 6.Quiz:Promises with .forEach
## 7.Quiz:Promises with .map
## 8.Quiz:All Promises
## 9.Course Outro
## 10.Exoplanets 101
## 11.Quiz:Bonuse Question:Parallel Requests