# Bagian 7: Percabangan dan Perulangan

## Yang Akan Dibahas

Percabangan digunakan untuk menjalankan kode berdasarkan kondisi. Perulangan digunakan untuk menjalankan kode berulang kali.

---

## Tujuan Pembelajaran

Setelah mempelajari modul ini, peserta diharapkan mampu:

1. Menggunakan `if`, `else if`, dan `else`.
2. Menggunakan `switch`.
3. Menggunakan `for`, `while`, dan `do while`.
4. Menggunakan `break` dan `continue`.

---

## 7.1 Percabangan if else

```javascript
const nilai = 80;

if (nilai >= 75) {
  console.log("Lulus");
} else {
  console.log("Tidak lulus");
}
```

Kondisi di dalam `if` harus menghasilkan nilai boolean.

---

## 7.2 else if

Gunakan `else if` untuk banyak kondisi.

```javascript
const nilai = 88;

if (nilai >= 90) {
  console.log("A");
} else if (nilai >= 80) {
  console.log("B");
} else if (nilai >= 70) {
  console.log("C");
} else {
  console.log("D");
}
```

---

## 7.3 switch

`switch` cocok untuk membandingkan satu nilai dengan banyak kemungkinan.

```javascript
const hari = "Senin";

switch (hari) {
  case "Senin":
    console.log("Mulai belajar");
    break;
  case "Sabtu":
  case "Minggu":
    console.log("Akhir pekan");
    break;
  default:
    console.log("Hari biasa");
}
```

`break` digunakan agar kode berhenti setelah case cocok.

---

## 7.4 Perulangan for

`for` cocok ketika jumlah pengulangan sudah jelas.

```javascript
for (let i = 1; i <= 5; i++) {
  console.log(`Perulangan ke-${i}`);
}
```

Struktur `for`:

```javascript
for (nilaiAwal; kondisi; perubahan) {
  // kode
}
```

---

## 7.5 Perulangan while

`while` berjalan selama kondisi bernilai true.

```javascript
let angka = 1;

while (angka <= 5) {
  console.log(angka);
  angka++;
}
```

Pastikan nilai berubah agar tidak terjadi infinite loop.

---

## 7.6 Perulangan do while

`do while` menjalankan kode minimal satu kali.

```javascript
let nomor = 1;

do {
  console.log(nomor);
  nomor++;
} while (nomor <= 5);
```

---

## 7.7 break dan continue

`break` menghentikan perulangan.

```javascript
for (let i = 1; i <= 10; i++) {
  if (i === 5) {
    break;
  }

  console.log(i);
}
```

`continue` melewati iterasi saat ini dan lanjut ke iterasi berikutnya.

```javascript
for (let i = 1; i <= 5; i++) {
  if (i === 3) {
    continue;
  }

  console.log(i);
}
```

---

## Ringkasan

- Percabangan menjalankan kode berdasarkan kondisi.
- Perulangan menjalankan kode berulang kali.
- `break` menghentikan loop, sedangkan `continue` melewati iterasi saat ini.

---

## Latihan

1. Buat program penentu nilai A, B, C, D.
2. Buat program yang mencetak angka 1 sampai 100.
3. Cetak hanya angka genap dari 1 sampai 50.
4. Gunakan `switch` untuk menampilkan nama hari berdasarkan angka 1 sampai 7.
