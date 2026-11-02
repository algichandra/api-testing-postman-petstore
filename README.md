# 🚀 Swagger Petstore API Testing Project

![Postman](https://img.shields.io/badge/Postman-FF6C37?style=for-the-badge&logo=postman&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![API Testing](https://img.shields.io/badge/API%20Testing-Automated-blue?style=for-the-badge)

## 📌 Overview
Proyek ini berisi pengujian API menyeluruh (*End-to-End API Testing*) untuk **Swagger Petstore API (v2)** menggunakan **Postman**. Pengujian mencakup skenario pengujian manual, pembuatan *Automated Test Scripts* (assertions), hingga penanganan skenario positif (*Happy Path*) dan negatif (*Negative Testing/Error Handling*).

---

## 📑 Test Scope & Coverage

### 1. User Management Module
* **POST** `/user` — Create a new user profile
* **GET** `/user/{username}` — Retrieve user profile by valid username
* **GET** `/user/login` — User authentication and session handling
* **PUT** `/user/{username}` — Update user profile details
* **GET** `/user/logout` — Terminate user session
* **DELETE** `/user/{username}` — Remove user profile

### 2. Pet Management Module
* **POST** `/pet` — Add a new pet to the store
* **GET** `/pet/{petId}` — Retrieve pet details by ID
* **GET** `/pet/findByStatus` — Filter pets by status (`available`, `pending`, `sold`)
* **PUT** `/pet` — Update existing pet information and status
* **DELETE** `/pet/{petId}` — Remove pet record by ID

---

## 🛠️ Key Features & Technical Highlights

* **Automated Assertions (`pm.test`):**
  * HTTP Status Code validation (`200 OK`, `404 Not Found`, etc.)
  * Response body data type and key-value payload validations
  * Response time performance threshold (< 2000 ms)
* **Environment Variables Management:** Dynamic test execution utilizing variables (`base_url`, `username`).
* **Collection Runner Automation:** Executing complete test suites automatically with zero manual observation required per request.
* **Negative & Boundary Testing:** Verifying API behavior on invalid parameters, non-existent endpoints/users, and handling server-side integer overflow cases safely.

---

## 📂 Repository Structure

```text
.
├── Petstore_Postman_Collection.json      # Exported Postman collection with test scripts
├── Petstore_Environment.json             # Postman environment variables setup
├── Petstore_API_Test_Execution_Report.xlsx # Test execution report & test cases
└── README.md                             # Project documentation
