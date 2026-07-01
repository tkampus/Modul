# Bagian 6: Truthy, Falsy, dan Type Conversion

## Yang Akan Dibahas

JavaScript sering mengubah tipe data secara otomatis. Materi ini membahas nilai truthy dan falsy, penggunaan `typeof`, konversi eksplisit dengan `String()`, `Number()`, `Boolean()`, method `toString()`, serta parsing angka menggunakan `parseInt()` dan `parseFloat()`.

---

## Tujuan Pembelajaran

Setelah mempelajari materi ini, peserta diharapkan mampu:

1. Memahami nilai truthy dan falsy.
2. Mengecek tipe data menggunakan `typeof`.
3. Membedakan implicit conversion dan explicit conversion.
4. Mengubah tipe data menggunakan `String()`, `Number()`, `Boolean()`, dan `toString()`.
5. Menggunakan `parseInt()` dan `parseFloat()` dengan tepat.
6. Menghindari jebakan umum konversi tipe.

---

JavaScript adalah bahasa dengan dynamic typing. Artinya, satu variabel dapat menyimpan nilai dengan tipe yang berbeda pada waktu berbeda.

```javascript
let nilai = 100;
nilai = "seratus";

console.log(nilai);
```

Hasil:

```text
seratus
```

Karena tipe data dapat berubah, developer perlu memahami cara JavaScript membaca dan mengubah tipe data.

---

## 6.1 Truthy dan Falsy

Dalam kondisi seperti `if`, JavaScript akan mengubah nilai menjadi boolean.

Nilai falsy:

| Nilai | Keterangan |
|---|---|
| `false` | Boolean false |
| `0` | Angka nol |
| `-0` | Angka negatif nol |
| `0n` | BigInt nol |
| `""` | String kosong |
| `null` | Kosong secara sengaja |
| `undefined` | Belum memiliki nilai |
| `NaN` | Not a Number |

Selain nilai di atas, umumnya dianggap truthy.

### Contoh

```javascript
if ("JavaScript") {
  console.log("Truthy");
}

if ("") {
  console.log("Tidak tampil");
}
```

Hasil:

```text
Truthy
```

Array kosong dan object kosong adalah truthy.

```javascript
console.log(Boolean([]));
console.log(Boolean({}));
```

Hasil:

```text
true
true
```

---

## 6.2 Mengecek Tipe Data dengan typeof

`typeof` digunakan untuk mengecek tipe data sebuah nilai.

### Sintaks

```javascript
typeof nilai
```

### Contoh

```javascript
console.log(typeof "Halo");
console.log(typeof 100);
console.log(typeof true);
console.log(typeof undefined);
console.log(typeof null);
console.log(typeof []);
console.log(typeof {});
console.log(typeof function () {});
```

Hasil:

```text
string
number
boolean
undefined
object
object
object
function
```

Catatan penting:

- `typeof null` menghasilkan `object`. Ini adalah perilaku lama JavaScript.
- `typeof []` juga menghasilkan `object` karena array adalah object khusus.
- Untuk mengecek array, gunakan `Array.isArray()`.

```javascript
console.log(Array.isArray([]));
console.log(Array.isArray({}));
```

Hasil:

```text
true
false
```

---

## 6.3 Implicit Conversion

Implicit conversion adalah konversi tipe yang dilakukan JavaScript secara otomatis.

### Contoh

```javascript
console.log("5" + 2);
console.log("5" - 2);
console.log(true + 1);
console.log(false + 10);
```

Hasil:

```text
52
3
2
10
```

Pada operator `+`, jika salah satu nilai adalah string, JavaScript cenderung menggabungkan nilai sebagai string. Pada operator `-`, JavaScript mencoba mengubah string menjadi number.

Implicit conversion dapat membuat kode sulit diprediksi, sehingga sebaiknya gunakan explicit conversion ketika tipe data penting.

---

## 6.4 Explicit Conversion

Explicit conversion adalah konversi tipe yang dilakukan secara sengaja oleh developer.

### String ke Number

```javascript
const umurInput = "20";
const umur = Number(umurInput);

console.log(umur + 5);
console.log(typeof umur);
```

Hasil:

```text
25
number
```

### Number ke String

```javascript
const total = 100;
const teks = String(total);

console.log(teks);
console.log(typeof teks);
```

Hasil:

```text
100
string
```

### Nilai ke Boolean

