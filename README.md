# Swagger Petstore API Testing Project

![Postman](https://img.shields.io/badge/Postman-FF6C37?style=for-the-badge&logo=postman&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![API Testing](https://img.shields.io/badge/API%20Testing-Positive%20%26%20Negative-blue?style=for-the-badge)
![Result](https://img.shields.io/badge/Result-13%2F13%20Passed-success?style=for-the-badge)

## 📌 Overview

Proyek ini berisi pengujian API (*End-to-End API Testing*) untuk **Swagger Petstore API (v2)** menggunakan **Postman**. Pengujian mencakup penyusunan test case, *automated test scripts* berbasis JavaScript (`pm.test` assertions), skenario positif (*happy path*) dan negatif (*error handling*), serta pelaporan hasil eksekusi dalam bentuk Test Execution Report (Excel).

Test script dijalankan secara otomatis melalui **Postman Collection Runner**.

---

## 📊 Ringkasan Hasil

| Modul | Total Test Case | Passed | Failed | Pass Rate |
|---|---|---|---|---|
| User Management | 7 | 7 | 0 | 100% |
| Pet Management | 6 | 6 | 0 | 100% |
| **Total** | **13** | **13** | **0** | **100%** |

Komposisi: 11 skenario positif dan 2 skenario negatif.

<!-- Tambahkan screenshot hasil Collection Runner di sini setelah file gambarnya diunggah ke folder screenshots/:
![Hasil Collection Runner](screenshots/runner-result.png)
-->

Laporan lengkap: [`reports/`](reports/) (file Excel berisi sheet *Summary Report* dan *Test Cases Execution*).

---

## 📑 Test Scope & Test Cases

### 1. User Management Module

| ID | Endpoint | Method | Tipe | Skenario | Expected | Actual | Status |
|---|---|---|---|---|---|---|---|
| TC_USER_01 | `/user` | POST | Positive | Membuat user baru dengan payload valid | 200 | 200 | ✅ PASS |
| TC_USER_02 | `/user/{username}` | GET | Positive | Mengambil detail user dengan username valid | 200 | 200 | ✅ PASS |
| TC_USER_03 | `/user/login` | GET | Positive | Login dengan kredensial valid (query params) | 200 | 200 | ✅ PASS |
| TC_USER_04 | `/user/{username}` | PUT | Positive | Memperbarui informasi profil user | 200 | 200 | ✅ PASS |
| TC_USER_05 | `/user/logout` | GET | Positive | Logout sesi user | 200 | 200 | ✅ PASS |
| TC_USER_06 | `/user/{username}` | DELETE | Positive | Menghapus user berdasarkan username | 200 | 200 | ✅ PASS |
| TC_USER_07 | `/user/{username}` | GET | **Negative** | Mengambil user yang tidak ada | 404 | 404 | ✅ PASS |

### 2. Pet Management Module

| ID | Endpoint | Method | Tipe | Skenario | Expected | Actual | Status |
|---|---|---|---|---|---|---|---|
| TC_PET_01 | `/pet` | POST | Positive | Membuat data pet baru dengan ID integer pendek | 200 | 200 | ✅ PASS |
| TC_PET_02 | `/pet/{petId}` | GET | Positive | Mengambil detail pet dengan petId valid | 200 | 200 | ✅ PASS |
| TC_PET_03 | `/pet/findByStatus` | GET | Positive | Memfilter pet berdasarkan status `available` | 200 | 200 | ✅ PASS |
| TC_PET_04 | `/pet` | PUT | Positive | Memperbarui nama dan status pet menjadi `sold` | 200 | 200 | ✅ PASS |
| TC_PET_05 | `/pet/{petId}` | DELETE | Positive | Menghapus pet berdasarkan petId | 200 | 200 | ✅ PASS |
| TC_PET_06 | `/pet` | POST | **Negative** | Membuat pet dengan data tidak valid | 500 | 500 | ✅ PASS |

---

## 🛠️ Key Features & Technical Highlights

* **Automated Assertions (`pm.test`)**
  * Validasi HTTP status code (`200 OK`, `404 Not Found`, `500`)
  * Validasi isi response body: nilai field (`username`, `id`, `status`, `message`) dan tipe data (`array`)
* **Environment Variables:** eksekusi dinamis dengan variabel environment (misalnya `base_url`).
* **Collection Runner:** seluruh test dijalankan berurutan tanpa menekan Send satu per satu.
* **Positive & Negative Testing:** mencakup alur normal serta perilaku API terhadap data yang tidak ada atau tidak valid.
* **Dokumentasi:** hasil eksekusi dicatat dalam Test Execution Report (Excel) dengan ringkasan per modul.

---

## 🔎 Catatan Temuan

* **TC_PET_06:** request pembuatan pet dengan data tidak valid dibalas **500 (Internal Server Error)**. Secara konvensi REST, kesalahan input dari client idealnya dibalas **4xx (misalnya 400 Bad Request)**, bukan 500 yang menandakan kegagalan di sisi server. Test script saat ini menerima 400 atau 500 (`oneOf([400, 500])`), sehingga dicatat PASS terhadap perilaku aktual API. Ini diamati sebagai kandidat perbaikan, bukan kegagalan test.

---

## 📂 Repository Structure

```text
.
├── collections/
│   ├── pet.postman_collection.json       # Collection modul Pet beserta test scripts
│   └── user.postman_collection.json      # Collection modul User beserta test scripts
├── environment/
│   └── swagger.postman_environment.json  # Variabel environment Postman
├── reports/
│   └── petstore-api-test-execution-report.xlsx  # Test cases & hasil eksekusi
└── README.md
```

---

## ▶️ Cara Menjalankan

1. Clone repository ini atau unduh file-nya.
2. Buka **Postman**, lalu **Import** semua file di folder `collections/` dan `environment/`.
3. Pilih environment **swagger** di pojok kanan atas.
4. Klik kanan collection, pilih **Run collection**, lalu klik **Run**.
5. Lihat hasil pass/fail di tab **Test Results**.

> Catatan: modul User dan Pet berada di collection terpisah. Jalankan masing-masing secara berurutan karena beberapa request bergantung pada data dari request sebelumnya (misalnya username dan petId).

---

## 🧰 Tools

* Postman (Collection Runner, Environment)
* JavaScript (`pm.test`, `pm.expect`, Chai assertions)
* Microsoft Excel (Test Execution Report)
* Git & GitHub (version control)

---
