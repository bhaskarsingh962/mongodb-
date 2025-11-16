//* Projection
// Which filed to display which not, only the _id is needs to be explicitly defined so that the _id won’t be included in our output.

// Including Specific Fields: To include only specific fields in the query result, you can use the projection with a value of 1 for the fields you want to include.
// db.products.find({}, { name:1, price:1}).limit(2)

// Excluding Specific Fields:To exclude specific fields from the query result, you can use the projection with a value of 0 for the fields you want to exclude.

// db.products.find({}, {_id:0, name:1, price:1}).limit(2)
// only show name and price

//! We cannot include and exclude fields in the same query projection in MongoDB. It's either inclusion or exclusion, not both simultaneously.
// db.products.find({}, { _id: 0, name: 1, price: 1, price: 0 }).limit(2);





# 📘 MongoDB Projection and Exclusion

## 🔹 What is Projection?
- **Projection** means selecting only the fields you want from a document.  
- By default, `find()` returns all fields of a document.  
- With projection, you can **include** or **exclude** specific fields.

👉 Syntax:
```js
db.collection.find(query, projection)
query → filter condition (like { price: { $gt: 1000 } })

projection → specifies which fields to show or hide

🔹 Inclusion Projection
Use 1 to include a field.

_id field is always returned by default (unless excluded).

👉 Example:

db.products.find({}, { name: 1, price: 1 })
✅ Returns only name, price, and _id.
👉 Example (remove _id):e
db.products.find({}, { name: 1, price: 1, _id: 0 })
✅ Returns only name and price (without _id).
🔹 Exclusion Projection
Use 0 to exclude a field.
You cannot mix inclusion and exclusion in the same projection (except _id).

👉 Example:
db.products.find({}, { description: 0, brand: 0 })
✅ Returns all fields except description and brand.