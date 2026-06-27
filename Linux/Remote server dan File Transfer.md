# 🌐 Modul Linux: Remote Server dan File Transfer

Remote server adalah server yang diakses dari komputer lain melalui jaringan. Di Linux, akses remote paling umum dilakukan menggunakan **SSH**. Untuk memindahkan file, pengguna dapat memakai `scp`, `rsync`, atau `sftp`.

Modul ini membahas cara mengakses server Linux secara remote dan mentransfer file antara komputer lokal dan server.

---

## 🎯 Tujuan Pembelajaran

Setelah mempelajari modul ini, peserta diharapkan mampu:

1. Menjelaskan konsep remote server.
2. Menggunakan SSH untuk masuk ke server Linux.
3. Memahami username, host, IP address, dan port.
4. Menggunakan SSH key untuk login yang lebih aman.
5. Mengirim dan mengambil file menggunakan `scp`.
6. Melakukan sinkronisasi file menggunakan `rsync`.
7. Menggunakan `sftp` untuk transfer file interaktif.

---

## 1. Apa Itu Remote Server?

Remote server adalah komputer server yang dapat diakses dari lokasi lain melalui jaringan atau internet.

Contoh remote server:

- VPS untuk hosting website.
- Server kampus atau kantor.
- Cloud server di AWS, Google Cloud, Azure, atau provider VPS.
- Server database.
- Server deployment aplikasi.

Untuk mengelola server Linux, administrator biasanya menggunakan terminal dan SSH.

---

## 2. Mengenal SSH

SSH atau Secure Shell adalah protokol untuk mengakses server secara aman melalui jaringan.

Format command SSH:

```bash
ssh username@alamat-server
```

Contoh:

```bash
ssh ubuntu@192.168.1.10
```

Jika server menggunakan port khusus:

```bash
ssh -p 2222 ubuntu@192.168.1.10
```

Keterangan:

- `ubuntu` adalah username di server.
- `192.168.1.10` adalah alamat IP server.
- `-p 2222` menunjukkan port SSH yang digunakan.

---

## 3. Login Menggunakan Password

Contoh login:

```bash
ssh user@server.example.com
```

Setelah menjalankan command, terminal akan meminta password user server.

Saat pertama kali login, biasanya muncul pertanyaan untuk menerima fingerprint server. Ketik:

```bash
yes
```

Setelah berhasil login, prompt terminal akan berubah menjadi prompt server.

---

## 4. Login Menggunakan SSH Key

SSH key lebih aman dan praktis dibanding password.

Membuat SSH key:

```bash
ssh-keygen
```

Menyalin public key ke server:

```bash
ssh-copy-id user@server.example.com
```

Login setelah key terpasang:

```bash
ssh user@server.example.com
```

File penting SSH:

| File | Fungsi |
|---|---|
| `~/.ssh/id_rsa` | Private key |
| `~/.ssh/id_rsa.pub` | Public key |
| `~/.ssh/known_hosts` | Daftar server yang pernah diakses |
| `~/.ssh/authorized_keys` | Public key yang diizinkan login ke server |

> Jangan membagikan private key kepada siapa pun.

---

## 5. Keluar dari Server

Untuk keluar dari sesi SSH:

```bash
exit
```

Atau tekan:

```bash
Ctrl + D
```

---

## 6. Transfer File dengan scp

`scp` digunakan untuk menyalin file melalui SSH.

Mengirim file dari lokal ke server:

```bash
scp file.txt user@server.example.com:/home/user/
```

Mengambil file dari server ke lokal:

```bash
scp user@server.example.com:/home/user/file.txt .
```

Mengirim folder:

```bash
scp -r folder/ user@server.example.com:/home/user/
```

Menggunakan port khusus:

```bash
scp -P 2222 file.txt user@server.example.com:/home/user/
```

Pada `scp`, opsi port menggunakan huruf besar `-P`.

---

## 7. Transfer File dengan rsync

`rsync` digunakan untuk sinkronisasi file dan folder. Tool ini efisien karena hanya mengirim perubahan.

Mengirim folder ke server:

```bash
rsync -av folder/ user@server.example.com:/home/user/folder/
```

Mengambil folder dari server:

```bash
rsync -av user@server.example.com:/home/user/folder/ ./folder/
```

Menggunakan port khusus:

```bash
rsync -av -e "ssh -p 2222" folder/ user@server.example.com:/home/user/folder/
```

Keterangan opsi:

- `-a` berarti archive mode.
- `-v` berarti verbose atau menampilkan proses.

---

## 8. Transfer File dengan sftp

`sftp` menyediakan mode transfer file interaktif.

Masuk ke SFTP:

```bash
sftp user@server.example.com
```

Command dasar di dalam SFTP:

| Command | Fungsi |
|---|---|
| `ls` | Melihat file di server |
| `lls` | Melihat file di lokal |
| `pwd` | Melihat lokasi di server |
| `lpwd` | Melihat lokasi di lokal |
| `put file.txt` | Upload file |
| `get file.txt` | Download file |
| `exit` | Keluar dari SFTP |

Contoh upload:

```bash
put index.html
```

Contoh download:

```bash
get backup.zip
```

---

## 9. Mengecek Koneksi Server

Menguji koneksi dasar:

```bash
ping server.example.com
```

Mengecek apakah port SSH terbuka:

```bash
ssh -v user@server.example.com
```

Opsi `-v` menampilkan informasi detail untuk troubleshooting.

---

## 10. Praktik

Gunakan server latihan atau VPS, lalu coba command berikut:

```bash
ssh user@alamat-server
pwd
ls
exit
```

Jika sudah berhasil, coba transfer file:

```bash
echo "Latihan transfer file" > latihan.txt
scp latihan.txt user@alamat-server:/home/user/
```

Tugas:

1. Apa fungsi SSH?
2. Apa perbedaan `scp` dan `rsync`?
3. Mengapa SSH key lebih disarankan daripada password?
4. Apa perbedaan opsi port SSH pada `ssh` dan `scp`?

---

## ✅ Kesimpulan

SSH adalah cara utama untuk mengelola server Linux dari jarak jauh. Untuk transfer file, pengguna dapat menggunakan `scp` untuk salin file sederhana, `rsync` untuk sinkronisasi yang efisien, dan `sftp` untuk transfer interaktif.

---

[⬅️ Kembali ke Daftar Isi](<index.md>)

✍️ **Dibuat oleh:** Muktashim Billah  
📅 **Terakhir diperbarui:** 28 Juni 2026
