# Modul Pembelajaran SQL: Dasar sampai Lanjutan

## Yang Akan Dibahas

Materi ini membahas pengenalan SQL dan database relasional sebagai dasar sebelum masuk ke query. Peserta akan mengenal konsep database, tabel, baris, kolom, primary key, foreign key, serta kelompok perintah SQL.

## Tujuan Pembelajaran Materi

Setelah mempelajari materi ini, peserta diharapkan mampu:

1. Menjelaskan pengertian database dan database relasional.
2. Memahami peran SQL dalam pengelolaan data.
3. Mengenali komponen dasar tabel seperti baris, kolom, primary key, dan foreign key.
4. Membedakan kelompok perintah SQL seperti DDL, DML, DQL, DCL, dan TCL.

## Deskripsi Modul

Modul ini dirancang untuk membantu pembelajar memahami SQL secara bertahap, mulai dari konsep database, query dasar, pengolahan data, relasi antar tabel, sampai topik lanjutan seperti subquery, window function, transaction, indexing, dan optimasi query.

SQL atau Structured Query Language adalah bahasa yang digunakan untuk mengelola dan mengambil data dari database relasional. SQL banyak digunakan pada aplikasi web, sistem informasi, data analyst, data engineer, business intelligence, dan backend development.

## Tujuan Pembelajaran

Setelah menyelesaikan modul ini, peserta diharapkan mampu:

1. Memahami konsep dasar database relasional.
2. Membuat database dan tabel menggunakan SQL.
3. Mengambil, menambah, mengubah, dan menghapus data.
4. Menggunakan filter, sorting, grouping, dan aggregate function.
5. Menggabungkan data dari beberapa tabel dengan JOIN.
6. Menggunakan subquery, CTE, view, dan window function.
7. Memahami constraint, relasi, transaction, indexing, dan dasar optimasi query.
8. Membuat query untuk kebutuhan studi kasus nyata.

## Prasyarat

Sebelum memulai, peserta sebaiknya memahami:

- Dasar penggunaan komputer.
- Logika pemrograman sederhana.
- Konsep data berbentuk tabel, baris, dan kolom.

Software yang dapat digunakan:

- PostgreSQL
- MySQL atau MariaDB
- SQLite
- SQL Server
- DB Browser for SQLite, DBeaver, TablePlus, DataGrip, atau pgAdmin

Catatan: Contoh dalam modul ini menggunakan gaya SQL umum. Beberapa database memiliki perbedaan kecil pada tipe data, fungsi tanggal, auto increment, dan sintaks tertentu.

---


# Bagian 1: Pengenalan Database dan SQL

## 1.1 Apa Itu Database?

Database adalah tempat penyimpanan data yang disusun secara terstruktur agar mudah dikelola, dicari, diperbarui, dan dianalisis.

Contoh penggunaan database:

- Data pelanggan toko online.
- Data transaksi penjualan.
- Data mahasiswa dan nilai.
- Data produk, stok, dan kategori.
- Data pengguna aplikasi.

## 1.2 Database Relasional

Database relasional menyimpan data dalam bentuk tabel. Setiap tabel memiliki:

- Kolom, yaitu atribut data.
- Baris, yaitu satu record data.
- Primary key, yaitu identitas unik setiap baris.
- Foreign key, yaitu kolom yang menghubungkan satu tabel dengan tabel lain.

Contoh tabel `customers`:

| id | name | email | city |
|---:|---|---|---|
| 1 | Andi | andi@example.com | Jakarta |
| 2 | Budi | budi@example.com | Bandung |

## 1.3 Apa Itu SQL?

SQL adalah bahasa untuk berinteraksi dengan database relasional. Dengan SQL, kita dapat:

- Membuat struktur database.
- Mengambil data.
- Menambahkan data.
- Mengubah data.
- Menghapus data.
- Mengatur hak akses.
- Mengoptimalkan proses pencarian data.

## 1.4 Kelompok Perintah SQL

Perintah SQL biasanya dibagi menjadi lima kelompok utama. Pembagian ini membantu kita memahami tujuan dari setiap query.

| Kelompok | Fungsi | Contoh Perintah |
|---|---|---|
| DDL | Membuat dan mengubah struktur database | `CREATE`, `ALTER`, `DROP` |
| DML | Mengelola isi data | `INSERT`, `UPDATE`, `DELETE` |
| DQL | Mengambil data | `SELECT` |
| DCL | Mengatur hak akses | `GRANT`, `REVOKE` |
| TCL | Mengatur transaksi | `COMMIT`, `ROLLBACK` |

