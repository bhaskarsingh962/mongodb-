##   📘 MongoDB Comparison Operators

MongoDB uses special operators that start with $ for queries.

##  🔹 1. Equal To ($eq)

Find documents where a field is equal to a value.

db.products.find({ price: { $eq: 30000 } })


👉 Matches products with price = 30000.

##  🔹 2. Not Equal ($ne)

Find documents where a field is not equal to a value.

db.products.find({ price: { $ne: 30000 } })


👉 Matches products whose price is not 30000.

##  🔹 3. Greater Than ($gt)

Find documents where a field is greater than a value.

db.products.find({ price: { $gt: 10000 } })


👉 Matches products with price > 10000.

##  🔹 4. Greater Than or Equal ($gte)

Find documents where a field is greater than or equal to a value.

db.products.find({ price: { $gte: 10000 } })


👉 Matches products with price ≥ 10000.

##  🔹 5. Less Than ($lt)

Find documents where a field is less than a value.

db.products.find({ price: { $lt: 10000 } })


👉 Matches products with price < 10000.

##  🔹 6. Less Than or Equal ($lte)

Find documents where a field is less than or equal to a value.

db.products.find({ price: { $lte: 10000 } })


👉 Matches products with price ≤ 10000.

##  🔹 7. In ($in)

Find documents where a field’s value is in an array.

db.products.find({ brand: { $in: ["Dell", "Sony"] } })


👉 Matches products whose brand is Dell or Sony.

##  🔹 8. Not In ($nin)

Find documents where a field’s value is not in an array.

db.products.find({ brand: { $nin: ["Samsung", "Milton"] } })


👉 Matches products whose brand is not Samsung or Milton.

✅ Combine Queries

You can combine multiple operators in one query.

db.products.find({
  price: { $gt: 1000, $lt: 50000 }
})


##  👉 Matches products with 1000 < price < 50000.

🔑 Summary of Operators
Operator	Meaning
$eq	Equal to
$ne	Not equal to
$gt	Greater than
$gte	Greater than or equal to
$lt	Less than
$lte	Less than or equal to
$in	Matches any value in array
$nin	Matches none of the values in array



//* Comparison Operators

//? 1 $eq: Matches values that are equal to the specified value.
// db.products.find({'price': {$eq:699}})

//? 2: $ne: Matches values that are not equal to the specified value.
// db.products.find({'price': {$ne:699}}).count()

// 3: $gt: Matches values that are greater than the specified value.
// db.products.find({'price': {$gt:699}})

// 4: $gte: Matches values that are greater than or equal to the specified value.
// db.products.find({'price': {$gte:699}})

// 5: $lt: Matches values that are less than the specified value.
// db.products.find({'price': {$lt:699}})

// 6: $lte: Matches values that are less than or equal to the specified value.
// Find products with price less than or equal to 699
// db.products.find({'price': {$lte:699}})

// $in: Matches values that are within the specified array.
// db.products.find({'price': 129, 'price':39})
// db.products.find({'price': {$in: [129,39]}})
//? Now here I will go with different collection
// db.category.find({ name: { $in: ["Travel & Luggage", "Home & Kitchen"] } });

//? $nin: Matches values that are not within the specified array.
// db.products.find({'price': {$nin: [249,129,39]}}).count()