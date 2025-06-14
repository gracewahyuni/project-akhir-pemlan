# 📌 Queue Task Manager

**Queue Task Manager** adalah aplikasi berbasis Java yang mensimulasikan sistem antrian (queue) berbasis peran (role) dengan fitur manajemen tugas menggunakan struktur data **tree**, **stack**, **queue**, dan **double linked list**. Aplikasi ini memiliki fitur khusus untuk masing-masing role: member dan admin.

---

## 🚀 Tujuan

Membuat aplikasi simulasi manajemen tugas berbasis antrian dengan kemampuan untuk menambah, menghapus, melihat tugas secara hirarkis (tree), serta melakukan **undo/redo**. Untuk admin, tersedia fitur untuk melihat **log aktivitas** yang bisa di-*search* dan di-*sort*.

---

## 🧩 Fitur Utama

### 👥 Role-based Flow
- Sistem berjalan dengan antrian: **member1 → member2 → admin**
- Setiap role menjalankan aksi berdasarkan menu yang tersedia
- Setelah `exit`, antrian berpindah ke role selanjutnya

### 👤 Member Menu (member1, member2)
1. **Lihat Tugas** → Menampilkan tree tugas
2. **Tambah Tugas** → Menambah task ke tree berdasarkan parent
3. **Hapus Tugas** → Menghapus task dari tree
4. **Undo** → Membatalkan aksi terakhir
5. **Redo** → Mengembalikan aksi yang di-undo
6. **Exit** → Keluar dari sesi dan lanjut ke antrian berikutnya

### 🛠 Tree Tugas
Contoh tampilan struktur tree saat user memilih “Lihat Tugas”:
```
1. Pemlan
    - Quiz
        > Quiz 1
        > Quiz 2
2. Pemweb
    - Quiz
    - Project
```

### 🔁 Undo/Redo
- Menggunakan dua stack
- Setiap aksi tambah/hapus dicatat dan bisa dibatalkan/dikembalikan
- Menampilkan “Belum ada perubahan” jika tidak ada aksi

### 👨‍💼 Admin Menu
1. **Lihat Log Aktivitas**
    - **Search** → Cari log berdasarkan kata kunci
    - **Sort** → Urutkan log berdasarkan waktu
    - **Exit** → Kembali ke menu utama
2. **Exit** → Keluar dari aplikasi

### 📊 Log Aktivitas
- Disimpan dalam **Double Linked List**
- Format tabel:
```
+------------+----------+------------------------+-------------+
|   Waktu    |  Nama    |         Aksi           |   Detail    |
+------------+----------+------------------------+-------------+
| 10:00:01   | member1  | Menambahkan tugas      | quiz 3      |
| 10:02:15   | member2  | Menghapus tugas        | Project     |
```

---

## 📁 Struktur Folder

```
ProjectQueueTaskManager/
├── src/
│   ├── Main.java
│   ├── models/
│   │   ├── Role.java
│   │   ├── TaskNode.java
│   │   ├── LogEntry.java
│   │   └── UserAction.java
│   ├── structures/
│   │   ├── TaskTree.java
│   │   ├── QueueRole.java
│   │   ├── ActivityLog.java
│   │   ├── UndoRedoManager.java
│   └── services/
│       ├── MemberService.java
│       └── AdminService.java
├── README.md
└── .gitignore
```

---

## 🛠️ Cara Menjalankan

1. Clone repository:
   ```bash
   git clone https://github.com/namamu/QueueTaskManager.git
   ```
2. Buka folder `src` di IDE seperti IntelliJ / VS Code
3. Jalankan `Main.java`

---

## 📚 Modul & Pembagian Tugas (Opsional)

| Nama Tim       | Modul                      | Tugas                                                                 |
|----------------|----------------------------|-----------------------------------------------------------------------|
| Gefi           | TaskTree, MemberService    | Struktur tree, penambahan & penghapusan tugas                        |
| Teman A        | UndoRedoManager            | Stack untuk undo & redo, integrasi ke member                         |
| Teman B        | ActivityLog, AdminService  | Double linked list, fitur search dan sort log aktivitas              |
| Teman C        | QueueRole, Main.java       | Antrian role, integrasi alur utama program                           |

---

## 🧠 Catatan Teknis

- Undo/Redo menggunakan `Stack<UserAction>`
- Log disimpan dengan `DoubleLinkedList<LogEntry>`
- Pencarian log pakai linear search
- Pengurutan log bisa gunakan bubble/insertion sort

---

## 🏁 Selesai Ketika

- Semua role selesai dieksekusi
- Queue kosong
- Program menampilkan pesan selesai dan berhenti

---

## 📌 Contoh Output Singkat

```
[INFO] Selamat datang member1
[MENU]
1. Lihat tugas
2. Tambah tugas
...

[PILIHAN] 2
Masukkan parent tugas: Pemlan
Masukkan nama tugas: Quiz 3
[SUKSES] Tugas berhasil ditambahkan

[LOG]
+----------+----------+------------------------+-----------+
| 10:00:01 | member1  | Menambahkan tugas      | Quiz 3    |
+----------+----------+------------------------+-----------+
```

---

## 📬 Kontak
Untuk pertanyaan atau kontribusi, silakan hubungi tim pengembang atau buka issue di repository ini.

_(Last updated: 2025-06-14)_