## 1.5 DDL: Data Definition Language

DDL digunakan untuk membuat, mengubah, dan menghapus struktur database. Struktur yang dimaksud adalah database, tabel, kolom, constraint, index, view, dan objek database lainnya.

Contoh perintah DDL:

```sql
CREATE DATABASE toko_online;
```

```sql
CREATE TABLE customers (
    id INT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE
);
```

```sql
ALTER TABLE customers
ADD phone VARCHAR(20);
```

```sql
DROP TABLE customers;
```

DDL biasanya digunakan saat membuat desain awal database atau ketika struktur aplikasi berubah.

## 1.6 DML: Data Manipulation Language

DML digunakan untuk mengelola isi data di dalam tabel. Perintah ini bekerja pada baris data, bukan struktur tabel.

Contoh perintah DML:

```sql
INSERT INTO customers (id, name, email)
VALUES (1, 'Andi', 'andi@example.com');
```

```sql
UPDATE customers
SET name = 'Andi Saputra'
WHERE id = 1;
```

```sql
DELETE FROM customers
WHERE id = 1;
```

DML harus digunakan dengan hati-hati, terutama `UPDATE` dan `DELETE`, karena dapat mengubah atau menghapus banyak data jika tidak memakai `WHERE`.

## 1.7 DQL: Data Query Language

DQL digunakan untuk mengambil atau membaca data dari database. Perintah utamanya adalah `SELECT`.

Contoh perintah DQL:

```sql
SELECT id, name, email
FROM customers
WHERE name = 'Andi';
```

DQL adalah kelompok perintah yang paling sering digunakan untuk laporan, pencarian data, dashboard, analisis, dan debugging isi tabel.

## 1.8 DCL: Data Control Language

DCL digunakan untuk mengatur hak akses pengguna terhadap database atau tabel.

Hak akses penting karena tidak semua pengguna boleh melakukan semua operasi. Misalnya, user laporan cukup diberi izin `SELECT`, sedangkan admin boleh melakukan `INSERT`, `UPDATE`, dan `DELETE`.

Jenis hak akses yang umum:

| Hak Akses | Fungsi |
|---|---|
| `SELECT` | Mengizinkan pengguna membaca data |
| `INSERT` | Mengizinkan pengguna menambah data |
| `UPDATE` | Mengizinkan pengguna mengubah data |
| `DELETE` | Mengizinkan pengguna menghapus data |
| `CREATE` | Mengizinkan pengguna membuat objek database |
| `ALTER` | Mengizinkan pengguna mengubah struktur objek |
| `DROP` | Mengizinkan pengguna menghapus objek database |

Contoh perintah DCL:

```sql
GRANT SELECT, INSERT
ON customers
TO staff_user;
```

Contoh memberi akses hanya untuk membaca data:

```sql
GRANT SELECT
ON customers
TO report_user;
```

```sql
REVOKE INSERT
ON customers
FROM staff_user;
```

Contoh mencabut akses membaca:

```sql
REVOKE SELECT
ON customers
FROM report_user;
```

DCL biasanya digunakan oleh database administrator untuk membatasi siapa yang boleh membaca, menambah, mengubah, atau menghapus data.

Catatan:

- Sintaks DCL dapat berbeda antar database.
- Pengaturan user, role, dan permission biasanya membutuhkan hak administrator.
- Pada aplikasi nyata, prinsip yang baik adalah memberi hak akses secukupnya sesuai kebutuhan.

## 1.9 TCL: Transaction Control Language

TCL digunakan untuk mengatur transaksi. Transaksi adalah kumpulan perintah SQL yang dianggap sebagai satu proses utuh.

Contoh perintah TCL:

```sql
BEGIN;

UPDATE products
SET stock = stock - 1
WHERE id = 10;

COMMIT;
```

Jika proses gagal, perubahan dapat dibatalkan:

```sql
ROLLBACK;
```

TCL penting digunakan pada proses yang tidak boleh setengah berhasil, misalnya pembayaran, transfer saldo, dan pengurangan stok barang.

## 1.10 Ringkasan Kelompok Perintah

| Kelompok | Fokus Utama | Digunakan Untuk |
|---|---|---|
| DDL | Struktur | Membuat database, membuat tabel, mengubah kolom, menghapus tabel |
| DML | Isi data | Menambah, mengubah, dan menghapus baris data |
| DQL | Pembacaan data | Mengambil data menggunakan `SELECT` |
| DCL | Hak akses | Memberi dan mencabut izin pengguna |
| TCL | Transaksi | Menyimpan atau membatalkan rangkaian perubahan |

---
