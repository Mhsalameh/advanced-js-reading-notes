# Content
- [Even Loop](#event-loop)
- [JS callback functions](#js-callback-functions)
- [JS Promises](#js-promises)
- [JS Async/Await](#js-asyncawait)
- [Test-Driven Development](#test-driven-development)

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

- JavaScript can do one thing at a time **_BUT not really_**, WHY NOT REALLY??
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

Prommises are a better way to manage multiple asynchronous operations, instead of events and callback functions as they have limited functionality and may create an unmanageable code. <br/>
Promises also provides better error handling than callbacks and events, it also provide a better chance for the user to read the code in a more efficient way especially if the code is implementing multiple asynchronous operations. <br/>
Promises are objects represents either completion or failure of a user task.

## why do we use promises?

- To improve code readability.
- To handle asynchronous operations in more efficient way.
- Better flow of control definition in asynchroous logic.
- Better error handling.

## Promises States

1. **fulfilled**: actions related to promise succeeding
2. **rejected**: action related to the promise faling
3. **pending**: promise is still pending (not fulfilled or rejected)
4. **settled**: Promise got fulfilled or rejected

## How do we create a promise?

- a promise is created using \*_Promise_ constructor syntax:

```
let promise = new Promise(function(resolve,reject){
    const id = "3";
    const requestedId = "5"
    if (id==requestedId){
        resolve()
    }
    else{
        rejecte()
    }
})

promise.then(()=>{
    console.log("you got the right id")
}).catch(()=>{
    console.log("you got the wrong id")
})
```

Output:
`you got the wrong id `

- .then(cb) and .catch(cb) methods are called promise consumeres, so they consumer promises by registering functions.

## .then(cb1,cb2)

if a promise is either resolved or rejected, then will be invoked either way. <br/>
takse two functions:

1. first function handles result if the promise is resolved
2. second function handles error if the promise is rejected, this parameter is optional and **.catch** is better to handle errors

```
.then(()=>{
    //handle result (success)
}, ()=>{
    //handle error
})
```

## .catch(cb)

if a promise was either rejected or if an error has occured in the execution, .catch will be invoked.<br/>
.catch method internally calls .then(null,errorHandler). we can say .catch is just a shorthand for .then(null,errorHandler).<br/>
takes one function as a parameter:

1. function to handle errors or promise rejection.
   ~~
   .catch(()=>{
   //handle error
   })
   ~~

## Applications

1. we used promises in handling asynchronous HTTP requests.
2. also promises are used for asynchronous handling of events.

# JS Async/Await

We already know the JS and a single threaded language, and we already know what the means refer to [Even loop](#event-loop), but there are some built in functionalities that we can use in our program to make it asynchronous. one of them is **Async/Await**.<br/>
Async/Await is the extension of promises.<br/>

## Async:

Async allows us to write promise base code as if it was synchronous and makes sure not to break the excecution thread.<br/>
it operates via the event loop asynchronously, and Async functions always returns a value.<br/>
it makes sure that a promise is returned and if it wasn't returned then JS will automatically wraps it in a promise which is resolved with tis value.

```
const getData = async () =>{
    let data = "Hello World"
    return data
}
getData.then((value)=>console.log(value)).
```

Output: `Hello World`

## Await:

the name says it all, Await function is used to wait for the promise it can only be used inside asynch block, it'll make the async code wait untill the promise returns a result.

```
const getData = async() => {
	var y = await "Hello World";
	console.log(y);
}

console.log(1);
getData();
console.log(2);


/*
Output:
1
2
Hello World
*/
```

here the "2" is printed before "Hello World" because we used await.

# Test-Driven Development

Testing is important, is it can find problems and bugs in your code that you didn't know about, and there are two methods for testing we will mention manual and automated.

- Manual Testing.
  Just manually going through the application from the user's prespective, navigating around the site to test the functionality of the application and to find bugs.
- Automated Testing.
  does what manual testing do but much faster, automated testing will do multiple tasks that we can define to our site and will check the output of each task it does and see if there was a malfunction or a bug during the operation of these tasks.

in Test-Driven Development we first decide what our code should do and then we create a failing test. Then we will write the code that will make this test pass, it's mostly associated with automated testing. but the princible itself can be applied in manual testing as well.<br/>

Here is an example of creating a table with Test-Driven Development (TDD). :

```
*I expect the table to be four feet in diameter.

The test fails because I have no table.

I cut a circular piece of wood four feet in diameter.

The test passes.*

*I expect the table to be three feet high.

The test fails because it is sitting on the ground.

I add one leg in the middle of the table.

The test passes.*

*I expect the table to hold a 20-pound object.

The test fails because when I place the object on the edge, it makes the table fall over since there is only one leg in the middle.

I move the one leg to the outer edge of the table and add two more legs to create a tripod structure.

The test passes.*
```

## How to setup a test
- We need to setup the testing enviroment first. We can use Jest as a testing suite as we will need a testing library and an assertion library, but jest here is an all in one solution. assertion is what we expect our code to do.
- to setup the project we will first.
    1. create an NPM project using : `npm init`.
    2. create **filename.js** file and add it to the project's root
    3. install Jest :`npm install jest --D`
    4. update the **package.json** test script `"test":"jest"` to run jest with `npm run test`;

    jest will be looking for a file name with some specific charecterstics such as **.spec** or **.test** within the file name

    5. we update the **filename.js** file to be **filename.test.js**
    6. we write our test.

## How to write a test?
tests are function that receives a couple of arguments, we call our test with **it()** or **test()**
```
//filename.test.js

test("testing filename", ()==>{
    expect(1).toBe(1);
})
```
- test() arguments:
    1. a title or description **"testing filename""**
    2. a function to assert something about our code **expect(1).toBe(1)**, here in expect we can check a variable in our code and in toBe we put our assertion of that variable. in this example it's always true so the test will always pass
