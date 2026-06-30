# Bagian 2: Membuat Database dan Tabel

## Yang Akan Dibahas

Materi ini membahas DDL atau Data Definition Language, yaitu kelompok perintah SQL untuk membuat, mengubah, dan menghapus struktur database. Bagian ini menjadi fondasi sebelum peserta mulai memasukkan dan mengambil data.

## Tujuan Pembelajaran

Setelah mempelajari materi ini, peserta diharapkan mampu:

1. Membuat database baru menggunakan `CREATE DATABASE`.
2. Membuat tabel menggunakan `CREATE TABLE`.
3. Memilih tipe data yang sesuai untuk kolom.
4. Mengubah struktur tabel menggunakan `ALTER TABLE`.
5. Menghapus database, tabel, kolom, dan isi tabel dengan aman.

## 2.1 Apa Itu DDL?

DDL adalah kelompok perintah SQL untuk mendefinisikan struktur database. Perintah DDL tidak berfokus pada isi data, tetapi pada wadah dan aturan penyimpanan data.

Contoh objek yang dikelola oleh DDL:

- Database.
- Tabel.
- Kolom.
- Constraint.
- Index.
- View.

Perintah DDL yang umum digunakan:

| Perintah | Fungsi |
|---|---|
| `CREATE` | Membuat database, tabel, view, index, atau objek lain |
| `ALTER` | Mengubah struktur objek yang sudah ada |
| `DROP` | Menghapus objek database secara permanen |
| `TRUNCATE` | Menghapus semua isi tabel dengan cepat |
| `RENAME` | Mengganti nama objek, tergantung dukungan database |

## 2.2 Membuat Database

Database adalah tempat utama untuk menyimpan kumpulan tabel.

```sql
CREATE DATABASE toko_online;
```

Pada beberapa database, kita dapat menambahkan pengecekan agar tidak error jika database sudah ada.

```sql
CREATE DATABASE IF NOT EXISTS toko_online;
```

Catatan:

- `IF NOT EXISTS` umum digunakan di MySQL dan SQLite.
- PostgreSQL tidak mendukung `CREATE DATABASE IF NOT EXISTS` secara langsung.

## 2.3 Menggunakan Database

Pada MySQL atau MariaDB, database dipilih dengan `USE`.

```sql
USE toko_online;
```

Pada PostgreSQL, pemilihan database biasanya dilakukan saat membuat koneksi dari terminal, pgAdmin, DBeaver, atau aplikasi.

Contoh melalui terminal PostgreSQL:

```bash
psql -d toko_online
```

## 2.4 Menghapus Database

Gunakan `DROP DATABASE` untuk menghapus database.

```sql
DROP DATABASE toko_online;
```

Agar tidak error jika database tidak ada:

```sql
DROP DATABASE IF EXISTS toko_online;
```

Penting:

- `DROP DATABASE` menghapus database beserta seluruh tabel dan datanya.
- Perintah ini berbahaya pada database produksi.
- Biasakan backup sebelum menjalankan `DROP DATABASE`.

## 2.5 Membuat Tabel

Tabel adalah tempat menyimpan data dalam bentuk baris dan kolom.

```sql
CREATE TABLE customers (
    id INT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE,
    city VARCHAR(50),
    created_at DATE
);
```

Penjelasan:

- `id` adalah identitas unik setiap customer.
- `PRIMARY KEY` memastikan nilai `id` tidak kosong dan tidak duplikat.
- `name` wajib diisi karena menggunakan `NOT NULL`.
- `email` harus unik karena menggunakan `UNIQUE`.
- `city` menyimpan kota customer.
- `created_at` menyimpan tanggal data dibuat.

## 2.6 Membuat Tabel Jika Belum Ada

```sql
CREATE TABLE IF NOT EXISTS customers (
    id INT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE,
    city VARCHAR(50),
    created_at DATE
);
```

Sintaks ini membantu mencegah error ketika script SQL dijalankan ulang.

## 2.7 Tipe Data Umum

| Tipe Data | Fungsi | Contoh Nilai |
|---|---|---|
| `INT` | Bilangan bulat | `10`, `250` |
| `BIGINT` | Bilangan bulat besar | `9000000000` |
| `DECIMAL(12, 2)` | Angka desimal presisi tetap | `150000.00` |
| `VARCHAR(100)` | Teks pendek dengan batas panjang | `'Andi'` |
| `TEXT` | Teks panjang | Deskripsi produk |
| `DATE` | Tanggal | `'2026-01-10'` |
| `TIME` | Waktu | `'13:45:00'` |
| `TIMESTAMP` | Tanggal dan waktu | `'2026-01-10 13:45:00'` |
| `BOOLEAN` | Benar atau salah | `TRUE`, `FALSE` |

