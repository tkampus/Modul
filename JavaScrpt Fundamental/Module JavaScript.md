# Bagian 18: Module JavaScript

## Yang Akan Dibahas

Module digunakan untuk memecah kode menjadi beberapa file. Dengan module, kode lebih rapi, mudah diuji, dan mudah digunakan kembali.

---

## Tujuan Pembelajaran

Setelah mempelajari modul ini, peserta diharapkan mampu:

1. Memahami fungsi module.
2. Menggunakan `export` dan `import`.
3. Menggunakan module di browser.
4. Menggunakan module di Node.js.
5. Memahami perbedaan named export dan default export.

---

## 18.1 Mengapa Perlu Module?

Jika semua kode ditulis dalam satu file, project akan sulit dikelola.

Module membantu:

- Memisahkan tanggung jawab kode.
- Menghindari file terlalu panjang.
- Menggunakan ulang function.
- Membuat struktur project lebih jelas.

---

## 18.2 Named Export

File `math.js`:

```javascript
export function tambah(a, b) {
  return a + b;
}

export function kurang(a, b) {
  return a - b;
}
```

File `app.js`:

```javascript
import { tambah, kurang } from "./math.js";

console.log(tambah(10, 5));
console.log(kurang(10, 5));
```

Named export harus di-import menggunakan nama yang sesuai.

---

## 18.3 Default Export

File `sapa.js`:

```javascript
export default function sapa(nama) {
  return `Halo, ${nama}`;
}
```

File `app.js`:

```javascript
import sapa from "./sapa.js";

console.log(sapa("Alya"));
```

Default export dapat di-import dengan nama bebas.

---

## 18.4 Menggunakan Module di Browser

File `index.html`:

```html
<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <title>Module JavaScript</title>
</head>
<body>
  <script type="module" src="app.js"></script>
</body>
</html>
```

Gunakan `type="module"` agar browser memahami `import` dan `export`.

---

## 18.5 Menggunakan Module di Node.js

Ada dua cara umum.

Cara pertama, gunakan ekstensi `.mjs`:

```bash
node app.mjs
```

Cara kedua, tambahkan konfigurasi di `package.json`:

```json
{
  "type": "module"
}
```

Setelah itu file `.js` dapat menggunakan `import` dan `export`.

---

## 18.6 Import dengan Alias

```javascript
import { tambah as penjumlahan } from "./math.js";

console.log(penjumlahan(2, 3));
```

Alias berguna jika nama import terlalu umum atau bentrok dengan nama lain.

---

## 18.7 Export Banyak Data

```javascript
const appName = "Kasir App";

function formatRupiah(angka) {
  return angka.toLocaleString("id-ID");
}

export { appName, formatRupiah };
```

Import:

```javascript
import { appName, formatRupiah } from "./utils.js";
```

---

## Ringkasan

- Module memecah kode menjadi beberapa file.
- `export` dan `import` digunakan untuk berbagi kode antar file.
- Module dapat digunakan di browser dan Node.js.

---

## Latihan

1. Buat file `math.js` berisi function tambah, kurang, kali, dan bagi.
2. Import semua function tersebut ke `app.js`.
3. Buat default export untuk function sapaan.
4. Jalankan module melalui browser atau Node.js.
