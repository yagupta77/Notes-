# Notes-  Mastering Database Fundamentals with MongoDB

Mastering Database Fundamentals with MongoDB

 1.Introduction to Database and DBMS 

 A Database is a structured collection of data that allows efficient storage, access, and management.

Why Use a Database
    -> Organize and retrieve data efficiently
    -> Ensure data security and integrity
    -> Support multiple users
    -> Handle large data volumes
    -> Provide backup and recovery

ISAM (Indexed Sequential Access Method)
    Early method of storing data using indexes for faster sequential access.

DBMS (Database Management System)
    Software that manages databases and handles operations like Create, Read, Update, Delete (CRUD).
    Examples: MySQL, MongoDB, PostgreSQL.

Components of a Database System
    -> DB Server: Handles client requests and manages data (runs as a TCP server).
    -> DB Client: Connects to the server.
        -> GUI Clients: MySQL Workbench, MongoDB Compass
        -> Terminal Clients: mysql, mongo
        -> Drivers: Used in apps (e.g., MySQL Node.js driver)

    -> Storage Engine: Stores data on disk (e.g., InnoDB, WiredTiger)

Communication Protocols
    Databases use their own protocols over TCP to talk to clients:
        -> MySQL Protocol
        -> MongoDB Wire Protocol



 2. Type Of DataBases

Relational Database (RDBMS)

    -> Stores data in tables, like Excel sheets.
    -> Data is organized in rows and columns.
    -> You must define the structure (schema) before adding data.
    -> Good at handling linked data (e.g., customers and their orders).
    -> Very accurate and reliable – used in banking, business apps.
    -> Needs powerful machines to scale.
    -> Examples: MySQL, PostgreSQL.

Non-Relational Database (NoSQL)

    -> Stores data in a more flexible way – like JSON files, key-value pairs, or graphs.
    -> You don’t need to define a fixed structure before adding data.
    -> Good for fast-changing or large amounts of data.
    -> Easier to scale across many computers.
    -> Used in apps like social media, real-time chats, analytics.
    -> Examples: MongoDB, Redis, Cassandra.

In Simple Terms:

    -> Use Relational DB when your data is organized and linked (like school or bank data).
    -> Use Non-Relational DB when your data is messy, big, or changes often (like social media posts or logs).


3. Introduction Of MongoDB

**MongoDB** is a popular open-source NoSQL database that stores data in a flexible, document-oriented format. It is designed to handle large-scale, high-performance applications while offering scalability, flexibility, and ease of use.

## What does the term Mongo mean?
The term "Mongo" in MongoDB is derived from the word "humongous", which reflects the database's ability to handle large volumes of data. MongoDB is designed to manage massive datasets and scale horizontally, making it suitable for modern applications that require handling extensive amounts of information efficiently.


## Key Features of MongoDB

1. **Document-Oriented**: 
   - Stores data in JSON-like BSON (Binary JSON) documents, allowing for hierarchical data storage and flexible schemas.

2. **Schema-Less**:
   - No predefined schema is required, enabling developers to store data with varying structures.

3. **Scalability**:
   - Supports horizontal scaling through sharding, making it suitable for applications with large datasets and high traffic.

4. **Rich Query Language**:
   - Offers a powerful query language (MQL) to perform CRUD operations, aggregations, and more.

5. **Indexing**:
   - Provides efficient indexing to enhance query performance.

6. **Replication**:
   - Ensures high availability and fault tolerance through replica sets.

## Use Cases of MongoDB

- Real-time analytics and big data applications.
- Content management systems (CMS) and blogs.
- IoT and sensor data storage.
- E-commerce platforms and product catalogs.
- Mobile and web applications with dynamic data requirements.

## Popular Integrations

MongoDB integrates seamlessly with modern programming languages and frameworks like:
- Node.js
- Python (Django, Flask)
- Java (Spring)
- Express.js (via Mongoose)

## Why Use MongoDB?

MongoDB’s flexible data model, scalability, and rich feature set make it an excellent choice for modern, high-performance applications that require handling unstructured or semi-structured data efficiently.


 5.Mongo Shell 

    It is a node REPL.
    Since it is a node REPL, we can do all the operations of NodeJS.

    mongo shell uses full node.exe but has modified it for handling database operations.

    Difference between node REPL and mongoSh REPL

    Node REPL:
        1. Undefined is return if there is no return value.
        2. Does not highlights the code.
        3. In case of promise, it returns the full promise object.
        4. We cannot redeclare, redefine a const variable.
        5. await can de used in global space.
        6. Npm can be accessed and used. 
        7. Don't have extra commands for handling databases. 
        8. process.exit() is used for exiting.

    MongoSH REPL:
        1. Newline character (Empty line) is returned if there is no return value.
        2. Highlights the code.
        3. In case of promise, it returns resolve value of promise, Highlights the Error in case of rejection.
        4. We can redeclare, redefine a const variable.
        5. await cannot be used in global space. ( use async function )
        6. NPM cannot be accessed.
        7. Have extra commands for handling databases. 
        8. exit command use to exit the shell

Key points:

The Complete Picture: MongoDB's Developer-Friendly Design
1. The Core Problem: The Mental Switch
Developers had to constantly switch between two mindsets:
Application Code: Thinking in objects, dictionaries, and lists (e.g., {name: "Alice"}).
Database Queries: Thinking in a different language like SQL (INSERT INTO users...).
This context switch was inefficient and frustrating.

2. The Vision: One Unified World
MongoDB’s goal was to eliminate this switch. Since modern apps use JSON-like data, MongoDB stores data in the same way—as JSON-like documents (BSON). This means the data in your database looks identical to the data in your code.

3. The Perfect Example: The MongoDB Shell (mongosh)
The shell is the purest expression of this vision. It’s a JavaScript environment where you interact with the database using plain JavaScript—no new language to learn.

javascript
// This is just JavaScript! No mental switch.
db.users.insertOne({name: "Alice"})
4. How This Works for Every Language (Python, Java, etc.)
The seamless experience doesn't end with JavaScript. For any other language, MongoDB provides a Driver (e.g., pymongo for Python).

The Driver’s Job: To mimic the MongoDB shell’s API in the style of its native language.

In Practice: This means you write commands in Python or Java that look and feel almost identical to the shell commands.

Python Example:

python
# This is Python code, but the style is inspired by the JS shell.
db.users.insert_one({"name": "Alice"})
5. The Magic Behind the Scenes: Universal Translation
Whether you use the JavaScript shell, a Python driver, or a Java driver, they all do the same thing:

They take your native code (JS objects, Python dicts, Java Maps).

They translate it into a universal language called BSON.

They send this BSON over the network to the MongoDB server using the Wire Protocol.

The server doesn't care what language you used. It only understands BSON. The driver and shell handle all the translation for you, making the experience consistent everywhere.

6. Why the Shell Feels Like Node.js
To be a powerful tool, the shell needed more than just variables and loops—it needed file operations, networking, and timers. Instead of building this from scratch, MongoDB used Node.js as a blueprint. The shell is built on the same technology (V8 engine) and offers familiar APIs (like require('fs')), but with custom, secure versions to keep your database safe.

In a Nutshell:
MongoDB gives you a consistent way to work with your database, no matter your programming language.

