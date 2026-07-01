# Bagian 1: Pengenalan JavaScript

## Yang Akan Dibahas

JavaScript adalah bahasa pemrograman yang awalnya dibuat untuk membuat halaman web menjadi interaktif. Saat ini JavaScript juga digunakan untuk backend, aplikasi mobile, desktop, game, automation, dan tooling development.

JavaScript termasuk bahasa yang sangat penting dalam web development karena berjalan langsung di browser seperti Chrome, Firefox, Edge, dan Safari.

---

## Tujuan Pembelajaran

Setelah mempelajari modul ini, peserta diharapkan mampu:

1. Memahami apa itu JavaScript.
2. Menjelaskan fungsi JavaScript dalam website.
3. Membedakan JavaScript, HTML, dan CSS.
4. Memahami peran JavaScript di browser dan server.

---

## 1.1 Apa Itu JavaScript?

JavaScript adalah bahasa pemrograman yang digunakan untuk memberikan logika dan interaksi pada aplikasi.

Contoh penggunaan JavaScript:

- Menampilkan pesan ketika tombol diklik.
- Mengambil data dari server.
- Memvalidasi form.
- Membuat slider, modal, dropdown, dan tab.
- Membuat aplikasi web modern seperti dashboard, chat, dan e-commerce.

Contoh sederhana:

```javascript
console.log("Halo, JavaScript!");
```

Kode di atas akan mencetak teks ke console.

---

## 1.2 HTML, CSS, dan JavaScript

Dalam pengembangan web, HTML, CSS, dan JavaScript memiliki peran berbeda.

| Teknologi | Fungsi |
|---|---|
| HTML | Membuat struktur halaman |
| CSS | Mengatur tampilan halaman |
| JavaScript | Mengatur logika dan interaksi |

Contoh:

```html
<button id="tombol">Klik Saya</button>

<script>
  document.getElementById("tombol").addEventListener("click", function () {
    alert("Tombol diklik!");
  });
</script>
```

HTML membuat tombol, JavaScript memberi aksi ketika tombol diklik.

---

## 1.3 JavaScript di Browser

Browser memiliki JavaScript engine untuk menjalankan kode JavaScript.

| Browser | JavaScript Engine |
|---|---|
| Chrome, Edge | V8 |
| Firefox | SpiderMonkey |
| Safari | JavaScriptCore |

Di browser, JavaScript dapat mengakses DOM, event, form, storage, dan API browser lainnya.

---

## 1.4 JavaScript di Server

JavaScript juga dapat berjalan di server menggunakan Node.js.

Dengan Node.js, JavaScript bisa digunakan untuk:

- Membuat REST API.
- Mengakses database.
- Membaca dan menulis file.
- Membuat command line tool.
- Menjalankan development server.

Contoh JavaScript di Node.js:

```javascript
console.log("Kode ini berjalan di Node.js");
```

---

## 1.5 Karakteristik JavaScript

Beberapa karakteristik JavaScript:

- Interpreted: kode dapat langsung dijalankan tanpa proses compile manual.
- Dynamic typing: tipe data variabel dapat berubah.
- Multi-paradigm: mendukung procedural, object-oriented, dan functional programming.
- Event-driven: banyak digunakan untuk merespons event seperti click, submit, dan input.
- Asynchronous: mendukung proses yang tidak langsung selesai, seperti request API.

---

## 1.6 Contoh Program Sederhana

```javascript
const nama = "Alya";
const umur = 20;

console.log("Nama:", nama);
console.log("Umur:", umur);

if (umur >= 18) {
  console.log("Sudah dewasa");
} else {
  console.log("Belum dewasa");
}
```

Program di atas menggunakan variabel, output, dan percabangan.

---

## Ringkasan

- JavaScript digunakan untuk membuat logika dan interaksi aplikasi.
- JavaScript dapat berjalan di browser dan server melalui Node.js.
- HTML, CSS, dan JavaScript memiliki peran berbeda dalam web development.

---

## Latihan

1. Jelaskan fungsi JavaScript dalam website.
2. Apa perbedaan HTML, CSS, dan JavaScript?
3. Sebutkan dua contoh penggunaan JavaScript.
4. Apa fungsi Node.js dalam ekosistem JavaScript?
