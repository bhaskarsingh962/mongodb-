# 📘 Importing JSON in MongoDB

MongoDB allows you to import JSON data into a database using the **`mongoimport`** tool.  
This is useful when you want to load external data into MongoDB for testing or production use.

---

## 🔹 General Command

```bash
mongoimport <filename>.json -d <database_name> -c <collection_name>
Meaning:
<filename>.json → The JSON file you want to import.

-d <database_name> → Database where the data will be stored. (If it doesn’t exist, MongoDB creates it after insertion.)


-c <collection_name> → Collection inside the database where data will be stored.

🔹 Example 1: Basic Import
bash
Copy code
mongoimport products.json -d shop -c products
👉 Explanation:

products.json = JSON file containing product data.

-d shop = Use (or create) a database called shop.

-c products = Import data into the products collection.

✅ This imports each JSON document (one per line) into the shop.products collection.


##  🔹 Example 2: Import JSON Array
bash
Copy code
mongoimport products.json -d shop -c products --jsonArray
👉 Explanation:

--jsonArray tells MongoDB the JSON file contains an array of documents instead of single-line JSON objects.

Without this, if your file has:

json
Copy code
[
  { "name": "Laptop", "price": 55000 },
  { "name": "Phone", "price": 30000 }
]
MongoDB will throw an error.

With --jsonArray, it correctly imports both documents.




## 🔹 Example 3: Generic Syntax
bash
Copy code
mongoimport jsonfile.json -d database_name -c collection_name
👉 Explanation:

Replace jsonfile.json with your actual JSON file.

Replace database_name and collection_name with your DB and collection names.

🔹 Important Notes
--jsonArray

Needed when the JSON file contains multiple documents inside an array.

Without it, MongoDB expects one JSON object per line.

File Size Limit

By default, mongoimport supports imports of 16 MB or smaller per document.

For larger datasets, use mongorestore or break data into smaller files.

Database Visibility

Remember, the database only appears in show dbs after you insert/import data.

🔑 Why Use mongoimport?
Quick way to load test data into MongoDB.

Easy to migrate existing JSON/CSV data into MongoDB.

Useful for backup/restore operations (along with mongodump / mongorestore).

✅ Summary
Use mongoimport when you have JSON/CSV data outside MongoDB and want to bring it in.

Choose --jsonArray if your file is wrapped in [ ].

Always specify -d (database) and -c (collection) to keep data organized.

pgsql
Copy code

---

👉 You can copy this into **VS Code**, save as `mongoimport-notes.md`, and open it in **Markdown preview** (`Ctrl + Shift + V`) for a nice formatted view.  

Do you want me to also add a **sample JSON file** (`products.json`) that you can try importing directly?






