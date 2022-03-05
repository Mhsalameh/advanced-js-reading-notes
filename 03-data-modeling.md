# Data Modeling

## questions

1. Name 3 advantages to Test Driven Development
    1. higher productivity
    2. fewer bugs
    3. makes maintainance much easier
2. In what case would you need to use beforeEach() or afterEach() in a test suite?
    - we use beforeEach to run a block of code before each test
    - we use afterEach to run a block of code after each test
3. What is one downside of Test Driven Development
    - TDD needs committed team that all agree on the efficiency of TDD, and it requires more time early.
4. What’s the primary difference between ES6 Classes and Constructor/Prototype Classes?
    - ES6 classes : its syntax is similar to object creation in other object-oriented programming languages
    - ES5 Constructor/Prototype: its syntax is unique and is not found in other object-oriented programming languages.
5. Why REST?
    - it provides flexibility, data isn't tied to resources or methods, REST can handle multiple type of calls and return different formats of data.

## Vocabulary terms
- functional Programming
    - (**FP**) is the process of building software by composing pure functions, avoiding shared state, mutable data, and side-effects. Functional programming is declarative rather than imperative, and application state flows through pure functions. It helps us to solve problems effectively in a simpler way. Some of the popular functional programming languages include: **Lisp, Python, Erlang, Haskell, Clojure**
- object-oriented programming (OOP)
    - (**OOP**) is a computer programming model that organizes software design around data, or objects, rather than functions and logic. An object can be defined as a data field that has unique attributes and behavior. Object-oriented programming has four basic concepts: **encapsulation, abstraction, inheritance, and polymorphism**. There are many object-oriented programming languages including **JavaScript, C++, Java, and Python**
- class 
    - A class is a template definition of the methods and variables in a particular kind of object
- super
    -  `Super` keyword acts as a reference variable to the parent class. It is mainly used when we want to access a variable, method, or constructor in the base class from the derived class.
- this
    - `This` keyword refers to an object. Which object depends on how this is being invoked (used or called). The this keyword refers to different objects depending on how it is used: In an object method, this refers to the object
- Test Driven Development (TDD)
    - Test Driven Development (TDD) is a software development practice that focuses on creating unit test cases before developing the actual code.
- jest
    - Jest is a JavaScript testing framework designed to ensure correctness of any JavaScript codebase. It's an open source project maintained by Facebook, and it's especially well suited for React code testing, although not limited to that: it can test any JavaScript code
- Continuous Integration (CI)
    - Continuous integration is a DevOps software development practice where developers regularly merge their code changes into a central repository, after which automated builds and tests are run. Continuous Integration enables better transparency and farsightedness in the process of software development and delivery. 
- REST
    - REST stands for REpresentational State Transfer. It means when a RESTful API is called, the server will transfer to the client a representation of the state of the requested resource. REST defines a set of constraints for how the architecture of an Internet-scale distributed hypermedia system, such as the Web, should behave.
- Data Model
    - Data models are visual representations of an enterprise's data elements and the connections between them. By helping to define and structure data in the context of relevant business processes, models support the development of effective information systems.

## What is SQL?
*SQL** stands for **S**tructured **Q**uery **L**anguage, it is a language that allows you to write databse queries that looks like this:
```
SELECT * FROM TABLE
```
- How does it work?
     It works with **tables**, we can call a table like our data bin.
     SQL is strict about what we store in our tables, it needs to be precise with a clear schema of which data can go into a table
     Schema is defined by what is called **fields (Columns)**, it cannot have more fields than the one we defined in our table
     Every new **record (Rows)** we add to our table has values for these fields, it is not possible that one record has different fields if we want to add a new field all the records need to have that field (can be null or empty but atleast provides an information)
     We work with multiple tables which are related by a unique field like (order number). So we can say SQL has strict schema and is relational
     we have multiple type of relations in SQL **Many-to-Many** , **One-to-Many**, and **One-to-One** 
     **One-to-One** is when a record inside a field can relate to another field
     **One-to-Many** is when a record inside a field can relate to multiple fields
     **Many-to-Many** is when multiple fields relate to each others using a record inside of them



## What is NoSQL (MongoDB)?
The name for stands for **Humongous** because it can store a huge ammount of data
- How does it work?
    - We do have databases in MongoDB but instead of tables we have something called **Collections** <br/>
    - Inside the **Collections** we have what is called **Documents** it is similar to rows inside a table. It looks like a JSON format, but multiple   **documents** in one **collections** that can have different fields, which means they don't have to follow the same schema, like if we have these document inside the same collections :
    ```
    document1--> id:1    name:'Maxe'     age:29
    document2--> id:2    name:'Khaled'
     ```
    - Its super flixable, like if you want to change the schema of your data at one point, you don't have to change already collection data's schema and just start adding what you want to add in the document, and you can still store them all in the same collection.

    - No/Few Relations, NoSQL doesn't rely much on relations like SQL, you can kind of relate multiple documents inside the collections together but NoSQL isn't reliant on that. Instead we can put all the information in one place 

## Main differences
- SQL vs NoSQL<br/>
    | SQL | NoSQL |
    | ----------- | ----------- |
    | Data use schemas | Schemaless |
    | Relations | No/Few relations |
    | Data is distributed in multiple tables | data is nested in a few collections |
    | Horizontal scaling is difficult, vertical scaling is possible | Both horizontal and vertical scaling is possible |
    | Limitations for read & write queries per second | Great performance for mass read and write requests |


## Preview
1. Which 3 things had you heard about previously and now have better clarity on?
    1. SQL
    2. relational databases
    3. Classes and the difference between ES6 constructor and ES5 constructors

2. Which 3 things are you hoping to learn more about in the upcoming lecture/demo?
    1. More about databases
    2. NoSQL
    3. sequelize API
3. What are you most excited about trying to implement or see how it works?
    - I want to know more about NoSQL and how we use it

## Bookmarks
- [Sequilize API](https://sequelize.org/master/)
Sequelize is an ORM tool for many relational DBMSs.
