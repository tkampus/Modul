# Bagian 2: Instalasi Node.js dan npm

## Yang Akan Dibahas

Node.js adalah runtime yang memungkinkan JavaScript berjalan di luar browser. npm adalah package manager yang digunakan untuk memasang library atau tools JavaScript.

---

## Tujuan Pembelajaran

Setelah mempelajari modul ini, peserta diharapkan mampu:

1. Menginstal Node.js.
2. Mengecek versi Node.js dan npm.
3. Memahami fungsi npm.
4. Menjalankan file JavaScript melalui terminal.

---

## 2.1 Apa Itu Node.js?

Node.js memungkinkan JavaScript digunakan untuk backend, tooling, automation, dan development server.

Tanpa Node.js, JavaScript biasanya hanya berjalan di browser. Dengan Node.js, file JavaScript dapat dijalankan melalui terminal:

```bash
node app.js
```

---

## 2.2 Apa Itu npm?

npm adalah singkatan dari Node Package Manager.

npm digunakan untuk:

- Menginstal package JavaScript.
- Mengelola dependency project.
- Menjalankan script project.
- Membuat file `package.json`.

Contoh instalasi package:

```bash
npm install axios
```

---

## 2.3 Instalasi di Windows

1. Buka halaman resmi Node.js: `https://nodejs.org`
2. Unduh versi LTS.
3. Jalankan installer.
4. Gunakan pengaturan default.
5. Setelah selesai, buka Command Prompt, PowerShell, atau terminal editor.

Cek versi:

```bash
node --version
npm --version
```

Jika berhasil, terminal akan menampilkan nomor versi.

---

## 2.4 Instalasi di macOS

Cara umum:

1. Buka `https://nodejs.org`
2. Unduh versi LTS untuk macOS.
3. Jalankan installer.
4. Cek versi:

```bash
node --version
npm --version
```

Jika menggunakan Homebrew:

```bash
brew install node
```

---

## 2.5 Instalasi di Linux

Ubuntu atau Debian:

```bash
sudo apt update
sudo apt install nodejs npm
```

Cek versi:

```bash
node --version
npm --version
```

Untuk versi Node.js yang lebih fleksibel, developer sering menggunakan `nvm`. Namun untuk tahap fundamental, instalasi melalui package manager sudah cukup.

---

## 2.6 Membuat File JavaScript Pertama

Buat file bernama `app.js`:

```javascript
console.log("Belajar JavaScript dengan Node.js");
```

Jalankan:

```bash
node app.js
```

Output:

```text
Belajar JavaScript dengan Node.js
```

---

## 2.7 Masalah Umum Instalasi

| Masalah | Solusi |
|---|---|
| `node` tidak dikenali | Tutup dan buka ulang terminal |
| npm tidak tersedia | Pastikan Node.js terinstal dari installer resmi |
| Versi tidak muncul | Cek ulang proses instalasi |
| Permission error di Linux/macOS | Hindari `sudo npm install -g` jika belum paham risikonya |

---

## Ringkasan

- Node.js menjalankan JavaScript di luar browser.
- npm digunakan untuk mengelola package JavaScript.
- Instalasi dapat dicek dengan `node --version` dan `npm --version`.

---

## Latihan

1. Instal Node.js versi LTS.
2. Jalankan `node --version`.
3. Jalankan `npm --version`.
4. Buat file `app.js` dan jalankan menggunakan `node app.js`.
