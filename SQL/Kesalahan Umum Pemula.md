# Bagian 15: Kesalahan Umum Pemula

## Yang Akan Dibahas

Materi ini membahas kesalahan yang sering dilakukan pemula saat menulis query SQL, seperti lupa `WHERE`, terlalu sering menggunakan `SELECT *`, salah memahami JOIN, dan keliru menangani `NULL`.

## Tujuan Pembelajaran

Setelah mempelajari materi ini, peserta diharapkan mampu:

1. Mengenali kesalahan umum dalam penggunaan SQL.
2. Menghindari query yang dapat merusak atau mengubah banyak data tanpa sengaja.
3. Menulis query yang lebih aman, jelas, dan sesuai kebutuhan.

## 15.1 Lupa WHERE saat UPDATE atau DELETE

```sql
UPDATE customers
SET city = 'Jakarta';
```

Query di atas akan mengubah semua data customer. Biasakan cek dengan `SELECT` terlebih dahulu.

## 15.2 Menggunakan SELECT * Terus-menerus

`SELECT *` praktis untuk belajar, tetapi pada aplikasi nyata lebih baik pilih kolom yang dibutuhkan.

```sql
SELECT name, email
FROM customers;
```

## 15.3 Salah Memahami JOIN

Jika hasil JOIN menjadi terlalu banyak, kemungkinan:

- Kondisi `ON` salah.
- Relasi tabel tidak tepat.
- Ada data duplikat.

## 15.4 Mengabaikan NULL

`NULL` bukan angka nol dan bukan teks kosong. Untuk mengecek `NULL`, gunakan:

```sql
SELECT *
FROM customers
WHERE phone IS NULL;
```

Untuk mengecek bukan `NULL`:

```sql
SELECT *
FROM customers
WHERE phone IS NOT NULL;
```

---
