# 👥 Modul Linux: Users dan Group

Linux adalah sistem operasi multi-user, artinya satu sistem dapat digunakan oleh banyak pengguna. Agar sistem tetap aman dan teratur, Linux menyediakan mekanisme **user**, **group**, dan **permission**.

Modul ini membahas cara memahami dan mengelola user serta group di Linux menggunakan terminal.

---

## 🎯 Tujuan Pembelajaran

Setelah mempelajari modul ini, peserta diharapkan mampu:

1. Menjelaskan konsep user dan group di Linux.
2. Membedakan user biasa, root, dan system user.
3. Melihat informasi user yang sedang digunakan.
4. Membuat, mengubah, dan menghapus user.
5. Membuat dan mengelola group.
6. Memberikan hak akses administrator menggunakan `sudo`.

---

## 1. Konsep User di Linux

User adalah akun yang digunakan untuk masuk dan menjalankan aktivitas di sistem Linux.

Jenis user yang umum:

| Jenis User | Keterangan |
|---|---|
| User biasa | Akun pengguna harian |
| Root | Administrator tertinggi di Linux |
| System user | Akun khusus untuk menjalankan service atau aplikasi |

Setiap user memiliki:

- Username.
- User ID atau UID.
- Home directory.
- Default shell.
- Group utama.

---

## 2. Konsep Group di Linux

Group digunakan untuk mengelompokkan beberapa user agar pengaturan hak akses menjadi lebih mudah.

Contoh penggunaan group:

- Group `developers` untuk tim developer.
- Group `admin` untuk user administrator.
- Group `www-data` untuk web server.

Dengan group, beberapa user dapat diberi akses ke folder atau file yang sama tanpa harus mengatur permission satu per satu.

---

## 3. Melihat Informasi User

Melihat user yang sedang aktif:

```bash
whoami
```

Melihat UID, GID, dan group user:

```bash
id
```

Melihat user yang sedang login:

```bash
who
```

Melihat informasi login terakhir:

```bash
last
```

---

## 4. File Penting User dan Group

Linux menyimpan informasi user dan group pada beberapa file penting.

| File | Fungsi |
|---|---|
| `/etc/passwd` | Menyimpan informasi user |
| `/etc/shadow` | Menyimpan password terenkripsi |
| `/etc/group` | Menyimpan informasi group |
| `/etc/sudoers` | Mengatur hak akses `sudo` |

Melihat daftar user:

```bash
cat /etc/passwd
```

Melihat daftar group:

```bash
cat /etc/group
```

> Jangan mengedit file sistem penting secara sembarangan. Gunakan command resmi seperti `useradd`, `usermod`, dan `groupadd`.

---

## 5. Membuat User Baru

Membuat user baru:

```bash
sudo adduser namauser
```

Contoh:

```bash
sudo adduser siswa
```

Command `adduser` biasanya akan membuat home directory, meminta password, dan menanyakan beberapa informasi tambahan.

Alternatif command tingkat rendah:

```bash
sudo useradd namauser
```

Pada banyak distro, `adduser` lebih nyaman untuk pemula dibanding `useradd`.

---

## 6. Mengubah Password User

Mengubah password user sendiri:

```bash
passwd
```

Mengubah password user lain:

```bash
sudo passwd siswa
```

Command ini sering digunakan administrator ketika membuat akun baru atau melakukan reset password.

---

## 7. Menghapus User

Menghapus user:

```bash
sudo deluser siswa
```

Menghapus user beserta home directory:

```bash
sudo deluser --remove-home siswa
```

Pastikan data penting sudah dipindahkan sebelum menghapus user.

---

## 8. Membuat dan Mengelola Group

Membuat group baru:

```bash
sudo groupadd developers
```

Menambahkan user ke group:

```bash
sudo usermod -aG developers siswa
```

Keterangan:

- `-a` berarti append atau menambahkan.
- `-G` berarti supplementary group.

Melihat group milik user:

```bash
groups siswa
```

Menghapus group:

```bash
sudo groupdel developers
```

---

## 9. Hak Akses Administrator dengan sudo

`sudo` digunakan untuk menjalankan command dengan hak akses administrator.

Contoh:

```bash
sudo apt update
```

Menambahkan user ke group `sudo`:

```bash
sudo usermod -aG sudo siswa
```

Setelah itu, user biasanya perlu logout dan login kembali agar perubahan group aktif.

---

## 10. Praktik

Jalankan latihan berikut pada lingkungan Linux latihan:

```bash
whoami
id
sudo adduser latihan
sudo groupadd kelaslinux
sudo usermod -aG kelaslinux latihan
groups latihan
```

Tugas:

1. Jelaskan fungsi command `id`.
2. Apa perbedaan user dan group?
3. Mengapa opsi `-aG` penting ketika menambahkan user ke group?
4. Apa risiko memberikan akses `sudo` kepada user yang tidak tepat?

---

## ✅ Kesimpulan

User dan group adalah bagian penting dalam administrasi Linux. Dengan memahami user, group, root, dan `sudo`, administrator dapat mengatur siapa saja yang boleh mengakses sistem serta membatasi hak pengguna sesuai kebutuhan.

---

[⬅️ Kembali ke Daftar Isi](<index.md>)

✍️ **Dibuat oleh:** Muktashim Billah  
📅 **Terakhir diperbarui:** 28 Juni 2026
