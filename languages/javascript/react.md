# React

*From: [Wikipedia]()*

> React is an open-source JavaScript library providing a view for data rendered as HTML. React views are typically rendered using components that contain additional components specified as custom HTML tags. React promises programmers a model in which subcomponents cannot directly affect enclosing components ("data flows down"); efficient updating of the HTML document when data changes; and a clean separation between components on a modern single-page application.

*From: [HackerNews](https://news.ycombinator.com/item?id=11204481)*

> React brings two important ideas to web app development:

> 1.  **The virtual DOM**. When I'm writing jQuery-based code, I have to write both a component template and code that updates the DOM in response to input; when I'm writing code for a virtual DOM, the component template is sufficient to update the DOM and I don't have to write that extra code, so there are fewer chances for bugs to creep in.

> 2.  HTML-like syntax embedded in Javascript (JSX). I didn't like this at first until I configured Sublime Text to highlight embedded HTML correctly. Embedded HTML has pros and cons, but I think it's a net positive.

> React projects also typically include new tech like ES2015, webpack, hot code reloading, and Redux with its time-traveling debugger. You can build your own stack that uses a virtual DOM library, embedded HTML, ES2015, and so on, but it's helpful to start with a common stack that many people understand. That's why React is interesting.

---

## Structures

### Basic

```sh
- actions
- components
- images
- reducers
- services
- utils
- app.js
```

|               |                                                                                                                                                                                                                                                                                              |
|:-------------:|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  `/actions`   | Flux action creators                                                                                                                                                                                                                                                                         |
| `/components` | These are all the JSX React components (the presentation layer) - so there are subfolders like "pages", "controls", etc.                                                                                                                                                                     |
|  `/reducers`  | These are Redux reducers - they're the logic that handles all of the application state                                                                                                                                                                                                       |
|  `/services`  | We use basic ES6 modules for services, with methods like "fetchUser(id)" which use the new JS Fetch API behind the scenes. We then have redux-thunk and redux-promise middleware so we can easily offload state manipulation to these services without actually putting state logic in them. |

---

## Unsorted

-   refs: <https://facebook.github.io/react/docs/more-about-refs.html>
-   findDOMNode: <https://facebook.github.io/react/docs/top-level-api.html#reactdom.finddomnode>

---

## References

-   [Docs](https://facebook.github.io/react/docs/getting-started.html)
-   [GitHub](https://facebook.github.io/react)
-   [HackerNews: Free React.js Fundamentals Course](https://news.ycombinator.com/item?id=11204481)
-   [ReactForDesigners: React.js Introduction For People Who Know Just Enough jQuery To Get By](http://reactfordesigners.com/labs/reactjs-introduction-for-people-who-know-just-enough-jquery-to-get-by/)
-   [ReactJSProgram: Fundamentals](http://courses.reactjsprogram.com/courses/reactjsfundamentals)
-   <https://en.wikipedia.org/wiki/React_(JavaScript_library)>