For JavaScript developers, the mongosh shell provides a native, powerful environment.

For all other developers, official drivers provide the same simple, intuitive experience tailored to their language.

The result: You always get to think in your code's native data structures, completely eliminating the old, frustrating context switch.


7. Installing and Understanding MongoDB Server

   Clients to Connect to MongoDB Server

    -> MongoDB Compass: Official GUI client for interacting with the server.
    -> MongoDB VS Code Extension:
        Acts as another client to connect to the server.
        Often provides more detailed views and features than Compass (like document preview, schema, and queries within the editor).

   MongoDB Server Summary

    -> MongoDB Server is mainly built in C++, along with other languages.
    -> Port: It uses a fixed default port 27017 (other ports won't work unless configured).
    -> On installation, MongoDB defaults to a virtual test database, which isn’t created on disk until data is stored.
    -> You can view available databases with:
        show("databases") or its short form show dbs.


8.Fundamentals of MongoDB: Databases, Collections, and Documents

Fundamentals of MongoDB

    MongoDB Server by default creates these databases:
    (We should not manipulate them) 
        -> admin
        -> config
        -> local

    Database:
        -> The main entity for our app is Database. 
        -> It can have multiple collections
        -> Drop database means DELETE Database.
        -> It is only created when we have atleast one collection & one document.

    Collections:
        -> It is a part of Database.
        -> It can have multiple documents.
        -> It is not actually array, but like array.
        -> Drop collection means DELETE Collection.
    
    Documents:
        -> It is JSON Object, which stores the actual data.

    Understandig this through making storageApp DB:
        Main Entity(DataBase) -> StorageAppDB
        Collection -> directoriesCollection.json
        Document -> Each Directory Object

    Connections:
        -> It means a connection between the client and the server.
        -> There can be different (user) connections on a single server.

    Commands:
        -> use("<Database Name>") OR use <Database Name>
            If the database it not-existing. It create a non-existence database. And use it
        -> show collections
            It will show all the existing collections.


 9.Create Operation in MongoDB

    Create Operation through GUI:
        -> Click '+' on Connection
        -> Enter DB name, Collection name.
        -> For creating document:
            -> Click on "Add Data" in Collection.
            -> You have 2 Options (import JSON or insert document)
            -> Write your data in JSON Format.

        -> It will store in the main Server.

    Create Operation through Shell:
        -> use <Database Name>
        -> db.<CollectionName>.insertOne(<Document>)
            It will create a collection and insert the data(document) in it.

        -> db.<CollectionName>.insertOne(<Documents>)
            It will create a collection and insert all the data(documents) in it.

    Access it thorugh Shell:
        -> db represent to the current database used.
        -> we can do db.<collectionName>.find()
            It will show all the available documents in it.


10. Read Operation in MongoDB

    Read Operation in MongoDB

    -> db represent to the current database used.
    -> we can do db.<collectionName>.find()
        It will show all the available documents in it.
        It returns a cursor, it is like an array
    
    -> For finding specific documents we can pass an object in find()
        db.<collectionName>.find({ user: "23" })

    -> Just like find we also have findOne method,
        Which returns only the first match (as Object not cursor).
        db.<collectionName>.findOne({ user: "23" })

    -> If we want to find document in more depth, use configuration object:
        db.<collectionName>.findOne({ user: {$gt : 2} })

        $gt -> greaterThan
        $gte -> greaterThanEqualTo
        $lt -> LessThan
        $lte -> LessThanEqualTo

11. Inspecting MongoDB Data Packets in Wireshark

      Behinds the Scenes Mongo Data Packets

    -> MongoDB Protocol is built on top of TCP.
    -> It make a three way TCP handshake.
    -> Send request-response in every 3-5 Secs for checking it connection is alive or not.
    -> For every DB call(Operation) a request is send to server.
    -> DB calls in Shell is Synchronous


    12. Update Operation in MongoDB
   
        Update Operation in MongoDB

    -> For updating a document we need to first find it.
    -> db.<Collection>.updateOne(findingObj, {$set: updateObj});

        Eg.
        db.expenses.updateOne({ title: "Grocery" }, {$set: { value: "20" }});

    -> db.<Collection>.replaceOne(findingObj, replaceObj);
        It will replace the whole object
    
    -> db.<Collection>.updateMany(findingObj, {$set: { value: 240 } });
        It will update all the available finded objects.


    13. Delete Operation in MongoDB

    Property:
        ->  We cannot delete/Update _id
        -> db.expenses.updateOne({ title: "Grocery" }, {$unset: { value: "" }});
            It will delete the value property from that document

    Document:
        -> db.expenses.deleteOne({ title: "Grocery" });
            It will find the document and delete it

    Collection:
        -> db.<collectionName>.drop()
            It will delete the collection

    Database:
        -> for deleting we should be in the database.
        -> db.dropDatabase()
            It will delete all the collections, document inside the DB.

    14. DataTypes in MongoDB
   
        # MongoDB Data Types Table

| **Data Type**       | **Description**                                         | **Example**                     |
|----------------------|---------------------------------------------------------|---------------------------------------|
| **ObjectId**         | A unique identifier for documents                      | `ObjectId()`                          |
| **Number (Int32)**     | Stores integer values                                  | `NumberInt(42)`                       |
| **Number (Int64) (Long)**    | Stores 64-bit integer values                           | `NumberLong("9223372036854775807")`   |
| **Double**           | Stores floating-point numbers                          | `NumberDouble(3.14)`                  |
| **Decimal128**       | Stores high-precision decimal values                   | `NumberDecimal("123.4567890123456789")` |
| **String**           | Stores text data                                       | `"Hello, World!"`                     |
| **Boolean**          | Stores true or false values                            | `true`, `false`                       |
| **Date**             | Stores date and time values                            | `new Date()`                          |
| **Array**            | Stores an array of values                              | `[1, 2, 3, "text"]`                   |
| **Embedded Document (Object)**| Stores nested documents                                | `{ "key": "value" }`                  |
| **Null**             | Represents a null value                                | `null`                                |
| **Binary Data**      | Stores binary data, such as images or files            | `BinData(0, "data")`                  |
| **Regular Expression** | Stores regex patterns                                | `/pattern/i`                          |
| **Code**       | Stores JavaScript code                                 | `Code("function() { return 42; }")`   |
| **Code (Scoped)** | Stores JavaScript code with a scope                 | `Code("function() { return x; }", {x: 42})` |
| **Min Key**          | Represents the smallest possible value in BSON         | `MinKey()`                            |
| **Max Key**          | Represents the largest possible value in BSON          | `MaxKey()`                            |
| **Timestamp**        | Stores timestamp values                                | `Timestamp()`                         |



15.MongoDB ObjectId DataType

ObjectId DataTye

    -> ObjectId is 12 bytes = 24-character hex string.
    -> Structure: 4-byte timestamp, 5-byte machine info, 3-byte counter.
    -> Ensures global uniqueness.
    -> You can override _id, but if not provided, MongoDB generates it automatically.


16. Understanding Number DataTypes in MongoDB

MongoDB Number Data Types

    Int32 (Standard Number)

        -> Used for regular integers.
        -> Suitable for most everyday use cases.
        -> Range is from -2,147,483,648 to 2,147,483,647.

    Int64 – NumberLong()

        -> Used for very large integers that exceed the Int32 range.
        -> Required when numbers go beyond JavaScript's safe integer limit.

    Decimal128 – NumberDecimal()

        -> Used for high-precision decimal values.
        -> Ideal for financial or scientific data where rounding errors must be avoided.


  17.MongoDB DataTypes in Practice

Other Data Types

String
    -> Most commonly used data type.
    -> Stores text values like "name": "Sahil".

Boolean
    -> Stores true or false.
    -> Useful for flags or conditions like "isActive": true.

Date
    -> Stores date and time in ISODate format.
    -> Example: ISODate("2025-05-26T00:00:00Z").

Array
    -> Stores a list of values.
    -> Example: "tags": ["nodejs", "mongodb"].

Object (Embedded Document)
    -> Stores nested documents inside a field.
    -> Example: "address": { "city": "Mumbai", "zip": 400001 }.

null
    -> Stores a null value, like "middleName": null.

Regular Expression (regex)
    -> Stores a regular expression pattern for matching strings.
    -> Example: { name: { $regex: /^S/ } }.

MinKey
    -> A special value that is always less than any other value in MongoDB.
    -> Used mainly for internal operations like range queries.

MaxKey
    -> Opposite of MinKey. Always greater than any other value.
    -> Also used in range operations and comparisons.

   18. BSON Types in MongoDB
# BSON Types

| **Type**             | **Alias**         | **Numeric Code** |
|-----------------------|-------------------|------------------|
| Double               | `double`         | 1                |
| String               | `string`         | 2                |
| Object               | `object`         | 3                |
| Array                | `array`          | 4                |
| Binary Data          | `binData`        | 5                |
| Undefined (deprecated) | `undefined`     | 6                |
| ObjectId             | `objectId`       | 7                |
| Boolean              | `bool`           | 8                |
| Date                 | `date`           | 9                |
| Null                 | `null`           | 10               |
| Regular Expression   | `regex`          | 11               |
| JavaScript           | `javascript`     | 13               |
| Symbol (deprecated)  | `symbol`         | 14               |
| JavaScript (with scope) | `javascriptWithScope` | 15      |
| 32-bit Integer       | `int`            | 16               |
| Timestamp            | `timestamp`      | 17               |
| 64-bit Integer       | `long`           | 18               |
| Decimal128           | `decimal`        | 19               |
| Min Key              | `minKey`         | -1               |
| Max Key              | `maxKey`         | 127              |


19. Where is the Data Stored in MongoDB?

    MongoDB Data Storage Summary

    Default data folder on Windows: C:\data\db
    (Data is stored here in binary format.)

    Custom data path:
        -> You can specify your own storage location when starting MongoDB with:
            mongod --dbpath <your_custom_path>

    Important:
        -> The specified folder must exist before running the command.


20. Configuring MongoDB Server with mongod.cfg File

    MongoDB Config File 

    -> It’s a text file where you tell MongoDB how to run.

    -> You can set things like:
        -> Where to save your data (dbPath).
        -> Where to save logs.
        -> What network address and port to use.

    Example to set data folder:
        storage:
        dbPath: C:\my_mongo_data

    -> To start MongoDB using this file, run:
        mongod --config path\to\mongod.config

21.Accessing Our MongoDB Server Over the Internet

 mongod.conf

# for documentation of all options, see:
#   http://docs.mongodb.org/manual/reference/configuration-options/

# Where and how to store data.
storage:
  dbPath: C:\Users\anura\OneDrive\Desktop\myDB

# where to write logging data.
# systemLog:
#   destination: file
#   logAppend: true
#   path:  C:\Program Files\MongoDB\Server\8.0\log\mongod.log

# network interfaces
net:
  port: 27017
  bindIp: 0.0.0.0,[::]
  ipv6: true


#processManagement:

#security:

#operationProfiling:

#replication:

#sharding:

## Enterprise-Only Options:

#auditLog:


22.Running MongoShell Scripts in JS Files

Run JavaScript files using the Mongo shell:
        mongosh your_script.js

    -> Inside the JS file, write only valid JavaScript code using MongoDB API methods.

    -> Use db.getCollection("name") to access collections, especially if the collection name has special characters or spaces.


  23.What is MongoDB Playground?

  MongoDB Playground is an interactive environment (mainly in VS Code) that lets you:
    -> Write and run MongoDB queries using JavaScript-like syntax.
    -> Test database scripts like insert, find, update, etc.
    -> Connect to real databases (local or remote).
    -> Preview results inline in the editor.


    


  24. MongoDB in Node.js

      MongoDB provides drivers for every popular backend language to work with it.
-> We also have Driver for NodeJS
-> Installation: npm i mongodb

-> Import and Connect
    import { MongoClient } from "mongodb";
    const client = new MongoClient("mongodb://127.0.0.1:27017/");
    await client.connect(); // Connect to MongoDB server

-> Database Access
    const db = client.db();               // Default 'test' DB
    const db = client.db("DataBaseName"); // Use a specific DB

-> View Collections
    console.log(await db.listCollections().toArray());
    // Lists all collections in the selected DB

-> Access Documents in a Collection
    const collection = db.collection("fruits");
    console.log(await collection.find().toArray());
    // Fetches all documents in the 'fruits' collection

-> List All Databases
    const admin = client.db().admin();
    console.log(await admin.listDatabases());
    // Lists all databases on the server

25.MongoDB CRUD Operation in Node.js


 Setup
    const db = client.db("DataBaseName");
    const collection = db.collection("users");

-> Read
    const users = await collection.find().toArray();

-> Create
    await collection.insertOne({ name: "XYZ", email: "x@g.com", age: 34 });

-> Update
    await collection.updateOne(
    { _id: new ObjectId("...") },
    { $set: { age: 35 } }
    );

-> Delete
    await collection.deleteOne({ _id: new ObjectId("...") });
    await collection.drop();         // Drop collection
    await db.dropDatabase();         // Drop DB
    

27.Understanding Cursors in MongoDB.

What is a Cursor?
    -> A Cursor is a JS object returned by .find().
    -> It stores query metadata and doesn't hit DB until a method like .toArray() or .next() is called.

Cursor as an Async Iterator
    -> const cursor = collection.find(); // returns a cursor
    -> cursor[Symbol.asyncIterator];     // true ⇒ it's iterable

    -> You can use:
        for await (const doc of cursor) {
        console.log(doc);
        }

Cursor Methods(few)

    -> await cursor.next();     // Returns next document or null
    -> await cursor.hasNext();  // Returns true/false

    
28. Cursor Methods in MongoDB

Cursor Chaining
-> Methods like .limit(), .skip(), .sort() return the cursor itself (not a promise).
-> You can chain them before executing with .toArray() or iterating.
-> Common Methods
    collection.find()
    .limit(5)                 // Limit result to 5 docs
    .skip(2)                  // Skip first 2 docs
    .sort({ name: 1, age: -1 }) // Sort by name ↑, then age ↓
-> No DB call is made until you use .toArray(), .next(), or a loop.


The Setup (const cursor = find()):
You create a cursor object. This is just a set of instructions. No request has been sent.
The cursor object has an empty internal cache (currentBatch: []), no cursorId, and methods like next().

The Trigger: The First Request
The First Request (First next(), Start of for-await, or toArray()):

The moment you call a method that needs data (await cursor.next(), start a for await (const doc of cursor) loop, or await cursor.toArray()), the process begins.

The cursor sends the initial query to the server for the first time.
The server executes the query and sends back the first batch of documents (e.g., 100 docs) along with a unique Cursor ID.
The cursor object stores this first batch in its internal currentBatch array and saves the cursorId.

How Each Method Consumes the Data
A. Using await cursor.next():

First Call to await cursor.next():

The method pops the first document off the currentBatch array and returns it to you.

The internal state now holds 99 documents.

Calls #2 to #100 to await cursor.next():

The method has documents in its local currentBatch. It simply pops the next one off and returns it immediately. This requires NO trip to the server.

Call #101 to await cursor.next():

The method finds the currentBatch empty.

It uses the stored cursorId to send a getMore command to the server.

The server sends the next batch.

The cursor stores this new batch and returns the first document from it.

This process repeats until the server sends an empty batch.

B. Using for await (const doc of cursor):

The Loop is a Wrapper for next():

Starting the loop implicitly makes the first call to await cursor.next(), triggering the initial query and populating the first batch (Step 2 above).

Each iteration of the loop automatically calls await cursor.next() for you.

The variable doc is set to the result of that next() call.

Iterations #2 to #100:

Each loop iteration pops a document from the local currentBatch. No server trips.

Iteration #101:

The loop's automatic call to next() triggers a getMore command to fetch the next batch.

The loop continues with the new batch.

The loop ends when next() has no more data to return.

C. Using await cursor.toArray():

The Method Takes Over:

The method triggers the initial query (Step 2 above).

It does not return. Instead, it enters a hidden, aggressive loop.

The Internal Loop:

It continuously pops all documents from the currentBatch and pushes them into a new, growing array.

When the currentBatch is empty, it automatically sends a getMore command using the cursorId to fetch the next batch.

It immediately empties that new batch into the array.

The Return:

It repeats this process—emptying batches, sending getMore commands—until the server has no more data.
Only then does the method return the complete, massive array containing every single document.

The Finale
Completion:

For all methods, the process ends when the server sends back an empty batch, signaling there is no more data. The cursor is then closed.


29. Batch Size in MongoDB

    What is Batch Size?
-> MongoDB returns documents in batches, not all at once.
-> Batch size controls how many docs are returned per network request.

Set Batch Size
-> const cursor = collection.find().batchSize(10);
-> This sets the batch size to 10 documents.
-> MongoDB will send results in chunks of 10 until all are returned.

Notes > Improves memory usage and performance for large datasets.


30.Projection in MongoDB

What is Projection?
-> Projection controls which fields are returned in the query result.

Include Fields
-> // Include only "name" and "email"
-> const users = await collection.find({}, { projection: { name: 1, email: 1 } }).toArray();

Exclude Fields
-> // Exclude "age"
-> const users = await collection.find({}, { projection: { age: 0 } }).toArray();

Note
-> 1 = include, 0 = exclude
-> You can't mix include and exclude (except for _id).


31.Limits of MongoDB
# MongoDB Limits and Thresholds

## 1. Document Size Limits
- **Maximum Document Size**: 16MB (BSON format)
  - Affects: Single document storage, embedded arrays/objects
  - Exception: GridFS for larger files

- **Maximum Array Elements**: ~4,000,000 (practical limit)
- **Maximum Nesting Depth**: 100 levels

## 2. BSON Data Types
- **String**: 16MB maximum
- **Binary Data**: 16MB (use GridFS for larger)
- **Number Precision**: 
  - 64-bit for integers (Long)
  - 64-bit IEEE 754 for doubles

## 3. Indexing Limits
| Limit Type                     | Value               |
|--------------------------------|---------------------|
| Indexes per Collection         | 64                  |
| Index Key Length               | 1024 bytes          |
| Compound Index Fields          | 32 fields           |
| Text Index Fields per Document | 1                   |
| Sharded Cluster Index Key Size | 512 bytes           |

## 4. Sharding Limits
- **Shard Key**: 
  - Immutable after creation
  - Maximum size: 512 bytes
- **Maximum Shards**: 1024
- **Chunk Size**: 1MB-1024MB (default 64MB)

## 5. Replication Limits
- **Replica Set Members**: 
  - Maximum 50 members
  - Maximum 7 voting members
- **Oplog Size**: 
  - Minimum 990MB (default for 64-bit systems: 5% disk space)

## 6. Query Limitations
| Operation                  | Limit                |
|----------------------------|----------------------|
| Result Set Size            | 32MB per query       |
| Sort Memory                | 32MB (without index) |
| Aggregation Pipeline Stages| 100 stages           |
| Aggregation Memory         | 100MB per stage      |

## 7. Connection Limits
| Deployment Type       | Default Connection Limit |
|-----------------------|---------------------------|
| MongoDB Atlas         | 500 connections/server    |
| Self-Managed Community| 16,000 connections        |
| Self-Managed Enterprise| 125,000 connections       |

## 8. Write Operations
- **Atomicity**: Single document level
- **Write Throughput**: ~100,000 ops/sec per shard
- **Bulk Write Batch Size**: 100,000 operations

## 9. Database/Collection Limits
| Entity           | Limit                         |
|------------------|-------------------------------|
| Databases        | 40 (Atlas limit per project)  |
| Collections      | 1000 per database (namespace) |
| Namespace Length | 123 bytes (db.collection)     |

## 10. Security Limits
- **Authentication**:
  - 16MB user name limit (LDAP)
  - 250 roles per user
- **X.509 Certificates**:
  - 25 attributes per certificate

## 11. MongoDB Atlas Specific
- **Document Storage**: 512MB per document
- **Free Tier**: 
  - 512MB storage
  - Shared RAM
- **Backups**: 2 days retention (free tier)

## Important Notes
1. Most limits are configurable (except fundamental BSON/document limits)
2. Workarounds exist for many limits (e.g., GridFS for large files)
3. Monitor with `db.serverStatus()` and `currentOp`



33.Using $in Operator for Bulk Operation in MongoDB

The $in operator in MongoDB checks if a field’s value exists in a specified array.
-> Syntax:
    { field: { $in: [value1, value2, ...] } }

-> Example:
    db.users.find({ age: { $in: [18, 25, 30] } });
    Matches users whose age is 18, 25, or 30.

-> Use case: Efficiently fetch multiple values in one query.

34. Why ObjectId is Not a String?

 Why ObjectId is not a String in MongoDB?

-> ObjectId is a special type in MongoDB that takes only 12 bytes, while a string version would take 24 bytes.
-> It is more efficient because it uses half the space of a string.
-> In hex, 2 characters = 1 byte.
-> An ObjectId is made up of:
    -> Timestamp
    -> Machine ID & Process ID
    -> Counter
-> MongoDB uses the binary (12-byte) form, not the full string, when inserting or querying.

35. Understanding Application Architecture

Application Architecture (Tiers)

    Tier-1 (Single-Tier)
        -> Runs on one machine, no network.
        -> Eg: Calculator, Notepad

    Tier-2 (Client-Server)
        -> Client: UI
        -> Server: Logic + Database
        -> Eg: MySQL Client, Online banking software

    Tier-3
        -> Frontend: UI
        -> Backend: Logic
        -> Database: Storage
        -> Eg: E-commerce sites, Social media apps

    Tier-N (Multi-Tier)
        -> 3-Tier + Services like CDN, AWS, Auth, Cache
        -> Eg: Netflix, YouTube, Large SaaS apps

  36. Ordered Inserts in MongoDB
Ordered Inserts

    -> Documents are inserted in order.
    -> If any insert fails, remaining inserts are stopped, and an error is thrown.
    -> To continue inserting remaining valid documents, use:
        { ordered: false }

37.What is Upsert in MongoDB?

Upsert

    -> If the document exists → it gets updated.
    -> If the document doesn’t exist → it gets inserted.
    -> Use the upsert: true flag.
    -> db.collection.updateOne(filter, update, { upsert: true });

   38. Running Commands in MongoDB

# MongoDB Commands Categorized

## 1. **Database Commands**

### 📌 General Database Operations

- **List Databases**
  ```js
  db.runCommand({ listDatabases: 1 });
  ```
- **List Available Commands**
  ```js
  db.runCommand({ listCommands: 1 });
  ```
- **Get Database Stats**
  ```js
  db.runCommand({ dbStats: 1 });
  ```
- **Drop Database**
  ```js
  db.runCommand({ dropDatabase: 1 });
  ```

---

## 2. **Collection Commands**

### 📌 Collection Management

- **Create Collection**
  ```js
  db.runCommand({ create: "myCollection" });
  ```
- **Drop Collection**
  ```js
  db.runCommand({ drop: "myCollection" });
  ```
- **List Collections**
  ```js
  db.runCommand({ listCollections: 1 });
  ```
- **Rename Collection**
  ```js
  db.runCommand({ renameCollection: "oldName", to: "newName" });
  ```
- **Validate Collection**
  ```js
  db.runCommand({ validate: "myCollection" });
  ```

---

## 3. **CRUD (Create, Read, Update, Delete) Commands**

### 📌 Insert Documents

- **Insert One or Multiple Documents**
  ```js
  db.runCommand({
    insert: "myCollection",
    documents: [
      { name: "Alice", age: 30 },
      { name: "Bob", age: 22 },
    ],
  });
  ```

### 📌 Read Documents

- **Find Documents**
  ```js
  db.runCommand({
    find: "myCollection",
    filter: { age: { $gt: 18 } },
    projection: { _id: 0, name: 1, age: 1 },
    limit: 5,
  });
  ```

### 📌 Update Documents

- **Update One or Multiple Documents**
  ```js
  db.runCommand({
    update: "myCollection",
    updates: [{ q: { name: "Alice" }, u: { $set: { age: 35 } }, upsert: true }],
  });
  ```

### 📌 Delete Documents

- **Delete One or Multiple Documents**
  ```js
  db.runCommand({
    delete: "myCollection",
    deletes: [{ q: { age: { $lt: 25 } }, limit: 0 }],
  });
  ```

---

## 4. **Index Commands**

### 📌 Index Management

- **Create Index**
  ```js
  db.runCommand({
    createIndexes: "myCollection",
    indexes: [{ key: { name: 1 }, name: "name_index" }],
  });
  ```
- **List Indexes**
  ```js
  db.runCommand({ listIndexes: "myCollection" });
  ```
- **Drop Index**
  ```js
  db.runCommand({ dropIndexes: "myCollection", index: "name_index" });
  ```

---

## 5. **Replication Commands**

### 📌 Replica Set Status & Configuration

- **Get Replica Set Status**
  ```js
  db.runCommand({ replSetGetStatus: 1 });
  ```
- **Get Replica Set Configuration**
  ```js
  db.runCommand({ replSetGetConfig: 1 });
  ```
- **Step Down Primary Node**
  ```js
  db.runCommand({ replSetStepDown: 60 });
  ```

---

## 6. **Sharding Commands**

### 📌 Shard Management

- **Enable Sharding for a Database**
  ```js
  db.runCommand({ enableSharding: "myDatabase" });
  ```
- **Shard a Collection**
  ```js
  db.runCommand({
    shardCollection: "myDatabase.myCollection",
    key: { _id: 1 },
  });
  ```
- **Get Shard Status**
  ```js
  db.runCommand({ getShardMap: 1 });
  ```

---

## 7. **Server & Performance Monitoring Commands**

### 📌 Server Status & Diagnostics

- **Get Server Status**
  ```js
  db.runCommand({ serverStatus: 1 });
  ```
- **Get Host Information**
  ```js
  db.runCommand({ hostInfo: 1 });
  ```
- **Get Running Operations**
  ```js
  db.runCommand({ currentOp: 1 });
  ```
- **Kill Running Operation**
  ```js
  db.runCommand({ killOp: 1, op: <opid> });
  ```
- **Rotate Logs**
  ```js
  db.runCommand({ logRotate: 1 });
  ```

---

## 8. **Security & Access Control Commands**

### 📌 User & Role Management

- **Create User**
  ```js
  db.runCommand({
    createUser: "admin",
    pwd: "securepassword",
    roles: ["readWrite", "dbAdmin"],
  });
  ```
- **Drop User**
  ```js
  db.runCommand({ dropUser: "admin" });
  ```
- **List Users**
  ```js
  db.runCommand({ usersInfo: 1 });
  ```
- **Grant a Role to a User**
  ```js
  db.runCommand({ grantRolesToUser: "admin", roles: ["read"] });
  ```

---

## 9. **Logging & Debugging Commands**

### 📌 Logs & Configuration

- **Get Log Data**
  ```js
  db.runCommand({ getLog: "global" });
  ```
- **List Available Logs**
  ```js
  db.runCommand({ getLog: "startupWarnings" });
  ```
- **Get Server Parameters**
  ```js
  db.runCommand({ getParameter: "*" });
  ```

---

## 🎯 **Final Notes**

- The `db.runCommand()` method in **Mongo shell** and `db.command()` in **Node.js driver** work the same way.
- Some commands are **administrative** and require proper permissions.
- **For CRUD operations**, the standard `insertOne()`, `find()`, `updateOne()`, `deleteOne()` methods are more convenient.

This document categorizes all the essential MongoDB commands for managing databases, collections, and server operations.


39.Operators in MongoDB

# MongoDB Query and Projection Operators

This document covers the most commonly used **Query and Projection Operators** in MongoDB with **Node.js examples**.

---

## 📌 1. Query Operators

Query operators are used to filter documents based on specific conditions.

### 🔹 `$eq` (Equal)

Finds documents where a field is equal to a specified value.

```js
const result = await db
  .collection("users")
  .find({ age: { $eq: 25 } })
  .toArray();
console.log(result);
```

### 🔹 `$ne` (Not Equal)

Finds documents where a field is **not** equal to a specified value.

```js
const result = await db
  .collection("users")
  .find({ status: { $ne: "inactive" } })
  .toArray();
console.log(result);
```

### 🔹 `$gt`, `$gte`, `$lt`, `$lte` (Greater Than, Less Than)

```js
const result = await db
  .collection("users")
  .find({ age: { $gt: 18 } })
  .toArray();
console.log(result);
```

### 🔹 `$in`, `$nin` (Match any of the specified values / Not in)

```js
const result = await db
  .collection("users")
  .find({ country: { $in: ["India", "USA"] } })
  .toArray();
console.log(result);
```

### 🔹 `$exists` (Check if a field exists)

```js
const result = await db
  .collection("users")
  .find({ phone: { $exists: true } })
  .toArray();
console.log(result);
```

### 🔹 `$regex` (Pattern Matching)

```js
const result = await db
  .collection("users")
  .find({ name: { $regex: /^A/i } })
  .toArray();
console.log(result);
```

### 🔹 `$or`, `$and`, `$not`, `$nor` (Logical Operators)

```js
const result = await db
  .collection("users")
  .find({
    $or: [{ age: { $gt: 30 } }, { status: "active" }],
  })
  .toArray();
console.log(result);
```

---

## 📌 2. Projection Operators

Projection operators control which fields are returned in the result.

### 🔹 Inclusion (`1`) and Exclusion (`0`)

```js
const result = await db
  .collection("users")
  .find({}, { projection: { name: 1, age: 1, _id: 0 } })
  .toArray();
console.log(result);
```

### 🔹 `$elemMatch` (Match elements in an array)

```js
const result = await db
  .collection("users")
  .find({
    hobbies: { $elemMatch: { type: "sports" } },
  })
  .toArray();
console.log(result);
```

### 🔹 `$slice` (Limit array fields in results)

```js
const result = await db
  .collection("users")
  .find({}, { projection: { posts: { $slice: 2 } } })
  .toArray();
console.log(result);
```

---

## 📌 3. Array Query Operators

### 🔹 `$all` (Match all values in an array)

```js
const result = await db
  .collection("users")
  .find({ skills: { $all: ["MongoDB", "Node.js"] } })
  .toArray();
console.log(result);
```

### 🔹 `$size` (Find arrays with a specific number of elements)

```js
const result = await db
  .collection("users")
  .find({ skills: { $size: 3 } })
  .toArray();
console.log(result);
```

---

## 📌 4. Evaluation Operators

### 🔹 `$expr` (Compare two fields)

```js
const result = await db
  .collection("users")
  .find({
    $expr: { $gt: ["$credits", "$debits"] },
  })
  .toArray();
console.log(result);
```

### 🔹 `$mod` (Modulo operation)

```js
const result = await db
  .collection("users")
  .find({ age: { $mod: [2, 0] } })
  .toArray();
console.log(result);
```


# MongoDB Update Operators

This document categorizes and explains the most commonly used **Update Operators** in MongoDB with **Node.js examples**.

---

## 📌 1. Field Update Operators

### 🔹 `$set` (Update or Add a Field)
```js
const result = await db.collection("users").updateOne(
  { name: "John" },
  { $set: { age: 30 } }
);
console.log(result);
```

### 🔹 `$unset` (Remove a Field)
```js
const result = await db.collection("users").updateOne(
  { name: "John" },
  { $unset: { age: "" } }
);
console.log(result);
```

### 🔹 `$rename` (Rename a Field)
```js
const result = await db.collection("users").updateOne(
  { name: "John" },
  { $rename: { "oldField": "newField" } }
);
console.log(result);
```

---

## 📌 2. Arithmetic Operators

### 🔹 `$inc` (Increment a Numeric Field)
```js
const result = await db.collection("users").updateOne(
  { name: "John" },
  { $inc: { score: 5 } }
);
console.log(result);
```

### 🔹 `$mul` (Multiply a Numeric Field)
```js
const result = await db.collection("users").updateOne(
  { name: "John" },
  { $mul: { salary: 1.1 } }
);
console.log(result);
```

---

## 📌 3. Array Update Operators

### 🔹 `$push` (Add an Element to an Array)
```js
const result = await db.collection("users").updateOne(
  { name: "John" },
  { $push: { skills: "MongoDB" } }
);
console.log(result);
```

### 🔹 `$pop` (Remove First or Last Element from an Array)
```js
const result = await db.collection("users").updateOne(
  { name: "John" },
  { $pop: { skills: -1 } } // -1 removes first, 1 removes last
);
console.log(result);
```

### 🔹 `$pull` (Remove Specific Elements from an Array)
```js
const result = await db.collection("users").updateOne(
  { name: "John" },
  { $pull: { skills: "Java" } }
);
console.log(result);
```

### 🔹 `$addToSet` (Add an Element Only If It Does Not Exist)
```js
const result = await db.collection("users").updateOne(
  { name: "John" },
  { $addToSet: { skills: "JavaScript" } }
);
console.log(result);
```

---

## 📌 4. Upsert Operations

### 🔹 `upsert: true` (Insert if Not Found)
```js
const result = await db.collection("users").updateOne(
  { name: "Jane" },
  { $set: { age: 25 } },
  { upsert: true }
);
console.log(result);
```

---

## 📌 5. Date Operators

### 🔹 `$currentDate` (Set Field to Current Date)
```js
const result = await db.collection("users").updateOne(
  { name: "John" },
  { $currentDate: { lastLogin: true } }
);
console.log(result);
```

---

## 📌 6. Bitwise Operators

### 🔹 `$bit` (Bitwise Operations on Integer Fields)
```js
const result = await db.collection("users").updateOne(
  { name: "John" },
  { $bit: { permissions: { or: 5 } } }
);
console.log(result);
```

40.What is Schema?

Schema

    -> A schema defines the structure of data in a database.
    -> It sets field names, data types, and rules (like required fields).
    -> MongoDB is schema-less, but using schemas (e.g., with Mongoose) ensures data consistency and validation.
    -> Useful for catching errors, maintaining uniformity, and writing reliable queries.


42. Understanding jsonSchema Validation
Defines strict structure, data types, and rules for documents.
-> Supports nested validation.
-> additionalProperties: false blocks extra unwanted fields.

-> Example with Nested Fields:

db.createCollection("users", {
validator: {
    $jsonSchema: {
    bsonType: "object",
    required: ["name", "age", "address"],
    additionalProperties: false,
    properties: {
        name: { bsonType: "string" },
        age: { bsonType: "int", minimum: 18 },
        address: {
        bsonType: "object",
        required: ["city", "zip"],
        additionalProperties: false,
        properties: {
            city: { bsonType: "string" },
            zip: { bsonType: "int" }
        }
        }
    }
    }
}
});


43.Validation Action VS Validation Level
These two control how MongoDB handles documents that fail validation.

1) Validation Action
-> What happens when a document fails validation?
    -> error (default): Reject the insert or update.
    -> warn: Allow the operation but log a warning.
