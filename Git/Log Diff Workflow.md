# Modul Git: Log, Diff, dan Praktik Workflow

Modul ini membahas cara membaca riwayat commit, membandingkan perubahan, dan menjalankan workflow Git sederhana dari awal sampai akhir.

---

## Tujuan Pembelajaran

Setelah mempelajari modul ini, peserta diharapkan mampu:

1. Melihat riwayat commit dengan `git log`.
2. Membandingkan perubahan dengan `git diff`.
3. Menjalankan workflow Git harian.
4. Melakukan praktik dari membuat branch sampai push.

---

## 1. Melihat Riwayat Commit

Melihat log lengkap:

```bash
git log
```

Melihat log ringkas:

```bash
git log --oneline
```

Melihat log dengan grafik branch:

```bash
git log --oneline --graph --all
```

---

## 2. Membandingkan Perubahan dengan `git diff`

Melihat perubahan yang belum masuk staging area:

```bash
git diff
```

Melihat perubahan yang sudah staged:

```bash
git diff --staged
```

Membandingkan dua commit:

```bash
git diff commit_hash_1 commit_hash_2
```

Contoh:

```bash
git diff a1b2c3d e4f5g6h
```

---

## 3. Workflow Harian Git

Alur kerja yang umum digunakan:

```bash
git switch main
git pull
git switch -c fitur-baru
```

Setelah mengubah file:

```bash
git status
git diff
git add .
git commit -m "Menambahkan fitur baru"
git push -u origin fitur-baru
```

Setelah branch digabung ke `main`, branch lokal dapat dihapus:

```bash
git switch main
git pull
git branch -d fitur-baru
```

---

## 4. Praktik Lengkap

Ikuti langkah berikut:

```bash
mkdir praktik-git
cd praktik-git
git init
git config user.name "Nama Anda"
git config user.email "email@example.com"
```

Buat file:

```bash
touch README.md
```

Isi file `README.md`, lalu simpan:

```bash
git status
git add README.md
git commit -m "Menambahkan README"
```

Buat branch fitur:

```bash
git switch -c fitur-dokumentasi
```

Ubah `README.md`, lalu:

```bash
git status
git diff
git add .
git commit -m "Memperbarui dokumentasi"
```

Gabungkan ke `main`:

```bash
git switch main
git merge fitur-dokumentasi
git log --oneline --graph --all
```

---

## 5. Checklist Sebelum Push

Sebelum menjalankan `git push`, biasakan cek:

```bash
git status
git log --oneline -5
```

Pastikan:

- Tidak ada file rahasia seperti `.env`.
- Pesan commit jelas.
- Branch yang aktif sudah benar.
- Perubahan sudah dites jika project memiliki test.

---

## Latihan Akhir

1. Buat repository lokal baru.
2. Buat commit pertama.
3. Buat branch `fitur-kontak`.
4. Tambahkan file `kontak.md`.
5. Commit perubahan.
6. Merge branch ke `main`.
7. Lihat riwayat dengan `git log --oneline --graph --all`.
