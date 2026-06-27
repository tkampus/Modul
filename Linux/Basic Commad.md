# 🐧 Modul Pembelajaran Linux: Basic Command

Linux adalah sistem operasi yang banyak digunakan untuk server, cloud, DevOps, cybersecurity, pengembangan aplikasi, dan administrasi jaringan. Salah satu kemampuan dasar yang wajib dikuasai adalah menggunakan **terminal** atau **command line**.

Modul ini membahas perintah-perintah dasar Linux yang sering dipakai untuk berpindah folder, melihat isi file, membuat file, mengelola direktori, mencari data, hingga memahami hak akses.

---

## 🎯 Tujuan Pembelajaran

Setelah mempelajari modul ini, peserta diharapkan mampu:

1. Memahami fungsi terminal di Linux.
2. Menjalankan command dasar Linux dengan benar.
3. Mengelola file dan folder melalui terminal.
4. Membaca isi file menggunakan command line.
5. Memahami konsep path, permission, dan user dasar.
6. Melakukan latihan sederhana menggunakan command Linux.

---

## 1. Mengenal Terminal Linux

Terminal adalah aplikasi untuk menjalankan perintah berbasis teks. Melalui terminal, pengguna dapat mengontrol sistem Linux secara cepat dan efisien.

Contoh tampilan prompt terminal:

```bash
user@hostname:~$
```

Keterangan:

- `user` adalah nama pengguna yang sedang login.
- `hostname` adalah nama komputer atau server.
- `~` menunjukkan direktori home pengguna.
- `$` menunjukkan user biasa.
- `#` biasanya menunjukkan user root atau administrator.

---

## 2. Struktur Direktori Linux

Linux menggunakan struktur folder berbentuk hierarki yang dimulai dari root directory `/`.

Beberapa direktori penting:

| Direktori | Fungsi |
|---|---|
| `/` | Direktori utama Linux |
| `/home` | Folder user biasa |
| `/root` | Folder user root |
| `/etc` | File konfigurasi sistem |
| `/var` | File log dan data yang sering berubah |
| `/tmp` | File sementara |
| `/usr` | Program dan library aplikasi |
| `/bin` | Command dasar sistem |

Contoh:

```bash
/home/muktashim/Documents
```

Artinya folder `Documents` berada di dalam folder user `muktashim`.

---

## 3. Command Dasar Navigasi Direktori

### `pwd`

Digunakan untuk melihat lokasi direktori saat ini.

```bash
pwd
```

Contoh output:

```bash
/home/user
```

### `ls`

Digunakan untuk melihat isi direktori.

```bash
ls
```

Beberapa opsi yang sering digunakan:

```bash
ls -l
ls -a
ls -la
```

Keterangan:

- `ls -l` menampilkan detail file dan folder.
- `ls -a` menampilkan file tersembunyi.
- `ls -la` menampilkan detail termasuk file tersembunyi.

### `cd`

Digunakan untuk berpindah direktori.

```bash
cd Documents
```

Contoh penggunaan:

```bash
cd /home/user/Documents
cd ..
cd ~
cd -
```

Keterangan:

- `cd ..` naik satu folder.
- `cd ~` masuk ke home directory.
- `cd -` kembali ke direktori sebelumnya.

---

## 4. Command Mengelola File dan Folder

### `mkdir`

Digunakan untuk membuat folder baru.

```bash
mkdir latihan-linux
```

Membuat folder bertingkat:

```bash
mkdir -p project/src/components
```

### `touch`

Digunakan untuk membuat file kosong.

```bash
touch catatan.txt
```

### `cp`

Digunakan untuk menyalin file atau folder.

```bash
cp catatan.txt backup-catatan.txt
```

Menyalin folder:

```bash
cp -r latihan-linux backup-latihan
```

### `mv`

Digunakan untuk memindahkan atau mengganti nama file.

Mengganti nama file:

```bash
mv catatan.txt materi.txt
```

Memindahkan file:

```bash
mv materi.txt latihan-linux/
```

### `rm`