-> validationAction: "error" // or "warn"

2) Validation Level
-> Which documents are checked during validation?
    -> strict (default): Validate all inserts and updates.
    -> moderate: Validate only documents that already have the validated fields.
    -> off (MongoDB 7.0+): Disable validation.
-> validationLevel: "strict" // or "moderate"

44.Finding Invalid Documents in a Collection
For finding invalid document in collection

db.collection("users").find({
$nor: [{ $jsonSchema: { ...your schema... } }]
});

44. What Are Transactions in Database?
Transactions in Database

-> In MongoDB, transactions are a feature that allows you to group multiple read and write operations into a single atomic operation — meaning either all operations succeed, or none of them are applied. This is similar to transactions in relational databases (like MySQL or PostgreSQL).

-> Why Use Transactions in MongoDB?

MongoDB is a NoSQL database and was originally designed with single-document atomicity in mind. However, in some cases, you need multi-document or multi-collection atomic operations, such as:
    -> Transferring money between accounts.
    -> Updating multiple collections consistently.
    -> Undoing partial updates if something fails.
    -> For these use cases, MongoDB supports multi-document transactions starting from version 4.0 for replica sets and 4.2+ for sharded clusters.

-> Key Properties of Transactions:
    -> Atomicity: All changes in a transaction are either fully applied or not applied at all.
    -> Consistency: The database moves from one valid state to another.
    -> Isolation: Operations in a transaction are invisible to others until committed.
    -> Durability: Once committed, changes are permanent even if there's a crash.


 45.Implementing Transaction in Code

 Steps to enable transaction in MongoDB

    1. Edit the Config File (mongod.conf)

        -> Add the following under the replication section:
            replication:
                replSetName: rs0

    2. Restart the MongoDB service if installed as a service on Windows

    3. Initiate the Replica Set
        -> In the shell, run: rs.initiate()

    4. Verify Status: rs.status()

    5. Change the connection String: mongodb://localhost:27017/?replicaSet=rs0


   46.ACID Properties of a Transaction

   ACID = Atomicity, Consistency, Isolation, Durability

