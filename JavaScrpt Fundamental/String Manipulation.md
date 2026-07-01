# Bagian 13: String Manipulation

## Yang Akan Dibahas

String manipulation adalah proses mengolah teks menggunakan JavaScript. Materi ini membahas cara mengubah huruf, mencari teks, memotong teks, mengganti teks, memecah dan menggabungkan string, membersihkan spasi, padding, template literal, serta regular expression dasar.

---

## Tujuan Pembelajaran

Setelah mempelajari materi ini, peserta diharapkan mampu:

1. Menggunakan method string untuk mengubah teks.
2. Mencari dan mengecek keberadaan teks.
3. Memotong, mengganti, memecah, dan menggabungkan string.
4. Membersihkan input user.
5. Menggunakan template literal untuk membuat teks dinamis.
6. Menggunakan regular expression dasar untuk pencarian dan penggantian teks.

---

String dalam JavaScript bersifat immutable. Artinya, method string tidak mengubah string asli, tetapi menghasilkan string baru.

```javascript
const nama = "javascript";
const hasil = nama.toUpperCase();

console.log(nama);
console.log(hasil);
```

Hasil:

```text
javascript
JAVASCRIPT
```

---

## 13.1 Mengubah Huruf

Gunakan `toUpperCase()` untuk mengubah teks menjadi huruf besar dan `toLowerCase()` untuk mengubah teks menjadi huruf kecil.

### Contoh

```javascript
const bahasa = "JavaScript";

console.log(bahasa.toUpperCase());
console.log(bahasa.toLowerCase());
```

Hasil:

```text
JAVASCRIPT
javascript
```

Contoh penggunaan untuk perbandingan:

```javascript
const input = "Admin";

if (input.toLowerCase() === "admin") {
  console.log("Role valid");
}
```

Hasil:

```text
Role valid
```

---

## 13.2 Menghitung Panjang String

Property `length` digunakan untuk menghitung jumlah karakter.

### Contoh

```javascript
const password = "secret123";

console.log(password.length);
```

Hasil:

```text
9
```

Contoh validasi:

```javascript
if (password.length < 8) {
  console.log("Password terlalu pendek");
} else {
  console.log("Password cukup panjang");
}
```

Hasil:

```text
Password cukup panjang
```

---

## 13.3 Mencari Teks

Beberapa method untuk mencari teks:

| Method | Fungsi |
|---|---|
| `includes()` | Mengecek apakah teks mengandung teks tertentu |
| `startsWith()` | Mengecek apakah teks diawali teks tertentu |
| `endsWith()` | Mengecek apakah teks diakhiri teks tertentu |
| `indexOf()` | Mengambil posisi kemunculan pertama |
| `lastIndexOf()` | Mengambil posisi kemunculan terakhir |

### Contoh

```javascript
const email = "admin@example.com";

console.log(email.includes("@"));
console.log(email.startsWith("admin"));
console.log(email.endsWith(".com"));
console.log(email.indexOf("@"));
```

Hasil:

```text
true
true
true
5
```

Jika teks tidak ditemukan, `indexOf()` menghasilkan `-1`.

---

## 13.4 Mengambil Bagian String

Gunakan `slice()` untuk mengambil bagian string.

### Sintaks

```javascript
string.slice(indexAwal, indexAkhir)
```

### Contoh

```javascript
const kode = "INV-2026-001";

console.log(kode.slice(0, 3));
console.log(kode.slice(4, 8));
console.log(kode.slice(-3));
```

Hasil:

```text
INV
2026
001
```

`indexAkhir` tidak ikut diambil.

---

## 13.5 Mengganti Teks

Gunakan `replace()` untuk mengganti kemunculan pertama dan `replaceAll()` untuk mengganti semua kemunculan.

### Contoh

```javascript
const kalimat = "Saya belajar JavaScript. JavaScript itu populer.";

console.log(kalimat.replace("JavaScript", "JS"));
console.log(kalimat.replaceAll("JavaScript", "JS"));
```

Hasil:

```text
Saya belajar JS. JavaScript itu populer.
Saya belajar JS. JS itu populer.
```

---

## 13.6 Memecah dan Menggabungkan String

`split()` memecah string menjadi array.

```javascript
const tags = "html,css,javascript";
const hasil = tags.split(",");

console.log(hasil);
```

