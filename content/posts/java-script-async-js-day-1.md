---
date: 2021-11-03T12:20:36.000+00:00
hero_image: "/content/images/16-11-20-three-ways-to-write-asynchronous-javascript-code-blog.jpg"
title: Java-Script | Async Js
author: ''

---
**What is Synchronous code ?**

_Synchronous_ code is executed line by line in defined order.

**What is Asynchronous code ?**

_Asynchronous_ programming is all about coordinating the behavior of our program over a certain period of time.

**What are AJAX calls ?**

**AJAX - A**synchronous **J**avaScript **A**nd **X**ML: Allows us to communicate with remote web servers in an **asynchronous way.** With AJAX calls, we can request data from web servers dynamically.

**What is an API ?**

**A**pplication **P**rogramming **I**nterface: Piece of software that can be used by another piece of software in order to allow a**pplications to talk to each other**;

There are be many types of APIs in web development:

DOM API / GeoAPI / Own Class API / **"Online" API**

**"Online" API:** Application running on a server, that receives requests for data and sends data back as response; **It can be called Web API or simply API**

We don't use XML nowadays but JSON for APIs.

### Our first AJAX CALL

In JavaScript there are different ways to make API calls. Lets start with the old school one.

**XML HTTP request function**

    const request = new XMLHttpRequest();
    
    request.open('GET', 'https://restcountries.com/v3.1/name/armenia');
    request.send();
    
    request.addEventListener('load', function() {
      console.log(JSON.parse(this.responseText))
    })

### Promises and the Fetch API

What are promises ?

**Promise:** An object that is used as a placeholder for the future result of an asynchronous operation. Its like a container for an asynchronously delivered value. Or less formal its like a container for a future value.

When we start ajax call there is no value yet. But we know that there will be some value in the future. And so we can use a promise to handle this future value.

**Live cycle of a promise**

Promise is time sensitive, this means that it can changes during the time. So in the very beginning we say that promise is PENDING (before the future value is available). Then is comes to SETTLED( Async task has hinished). And there are 2 type of SETTLED: fullfilled and rejected.

And the one more important thing is that we can't change promise state. 

Lets look at fetch example:

    fetch('https://api.github.com/repos/javascript-tutorial') // Promise
      .then(response => response.json()) This with first like becoume new Promise which needs THEN
      .then(data => console.log(data)); // Finally

Fetch returns a Promise whish in pending state and then it wait for async answer. With **then**    method we can specify what should happen after answer will be gotten. In first then which is interesting we get Pomise as well, so wee need to use second then to get result of that resolved promise and console that.

**Important**

We should remember that **then method of Promise** always return a promise. And fulfilled value which is accessible in next then will be the value which we have returned from previous then.

Only way when request can be rejected is when user lose his internet connection.

There are two ways. to process this status. First we can pass second callback into then method, like this.

    fetch('https://api.github.com/repos/javascript-tutorial') // Promise
      .then(
      	response => response.json(),
        err=> alert(err)
      ) This with first like becoume new Promise which needs THEN
      .then(data => console.log(data)); // Finally

And we will see that error from console will gone. Because we cough that error. 

But there is a way to handle errors globally. So instead writing for each promise we can write at the end like.

    fetch('https://api.github.com/repos/javascript-tutorial') // Promise
      .then( response => response.json() ) This with first like becoume new Promise which needs THEN
      .then( data => console.log(data) )
      .catch( err => alert(err) ); // Finally

There is another method called finally() which usually used when something needs to happen no matter what is result.

    fetch('https://api.github.com/repos/javascript-tutorial') // Promise
      .then( response => response.json() ) This with first like becoume new Promise which needs THEN
      .then( data => console.log(data) )
      .catch( err => alert(err) )
      .finally( ()=>{
      	//FOR EXAMPLE HIDE SPINNER
      }); // Finally

Why finally works because catch return promise.

> It could be that we can got errors like 404,500 erc. but this won't mean that we have internet connection issue. So it such situations we catch is pointless.

Lets review this situation:

    fetch('https://api.github.com/repos/javascript-tutorial') // Promise
      .then( response => {
      	if(!response.ok)
        	throw new Error(`Error ${response.status}`)
      	return response.json()
      }) This with first like becoume new Promise which needs THEN
      .then( data => console.log(data) )
      .catch( err => alert(err.message) ); // Finally

Any error that happens in any of the callback functions here, so in any then handler, will immediately terminate(end) that then handler and will propagate down to the catch method here.

err.message == throw new Error

Lets pretend that we need to repeat some part of promise callback including error processing. How we can make it more readable ?

    const getJSON = function (url, errorMsg = 'Something went wrong') {
      return fetch(url).then(response => {
        if (!response.ok) throw new Error(`${errorMsg} (${response.status})`);
    
        return response.json();
      });
    };
    getJSON(
      `https://restcountries.eu/rest/v2/name/${country}`,
      'Country not found'
    )
      .then(data => { // Etc...
    