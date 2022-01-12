---
date: 2022-01-08T10:02:18Z
hero_image: "/content/images/035575f2985fe451d86e717d73691e533a1a00545d7230900ed786341dc3c882.png"
title: Node js | modules

---
# Why do we need modules ?

1. Repeat same code
2. Compounding body from different modules
3. Convenient development in team
4. Encapsulation ( Isolation )
5. Organizing and easy navigation in project

History started with native approach called IIFE (immediately invoked function expressions)

![](/content/images/screenshot_4.jpg)

Such implementation allows us to have some global object like APP which can't be affected with other js code. That helps us to avoid rewriting global variables/objects/functions... 

What is the cons of such approach ?

* restricted order of including scripts
* extra code for assignment 