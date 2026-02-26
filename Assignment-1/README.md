# Assignment-1 — Student Records REST API

A simple **Node.js + Express** REST API that serves student records stored in-memory. It exposes endpoints to retrieve all students, find a student by ID or branch, and compute statistics like the topper, average CGPA, and total count.

---

## 🛠 Tech Stack

| Technology | Version |
|------------|---------|
| Node.js    | ≥ 18.x  |
| Express.js | ^5.2.1  |

---

## 📁 Project Structure

```
Assignment-1/
├── index.js          # Main server file with all routes
├── package.json      # Project metadata and dependencies
└── README.md         # Project documentation
```

---

## 🚀 Getting Started

### Prerequisites

Make sure you have **Node.js** installed. You can verify with:

```bash
node -v
npm -v
```

### Installation

1. Navigate to the project folder:

   ```bash
   cd Assignment-1
   ```

2. Install dependencies:

   ```bash
   npm install
   ```

3. Start the server:

   ```bash
   node index.js
   ```

The server will start on **http://localhost:3000**

---

## 📡 API Endpoints

### Base URL
```
http://localhost:3000
```

---

### 1. Get All Students

**GET** `/students`

Returns the full list of all students.

**Response:**
```json
[
  { "id": 1, "name": "Aarav Sharma", "branch": "CSE", "semester": 8, "cgpa": 9.3 },
  ...
]
```

---

### 2. Get Topper

**GET** `/students/topper`

Returns the student with the highest CGPA.

**Response:**
```json
{ "id": 1, "name": "Aarav Sharma", "branch": "CSE", "semester": 8, "cgpa": 9.3 }
```

---

### 3. Get Average CGPA

**GET** `/students/average`

Returns the average CGPA of all students.

**Response:**
```json
{ "average": 8.61 }
```

---

### 4. Get Total Student Count

**GET** `/students/count`

Returns the total number of students.

**Response:**
```json
{ "totalStudents": 10 }
```

---

### 5. Get Student by ID

**GET** `/students/:id`

Returns a single student matching the given ID.

| Parameter | Type   | Description         |
|-----------|--------|---------------------|
| `id`      | Number | The student's ID    |

**Example:** `GET /students/3`

**Success Response (200):**
```json
{ "id": 3, "name": "Rohan Kulkarni", "branch": "ECE", "semester": 6, "cgpa": 8.4 }
```

**Error Response (404):**
```json
{ "message": "Student Not Found" }
```

---

### 6. Get Student by Branch

**GET** `/students/branch/:branchName`

Returns the first student found in the given branch (case-insensitive).

| Parameter    | Type   | Description              |
|--------------|--------|--------------------------|
| `branchName` | String | Branch name (e.g. `cse`) |

**Example:** `GET /students/branch/cse`

**Success Response (200):**
```json
{ "id": 1, "name": "Aarav Sharma", "branch": "CSE", "semester": 8, "cgpa": 9.3 }
```

**Error Response (404):**
```json
{ "message": "Student Not Found" }
```

---

## 🗂 Sample Data

The server ships with 10 pre-loaded students across branches: **CSE, IT, ECE, AI, Data Science**.

| ID | Name              | Branch       | Semester | CGPA |
|----|-------------------|--------------|----------|------|
| 1  | Aarav Sharma      | CSE          | 8        | 9.3  |
| 2  | Ishita Verma      | IT           | 7        | 8.9  |
| 3  | Rohan Kulkarni    | ECE          | 6        | 8.4  |
| 4  | Meera Iyer        | CSE          | 8        | 9.1  |
| 5  | Kunal Deshmukh    | IT           | 5        | 7.8  |
| 6  | Ananya Reddy      | CSE          | 6        | 8.7  |
| 7  | Vikram Patil      | ECE          | 7        | 8.2  |
| 8  | Priyanka Nair     | AI           | 4        | 8.8  |
| 9  | Harsh Mehta       | Data Science | 5        | 8.0  |
| 10 | Neha Gupta        | CSE          | 6        | 7.9  |

---

## 📝 Notes

- Data is stored **in-memory** — it resets every time the server restarts.
- The `/students/topper`, `/students/average`, and `/students/count` routes must be defined **before** `/students/:id` to avoid route conflicts.
- Branch lookup is **case-insensitive** on the stored value but requires the URL parameter to be **lowercase**.

---

## 👤 Author

**Aryan Sabasana**
