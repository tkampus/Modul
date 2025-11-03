# 🖥️ Cara Hosting Website Gratis di GitHub Pages (Panduan Lengkap 2025)

GitHub Pages adalah layanan gratis dari GitHub yang memungkinkan kamu untuk menghosting situs web statis langsung dari repositori.  
Dengan cara ini, kamu bisa mempublikasikan portofolio, proyek, atau website pribadi tanpa perlu membeli hosting atau domain tambahan.

---

## 🚀 Langkah-Langkah Hosting Website di GitHub Pages

### 1. **Buat Akun GitHub**
Jika belum memiliki akun, buka [https://github.com](https://github.com) dan daftar secara gratis.  
Jika sudah punya akun, cukup login ke akun GitHub kamu.

---

### 2. **Buat Repositori Baru**
1. Klik tombol **New Repository**.  
2. Beri nama repositori dengan format berikut:
```bash
username.github.io
```
Ganti `username` dengan nama pengguna GitHub kamu.  
Contoh: `elfatih.github.io`

3. Pastikan visibilitas diatur menjadi **Public**.  
4. Klik tombol **Create repository**.

---

### 3. **Unggah File Website**
1. Buka repositori yang baru kamu buat.  
2. Klik tombol **Add file → Upload files**.  
3. Seret dan lepaskan semua file situs web kamu (misalnya `index.html`, `style.css`, `script.js`, dll).  
4. Pastikan file utama (`index.html`) berada di **root directory** (tingkat atas folder, bukan di dalam subfolder).  
5. Masukkan pesan *commit* seperti:
```bash
Initial commit
```
lalu klik **Commit changes**.

---

### 4. **Aktifkan GitHub Pages**
1. Masuk ke tab **Settings** di repositori kamu.  
2. Pilih menu **Pages** di sidebar kiri.  
3. Di bagian **Source**, ubah opsi menjadi:
```bash
Deploy from a branch
```
4. Pilih branch `main` (atau `master`) dan folder `/ (root)`.  
5. Klik **Save**.

---

### 5. **Akses Website Kamu**
Tunggu beberapa menit hingga proses publikasi selesai.  
Setelah itu, buka di browser:
```bash
https://username.github.io
```
Ganti `username` dengan nama pengguna GitHub kamu.  
Selamat! 🎉 Website kamu sekarang sudah online secara gratis.

---

## 🧠 Tips Tambahan
- Gunakan file `index.html` sebagai halaman utama.  
- Untuk pembaruan situs, cukup **push commit baru** ke repositori — GitHub Pages akan memperbarui otomatis.  
- Kamu juga bisa menambahkan **custom domain** lewat pengaturan Pages jika ingin menggunakan domain sendiri.  

---

## 📄 Contoh Struktur Folder
```bash
my-website/
├── index.html
├── about.html
├── style.css
└── script.js
```

---

## 💡 Kesimpulan
GitHub Pages adalah solusi ideal untuk hosting gratis dan mudah bagi pengembang web maupun pemula.  
Dengan beberapa langkah sederhana, kamu bisa memublikasikan situs pribadi, portofolio, atau dokumentasi proyek langsung dari repositori GitHub.

---

✍️ **Dibuat oleh:** Muktashim Billah   
📅 **Terakhir diperbarui:** 04 November 2025  






