# Bagian 10: Object dan JSON

## Yang Akan Dibahas

Object digunakan untuk menyimpan data dalam pasangan key dan value. JSON adalah format teks yang sering digunakan untuk bertukar data antar aplikasi.

---

## Tujuan Pembelajaran

Setelah mempelajari modul ini, peserta diharapkan mampu:

1. Membuat dan mengakses object.
2. Mengubah property object.
3. Menggunakan method dalam object.
4. Menggunakan destructuring dan spread operator.
5. Mengubah object ke JSON dan sebaliknya.

---

## 10.1 Membuat Object

```javascript
const user = {
  nama: "Alya",
  umur: 20,
  aktif: true,
};

console.log(user);
```

Object cocok untuk data yang memiliki banyak informasi terkait.

---

## 10.2 Mengakses Property

Menggunakan dot notation:

```javascript
console.log(user.nama);
```

Menggunakan bracket notation:

```javascript
console.log(user["umur"]);
```

Bracket notation berguna jika nama property berasal dari variabel.

```javascript
const key = "aktif";
console.log(user[key]);
```

---

## 10.3 Mengubah dan Menambah Property

```javascript
const produk = {
  nama: "Laptop",
  harga: 7500000,
};

produk.harga = 7000000;
produk.stok = 12;

console.log(produk);
```

Menghapus property:

```javascript
delete produk.stok;
```

---

## 10.4 Method dalam Object

Method adalah function yang menjadi property object.

```javascript
const user = {
  nama: "Budi",
  sapa: function () {
    return `Halo, saya ${this.nama}`;
  },
};

console.log(user.sapa());
```

`this` mengacu pada object yang sedang menjalankan method.

---

## 10.5 Destructuring Object

Destructuring digunakan untuk mengambil property ke variabel.

```javascript
const siswa = {
  nama: "Citra",
  kelas: "XI RPL",
};

const { nama, kelas } = siswa;

console.log(nama);
console.log(kelas);
```

---

## 10.6 Spread Operator

Spread operator digunakan untuk menyalin atau menggabungkan object.

```javascript
const user = {
  nama: "Dina",
  role: "admin",
};

const userBaru = {
  ...user,
  aktif: true,
};

console.log(userBaru);
```

Jika property sama, nilai terakhir akan menimpa nilai sebelumnya.

---

## 10.7 Array of Object

Data nyata sering berbentuk array berisi object.

```javascript
const produk = [
  { id: 1, nama: "Keyboard", harga: 250000 },
  { id: 2, nama: "Mouse", harga: 150000 },
  { id: 3, nama: "Monitor", harga: 1200000 },
];

const produkMahal = produk.filter((item) => item.harga > 200000);

console.log(produkMahal);
```

---

## 10.8 JSON

JSON adalah format teks untuk menyimpan atau mengirim data.

Contoh JSON:

```json
{
  "nama": "Alya",
  "umur": 20,
  "aktif": true
}
```

Perbedaan penting:

- Key JSON harus memakai tanda kutip ganda.
- JSON tidak bisa menyimpan function.
- JSON biasanya dikirim melalui API.

---

## 10.9 JSON.stringify dan JSON.parse

Mengubah object menjadi JSON string:

```javascript
const user = {
  nama: "Alya",
  umur: 20,
};

const json = JSON.stringify(user);
console.log(json);
```

Mengubah JSON string menjadi object:

```javascript
const data = '{"nama":"Alya","umur":20}';
const object = JSON.parse(data);

console.log(object.nama);
```

---

## Ringkasan

- Object menyimpan data dalam pasangan key dan value.
- JSON adalah format teks untuk pertukaran data.
- `JSON.stringify()` dan `JSON.parse()` digunakan untuk konversi object dan JSON string.

---

## Latihan

1. Buat object `mahasiswa` berisi nama, jurusan, dan semester.
2. Tambahkan method untuk menampilkan biodata mahasiswa.
3. Buat array berisi minimal 3 object produk.
4. Ubah object menjadi JSON string, lalu ubah kembali menjadi object.
