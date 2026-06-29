# Modul Git: Merge dan Conflict

Merge digunakan untuk menggabungkan perubahan dari satu branch ke branch lain. Conflict terjadi ketika Git tidak bisa menentukan perubahan mana yang harus dipakai.

---

## Tujuan Pembelajaran

Setelah mempelajari modul ini, peserta diharapkan mampu:

1. Menggabungkan branch dengan `git merge`.
2. Memahami penyebab conflict.
3. Menyelesaikan conflict secara manual.
4. Melanjutkan proses merge setelah conflict selesai.

---

## 1. Menggabungkan Branch

Misalnya perubahan di branch `fitur-login` ingin digabung ke `main`.

Pindah ke branch tujuan:

```bash
git switch main
```

Pastikan branch utama terbaru:

```bash
git pull
```

Gabungkan branch:

```bash
git merge fitur-login
```

Jika tidak ada conflict, Git akan menyelesaikan merge secara otomatis.

---

## 2. Penyebab Conflict

Conflict biasanya terjadi ketika dua branch mengubah baris yang sama pada file yang sama.

Contoh:

- Branch `main` mengubah judul halaman.
- Branch `fitur-login` juga mengubah judul halaman yang sama.
- Saat merge, Git tidak tahu versi mana yang harus dipakai.

---

## 3. Bentuk Conflict di File

Saat conflict, isi file akan terlihat seperti ini:

```text
<<<<<<< HEAD
Judul dari branch main
=======
Judul dari branch fitur-login
>>>>>>> fitur-login
```

Keterangan:

- Bagian `HEAD` adalah isi dari branch yang sedang aktif.
- Bagian setelah `=======` adalah isi dari branch yang sedang digabung.

---

## 4. Menyelesaikan Conflict

Langkah penyelesaian:

1. Buka file yang conflict.
2. Pilih isi yang benar atau gabungkan keduanya.
3. Hapus tanda `<<<<<<<`, `=======`, dan `>>>>>>>`.
4. Simpan file.
5. Jalankan `git add`.
6. Jalankan `git commit` jika diperlukan.

Contoh:

```bash
git status
git add nama-file
git commit
```

Pada beberapa kondisi, Git otomatis membuat commit merge setelah conflict diselesaikan.

---

## 5. Membatalkan Merge

Jika ingin membatalkan proses merge yang sedang conflict:

```bash
git merge --abort
```

Command ini mengembalikan repository ke kondisi sebelum merge.

---

## Latihan

1. Buat branch `fitur-a`.
2. Ubah satu baris di file `README.md`, lalu commit.
3. Pindah ke `main`.
4. Ubah baris yang sama, lalu commit.
5. Merge branch `fitur-a` ke `main`.
6. Selesaikan conflict yang muncul.
