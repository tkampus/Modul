# Modul Git: Pengenalan

Git adalah version control system yang digunakan untuk mencatat perubahan pada file project. Dengan Git, developer dapat melihat riwayat perubahan, kembali ke versi sebelumnya, bekerja di branch terpisah, dan berkolaborasi dengan tim.

Git banyak digunakan dalam pengembangan aplikasi, dokumentasi, DevOps, open source, dan workflow kerja berbasis repository seperti GitHub, GitLab, atau Bitbucket.

---

## Tujuan Pembelajaran

Setelah mempelajari modul ini, peserta diharapkan mampu:

1. Memahami fungsi Git.
2. Memahami perbedaan Git dan GitHub.
3. Mengenal istilah penting dalam Git.
4. Memahami alur kerja dasar Git.

---

## 1. Apa Itu Version Control?

Version control adalah sistem untuk mencatat perubahan file dari waktu ke waktu.

Tanpa version control, biasanya file disimpan seperti ini:

```text
project-final.zip
project-final-revisi.zip
project-final-revisi-banget.zip
project-fix-terakhir.zip
```

Dengan Git, setiap perubahan penting disimpan sebagai commit. Commit berisi catatan perubahan, pembuat perubahan, waktu perubahan, dan pesan penjelasan.

---

## 2. Git dan GitHub

Git dan GitHub sering disebut bersamaan, tetapi keduanya berbeda.

| Istilah | Penjelasan |
|---|---|
| Git | Aplikasi version control yang berjalan di komputer lokal |
| GitHub | Platform online untuk menyimpan repository Git dan kolaborasi |

Git dapat digunakan tanpa GitHub. Namun, GitHub memudahkan backup, kolaborasi, pull request, issue tracking, dan publikasi project.

---

## 3. Istilah Penting dalam Git

| Istilah | Arti |
|---|---|
| Repository | Folder project yang dipantau oleh Git |
| Commit | Simpanan perubahan pada satu titik waktu |
| Branch | Jalur kerja terpisah dari branch utama |
| Remote | Repository yang berada di server seperti GitHub |
| Clone | Menyalin repository remote ke komputer lokal |
| Pull | Mengambil perubahan terbaru dari remote |
| Push | Mengirim commit lokal ke remote |
| Merge | Menggabungkan perubahan dari branch lain |
| Conflict | Benturan perubahan pada bagian file yang sama |

---

## 4. Alur Kerja Dasar Git

Alur kerja Git yang paling umum:

```bash
git status
git add .
git commit -m "Menambahkan halaman login"
git push
```

Keterangan:

- `git status` melihat kondisi repository.
- `git add .` memasukkan perubahan ke staging area.
- `git commit` menyimpan perubahan ke riwayat Git.
- `git push` mengirim commit ke remote repository.

---

## 5. Area Kerja Git

Git memiliki tiga area utama:

| Area | Fungsi |
|---|---|
| Working directory | Tempat file diedit |
| Staging area | Tempat perubahan disiapkan sebelum commit |
| Repository | Tempat commit disimpan |

Urutannya:

```text
Working directory -> Staging area -> Repository
```

---

## Latihan

Jawab pertanyaan berikut:

1. Apa fungsi utama Git?
2. Apa perbedaan Git dan GitHub?
3. Apa itu commit?
4. Mengapa branch berguna dalam kerja tim?
