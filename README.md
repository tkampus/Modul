# AI Module Writing Guide

Dokumen ini digunakan sebagai pedoman AI dalam menghasilkan modul pembelajaran.

---

# Struktur Repository

```
/
│── index.md                 ← Halaman utama daftar
modul
│
├── Modul 1.md
├── Modul 2.md
├── Modul 3.md
└── ...
```

---

# Struktur index.md

Setiap materi memiliki satu halaman utama (`index.md`) yang berfungsi sebagai daftar isi seluruh modul.

Gunakan struktur berikut.

```md
# Judul Materi

Penjelasan singkat mengenai materi secara keseluruhan.

---

# Daftar Isi

Penjelasan singkat mengenai daftar modul.

---

## Peta Materi

| No | Modul | Fokus Materi |
|---|---|---|
| 1 | [Nama Modul](<Modul 1.md>) | Ringkasan materi |
| 2 | [Nama Modul](<Modul 2.md>) | Ringkasan materi |
| .. | [Mini Project](<Mini Project.md>) | Penjelasan Project |

---

## Target Pembelajaran

Setelah menyelesaikan seluruh modul, peserta diharapkan mampu:

- Target pembelajaran 1
- Target pembelajaran 2
- Target pembelajaran 3

---

Ditulis oleh: Muktashim Billah

Terakhir diperbarui: YYYY-MM-DD
```

---

# Struktur Modul

Setiap file modul wajib mengikuti struktur berikut.

```md
# Bagian X: Judul Modul

## Yang Akan Dibahas

Paragraf singkat mengenai isi modul.

## Tujuan Pembelajaran

Setelah mempelajari materi ini, peserta diharapkan mampu:

1. Tujuan pertama.
2. Tujuan kedua.
3. Tujuan ketiga.

---

Pendahuluan materi.

---

## X.1 Subjudul Pertama

Penjelasan konsep.

### Sintaks

```language
Kode
``

### Contoh

Penjelasan contoh.

```language
Kode
``

Hasil:

(Tampilkan output apabila diperlukan.)

---

## X.2 Subjudul Kedua

Penjelasan.

### Contoh

```language
Kode
``

Hasil:

(Tampilkan output apabila diperlukan.)

---

## Ringkasan

- Poin penting 1.
- Poin penting 2.
- Poin penting 3.

---

## Latihan

1. Soal pertama.
2. Soal kedua.
3. Soal ketiga.

---

Ditulis oleh: Muktashim Billah
Terakhir diperbarui: YYYY-MM-DD
```

---

# Aturan Penulisan

## Struktur

- Gunakan heading Markdown (`#`, `##`, `###`) secara konsisten.
- Gunakan pemisah `---` untuk setiap bagian utama.
- Gunakan tabel bila informasi lebih mudah dipahami dalam bentuk tabel.
- Gunakan bullet list atau numbered list sesuai kebutuhan.

## Penjelasan

- Mulai dari konsep paling dasar.
- Gunakan bahasa Indonesia yang formal dan mudah dipahami.
- Hindari penjelasan yang terlalu singkat maupun terlalu panjang.
- Setiap konsep penting sebaiknya disertai contoh.

## Contoh Kode

- Gunakan fenced code block.
- Beri nama bahasa pada code block.
- Format kode harus rapi.
- Sertakan output jika relevan.

## Contoh Output

Jika materi menghasilkan output (SQL, CLI, terminal, dsb.), tampilkan hasilnya menggunakan:

- Tabel Markdown.
- Code block.
- Screenshot (opsional).

## Konsistensi

Seluruh modul harus memiliki struktur yang sama agar mudah dibaca dan dinavigasi.

---

# Checklist Sebelum Modul Selesai

- [ ] Memiliki judul modul.
- [ ] Memiliki bagian "Yang Akan Dibahas".
- [ ] Memiliki tujuan pembelajaran.
- [ ] Memiliki penjelasan konsep.
- [ ] Memiliki contoh.
- [ ] Memiliki output contoh (jika diperlukan).
- [ ] Memiliki ringkasan.
- [ ] Memiliki latihan.