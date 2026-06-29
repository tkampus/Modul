# Modul Git: Remote, Clone, Pull, dan Push

Remote repository adalah repository yang berada di server, misalnya GitHub. Dengan remote repository, project dapat disimpan online dan dikerjakan bersama tim.

---

## Tujuan Pembelajaran

Setelah mempelajari modul ini, peserta diharapkan mampu:

1. Memahami remote repository.
2. Menyalin repository dengan `git clone`.
3. Menghubungkan repository lokal ke GitHub.
4. Mengambil perubahan dengan `git pull`.
5. Mengirim perubahan dengan `git push`.

---

## 1. Clone Repository

`git clone` digunakan untuk menyalin repository dari remote ke komputer lokal.

```bash
git clone https://github.com/username/nama-repository.git
```

Setelah clone selesai:

```bash
cd nama-repository
git status
```

---

## 2. Melihat Remote

Gunakan:

```bash
git remote -v
```

Contoh output:

```text
origin  https://github.com/username/project.git (fetch)
origin  https://github.com/username/project.git (push)
```

`origin` adalah nama default untuk remote utama.

---

## 3. Menghubungkan Repository Lokal ke GitHub

Jika repository dibuat dari lokal, tambahkan remote:

```bash
git remote add origin https://github.com/username/nama-repository.git
```

Lalu kirim branch utama:

```bash
git push -u origin main
```

Opsi `-u` membuat branch lokal terhubung dengan branch remote, sehingga push berikutnya cukup:

```bash
git push
```

---

## 4. Mengirim Perubahan dengan `git push`

Setelah membuat commit:

```bash
git push
```

Jika branch belum terhubung dengan remote:

```bash
git push -u origin nama-branch
```

---

## 5. Mengambil Perubahan dengan `git pull`

`git pull` digunakan untuk mengambil perubahan terbaru dari remote lalu menggabungkannya ke branch lokal.

```bash
git pull
```

Atau lebih spesifik:

```bash
git pull origin main
```

Biasakan menjalankan `git pull` sebelum mulai bekerja, terutama saat bekerja dalam tim.

---

## 6. Fetch vs Pull

| Command | Fungsi |
|---|---|
| `git fetch` | Mengambil informasi terbaru dari remote tanpa langsung menggabungkan |
| `git pull` | Mengambil informasi terbaru dan langsung menggabungkan ke branch aktif |

Contoh:

```bash
git fetch
git status
```

---

## Latihan

1. Buat repository baru di GitHub.
2. Hubungkan repository lokal dengan `git remote add origin`.
3. Push commit pertama menggunakan `git push -u origin main`.
4. Ubah file di GitHub, lalu ambil perubahannya dengan `git pull`.
