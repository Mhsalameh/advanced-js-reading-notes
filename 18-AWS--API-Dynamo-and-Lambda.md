# AWS: API, Dynamo and Lambda

## What is DynamoDB?

DynamoDB is a hosted NoSQL database offered by Amazon Web Services (AWS).

- features:

  - reliable performance even as it scales;
  - a managed experience, so you won't be SSH-ing into servers to upgrade the crypto libraries;
  - a small, simple API allowing for simple key-value access as well as more advanced query patterns.

- Key Concepts:

  - Tables, Items, and Attributes
    - A table is a grouping of data records. For example, you might have a Users table to store data about your users, and an Orders table to store data about your users' orders. This concept is similar to a table in a relational database or a collection in MongoDB.
    - An item is a single data record in a table. Each item in a table is uniquely identified by the stated primary key of the table. In your Users table, an item would be a particular User. An item is similar to a row in a relational database or a document in MongoDB.
    - Attributes are pieces of data attached to a single item.
  - No Relational model
    - The relational data model is a useful way to model many types of data. Often, relational data is normalized to improve the integrity of the data. Rather than duplicating a particular piece of data in multiple rows, you can store it in one place and refer to it using a JOIN operation from one table to another. Now you can update that single place, and all items that refer to that data will gain the benefits of the update as well.
  - Availability > Consistency
    - Instead of maintaining a single database instance, perhaps Twitter wants to have two instances that are exact replicas -- one in Virginia and one in Singapore. If we still want to maintain strong consistency, this means a user must get the same answer if she queries the Virginia instance or the Singapore instance at the same time. This could be implemented by a more complex system on database writes -- before Bob's tweet is committed to the database, it has to be submitted to both the Virginia instance and the Singapore instance. Now Bob's request needs to make the hop across the ocean and back. This results in slower write times to some users. Strong consistency is important for certain use cases - think bank account balances - but less important for others, such as our Twitter example or the Amazon shopping cart, which was the impetus for Dynamo. For these use cases, speed and availability are more important than a consistent view of the world. By weakening the consistency model of a relational database, the Dynamo engineers were able to provide a database that better fit the needs of Amazon.com.
  - Infinitely Scalable
    - The final key aspect of Dynamo is that it is infinitely scalable without any negative performance impacts. This aspect is a result of the relaxing of relational and consistency constraints from prior databases.

- Enviroment Setup

  - Install the AWS CLI

  ```bash
  pip install awscli
  ```

  - Get IAM credentials

    ```json
    {
      "Version": "2012-10-17",
      "Statement": [
        {
          "Effect": "Allow",
          "Action": ["dynamodb:*"],
          "Resource": "*"
        }
      ]
    }
    ```

    Once you have the keys for your IAM user, you can add your profile with aws configure:

    ```bash
    $ aws configure
    AWS Access Key ID [None]: AKIAIOSFODNN7EXAMPLE
    AWS Secret Access Key [None]: wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
    Default region name [None]: us-west-2
    Default output format [None]: json
    ```

  -

## Dynamoose

Dynamoose is a modeling tool for Amazon's DynamoDB. Dynamoose is heavily inspired by Mongoose, which means if you are coming from Mongoose the syntax will be very familar.

- Key features:
  - Type safety
  - High level API
  - Easy to use syntax
  - Ability to transform data before saving or retrieving documents
  - Strict data modeling (validation, required attributes, and more)
  - Support for DynamoDB Transactions
  - Powerful Conditional/Filtering Support
  - Callback & Promise support

## Amazon API Gateway

API Gateway sits between the backend services of your API and your API’s users, handling the HTTP requests to your API endpoints and routing them to the correct backends. It provides a set of tools that help you manage your API definitions and the mappings between endpoints and their respective backend services. It can also generate API references from your definitions and make them available to your users as API documentation.

## bookmarks

- [AWS API Gateway Overview](https://www.serverless.com/amazon-api-gateway)
- [AWS API Gateway](https://www.serverless.com/amazon-api-gateway)
- [AWS DynamoDB Guide](https://www.serverless.com/amazon-api-gateway)
- [AWS DynamoDB](https://aws.amazon.com/dynamodb/)
- [Dynamoose](https://dynamoosejs.com/getting_started/Introduction)
