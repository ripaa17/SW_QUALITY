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


