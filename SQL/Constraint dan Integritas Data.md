# Bagian 7: Constraint dan Integritas Data

## Yang Akan Dibahas

Materi ini membahas constraint sebagai aturan yang menjaga data tetap valid, konsisten, dan sesuai relasi antar tabel. Peserta akan mempelajari primary key, foreign key, not null, unique, dan check.

## Tujuan Pembelajaran

Setelah mempelajari materi ini, peserta diharapkan mampu:

1. Menjelaskan fungsi constraint pada database.
2. Membuat primary key dan foreign key.
3. Menggunakan constraint `NOT NULL`, `UNIQUE`, dan `CHECK`.
4. Memahami peran constraint dalam menjaga integritas data.

Constraint digunakan untuk menjaga kualitas dan konsistensi data.

## 7.1 Primary Key

```sql
CREATE TABLE categories (
    id INT PRIMARY KEY,
    name VARCHAR(100) NOT NULL
);
```

## 7.2 Foreign Key

```sql
CREATE TABLE products (
    id INT PRIMARY KEY,
    category_id INT,
    name VARCHAR(100) NOT NULL,
    price DECIMAL(12, 2),
    FOREIGN KEY (category_id) REFERENCES categories(id)
);
```

## 7.3 NOT NULL

```sql
CREATE TABLE users (
    id INT PRIMARY KEY,
    username VARCHAR(50) NOT NULL
);
```

## 7.4 UNIQUE

```sql
CREATE TABLE users (
    id INT PRIMARY KEY,
    email VARCHAR(100) UNIQUE
);
```

## 7.5 CHECK

```sql
CREATE TABLE products (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    price DECIMAL(12, 2) CHECK (price >= 0)
);
```

---
