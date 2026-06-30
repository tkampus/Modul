# Bagian 11: Transaction

## Yang Akan Dibahas

Materi ini membahas TCL atau Transaction Control Language, yaitu kelompok perintah SQL untuk mengatur transaksi. Peserta akan belajar menggunakan `BEGIN`, `COMMIT`, `ROLLBACK`, dan memahami prinsip ACID.

## Tujuan Pembelajaran

Setelah mempelajari materi ini, peserta diharapkan mampu:

1. Menjelaskan fungsi transaction dalam database.
2. Menjelaskan peran TCL dalam SQL.
3. Menggunakan `BEGIN`, `COMMIT`, dan `ROLLBACK`.
4. Memahami prinsip ACID.
5. Menentukan kapan transaction perlu digunakan.

## 11.1 Apa Itu Transaction?

Transaction adalah kumpulan perintah SQL yang dijalankan sebagai satu proses utuh. Jika semua perintah berhasil, perubahan disimpan. Jika ada kesalahan, perubahan dapat dibatalkan.

Contoh kasus yang membutuhkan transaction:

- Proses pembayaran.
- Transfer saldo antar rekening.
- Pengurangan stok setelah order dibuat.
- Pembuatan order dan detail order sekaligus.

Transaction penting karena beberapa proses tidak boleh berhasil sebagian.

## 11.2 Apa Itu TCL?

TCL adalah kelompok perintah SQL untuk mengontrol transaction.

| Perintah | Fungsi |
|---|---|
| `BEGIN` atau `START TRANSACTION` | Memulai transaksi |
| `COMMIT` | Menyimpan semua perubahan dalam transaksi |
| `ROLLBACK` | Membatalkan semua perubahan dalam transaksi |
| `SAVEPOINT` | Membuat titik simpan sementara di dalam transaksi |

## 11.3 Contoh Transaction Sederhana

```sql
BEGIN;

UPDATE products
SET stock = stock - 2
WHERE id = 1;

INSERT INTO orders (id, customer_id, order_date, status)
VALUES (10, 1, '2026-02-01', 'paid');

COMMIT;
```

Jika semua query berhasil, `COMMIT` akan menyimpan perubahan.

## 11.4 Membatalkan Transaction

Jika terjadi kesalahan, gunakan `ROLLBACK`.

```sql
BEGIN;

UPDATE products
SET stock = stock - 2
WHERE id = 1;

INSERT INTO orders (id, customer_id, order_date, status)
VALUES (10, 999, '2026-02-01', 'paid');

ROLLBACK;
```

Pada contoh di atas, jika `customer_id = 999` tidak valid, transaksi dapat dibatalkan sehingga stok produk tidak ikut berkurang.

## 11.5 SAVEPOINT

`SAVEPOINT` digunakan untuk membuat titik simpan sementara di dalam transaction.

```sql
BEGIN;

UPDATE products
SET stock = stock - 1
WHERE id = 1;

SAVEPOINT after_stock_update;

INSERT INTO orders (id, customer_id, order_date, status)
VALUES (11, 1, '2026-02-02', 'paid');

ROLLBACK TO after_stock_update;

COMMIT;
```

Dengan `SAVEPOINT`, kita dapat membatalkan sebagian proses tanpa membatalkan seluruh transaction.

## 11.6 Prinsip ACID

| Prinsip | Penjelasan |
|---|---|
| Atomicity | Semua operasi berhasil atau semua dibatalkan |
| Consistency | Data tetap valid sesuai aturan database |
| Isolation | Transaksi tidak saling mengganggu |
| Durability | Data tetap tersimpan setelah transaksi selesai |

## 11.7 Kapan Menggunakan Transaction?

Gunakan transaction ketika:

- Ada lebih dari satu query yang harus dianggap sebagai satu proses.
- Data tidak boleh berubah sebagian.
- Query berhubungan dengan uang, stok, order, atau data penting.
- Ada kemungkinan salah satu query gagal.

Contoh proses yang sebaiknya memakai transaction:

1. Kurangi stok produk.
2. Buat data order.
3. Buat detail order.
4. Simpan data pembayaran.
5. Jika semua berhasil, jalankan `COMMIT`.
6. Jika salah satu gagal, jalankan `ROLLBACK`.

---
