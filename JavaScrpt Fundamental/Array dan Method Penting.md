# Bagian 9: Array dan Method Penting

## Yang Akan Dibahas

Array digunakan untuk menyimpan banyak data dalam satu variabel. Data dalam array memiliki urutan dan dapat diakses melalui index.

---

## Tujuan Pembelajaran

Setelah mempelajari modul ini, peserta diharapkan mampu:

1. Membuat dan mengakses array.
2. Menambah, mengubah, dan menghapus data array.
3. Melakukan perulangan pada array.
4. Menggunakan method array penting seperti `map`, `filter`, `reduce`, dan `find`.

---

## 9.1 Membuat Array

```javascript
const buah = ["Apel", "Jeruk", "Mangga"];

console.log(buah);
```

Index array dimulai dari 0.

```javascript
console.log(buah[0]); // Apel
console.log(buah[1]); // Jeruk
```

---

## 9.2 Mengubah Data Array

```javascript
const buah = ["Apel", "Jeruk", "Mangga"];

buah[1] = "Pisang";

console.log(buah);
```

Walaupun menggunakan `const`, isi array tetap dapat diubah. Yang tidak boleh adalah assignment ulang variabel array.

---

## 9.3 Menambah dan Menghapus Data

```javascript
const angka = [1, 2, 3];

angka.push(4); // tambah di akhir
angka.unshift(0); // tambah di awal

angka.pop(); // hapus dari akhir
angka.shift(); // hapus dari awal

console.log(angka);
```

---

## 9.4 Panjang Array

```javascript
const siswa = ["Alya", "Budi", "Citra"];

console.log(siswa.length);
```

`length` sering digunakan dalam perulangan.

---

## 9.5 Loop Array

Menggunakan `for`:

```javascript
const siswa = ["Alya", "Budi", "Citra"];

for (let i = 0; i < siswa.length; i++) {
  console.log(siswa[i]);
}
```

Menggunakan `for...of`:

```javascript
for (const nama of siswa) {
  console.log(nama);
}
```

---

## 9.6 forEach

`forEach` menjalankan function untuk setiap item.

```javascript
const angka = [10, 20, 30];

angka.forEach(function (item) {
  console.log(item);
});
```

---

## 9.7 map

`map` membuat array baru dari hasil transformasi.

```javascript
const angka = [1, 2, 3];
const kuadrat = angka.map((item) => item * item);

console.log(kuadrat);
```

---

## 9.8 filter

`filter` membuat array baru berisi item yang lolos kondisi.

```javascript
const angka = [1, 2, 3, 4, 5, 6];
const genap = angka.filter((item) => item % 2 === 0);

console.log(genap);
```

---

## 9.9 find

`find` mencari item pertama yang cocok.

```javascript
const produk = [
  { id: 1, nama: "Keyboard" },
  { id: 2, nama: "Mouse" },
];

const hasil = produk.find((item) => item.id === 2);

console.log(hasil);
```

---

## 9.10 reduce

`reduce` mengubah array menjadi satu nilai.

```javascript
const angka = [10, 20, 30];
const total = angka.reduce((acc, item) => acc + item, 0);

console.log(total);
```

`acc` adalah accumulator, yaitu nilai yang dikumpulkan dari setiap iterasi.

---

## 9.11 includes dan join

```javascript
const role = ["admin", "editor", "viewer"];

console.log(role.includes("admin"));
console.log(role.join(", "));
```

---

## Ringkasan

- Array menyimpan data berurutan dalam satu variabel.
- Method seperti `map`, `filter`, `find`, dan `reduce` membantu mengolah data.
- Array sering digunakan bersama object untuk data aplikasi nyata.

---

## Latihan

1. Buat array berisi 5 nama teman.
2. Tampilkan semua nama menggunakan `for...of`.
3. Buat array angka, lalu ambil hanya angka ganjil menggunakan `filter`.
4. Hitung total harga belanja menggunakan `reduce`.