-> Atomicity:
All steps in a transaction happen, or none happen.
"All or nothing."

-> Consistency:
The database follows rules before and after the transaction.
"Data stays valid."

-> Isolation:
Transactions don’t interfere with each other.
"No mix-ups when multiple users act at once."

-> Durability:
Once a transaction is saved, it stays saved — even after a crash.
"It's permanent."

Sharding:
Sharding distributes data across multiple servers, allowing you to manage and query very large datasets more efficiently. Each shard holds a subset of the overall data, which helps improve performance by balancing the load.

Replication:
Replication involves creating multiple copies of the same data across different servers. This ensures high availability and fault tolerance. If one server is busy or fails, another server with a replica can handle the request, which reduces latency and ensures continuity. right?


47.Relational vs. Non-Relational Databases: Key Differences

Relational Vs Non-Relational DBs

1. Structure
    -> Relational:
        Stores data in tables (like Excel sheets – rows and columns).
    -> Non-Relational:
        Stores data in flexible formats like JSON, key-value pairs, or graphs.

2. Schema
    -> Relational:
        Fixed structure – you must define the format before adding data.
    -> Non-Relational:
        No fixed structure – you can store different types of data freely.

3. Scalability
    -> Relational:
        Grows by getting a bigger machine (vertical scaling).
    -> Non-Relational:
        Grows by adding more machines (horizontal scaling), easier for big systems.

