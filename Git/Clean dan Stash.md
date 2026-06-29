# Modul Git: Clean dan Stash

`git clean` digunakan untuk menghapus file yang belum dilacak Git. `git stash` digunakan untuk menyimpan perubahan sementara tanpa membuat commit.

---

## Tujuan Pembelajaran

Setelah mempelajari modul ini, peserta diharapkan mampu:

1. Membersihkan file untracked dengan `git clean`.
2. Melihat simulasi pembersihan sebelum menghapus file.
3. Menyimpan perubahan sementara dengan `git stash`.
4. Mengembalikan perubahan dari stash.

---

## 1. Memahami File Untracked

File untracked adalah file baru yang belum pernah dimasukkan ke Git.

Cek status:

```bash
git status
```

Contoh:

```text
Untracked files:
  catatan.txt
```

---

## 2. Simulasi `git clean`

Sebelum menghapus file, lihat dulu file apa saja yang akan dibersihkan:

```bash
git clean -n
```

Opsi `-n` berarti dry run atau simulasi.

---

## 3. Menghapus File Untracked

Menghapus file untracked:

```bash
git clean -f
```

Menghapus folder untracked:

```bash
git clean -fd
```

Menghapus file yang diabaikan `.gitignore` juga:

```bash
git clean -fdx
```

Gunakan `git clean -fdx` dengan sangat hati-hati karena dapat menghapus folder dependency, hasil build, atau file lokal lain.

---

## 4. Menyimpan Perubahan Sementara dengan Stash

Jika sedang mengerjakan sesuatu tetapi harus berpindah branch, simpan perubahan sementara:

```bash
git stash
```

Memberi pesan pada stash:

```bash
git stash push -m "Perubahan sementara halaman login"
```

Melihat daftar stash:

```bash
git stash list
```

---

## 5. Mengembalikan Stash

Mengembalikan stash terbaru tanpa menghapus dari daftar stash:

```bash
git stash apply
```

Mengembalikan stash terbaru dan menghapusnya dari daftar stash:

```bash
git stash pop
```

Menghapus stash tertentu:

```bash
git stash drop stash@{0}
```

Menghapus semua stash:

```bash
git stash clear
```

---

## 6. Kapan Menggunakan Clean dan Stash?

| Kebutuhan | Command |
|---|---|
| Melihat file untracked yang akan dihapus | `git clean -n` |
| Menghapus file untracked | `git clean -f` |
| Menghapus folder untracked | `git clean -fd` |
| Menyimpan perubahan sementara | `git stash` |
| Mengembalikan stash terbaru | `git stash pop` |

---

## Latihan

1. Buat file baru `sementara.txt`.
2. Jalankan `git status`.
3. Jalankan `git clean -n`.
4. Hapus file untracked dengan `git clean -f`.
5. Ubah file yang sudah dilacak.
6. Simpan perubahan dengan `git stash`.
7. Kembalikan perubahan dengan `git stash pop`.
