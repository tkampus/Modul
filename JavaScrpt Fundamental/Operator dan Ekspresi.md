# Bagian 5: Operator dan Ekspresi

## Yang Akan Dibahas

Operator digunakan untuk melakukan operasi pada nilai, seperti menghitung angka, membandingkan data, atau menggabungkan kondisi.

---

## Tujuan Pembelajaran

Setelah mempelajari modul ini, peserta diharapkan mampu:

1. Menggunakan operator aritmatika.
2. Menggunakan operator assignment.
3. Membandingkan nilai dengan operator perbandingan.
4. Menggabungkan kondisi dengan operator logika.
5. Menggunakan ternary operator dan nullish coalescing.

---

## 5.1 Operator Aritmatika

| Operator | Fungsi | Contoh |
|---|---|---|
| `+` | Penjumlahan | `10 + 5` |
| `-` | Pengurangan | `10 - 5` |
| `*` | Perkalian | `10 * 5` |
| `/` | Pembagian | `10 / 5` |
| `%` | Sisa bagi | `10 % 3` |
| `**` | Pangkat | `2 ** 3` |

Contoh:

```javascript
const a = 10;
const b = 3;

console.log(a + b);
console.log(a % b);
console.log(a ** b);
```

---

## 5.2 Operator Assignment

Assignment digunakan untuk memberi atau mengubah nilai.

```javascript
let skor = 10;

skor += 5; // skor = skor + 5
skor -= 2;
skor *= 3;
skor /= 2;

console.log(skor);
```

---

## 5.3 Operator Perbandingan

| Operator | Fungsi |
|---|---|
| `==` | Sama nilai, dengan konversi tipe |
| `===` | Sama nilai dan tipe |
| `!=` | Tidak sama nilai |
| `!==` | Tidak sama nilai atau tipe |
| `>` | Lebih besar |
| `<` | Lebih kecil |
| `>=` | Lebih besar atau sama |
| `<=` | Lebih kecil atau sama |

Gunakan `===` dan `!==` untuk menghindari konversi tipe yang tidak terduga.

```javascript
console.log(10 == "10"); // true
console.log(10 === "10"); // false
```

---

## 5.4 Operator Logika

| Operator | Fungsi |
|---|---|
| `&&` | AND, benar jika semua kondisi benar |
| `||` | OR, benar jika salah satu kondisi benar |
| `!` | NOT, membalik nilai boolean |

Contoh:

```javascript
const umur = 20;
const punyaKtp = true;

console.log(umur >= 17 && punyaKtp);
console.log(umur < 17 || punyaKtp);
console.log(!punyaKtp);
```

---

## 5.5 Ternary Operator

Ternary adalah bentuk singkat dari `if else`.

```javascript
const umur = 18;
const status = umur >= 17 ? "Boleh membuat KTP" : "Belum boleh";

console.log(status);
```

Gunakan ternary untuk kondisi sederhana.

---

## 5.6 Nullish Coalescing

Operator `??` digunakan untuk memberi nilai default jika nilai kiri adalah `null` atau `undefined`.

```javascript
const namaInput = null;
const nama = namaInput ?? "Guest";

console.log(nama);
```

Berbeda dengan `||`, operator `??` tidak menganggap `0`, `false`, atau string kosong sebagai nilai kosong.

```javascript
const stok = 0;

console.log(stok || 10); // 10
console.log(stok ?? 10); // 0
```

---

## Ringkasan

- Operator digunakan untuk aritmatika, assignment, perbandingan, dan logika.
- Gunakan `===` dan `!==` agar perbandingan lebih aman.
- Ternary dan nullish coalescing membantu menulis ekspresi kondisi sederhana.

---

## Latihan

1. Hitung luas persegi panjang dari `panjang` dan `lebar`.
2. Buat pengecekan apakah seseorang boleh masuk bioskop berdasarkan umur.
3. Gunakan ternary untuk menentukan nilai lulus atau tidak.
4. Gunakan `??` untuk memberi nilai default pada data yang belum tersedia.