4. ACID
    -> Relational:
        Follows strict rules to keep data accurate and safe (ACID).
    -> Non-Relational:
        May skip some rules for better speed and flexibility.

5. Query Language
    -> Relational:
        Uses SQL – a standard language to ask and manage data.
    -> Non-Relational:
        Uses different methods depending on the type (not always SQL).

6. Examples
    -> Relational:
        MySQL, PostgreSQL, Oracle
    -> Non-Relational:
        MongoDB (document), Redis (key-value), Cassandra (wide-column), Neo4j (graph).

   49.Embedded vs. Referenced Documents: Choosing the Right Data Model
Embedded Documents
    -> Meaning: Related data is stored inside the same document.
    -> Example:
        {
        "name": "John",
        "address": { "city": "Mumbai", "zip": "400001" }
        }
    -> Good for: Data used together
    -> Pros: Fast reads
    -> Cons: Can get large, harder to update

Referenced Documents
    -> Meaning: Related data is stored in a separate document and linked by ID.
    -> Example:
        {
        "name": "John",
        "address_id": "abc123"
        }
    -> Good for: Shared or large data
    -> Pros: Cleaner, flexible
    -> Cons: Requires extra query to fetch related data

# Embedded vs. Referenced Documents

## Introduction
In NoSQL databases, particularly in document-based databases like MongoDB, data relationships can be handled using **embedded** or **referenced** documents. The choice between these approaches affects performance, scalability, and ease of querying.

