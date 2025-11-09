# MongoDB

## Definition
**MongoDB** is a **NoSQL document-oriented database** that stores data in flexible **BSON (Binary JSON)** documents instead of traditional rows and tables.

## Why MongoDB (Purpose)
MongoDB is used because:

- No need for a fixed schema (**flexible structure**)
- Handles **large unstructured / semi-structured data**
- Supports **horizontal scalability (Sharding)**
- **Faster read/write** for high-volume applications
- Useful when **application data changes frequently**
- Can store **nested and complex objects**
- Suitable for **real-time analytics, logging, sessions**
- Works well for **distributed systems / cloud apps**
- All information related to a document will be stored in a single place.
- To retrieve data, it is not required to perform join operations.
- Documents are independent of each other and no schema.
- Retrieval data is in the form of JSON which can be understandable by any programming language without any conversion (interoperability)



## Applications (Where It Is Used)

| Domain | Use Case |
|-------|----------|
| Social Media | Users, posts, comments, likes |
| E-commerce | Product catalogs, orders |
| Real-Time Analytics | Dashboards, monitoring |
| IoT Systems | Sensor data storage |
| Mobile Apps | Offline + sync data storage |
| CMS | Articles, media storage |
| Chat Apps | Messages, conversations |

### Companies Using MongoDB
- Facebook (Messaging)
- Adobe
- Uber
- eBay
- Google (some services)

---

# Sharding in MongoDB

## Meaning
**Sharding** = Splitting a large collection into smaller parts (**shards**) stored across multiple machines.

## Why Sharding is Needed
As data grows:

- One server becomes slow
- Storage runs out
- Query performance drops

Sharding solves this by distributing data across **multiple servers**.

## How Sharding Works

| Component | Role |
|---------|------|
| **Shard Key** | Field used to divide data into chunks |
| **Chunks** | Data segments based on shard key |
| **Shards** | Servers storing different chunks |
| **mongos Router** | Routes queries to correct shard |
| **Config Servers** | Store metadata about shard distribution |

**Flow:**
1. Collection is split into **chunks** using a **shard key**.
2. Chunks are distributed across **multiple shards (servers)**.
3. `mongos` router decides **which shard** to query.
4. Config servers maintain the **location map of data**.

---

# Difference Between RDBMS and MongoDB

| **Feature** | **RDBMS (Relational Database)** | **MongoDB (NoSQL Document Database)** |
|------------|--------------------------------|--------------------------------------|
| **Data Model** | Table-based (rows & columns) | Document-based (JSON/BSON) |
| **Schema** | Fixed schema (structure must be predefined) | Schema-less (structure can change anytime) |
| **Data Storage** | Data stored in tables | Data stored in **collections** as **documents** |
| **Relationships** | Uses **JOINs** to connect multiple tables | Embeds related data **inside documents** (reduces need for JOINs) |
| **Query Language** | **SQL** (Structured Query Language) | **MQL** (MongoDB Query Language) |
| **Scaling** | **Vertical Scaling** (increasing CPU/RAM of one server) | **Horizontal Scaling / Sharding** (adding more servers) |
| **Performance** | Slower for handling large unstructured data | Faster for large or unstructured data |
| **Transactions** | Strong multi-table **ACID** transactions | Supports transactions, but optimized for **document-level** operations |
| **Best Used For** | Banking, ERP, HR systems (structured and consistent data) | Social media, IoT, real-time apps (dynamic, rapidly changing data) |

---
# Difference Between JSON and BSON

| **Feature** | **JSON** | **BSON** |
|------------|----------|----------|
| **Type** | Text format | Binary format |
| **Speed** | Fast to read but slower to build | Slow to read but faster to build and scan |
| **Space** | JSON data is slightly smaller in byte size | BSON data is slightly larger in byte size |
| **Encode & Decode** | Can be sent directly through APIs without encoding/decoding | Encoded before storing and decoded before displaying |
| **Parse** | Human-readable (no special parsing needed) | Needs parsing (machine-generated / not human-readable) |
| **Data Types** | Limited types: string, boolean, number, array, object, null | Supports additional types like `binData`, `decimal128`, `date`, etc. |
| **Usage** | Used mainly for **data transfer** (e.g., APIs, web communication) | Used mainly for **data storage** in databases (e.g., MongoDB) |

---
# Indexing in MongoDB

## Definition
**Indexing** in MongoDB is a technique used to **speed up search (query) operations** in a collection.

- **Without Index** → MongoDB performs **COLLSCAN** (Collection Scan) → checks every document → **slow**
- **With Index** → MongoDB performs **IXSCAN** (Index Scan) → directly finds matching documents → **fast**

---

## How Indexes Work
MongoDB indexes are stored as **B-Tree (Balanced Tree) structures**, which allow:

- Fast searching
- Fast sorting
- Fast range queries (e.g., `10 < x < 50`)

---

## Default Index
MongoDB automatically creates an index on the **_id** field.

```js
_id: ObjectId("...")   // always indexed by default
```
Types of Indexes in MongoDB
### 1. Single Field Index

Index created on one field.
```js
db.employees.createIndex({ ename: 1 })   // 1 → Ascending order
db.employees.createIndex({ esal: -1 })   // -1 → Descending order
```
Used for:

Fast equality queries (ename = "Sunny")

Sorting based on a field
### 2. Compound Index

Index on multiple fields.
```js
db.employees.createIndex({ ename: 1, esal: -1 })
```
### 3. Unique Index

Prevents duplicate values for a field.
```js

db.students.createIndex({ rollno: 1 }, { unique: true })
```

### How to View Indexes
```js

db.employees.getIndexes()
```

### How to Remove Index
```js

db.employees.dropIndex({ ename: 1 })
```

### Checking Query Performance

Use explain() to check whether index is used:
```js

db.employees.find({ ename: "Sunny" }).explain("executionStats")
```

Look for:
Term	Meaning	Performance
COLLSCAN	Full collection scan	Slow (No index used)
IXSCAN	Index-based scan	Fast (Index used)

### Additional Index Options

#### Option	Purpose
- unique	Ensures no duplicates
- background	Creates index without locking database (used in production)
Syntax
```js
db.collection.createIndex(
  { fieldName: 1 },
  { unique: true, background: true }
)
```
### Advantages of Indexing

Faster search/query operations

Faster sorting and range queries

Improved overall query performance

### Disadvantages of Indexing

Extra storage space required

Write operations (insert, update, delete) become slower

Must be used carefully; unnecessary indexes reduce efficiency
