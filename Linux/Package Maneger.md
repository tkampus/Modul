# 📦 Modul Linux: Package Manager

Package manager adalah alat untuk menginstal, memperbarui, menghapus, dan mencari software di Linux. Dengan package manager, pengguna tidak perlu mengunduh installer secara manual dari banyak website.

Modul ini membahas konsep package manager, repository, serta contoh penggunaan pada beberapa distribusi Linux.

---

## 🎯 Tujuan Pembelajaran

Setelah mempelajari modul ini, peserta diharapkan mampu:

1. Menjelaskan fungsi package manager.
2. Memahami konsep package dan repository.
3. Menggunakan `apt` pada Ubuntu/Debian.
4. Mengenal package manager pada distro lain.
5. Menginstal, memperbarui, mencari, dan menghapus aplikasi.
6. Melakukan troubleshooting dasar package manager.

---

## 1. Apa Itu Package?

Package adalah paket software yang berisi aplikasi, library, konfigurasi, atau dependency yang dibutuhkan oleh sistem.

Contoh package:

- `git`
- `curl`
- `nginx`
- `mysql-server`
- `python3`
- `vim`

Package manager akan membantu memastikan aplikasi dan dependency yang dibutuhkan terpasang dengan benar.

---

## 2. Apa Itu Repository?

Repository adalah tempat penyimpanan package. Saat menginstal aplikasi, Linux mengambil package dari repository yang sudah dikonfigurasi.

Alur sederhananya:

```text
User menjalankan command -> Package manager -> Repository -> Package terinstal
```

Keuntungan repository:

- Software lebih mudah dicari.
- Update lebih terpusat.
- Dependency dikelola otomatis.
- Lebih aman dibanding mengunduh file sembarangan.

---

## 3. Package Manager Populer

| Distro | Package Manager | Contoh Command |
|---|---|---|
| Ubuntu/Debian | `apt` | `sudo apt install git` |
| Fedora | `dnf` | `sudo dnf install git` |
| Arch Linux | `pacman` | `sudo pacman -S git` |
| openSUSE | `zypper` | `sudo zypper install git` |
| Alpine Linux | `apk` | `sudo apk add git` |

Dalam pelatihan dasar, Ubuntu/Debian sering menggunakan `apt`.

---

## 4. Menggunakan apt pada Ubuntu/Debian

Memperbarui daftar package:

```bash
sudo apt update
```

Meng-upgrade package yang sudah terpasang:

```bash
sudo apt upgrade
```

Menginstal package:

```bash
sudo apt install git
```

Menghapus package:

```bash
sudo apt remove git
```

Menghapus package beserta file konfigurasi:

```bash
sudo apt purge git
```

Membersihkan package yang tidak lagi dibutuhkan:

```bash
sudo apt autoremove
```

---

## 5. Mencari dan Melihat Informasi Package

Mencari package:

```bash
apt search nginx
```

Melihat informasi package:

```bash
apt show nginx
```

Melihat package yang sudah terinstal:

```bash
apt list --installed
```

Melihat lokasi program:

```bash
which git
```

Melihat versi program:

```bash
git --version
```

---

## 6. Perbedaan update dan upgrade

`apt update` tidak menginstal versi baru aplikasi. Command ini hanya memperbarui daftar informasi package dari repository.

`apt upgrade` digunakan untuk meng-upgrade package yang sudah terpasang ke versi yang lebih baru.

Urutan yang umum:

```bash
sudo apt update
sudo apt upgrade
```

---

## 7. Instalasi dari File .deb

Pada Ubuntu/Debian, aplikasi juga dapat tersedia dalam file `.deb`.

Menginstal file `.deb`:

```bash
sudo apt install ./nama-file.deb
```

Atau menggunakan `dpkg`:

```bash
sudo dpkg -i nama-file.deb
sudo apt install -f
```

Command `sudo apt install -f` digunakan untuk memperbaiki dependency yang belum terpenuhi.

---

## 8. Troubleshooting Dasar

Jika package manager terkunci karena proses lain:

```bash
ps aux | grep apt
```

Jika ada dependency bermasalah:

```bash
sudo apt install -f
```

Jika cache package ingin dibersihkan:

```bash
sudo apt clean
```

Jika repository belum lengkap, periksa file:

```bash
/etc/apt/sources.list
```

> Hati-hati mengubah konfigurasi repository. Gunakan repository resmi atau sumber yang terpercaya.

---

## 9. Praktik

Jalankan latihan berikut:

```bash
sudo apt update
apt search tree
sudo apt install tree
tree --version
sudo apt remove tree
```

Tugas:

1. Apa fungsi `sudo apt update`?
2. Apa perbedaan `apt remove` dan `apt purge`?
3. Mengapa package manager membutuhkan repository?
4. Apa fungsi dependency?

---

## ✅ Kesimpulan

Package manager memudahkan pengguna Linux untuk mengelola software secara aman dan terpusat. Pada Ubuntu/Debian, command utama yang sering digunakan adalah `apt update`, `apt upgrade`, `apt install`, `apt remove`, `apt search`, dan `apt show`.

---

[⬅️ Kembali ke Daftar Isi](<index.md>)

✍️ **Dibuat oleh:** Muktashim Billah  
📅 **Terakhir diperbarui:** 28 Juni 2026
