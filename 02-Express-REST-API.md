# questions
1. Name 3 real world use cases where you’d want to change the request with custom middleware
    - logging
    - authentication and authorization
    - error handling
    - validate params
2. True or false: The route handler is middleware? ***true***

3. In what ways can a middleware function end the process and send data to the browser? by not calling the next function in the middlware

4. At what point in the request lifecycle can you “inject” middleware? right after the requesting the path and before responding.

5. What can cause express to error with “Request headers sent twice, cannot start a second response”?


# Classes

## How to define a class?
- Class Declaration:
to declare a class we use the `class` with the name of the class as below example:
```
class Rectangle{
    Constructor(height,width){
        this.height=height;
        this.width=width;
    }
}
```
note that classes must be defined before calling them; while class is hoisted it's values are not initialized.

- Class expressions
It can be named or unnamed as seen below:

```
//unnamed
const Rectangle = calss {
    constructor(height,width){
        this.height=height;
        this.width=width;
    }
//named
const Rectangle = class Rectangle2 {
    constructor(height,width){
        this.height=height;
        this.width=width;
    }
}
}
```
note that the constructor we using here is a special method of class for creating and initializing an object instance of that class

# Express Routing

To define routing we use express app methods that corresponds with http methods such as:
```
const express = require('express')
const app = express()

// handle get requests
app.get('/', (req,res)=>{
    res.send("Home Page")
})

//handle post requests
app.post()

//hanlde all HTTP methods
app.all()

//specify middleware as the callBack function
app.use()
```

express app methods takes the following arguments :
- a path like `'/'`.
- a list of middlewares

# Middleware
## what's a middleware?
middleware is a function or a program that runs after receiving a request and before sending a response. A simple middleware can be 
```
(req,res)=>{
res.send("home page")
}
```
but we don't usually call this action a middleware. <br/>

a middleware can take three arguments (req,res,next)
an error-handling middleware can take four arguments (error, req, res, next)

## Application-level middleware
- means that the middleware will applay to the app requests
- we will use app.use() here 
```
const express = require('express');
const app = express();

app.use((req,res, next)=>{
    console.log('request type', req.method)
    next ()
})
```

## router-level middleware
- same as application level but it is connected to express().Router instance `const router = express().Router`
- example :
```
const express = require('express')
const app = express()
const router = express.Router()

//
router.use((req,res, next)=>{
    console.log('log');
    next()
})

```



# Using express router

- first we need to import express in our server `const express = require('express');`
- `const app=express();`
- then we create an instance for our app `const router = express().router;`
- call the port from .env file `let PORT = process.env.PORT || 3000;`
- we apply routes to our router using HTTP methods
    ```
    //home page "localhost:3000"
    router.get('/',(req,res)=>{
        res.send("home page")
    })
    //data page "localhost:data"
    router.get('/',(req,res)=>{
        res.send("data page")
    })
    // apply the routes to our root, if we used something like '/app' instead of '/' we can visit home using localhost:300/app/
    app.use('/',router)
    ```
- using router we can create multiple `express.router()`s and apply them to our application.