Digunakan untuk menghapus file atau folder.

Menghapus file:

```bash
rm materi.txt
```

Menghapus folder beserta isinya:

```bash
rm -r latihan-linux
```

> Hati-hati menggunakan `rm`, karena file yang dihapus melalui terminal biasanya tidak masuk ke recycle bin.

---

## 5. Command Membaca Isi File

### `cat`

Digunakan untuk menampilkan seluruh isi file.

```bash
cat catatan.txt
```

### `less`

Digunakan untuk membaca file panjang halaman demi halaman.

```bash
less log.txt
```

Tombol penting di `less`:

- `Space` untuk turun halaman.
- `b` untuk naik halaman.
- `q` untuk keluar.

### `head`

Digunakan untuk menampilkan beberapa baris awal file.

```bash
head catatan.txt
head -n 5 catatan.txt
```

### `tail`

Digunakan untuk menampilkan beberapa baris akhir file.

```bash
tail catatan.txt
tail -n 5 catatan.txt
```

Melihat log secara realtime:

```bash
tail -f /var/log/syslog
```

---

## 6. Command Pencarian

### `find`

Digunakan untuk mencari file atau folder berdasarkan nama.

```bash
find . -name "catatan.txt"
```

Contoh mencari semua file `.txt`:

```bash
find . -name "*.txt"
```

### `grep`

Digunakan untuk mencari teks di dalam file.

```bash
grep "Linux" catatan.txt
```

Mencari teks dalam banyak file:

```bash
grep -r "Linux" .
```

Mengabaikan huruf besar dan kecil:

```bash
grep -i "linux" catatan.txt
```

---

## 7. Command Informasi Sistem

### `whoami`

Menampilkan nama user yang sedang digunakan.

```bash
whoami
```

### `hostname`

Menampilkan nama komputer atau server.

```bash
hostname
```

### `uname`

Menampilkan informasi kernel Linux.

```bash
uname -a
```

### `df`

Menampilkan penggunaan ruang disk.

```bash
df -h
```

### `free`

Menampilkan penggunaan memori.

```bash
free -h
```

### `top`

Menampilkan proses yang sedang berjalan.

```bash
top
```

Tekan `q` untuk keluar dari tampilan `top`.

---

## 8. Permission Dasar Linux

Linux memiliki sistem hak akses untuk file dan folder.

Contoh output `ls -l`:

```bash
-rw-r--r-- 1 user user 120 Jun 28 10:00 catatan.txt
```

Bagian permission:

```bash
-rw-r--r--
```

Keterangan:

| Simbol | Arti |
|---|---|
| `r` | read, izin membaca |
| `w` | write, izin menulis atau mengubah |
| `x` | execute, izin menjalankan |

Permission dibagi menjadi tiga bagian:

| Bagian | Keterangan |
|---|---|
| User | Pemilik file |
| Group | Grup pemilik file |
| Others | Pengguna lain |

### `chmod`

Digunakan untuk mengubah permission file.

Contoh memberi izin eksekusi:

```bash
chmod +x script.sh
```

Contoh permission angka:

```bash
chmod 755 script.sh
chmod 644 catatan.txt
```

Keterangan umum:

- `755` biasanya digunakan untuk script atau folder.
- `644` biasanya digunakan untuk file biasa.

### `chown`

Digunakan untuk mengubah pemilik file.

```bash
sudo chown user:user catatan.txt
```

---

## 9. Command dengan Hak Akses Administrator

### `sudo`

`sudo` digunakan untuk menjalankan command dengan hak akses administrator.

Contoh:

```bash
sudo apt update
```

Saat menggunakan `sudo`, sistem biasanya meminta password user.

> Gunakan `sudo` hanya jika diperlukan, karena command administrator dapat mengubah konfigurasi penting sistem.

---

## 10. Manajemen Paket Dasar

Pada distribusi berbasis Debian atau Ubuntu, package manager yang umum digunakan adalah `apt`.

Memperbarui daftar paket:

```bash
sudo apt update
```

Meng-upgrade paket:

