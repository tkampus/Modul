# Bagian 6: Relasi dan JOIN

## Yang Akan Dibahas

Materi ini membahas cara menghubungkan data dari beberapa tabel menggunakan relasi dan JOIN. Peserta akan belajar membaca skema relasi serta menggunakan beberapa jenis JOIN sesuai kebutuhan.

## Tujuan Pembelajaran

Setelah mempelajari materi ini, peserta diharapkan mampu:

1. Memahami relasi antar tabel menggunakan foreign key.
2. Menggunakan `INNER JOIN`, `LEFT JOIN`, `RIGHT JOIN`, dan `FULL OUTER JOIN`.
3. Menggabungkan lebih dari dua tabel dalam satu query.
4. Membaca hasil JOIN dan memahami perbedaannya.

## 6.1 Contoh Skema Relasi

```sql
CREATE TABLE products (
    id INT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    category VARCHAR(50),
    price DECIMAL(12, 2),
    stock INT
);

CREATE TABLE orders (
    id INT PRIMARY KEY,
    customer_id INT,
    order_date DATE,
    status VARCHAR(30),
    FOREIGN KEY (customer_id) REFERENCES customers(id)
);

CREATE TABLE order_items (
    id INT PRIMARY KEY,
    order_id INT,
    product_id INT,
    quantity INT,
    unit_price DECIMAL(12, 2),
    FOREIGN KEY (order_id) REFERENCES orders(id),
    FOREIGN KEY (product_id) REFERENCES products(id)
);
```

Relasi:

- Satu customer dapat memiliki banyak order.
- Satu order dapat memiliki banyak item.
- Satu produk dapat muncul di banyak order item.

## 6.2 INNER JOIN

Mengambil data yang cocok di kedua tabel.

```sql
SELECT
    orders.id AS order_id,
    customers.name AS customer_name,
    orders.order_date
FROM orders
INNER JOIN customers
    ON orders.customer_id = customers.id;
```

## 6.3 LEFT JOIN

Mengambil semua data dari tabel kiri, meskipun tidak punya pasangan di tabel kanan.

```sql
SELECT
    customers.name,
    orders.id AS order_id,
    orders.order_date
FROM customers
LEFT JOIN orders
    ON customers.id = orders.customer_id;
```

## 6.4 RIGHT JOIN

Mengambil semua data dari tabel kanan, meskipun tidak punya pasangan di tabel kiri.

```sql
SELECT
    customers.name,
    orders.id AS order_id
FROM customers
RIGHT JOIN orders
    ON customers.id = orders.customer_id;
```

## 6.5 FULL OUTER JOIN

Mengambil semua data dari kedua tabel, baik yang cocok maupun tidak.

```sql
SELECT
    customers.name,
    orders.id AS order_id
FROM customers
FULL OUTER JOIN orders
    ON customers.id = orders.customer_id;
```

Catatan: MySQL tidak mendukung `FULL OUTER JOIN` secara langsung. Biasanya diganti dengan kombinasi `LEFT JOIN`, `RIGHT JOIN`, dan `UNION`.

## 6.6 JOIN Lebih dari Dua Tabel

```sql
SELECT
    orders.id AS order_id,
    customers.name AS customer_name,
    products.name AS product_name,
    order_items.quantity,
    order_items.unit_price,
    order_items.quantity * order_items.unit_price AS subtotal
FROM orders
INNER JOIN customers
    ON orders.customer_id = customers.id
INNER JOIN order_items
    ON orders.id = order_items.order_id
INNER JOIN products
    ON order_items.product_id = products.id;
```

---
