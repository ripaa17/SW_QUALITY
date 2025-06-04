## Matrix Testing
**Matrix Testing** adalah teknik pengujian perangkat lunak yang sistematis dan terstruktur untuk
 menguji berbagai kombinasi input dan kondisi dalam suatu aplikasi. Teknik ini membantu
 mengidentifikasi bug yang disebabkan oleh interaksi antara parameter atau faktor yang berbeda
 dalam aplikasi.
 
# Parameter dan Kondisi Pengujian Fitur Sistem Pada Aplikasi Kasir
---
## 🔐 1. Fitur Login
**Parameter:**  
- Username  
- Password  
- Role  

**Kondisi Pengujian:**  
- Username, password, dan role valid → Berhasil login.  
- Username tidak terdaftar → Gagal login.  
- Password salah → Gagal login.  
- Role tidak dipilih → Gagal login / peringatan.  
- Semua field kosong → Gagal login / wajib isi.  

---
## 📦 2. Fitur Penambahan Barang
**Parameter:**  
- Kode Barang  
- Nama Barang  
- Harga Barang  
- Stok Barang 

**Kondisi Pengujian:**  
- Semua field diisi dengan benar → Barang berhasil ditambahkan.  
- Nama barang atau kode kosong → Gagal tambah / error.  
- Harga negatif atau 0 → Tidak valid → gagal simpan.  
- Stok barang kosong atau huruf → Gagal / error input.  
- Kode barang sama dengan yang sudah ada → Gagal (duplikat).  

---
## 👤 3. Fitur Penambahan User
**Parameter:**  
- Username  
- Password  
- Role  

**Kondisi Pengujian:**  
- Semua field valid dan unik → User berhasil ditambahkan.  
- Username kosong atau sudah ada → Gagal / error.  
- Password kosong atau kurang dari 6 karakter → Ditolak.  
- Role tidak dipilih → Gagal tambah / warning.  

---
## 💰 4. Fitur Transaksi
**Parameter:**  
- Kode Barang  
- Jumlah Beli (Qty)  
- Harga  
- Total  
- Uang Bayar  

**Kondisi Pengujian:**  
- Semua input valid → Transaksi berhasil, kembalian ditampilkan.  
- Qty = 0 atau negatif → Gagal transaksi.  
- Bayar < Total → Gagal: Uang kurang.  
- Bayar tidak diisi atau bukan angka → Error input.  
- Total < 0 → Error / input tidak valid.  
- Bayar = Total → Transaksi berhasil, kembalian 0.  

# Matrix Testing

---

## 🔐 1. Fitur Login
## Matrix Testing Fitur Login (Admin & Kasir)

| No | Username    | Password | Role  | Hasil yang diharapkan                                         | Status |
|-----|-------------|----------|-------|---------------------------------------------------------------|--------|
| 1   | Eva         | 123456   | Admin | Admin berhasil login dan masuk ke dashboard admin             | ✅     |
| 2   | Eva         | 654321   | Admin | Sistem menolak login, tampilkan pesan: "Username dan Password salah" | ✅     |
| 3   | (kosong)    | 123456   | Admin | Sistem menolak login, tampilkan pesan: "Username dan Password salah" | ✅     |
| 4   | (kosong)    | (kosong) | Admin | Sistem menolak login, tampilkan pesan: "Username dan Password salah" | ✅     |
| 5   | Eeva        | 123456   | Admin | Sistem menolak login, tampilkan pesan: "Username dan Password salah" | ✅     |
| 6   | Dede        | 098765   | Kasir | Kasir berhasil login ke halaman transaksi                      | ✅     |
| 7   | Dede        | 123456   | Kasir | Sistem menolak login, tampilkan pesan: "Username dan Password salah" | ✅     |
| 8   | Dodi        | 098765   | Kasir | Sistem menolak login, tampilkan pesan: "Username dan Password salah" | ✅     |
| 9   | (kosong)    | (kosong) | Kasir | Sistem menolak login, tampilkan pesan: "Username dan Password salah" | ✅     |
---

## 📦 2. Fitur Penambahan Barang
| TC  | Kode   | Nama               | Harga  | Jumlah Stok | Hasil yang Diharapkan           | Status |
|-----|--------|--------------------|--------|-------------|--------------------------------|--------|
| TC1 | B0059  | Bola Basket Besar  | 60000  | 10          | Berhasil tambah barang (valid) | ✅     |
| TC2 | B0055  | Sabun Mandi        | 2500   | 10          | Berhasil tambah barang (valid) | ✅     |
| TC3 | B0054  | Pasta Gigi         | 2000   | 20          | Berhasil tambah barang (valid) | ✅     |
| TC4 | B0053  | Sampoo Botol 350ml | 16000  | 10          | Berhasil tambah barang (valid) | ✅     |
| TC5 | B0056  | Balsem             | 5000   | 10          | Berhasil tambah barang (valid) | ✅     |
| TC6 | B0052  | Sapu Lidi          | 10000  | 10          | Berhasil tambah barang (valid) | ✅     |
| TC7 | B0051  | Sandal             | 12000  | 10          | Berhasil tambah barang (valid) | ✅     |
| TC8 | B0040  | Minyak             | 22000  | 10          | Berhasil tambah barang (valid) | ✅     |
| TC9 | B0088  | Salak Buah         | 5000   | 10          | Berhasil tambah barang (valid) | ✅     |
---

## 👤 3. Fitur Penambahan User
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

## 💰 4. Fitur Transaksi
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



