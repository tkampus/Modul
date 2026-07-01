# Bagian 5: Aggregate Function dan Grouping

## Yang Akan Dibahas

Materi ini membahas cara membuat ringkasan data menggunakan **aggregate function** dan **pengelompokan data (grouping)**. Peserta akan belajar menghitung jumlah data, total nilai, rata-rata, nilai minimum, nilai maksimum, serta mengelompokkan data berdasarkan suatu kolom. Selain itu, peserta juga akan mempelajari cara memfilter hasil agregasi menggunakan klausa `HAVING`.

## Tujuan Pembelajaran

Setelah mempelajari materi ini, peserta diharapkan mampu:

1. Menjelaskan fungsi aggregate dalam SQL.
2. Menggunakan fungsi `COUNT()`, `SUM()`, `AVG()`, `MIN()`, `MAX()`, dan `ROUND()`.
3. Mengelompokkan data menggunakan `GROUP BY`.
4. Memfilter hasil agregasi menggunakan `HAVING`.
5. Membedakan penggunaan `WHERE` dan `HAVING`.

---

Aggregate function adalah fungsi SQL yang digunakan untuk menghasilkan **satu nilai ringkasan** dari sekumpulan data.

Contoh penggunaannya:

- Menghitung jumlah seluruh pengguna.
- Menghitung total transaksi.
- Menghitung rata-rata umur.
- Mengetahui nilai tertinggi dan terendah.

---

## 5.1 Fungsi Agregat Umum

| Fungsi | Kegunaan |
|---|---|
| `COUNT()` | Menghitung jumlah baris atau jumlah data yang tidak bernilai `NULL`. |
| `SUM()` | Menjumlahkan seluruh nilai pada kolom numerik. |
| `AVG()` | Menghitung nilai rata-rata pada kolom numerik. |
| `MIN()` | Mengambil nilai terkecil. |
| `MAX()` | Mengambil nilai terbesar. |
| `ROUND()` | Membulatkan angka ke jumlah digit desimal tertentu. |

### Contoh Data

Misalkan terdapat tabel **users** berikut.

| id | nama | gender | umur | kota |
|---:|---|:---:|---:|---|
| 1 | Andi | L | 21 | Bandung |
| 2 | Budi | L | 24 | Bandung |
| 3 | Siti | P | 20 | Jakarta |
| 4 | Rina | P | 23 | Bandung |
| 5 | Doni | L | 22 | Jakarta |

### COUNT()

Menghitung jumlah seluruh data.

```sql
SELECT COUNT(*) AS total_users
FROM users;
```

Hasil:

| total_users |
|---:|
| 5 |

---

### SUM()

Menjumlahkan seluruh nilai umur.

```sql
SELECT SUM(umur) AS total_umur
FROM users;
```

Hasil:

| total_umur |
|---:|
| 110 |

---

### AVG()

Menghitung rata-rata umur.

```sql
SELECT AVG(umur) AS rata_rata_umur
FROM users;
```

Hasil:

| rata_rata_umur |
|---:|
| 22.0 |

---

### ROUND()

Membulatkan hasil rata-rata menjadi dua angka di belakang koma.

```sql
SELECT ROUND(AVG(umur), 2) AS rata_rata_umur
FROM users;
```

Hasil:

| rata_rata_umur |
|---:|
| 22.00 |

---

### MIN()

Mengambil nilai umur terkecil.

```sql
SELECT MIN(umur) AS umur_termuda
FROM users;
```

Hasil:

| umur_termuda |
|---:|
| 20 |

---

### MAX()

Mengambil nilai umur terbesar.

```sql
SELECT MAX(umur) AS umur_tertua
FROM users;
```

Hasil:

| umur_tertua |
|---:|
| 24 |

---

## 5.2 GROUP BY

`GROUP BY` digunakan untuk **mengelompokkan data** berdasarkan nilai yang sama pada suatu kolom sehingga fungsi agregat dapat dihitung untuk setiap kelompok.

### Sintaks

```sql
SELECT kolom, aggregate_function(kolom_lain)
FROM nama_tabel
GROUP BY kolom;
```

### Contoh 1

Menghitung jumlah pengguna berdasarkan kota.

```sql
SELECT kota,
       COUNT(*) AS total_users
FROM users
GROUP BY kota;
```

Hasil:

| kota | total_users |
|---|---:|
| Bandung | 3 |
| Jakarta | 2 |

---

### Contoh 2

Menghitung rata-rata umur berdasarkan kota.

```sql
SELECT kota,
       ROUND(AVG(umur), 2) AS rata_rata_umur
FROM users
GROUP BY kota;
```

Hasil:

| kota | rata_rata_umur |
|---|---:|
| Bandung | 22.67 |
| Jakarta | 21.00 |

---

### Contoh 3

Menghitung jumlah pengguna berdasarkan gender.

```sql
SELECT gender,
       COUNT(*) AS total_users
FROM users
GROUP BY gender;
```

Hasil:

| gender | total_users |
|:---:|---:|
| L | 3 |
| P | 2 |

---

## 5.3 HAVING

`HAVING` digunakan untuk **memfilter hasil agregasi**.

Berbeda dengan `WHERE`, klausa `HAVING` dijalankan setelah proses `GROUP BY`.

### Sintaks

```sql
SELECT kolom,
       COUNT(*)
FROM nama_tabel
GROUP BY kolom
HAVING kondisi;
```

### Contoh

Menampilkan kota yang memiliki lebih dari dua pengguna.

```sql
SELECT kota,
       COUNT(*) AS total_users
FROM users
GROUP BY kota
HAVING COUNT(*) > 2;
```

Hasil:

| kota | total_users |
|---|---:|
| Bandung | 3 |

---

## 5.4 Perbedaan WHERE dan HAVING

Meskipun sama-sama digunakan untuk memfilter data, `WHERE` dan `HAVING` memiliki fungsi yang berbeda.

| WHERE | HAVING |
|---|---|
| Memfilter data sebelum proses agregasi atau pengelompokan. | Memfilter hasil setelah proses agregasi atau pengelompokan. |
| Tidak dapat menggunakan fungsi agregat seperti `COUNT()` atau `SUM()`. | Dapat menggunakan fungsi agregat. |

### Contoh WHERE

Menghitung jumlah pengguna yang berumur di atas 21 tahun.

```sql
SELECT COUNT(*) AS total_users
FROM users
WHERE umur > 21;
```

---

### Contoh HAVING

Menghitung jumlah pengguna setiap kota, kemudian hanya menampilkan kota yang memiliki lebih dari dua pengguna.

```sql
SELECT kota,
       COUNT(*) AS total_users
FROM users
GROUP BY kota
HAVING COUNT(*) > 2;
```

