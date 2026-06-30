# Bagian 4: Filter, Sorting, dan Operator

## Yang Akan Dibahas

Materi ini membahas cara mengambil data secara lebih spesifik menggunakan `SELECT`, `WHERE`, operator, pengurutan, dan pembatasan jumlah data. Bagian ini penting agar query tidak hanya menampilkan semua data, tetapi dapat mengambil data sesuai kebutuhan.

## Tujuan Pembelajaran

Setelah mempelajari materi ini, peserta diharapkan mampu:

1. Menulis query `SELECT` dengan kolom tertentu.
2. Menggunakan `WHERE` untuk memfilter data.
3. Memahami operator perbandingan dan logika.
4. Menggunakan `BETWEEN`, `IN`, `LIKE`, `IS NULL`, dan `IS NOT NULL`.
5. Mengurutkan data dengan `ORDER BY`.
6. Membatasi jumlah hasil query dengan `LIMIT` dan `OFFSET`.

## 4.1 Struktur Dasar SELECT

`SELECT` digunakan untuk mengambil data dari tabel.

```sql
SELECT kolom_1, kolom_2
FROM nama_tabel;
```

Contoh:

```sql
SELECT name, email
FROM customers;
```

Mengambil semua kolom:

```sql
SELECT *
FROM customers;
```

Catatan: `SELECT *` praktis untuk belajar, tetapi kurang ideal untuk aplikasi nyata karena mengambil semua kolom, termasuk kolom yang tidak dibutuhkan.

## 4.2 SELECT dengan Alias

Alias digunakan untuk memberi nama sementara pada kolom hasil query.

```sql
SELECT
    name AS nama,
    email AS alamat_email
FROM customers;
```

Alias juga dapat digunakan pada hasil perhitungan.

```sql
SELECT
    name,
    price,
    stock,
    price * stock AS total_nilai_stok
FROM products;
```

## 4.3 SELECT DISTINCT

`DISTINCT` digunakan untuk menampilkan data unik.

```sql
SELECT DISTINCT city
FROM customers;
```

Jika ada banyak customer dari kota yang sama, nama kota hanya muncul satu kali.

## 4.4 Filter dengan WHERE

`WHERE` digunakan untuk mengambil data yang memenuhi kondisi tertentu.

```sql
SELECT *
FROM customers
WHERE city = 'Jakarta';
```

Query di atas hanya menampilkan customer yang berada di Jakarta.

Contoh dengan angka:

```sql
SELECT *
FROM products
WHERE price >= 100000;
```

Contoh dengan tanggal:

```sql
SELECT *
FROM orders
WHERE order_date >= '2026-01-01';
```

## 4.5 Operator Perbandingan

| Operator | Fungsi | Contoh |
|---|---|---|
| `=` | Sama dengan | `city = 'Jakarta'` |
| `<>` atau `!=` | Tidak sama dengan | `city <> 'Jakarta'` |
| `>` | Lebih besar | `price > 100000` |
| `<` | Lebih kecil | `price < 100000` |
| `>=` | Lebih besar atau sama dengan | `stock >= 10` |
| `<=` | Lebih kecil atau sama dengan | `stock <= 5` |

Contoh:

```sql
SELECT *
FROM products
WHERE stock <= 5;
```

## 4.6 Operator Logika AND, OR, dan NOT

`AND` digunakan jika semua kondisi harus benar.

```sql
SELECT *
FROM products
WHERE price >= 100000
  AND stock > 0;
```

`OR` digunakan jika salah satu kondisi boleh benar.

```sql
SELECT *
FROM customers
WHERE city = 'Jakarta'
   OR city = 'Bandung';
```

`NOT` digunakan untuk membalik kondisi.

```sql
SELECT *
FROM products
WHERE NOT category = 'Elektronik';
```

Gunakan tanda kurung jika kondisi mulai kompleks.

```sql
SELECT *
FROM products
WHERE category = 'Elektronik'
  AND (price < 1000000 OR stock > 10);
```

## 4.7 BETWEEN

`BETWEEN` digunakan untuk mencari nilai dalam rentang tertentu.

```sql
SELECT *
FROM products
WHERE price BETWEEN 50000 AND 200000;
```

