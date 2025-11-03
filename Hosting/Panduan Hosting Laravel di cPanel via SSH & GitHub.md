# 🚀 Panduan Hosting Laravel di cPanel via SSH & GitHub

Panduan lengkap untuk melakukan deploy project **Laravel** ke **cPanel** menggunakan **SSH dan GitHub**.

---

## 🧩 1. Login ke Server via SSH

Buka terminal (PowerShell / VS Code / Git Bash) dan jalankan:

```bash
ssh -i ".ssh\id_rsa" username@namadomainmu.com
```
Ganti username dengan username cPanel kamu, dan sesuaikan path id_rsa dengan lokasi private key kamu.

## 📁 2. Cek Direktori Awal

Setelah berhasil login, pastikan kamu berada di home directory:

```bash
pwd
```

Biasanya hasilnya seperti:

```bash
/home/username/
```

Lalu cek apakah ada folder public_html:

```bash
ls
```

## 🌿 3. Clone Project dari GitHub

Masuk ke direktori home:

```bash
cd ~
```

Clone repository kamu:

```bash
git clone https://github.com/username/nama-repo.git
```

Jika repository bersifat private, pastikan SSH key server sudah ditambahkan ke GitHub.

## 📦 4. Masuk ke Folder Project

```bash
cd nama-repo
```

## 🧰 5. Install Dependency Laravel
Jalankan Composer

```bash
composer install
```

Copy File .env dan Generate Key
```bash
cp .env.example .env
php artisan key:generate
```
(Opsional) Jalankan NPM

Jika server mendukung Node.js:
```bash
npm install
npm run build
```

Jika tidak mendukung, build di lokal lalu upload folder public/build ke server.

## ⚙️ 6. Atur Folder Public ke public_html

Masuk ke direktori home:

```bash
cd ~
```

Backup folder public_html lama:

```bash
mv public_html public_html_backup
```

Buat symbolic link dari folder project:

```bash
ln -s ~/nama-repo/public ~/public_html
```

Sekarang domain otomatis mengarah ke folder public Laravel.

## 🗄️ 7. Konfigurasi Database di cPanel

- Buka cPanel → MySQL Databases
- Buat database dan user baru
- Hubungkan user ke database (ALL PRIVILEGES)

Edit file .env:

```bash
DB_CONNECTION=mysql
DB_HOST=localhost
DB_PORT=3306
DB_DATABASE=namadatabase
DB_USERNAME=namauser
DB_PASSWORD=katapassword
```


Jalankan migrasi:

```bash
php artisan migrate --seed
```

## 🔐 8. Aktifkan SSL (HTTPS)

Pastikan AutoSSL aktif di cPanel, lalu ubah di .env:

```bash
APP_URL=https://namadomainmu.com
```

## 🪣 9. Jalankan Storage Link
```bash
php artisan storage:link
```

## 🧹 10. Bersihkan Cache Laravel
```bash
php artisan config:clear
php artisan route:clear
php artisan cache:clear
php artisan view:clear
```

## ✅ 11. Selesai

Sekarang buka:

```bash
https://namadomainmu.com
```
Jika semua langkah benar, aplikasi Laravel kamu akan tampil dengan sempurna 🎉

---

✍️ **Dibuat oleh:** Muktashim Billah   
📅 **Terakhir diperbarui:** 10 Oktober 2025  
