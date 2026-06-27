# 🔐 Modul Linux: File Permission

File permission adalah mekanisme Linux untuk mengatur siapa yang boleh membaca, mengubah, atau menjalankan file dan folder. Konsep ini sangat penting untuk keamanan sistem.

Modul ini membahas permission dasar Linux, cara membaca output `ls -l`, serta penggunaan `chmod`, `chown`, dan `chgrp`.

---

## 🎯 Tujuan Pembelajaran

Setelah mempelajari modul ini, peserta diharapkan mampu:

1. Memahami konsep permission file dan folder.
2. Membaca informasi permission dari command `ls -l`.
3. Membedakan hak akses user, group, dan others.
4. Mengubah permission menggunakan `chmod`.
5. Mengubah pemilik file menggunakan `chown`.
6. Mengubah group file menggunakan `chgrp`.

---

## 1. Melihat Permission File

Gunakan command berikut:

```bash
ls -l
```

Contoh output:

```bash
-rw-r--r-- 1 user user 120 Jun 28 10:00 catatan.txt
drwxr-xr-x 2 user user 4096 Jun 28 10:10 dokumen
```

Karakter pertama menunjukkan jenis file:

| Simbol | Arti |
|---|---|
| `-` | File biasa |
| `d` | Direktori |
| `l` | Symbolic link |

---

## 2. Jenis Permission

Linux memiliki tiga permission utama:

| Simbol | Nama | Arti pada File | Arti pada Folder |
|---|---|---|---|
| `r` | read | Membaca isi file | Melihat isi folder |
| `w` | write | Mengubah isi file | Membuat, menghapus, atau rename isi folder |
| `x` | execute | Menjalankan file | Masuk ke folder |

Contoh:

```bash
-rw-r--r--
```

Dibaca menjadi:

- User: `rw-`
- Group: `r--`
- Others: `r--`

Artinya pemilik file dapat membaca dan menulis, sedangkan group dan others hanya dapat membaca.

---

## 3. User, Group, dan Others

Permission dibagi menjadi tiga bagian:

| Bagian | Keterangan |
|---|---|
| User | Pemilik file |
| Group | Group yang memiliki file |
| Others | Pengguna lain di luar user dan group |

Contoh output:

```bash
-rw-r--r-- 1 muktashim kelas 120 Jun 28 10:00 materi.txt
```

Keterangan:

- Pemilik file adalah `muktashim`.
- Group file adalah `kelas`.
- Nama file adalah `materi.txt`.

---

## 4. Mode Numerik Permission

Permission juga dapat ditulis menggunakan angka.

| Angka | Permission | Arti |
|---|---|---|
| 4 | `r` | read |
| 2 | `w` | write |
| 1 | `x` | execute |
| 0 | `-` | tidak ada izin |

Contoh kombinasi:

| Angka | Permission |
|---|---|
| 7 | `rwx` |
| 6 | `rw-` |
| 5 | `r-x` |
| 4 | `r--` |

Contoh permission `755`:

```bash
rwxr-xr-x
```

Artinya:

- User: read, write, execute.
- Group: read, execute.
- Others: read, execute.

---

## 5. Mengubah Permission dengan chmod

Memberi execute permission:

```bash
chmod +x script.sh
```

Menghapus write permission dari others:

```bash
chmod o-w file.txt
```

Memberi permission menggunakan angka:

```bash
chmod 755 script.sh
chmod 644 catatan.txt
```

Penggunaan umum:

| Permission | Umum Digunakan Untuk |
|---|---|
| `755` | Folder atau script |
| `644` | File biasa |
| `600` | File rahasia seperti private key |
| `700` | Folder pribadi atau script khusus pemilik |

---

## 6. Mengubah Pemilik dengan chown

Mengubah pemilik file:

```bash
sudo chown userbaru file.txt
```

Mengubah pemilik dan group:

```bash
sudo chown userbaru:groupbaru file.txt
```

Mengubah pemilik folder beserta isinya:

```bash
sudo chown -R userbaru:groupbaru folder/
```

Opsi `-R` berarti recursive, yaitu berlaku untuk folder dan seluruh isi di dalamnya.

---

## 7. Mengubah Group dengan chgrp

Mengubah group file:

```bash
sudo chgrp developers file.txt
```

Mengubah group folder secara recursive:

```bash
sudo chgrp -R developers project/
```

---

## 8. Permission Folder

Permission pada folder sedikit berbeda dari file.

Contoh:

```bash
chmod 755 public
chmod 700 private
```

Keterangan:

- `755` membuat folder bisa dibuka oleh orang lain, tetapi hanya pemilik yang bisa mengubah isi.
- `700` membuat folder hanya dapat diakses oleh pemilik.

---

## 9. Praktik

Jalankan command berikut:

```bash
mkdir latihan-permission
cd latihan-permission
touch catatan.txt
ls -l
chmod 600 catatan.txt
ls -l
chmod 644 catatan.txt
ls -l
echo "echo Halo Linux" > script.sh
chmod +x script.sh
./script.sh
```

Tugas:

1. Apa perbedaan permission `600` dan `644`?
2. Mengapa `script.sh` perlu diberi permission execute?
3. Apa fungsi command `chown`?
4. Apa arti opsi `-R`?

---

## ✅ Kesimpulan

File permission membantu menjaga keamanan Linux dengan mengatur hak akses user, group, dan others. Command utama yang perlu dikuasai adalah `ls -l`, `chmod`, `chown`, dan `chgrp`.

---

[⬅️ Kembali ke Daftar Isi](<index.md>)

✍️ **Dibuat oleh:** Muktashim Billah  
📅 **Terakhir diperbarui:** 28 Juni 2026
