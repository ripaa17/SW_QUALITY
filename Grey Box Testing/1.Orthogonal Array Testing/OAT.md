# Pengujian Array Ortogonal (OAT) 
  Pengujian Array Ortogonal (OAT)adalah teknik pengujian perangkat lunak yang menggunakan array ortogonal untuk membuat kasus uji. Ini adalah pendekatan
  pengujian statistik yang sangat berguna ketika sistem yang akan diuji memiliki input data yang besar. Pengujian susunan ortogonal membantu memaksimalkan 
  cakupan pengujian dengan memasangkan dan menggabungkan input serta menguji sistem dengan
  jumlah kasus pengujian yang relatif lebih sedikit untuk menghemat waktu.
   
🧩 FAKTOR & LEVEL UNTUK SETIAP FITUR
--
pada tahap ini terdapat beberapa faktor yang akan  diuji dari fitur login, penambahan barang, penambahan user, dan transaksi.
---
## Tabel Pengujian Fitur Login (Admin & Kasir) 
| No | Skenario Pengujian                                       | Test Case                                               | Hasil yang Diharapkan                                                   | Status |
|----|----------------------------------------------------------|----------------------------------------------------------|-------------------------------------------------------------------------|--------|
| 1  | Login Admin dengan username dan password benar           | Username: Eva, Password: 123456                          | Admin berhasil login dan masuk ke dashboard admin                      | ✅     |
| 2  | Login Admin dengan username benar tapi password salah    | Username: Eva, Password: 654321                          | Sistem menolak login, tampilkan pesan: "Username dan Password salah"   | ✅     |
| 3  | Login Admin dengan username kosong dan password terisi   | Username: (kosong), Password: 123456                     | Sistem menolak login, tampilkan pesan: "Username dan Password salah"                         | ❌     |
| 4  | Login Admin dengan username dan password kosong          | Username: (kosong), Password: (kosong)                   | Sistem menolak login, tampilkan pesan: "Username dan Password salah"             | ❌     |
| 5  | Login Admin dengan username salah dan password benar     | Username: Eeva, Password: 123456                         | Sistem menolak login, tampilkan pesan: "Username dan Password salah"   | ✅     |
| 6  | Login Kasir dengan username dan password benar           | Username: Dede, Password: 098765                         | Kasir berhasil login ke halaman transaksi                              | ✅     |
| 7  | Login Kasir dengan username benar tapi password salah    | Username: Dede, Password: 123456                         | Sistem menolak login, tampilkan pesan: "Username dan Password salah"   | ✅     |
| 8  | Login Kasir dengan username salah dan password benar     | Username: Dodi, Password: 098765                         | Sistem menolak login, tampilkan pesan: "Username dan Password salah"   | ✅     |
| 9  | Login Kasir dengan username dan password kosong          | Username: (kosong), Password: (kosong)                   | Sistem menolak login, tampilkan pesan: "Username dan Password salah"   | ❌     |
--
Total Pengujian: 9
Berhasil (✅): 6
Gagal (❌): 3
Catatan:
Semua pengujian dengan input yang benar dinyatakan berhasil. Namun, ada 3 skenario gagal (input kosong) yang belum divalidasi dengan benar oleh sistem.
---
### Pengujian Pada Penambahan Barang
| TC  | Kode   | Nama               | Harga  | Jumlah Stok | Status Uji                                |
|-----|--------|--------------------|--------|--------------|--------------------------------------------|
| TC1 | B0059  | Bola Basket Besar  | 60000  | 10           | ✅ Berhasil (data valid)                   |
| TC2 | B0055  | Sabun Mandi        | 2500   | 10           | ❌ Gagal (kode duplikat, stok negatif)     |
| TC3 | B0054  | Pasta Gigi         | 2000   | 20           | ❌ Gagal (nama kosong)                     |
| TC4 | B0053  | Sampoo Botol 350ml | 16000  | 10           | ❌ Gagal (harga tidak valid, karakter khusus) |
| TC5 | B0056  | Balsem             | 5000   | 10           | ❌ Gagal (harga nol)                       |
| TC6 | B0052  | Sapu Lidi          | 10000  | 10           | ✅ Berhasil (data valid)                   |
| TC7 | B0051  | Sandal             | 12000  | 10           | ❌ Gagal (kode kosong)                     |
| TC8 | B0040  | Minyak             | 22000  | 10           | ❌ Gagal (harga negatif)                   |
| TC9 | B0088  | Salak Buah         | 5000   | 10           | ✅ Berhasil (data valid)                   |
---
Total Pengujian: 9
Berhasil (✅): 3
Gagal (❌): 6
Catatan:
Validasi input pada penambahan barang cukup ketat, dan sistem berhasil menolak banyak input tidak valid (duplikat, harga nol/negatif, karakter khusus, nama kosong, kode kosong). Namun, hal ini menunjukkan kebutuhan validasi sistem sudah cukup baik.
--
### Tabel Pengujian Pada Penambahan User
| TC  | Username | Password | Role Akses | Hasil yang Diharapkan                                     | Status |
|-----|----------|----------|-------------|------------------------------------------------------------|--------|
| TC1 | Eva      | 123456   | Admin       | Berhasil login dan masuk ke dashboard Admin                | ✅     |
| TC2 | Eva      | 098765   | Admin       | Gagal login (password salah)                               | ✅     |
| TC3 | Eva      | 123456   | Kasir       | Gagal login (role tidak sesuai)                            | ✅     |
| TC4 | Dede     | 098765   | Kasir       | Berhasil login dan masuk ke halaman transaksi Kasir        | ✅     |
| TC5 | Dede     | 121212   | Kasir       | Gagal login (password salah)                               | ✅     |
| TC6 | Dede     | 098765   | Admin       | Gagal login (role tidak sesuai)                            | ✅     |
| TC7 | Rahma    | 121212   | Kasir       | Berhasil login dan masuk ke halaman transaksi Kasir        | ✅     |
| TC8 | Rahma    | 123456   | Kasir       | Gagal login (password salah)                               | ✅     |
| TC9 | Rahma    | 121212   | Admin       | Gagal login (role tidak sesuai)                            | ✅     |
---
Total Pengujian: 9
Berhasil (✅): 9
Gagal (❌): 0
Catatan:
Semua test case login berdasarkan kombinasi username, password, dan role berhasil tervalidasi sesuai ekspektasi.
--
### Tabel Pengujian Fitur Pembayaran Transaksi
| TC  | Nama Barang | Harga | Qty | Total | Bayar     | Kembalian yang Diharapkan | Hasil yang Diharapkan               | Status |
|-----|-------------|--------|-----|--------|-----------|-----------------------------|--------------------------------------|--------|
| TC1 | Sapu Lidi   | 10,000 | 1   | 10,000 | 20,000     | 10,000                      | Transaksi berhasil, kembalian benar | ✅     |
| TC2 | Sapu Lidi   | 10,000 | 1   | 10,000 | 5,000      | -                           | Gagal, pembayaran kurang            | ❌     |
| TC3 | Sapu Lidi   | 10,000 | 1   | 10,000 | 10,000     | 0                           | Transaksi berhasil tanpa kembalian  | ✅     |
| TC4 | Sapu Lidi   | 10,000 | 1   | 10,000 | 0          | -                           | Gagal, nominal bayar tidak valid     | ❌     |
| TC5 | Sapu Lidi   | 10,000 | 1   | 10,000 | (kosong)   | -                           | Gagal, input pembayaran wajib diisi  | ❌     |
| TC6 | Sapu Lidi   | 10,000 | 1   | 10,000 | teks: "abc"| -                           | Gagal, input bayar harus numerik     | ❌     |
--
Total Pengujian: 6
Berhasil (✅): 2
Gagal (❌): 4
Catatan:
Sistem hanya berhasil memproses pembayaran yang valid secara numerik dan mencukupi. Validasi pada input kosong, teks, dan nominal tidak mencukupi belum tertangani dengan baik, perlu perbaikan pada sisi input dan validasi pembayaran.
