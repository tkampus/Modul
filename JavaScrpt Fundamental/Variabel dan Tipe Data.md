# Bagian 4: Variabel dan Tipe Data

## Yang Akan Dibahas

Variabel digunakan untuk menyimpan data. Tipe data menjelaskan jenis nilai yang disimpan, seperti teks, angka, boolean, array, atau object.

---

## Tujuan Pembelajaran

Setelah mempelajari modul ini, peserta diharapkan mampu:

1. Membuat variabel menggunakan `let` dan `const`.
2. Memahami perbedaan `let`, `const`, dan `var`.
3. Mengenal tipe data primitive dan object.
4. Menggunakan `typeof` untuk mengecek tipe data.

---

## 4.1 Membuat Variabel

JavaScript modern menggunakan `let` dan `const`.

```javascript
let nama = "Budi";
const tahunLahir = 2005;

console.log(nama);
console.log(tahunLahir);
```

Gunakan `let` jika nilainya akan berubah. Gunakan `const` jika nilainya tidak akan diganti.

---

## 4.2 let, const, dan var

| Keyword | Keterangan |
|---|---|
| `let` | Variabel dapat diubah nilainya |
| `const` | Variabel tidak dapat di-assign ulang |
| `var` | Cara lama, sebaiknya dihindari untuk kode modern |

Contoh:

```javascript
let skor = 10;
skor = 20;

const aplikasi = "Kasir";
// aplikasi = "Inventory"; // Error
```

Catatan: `const` mencegah assignment ulang, bukan selalu membuat isi data tidak bisa berubah.

```javascript
const user = {
  nama: "Sinta",
};

user.nama = "Rani"; // Boleh
```

---

## 4.3 Aturan Penamaan Variabel

Aturan umum:

- Tidak boleh diawali angka.
- Tidak boleh menggunakan spasi.
- Tidak boleh menggunakan keyword JavaScript.
- Gunakan nama yang jelas.
- Umumnya menggunakan camelCase.

Contoh baik:

```javascript
const namaLengkap = "Andi Pratama";
const totalHarga = 150000;
```

Contoh kurang baik:

```javascript
const x = "Andi";
const data1 = 150000;
```

---

## 4.4 Tipe Data Primitive

| Tipe Data | Contoh |
|---|---|
| String | `"JavaScript"` |
| Number | `100`, `3.14` |
| Boolean | `true`, `false` |
| Undefined | Variabel belum memiliki nilai |
| Null | Nilai kosong secara sengaja |
| BigInt | Angka sangat besar |
| Symbol | Nilai unik |

Contoh:

```javascript
const nama = "Alya";
const umur = 19;
const sudahLogin = true;
let alamat;
const pekerjaan = null;
```

---

## 4.5 Tipe Data Object

Object digunakan untuk menyimpan data kompleks.

```javascript
const siswa = {
  nama: "Dina",
  umur: 18,
  aktif: true,
};

const angka = [10, 20, 30];
```

Array sebenarnya termasuk object khusus untuk menyimpan data berurutan.

---

## 4.6 Mengecek Tipe Data

Gunakan `typeof`:

```javascript
console.log(typeof "Halo"); // string
console.log(typeof 100); // number
console.log(typeof true); // boolean
console.log(typeof undefined); // undefined
console.log(typeof null); // object
console.log(typeof []); // object
```

`typeof null` menghasilkan `object`. Ini adalah perilaku lama JavaScript yang tetap dipertahankan.

---

## 4.7 Template Literal

Template literal menggunakan backtick.

```javascript
const nama = "Alya";
const umur = 20;

console.log(`Nama saya ${nama}, umur saya ${umur} tahun.`);
```

Template literal memudahkan penggabungan teks dan variabel.

---

## Ringkasan

- `let` digunakan untuk nilai yang dapat berubah, sedangkan `const` untuk nilai yang tidak di-assign ulang.
- JavaScript memiliki tipe data primitive dan object.
- `typeof` digunakan untuk mengecek tipe data dasar.

---

## Latihan

1. Buat variabel `nama`, `umur`, dan `sudahMenikah`.
2. Tampilkan semua variabel menggunakan `console.log`.
3. Cek tipe data setiap variabel menggunakan `typeof`.
4. Buat kalimat perkenalan menggunakan template literal.