## 1. Embedded Documents
Embedded documents store related data within the same document.

### Pros:
- **Faster Reads**: Data retrieval is quicker since related data is stored together.
- **Fewer Joins**: No need for complex queries or additional lookups.
- **Atomic Updates**: Easier to update related data in a single operation.

### Cons:
- **Data Duplication**: Can lead to redundancy if the same sub-document is used in multiple documents.
- **Limited Scalability**: Large nested documents can impact performance and exceed document size limits.

### Example:
```json
{
  "_id": 1,
  "name": "John Doe",
  "orders": [
    { "order_id": 101, "amount": 50 },
    { "order_id": 102, "amount": 75 }
  ]
}
```

## 2. Referenced Documents
Referenced documents store relationships using document references (IDs).

### Pros:
- **Better Scalability**: Useful for large datasets where embedding would exceed size constraints.
- **Efficient Updates**: Changes to referenced documents don’t require updating multiple documents.
- **Normalization**: Reduces redundancy and improves maintainability.

### Cons:
- **Slower Reads**: Requires additional lookups to retrieve related data.
- **Increased Query Complexity**: Queries involve joins or multiple fetch operations.

### Example:
```json
{
  "_id": 1,
  "name": "John Doe",
  "orders": [101, 102]
}

{
  "_id": 101,
  "order_id": 101,
  "amount": 50
}

{
  "_id": 102,
  "order_id": 102,
  "amount": 75
}
```

