---
# You can also start simply with 'default'
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://cover.sli.dev
# some information about your slides (markdown enabled)
title: Welcome to Slidev
info: |
  ## Microtasks vs. Macrotasks in JavaScript

# apply unocss classes to the current slide
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: slide-left
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true
---

# Microtasks vs. Macrotasks in JavaScript

---
transition: fade-out
layout: image
---

<img src="https://i.ibb.co/nbQc6sk/Javascript-event-loop.png"/>

---
transition: slide-up
---

<img src="https://img.notionusercontent.com/s3/prod-files-secure%2Fc547a10a-75b8-4e3e-b0c0-5c35e28991da%2F347b65d0-1aa6-4061-8493-eedeabaf1122%2Fimage.png/size/w=1420?exp=1727269649&sig=buC48pAJCb-2FFKIZ8CwJ7Og7BtPse7xn6kjw8F4lnI"/>

---
transition: slide-up
---

Microtasks are small tasks that run immediately after the current execution, before any rendering or I/O. They include:

- Promises (.then(), .catch())

- queueMicrotask() method

- MutationObserver callbacks: Web API

---
transition: slide-up
---

Macrotasks are used for tasks that run at a later point, allowing the browser to render updates or perform I/O in between. Common macrotasks include:

- setTimeout()

- setInterval()

- setImmediate() (Node.js)

- I/O callbacks

- Event listeners

---
transition: slide-up
---

<img src="https://res.cloudinary.com/practicaldev/image/fetch/s--05Fi8vBq--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_66%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/i/42eatw03fcha0e1qcrf0.gif?trk=public_post_comment-textv"/>

---
transition: slide-up
---

Event Loop and Task Execution

JavaScript's event loop processes tasks in a specific order:

1. Script Execution: Runs the code.
2. Process Microtasks: Executes all microtasks in the queue.
3. Render (if needed): The browser may update the UI.
4. Process Macrotasks: Handles the next macrotask and then repeats the loop.

---
transition: slide-up
---

```ts {monaco} { editorOptions: { wordWrap:'on'} }
console.log("Script start"); // (1)

// Macro task
setTimeout(() => {
    console.log("Macrotask: setTimeout"); // (6)
}, 0);

// Micro task
Promise.resolve()
    .then(() => {
        console.log("Microtask: Promise 1"); // (3)
    })
    .then(() => {
        console.log("Microtask: Promise 2"); // (4)
    });

// Another micro task
queueMicrotask(() => {
    console.log("Microtask: queueMicrotask"); // (5)
});

console.log("Script end"); // (2)

```

---
transition: slide-up
---

Key Differences

- Microtasks run immediately after the current script, and before any rendering or macrotask.
- Macrotasks run after microtasks and allow the browser to perform rendering or handle I/O operations.

Best Practices

1. Use Microtasks for Immediate Actions: Ideal for promises or callbacks that need quick execution.
2. Use Macrotasks for Delayed Actions: Suitable for timers, intervals, or event listeners where some delay is acceptable.
3. Understand the Execution Order: Helps avoid unexpected behavior in your asynchronous code.

---
transition: fade-out
layout: end
---

Thank you!

