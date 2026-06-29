# Modul Git: Add, Status, dan Commit

Setelah repository dibuat, perubahan file perlu disimpan ke riwayat Git. Proses ini dilakukan melalui `git add` dan `git commit`.

---

## Tujuan Pembelajaran

Setelah mempelajari modul ini, peserta diharapkan mampu:

1. Mengecek perubahan dengan `git status`.
2. Memasukkan perubahan ke staging area dengan `git add`.
3. Menyimpan perubahan dengan `git commit`.
4. Menulis pesan commit yang jelas.

---

## 1. Melihat Status Perubahan

Gunakan:

```bash
git status
```

Status yang sering muncul:

| Status | Arti |
|---|---|
| Untracked | File baru belum dilacak Git |
| Modified | File yang sudah dilacak mengalami perubahan |
| Staged | Perubahan sudah siap untuk commit |
| Clean | Tidak ada perubahan yang belum disimpan |

---

## 2. Memasukkan File ke Staging Area

Memasukkan satu file:

```bash
git add README.md
```

Memasukkan semua perubahan:

```bash
git add .
```

Memasukkan semua file dengan ekstensi tertentu:

```bash
git add *.md
```

---

## 3. Membuat Commit

Commit digunakan untuk menyimpan perubahan ke riwayat Git.

```bash
git commit -m "Menambahkan README"
```

Pesan commit sebaiknya singkat, jelas, dan menjelaskan perubahan.

Contoh pesan commit yang baik:

```text
Menambahkan halaman login
Memperbaiki validasi form register
Menambahkan dokumentasi instalasi
```

Contoh pesan commit yang kurang jelas:

```text
update
fix
revisi
asd
```

---

## 4. Melihat Riwayat Commit

Gunakan:

```bash
git log
```

Versi ringkas:

```bash
git log --oneline
```

Contoh output:

```text
a1b2c3d Menambahkan README
```

Kode di awal baris disebut commit hash. Hash digunakan sebagai identitas commit.

---

## 5. Mengubah Pesan Commit Terakhir

Jika pesan commit terakhir salah:

```bash
git commit --amend -m "Pesan commit baru"
```

Gunakan command ini hanya jika commit tersebut belum dibagikan ke orang lain.

---

## Latihan

1. Buat file `README.md`.
2. Isi file dengan deskripsi project.
3. Jalankan `git status`.
4. Jalankan `git add README.md`.
5. Jalankan `git commit -m "Menambahkan README"`.
6. Lihat riwayat dengan `git log --oneline`.