Hasil:

```text
[ 'html', 'css', 'javascript' ]
```

`join()` menggabungkan array menjadi string.

```javascript
const skill = ["HTML", "CSS", "JavaScript"];

console.log(skill.join(", "));
```

Hasil:

```text
HTML, CSS, JavaScript
```

---

## 13.7 Membersihkan Spasi

Gunakan `trim()`, `trimStart()`, dan `trimEnd()` untuk membersihkan spasi.

### Contoh

```javascript
const username = "  muktashim  ";

console.log(username.trim());
console.log(username.trimStart());
console.log(username.trimEnd());
```

Hasil:

```text
muktashim
muktashim  
  muktashim
```

`trim()` sering digunakan untuk membersihkan input user sebelum validasi.

---

## 13.8 Padding String

`padStart()` dan `padEnd()` digunakan untuk menambahkan karakter sampai panjang tertentu.

### Contoh

```javascript
const nomor = "7";

console.log(nomor.padStart(3, "0"));
console.log(nomor.padEnd(3, "0"));
```

Hasil:

```text
007
700
```

Contoh penggunaan:

```javascript
const nomorAntrian = 12;
const kodeAntrian = String(nomorAntrian).padStart(4, "0");

console.log(`A-${kodeAntrian}`);
```

Hasil:

```text
A-0012
```

---

## 13.9 Template Literal

Template literal menggunakan backtick dan dapat menyisipkan ekspresi dengan `${}`.

### Contoh

```javascript
const nama = "Alya";
const total = 150000;

const pesan = `Halo ${nama}, total belanja kamu adalah Rp${total.toLocaleString("id-ID")}.`;

console.log(pesan);
```

Hasil:

```text
Halo Alya, total belanja kamu adalah Rp150.000.
```

Template literal juga dapat digunakan untuk teks banyak baris.

```javascript
const invoice = `
Invoice
Nama: ${nama}
Total: ${total}
`;

console.log(invoice);
```

---

## 13.10 Regular Expression Dasar

Regular expression atau regex digunakan untuk pencarian pola teks.

### Contoh test()

```javascript
const email = "user@example.com";
const polaEmail = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;

console.log(polaEmail.test(email));
```

Hasil:

```text
true
```

### Contoh replace dengan regex

```javascript
const teks = "Belajar    JavaScript   Fundamental";
const rapi = teks.replace(/\s+/g, " ");

console.log(rapi);
```

Hasil:

```text
Belajar JavaScript Fundamental
```

Regex sangat kuat, tetapi untuk pemula cukup pahami penggunaan dasar seperti validasi sederhana dan mengganti pola teks.

---

## 13.11 Studi Kasus: Membuat Slug

Slug adalah teks URL-friendly, misalnya dari judul artikel.

```javascript
function buatSlug(judul) {
  return judul
    .trim()
    .toLowerCase()
    .replace(/[^a-z0-9\s-]/g, "")
    .replace(/\s+/g, "-");
}

console.log(buatSlug(" Belajar JavaScript Dasar! "));
```

Hasil:

```text
belajar-javascript-dasar
```

---

## Ringkasan

- String manipulation digunakan untuk mengolah teks agar sesuai kebutuhan aplikasi.
- Method string menghasilkan string baru karena string bersifat immutable.
- `includes()`, `startsWith()`, `endsWith()`, dan `indexOf()` digunakan untuk pencarian teks.
- `slice()`, `replace()`, `replaceAll()`, `split()`, `join()`, dan `trim()` sering digunakan untuk membersihkan dan membentuk data.
- Template literal memudahkan pembuatan teks dinamis.
- Regex dapat digunakan untuk pencarian pola dan validasi sederhana.

---

## Latihan

1. Buat program yang mengubah nama menjadi huruf kapital semua.
2. Buat validasi sederhana untuk mengecek apakah email mengandung `@` dan diakhiri `.com`.
3. Ambil tahun dari string `INV-2026-001`.
4. Ubah teks `"belajar javascript dasar"` menjadi `"belajar-javascript-dasar"`.
5. Buat function `formatKodeProduk(nomor)` yang menghasilkan kode seperti `PRD-0007`.
6. Buat function untuk membersihkan spasi berlebih dalam kalimat.
