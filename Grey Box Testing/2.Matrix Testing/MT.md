## Matrix Testing
**Matrix Testing** adalah teknik pengujian perangkat lunak yang sistematis dan terstruktur untuk
 menguji berbagai kombinasi input dan kondisi dalam suatu aplikasi. Teknik ini membantu
 mengidentifikasi bug yang disebabkan oleh interaksi antara parameter atau faktor yang berbeda
 dalam aplikasi.
 
# Parameter dan Kondisi Pengujian Fitur Sistem Pada Aplikasi Kasir
## 📦 Fitur Penambahan Barang
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



