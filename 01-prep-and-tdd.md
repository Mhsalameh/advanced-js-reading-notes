# Event Loop

## JavaScript is single threaded programming language what does that mean?

It can do one thing at a time as simple as that, the program can run one piece of code at a time.

```
        one thread == one call stack == one thing at a time
```

## What is call stack ?

The call stack is a data structure that records where did we reach in the program, let's look at the example below:

```
function multiplay(n1,n2){                      
    return n1*n2; 
}

function square(n){
    return multiplay(n,n)                               (our full stack)
}                                                ---------------------------          
                                                 | + 4 multiplay(3,3) -5  |
function printSquare(n){                         | + 3 square(3) -6        |
    let result=square(n);                        | + 2 printSquare(3) -7   |
    console.log(result);                         | + 1 [main()] -8         |
}                                                ---------------------------    

printSquare(3);
```
as you can see the stack above with steps (from 1 to 8) to what happend in the stack (+) means push, (-) means pop .

## What's blocking?

- Blocking is running a slow code that will block the stack untill it's done, like counting from 1 to 10 million is slow.
- Slow is problem because we are using browsers, we can't render anything including events untill the code is done running
- the solution is [asynchronous callbacks](#js-callback-functions) which we'll get to talk about it later below let's look how the call stack looks with call backfunctions

```
console.log('Hello')
                                                             ------------------------------
                                                             | + 9 log("My name is")-10   | 
setTimeOut(function (cb){                                    | + 6 log("Mohammad) -7      |
console.log('My name is')                                    | + 4 setTimeOut(cb,5000) -5 |
}, 5000)                                                     | + 2 log('Hello') -3        |   
                                                             | + 1 [main()] -8            |
console.log("Mohammad")                                      ------------------------------
```
so basically here everything else in the code ran before **console.log('My name is")** in step 4 when we push setTimeOut to the call stack it just popped right after that and the next code runs whhich is console.log("Mohammad"), and after 5 seconds **console.log('My name is')** appears in the stack and we log the message inside it.

## Cocurrency and Event Loop
- JavaScript can do one thing at a time ***BUT not really***, WHY NOT REALLY??
We have the browser to help with that, 
remember the function in step 4 that deleted poped from the call stack and returned it's callback function after 5 seconds, seTimeOut(af,5000). While the javascript runtime can do one thing at a time, the browser gives us WebAPIs here the cocurrency starts.
- setTimeOut is a WebAPI that was called from the browser, so we just called it and the timer sets of in the WebAPI.
- the API can't push directly to stack so it calls a task queue to help out.
- after the 5 seconds are done the API will push your callback function which is **cb** in this example to the task queue
- then we get to what's called the event loop which is out Main topic here.

## What's the Event loop
The event loop looks at the task queue and the call stack, if the stack is empty it'll take the first thing on the queue and push it to the stack which will run it.
- what will the event loop do if we set the time to 0?
wehen we get to step 4, the WebAPI will not wait 5 seconds before pushing the function to the task queue, instead it'll push it directly, but the event loop will not push it to the stack untill the stack it clear.

## Why do we need it exactly?
- as we said before we are in a browser, so if we got stuck in one piece of code other pieces of code won't render and events will not be handled, so the task queue is good for the job, it'll push the functions that are inside the queue everytime it sees the stack is empty.
- so doing other things during this can be rendered, and buttons will function normally.
---

# JS callback functions

## How do we pass a function as a parameter?

In JavaScrip functions are objects at the same time, we can pass objects to functions as parameter i,e.

    function print(callBack){
        callBack();
    }

In above example we identified a function called "**print**" with a parameter called "**callBack**" and we called the **callBack** parameter as function inside **print**.

## Why do we use callback functions?

JavaScript codes run in top-down order and in sequence.
We use callback function to help us develop **asynchronous** JavaScript code, as in some cases our code runs or (should run) after something else and not **sequentially**.
**Callbacks** makes sure that a function isn't going to run before a task is completed but will run as soon as the task is done.
this will keep us safe from **problems** and **errors**

## Creating a Callback function

- A simple example can be **setTimeOut**.

```
const message = function() {
console.log("this message is shown after 1 second)
}
setTimeOut(message, 1000);
```

setTimeOut function takes two parameters:

1. A callback function (**message**)
2. a number endicating a period of time in **milliseconds** (**1000**)

- We can also make the expresion above with an **Anonymous Function**

```
setTimeOut(function(){
console.log("This message is shown after 1 second")
}, 1000)
```

- or we can use an **arrow function**

```
setTimeOut(()=>{
console.log("this message is shown aftet 1 second")
}, 1000)
```

- another example is event handling

let's say we have a button and we want the button to **console a message** when clicked

```
<!-- HTML -->
<button id="callback-btn">Click here</button>
<!-- HTML -->

//JavaScript:
const btn=document.getDocumentById("callback-btn);

callback-btn.addEvenetListener("click", ()=>{
    console.log("button was clicked");
})
```

the arrow function here is a callback function that will not execute untill the button element is clicked.

# JS Promises

# JS Async/Await

# Test-Driven Development
