---
date: 2021-11-03T12:20:36.000+00:00
hero_image: "/content/images/16-11-20-three-ways-to-write-asynchronous-javascript-code-blog.jpg"
title: Java-Script / Async Js / Day 1
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