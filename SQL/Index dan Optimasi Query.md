# Bagian 12: Index dan Optimasi Query

## Yang Akan Dibahas

Materi ini membahas index dan dasar optimasi query agar proses pencarian data lebih cepat. Peserta juga akan belajar kapan index perlu dibuat dan bagaimana membaca query plan sederhana.

## Tujuan Pembelajaran

Setelah mempelajari materi ini, peserta diharapkan mampu:

1. Menjelaskan fungsi index dalam database.
2. Membuat index pada kolom yang sering digunakan.
3. Menentukan kapan index perlu dan tidak perlu digunakan.
4. Membaca query plan dasar menggunakan `EXPLAIN`.

## 12.1 Apa Itu Index?

Index adalah struktur data yang membantu database mencari data lebih cepat. Index mirip daftar isi pada buku.

Tanpa index, database mungkin perlu membaca seluruh tabel. Dengan index, database dapat menemukan data secara lebih efisien.

## 12.2 Membuat Index

```sql
CREATE INDEX idx_customers_city
ON customers(city);
```

## 12.3 Index pada Foreign Key

```sql
CREATE INDEX idx_orders_customer_id
ON orders(customer_id);
```

## 12.4 Kapan Menggunakan Index?

Gunakan index pada kolom yang sering dipakai untuk:

- `WHERE`
- `JOIN`
- `ORDER BY`
- `GROUP BY`

Namun, jangan membuat index terlalu banyak karena dapat memperlambat proses `INSERT`, `UPDATE`, dan `DELETE`.

## 12.5 Membaca Query Plan

Pada PostgreSQL:

```sql
EXPLAIN ANALYZE
SELECT *
FROM customers
WHERE city = 'Jakarta';
```

Pada MySQL:

```sql
EXPLAIN
SELECT *
FROM customers
WHERE city = 'Jakarta';
```

Query plan membantu melihat apakah database melakukan full table scan atau menggunakan index.

---
