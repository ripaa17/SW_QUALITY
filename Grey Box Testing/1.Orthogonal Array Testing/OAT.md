# Pengujian Array Ortogonal (OAT) 
  Pengujian Array Ortogonal (OAT)adalah teknik pengujian perangkat lunak yang menggunakan array ortogonal untuk membuat kasus uji. Ini adalah pendekatan
  pengujian statistik yang sangat berguna ketika sistem yang akan diuji memiliki input data yang besar. Pengujian susunan ortogonal membantu memaksimalkan 
  cakupan pengujian dengan memasangkan dan menggabungkan input serta menguji sistem dengan
  jumlah kasus pengujian yang relatif lebih sedikit untuk menghemat waktu.
   
🧩 FAKTOR & LEVEL UNTUK SETIAP FITUR
---
pada tahap ini terdapat beberapa faktor yang akan  diuji dari fitur login, penambahan barang, penambahan user, dan transaksi.
---
## ✅ Tabel Pengujian Fitur Login (Admin & Kasir) 
| No | Skenario Pengujian                                       | Test Case                                               | Hasil yang Diharapkan                                                   | Status |
|----|----------------------------------------------------------|----------------------------------------------------------|-------------------------------------------------------------------------|--------|
| 1  | Login Admin dengan username dan password benar           | Username: Eva, Password: 123456                          | Admin berhasil login dan masuk ke dashboard admin                      | ✅     |
| 2  | Login Admin dengan username benar tapi password salah    | Username: Eva, Password: 654321                          | Sistem menolak login, tampilkan pesan: "Username dan Password salah"   | ✅     |
| 3  | Login Admin dengan username kosong dan password terisi   | Username: (kosong), Password: 123456                     | Sistem menampilkan pesan: "Username belum diisi"                       | ✅     |
| 4  | Login Admin dengan username dan password kosong          | Username: (kosong), Password: (kosong)                   | Sistem menampilkan pesan: "Harap isi username dan password"            | ✅     |
| 5  | Login Admin dengan username salah dan password benar     | Username: Eeva, Password: 123456                         | Sistem menolak login, tampilkan pesan: "Username dan Password salah"   | ✅     |
| 6  | Login Kasir dengan username dan password benar           | Username: Dede, Password: 098765                         | Kasir berhasil login ke halaman transaksi                              | ✅     |
| 7  | Login Kasir dengan username benar tapi password salah    | Username: Dede, Password: 123456                         | Sistem menolak login, tampilkan pesan: "Username dan Password salah"   | ✅     |
| 8  | Login Kasir dengan username salah dan password benar     | Username: Dodi, Password: 098765                         | Sistem menolak login, tampilkan pesan: "Username dan Password salah"   | ✅     |
| 9  | Login Kasir dengan username dan password kosong          | Username: (kosong), Password: (kosong)                   | Sistem menampilkan pesan: "Harap isi username dan password"            | ✅     |

