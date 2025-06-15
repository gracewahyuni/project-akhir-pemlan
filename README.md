# 🎓 Java Project: Sistem Antrian Role dengan Manajemen Tugas

## 📌 Deskripsi Singkat

Program ini adalah aplikasi berbasis **Java Console** yang mensimulasikan sistem manajemen tugas dengan role **berbasis antrian (queue)** dan fitur seperti **pengelolaan tree tugas**, **undo/redo**, serta **log aktivitas**.

Terdapat tiga role:

1. `member1`
2. `member2`
3. `admin` (management role)

Program dijalankan secara **FIFO (First In First Out)** berdasarkan role yang masuk ke dalam queue.

---

## ⚙️ Fitur Utama

### ✅ Untuk Member (`member1`, `member2`)

Saat giliran member aktif, mereka memiliki 8 pilihan menu:

```
1. Lihat tugas
2. Tambah tugas
3. Hapus tugas
4. Cari tugas berdasarkan nama
5. Sorting tugas berdasarkan prioritas
6. Undo
7. Redo
8. Exit
```

- **Lihat tugas**: menampilkan struktur data tugas dalam format tree:

  ```
  1. pemlan
     - quiz
        > quiz 1
        > quiz 2
  2. pemweb
     - Quiz
     - Project
  ```

- **Tambah tugas**: pengguna memilih di mana tugas akan ditambahkan.
- **Hapus tugas**: pengguna memilih nama tugas yang ingin dihapus.
- **Cari tugas**: mencari tugas berdasarkan nama menggunakan traversal tree.
- **Sorting tugas**: menyortir anak-anak dari node tertentu berdasarkan prioritas.
- **Undo/Redo**: mengembalikan atau mengulangi aksi terakhir yang dilakukan (tambah/hapus).
- **Exit**: melanjutkan giliran ke role berikutnya.

### 🔐 Untuk Admin

Admin hanya memiliki dua opsi:

```
1. Lihat log aktivitas
2. Exit
```

- **Lihat log aktivitas**: menampilkan semua aktivitas yang dilakukan oleh member sebelumnya dalam format tabel:

```
+------------+----------+------------------------+-------------+
|   Waktu    |  Nama    |         Aksi           |   Detail    |
+------------+----------+------------------------+-------------+
| 10:00:01   | member1  | Menambahkan tugas      | quiz 3      |
| 10:02:15   | member2  | Menghapus tugas        | Project     |
| 10:03:10   | member1  | Undo                   | quiz 3      |
+------------+----------+------------------------+-------------+
```

Setelah admin `exit`, program akan berhenti jika queue role sudah kosong.

---

## 🗂️ Struktur Folder

```
TaskManager/
│
├── Main.java                  // Entry point program
├── App.java                   // Mengelola queue dan alur utama
│
├── models/
│   ├── TaskNode.java          // Struktur node dalam tree
│   ├── TaskTree.java          // Operasi tree: add, delete, search, sort
│   └── Action.java            // Menyimpan informasi undo/redo
│
├── services/
│   ├── MemberService.java     // Menyediakan menu dan aksi untuk member
│   ├── AdminService.java      // Menu log untuk admin
│   └── HistoryManager.java    // Stack undo/redo
│
├── utils/
│   ├── Logger.java            // Menulis dan menampilkan log aktivitas
│   └── InputUtil.java         // Utilitas input scanner, validasi, dsb.
```

---

## 🧠 Struktur Data

- **Antrian (Queue):** untuk menyimpan giliran member
- **Tree (TaskTree):** untuk menyimpan struktur tugas
- **Stack (Undo/Redo):** menyimpan aksi perubahan
- **ArrayList (Log):** menyimpan riwayat aktivitas

---

## 🧪 Contoh Alur Eksekusi

```
Queue: [member1, member2, admin]

→ member1 login
→ tambah tugas "quiz 3" ke pemlan/quiz
→ hapus tugas "quiz 1"
→ undo (mengembalikan quiz 1)
→ exit

→ member2 login
→ hapus tugas "project"
→ exit

→ admin login
→ lihat log aktivitas
→ exit

Program selesai.
```

---

## 💡 Catatan Tambahan

- Semua operasi bersifat **berurutan per role**
- Data tree bersifat **dinamis**
- Undo/Redo hanya berlaku untuk penambahan dan penghapusan tugas
- Log tidak dihapus, tetap tersimpan hingga akhir program

---
