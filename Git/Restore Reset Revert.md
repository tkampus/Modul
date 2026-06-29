# Modul Git: Restore, Reset, dan Revert

Git menyediakan beberapa command untuk membatalkan atau mengembalikan perubahan. Tiga command yang sering digunakan adalah `restore`, `reset`, dan `revert`.

---

## Tujuan Pembelajaran

Setelah mempelajari modul ini, peserta diharapkan mampu:

1. Mengembalikan perubahan file dengan `git restore`.
2. Mengeluarkan file dari staging area.
3. Membatalkan commit dengan `git reset`.
4. Membuat commit pembalik dengan `git revert`.

---

## 1. `git restore`

`git restore` digunakan untuk mengembalikan file di working directory.

Misalnya file `README.md` sudah diubah tetapi belum di-commit:

```bash
git restore README.md
```

Command ini membuang perubahan yang belum masuk commit.

Mengembalikan semua perubahan file yang sudah dilacak:

```bash
git restore .
```

Gunakan dengan hati-hati karena perubahan lokal akan hilang.

---

## 2. Mengeluarkan File dari Staging Area

Jika file sudah terlanjur di-`add`:

```bash
git restore --staged README.md
```

Command ini hanya mengeluarkan file dari staging area. Isi file tetap berubah di working directory.

---

## 3. `git reset`

`git reset` digunakan untuk memindahkan posisi branch ke commit tertentu.

Jenis reset:

| Command | Efek |
|---|---|
| `git reset --soft HEAD~1` | Membatalkan commit terakhir, perubahan tetap staged |
| `git reset --mixed HEAD~1` | Membatalkan commit terakhir, perubahan tidak staged |
| `git reset --hard HEAD~1` | Membatalkan commit terakhir dan membuang perubahan |

Contoh:

```bash
git reset --soft HEAD~1
```

`HEAD~1` berarti satu commit sebelum commit saat ini.

Gunakan `--hard` dengan sangat hati-hati karena perubahan dapat hilang.

---

## 4. `git revert`

`git revert` digunakan untuk membatalkan efek commit dengan membuat commit baru.

```bash
git revert commit_hash
```

Contoh:

```bash
git revert a1b2c3d
```

`revert` lebih aman untuk branch yang sudah dibagikan ke remote karena tidak mengubah riwayat commit lama.

---

## 5. Kapan Menggunakan Apa?

| Kebutuhan | Command |
|---|---|
| Membuang perubahan file yang belum commit | `git restore nama-file` |
| Mengeluarkan file dari staging area | `git restore --staged nama-file` |
| Membatalkan commit lokal terakhir | `git reset --soft HEAD~1` |
| Membuang commit dan perubahan lokal | `git reset --hard HEAD~1` |
| Membatalkan commit yang sudah terlanjur dipush | `git revert commit_hash` |

---

## Latihan

1. Ubah file `README.md`.
2. Jalankan `git status`.
3. Batalkan perubahan dengan `git restore README.md`.
4. Buat commit baru.
5. Batalkan commit terakhir dengan `git reset --soft HEAD~1`.
