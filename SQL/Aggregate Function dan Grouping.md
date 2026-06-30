# Bagian 5: Aggregate Function dan Grouping

## Yang Akan Dibahas

Materi ini membahas cara membuat ringkasan data menggunakan aggregate function dan pengelompokan data. Peserta akan belajar menghitung jumlah data, total, rata-rata, nilai minimum, nilai maksimum, serta memfilter hasil agregasi.

## Tujuan Pembelajaran

Setelah mempelajari materi ini, peserta diharapkan mampu:

1. Menjelaskan fungsi aggregate dalam SQL.
2. Menggunakan `COUNT`, `SUM`, `AVG`, `MIN`, dan `MAX`.
3. Mengelompokkan data menggunakan `GROUP BY`.
4. Memfilter hasil agregasi menggunakan `HAVING`.

Aggregate function digunakan untuk menghitung ringkasan data.

## 5.1 Fungsi Agregat Umum

| Fungsi | Kegunaan |
|---|---|
| `COUNT()` | Menghitung jumlah baris |
| `SUM()` | Menjumlahkan nilai |
| `AVG()` | Menghitung rata-rata |
| `MIN()` | Mengambil nilai terkecil |
| `MAX()` | Mengambil nilai terbesar |

Contoh:

```sql
SELECT COUNT(*) AS total_customer
FROM customers;
```

```sql
SELECT AVG(price) AS rata_rata_harga
FROM products;
```

## 5.2 GROUP BY

```sql
SELECT city, COUNT(*) AS total_customer
FROM customers
GROUP BY city;
```

## 5.3 HAVING

`HAVING` digunakan untuk memfilter hasil agregasi.

```sql
SELECT city, COUNT(*) AS total_customer
FROM customers
GROUP BY city
HAVING COUNT(*) > 1;
```

Perbedaan `WHERE` dan `HAVING`:

- `WHERE` memfilter data sebelum dikelompokkan.
- `HAVING` memfilter hasil setelah agregasi.

---
