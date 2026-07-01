# Bagian 8: Function dan Scope

## Yang Akan Dibahas

Function digunakan untuk mengelompokkan kode agar dapat digunakan berulang kali. Scope menentukan area tempat variabel dapat diakses.

---

## Tujuan Pembelajaran

Setelah mempelajari modul ini, peserta diharapkan mampu:

1. Membuat function.
2. Menggunakan parameter dan return value.
3. Memahami function declaration dan arrow function.
4. Memahami scope, hoisting, dan closure dasar.

---

## 8.1 Membuat Function

```javascript
function sapa() {
  console.log("Halo!");
}

sapa();
```

Function tidak berjalan sampai dipanggil.

---

## 8.2 Parameter dan Argument

Parameter adalah variabel di definisi function. Argument adalah nilai yang dikirim saat function dipanggil.

```javascript
function sapaNama(nama) {
  console.log(`Halo, ${nama}`);
}

sapaNama("Alya");
sapaNama("Budi");
```

---

## 8.3 Return Value

`return` digunakan untuk mengembalikan nilai dari function.

```javascript
function tambah(a, b) {
  return a + b;
}

const hasil = tambah(10, 5);
console.log(hasil);
```

Kode setelah `return` tidak akan dijalankan.

---

## 8.4 Default Parameter

Default parameter digunakan jika argument tidak dikirim.

```javascript
function buatSalam(nama = "Guest") {
  return `Halo, ${nama}`;
}

console.log(buatSalam());
console.log(buatSalam("Dina"));
```

---

## 8.5 Function Expression

Function dapat disimpan dalam variabel.

```javascript
const kali = function (a, b) {
  return a * b;
};

console.log(kali(4, 5));
```

---

## 8.6 Arrow Function

Arrow function adalah sintaks function yang lebih ringkas.

```javascript
const bagi = (a, b) => {
  return a / b;
};

console.log(bagi(10, 2));
```

Jika hanya satu baris return:

```javascript
const kuadrat = (angka) => angka * angka;

console.log(kuadrat(5));
```

---

## 8.7 Scope

Scope menentukan area akses variabel.

```javascript
const global = "Bisa diakses di mana saja dalam file";

function contohScope() {
  const lokal = "Hanya bisa diakses di dalam function";
  console.log(global);
  console.log(lokal);
}

contohScope();
```

Variabel `lokal` tidak bisa diakses dari luar function.

---

## 8.8 Hoisting Dasar

Function declaration dapat dipanggil sebelum didefinisikan.

```javascript
sapa();

function sapa() {
  console.log("Halo");
}
```

Namun function expression tidak disarankan dipanggil sebelum dibuat.

---

## 8.9 Closure Dasar

Closure terjadi ketika function di dalam masih mengakses variabel dari function luar.

```javascript
function buatCounter() {
  let angka = 0;

  return function () {
    angka++;
    return angka;
  };
}

const counter = buatCounter();

console.log(counter()); // 1
console.log(counter()); // 2
```

Closure sering digunakan untuk menyimpan state secara tersembunyi.

---

## Ringkasan

- Function mengelompokkan kode agar dapat digunakan ulang.
- Scope menentukan area akses variabel.
- Closure memungkinkan function mengingat variabel dari scope luarnya.

---

## Latihan

1. Buat function untuk menghitung luas segitiga.
2. Buat function yang menerima nama dan mengembalikan kalimat sapaan.
3. Ubah function biasa menjadi arrow function.
4. Buat counter sederhana menggunakan closure.
