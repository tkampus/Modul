# Bagian 8: Subquery dan CTE

## Yang Akan Dibahas

Materi ini membahas subquery dan Common Table Expression untuk membuat query yang lebih fleksibel dan mudah dibaca. Peserta akan belajar menaruh query di dalam query lain dan memecah query kompleks menjadi bagian yang lebih rapi.

## Tujuan Pembelajaran

Setelah mempelajari materi ini, peserta diharapkan mampu:

1. Menggunakan subquery pada `WHERE` dan `FROM`.
2. Menggunakan `EXISTS` untuk mengecek keberadaan data terkait.
3. Membuat CTE menggunakan `WITH`.
4. Menulis query kompleks dengan struktur yang lebih mudah dipahami.

## 8.1 Subquery di WHERE

```sql
SELECT *
FROM products
WHERE price > (
    SELECT AVG(price)
    FROM products
);
```

Query di atas menampilkan produk dengan harga di atas rata-rata.

## 8.2 Subquery di FROM

```sql
SELECT city, total_customer
FROM (
    SELECT city, COUNT(*) AS total_customer
    FROM customers
    GROUP BY city
) AS customer_summary
WHERE total_customer > 1;
```

## 8.3 EXISTS

```sql
SELECT *
FROM customers
WHERE EXISTS (
    SELECT 1
    FROM orders
    WHERE orders.customer_id = customers.id
);
```

Query di atas mengambil customer yang pernah melakukan order.

## 8.4 Common Table Expression

CTE membuat query kompleks lebih mudah dibaca.

```sql
WITH sales_summary AS (
    SELECT
        orders.id AS order_id,
        customers.name AS customer_name,
        SUM(order_items.quantity * order_items.unit_price) AS total_amount
    FROM orders
    INNER JOIN customers
        ON orders.customer_id = customers.id
    INNER JOIN order_items
        ON orders.id = order_items.order_id
    GROUP BY orders.id, customers.name
)
SELECT *
FROM sales_summary
WHERE total_amount >= 500000;
```

---
