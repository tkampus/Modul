# Bagian 3: Menjalankan JavaScript

## Yang Akan Dibahas

JavaScript dapat dijalankan dengan beberapa cara. Untuk belajar fundamental, cara paling umum adalah melalui browser, file HTML, dan terminal menggunakan Node.js.

---

## Tujuan Pembelajaran

Setelah mempelajari modul ini, peserta diharapkan mampu:

1. Menjalankan JavaScript di console browser.
2. Menulis JavaScript di file HTML.
3. Menjalankan JavaScript dari file `.js`.
4. Memahami perbedaan output di browser dan Node.js.

---

## 3.1 Menjalankan JavaScript di Console Browser

Langkah:

1. Buka browser.
2. Tekan `F12` atau klik kanan lalu pilih Inspect.
3. Buka tab Console.
4. Ketik kode berikut:

```javascript
console.log("Halo dari browser");
```

Tekan Enter untuk menjalankan.

Console browser cocok untuk mencoba kode singkat.

---

## 3.2 Menjalankan JavaScript di File HTML

Buat file `index.html`:

```html
<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <title>Belajar JavaScript</title>
</head>
<body>
  <h1>Belajar JavaScript</h1>

  <script>
    console.log("JavaScript berjalan dari HTML");
  </script>
</body>
</html>
```

Buka file tersebut di browser, lalu cek console.

---

## 3.3 Menghubungkan File JavaScript Eksternal

Pisahkan kode JavaScript ke file `script.js`.

File `index.html`:

```html
<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <title>JS Eksternal</title>
</head>
<body>
  <h1>JS Eksternal</h1>

  <script src="script.js"></script>
</body>
</html>
```

File `script.js`:

```javascript
console.log("Kode berasal dari script.js");
```

Cara ini lebih rapi untuk project nyata.

---

## 3.4 Menjalankan JavaScript dengan Node.js

Buat file `app.js`:

```javascript
const pesan = "Halo dari Node.js";
console.log(pesan);
```

Jalankan di terminal:

```bash
node app.js
```

---

## 3.5 Output Menggunakan console.log

`console.log()` digunakan untuk menampilkan output:

```javascript
console.log("Teks");
console.log(100);
console.log(true);
console.log(["HTML", "CSS", "JavaScript"]);
```

Output sangat berguna untuk belajar dan debugging.

---

## 3.6 Komentar dalam JavaScript

Komentar satu baris:

```javascript
// Ini komentar satu baris
```

Komentar banyak baris:

```javascript
/*
  Ini komentar
  lebih dari satu baris
*/
```

Komentar digunakan untuk memberi catatan pada kode, tetapi jangan berlebihan.

---

## Ringkasan

- JavaScript dapat dijalankan melalui console browser, file HTML, file eksternal, dan Node.js.
- `console.log()` berguna untuk menampilkan output dan membantu debugging.
- Komentar membantu memberi catatan pada kode.

---

## Latihan

1. Jalankan `console.log("Nama saya ...")` di console browser.
2. Buat file HTML yang menjalankan JavaScript internal.
3. Buat file `script.js` dan hubungkan ke HTML.
4. Buat file `app.js` dan jalankan dengan Node.js.
