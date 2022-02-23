# Data Modeling

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
    | SQL      | NoSQL |
    | ----------- | ----------- |
    | Data use schemas      | Schemaless       |
    | Relations   | No/Few relations        |
    | Data is distributed in multiple tables   | data is nested in a few collections        |
    | Horizontal scaling is difficult, vertical scaling is possible   | Both horizontal and vertical scaling is possible        |
    | Limitations for read & write queries per second   | Great performance for mass read and write requests        |


    