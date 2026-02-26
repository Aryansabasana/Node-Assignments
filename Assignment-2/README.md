# Assignment-2 — Products REST API

A simple RESTful API built with **Node.js** and **Express.js** that performs CRUD operations on an in-memory list of products.

---

## 🚀 Tech Stack

| Tool | Purpose |
|------|---------|
| Node.js | Runtime environment |
| Express.js v5 | Web framework |
| CORS | Cross-Origin Resource Sharing middleware |

---

## 📦 Getting Started

### Prerequisites
- Node.js installed on your machine

### Installation

```bash
# Navigate into the project folder
cd Assignment-2

# Install dependencies
npm install
```

### Running the Server

```bash
node index.js
```

The server starts on **http://localhost:3000**

---

## 🗃️ Sample Data

The API comes pre-loaded with 5 products:

| ID | Name | Category | Price (₹) | Stock | Rating |
|----|------|----------|-----------|-------|--------|
| 1 | Wireless Mouse | Electronics | 799 | 25 | 4.3 |
| 2 | Running Shoes | Footwear | 2499 | 40 | 4.5 |
| 3 | Laptop Stand | Accessories | 999 | 30 | 4.2 |
| 4 | Smart Watch | Electronics | 4999 | 12 | 4.4 |
| 5 | Backpack | Fashion | 1599 | 50 | 4.1 |

---

## 📡 API Endpoints

### Get All Products
```
GET /products
```
Returns the full list of products.

**Response:** `200 OK`
```json
[
  { "id": 1, "name": "Wireless Mouse", "category": "Electronics", "price": 799, "stock": 25, "rating": 4.3 },
  ...
]
```

---

### Get Product by ID
```
GET /products/:id
```
Returns a single product matching the given ID.

**Example:** `GET /products/1`

**Response:** `200 OK`
```json
{ "id": 1, "name": "Wireless Mouse", "category": "Electronics", "price": 799, "stock": 25, "rating": 4.3 }
```

---

### Get Products by Category
```
GET /products/category/:categoryName
```
Returns all products matching the given category (case-insensitive).

**Example:** `GET /products/category/electronics`

**Response:** `200 OK`
```json
[
  { "id": 1, "name": "Wireless Mouse", "category": "Electronics", ... },
  { "id": 4, "name": "Smart Watch", "category": "Electronics", ... }
]
```

---

### Add a New Product
```
POST /products/
```
Adds a new product to the list.

**Request Body:**
```json
{
  "id": 6,
  "name": "Noise Cancelling Headphones",
  "category": "Electronics",
  "price": 3499,
  "stock": 20,
  "rating": 4.6
}
```

**Response:** `201 Created`
```json
{
  "added": {
    "id": 6,
    "name": "Noise Cancelling Headphones",
    ...
  }
}
```

---

### Update a Product (Full Update)
```
PUT /products/:id
```
Replaces all fields of the product with the given ID.

**Request Body:** *(same structure as POST)*

**Response:** `201 Created`
```json
{
  "Updated": { "id": 1, "name": "...", ... }
}
```

---

### Update Product Stock
```
PUT /products/:id/stock
```
Updates only the `stock` field of a product.

**Request Body:**
```json
{ "stock": 100 }
```

**Response:** `201 Created`
```json
{
  "Updated Stock": { "id": 1, "name": "Wireless Mouse", "stock": 100, ... }
}
```

---

### Update Product Price
```
PUT /products/:id/price
```
Updates only the `price` field of a product.

**Request Body:**
```json
{ "price": 999 }
```

**Response:** `201 Created`
```json
{
  "Updated price": { "id": 1, "name": "Wireless Mouse", "price": 999, ... }
}
```

---

## 📁 Project Structure

```
Assignment-2/
├── index.js          # Main server file with all routes
├── package.json      # Project metadata and dependencies
└── README.md         # Project documentation
```

---

## ⚠️ Notes

- Data is stored **in-memory** — all changes are lost when the server restarts.
- The server runs on port **3000** by default.
