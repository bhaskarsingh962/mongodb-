## mongoDB was made by company  10gen
2007 → Founded by Dwight Merriman & Eliot Horowitz (Company: 10gen).
2009 → MongoDB first released.
2013 → 10gen changed its name to MongoDB Inc..
2017 → MongoDB Inc. went public on the NASDAQ stock exchange.
Now → MongoDB is one of the most popular databases in the world (used by Google, Adobe, eBay, Uber, etc.).



## 📌 What is MongoDB?

MongoDB is a NoSQL database (not a traditional SQL database like MySQL).
It stores data in a document format (similar to JSON), instead of rows and columns.
Each record is called a document and is stored in a collection (instead of a table).

## 👉 Example of a MongoDB document:
{
  "name": "Bhaskar",
  "age": 23,
  "skills": ["Java", "SQL", "MongoDB"]
}

## 📌 Why do we use MongoDB?

We use MongoDB when we need flexibility, scalability, and speed.
✅ Advantages of MongoDB:
1- Schema-less (Flexible)
2-You don’t need to define columns in advance like SQL.
3-Each document can have different fields.
Example: one user can have "email", another can have "phone", both in the same collection.
Scalability

4-MongoDB supports horizontal scaling (adding more servers when data grows).
5-Used in large applications like e-commerce, social media, IoT, etc.
6-Fast for read/write
7-Stores data in BSON (binary JSON) → faster queries.
8-Good for unstructured / semi-structured data
9-If your data doesn’t fit well into tables (like user profiles, logs, JSON APIs), MongoDB is better.
10-Supports Aggregation & Indexing
11-Powerful queries like filtering, grouping, sorting.