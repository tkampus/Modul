# Bagian 11: Destructuring, Spread, dan Rest

## Yang Akan Dibahas

Destructuring, spread, dan rest adalah fitur JavaScript modern yang membuat pengolahan array, object, dan parameter function menjadi lebih ringkas.

---

## Tujuan Pembelajaran

Setelah mempelajari modul ini, peserta diharapkan mampu:

1. Menggunakan destructuring pada array.
2. Menggunakan destructuring pada object.
3. Menggunakan spread operator untuk menyalin dan menggabungkan data.
4. Menggunakan rest parameter pada function.

---

## 11.1 Destructuring Array

Destructuring array mengambil nilai berdasarkan urutan.

```javascript
const warna = ["Merah", "Hijau", "Biru"];

const [pertama, kedua, ketiga] = warna;

console.log(pertama);
console.log(kedua);
console.log(ketiga);
```

Melewati item:

```javascript
const angka = [10, 20, 30];
const [awal, , akhir] = angka;

console.log(awal);
console.log(akhir);
```

---

## 11.2 Destructuring Object

Destructuring object mengambil nilai berdasarkan nama property.

```javascript
const user = {
  nama: "Alya",
  umur: 20,
  role: "admin",
};

const { nama, role } = user;

console.log(nama);
console.log(role);
```

Menggunakan nama variabel berbeda:

```javascript
const { nama: namaUser } = user;

console.log(namaUser);
```

---

## 11.3 Default Value

```javascript
const produk = {
  nama: "Keyboard",
};

const { nama, stok = 0 } = produk;

console.log(nama);
console.log(stok);
```

Default value digunakan jika property tidak tersedia.

---

## 11.4 Destructuring Parameter Function

```javascript
function tampilkanUser({ nama, umur }) {
  console.log(`${nama} berumur ${umur} tahun`);
}

tampilkanUser({
  nama: "Budi",
  umur: 21,
});
```

Cara ini sering dipakai ketika function menerima object konfigurasi.

---

## 11.5 Spread Array

Spread operator `...` dapat menyalin array.

```javascript
const angka = [1, 2, 3];
const salinan = [...angka];

console.log(salinan);
```

Menggabungkan array:

```javascript
const frontend = ["HTML", "CSS"];
const backend = ["Node.js", "Express"];

const skill = [...frontend, ...backend];

console.log(skill);
```

---

## 11.6 Spread Object

```javascript
const user = {
  nama: "Citra",
  role: "editor",
};

const userAktif = {
  ...user,
  aktif: true,
};

console.log(userAktif);
```

Spread object umum digunakan untuk membuat salinan data sebelum mengubah property.

---

## 11.7 Rest Parameter

Rest parameter menerima banyak argument menjadi array.

```javascript
function jumlahkan(...angka) {
  return angka.reduce((total, item) => total + item, 0);
}

console.log(jumlahkan(10, 20, 30));
```

Rest parameter harus berada di posisi terakhir.

```javascript
function cetakData(nama, ...hobi) {
  console.log(nama);
  console.log(hobi);
}

cetakData("Alya", "Membaca", "Coding", "Musik");
```

---

## Ringkasan

- Destructuring memudahkan pengambilan data dari array dan object.
- Spread digunakan untuk menyalin atau menggabungkan data.
- Rest parameter menerima banyak argument dalam bentuk array.

---

## Latihan

1. Ambil item pertama dan kedua dari array menggunakan destructuring.
2. Ambil property `nama` dan `harga` dari object produk.
3. Gabungkan dua array menggunakan spread operator.
4. Buat function `rataRata(...angka)` menggunakan rest parameter.
