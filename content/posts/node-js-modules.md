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

#### IIFE

History started with native approach called IIFE (immediately invoked function expressions)

![](/content/images/screenshot_4.jpg)

Such implementation allows us to have some global object like APP which can't be affected with other js code. That helps us to avoid rewriting global variables/objects/functions...

What is the cons of such approach ?

* restricted order of including scripts
* extra code for assignment

This could work only in borwsers.

#### Comman js

What is CommonJS used for?

CommonJS is a module formatting system. It is a standard for **structuring and organizing JavaScript code**. CJS assists in the server-side development of apps and it's format has heavily influenced NodeJS's module management.

    We use module.export = {all wee need to export}
    and
    const {one,two} = require('./path.js')

![](/content/images/screenshot_1.jpg)

The thig is that we can not use this in browser but we can use in bundlers like webpack which works with node js and prepare already combined code.

#### ES Modules

ES Modules is the ECMAScript standard for working with modules. While Node.js has been using the CommonJS standard since years, the browser never had a module system, as every major decision such as a module system must be first standardized by ECMAScript and then implemented.

![](/content/images/screenshot_2.jpg)

Difference between Comman JS and ES Modules

![](/content/images/screenshot_3.jpg)

How to use Es moduels in Node JS ?

![](/content/images/screenshot_5.jpg)

### What is circular dependency ?

A circular dependency between Node. js modules **occurs when the modules require() each other**. This dependency results in an incomplete module being loaded, and mysterious problems later.

### Example of using ES modules

We should use either package.json or .mjs prefix

![](/content/images/screenshot_5.jpg)

![](/content/images/screenshot_6.jpg)

or we can use

![](/content/images/screenshot_9.jpg)

![](/content/images/screenshot_10.jpg)

### Asycn Imports

Lets consider that "import" is just a global function which allows us to import something.

![](/content/images/screenshot_11.jpg)

Such approach allows us to import in different places depend on different conditions. And because we use promises when do import, our thread is not blocked. Moreover we can use try catch to process our result of importing.