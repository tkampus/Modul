# Bagian 20: Error Handling dan Debugging

## Yang Akan Dibahas

Error handling adalah cara menangani kesalahan agar program tidak berhenti secara tidak terkendali. Debugging adalah proses mencari dan memperbaiki masalah dalam kode.

---

## Tujuan Pembelajaran

Setelah mempelajari modul ini, peserta diharapkan mampu:

1. Mengenal jenis error umum.
2. Membaca pesan error.
3. Menggunakan `try catch`.
4. Membuat custom error.
5. Melakukan debugging dengan console dan DevTools.

---

## 20.1 Jenis Error Umum

| Error | Penyebab Umum |
|---|---|
| SyntaxError | Penulisan kode tidak valid |
| ReferenceError | Mengakses variabel yang tidak ada |
| TypeError | Menggunakan nilai dengan cara yang salah |
| RangeError | Nilai berada di luar batas yang diperbolehkan |

Contoh SyntaxError:

```javascript
// Kurung tutup hilang
console.log("Halo"
```

Contoh ReferenceError:

```javascript
console.log(nama);
```

Contoh TypeError:

```javascript
const nama = null;
console.log(nama.length);
```

---

## 20.2 Membaca Pesan Error

Pesan error biasanya memberi informasi:

- Jenis error.
- Pesan penyebab error.
- File tempat error terjadi.
- Nomor baris error.

Contoh:

```text
TypeError: Cannot read properties of null
```

Artinya kode mencoba membaca property dari nilai `null`.

---

## 20.3 try catch

`try catch` digunakan untuk menangani error.

```javascript
try {
  const data = JSON.parse("{ salah json }");
  console.log(data);
} catch (error) {
  console.log("JSON tidak valid");
  console.log(error.message);
}
```

Kode di dalam `catch` berjalan jika terjadi error di dalam `try`.

---

## 20.4 finally

`finally` selalu berjalan, baik terjadi error maupun tidak.

```javascript
try {
  console.log("Membuka koneksi");
} catch (error) {
  console.log("Terjadi error");
} finally {
  console.log("Menutup koneksi");
}
```

---

## 20.5 throw

`throw` digunakan untuk membuat error sendiri.

```javascript
function bagi(a, b) {
  if (b === 0) {
    throw new Error("Pembagi tidak boleh nol");
  }

  return a / b;
}

try {
  console.log(bagi(10, 0));
} catch (error) {
  console.log(error.message);
}
```

---

## 20.6 Debugging dengan console

```javascript
const harga = 10000;
const jumlah = 3;
const total = harga * jumlah;

console.log("harga:", harga);
console.log("jumlah:", jumlah);
console.log("total:", total);
```

Method console lain:

```javascript
console.table([
  { nama: "Alya", nilai: 90 },
  { nama: "Budi", nilai: 80 },
]);

console.warn("Ini peringatan");
console.error("Ini error");
```

---

## 20.7 Debugging dengan DevTools

Langkah dasar:

1. Buka browser.
2. Tekan `F12`.
3. Buka tab Sources.
4. Pilih file JavaScript.
5. Klik nomor baris untuk membuat breakpoint.
6. Jalankan ulang aksi di halaman.
7. Periksa nilai variabel saat kode berhenti.

Breakpoint membantu melihat alur program secara perlahan.

---

## 20.8 Tips Debugging

- Baca pesan error dari atas.
- Cari nomor baris yang disebutkan.
- Periksa nama variabel.
- Cek tipe data menggunakan `typeof`.
- Pecah kode besar menjadi function kecil.
- Buat contoh data sederhana untuk menguji logika.

---

## Ringkasan

- Error handling membantu program menangani kesalahan dengan lebih terkendali.
- `try catch`, `throw`, dan `finally` digunakan untuk menangani error.
- Debugging dapat dilakukan dengan console dan DevTools.

---

## Latihan

1. Buat contoh SyntaxError, lalu perbaiki.
2. Buat function pembagian yang menolak pembagi nol.
3. Gunakan `try catch` untuk menangani JSON yang tidak valid.
4. Debug program sederhana menggunakan `console.log`.
