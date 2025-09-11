##  JSON (JavaScript Object Notation)

## What it is: A text format (human-readable).

## Where it’s used: For sending and storing data, e.g., between a client (browser) and server.

Looks like:

{
  "name": "Bhaskar",
  "age": 22,
  "hobby": "Calisthenics"
}


This is just plain text. Easy for humans to read and write.

## 2. BSON (Binary JSON)

What it is: A binary format (machine-readable).

Where it’s used: Inside MongoDB to store documents efficiently.

Why: Faster for machines to process, supports more data types than JSON (like Date, ObjectId, Binary data).

## 3. How MongoDB Uses Them

When you insert data into MongoDB:

You usually write in JSON-like format in your code.

MongoDB converts it into BSON internally to store.

When you read data from MongoDB:

MongoDB sends it back as BSON, which the driver (like Node.js, Java, Python) converts back into JSON for you.

## 4. Example

👉 Suppose you insert this into MongoDB:

db.students.insertOne({
  name: "Bhaskar",
  age: 22,
  joined: new Date()
})


What you wrote looks like JSON.

What MongoDB stores internally is BSON, something like:

{
  "name": "Bhaskar",   // string
  "age": 22,           // integer
  "joined": ISODate("2025-09-09T12:00:00Z") // BSON date type
}


Notice: JSON has no special Date type — it would just be a string. But BSON supports Date, ObjectId, etc.

## 5. Key Differences
Feature	JSON (Text)	BSON (Binary)
Readable	Human-friendly	Machine-friendly
Storage	Bigger (text takes more space)	Smaller & faster to parse
Data Types	Limited (string, number, bool)	Rich (Date, ObjectId, binary)
Use in MongoDB	You write queries in JSON style	MongoDB stores it as BSON

👉 In short:
You talk to MongoDB in JSON-like syntax, MongoDB saves and works with it in BSON for speed and extra data types.