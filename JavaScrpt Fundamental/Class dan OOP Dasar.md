# Bagian 12: Class dan OOP Dasar

## Yang Akan Dibahas

Object-oriented programming atau OOP adalah cara menulis program dengan memodelkan data dan perilaku sebagai object. JavaScript mendukung OOP melalui object, prototype, dan sintaks `class`.

---

## Tujuan Pembelajaran

Setelah mempelajari modul ini, peserta diharapkan mampu:

1. Memahami konsep object dan class.
2. Membuat class dan object instance.
3. Menggunakan constructor dan method.
4. Menggunakan inheritance dasar.
5. Memahami encapsulation sederhana.

---

## 12.1 Object dan Class

Object adalah data nyata yang memiliki property dan method.

Class adalah cetakan untuk membuat object.

```javascript
class User {
  constructor(nama, email) {
    this.nama = nama;
    this.email = email;
  }

  sapa() {
    return `Halo, saya ${this.nama}`;
  }
}

const user1 = new User("Alya", "alya@example.com");

console.log(user1.nama);
console.log(user1.sapa());
```

---

## 12.2 Constructor

`constructor` berjalan otomatis saat object dibuat dengan `new`.

```javascript
class Produk {
  constructor(nama, harga) {
    this.nama = nama;
    this.harga = harga;
  }
}

const keyboard = new Produk("Keyboard", 250000);

console.log(keyboard);
```

---

## 12.3 Method

Method adalah function yang berada di dalam class.

```javascript
class Produk {
  constructor(nama, harga) {
    this.nama = nama;
    this.harga = harga;
  }

  formatHarga() {
    return this.harga.toLocaleString("id-ID");
  }
}

const mouse = new Produk("Mouse", 150000);

console.log(mouse.formatHarga());
```

---

## 12.4 Inheritance

Inheritance membuat class baru mewarisi property dan method dari class lain.

```javascript
class User {
  constructor(nama) {
    this.nama = nama;
  }

  sapa() {
    return `Halo, saya ${this.nama}`;
  }
}

class Admin extends User {
  hapusData() {
    return "Data berhasil dihapus";
  }
}

const admin = new Admin("Rani");

console.log(admin.sapa());
console.log(admin.hapusData());
```

---

## 12.5 super

`super` digunakan untuk memanggil constructor atau method dari parent class.

```javascript
class Pegawai {
  constructor(nama, jabatan) {
    this.nama = nama;
    this.jabatan = jabatan;
  }
}

class Manager extends Pegawai {
  constructor(nama, divisi) {
    super(nama, "Manager");
    this.divisi = divisi;
  }
}

const manager = new Manager("Dina", "Teknologi");

console.log(manager);
```

---

## 12.6 Encapsulation Sederhana

Private field menggunakan tanda `#`.

```javascript
class Rekening {
  #saldo = 0;

  setor(jumlah) {
    if (jumlah <= 0) {
      throw new Error("Jumlah setor harus lebih dari nol");
    }

    this.#saldo += jumlah;
  }

  lihatSaldo() {
    return this.#saldo;
  }
}

const rekening = new Rekening();
rekening.setor(100000);

console.log(rekening.lihatSaldo());
```

Private field tidak dapat diakses langsung dari luar class.

---

## 12.7 Kapan Menggunakan Class?

Gunakan class ketika:

- Membutuhkan banyak object dengan struktur yang sama.
- Object memiliki data dan perilaku yang saling terkait.
- Ingin membuat model seperti User, Produk, Transaksi, atau Kendaraan.

Untuk data sederhana, object biasa sering sudah cukup.

---

## Ringkasan

- Class adalah cetakan untuk membuat object.
- Constructor dan method digunakan untuk menyimpan data dan perilaku object.
- Inheritance dan private field membantu membuat struktur OOP dasar.

---

## Latihan

1. Buat class `Siswa` dengan property nama dan nilai.
2. Tambahkan method untuk mengecek lulus atau tidak.
3. Buat class `Admin` yang mewarisi class `User`.
4. Buat class `Keranjang` dengan private field untuk menyimpan total harga.
