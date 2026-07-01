# Bagian 16: LocalStorage dan Browser API

## Yang Akan Dibahas

Browser menyediakan berbagai API yang bisa digunakan JavaScript. Salah satu yang paling sering digunakan pemula adalah localStorage untuk menyimpan data sederhana di browser.

---

## Tujuan Pembelajaran

Setelah mempelajari modul ini, peserta diharapkan mampu:

1. Memahami fungsi localStorage.
2. Menyimpan, mengambil, dan menghapus data dari localStorage.
3. Menyimpan array atau object sebagai JSON.
4. Mengenal beberapa Browser API dasar.

---

## 16.1 Apa Itu localStorage?

localStorage adalah penyimpanan sederhana di browser.

Ciri-ciri localStorage:

- Data disimpan dalam bentuk string.
- Data tetap ada walaupun halaman ditutup.
- Data hanya tersedia pada domain yang sama.
- Cocok untuk preferensi sederhana, token sementara pembelajaran, atau data latihan.

Jangan menyimpan data sensitif seperti password di localStorage.

---

## 16.2 Menyimpan Data

```javascript
localStorage.setItem("nama", "Alya");
```

Format:

```javascript
localStorage.setItem("key", "value");
```

---

## 16.3 Mengambil Data

```javascript
const nama = localStorage.getItem("nama");

console.log(nama);
```

Jika key tidak ditemukan, hasilnya `null`.

---

## 16.4 Menghapus Data

Menghapus satu item:

```javascript
localStorage.removeItem("nama");
```

Menghapus semua data localStorage untuk domain tersebut:

```javascript
localStorage.clear();
```

---

## 16.5 Menyimpan Object

localStorage hanya menyimpan string. Object harus diubah menjadi JSON string.

```javascript
const user = {
  nama: "Budi",
  role: "admin",
};

localStorage.setItem("user", JSON.stringify(user));
```

Mengambil kembali:

```javascript
const userJson = localStorage.getItem("user");
const user = JSON.parse(userJson);

console.log(user.nama);
```

---

## 16.6 Menyimpan Array

```javascript
const todos = ["Belajar JS", "Latihan DOM"];

localStorage.setItem("todos", JSON.stringify(todos));
```

Mengambil:

```javascript
const data = localStorage.getItem("todos");
const todos = data ? JSON.parse(data) : [];

console.log(todos);
```

Pengecekan `data ? ... : []` mencegah error ketika data belum ada.

---

## 16.7 sessionStorage

`sessionStorage` mirip localStorage, tetapi datanya hilang ketika tab browser ditutup.

```javascript
sessionStorage.setItem("mode", "preview");
console.log(sessionStorage.getItem("mode"));
```

---

## 16.8 Browser API Lain yang Sering Dipakai

| API | Fungsi |
|---|---|
| `alert` | Menampilkan pesan sederhana |
| `confirm` | Meminta konfirmasi user |
| `prompt` | Meminta input sederhana |
| `navigator` | Informasi browser dan device |
| `location` | Informasi URL halaman |
| `history` | Navigasi riwayat browser |

Contoh:

```javascript
const yakin = confirm("Apakah ingin menghapus data?");

if (yakin) {
  console.log("Data dihapus");
}
```

---

## 16.9 Contoh Tema Gelap

```javascript
const tombol = document.getElementById("toggleTema");
const tema = localStorage.getItem("tema") || "light";

document.body.dataset.theme = tema;

tombol.addEventListener("click", function () {
  const temaAktif = document.body.dataset.theme;
  const temaBaru = temaAktif === "dark" ? "light" : "dark";

  document.body.dataset.theme = temaBaru;
  localStorage.setItem("tema", temaBaru);
});
```

---

## Ringkasan

- localStorage menyimpan data sederhana di browser.
- Data object dan array harus disimpan sebagai JSON string.
- Browser API menyediakan fitur tambahan seperti alert, confirm, location, dan history.

---

## Latihan

1. Simpan nama user ke localStorage.
2. Ambil nama user dan tampilkan ke halaman.
3. Simpan array todo ke localStorage.
4. Buat toggle tema sederhana yang tetap tersimpan setelah halaman di-refresh.