## 3. When to Use Each Approach
| Use Case | Embedded Documents | Referenced Documents |
|----------|--------------------|---------------------|
| Data is frequently read together | ✅ | ❌ |
| Data relationships are complex and scalable | ❌ | ✅ |
| Updates are frequent across multiple documents | ❌ | ✅ |
| Document size constraints are not a concern | ✅ | ❌ |

## Conclusion
Choosing between embedded and referenced documents depends on the application’s needs. Use **embedded documents** when data is closely related and frequently accessed together. Use **referenced documents** when scalability, normalization, and flexibility are priorities.

50.Understanding One-to-One, One-to-Many, and Many-to-Many Relationships

1. One-to-One
    Meaning: One document is related to only one other document.
    Example: A User has one Profile.

2. One-to-Many
    Meaning: One document relates to many documents.
    Example: A Blog Post has many Comments.

3. Many-to-Many
    Meaning: Many documents relate to many others.
    Example: Students enrolled in many Courses, and Courses have many Students.


51. Backup & Restore Using mongodump and mongorestore

mongodump (Backup)
    -> Creates a backup of MongoDB data in BSON format.
    -> Can dump entire DB, specific DB, or collections.
    -> Supports options like compression (--gzip), authentication, and dumping to archive files.
    -> Example:
        mongodump --db mydatabase --out /backup/mongo/

mongorestore (Restore)
    -> Restores data from BSON backups created by mongodump.
    -> Can restore entire dump, specific DB, or collections.
    -> Supports options like dropping existing data before restore (--drop), authentication, and reading from archives or compressed files.
    -> Example:
        mongorestore --db mydatabase /backup/mongo/mydatabase/

