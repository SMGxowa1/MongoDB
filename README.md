# SQL Notes 
## Introduction to MongoDB (week 6):
-Document database, robust, versatile and user friendly.
-For distributed systems facilitating vertical and horizontak database scaling.
-Relational DB => in rows and columns within tables; have relations e.g. data tables for teams and players 
-Relational data can be joined by rows(records);
-Non-relational DB => data stored in documents rather than tables; key-value pairs as objects.
-Includes a schema-less format, fast and scalable.

## Documents and Collections (week 6):
-Documents are field-value pairs in BSON (JSON format).
-Various data types can be used in these pairs(more flexible).
-Inserting a document involves assigning it to a variable specifying field-value pairs.
-After insertion the document's emphasizes the necessity of the id_field
-Find command = SELECT statement in SQL; Quering requires a query document (1st parameter) & an empty query document retrieving all documents.
-Mongo allows one to mix and match data types
-Collections allow related documents to be grouped for enhancment and performance.
-Mongo provides advanced collection feautures (capped collections) which limits max number of stored documents & automatically removing old docs.

## Querying in MongoDB (week 7):
-Limiting, sorting or skipping documents in MongoDB is a concept called Cursors (returned when querying)
-Chaining - query does not run immediately it waits until results are requested back.
-Find command without limits returns all documents. By adding the "limit" option, we can refine the results, such as obtaining only two or three recipes.
-Sorting is another crucial query option. Utilizing "Sort" with parameters like the field to sort by and the direction (1 for ascending, -1 for descending) allows us to arrange results accordingly.
-Skip option enables skipping a specified number of documents. By combining "Skip" with "Limit" and other options, we can create nuanced queries. 

-Operator fields (data types) are used for conditionally filterung results in queries.
-E,g, greater than sign => $gt
-Tags array allows one to tag the data we want displayed e.g. {tags: "full"} displaying persons paying full price.
-To navigate in MongoDB especially arrays and objects, we do that by dot notation.
-E.g. To find eggs in recipe we query by {"ingredients.name": "egg"}

-updateOne command = single-field update in a document using operators like set,unset and inc.
-update command = updates multiple documents similarly.
-Updating a document: $set(adding), $unset(removing) and $inc(increamenting)

-udating arrays requires the $push and $pull operator.
-adding = $push (appends to end of array)
-removing = $pull(removes data)

-delete methods require a filter document.
-deleteOne => first matching document in collection is deleted.
-deleteMany => removes all documents that match specified filter


## Data and Schema Modeling(week 7):
-Data is embedded within another in MongoDB, rather than dispersing to diff locations.
-Data should be close association if they link 
-As data complexity increases, no. of objects is limited due to RAM.
-Embedding data together reduces queries and simplifies operations.
-References => Data rarely accesed simultaneously can be stored seperately to optimize RAM.
-Gotchas => Optimize performance by storing only important info and the rest in a seperate collection.
-Indices => Facilitates a quick lookup of info. in the database without scanning entire data set.
-Collection Types:
-Capped collections, designed for scenarios such as log data where order is crucial, limit the stored data and automatically purge older documents upon reaching the specified cap. => capped set to TRUE
-Automatic deletion mechanism in capped collections ensures old data removed first.
-Possible to change a an existing collection to capped.
-Limitations => absence of default index and inability to be sharded.

## Development with MongoDB(week 7):
-GridFS => breaks down file contents into chunks(each in own document) while parent document holds info on the file.

## Server-side Administration with MongoDB(week 7):
-Config files are written in YAML, placed differently based on operating system and manually configured.
-Log files and database paths are directed to specific locations, enabling separation onto different physical disks. Other notable options include directory per database, maximum incoming connections, and process management settings like forking for background processes, often preferred in production environments.
-Security considerations involve enabling authorization for role-based authentication, and a cautionary note about enabling JavaScript due to potential security issues. Replication settings, such as specifying the default replica set name, are crucial.
-MongoDB recommends replica sets(running multiple identical copies of database concurrently).
-Primary node replicates data to secondaries, if primary unavailable,secondary database takes its role.
-rs.initiate() => logging into primary node.
-rs.status() or db.isMaster() => verify statues of replica set
-Sharding => distributing data across multiple servers, for performance and infastructure benefits. Allows scaling.
-MongoDb provides automatic sharding; sharding divides data among servers
-sharding introduces MongoS, acts as a router with table of contents, tracking data locations using a shard key and config servers.
-MongoS determines where data resides, retrieves it from the correct server, and merges it seamlessly, simplifying the process for the client.
-To automate sharding, enable it on the database, specify a collection, and choose a shard key.
-Authentication, akin to logging into an account, involves MongoDB usernames, passwords, or keys for access—a bit like having a badge for an office building. 
-Backups:
-Copying data files, a relatively straightforward yet manual approach. 
-Running 'mongodump' creates a dump folder with subfolders for each database containing collection files.