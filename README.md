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
-