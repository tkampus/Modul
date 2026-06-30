# Bagian 9: View

## Yang Akan Dibahas

Materi ini membahas view sebagai query yang disimpan di database. View membantu menyederhanakan query yang sering dipakai dan membuat laporan lebih mudah digunakan ulang.

## Tujuan Pembelajaran

Setelah mempelajari materi ini, peserta diharapkan mampu:

1. Menjelaskan fungsi view dalam SQL.
2. Membuat view dari query SELECT.
3. Menggunakan view untuk mengambil data.
4. Menghapus view yang tidak lagi dibutuhkan.

View adalah query yang disimpan sebagai objek database. View membantu menyederhanakan query yang sering digunakan.

## 9.1 Membuat View

```sql
CREATE VIEW order_summary AS
SELECT
    orders.id AS order_id,
    customers.name AS customer_name,
    orders.order_date,
    SUM(order_items.quantity * order_items.unit_price) AS total_amount
FROM orders
INNER JOIN customers
    ON orders.customer_id = customers.id
INNER JOIN order_items
    ON orders.id = order_items.order_id
GROUP BY orders.id, customers.name, orders.order_date;
```

## 9.2 Menggunakan View

```sql
SELECT *
FROM order_summary
WHERE total_amount > 1000000;
```

## 9.3 Menghapus View

```sql
DROP VIEW order_summary;
```

---
