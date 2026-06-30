# Bagian 3: Operasi CRUD

## Yang Akan Dibahas

Materi ini membahas operasi utama untuk mengelola isi tabel, yaitu membuat data baru, membaca data, mengubah data, dan menghapus data. Bagian ini juga memperjelas hubungan antara CRUD, DML, dan DQL.

## Tujuan Pembelajaran

Setelah mempelajari materi ini, peserta diharapkan mampu:

1. Menambahkan data menggunakan `INSERT`.
2. Mengambil data menggunakan `SELECT`.
3. Mengubah data menggunakan `UPDATE`.
4. Menghapus data menggunakan `DELETE`.
5. Menggunakan `WHERE` agar perubahan data lebih aman.

## 3.1 Apa Itu CRUD?

CRUD adalah singkatan dari:

| CRUD | SQL | Kelompok |
|---|---|---|
| Create | `INSERT` | DML |
| Read | `SELECT` | DQL |
| Update | `UPDATE` | DML |
| Delete | `DELETE` | DML |

DML digunakan untuk menambah, mengubah, dan menghapus data. DQL digunakan untuk membaca data.

## 3.2 Contoh Tabel

Contoh pada materi ini menggunakan tabel `customers`.

```sql
CREATE TABLE customers (
    id INT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE,
    city VARCHAR(50),
    created_at DATE
);
```

## 3.3 INSERT: Menambahkan Data

`INSERT` digunakan untuk menambahkan baris baru ke dalam tabel.

```sql
INSERT INTO customers (id, name, email, city, created_at)
VALUES (1, 'Andi', 'andi@example.com', 'Jakarta', '2026-01-10');
```

Menambahkan beberapa data sekaligus:

```sql
INSERT INTO customers (id, name, email, city, created_at)
VALUES
    (2, 'Budi', 'budi@example.com', 'Bandung', '2026-01-12'),
    (3, 'Citra', 'citra@example.com', 'Surabaya', '2026-01-15'),
    (4, 'Dewi', 'dewi@example.com', 'Jakarta', '2026-01-18');
```

Jika kolom memiliki nilai default atau auto increment, kolom tersebut tidak harus selalu ditulis.

```sql
INSERT INTO customers (name, email, city, created_at)
VALUES ('Eka', 'eka@example.com', 'Medan', '2026-01-20');
```

Catatan: Contoh di atas hanya bisa digunakan jika `id` dibuat otomatis, misalnya dengan `AUTO_INCREMENT` atau `SERIAL`.

## 3.4 SELECT: Mengambil Semua Data

`SELECT` digunakan untuk membaca data dari tabel.

```sql
SELECT *
FROM customers;
```

Tanda `*` berarti mengambil semua kolom. Ini berguna saat belajar, tetapi pada aplikasi nyata sebaiknya pilih kolom yang dibutuhkan saja.

## 3.5 SELECT: Mengambil Kolom Tertentu

```sql
SELECT name, email, city
FROM customers;
```

Query di atas hanya mengambil kolom `name`, `email`, dan `city`.

## 3.6 SELECT dengan Alias

Alias digunakan untuk mengganti nama kolom pada hasil query.

```sql
SELECT
    name AS nama_customer,
    email AS alamat_email,
    city AS kota
FROM customers;
```

Alias membuat hasil laporan lebih mudah dibaca.

## 3.7 SELECT dengan DISTINCT

`DISTINCT` digunakan untuk menghilangkan data duplikat pada hasil query.

```sql
SELECT DISTINCT city
FROM customers;
```

Query di atas menampilkan daftar kota tanpa pengulangan.

## 3.8 UPDATE: Mengubah Data

`UPDATE` digunakan untuk mengubah data yang sudah ada.

```sql
UPDATE customers
SET city = 'Depok'
WHERE id = 1;
```

Mengubah lebih dari satu kolom:

```sql
UPDATE customers
SET
    city = 'Bogor',
    email = 'andi.baru@example.com'
WHERE id = 1;
```

Penting: Selalu gunakan `WHERE` saat melakukan `UPDATE`, kecuali memang ingin mengubah seluruh data.

Contoh berbahaya:

```sql
UPDATE customers
SET city = 'Jakarta';
```

Query di atas akan mengubah kota seluruh customer menjadi Jakarta.

## 3.9 DELETE: Menghapus Data

`DELETE` digunakan untuk menghapus baris data.

```sql
DELETE FROM customers
WHERE id = 3;
```

Menghapus data berdasarkan kondisi:

```sql
DELETE FROM customers
WHERE city = 'Surabaya';
```

Penting: Selalu gunakan `WHERE` saat melakukan `DELETE`, kecuali memang ingin menghapus seluruh isi tabel.

Contoh berbahaya:

```sql
DELETE FROM customers;
```

Query di atas akan menghapus semua data pada tabel `customers`, tetapi struktur tabel tetap ada.

## 3.10 Mengecek Data Sebelum UPDATE atau DELETE

Sebelum menjalankan `UPDATE` atau `DELETE`, biasakan cek data dengan `SELECT`.

```sql
SELECT *
FROM customers
WHERE id = 1;
```

Jika hasilnya sudah benar, baru jalankan:

```sql
UPDATE customers
SET city = 'Depok'
WHERE id = 1;
```

Kebiasaan ini membantu mencegah perubahan data yang salah.

## 3.11 Perbedaan DELETE, TRUNCATE, dan DROP

| Perintah | Kelompok | Fungsi |
|---|---|---|
| `DELETE` | DML | Menghapus baris data tertentu atau semua baris |
| `TRUNCATE` | DDL | Menghapus semua isi tabel dengan cepat |
| `DROP` | DDL | Menghapus tabel beserta strukturnya |

Contoh:

```sql
DELETE FROM customers
WHERE id = 1;
```

```sql
TRUNCATE TABLE customers;
```

```sql
DROP TABLE customers;
```

---
