# How does timers work with the asynchrony of JavaScript? 

There are two types of timers: 

* SetTimeout : allows to delay the execution of a function 

* SetInterval: allows to run a code in a loop with intervals in between 

JavaScript works in a single threat, so the delays, and timers are not part of JavaScript but part of the window timers in the WEB API. 

As running in a single threat, there is no concept as delaying, because this will cause the browser to get blocked. 

The relationship between the timers and JavaScript is done by the event loop. 

 ![Event Loop, https://dev.to/lydiahallie/javascript-visualized-event-loop-3dif ](images/event_loop.png)

The event loop works with different parts: 

* The heap → memory allocation without any order, where the objects are allocated 

* Stack of methods → single threat that follows the LIFO (last in first out) that keeps track of the current function in execution 

* Web API’s → This includes the DOM API, ajax requests, `setTimeout`, `SetInterval`, HTTP requests, etc. 

* Queue of callbacks  → where the callbacks from the api’s are added before they pass to the stack 

Eventhough `setTimeOut` and `SetInterval` are used with indication of time 

```Javascript
setTimeout( 

function callback1() {  

   console.log('this is a message from callback1');  

}, 0); 
```

This time is not guaranteed, this means that if a setTimeout or setInterval is send with time 0, it is not guaranteed that that it would immediately run the code. This is because it depends on the event loop and the number of tasks in the queue of callbacks that are waiting to pas to the stack of methods, and then, executed by JavaScript. 
