# Bagian 19: npm dan package.json

## Yang Akan Dibahas

npm digunakan untuk mengelola package JavaScript. File `package.json` digunakan untuk menyimpan informasi project, script, dan dependency.

---

## Tujuan Pembelajaran

Setelah mempelajari modul ini, peserta diharapkan mampu:

1. Membuat `package.json`.
2. Memasang dan menghapus package.
3. Memahami dependency dan dev dependency.
4. Menjalankan npm script.
5. Memahami fungsi `node_modules` dan `package-lock.json`.

---

## 19.1 Membuat package.json

Masuk ke folder project, lalu jalankan:

```bash
npm init
```

Untuk membuat dengan jawaban default:

```bash
npm init -y
```

Contoh isi `package.json`:

```json
{
  "name": "belajar-js",
  "version": "1.0.0",
  "main": "app.js",
  "scripts": {
    "start": "node app.js"
  }
}
```

---

## 19.2 Menjalankan Script

Jika `package.json` berisi:

```json
{
  "scripts": {
    "start": "node app.js",
    "dev": "node --watch app.js"
  }
}
```

Jalankan:

```bash
npm run dev
```

Khusus script bernama `start`, dapat dijalankan dengan:

```bash
npm start
```

---

## 19.3 Menginstal Package

```bash
npm install axios
```

Setelah package dipasang, `package.json` akan memiliki bagian dependencies:

```json
{
  "dependencies": {
    "axios": "^1.0.0"
  }
}
```

Contoh penggunaan:

```javascript
import axios from "axios";

const response = await axios.get("https://jsonplaceholder.typicode.com/users/1");
console.log(response.data);
```

---

## 19.4 Dependency dan Dev Dependency

Dependency adalah package yang dibutuhkan saat aplikasi berjalan.

```bash
npm install axios
```

Dev dependency adalah package yang hanya dibutuhkan saat development.

```bash
npm install eslint --save-dev
```

Di `package.json`:

```json
{
  "devDependencies": {
    "eslint": "^9.0.0"
  }
}
```

---

## 19.5 Menghapus Package

```bash
npm uninstall axios
```

Perintah ini menghapus package dari `node_modules` dan `package.json`.

---

## 19.6 node_modules

Folder `node_modules` berisi semua package yang dipasang.

Folder ini biasanya tidak dimasukkan ke Git karena ukurannya besar dan dapat dibuat ulang dengan:

```bash
npm install
```

---

## 19.7 package-lock.json

`package-lock.json` menyimpan versi dependency secara detail.

Fungsi utamanya:

- Membuat instalasi dependency lebih konsisten.
- Mengunci versi package dan dependency turunannya.
- Membantu tim memakai versi dependency yang sama.

File ini biasanya ikut disimpan di Git.

---

## 19.8 npx

`npx` digunakan untuk menjalankan package tanpa harus memasang global secara manual.

Contoh:

```bash
npx eslint .
```

---

## Ringkasan

- npm digunakan untuk mengelola package dan script project.
- `package.json` menyimpan informasi project dan dependency.
- `node_modules` dapat dibuat ulang dengan `npm install`.

---

## Latihan

1. Buat folder project baru.
2. Jalankan `npm init -y`.
3. Buat script `start` untuk menjalankan `app.js`.
4. Instal satu package, lalu cek perubahan di `package.json`.
5. Hapus package tersebut menggunakan `npm uninstall`.
