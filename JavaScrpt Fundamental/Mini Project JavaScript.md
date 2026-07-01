# Bagian 21: Mini Project JavaScript

## Yang Akan Dibahas

Mini project ini bertujuan menggabungkan materi fundamental JavaScript dalam satu latihan sederhana. Project yang dibuat adalah aplikasi todo list berbasis HTML, CSS, dan JavaScript.

---

## Tujuan Pembelajaran

Setelah menyelesaikan mini project ini, peserta diharapkan mampu:

1. Membuat struktur HTML sederhana.
2. Mengambil elemen DOM.
3. Menangani event submit.
4. Menambah, menampilkan, dan menghapus data array.
5. Memecah kode menjadi function kecil.

---

## 21.1 Struktur File

Buat folder project dengan struktur berikut:

```text
todo-app/
├── index.html
├── style.css
└── script.js
```

---

## 21.2 File index.html

```html
<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Todo App</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <main class="app">
    <h1>Todo App</h1>

    <form id="todoForm">
      <input id="todoInput" type="text" placeholder="Tulis tugas baru">
      <button type="submit">Tambah</button>
    </form>

    <ul id="todoList"></ul>
  </main>

  <script src="script.js"></script>
</body>
</html>
```

---

## 21.3 File style.css

```css
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: #f3f4f6;
  color: #111827;
}

.app {
  width: min(600px, 100%);
  margin: 40px auto;
  padding: 24px;
}

form {
  display: flex;
  gap: 8px;
}

input {
  flex: 1;
  padding: 10px;
}

button {
  padding: 10px 14px;
  cursor: pointer;
}

ul {
  padding: 0;
  list-style: none;
}

li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-top: 8px;
  padding: 10px;
  background: white;
  border: 1px solid #d1d5db;
}
```

---

## 21.4 File script.js

```javascript
const todoForm = document.getElementById("todoForm");
const todoInput = document.getElementById("todoInput");
const todoList = document.getElementById("todoList");

let todos = [];

function renderTodos() {
  todoList.innerHTML = "";

  todos.forEach(function (todo, index) {
    const item = document.createElement("li");
    const text = document.createElement("span");
    const button = document.createElement("button");

    text.textContent = todo;
    button.textContent = "Hapus";

    button.addEventListener("click", function () {
      hapusTodo(index);
    });

    item.appendChild(text);
    item.appendChild(button);
    todoList.appendChild(item);
  });
}

function tambahTodo(todo) {
  todos.push(todo);
  renderTodos();
}

function hapusTodo(index) {
  todos.splice(index, 1);
  renderTodos();
}

todoForm.addEventListener("submit", function (event) {
  event.preventDefault();

  const todo = todoInput.value.trim();

  if (todo === "") {
    alert("Todo tidak boleh kosong");
    return;
  }

  tambahTodo(todo);
  todoInput.value = "";
  todoInput.focus();
});
```

---

## 21.5 Alur Program

1. User mengisi input.
2. User menekan tombol Tambah.
3. Event submit dicegah agar halaman tidak reload.
4. Nilai input divalidasi.
5. Todo dimasukkan ke array.
6. List ditampilkan ulang melalui `renderTodos`.
7. Tombol Hapus menghapus todo berdasarkan index.

---

## 21.6 Pengembangan Lanjutan

Setelah versi dasar selesai, tambahkan fitur berikut:

- Menandai todo selesai.
- Mengedit todo.
- Menyimpan todo ke localStorage.
- Menampilkan jumlah todo.
- Filter semua, aktif, dan selesai.

---

## Ringkasan

- Mini project menggabungkan DOM, event, array, dan function.
- Todo app melatih proses tambah, tampil, dan hapus data.
- Project dapat dikembangkan dengan fitur edit, status selesai, dan localStorage.

---

## Latihan

1. Buat mini project sesuai struktur file.
2. Jalankan di browser.
3. Tambahkan minimal 3 todo.
4. Hapus salah satu todo.
5. Tambahkan fitur jumlah todo yang sedang ditampilkan.
