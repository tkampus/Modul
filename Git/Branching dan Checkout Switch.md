# Modul Git: Branching dan Checkout Switch

Branch adalah jalur kerja terpisah dalam repository. Dengan branch, developer dapat mengembangkan fitur baru tanpa langsung mengubah branch utama.

---

## Tujuan Pembelajaran

Setelah mempelajari modul ini, peserta diharapkan mampu:

1. Memahami fungsi branch.
2. Membuat branch baru.
3. Berpindah branch.
4. Menghapus branch.
5. Menggunakan workflow feature branch.

---

## 1. Melihat Daftar Branch

Gunakan:

```bash
git branch
```

Branch yang sedang aktif ditandai dengan simbol `*`.

Melihat branch lokal dan remote:

```bash
git branch -a
```

---

## 2. Membuat Branch Baru

```bash
git branch fitur-login
```

Command ini hanya membuat branch, belum berpindah ke branch tersebut.

---

## 3. Berpindah Branch

Menggunakan `switch`:

```bash
git switch fitur-login
```

Menggunakan `checkout`:

```bash
git checkout fitur-login
```

`git switch` lebih baru dan lebih jelas untuk berpindah branch. `git checkout` masih banyak ditemukan di dokumentasi lama.

---

## 4. Membuat dan Langsung Berpindah Branch

Menggunakan `switch`:

```bash
git switch -c fitur-login
```

Menggunakan `checkout`:

```bash
git checkout -b fitur-login
```

---

## 5. Menghapus Branch

Menghapus branch yang sudah selesai digabung:

```bash
git branch -d fitur-login
```

Menghapus paksa branch lokal:

```bash
git branch -D fitur-login
```

Gunakan `-D` dengan hati-hati karena branch dapat terhapus walaupun belum digabung.

---

## 6. Push Branch ke Remote

```bash
git push -u origin fitur-login
```

Setelah itu, push berikutnya cukup:

```bash
git push
```

---

## 7. Workflow Feature Branch

Contoh alur kerja:

```bash
git switch main
git pull
git switch -c fitur-login
```

Lakukan perubahan, lalu:

```bash
git add .
git commit -m "Menambahkan fitur login"
git push -u origin fitur-login
```

Setelah fitur selesai, branch dapat digabung ke `main` melalui merge atau pull request.

---

## Latihan

1. Buat branch `fitur-profil`.
2. Pindah ke branch tersebut.
3. Buat file `profil.md`.
4. Commit perubahan.
5. Push branch ke remote.