Query di atas setara dengan:

```sql
SELECT *
FROM products
WHERE price >= 50000
  AND price <= 200000;
```

`BETWEEN` juga dapat digunakan pada tanggal.

```sql
SELECT *
FROM orders
WHERE order_date BETWEEN '2026-01-01' AND '2026-01-31';
```

## 4.8 IN

`IN` digunakan untuk mencocokkan data dengan beberapa pilihan nilai.

```sql
SELECT *
FROM customers
WHERE city IN ('Jakarta', 'Bandung', 'Surabaya');
```

Query di atas lebih ringkas daripada menulis banyak `OR`.

```sql
SELECT *
FROM customers
WHERE city = 'Jakarta'
   OR city = 'Bandung'
   OR city = 'Surabaya';
```

## 4.9 LIKE

`LIKE` digunakan untuk pencarian pola teks.

```sql
SELECT *
FROM customers
WHERE name LIKE 'A%';
```

Penjelasan pola:

| Pola | Arti |
|---|---|
| `'A%'` | Diawali huruf A |
| `'%a'` | Diakhiri huruf a |
| `'%di%'` | Mengandung teks di |
| `'_udi'` | Satu karakter bebas di depan, misalnya Budi |

Contoh:

```sql
SELECT *
FROM customers
WHERE email LIKE '%@gmail.com';
```

Catatan: Pada beberapa database, `LIKE` membedakan huruf besar dan kecil. PostgreSQL menyediakan `ILIKE` untuk pencarian yang tidak sensitif terhadap huruf besar kecil.

```sql
SELECT *
FROM customers
WHERE name ILIKE 'andi%';
```

## 4.10 IS NULL dan IS NOT NULL

`NULL` berarti data kosong atau belum diketahui. `NULL` tidak sama dengan `0` dan tidak sama dengan teks kosong.

Cara yang benar untuk mencari `NULL`:

```sql
SELECT *
FROM customers
WHERE phone IS NULL;
```

Cara mencari data yang tidak `NULL`:

```sql
SELECT *
FROM customers
WHERE phone IS NOT NULL;
```

Jangan menulis seperti ini:

```sql
SELECT *
FROM customers
WHERE phone = NULL;
```

Query tersebut tidak tepat karena `NULL` harus dicek dengan `IS NULL`.

## 4.11 ORDER BY

`ORDER BY` digunakan untuk mengurutkan hasil query.

Urut dari kecil ke besar:

```sql
SELECT *
FROM products
ORDER BY price ASC;
```

Urut dari besar ke kecil:

```sql
SELECT *
FROM products
ORDER BY price DESC;
```

Mengurutkan berdasarkan lebih dari satu kolom:

```sql
SELECT *
FROM products
ORDER BY category ASC, price DESC;
```

Query di atas mengurutkan data berdasarkan kategori, lalu harga tertinggi dalam setiap kategori.

## 4.12 LIMIT dan OFFSET

`LIMIT` digunakan untuk membatasi jumlah data yang ditampilkan.

```sql
SELECT *
FROM products
ORDER BY price DESC
LIMIT 5;
```

Query di atas menampilkan 5 produk termahal.

`OFFSET` digunakan untuk melewati sejumlah baris.

```sql
SELECT *
FROM products
ORDER BY id ASC
LIMIT 10 OFFSET 10;
```

Query di atas biasanya digunakan untuk pagination. Artinya, ambil 10 data setelah melewati 10 data pertama.

## 4.13 Urutan Penulisan Query

Urutan umum penulisan query:

```sql
SELECT kolom
FROM tabel
WHERE kondisi
ORDER BY kolom
LIMIT jumlah;
```

Contoh lengkap:

```sql
SELECT
    name,
    email,
    city
FROM customers
WHERE city IN ('Jakarta', 'Bandung')
ORDER BY name ASC
LIMIT 10;
```

## 4.14 Urutan Eksekusi Query

Walaupun `SELECT` ditulis paling atas, database biasanya memproses query dengan urutan konsep berikut:

1. `FROM`
2. `WHERE`
3. `SELECT`
4. `ORDER BY`
5. `LIMIT`

Memahami urutan ini membantu saat query mulai kompleks.

---
