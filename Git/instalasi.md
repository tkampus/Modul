# Modul Git: Instalasi dan Konfigurasi

Sebelum menggunakan Git, komputer harus memiliki aplikasi Git. Setelah itu, Git perlu dikonfigurasi agar setiap commit memiliki identitas pembuat.

---

## Tujuan Pembelajaran

Setelah mempelajari modul ini, peserta diharapkan mampu:

1. Menginstal Git di Windows, macOS, dan Linux.
2. Mengecek versi Git.
3. Mengatur nama dan email Git.
4. Memahami konfigurasi dasar Git.

---

## 1. Instalasi Git di Windows

1. Buka halaman resmi Git: `https://git-scm.com/downloads`
2. Pilih Windows.
3. Jalankan installer.
4. Gunakan pengaturan default jika belum memahami opsi instalasi.
5. Setelah selesai, buka Git Bash atau Command Prompt.

Cek instalasi:

```bash
git --version
```

Jika berhasil, akan muncul versi Git, misalnya:

```bash
git version 2.45.0
```

---

## 2. Instalasi Git di macOS

Cara termudah adalah menggunakan command berikut:

```bash
git --version
```

Jika Git belum tersedia, macOS biasanya akan menawarkan instalasi Command Line Tools.

Jika menggunakan Homebrew:

```bash
brew install git
```

---

## 3. Instalasi Git di Linux

Ubuntu atau Debian:

```bash
sudo apt update
sudo apt install git
```

Fedora:

```bash
sudo dnf install git
```

Arch Linux:

```bash
sudo pacman -S git
```

Cek versi:

```bash
git --version
```

---

## 4. Konfigurasi Nama dan Email

Git menggunakan nama dan email untuk mencatat siapa pembuat commit.

```bash
git config --global user.name "Nama Anda"
git config --global user.email "email@example.com"
```

Contoh:

```bash
git config --global user.name "Muktashim Billah"
git config --global user.email "muktashim@example.com"
```

Melihat konfigurasi:

```bash
git config --list
```

Melihat konfigurasi tertentu:

```bash
git config user.name
git config user.email
```

---

## 5. Mengatur Default Branch

Banyak repository modern menggunakan `main` sebagai nama branch utama.

```bash
git config --global init.defaultBranch main
```

Dengan konfigurasi ini, saat membuat repository baru menggunakan `git init`, branch awal akan bernama `main`.

---

## Latihan

1. Instal Git di komputer.
2. Jalankan `git --version`.
3. Atur `user.name` dan `user.email`.
4. Tampilkan konfigurasi Git dengan `git config --list`.
