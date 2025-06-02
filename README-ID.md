# Inventra - API Manajemen Inventaris

[![Versi Java](https://img.shields.io/badge/Java-21-blue.svg)](https://www.oracle.com/java/technologies/downloads/#java21)
[![Versi Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.5.0-brightgreen.svg)](https://spring.io/projects/spring-boot)
[![Build Maven](https://img.shields.io/badge/Build-Maven-red.svg)](https://maven.apache.org/)

Inventra adalah RESTful API yang tangguh untuk mengelola sistem inventaris. API ini memungkinkan pengguna untuk melakukan operasi CRUD (Create, Read, Update, Delete) pada produk dan kategorinya. Dibangun dengan Spring Boot, Inventra menyediakan fondasi backend yang solid untuk aplikasi terkait inventaris.

## ✨ Fitur Utama

*   **Manajemen Kategori**: Operasi CRUD penuh untuk kategori produk.
*   **Manajemen Produk**: Operasi CRUD penuh untuk produk, termasuk asosiasi dengan kategori.
*   **RESTful API**: Endpoint API yang bersih dan intuitif.
*   **Validasi Input**: Menjamin integritas data melalui validasi payload permintaan.
*   **Penanganan Eksepsi Terpusat**: Memberikan respons error yang konsisten dan informatif.
*   **Spring Data JPA**: Menyederhanakan interaksi database dengan MySQL.

## 🛠️ Teknologi yang Digunakan

*   **Java 21**: Bahasa pemrograman inti.
*   **Spring Boot 3.5.0**: Kerangka kerja untuk membangun aplikasi.
    *   Spring Web: Untuk membangun RESTful API.
    *   Spring Data JPA: Untuk persistensi data.
    *   Spring Boot Starter Validation: Untuk validasi input.
*   **Hibernate**: Penyedia JPA.
*   **Maven**: Otomatisasi build dan manajemen dependensi.
*   **MySQL**: Database relasional untuk menyimpan data inventaris.
*   **Lombok**: Mengurangi kode boilerplate (misalnya, getter, setter, konstruktor).
*   **Jakarta Validation API**: Untuk mendefinisikan dan memvalidasi batasan pada objek.

## 📋 Prasyarat

Sebelum memulai, pastikan Anda telah menginstal:

*   **JDK 21** (Java Development Kit)
*   **Maven** (Dapat menggunakan Maven Wrapper `mvnw` yang disertakan)
*   **MySQL Server**: Berjalan dan dapat diakses.

## 🚀 Pengaturan & Instalasi

1.  **Clone Repositori**
    ```bash
    # git clone https://github.com/i-snrdra/Inventra-SpringBoot.git
    # cd Inventra
    ```
    *(Saat ini, Anda bekerja dengan proyek secara lokal.)*

2.  **Pengaturan Database**
    *   Pastikan server MySQL Anda berjalan.
    *   Buat database dengan nama `inventra_db`:
        ```sql
        CREATE DATABASE inventra_db;
        ```
    *   Konfigurasikan kredensial database Anda di `src/main/resources/application.properties`:
        ```properties
        spring.datasource.url=jdbc:mysql://localhost:3306/inventra_db
        spring.datasource.username=username_mysql_anda # Biasanya 'root' untuk dev lokal
        spring.datasource.password=password_mysql_anda # Biarkan kosong jika tidak ada password
        ```
        *Catatan: Proyek saat ini dikonfigurasi untuk menggunakan `root` tanpa password.*

3.  **Build Proyek**
    Buka terminal di direktori root proyek dan jalankan:
    *   Di Windows:
        ```bash
        .\mvnw.cmd clean package
        ```
    *   Di macOS/Linux:
        ```bash
        ./mvnw clean package
        ```
    Perintah ini akan mengompilasi kode, menjalankan tes, dan mengemas aplikasi menjadi file JAR yang dapat dieksekusi di direktori `target/` (misalnya, `Inventra-0.0.1-SNAPSHOT.jar`). Aplikasi kemudian dapat dijalankan menggunakan `java -jar target/Inventra-0.0.1-SNAPSHOT.jar`.

## 🔌 Endpoint API

Semua endpoint diawali dengan `/api`. API berkomunikasi menggunakan JSON.

### Endpoint Kategori (`/api/categories`)

*   **`POST /api/categories`**: Membuat kategori baru.
    *   Request Body:
        ```json
        {
            "name": "Nama Kategori"
        }
        ```
*   **`GET /api/categories`**: Mendapatkan semua kategori.
*   **`GET /api/categories/{id}`**: Mendapatkan kategori spesifik berdasarkan ID.
*   **`PUT /api/categories/{id}`**: Memperbarui kategori yang ada.
    *   Request Body: Sama seperti POST.
*   **`DELETE /api/categories/{id}`**: Menghapus kategori.

### Endpoint Produk (`/api/products`)

*   **`POST /api/products`**: Membuat produk baru.
    *   Request Body:
        ```json
        {
            "name": "Nama Produk",
            "stock": 100,
            "price": 99.99,
            "categoryId": 1
        }
        ```
*   **`GET /api/products`**: Mendapatkan semua produk.
*   **`GET /api/products/{id}`**: Mendapatkan produk spesifik berdasarkan ID.
*   **`PUT /api/products/{id}`**: Memperbarui produk yang ada.
    *   Request Body: Sama seperti POST.
*   **`DELETE /api/products/{id}`**: Menghapus produk.

## ⚙️ Konfigurasi

*   **Koneksi Database**: Terletak di `src/main/resources/application.properties`.
    *   `spring.datasource.url`
    *   `spring.datasource.username`
    *   `spring.datasource.password`
*   **JPA & Hibernate**:
    *   `spring.jpa.hibernate.ddl-auto=update`: Secara otomatis memperbarui skema database berdasarkan entitas. Ubah sesuai kebutuhan untuk lingkungan yang berbeda (misalnya, `validate` atau `none` untuk produksi).
    *   `spring.jpa.show-sql=true`: Menampilkan statement SQL di log.
    *   `spring.jpa.properties.hibernate.format_sql=true`: Memformat statement SQL yang ditampilkan di log.

## 🧪 Pengujian

Disarankan untuk menggunakan klien API seperti [Postman](https://www.postman.com/) atau [Insomnia](https://insomnia.rest/) untuk menguji endpoint API.

1.  Pastikan aplikasi berjalan (misalnya, dengan menjalankan `java -jar target/Inventra-0.0.1-SNAPSHOT.jar` dari root proyek setelah build).
2.  Kirim permintaan HTTP ke endpoint yang telah ditentukan (lihat bagian [Endpoint API](#-endpoint-api)).
    *   Untuk permintaan `POST` dan `PUT`, pastikan header `Content-Type` diatur ke `application/json`.
    *   Amati kode status HTTP dan respons JSON.

## 🤝 Berkontribusi (Placeholder)

Kontribusi sangat diharapkan! Jika Anda ingin berkontribusi, silakan ikuti langkah-langkah berikut:
1.  Fork repositori ini.
2.  Buat branch baru (`git checkout -b feature/nama-fitur-anda`).
3.  Lakukan perubahan Anda.
4.  Commit perubahan Anda (`git commit -m 'Menambahkan fitur X'`).
5.  Push ke branch (`git push origin feature/nama-fitur-anda`).
6.  Buka Pull Request.

## 📜 Lisensi

Proyek ini dilisensikan di bawah Lisensi MIT - lihat file `LICENSE.md` untuk detailnya.

---

*Stay Curious!* 