```javascript
const input = "admin";
const adaInput = Boolean(input);

console.log(adaInput);
```

Hasil:

```text
true
```

---

## 6.5 String() dan toString()

`String()` dan `toString()` sama-sama dapat mengubah nilai menjadi string, tetapi cara pakainya berbeda.

### String()

```javascript
console.log(String(100));
console.log(String(true));
console.log(String(null));
console.log(String(undefined));
```

Hasil:

```text
100
true
null
undefined
```

`String()` aman digunakan pada `null` dan `undefined`.

### toString()

```javascript
const angka = 100;
const aktif = true;

console.log(angka.toString());
console.log(aktif.toString());
```

Hasil:

```text
100
true
```

Namun `toString()` akan error jika dipanggil dari `null` atau `undefined`.

```javascript
const data = null;

// console.log(data.toString()); // TypeError
console.log(String(data));
```

Hasil:

```text
null
```

Gunakan `String(nilai)` jika data berpotensi `null` atau `undefined`.

---

## 6.6 Number(), parseInt(), dan parseFloat()

`Number()` mengubah seluruh nilai menjadi number.

```javascript
console.log(Number("100"));
console.log(Number("100px"));
console.log(Number(""));
console.log(Number(true));
console.log(Number(false));
```

Hasil:

```text
100
NaN
0
1
0
```

`parseInt()` mengambil angka bulat dari awal string.

```javascript
console.log(parseInt("100px"));
console.log(parseInt("3.14"));
console.log(parseInt("px100"));
```

Hasil:

```text
100
3
NaN
```

`parseFloat()` mengambil angka decimal dari awal string.

```javascript
console.log(parseFloat("3.14"));
console.log(parseFloat("12.5kg"));
```

Hasil:

```text
3.14
12.5
```

Gunakan `Number()` jika seluruh input harus valid sebagai angka. Gunakan `parseInt()` atau `parseFloat()` jika ingin mengambil angka dari awal string.

---

## 6.7 Boolean()

`Boolean()` digunakan untuk melihat hasil konversi nilai ke boolean.

```javascript
console.log(Boolean("Halo"));
console.log(Boolean(""));
console.log(Boolean(1));
console.log(Boolean(0));
console.log(Boolean(null));
console.log(Boolean(undefined));
```

Hasil:

```text
true
false
true
false
false
false
```

Contoh penggunaan dalam validasi:

```javascript
const nama = "";

if (!nama) {
  console.log("Nama wajib diisi");
}
```

Hasil:

```text
Nama wajib diisi
```

---

## 6.8 == dan ===

Operator `==` melakukan konversi tipe otomatis.

```javascript
console.log(10 == "10");
console.log(10 === "10");
```

Hasil:

```text
true
false
```

Gunakan `===` dan `!==` agar perbandingan lebih aman dan mudah diprediksi.

---

## 6.9 Mengecek NaN

`NaN` berarti Not a Number.

```javascript
const hasil = Number("abc");

console.log(hasil);
console.log(Number.isNaN(hasil));
```

Hasil:

```text
NaN
true
```

Jangan membandingkan `NaN` dengan `NaN`.

```javascript
console.log(NaN === NaN);
```

Hasil:

```text
false
```

---

## Ringkasan

- Truthy dan falsy menentukan bagaimana nilai dibaca dalam kondisi boolean.
- `typeof` digunakan untuk mengecek tipe data dasar, tetapi array perlu dicek dengan `Array.isArray()`.
- `String()`, `Number()`, dan `Boolean()` digunakan untuk explicit conversion.
- `toString()` mengubah nilai menjadi string, tetapi tidak aman untuk `null` dan `undefined`.
- `parseInt()` dan `parseFloat()` membaca angka dari awal string.
- Gunakan `===` dan `!==` agar perbandingan tidak melakukan konversi tipe otomatis.

---

## Latihan

1. Cek hasil `typeof` dari string, number, boolean, object, array, function, `null`, dan `undefined`.
2. Cek hasil `Boolean()` dari `0`, `"0"`, `""`, `[]`, `{}`, `null`, dan `undefined`.
3. Ubah string `"25000"` menjadi number lalu tambahkan 5000.
4. Bandingkan hasil `5 == "5"` dan `5 === "5"`.
5. Coba `String(null)` dan bandingkan dengan `null.toString()`.
6. Buat validasi input kosong menggunakan konsep falsy.
