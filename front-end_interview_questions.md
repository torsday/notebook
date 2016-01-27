# Front-End Interview Questions

An answered and custom version of [h5bp's "Front-end-Developer-Interview-Questions"](https://github.com/h5bp/Front-end-Developer-Interview-Questions) repo...

This file contains a number of front-end interview questions that can be used when vetting potential candidates. It is by no means recommended to use every single question here on the same candidate (that would take hours). Choosing a few items from this list should help you vet the intended skills you require.

**Note:** Keep in mind that many of these questions are open-ended and could lead to interesting discussions that tell you more about the person's capabilities than a straight answer would.

Table of Contents
-----------------

1.  [General Questions](#general-questions)
2.  [HTML Questions](#html-questions)
3.  [CSS Questions](#css-questions)
4.  [JS Questions](#js-questions)
5.  [Network Questions](#network-questions)
6.  [Coding Questions](#coding-questions)
7.  [Fun Questions](#fun-questions)

#### GENERAL QUESTIONS:

-  **What did you learn yesterday/this week?**
-  **What excites or interests you about coding?**
-  **What is a recent technical challenge you experienced and how did you solve it?**
-  **What UI, Security, Performance, SEO, Maintainability or Technology considerations do you make while building a web application or site?**
-  **Talk about your preferred development environment.**
-  **Which version control systems are you familiar with?**
-  **Can you describe your workflow when you create a web page?**
-  **If you have 5 different stylesheets, how would you best integrate them into the site?**
-  **Can you describe [the difference between progressive enhancement and graceful degradation](https://stackoverflow.com/questions/2550431/what-is-the-difference-between-progressive-enhancement-and-graceful-degradation)?**
    > **Graceful Degradation** starts at a ideal user experience level and decreases depending on user agent capabilities down to a minimum level, catering for agents that don't support certain features used by the baseline.

    > **Progressive Enhancement** starts at a broad minimum user experience and increases depending on user agent capabilities up to a more capable level, catering for agents that support more advanced features than the baseline.
-  **How would you optimize a website's assets/resources?**
-  **How many resources will a browser download from a given domain at a time?**
  -  **What are the exceptions?**
-  **Name 3 ways to decrease page load (perceived or actual load time).**
-  **If you jumped on a project and they used tabs and you used spaces, what would you do?**
-  **Describe how you would create a simple slideshow page.**
-  **If you could master one technology this year, what would it be?**
-  **Explain the importance of standards and standards bodies.**
-  **What is Flash of Unstyled Content? How do you avoid FOUC?**
-  **Explain what ARIA and screenreaders are, and how to make a website accessible.**
-  **Explain some of the pros and cons for CSS animations versus JavaScript animations.**

#### HTML QUESTIONS:

-  **What does a `doctype` do?**
-  **What's the difference between standards mode and quirks mode?**
-  **What's the difference between HTML and XHTML?**
-  **Are there any problems with serving pages as `application/xhtml+xml`?**
-  **How do you serve a page with content in multiple languages?**
-  **What kind of things must you be wary of when design or developing for multilingual sites?**
-  **What are `data-` attributes good for?**
-  **Consider HTML5 as an open web platform. What are the building blocks of HTML5?**
-  **Describe the difference between a `cookie`, `sessionStorage` and `localStorage`.**
-  **Describe the difference between `<script>`, `<script async>` and `<script defer>`.**
-  **Why is it generally a good idea to position CSS `<link>`s between `<head></head>` and JS `<script>`s just before `</body>`? Do you know any exceptions?**
-  **What is progressive rendering?**
-  **Have you used different HTML templating languages before?**

#### CSS QUESTIONS:

-  **What is the difference between classes and ID's in CSS?**
-  **[What's the difference between "resetting" and "normalizing" CSS?](https://stackoverflow.com/questions/6887336/what-is-the-difference-between-normalize-css-and-reset-css) Which would you choose, and why?**
  - difference
    - CSS resets aim to remove all built-in browser styling. Standard elements like H1-6, p, strong, em, et cetera end up looking exactly alike, having no decoration at all. You're then supposed to add all decoration yourself.
    - Normalize CSS aims to make built-in browser styling consistent across browsers. Elements like H1-6 will appear bold, larger et cetera in a consistent way across browsers. You're then supposed to add only the difference in decoration your design needs.
  - pros / cons
    - One disadvantage of normalize.css over other reset sheets is that you’ll end up typing more code in elements
    Normalize.css preserves useful defaults rather than "unstyling" everything. For example, elements like sup or sub "just work" after including normalize.css (and are actually made more robust) whereas they are visually indistinguishable from normal text after including reset.css. So, normalize.css does not impose a visual starting point (homogeny) upon you. This may not be to everyone's taste. The best thing to do is experiment with both and see which gels with your preferences.
    - Normalize.css corrects some common bugs that are out of scope for reset.css. It has a wider scope than reset.css, and also provides bug fixes for common problems like: display settings for HTML5 elements, the lack of font inheritance by form elements, correcting font-size rendering for pre, SVG overflow in IE9, and the button styling bug in iOS.
    - Normalize.css doesn't clutter your dev tools. A common irritation when using reset.css is the large inheritance chain that is displayed in browser CSS debugging tools. This is not such an issue with normalize.css because of the targeted stylings.
    - Normalize.css is more modular. The project is broken down into relatively independent sections, making it easy for you to potentially remove sections (like the form normalizations) if you know they will never be needed by your website.
    - Normalize.css has better documentation. The normalize.css code is documented inline as well as more comprehensively in the GitHub Wiki. This means you can find out what each line of code is doing, why it was included, what the differences are between browsers, and more easily run your own tests. The project aims to help educate people on how browsers render elements by default, and make it easier for them to be involved in submitting improvements.
-  **Describe Floats and how they work.**
-  **Describe z-index and how stacking context is formed.**
-  **What are the various clearing techniques and which is appropriate for what context?**
-  **Explain CSS sprites, and how you would implement them on a page or site.**
-  **What are your favourite image replacement techniques and which do you use when?**
-  **How would you approach fixing browser-specific styling issues?**
-  **How do you serve your pages for feature-constrained browsers?**
  -  **What techniques/processes do you use?**
-  **What are the different ways to visually hide content (and make it available only for screen readers)?**
-  **Have you ever used a grid system, and if so, what do you prefer?**
-  **Have you used or implemented media queries or mobile specific layouts/CSS?**
-  **Any familiarity with styling SVG?**
-  **How do you optimize your webpages for print?**
-  **What are some of the "gotchas" for writing efficient CSS?**
-  **What are the advantages/disadvantages of using CSS preprocessors?**
  -  **Describe what you like and dislike about the CSS preprocessors you have used.**
-  **How would you implement a web design comp that uses non-standard fonts?**
-  **Explain how a browser determines what elements match a CSS selector.**
-  **Explain your understanding of the box model and how you would tell the browser in CSS to render your layout in different box models.**
-  **What does `* { box-sizing: border-box; }` do? What are its advantages?**
-  **List as many values for the display property that you can remember.**
-  **What's the difference between inline and inline-block?**
-  **What's the difference between a relative, fixed, absolute and statically positioned element?**
-  **The 'C' in CSS stands for Cascading. How is priority determined in assigning styles (a few examples)? How can you use this system to your advantage?**
-  **What existing CSS frameworks have you used locally, or in production? How would you change/improve them?**
-  **Have you played around with the new CSS Flexbox or Grid specs?**
-  **How is responsive design different from adaptive design?**
-  **Have you ever worked with retina graphics? If so, when and what techniques did you use?**
-  **Is there any reason you'd want to use `translate()` instead of *absolute positioning*, or vice-versa? And why?**

#### JS QUESTIONS:

-  **Explain event delegation**
-  **Explain how `this` works in JavaScript**
    - doesn't matter where the fx is declared, only where it's called

        ```js
        function foo() {
            console.log(this.bar);
        }

        var bar = "bar1";
        var t2  = { bar: "bar2", foo: foo };
        var t3  = { bar: "bar3", foo: foo };

        foo();    // "bar1"
        t2.foo(); // "bar2"
        t3.foo(); // "bar3"
        ```

-  **Explain how prototypal inheritance works**
-  **[What do you think of AMD vs CommonJS?](https://stackoverflow.com/questions/16521471/relation-between-commonjs-amd-and-requirejs)**
-  **[Explain why the following doesn't work as an IIFE: `function foo(){}();`](http://benalman.com/news/2010/11/immediately-invoked-function-expression/).**
  -  While parens placed after an expression indicate that the expression is a function to be invoked, parens placed after a statement are totally separate from the preceding statement, and are simply a grouping operator (used as a means to control precedence of evaluation).
  -  The most widely accepted way to tell the parser to expect a function expression is just to wrap it in parens, because in JavaScript, parens can’t contain statements. At this point, when the parser encounters the function keyword, it knows to parse it as a function expression and not a function declaration
  -  **What needs to be changed to properly make it an IIFE?**
    -  `(function foo(){})();.`
-  **What's the difference between a variable that is: `null`, `undefined` or** `undeclared`?
  -  **How would you go about checking for any of these states?**
-  **[What is a closure, and how/why would you use one?](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures)**
  -  **Closures:** functions that refer to independent (free) variables. In other words, the function defined in the closure 'remembers' the environment in which it was created

  ```js
  function makeFunc() {
      var name = "Mozilla";
      function displayName() {
          alert(name);
      }
      return displayName;
  }

  var myFunc = makeFunc();
  myFunc();
  ```

myFunc has become a closure

A closure is a special kind of object that combines two things: a function, and the environment in which that function was created. The environment consists of any local variables that were in-scope at the time that the closure was created. In this case, myFunc is a closure that incorporates both the displayName function and the "Mozilla" string that existed when the closure was created.

-  **What's a typical use case for anonymous functions?**
-  **How do you organize your code? (module pattern, classical inheritance?)**
-  **What's the difference between host objects and native objects?**
-  **Difference between: `function Person(){}`, `var person = Person()`, and `var person = new Person()`?**
-  **What's the difference between `.call` and `.apply`?**
-  **Explain `Function.prototype.bind`.**
-  **When would you use `document.write()`?**
  -  never, unless you're a 3rd party tool, even then, I don't quite understandy why
-  **What's the difference between feature detection, feature inference, and using the UA string?**
-  **Explain AJAX in as much detail as possible.**
-  **Explain how JSONP works (and how it's not really AJAX).**
-  **Have you ever used JavaScript templating?**
  -  **If so, what libraries have you used?**
    -  mustache
-  **[Explain "hoisting"](http://code.tutsplus.com/tutorials/javascript-hoisting-explained--net-15092)**

  -  variable declarations are "hoisted" to the top of the function declaration

  ```js
  var myvar = 'my value';
  (function() {
    alert(myvar); // undefined
    var myvar = 'local value';
  })();
  ```

  is really

  ```js
  var myvar = 'my value';
  (function() {
    var myvar;
    alert(myvar); // undefined
    myvar = 'local value';
  })();
  ```

-  function *declarations* are hoisted to the top too, but not function *expressions*

  -  declaration: `function myFunction() {}`
  -  expression: `var myFunction = function () {}`
    -  the name `myFunction` gets hoisted like other variables, but it's anonymous function (i.e. value) is only added later

-  **Describe event bubbling.**

-  **What's the difference between an "attribute" and a "property"?**

  -  Attributes are defined by HTML. Properties are defined by DOM.
  -  An attribute is only ever a string, no other type
  -  If an element has a default value, the attribute shows the default value even if the value has changed.

  ```html
  <input type="text" name="username" value="user123">
  ```

  ```js
  $('input').prop('value', '456user'); $('input').prop('value'); // "456user"
  $('input').attr('value'); // "user123"
  ```

-  **Why is extending built-in JavaScript objects not a good idea?**

-  **[Difference between document load event and document ready event?](http://stackoverflow.com/questions/3698200/window-onload-vs-document-ready)**

  -  The ready event occurs after the HTML document has been loaded, while the onload event occurs later, when all content (e.g. images) also has been loaded.
  -  The onload event is a standard event in the DOM, while the ready event is specific to jQuery. The purpose of the ready event is that it should occur as early as possible after the document has loaded, so that code that adds functionality to the elements in the page doesn't have to wait for all content to load.

-  **[What is the difference between `==` and `===`?](https://stackoverflow.com/questions/523643/difference-between-and-in-javascript)**

  -  `===` and `!==` are strict comparison operators:
    -  JavaScript has both strict and type-converting equality comparison. For strict equality the objects being compared must have the same type and:
      -  Two strings are strictly equal when they have the same sequence of characters, same length, and same characters in corresponding positions.
      -  Two numbers are strictly equal when they are numerically equal (have the same number value). NaN is not equal to anything, including NaN. Positive and negative zeros are equal to one another.
      -  Two Boolean operands are strictly equal if both are true or both are false.
      -  Two objects are strictly equal if they refer to the same Object.
      -  Null and Undefined types are == (but not ===). [I.e. Null==Undefined (but not Null===Undefined)]

-  **Explain the same-origin policy with regards to JavaScript.**

  -  **[Same-origin policy](http://javascript.info/tutorial/same-origin-security-policy):** restricts how a document or script loaded from one origin can interact with a resource from another origin.
    -  used as a means to prevent some of the Cross-site Request Forgery attacks.
-  **Make this work:**

  ```js
  duplicate([1,2,3,4,5]); // [1,2,3,4,5,1,2,3,4,5]
  ```
  Solution

  ```js
  function duplicate(args) {
      return args.concat(args)
  }
  ```

-  **Why is it called a Ternary expression, what does the word "Ternary" indicate?**

  -  The conditional (ternary) operator is the only JavaScript operator that takes three operands.
  -  This operator is frequently used as a shortcut for the if statement.

-  **What is `"use strict";`? what are the advantages and disadvantages to using it?**

  -  ECMAScript 5's strict mode is a way to opt in to a restricted variant of JavaScript. Strict mode isn't just a subset: it intentionally has different semantics from normal code. Browsers not supporting strict mode will run strict mode code with different behavior from browsers that do, so don't rely on strict mode without feature-testing for support for the relevant aspects of strict mode.
  -  Strict mode makes several changes to normal JavaScript semantics.
  -  strict mode eliminates some JavaScript silent errors by changing them to throw errors.
  -  strict mode fixes mistakes that make it difficult for JavaScript engines to perform optimizations: strict mode code can sometimes be made to run faster than identical code that's not strict mode strict mode prohibits some syntax likely to be defined in future versions of ECMAScript.

-  **Create a for loop that iterates up to `100` while outputting *fizz* at multiples of `3`, `"buzz"` at multiples of `5` and *fizzbuzz* at multiples of `3` and `5`**.

  ```js
  function fizzBuzz() {
      var response
      for(var i=1; i <= 100; i++) {
          response = ""
          if ( i % 3 === 0 ) { response += "Fizz" }
          if ( i % 5 === 0 ) { response += "Buzz" }
          console.log(i + ": " + response)
      }
  }
  ```

-  **Why is it, in general, a good idea to leave the global scope of a website as-is and never touch it?**

  -  It's harder to read the code and reason about it when variables seem to appear out of thin air (but really from the global scope).
  -  Anyone can update a global variable from any point in the program at any time (and from any thread if there's more than one going).
  -  General code smell - if you're too lazy to put the variable only where it needs to be then what other corners are you cutting?
  -  It's probable that you'll encounter global variable name clashes. Since there's only one namespace you're more likely to double up on a variable name.

-  **Why would you use something like the `load` event? Does this event have disadvantages? Do you know any alternatives, and why would you use those?**

-  **Explain what a single page app is and how to make one SEO-friendly.**

-  **What is the extent of your experience with Promises and/or their polyfills?**

-  **What are the pros and cons of using Promises instead of callbacks?**

-  **What are some of the advantages/disadvantages of writing JavaScript code in a language that compiles to JavaScript?**

#### TESTING QUESTIONS:

-  **What are some advantages/disadvantages to testing your code?**
-  **What tools would you use to test your code's functionality?**
-  **What is the difference between a unit test and a functional/integration test?**
-  **What is the purpose of a code style linting tool?**

#### PERFORMANCE QUESTIONS:

-  **What tools would you use to find a performance bug in your code?**
-  **What are some ways you may improve your website's scrolling performance?**
-  **Explain the difference between layout, painting and compositing.**

#### NETWORK QUESTIONS:

-  **Traditionally, why has it been better to serve site assets from multiple domains?**
  - [Serving assets from multiple domains can increase the number of assets a browser can download in parallel.](http://csswizardry.com/2013/01/front-end-performance-for-web-designers-and-front-end-developers/)
-  **Do your best to describe the process from the time you type in a website's URL to it finishing loading on your screen.**
-  **[What are the differences between Long-Polling, Websockets and Server-Sent Events?](https://stackoverflow.com/questions/11077857/what-are-long-polling-websockets-server-sent-events-sse-and-comet)**
-  **Explain the following request and response headers:**
  -  **Diff. between Expires, Date, Age and If-Modified-...**
  -  **Do Not Track**
  -  **Cache-Control**
  -  **Transfer-Encoding**
  -  **ETag**
  -  **X-Frame-Options**
-  **What are HTTP actions? List all HTTP actions that you know, and explain them.**
  1. `GET`
  1. `POST`
  1. `PUT`

#### CODING QUESTIONS:

*Question: What is the value of `foo`?*

```js
var foo = 10 + '20';
```

```js
"1020"
```

*[Question: How would you make this work?](https://stackoverflow.com/questions/2272902/make-this-syntax-possible-var-a-add23-5)*

```js
add(2, 5); // 7
add(2)(5); // 7
```

**Currying:** the process of transforming a function that takes multiple arguments into a function that takes just a single argument and returns another function if any arguments are still needed.

You need add to be a function that takes an argument and returns a function that takes an argument that adds the argument to add and itself

```js
var add = function(x) {
    return function(y) { return x + y}
}
```

*Question: What value is returned from the following statement?*

```js
"i'm a lasagna hog".split("").reverse().join("");
```

*Question: What is the value of `window.foo`?*

```js
( window.foo || ( window.foo = "bar" ) );

// SOLUTION

"bar"
```

*Question: What is the outcome of the two alerts below?*

```js
var foo = "Hello";
(function() {
  var bar = " World";
  alert(foo + bar);
})();
alert(foo + bar);
```

1.  alert of `Hello World`
2.  `Uncaught ReferenceError: bar is not defined`

*Question: What is the value of `foo.length`?*

```js
var foo = [];
foo.push(1);
foo.push(2);

// SOLUTION

2
```

#### FUN QUESTIONS:

-  **What's a cool project that you've recently worked on?**
-  **What are some things you like about the developer tools you use?**
-  **Do you have any pet projects? What kind?**
-  **What's your favorite feature of Internet Explorer?**
-  **How do you like your coffee?**

#### MY ADDITIONS

-  What is the difference between undeclared and undefined variables?
  -  if it's undefined, it was declared at somepoint
-  Think about how *this* is going to work in regards to **hoisting**

  ```js
  var a = b();
  var c = d();
  a;
  c;

  function b() {
      return c;
  }

  var d = function() {
      return b();
  }
  ```

  HOW IT COMPILES

  ```js
  function b() {
    return c;
  }
  var a;
  var c;
  var d;
  a = b();
  c = d();
  a;
  c;
  d = function() {
    return b();
  };
  ```
  - note that
    - the fx expression didn't get hoisted, while the fx declaration did
    - function get moved to the top first, than variables, then you start executing
- why hoist in the firstplace?
  - mutual recursion would not be possible w/o hoisting

    ```js
    a(1);

    function a(foo) {
        if (foo > 20) return foo;
        return b(foo+2);
    }

    function b(foo) {
        return c(foo) + 1;
    }

    function c(foo) {
        return a(foo*2);
    }
    ```

  - ```let``` gotcha

    ```js
    function foo(bar) {
        if (bar) {
            console.log(baz); // reference error
            let baz = bar;
        }
    }

    foo("bar");
    ```

- [What is the difference between event bubbling and capturing?](https://stackoverflow.com/questions/4616694/what-is-event-bubbling-and-capturing)


#### OTHER:

-  [perfectionkills.com/javascript-quiz/](http://perfectionkills.com/javascript-quiz/)
-  [testdome.com/Programming-Tests/Html-Css-JavaScript/16](http://www.testdome.com/Programming-Tests/Html-Css-JavaScript/16)
- [youmightnotneedjquery.com/](http://youmightnotneedjquery.com/)