52.Using mongoexport and mongoimport to Export and Import JSON or CSV Data

mongoexport (Export Data)
    -> Exports data from MongoDB to JSON or CSV files.
    -> Useful for sharing or backing up in readable formats.
    -> Common Options:
        --db, --collection, --out, --type, --fields, --query, --jsonArray
    -> Example:
        mongoexport --db mydatabase --collection users --out users.json

mongoimport (Import Data)
    -> Imports data into MongoDB from JSON or CSV files.
    -> Used to restore, migrate, or populate data.
    -> Common Options:
        --db, --collection, --file, --type, --fields, --jsonArray, --drop
    -> Example:
        mongoimport --db mydatabase --collection users --file users.json

  53. mongodump VS mongoexport: When to Use What?

  54. mongodump / mongorestore (Binary Backup & Restore)
    Use when:
        -> You need a full backup or restore of a database/collection
        -> You want to preserve MongoDB-specific types (e.g. ObjectId, Date).
        -> You’re migrating between MongoDB servers.
        -> You need fast, efficient backup (BSON format).

    Avoid when:
        -> You need human-readable or filtered data.

mongoexport / mongoimport (Structured Data Transfer)
    Use when:
        -> You want to export/import JSON or CSV.
        -> You need to filter or share specific fields or documents.
        -> You're migrating to another database system (e.g. PostgreSQL).

    Avoid when:
        -> You want a complete backup with indexes and metadata.

  55.Securing MongoDB: Authentication and Authorization
  We can change password of a user:

db.changeUserPassword("username", "newPassword")

Roles that can change any user's password:
root - All users (cluster-wide)
userAdminAnyDatabase - All users (cluster-wide)
userAdmin - Users of that DB only
dbOwner - Users of that DB only



We should not create all the users inside the admin database we should create the user in the database in which that user belongs. This is considered as a good practice.
And you don't need to remember all the users you can get all users along with their database info by running this `db.system.users.find()` query inside the admin database.

56.Enabling Auth in MongoDB Replica Set
# Enabling Authentication in MongoDB Replica Set

## 1. **Generating the KeyFile**

To enable authentication in a MongoDB replica set, you need to create a keyFile for internal authentication between the nodes.

### **Step 1: Generate a KeyFile**

Run the following command to generate a secure key file:

```sh
openssl rand -base64 756 > /path/to/mongo-keyfile
```

### **Step 2: Set Correct Permissions (Only for Unix Systems)**

Ensure that the key file has the correct permissions:

```sh
chmod 400 mongo-keyfile
```

## 2. **Configuring MongoDB to Use the KeyFile**

Add the following lines under the `security` section in the MongoDB configuration file (`mongod.conf`):

```yaml
security:
  authorization: enabled
  keyFile: /path/to/mongo-keyfile
```

## 3. **Restart MongoDB Nodes with Authentication**

Once the keyFile is set up, restart all nodes in the replica set:


Now, authentication is enabled for the replica set, and nodes will communicate securely using the keyFile.

57.Exploring MongoDB Atlas

MongoDB Atlas – Key Points
What is it?
    -> Cloud-based, fully managed MongoDB service.
    -> Hosted by MongoDB Inc.
    -> Supports AWS, GCP, and Azure.

Features
    -> No server setup required – fully managed.
    -> Free tier available (M0 cluster)
    -> Built-in security: IP whitelisting, encryption, user roles.
    -> Global clusters for low-latency access.
    -> Auto-scaling & sharding support.
    -> Automated backups with restore options.
    -> Monitoring tools built-in (charts, metrics, alerts).
    -> Easy integrations with Node.js, Python, etc.

How to Use
    -> Sign up at: mongodb.com/cloud/atlas
    -> Create a cluster (select cloud provider and region).
    -> Add your IP address to access list.
    -> Create a database user with username & password.
    -> Connect using:
        -> MongoDB URI in your app
        -> Compass (GUI)
        -> Mongo Shell

58. Managed VS Self-Managed Databases
    # Managed vs. Self-Managed Databases

## Introduction
Choosing between a **managed** and **self-managed** database depends on factors like cost, scalability, maintenance, and control. Below, we compare the pros and cons of both approaches.

---

## **Managed Databases**
Managed databases are cloud-based services where the provider handles infrastructure, maintenance, security, and scaling.

### ✅ **Pros**
1. **Ease of Use**: No need to manage database servers, updates, or backups.
2. **Scalability**: Auto-scaling options make it easier to handle traffic spikes.
3. **Security**: Built-in security measures like encryption, role-based access control, and compliance.
4. **Automated Maintenance**: Handles patching, backups, and disaster recovery.
5. **High Availability**: Redundant systems ensure minimal downtime.
6. **Performance Optimization**: Providers offer monitoring tools for performance tuning.

### ❌ **Cons**
1. **Limited Control**: Cannot fine-tune infrastructure and configurations beyond provider limits.
2. **Cost**: Generally more expensive than self-managed solutions.
3. **Vendor Lock-in**: Moving to a different provider can be difficult and costly.
4. **Customization Restrictions**: Some features may be unavailable or require premium plans.

---

## **Self-Managed Databases**
Self-managed databases require you to install, configure, maintain, and secure your own database servers.

### ✅ **Pros**
1. **Full Control**: Complete access to database configuration, hardware, and optimizations.
2. **Customization**: Ability to tailor settings, performance tuning, and security policies.
3. **Cost Efficiency**: Can be cheaper if you have in-house expertise and infrastructure.
4. **No Vendor Lock-in**: Freedom to migrate and choose the best hosting environment.
5. **Better Performance and Security**: Since the database and server run on the same machine, database operations can be faster. Additionally, there is no need to expose the database to the internet, making it more secure.

### ❌ **Cons**
1. **High Maintenance**: Requires regular patching, backups, and performance tuning.
2. **Security Risks**: Responsibility for securing data, managing access controls, and handling compliance.
3. **Scalability Challenges**: Requires manual effort to add servers and optimize for high traffic.
4. **Downtime Risks**: Failover and disaster recovery must be planned and executed manually.
5. **Operational Complexity**: Requires in-depth knowledge of database management and infrastructure.

---

## **Conclusion**
- **Choose Managed Databases** if you want a hassle-free, scalable, and secure solution with minimal maintenance.
- **Choose Self-Managed Databases** if you need full control, custom configurations, and cost efficiency for large-scale or specialized applications.

The choice ultimately depends on your business needs, technical expertise, and budget.


My further study: 1) sudo means "superuser do" --> it means only access like admin. sudo grants elevated privileges to perform administrative tasks. 2) The name systemctl is a blend of "system" and "control," reflecting its role in controlling and managing systemd services, units, and system states. 3) cat --> it is short form of concatenate that means to join things and although  to display the content. 4) After cat /etc/mongod.conf  shows all contents of mongod.conf. It shows YAML format that means "YAML Ain't (is not) Markup Language" or "Yet Another Markup Language". YAML format defines human readable format. 5) nano --> it means editor that helps us to edit our mongodb configuration file. If we want to edit any file it have to use sudo because sudo means superuser do, only sudo can edit and save the mongodb configuration




                                                              Mastering Database Fundamentals
