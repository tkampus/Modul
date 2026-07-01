# Bagian 17: Asynchronous JavaScript

## Yang Akan Dibahas

Asynchronous JavaScript digunakan untuk menjalankan proses yang membutuhkan waktu tanpa menghentikan seluruh program, misalnya request API, timer, membaca file, atau komunikasi jaringan.

---

## Tujuan Pembelajaran

Setelah mempelajari modul ini, peserta diharapkan mampu:

1. Memahami perbedaan synchronous dan asynchronous.
2. Menggunakan callback.
3. Menggunakan promise.
4. Menggunakan `async await`.
5. Mengambil data menggunakan `fetch`.

---

## 17.1 Synchronous

Kode synchronous berjalan berurutan dari atas ke bawah.

```javascript
console.log("Satu");
console.log("Dua");
console.log("Tiga");
```

Output:

```text
Satu
Dua
Tiga
```

---

## 17.2 Asynchronous

Kode asynchronous tidak selalu selesai sesuai urutan penulisan.

```javascript
console.log("Mulai");

setTimeout(function () {
  console.log("Selesai setelah 2 detik");
}, 2000);

console.log("Lanjut");
```

Output:

```text
Mulai
Lanjut
Selesai setelah 2 detik
```

---

## 17.3 Callback

Callback adalah function yang dikirim sebagai argument ke function lain.

```javascript
function prosesData(callback) {
  console.log("Memproses data...");
  callback();
}

prosesData(function () {
  console.log("Data selesai diproses");
});
```

Callback sering digunakan pada event dan proses asynchronous.

---

## 17.4 Promise

Promise mewakili proses yang akan selesai di masa depan.

Status promise:

| Status | Arti |
|---|---|
| Pending | Masih berjalan |
| Fulfilled | Berhasil |
| Rejected | Gagal |

Contoh:

```javascript
const janji = new Promise(function (resolve, reject) {
  const berhasil = true;

  if (berhasil) {
    resolve("Data berhasil");
  } else {
    reject("Data gagal");
  }
});

janji
  .then(function (hasil) {
    console.log(hasil);
  })
  .catch(function (error) {
    console.log(error);
  });
```

---

## 17.5 async await

`async await` membuat promise lebih mudah dibaca.

```javascript
function ambilData() {
  return new Promise(function (resolve) {
    setTimeout(function () {
      resolve("Data user");
    }, 1000);
  });
}

async function main() {
  const data = await ambilData();
  console.log(data);
}

main();
```

Function yang menggunakan `await` harus diberi keyword `async`.

---

## 17.6 Error Handling dengan async await

```javascript
async function main() {
  try {
    const data = await ambilData();
    console.log(data);
  } catch (error) {
    console.log("Terjadi error:", error);
  }
}
```

Gunakan `try catch` agar error asynchronous dapat ditangani.

---

## 17.7 fetch

`fetch` digunakan untuk mengambil data dari API.

```javascript
async function ambilUser() {
  const response = await fetch("https://jsonplaceholder.typicode.com/users/1");
  const user = await response.json();

  console.log(user);
}

ambilUser();
```

`fetch` tersedia di browser modern dan Node.js versi baru.

---

## 17.8 Mengecek Response

```javascript
async function ambilPost() {
  try {
    const response = await fetch("https://jsonplaceholder.typicode.com/posts/1");

    if (!response.ok) {
      throw new Error("Request gagal");
    }

    const post = await response.json();
    console.log(post);
  } catch (error) {
    console.log(error.message);
  }
}

ambilPost();
```

---

## Ringkasan

- Asynchronous JavaScript menangani proses yang membutuhkan waktu.
- Promise dan `async await` membuat alur asynchronous lebih mudah dibaca.
- `fetch` digunakan untuk mengambil data dari API.

---

## Latihan

1. Buat `setTimeout` yang mencetak pesan setelah 3 detik.
2. Buat promise sederhana yang berhasil jika nilai angka lebih dari 70.
3. Ubah promise menjadi penggunaan `async await`.
4. Ambil data dari API publik menggunakan `fetch`.
