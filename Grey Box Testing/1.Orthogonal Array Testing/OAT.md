# Pengujian Array Ortogonal (OAT) 
  Pengujian Array Ortogonal (OAT)adalah teknik pengujian perangkat lunak yang menggunakan array ortogonal untuk membuat kasus uji. Ini adalah pendekatan
  pengujian statistik yang sangat berguna ketika sistem yang akan diuji memiliki input data yang besar. Pengujian susunan ortogonal membantu memaksimalkan 
  cakupan pengujian dengan memasangkan dan menggabungkan input serta menguji sistem dengan
  jumlah kasus pengujian yang relatif lebih sedikit untuk menghemat waktu.
   
🧩 FAKTOR & LEVEL UNTUK SETIAP FITUR
---
pada tahap ini terdapat beberapa faktor yang akan  diuji dari fitur login, penambahan barang, penambahan user, dan transaksi.
---
**Pengujian pada Fitur Login
---
| No | Skenario Pengujian                          | Test Case                                                              | Hasil yang Diharapkan                                              | Status |
|----|---------------------------------------------|------------------------------------------------------------------------|--------------------------------------------------------------------|--------|
| 1  | Login Admin dengan Username & Password      | Username: Eva, Password: 123456                                        | Admin berhasil login dan masuk ke dashboard admin                 | ✅     |
| 2  | Login Admin tapi password salah             | Username: Eva, Password: 654321                                        | Sistem menolak login, pesan: "Username dan Password Salah"        | ❌     |
| 3  | Login Admin dengan QR Code saat offline     | Admin memindai QR Code saat koneksi terputus                          | Sistem menampilkan error: "Koneksi tidak tersedia"                | ✅     |
| 4  | Login Kasir dengan Username & Password      | Username dan password valid, koneksi lambat                           | Kasir berhasil login dengan sedikit delay                         | ✅     |
| 5  | Login Kasir dengan PIN saat koneksi terputus| Kasir login menggunakan PIN tanpa koneksi                             | Sistem menampilkan pesan gagal login akibat koneksi               | ✅     |
| 6  | Login Kasir dengan QR Code saat koneksi normal| Kasir login dengan QR Code dalam kondisi normal                       | Kasir berhasil login ke halaman transaksi                         | ✅     |