Tips memilih tipe data:

- Gunakan `INT` untuk angka bulat seperti jumlah stok.
- Gunakan `DECIMAL`, bukan `FLOAT`, untuk uang.
- Gunakan `VARCHAR` untuk teks pendek seperti nama dan email.
- Gunakan `DATE` untuk tanggal tanpa jam.
- Gunakan `TIMESTAMP` untuk tanggal lengkap dengan jam.

## 2.8 Membuat Tabel dengan Auto Increment

MySQL:

```sql
CREATE TABLE products (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    price DECIMAL(12, 2) NOT NULL,
    stock INT DEFAULT 0
);
```

PostgreSQL:

```sql
CREATE TABLE products (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    price DECIMAL(12, 2) NOT NULL,
    stock INT DEFAULT 0
);
```

Auto increment membuat nilai `id` bertambah otomatis saat data baru dimasukkan.

## 2.9 Mengubah Struktur Tabel

`ALTER TABLE` digunakan untuk mengubah struktur tabel yang sudah ada.

Menambahkan kolom:

```sql
ALTER TABLE customers
ADD phone VARCHAR(20);
```

Menambahkan beberapa kolom pada MySQL:

```sql
ALTER TABLE customers
ADD address TEXT,
ADD birth_date DATE;
```

Mengubah tipe kolom pada PostgreSQL:

```sql
ALTER TABLE customers
ALTER COLUMN phone TYPE VARCHAR(30);
```

Mengubah tipe kolom pada MySQL:

```sql
ALTER TABLE customers
MODIFY phone VARCHAR(30);
```

Mengubah nama kolom pada PostgreSQL:

```sql
ALTER TABLE customers
RENAME COLUMN phone TO phone_number;
```

Mengubah nama tabel:

```sql
ALTER TABLE customers
RENAME TO customer_profiles;
```

## 2.10 Menghapus Kolom

```sql
ALTER TABLE customers
DROP COLUMN phone_number;
```

Penting:

- Menghapus kolom berarti data pada kolom tersebut ikut hilang.
- Pastikan kolom tidak sedang digunakan oleh aplikasi atau laporan.

## 2.11 Menghapus Tabel

```sql
DROP TABLE customers;
```

Agar tidak error jika tabel tidak ada:

```sql
DROP TABLE IF EXISTS customers;
```

Jika tabel memiliki relasi dengan tabel lain, database bisa menolak `DROP TABLE` karena ada foreign key.

PostgreSQL mendukung `CASCADE` untuk ikut menghapus objek yang bergantung pada tabel tersebut.

```sql
DROP TABLE customers CASCADE;
```

Penting:

- `DROP TABLE` menghapus struktur tabel dan seluruh datanya.
- Gunakan dengan sangat hati-hati.
- Pada database produksi, lakukan backup dan cek dependensi terlebih dahulu.

## 2.12 Menghapus Semua Isi Tabel dengan TRUNCATE

`TRUNCATE` menghapus semua baris dalam tabel, tetapi struktur tabel tetap ada.

```sql
TRUNCATE TABLE customers;
```

Perbedaan `DELETE`, `TRUNCATE`, dan `DROP`:

| Perintah | Yang Dihapus | Struktur Tabel Tetap Ada? |
|---|---|---|
| `DELETE FROM customers;` | Semua baris data | Ya |
| `TRUNCATE TABLE customers;` | Semua baris data | Ya |
| `DROP TABLE customers;` | Tabel dan semua datanya | Tidak |

## 2.13 Urutan Umum Saat Membuat Database

1. Buat database.
2. Pilih database.
3. Buat tabel utama.
4. Tambahkan constraint.
5. Buat tabel relasi.
6. Tambahkan index jika dibutuhkan.
7. Masukkan data awal.

Contoh sederhana:

```sql
CREATE DATABASE toko_online;

USE toko_online;

CREATE TABLE categories (
    id INT PRIMARY KEY,
    name VARCHAR(100) NOT NULL
);

CREATE TABLE products (
    id INT PRIMARY KEY,
    category_id INT,
    name VARCHAR(100) NOT NULL,
    price DECIMAL(12, 2) NOT NULL,
    stock INT DEFAULT 0,
    FOREIGN KEY (category_id) REFERENCES categories(id)
);
```

---
