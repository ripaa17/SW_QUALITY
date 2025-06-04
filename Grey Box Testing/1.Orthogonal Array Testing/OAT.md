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

---
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
| TC2 | B0055  | Sabun Mandi        | 2500   | 10           | ✅ Berhasil (data valid)      |
| TC3 | B0054  | Pasta Gigi         | 2000   | 20           | ✅ Berhasil (data valid)                      |
| TC4 | B0053  | Sampoo Botol 350ml | 16000  | 10           | ✅ Berhasil (data valid)  |
| TC5 | B0056  | Balsem             | 5000   | 10           | ✅ Berhasil (data valid)                        |
| TC6 | B0052  | Sapu Lidi          | 10000  | 10           | ✅ Berhasil (data valid)                   |
| TC7 | B0051  | Sandal             | 12000  | 10           | ✅ Berhasil (data valid)                   |
| TC8 | B0040  | Minyak             | 22000  | 10           | ✅ Berhasil (data valid)                   |
| TC9 | B0088  | Salak Buah         | 5000   | 10           | ✅ Berhasil (data valid)                   |

---
Total Pengujian: 9
Berhasil (✅): 9
Gagal (❌): 0
Catatan:
Dari 9 pengujian yang dilakukan dengan data valid, seluruhnya berhasil ✅. Hal ini menunjukkan bahwa sistem dapat menambahkan barang dengan benar saat input sesuai. Untuk memastikan sistem lebih kuat, pengujian dengan data tidak valid (seperti kode duplikat, harga nol, atau nama kosong) juga perlu dilakukan.
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
| TC  | Kode   | Nama Barang         | Harga  | Qty | Total   | Bayar   | Kembalian yang Diharapkan | Hasil yang Diharapkan           | Status |
|-----|--------|---------------------|--------|-----|---------|---------|-----------------------------|----------------------------------|--------|
| TC1 | B0059  | Bola Basket Besar   | 60000  | 1   | 60000   | 70000   | 10000                       | Transaksi berhasil              | ✅     |
| TC2 | B0055  | Sabun Mandi         | 2500   | 1   | 2500    | 2500    | 0                           | Transaksi berhasil              | ✅     |
| TC3 | B0054  | Pasta Gigi          | 2000   | 1   | 2000    | 5000    | 3000                        | Transaksi berhasil              | ✅     |
| TC4 | B0053  | Sampoo Botol 350ml  | 16000  | 1   | 16000   | 20000   | 4000                        | Transaksi berhasil              | ✅     |
| TC5 | B0056  | Balsem              | 5000   | 1   | 5000    | 4000    | -                           | Gagal: Uang bayar tidak cukup   | ✅     |
| TC6 | B0052  | Sapu Lidi           | 10000  | 0   | 0       | 10000   | -                           | Gagal: Qty tidak boleh 0        | ✅     |
| TC7 | B0051  | Sandal              | 12000  | -1  | -12000  | 12000   | -                           | Gagal: Qty tidak valid          | ✅     |
| TC8 | B0040  | Minyak              | 22000  | 1   | 22000   | abc     | -                           | Gagal: Input bayar tidak valid  | ✅     |
| TC9 | B0088  | Salak Buah          | 5000   | 1   | 5000    | 5000    | 0                           | Transaksi berhasil              | ✅     |
---
Dari 9 test case yang diuji, sistem berhasil menangani berbagai kondisi transaksi dengan baik, termasuk pembayaran yang cukup, kembalian, dan validasi input. Semua skenario berjalan sesuai harapan dengan hasil 100% berhasil (✅ semua). Fitur pembayaran dinyatakan berfungsi dengan baik dan stabil.
