# Bagian 14: String, Number, Date, dan Math

## Yang Akan Dibahas

JavaScript menyediakan object bawaan untuk mengolah teks, angka, tanggal, dan operasi matematika umum.

---

## Tujuan Pembelajaran

Setelah mempelajari modul ini, peserta diharapkan mampu:

1. Menggunakan method string.
2. Mengolah number dan konversi tipe.
3. Menggunakan Date untuk tanggal dan waktu.
4. Menggunakan Math untuk pembulatan dan angka acak.

---

## 14.1 String

String adalah tipe data teks.

```javascript
const nama = "JavaScript";

console.log(nama.length);
console.log(nama.toUpperCase());
console.log(nama.toLowerCase());
```

---

## 14.2 Method String Penting

```javascript
const kalimat = "Saya sedang belajar JavaScript";

console.log(kalimat.includes("belajar"));
console.log(kalimat.startsWith("Saya"));
console.log(kalimat.endsWith("JavaScript"));
console.log(kalimat.replace("JavaScript", "Node.js"));
console.log(kalimat.slice(0, 4));
```

Memecah string menjadi array:

```javascript
const tags = "html,css,javascript";
const hasil = tags.split(",");

console.log(hasil);
```

Menghapus spasi di awal dan akhir:

```javascript
const email = "  user@example.com  ";
console.log(email.trim());
```

---

## 14.3 Number

JavaScript menggunakan satu tipe `number` untuk integer dan decimal.

```javascript
const harga = 15000;
const diskon = 12.5;

console.log(typeof harga);
console.log(typeof diskon);
```

---

## 14.4 Konversi Number

```javascript
const input = "100";

console.log(Number(input));
console.log(parseInt("100px"));
console.log(parseFloat("3.14"));
```

Hati-hati dengan `NaN` atau Not a Number.

```javascript
console.log(Number("abc")); // NaN
console.log(Number.isNaN(Number("abc")));
```

---

## 14.5 Format Number

```javascript
const harga = 1500000;

console.log(harga.toLocaleString("id-ID"));
```

Format mata uang:

```javascript
const rupiah = new Intl.NumberFormat("id-ID", {
  style: "currency",
  currency: "IDR",
}).format(1500000);

console.log(rupiah);
```

---

## 14.6 Date

`Date` digunakan untuk tanggal dan waktu.

```javascript
const sekarang = new Date();

console.log(sekarang);
console.log(sekarang.getFullYear());
console.log(sekarang.getMonth()); // 0 sampai 11
console.log(sekarang.getDate());
```

Membuat tanggal tertentu:

```javascript
const tanggalLahir = new Date("2005-08-17");
console.log(tanggalLahir);
```

---

## 14.7 Format Tanggal

```javascript
const tanggal = new Date("2026-07-01");

console.log(tanggal.toLocaleDateString("id-ID"));
```

Dengan opsi:

```javascript
const format = tanggal.toLocaleDateString("id-ID", {
  weekday: "long",
  year: "numeric",
  month: "long",
  day: "numeric",
});

console.log(format);
```

---

## 14.8 Math

```javascript
console.log(Math.round(4.6));
console.log(Math.floor(4.9));
console.log(Math.ceil(4.1));
console.log(Math.max(10, 20, 5));
console.log(Math.min(10, 20, 5));
```

Angka acak:

```javascript
const random = Math.random();
console.log(random);
```

Angka acak 1 sampai 10:

```javascript
const angka = Math.floor(Math.random() * 10) + 1;
console.log(angka);
```

---

## Ringkasan

- String, number, date, dan math adalah object bawaan yang sering digunakan.
- Method bawaan membantu mengolah teks, angka, tanggal, dan perhitungan.
- Format data penting agar output mudah dibaca user.

---

## Latihan

1. Buat program yang mengubah nama menjadi huruf besar.
2. Buat program validasi sederhana apakah email mengandung `@`.
3. Format angka `2500000` menjadi format rupiah.
4. Buat angka random dari 1 sampai 100.
