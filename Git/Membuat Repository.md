# Modul Git: Membuat Repository

Repository adalah folder project yang dipantau oleh Git. Di dalam repository, Git menyimpan riwayat perubahan file.

---

## Tujuan Pembelajaran

Setelah mempelajari modul ini, peserta diharapkan mampu:

1. Membuat repository lokal.
2. Memahami fungsi folder `.git`.
3. Mengecek status repository.
4. Mengabaikan file tertentu dengan `.gitignore`.

---

## 1. Membuat Folder Project

Buat folder latihan:

```bash
mkdir latihan-git
cd latihan-git
```

Buat file awal:

```bash
touch README.md
```

---

## 2. Membuat Repository dengan `git init`

Jalankan:

```bash
git init
```

Command ini akan membuat folder tersembunyi bernama `.git`.

Folder `.git` berisi data internal Git, seperti konfigurasi repository, riwayat commit, branch, dan informasi perubahan.

---

## 3. Mengecek Status Repository

Gunakan:

```bash
git status
```

Contoh output saat ada file baru:

```text
Untracked files:
  README.md
```

`Untracked files` berarti file tersebut belum dilacak oleh Git.

---

## 4. Membuat Repository dari Folder yang Sudah Ada

Jika project sudah ada, masuk ke folder project:

```bash
cd nama-project
git init
git status
```

Setelah itu, file dapat dimasukkan ke Git menggunakan `git add` dan `git commit`.

---

## 5. Menggunakan `.gitignore`

File `.gitignore` digunakan untuk memberi tahu Git agar tidak melacak file tertentu.

Buat file `.gitignore`:

```bash
touch .gitignore
```

Contoh isi `.gitignore`:

```gitignore
node_modules/
.env
vendor/
dist/
*.log
```

File yang biasanya diabaikan:

| File atau Folder | Alasan |
|---|---|
| `.env` | Berisi password, token, atau konfigurasi rahasia |
| `node_modules/` | Folder dependency yang bisa diunduh ulang |
| `vendor/` | Dependency PHP dari Composer |
| `dist/` | Hasil build aplikasi |
| `*.log` | File catatan sistem atau aplikasi |

---

## Latihan

1. Buat folder `latihan-git`.
2. Jalankan `git init`.
3. Buat file `README.md`.
4. Jalankan `git status`.
5. Buat file `.gitignore` dan isi dengan `.env`.