```bash
sudo apt upgrade
```

Menginstal aplikasi:

```bash
sudo apt install nama-paket
```

Menghapus aplikasi:

```bash
sudo apt remove nama-paket
```

Contoh:

```bash
sudo apt install git
```

---

## 11. Redirection dan Pipeline

### Redirection

Redirection digunakan untuk mengarahkan output command ke file.

Menulis output ke file:

```bash
echo "Belajar Linux" > catatan.txt
```

Menambahkan output ke akhir file:

```bash
echo "Basic command" >> catatan.txt
```

### Pipeline

Pipeline `|` digunakan untuk mengirim output command pertama menjadi input command berikutnya.

Contoh:

```bash
ls -la | grep ".txt"
```

Contoh melihat proses tertentu:

```bash
ps aux | grep apache
```

---

## 12. Latihan Praktik

Ikuti langkah berikut di terminal:

### Latihan 1: Navigasi dan Folder

```bash
pwd
mkdir latihan-linux
cd latihan-linux
pwd
```

Tugas:

1. Jelaskan lokasi direktori setelah menjalankan `pwd`.
2. Apa fungsi command `cd latihan-linux`?

### Latihan 2: Membuat dan Membaca File

```bash
touch biodata.txt
echo "Nama: Muktashim" > biodata.txt
echo "Materi: Basic Command Linux" >> biodata.txt
cat biodata.txt
```

Tugas:

1. Apa perbedaan `>` dan `>>`?
2. Command apa yang digunakan untuk melihat isi file?

### Latihan 3: Menyalin, Memindahkan, dan Menghapus

```bash
cp biodata.txt backup-biodata.txt
mkdir arsip
mv backup-biodata.txt arsip/
ls arsip
rm biodata.txt
```

Tugas:

1. Apa fungsi `cp`?
2. Apa fungsi `mv`?
3. Mengapa command `rm` harus digunakan dengan hati-hati?

### Latihan 4: Permission

```bash
touch script.sh
echo "echo Halo Linux" > script.sh
ls -l script.sh
chmod +x script.sh
ls -l script.sh
./script.sh
```

Tugas:

1. Apa perubahan permission setelah menjalankan `chmod +x`?
2. Mengapa file `script.sh` bisa dijalankan setelah diberi permission execute?

---

## 13. Ringkasan Command

| Command | Fungsi |
|---|---|
| `pwd` | Melihat direktori saat ini |
| `ls` | Melihat isi direktori |
| `cd` | Berpindah direktori |
| `mkdir` | Membuat folder |
| `touch` | Membuat file kosong |
| `cp` | Menyalin file atau folder |
| `mv` | Memindahkan atau mengganti nama file |
| `rm` | Menghapus file atau folder |
| `cat` | Menampilkan isi file |
| `less` | Membaca file panjang |
| `head` | Melihat baris awal file |
| `tail` | Melihat baris akhir file |
| `find` | Mencari file atau folder |
| `grep` | Mencari teks dalam file |
| `chmod` | Mengubah permission |
| `chown` | Mengubah pemilik file |
| `sudo` | Menjalankan command sebagai administrator |
| `df -h` | Melihat kapasitas disk |
| `free -h` | Melihat penggunaan memori |
| `top` | Melihat proses berjalan |

---

## ✅ Kesimpulan

Basic command Linux adalah fondasi penting untuk menggunakan Linux secara efektif. Dengan memahami command seperti `pwd`, `ls`, `cd`, `mkdir`, `touch`, `cp`, `mv`, `rm`, `cat`, `grep`, dan `chmod`, peserta dapat mulai mengelola file, folder, serta memahami cara kerja dasar sistem Linux melalui terminal.

Latihan secara rutin sangat penting agar command-command tersebut menjadi terbiasa digunakan dalam pekerjaan sehari-hari.

---

[⬅️ Kembali ke Daftar Isi](<index.md>)

✍️ **Dibuat oleh:** Muktashim Billah  
📅 **Terakhir diperbarui:** 28 Juni 2026
