# Pengujian Array Ortogonal (OAT) 
  Pengujian Array Ortogonal (OAT)adalah teknik pengujian perangkat lunak yang menggunakan array ortogonal untuk membuat kasus uji. Ini adalah pendekatan
  pengujian statistik yang sangat berguna ketika sistem yang akan diuji memiliki input data yang besar. Pengujian susunan ortogonal membantu memaksimalkan 
  cakupan pengujian dengan memasangkan dan menggabungkan input serta menguji sistem dengan
  jumlah kasus pengujian yang relatif lebih sedikit untuk menghemat waktu.
  
🧩 FAKTOR & LEVEL UNTUK SETIAP FITUR
---
| Fitur                 | Faktor                    | Level 1         | Level 2          | Level 3          |
| --------------------- | ------------------------- | --------------- | ---------------- | ---------------- |
| **Login**             | Kombinasi Input Login     | Valid           | Password Salah   | Username Kosong  |
| **Penambahan Barang** | Validasi Data Barang      | Lengkap & Valid | Harga Negatif    | Stok Kosong      |
| **Penambahan User**   | Role & Input User         | Admin Valid     | Kasir Tanpa Nama | Role Tidak Valid |
| **Transaksi**         | Jenis & Jumlah Pembayaran | Tunai - 1 Item  | Kartu - 5 Item   | QRIS - >10 Item  |
---
📋 TABEL ORTHOGONAL ARRAY (L9)
| TC# | Login           | Barang          | User             | Transaksi       |
| --- | --------------- | --------------- | ---------------- | --------------- |
| TC1 | Valid           | Lengkap & Valid | Admin Valid      | Tunai - 1 Item  |
| TC2 | Valid           | Harga Negatif   | Kasir Tanpa Nama | Kartu - 5 Item  |
| TC3 | Valid           | Stok Kosong     | Role Tidak Valid | QRIS - >10 Item |
| TC4 | Password Salah  | Lengkap & Valid | Kasir Tanpa Nama | QRIS - >10 Item |
| TC5 | Password Salah  | Harga Negatif   | Role Tidak Valid | Tunai - 1 Item  |
| TC6 | Password Salah  | Stok Kosong     | Admin Valid      | Kartu - 5 Item  |
| TC7 | Username Kosong | Lengkap & Valid | Role Tidak Valid | Kartu - 5 Item  |
| TC8 | Username Kosong | Harga Negatif   | Admin Valid      | QRIS - >10 Item |
| TC9 | Username Kosong | Stok Kosong     | Kasir Tanpa Nama | Tunai - 1 Item  |
