# Bagian 13: Normalisasi Database

## Yang Akan Dibahas

Materi ini membahas normalisasi database, yaitu proses merancang tabel agar data tidak berulang secara berlebihan dan tetap mudah dijaga konsistensinya.

## Tujuan Pembelajaran

Setelah mempelajari materi ini, peserta diharapkan mampu:

1. Menjelaskan tujuan normalisasi database.
2. Mengenali masalah pada tabel yang tidak ternormalisasi.
3. Memahami konsep dasar 1NF, 2NF, dan 3NF.
4. Merancang tabel yang lebih rapi dan fleksibel.

Normalisasi adalah proses merancang tabel agar data tidak berulang secara berlebihan dan tetap konsisten.

## 13.1 Masalah Data Tidak Ternormalisasi

Contoh tabel yang kurang baik:

| order_id | customer_name | product_1 | product_2 |
|---:|---|---|---|
| 1 | Andi | Keyboard | Mouse |

Masalah:

- Sulit menambah produk ketiga.
- Data customer bisa berulang.
- Query menjadi tidak fleksibel.

## 13.2 Bentuk yang Lebih Baik

Gunakan tabel terpisah:

- `customers`
- `orders`
- `products`
- `order_items`

Struktur ini lebih fleksibel karena satu order dapat memiliki banyak item tanpa membuat kolom baru.

## 13.3 Bentuk Normal Umum

| Bentuk Normal | Inti Aturan |
|---|---|
| 1NF | Setiap kolom berisi nilai atomik, bukan daftar |
| 2NF | Setiap kolom non-key bergantung pada seluruh primary key |
| 3NF | Tidak ada ketergantungan antar kolom non-key |

---
