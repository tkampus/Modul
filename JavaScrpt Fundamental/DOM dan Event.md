# Bagian 15: DOM dan Event

## Yang Akan Dibahas

DOM adalah representasi struktur HTML yang dapat diakses dan diubah menggunakan JavaScript. Event adalah aksi yang terjadi pada halaman, seperti click, input, submit, dan keydown.

---

## Tujuan Pembelajaran

Setelah mempelajari modul ini, peserta diharapkan mampu:

1. Memahami DOM.
2. Mengambil elemen HTML dengan JavaScript.
3. Mengubah isi dan style elemen.
4. Menangani event.
5. Membuat interaksi sederhana.

---

## 15.1 Apa Itu DOM?

DOM adalah singkatan dari Document Object Model.

Ketika browser membaca HTML, browser membuat struktur object yang dapat dimanipulasi JavaScript.

Contoh HTML:

```html
<h1 id="judul">Belajar DOM</h1>
```

JavaScript dapat mengambil dan mengubah elemen tersebut:

```javascript
const judul = document.getElementById("judul");
judul.textContent = "Belajar JavaScript DOM";
```

---

## 15.2 Mengambil Elemen

```javascript
const judul = document.getElementById("judul");
const tombol = document.querySelector(".tombol");
const semuaItem = document.querySelectorAll(".item");
```

| Method | Fungsi |
|---|---|
| `getElementById` | Mengambil elemen berdasarkan id |
| `querySelector` | Mengambil elemen pertama berdasarkan selector CSS |
| `querySelectorAll` | Mengambil semua elemen berdasarkan selector CSS |

---

## 15.3 Mengubah Isi Elemen

```html
<p id="pesan">Pesan lama</p>
```

```javascript
const pesan = document.getElementById("pesan");

pesan.textContent = "Pesan baru";
pesan.innerHTML = "<strong>Pesan tebal</strong>";
```

Gunakan `textContent` untuk teks biasa. Gunakan `innerHTML` hanya jika perlu memasukkan HTML.

---

## 15.4 Mengubah Attribute dan Style

```html
<img id="gambar" src="lama.jpg" alt="Gambar lama">
```

```javascript
const gambar = document.getElementById("gambar");

gambar.setAttribute("src", "baru.jpg");
gambar.setAttribute("alt", "Gambar baru");
```

Mengubah style:

```javascript
const judul = document.getElementById("judul");

judul.style.color = "blue";
judul.style.fontSize = "32px";
```

Untuk project nyata, lebih baik mengubah class CSS daripada banyak mengubah inline style.

---

## 15.5 classList

```javascript
const box = document.querySelector(".box");

box.classList.add("aktif");
box.classList.remove("hidden");
box.classList.toggle("dark");
box.classList.contains("aktif");
```

---

## 15.6 Event Click

```html
<button id="tombol">Klik</button>
<p id="output"></p>
```

```javascript
const tombol = document.getElementById("tombol");
const output = document.getElementById("output");

tombol.addEventListener("click", function () {
  output.textContent = "Tombol sudah diklik";
});
```

---

## 15.7 Event Input

```html
<input id="nama" type="text">
<p id="preview"></p>
```

```javascript
const nama = document.getElementById("nama");
const preview = document.getElementById("preview");

nama.addEventListener("input", function () {
  preview.textContent = nama.value;
});
```

---

## 15.8 Event Submit

```html
<form id="form">
  <input id="email" type="email">
  <button type="submit">Kirim</button>
</form>
```

```javascript
const form = document.getElementById("form");
const email = document.getElementById("email");

form.addEventListener("submit", function (event) {
  event.preventDefault();
  console.log(email.value);
});
```

`event.preventDefault()` mencegah form melakukan reload halaman.

---

## 15.9 Membuat Elemen Baru

```javascript
const daftar = document.getElementById("daftar");
const item = document.createElement("li");

item.textContent = "Belajar DOM";
daftar.appendChild(item);
```

---

## Ringkasan

- DOM memungkinkan JavaScript mengakses dan mengubah elemen HTML.
- Event digunakan untuk merespons aksi user.
- Interaksi halaman biasanya dibuat dengan kombinasi selector, event listener, dan manipulasi elemen.

---

## Latihan

1. Buat tombol yang mengubah teks paragraf.
2. Buat input nama dan tampilkan preview secara langsung.
3. Buat tombol untuk menambah item ke daftar.
4. Buat tombol untuk toggle class `dark` pada halaman.
