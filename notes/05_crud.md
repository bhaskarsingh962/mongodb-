## NOTE - use mongodb shell to execute the command from shell


## 1. Start MongoDB Shell

If you’re using MongoDB shell (mongosh), first open it by typing in terminal:

mongosh

## 🟢 2. Create / Switch Database

In MongoDB, databases are created when you insert something.

use myDatabase
👉 This switches you to a database named myDatabase.
👉 If it doesn’t exist, MongoDB will create it only after you add data.



## 🟢 3. Show All Databases
show dbs
 ⚠️ Important: If your new database is empty, it won’t appear here. It appears only after you insert something.




## 🟢 4. Show Current Database
db
👉 Tells you which database you are using right now.




## 🟢 5. Create a Collection and Insert Data
db.students.insertOne({ name: "Bhaskar", age: 22 })


students = collection (like a table in SQL).

## -> insertOne() = adds a single document.

👉 Now your myDatabase exists because it has data.




## 🟢 6. Show Collections in a Database
show collections
👉 Shows all collections (tables) inside the current database.



## 🟢 7. Insert Multiple Documents
db.students.insertMany([
  { name: "Amit", age: 21 },
  { name: "Priya", age: 23 }
])

1-inside double quote
2-if you are inserting with space add single/double quote that time for example
 'course name' : 'dbms'
3-there is $ sign for mongodb keyword 

## 🔹 1. Ordered Insertion (default)

MongoDB inserts documents one by one in order.

If an error happens (like a duplicate _id), it stops right there and does not insert the rest.

Safer, but slower.

✅ Example:

db.students.insertMany(
  [
    { _id: 1, name: "Bhaskar" },
    { _id: 2, name: "Amit" },
    { _id: 2, name: "Priya" }, // duplicate _id (error!)
    { _id: 3, name: "Rahul" }
  ],
  { ordered: true } // default
)


👉 What happens?

Inserts _id:1 and _id:2 (Amit).

Sees error at _id:2 (Priya) → stops.

_id:3 (Rahul) will NOT be inserted.

## 🔹 2. Unordered Insertion

MongoDB tries to insert all documents in parallel, ignoring order.

If an error happens, it skips that document but continues inserting the rest.

Faster, but order is not guaranteed.

✅ Example:

db.students.insertMany(
  [
    { _id: 1, name: "Bhaskar" },
    { _id: 2, name: "Amit" },
    { _id: 2, name: "Priya" }, // duplicate _id (error!)
    { _id: 3, name: "Rahul" }
  ],
  { ordered: false }
)


👉 What happens?

Inserts _id:1 and _id:2 (Amit).

_id:2 (Priya) → error, skipped.

But _id:3 (Rahul) still gets inserted because unordered doesn’t stop.




## 🟢 8. Read Data (Find Documents)
db.students.find()


👉 Shows all documents in the students collection.

Pretty print (formatted view):

db.students.find().pretty()
db.students.findOne({key : value});
db.students.findOne({'name': 'bhaskar'});



## 🟢 9. Update Documents
db.students.updateOne(
  { name: "Bhaskar" },   // filter
  { $set: { age: 23 } }  // update
)


👉 Updates Bhaskar’s age to 23.




## 🟢 10. Delete Documents
db.students.deleteOne({ name: "Amit" })
👉 Deletes the first document that matches.

Delete many:

db.students.deleteMany({ age: 21 })



## 🟢 11. Drop Collection / Database
db.students.drop()   // deletes collection
db.dropDatabase()    // deletes current database


✅ Flow Example
use school                // create/use "school" DB
db.students.insertOne({ name: "Bhaskar", age: 22 })  
show dbs                  // now "school" will appear
show collections          // shows "students"
db.students.find().pretty()  // see d



## how to import database

## 1. Using mongoimport (most common)

mongoimport is a command-line tool that comes with MongoDB.
You use it to import JSON, CSV, or TSV files into a MongoDB collection.

👉 Syntax:
mongoimport --db <databaseName> --collection <collectionName> --file <filename> --jsonArray


## jsonArray - array of document to normal if the data have array of document

✅ Example:
mongoimport --db school --collection students --file students.json --jsonArray


--db school → database name = school

--collection students → collection name = students

--file students.json → file you’re importing

--jsonArray → tells MongoDB the file contains an array of JSON documents

👉 If school DB or students collection doesn’t exist, MongoDB creates them automatically.

Import CSV Example:
mongoimport --db school --collection students --type csv --file students.csv --headerline


--type csv → file is CSV

--headerline → first row of CSV is column names

## 🔹 2. Import Using mongorestore

This is used when you already have a MongoDB backup (created with mongodump).
The backup is usually in BSON format.

👉 Syntax:
mongorestore --db <databaseName> <path_to_dump_folder>

✅ Example:
mongorestore --db school dump/school


--db school → restore into school DB

dump/school → folder created earlier by mongodump

## 🔹 3. Import from MongoDB Compass (GUI method)

MongoDB Compass (the GUI tool) also allows you to import:

Open Compass and connect to your MongoDB server.

Select the database and collection.

Click “Import Data”.

Choose your file (.json or .csv).

Click Import.

👉 Good for beginners who don’t want to use terminal commands.