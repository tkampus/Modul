# Bagian 10: Window Function

## Yang Akan Dibahas

Materi ini membahas window function untuk menghitung nilai berdasarkan sekumpulan baris tanpa menggabungkan hasil menjadi satu baris. Peserta akan belajar ranking, penomoran baris, partisi data, dan running total.

## Tujuan Pembelajaran

Setelah mempelajari materi ini, peserta diharapkan mampu:

1. Menggunakan `ROW_NUMBER` untuk memberi nomor baris.
2. Menggunakan `RANK` untuk membuat peringkat.
3. Menggunakan `PARTITION BY` untuk membagi perhitungan per kelompok.
4. Membuat running total dengan window function.

Window function digunakan untuk menghitung nilai berdasarkan sekumpulan baris tanpa menggabungkan hasil menjadi satu baris seperti `GROUP BY`.

## 10.1 ROW_NUMBER

```sql
SELECT
    name,
    city,
    ROW_NUMBER() OVER (ORDER BY name) AS row_num
FROM customers;
```

## 10.2 RANK

```sql
SELECT
    name,
    price,
    RANK() OVER (ORDER BY price DESC) AS price_rank
FROM products;
```

## 10.3 PARTITION BY

```sql
SELECT
    category,
    name,
    price,
    RANK() OVER (
        PARTITION BY category
        ORDER BY price DESC
    ) AS rank_in_category
FROM products;
```

## 10.4 Running Total

```sql
SELECT
    order_date,
    total_amount,
    SUM(total_amount) OVER (
        ORDER BY order_date
    ) AS running_total
FROM order_summary;
```

---
