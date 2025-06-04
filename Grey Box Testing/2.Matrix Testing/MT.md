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
- Satuan  

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

# Membuat Tabel Matrix Testing

---

## 🔐 1. Fitur Login

| No | Username        | Password       | Role          | Expected Result                    |
|-----|-----------------|----------------|---------------|----------------------------------|
| 1   | Valid           | Valid          | Admin         | Berhasil login                   |
| 2   | Valid           | Valid          | Kasir         | Berhasil login                   |
| 3   | Valid           | Valid          | Tidak dipilih | Gagal login / peringatan         |
| 4   | Valid           | Salah          | Admin         | Gagal login                     |
| 5   | Valid           | Salah          | Kasir         | Gagal login                     |
| 6   | Tidak terdaftar | Valid          | Admin         | Gagal login                     |
| 7   | Tidak terdaftar | Salah          | Kasir         | Gagal login                     |
| 8   | Kosong          | Kosong         | Kosong        | Gagal login / wajib isi           |

---

## 📦 2. Fitur Penambahan Barang

| No | Kode Barang     | Nama Barang    | Harga Barang  | Stok Barang      | Satuan     | Expected Result                   |
|-----|-----------------|----------------|---------------|------------------|------------|----------------------------------|
| 1   | Valid unik      | Valid          | > 0           | Valid angka      | Valid      | Barang berhasil ditambahkan       |
| 2   | Kosong          | Valid          | > 0           | Valid angka      | Valid      | Gagal tambah / error              |
| 3   | Valid unik      | Kosong         | > 0           | Valid angka      | Valid      | Gagal tambah / error              |
| 4   | Valid unik      | Valid          | 0 / negatif   | Valid angka      | Valid      | Gagal simpan (harga tidak valid) |
| 5   | Valid unik      | Valid          | > 0           | Kosong / huruf   | Valid      | Gagal / error input stok          |
| 6   | Duplikat kode   | Valid          | > 0           | Valid angka      | Valid      | Gagal (kode barang duplikat)     |

---

## 👤 3. Fitur Penambahan User

| No | Username        | Password           | Role           | Expected Result                  |
|-----|-----------------|--------------------|----------------|--------------------------------|
| 1   | Valid unik      | ≥ 6 karakter       | Admin / Kasir  | User berhasil ditambahkan       |
| 2   | Kosong          | Valid              | Admin / Kasir  | Gagal / error                  |
| 3   | Sudah ada       | Valid              | Admin / Kasir  | Gagal / error                  |
| 4   | Valid unik      | Kosong / < 6 karakter | Admin / Kasir | Ditolak                       |
| 5   | Valid unik      | Valid              | Tidak dipilih  | Gagal tambah / warning         |

---

## 💰 4. Fitur Transaksi

| No | Kode Barang     | Jumlah Beli (Qty) | Harga          | Total          | Uang Bayar        | Expected Result                    |
|-----|-----------------|-------------------|----------------|----------------|-------------------|----------------------------------|
| 1   | Valid           | > 0               | Valid          | Valid          | ≥ Total           | Transaksi berhasil, kembalian ditampilkan |
| 2   | Valid           | 0 / negatif       | Valid          | Valid          | Valid             | Gagal transaksi                   |
| 3   | Valid           | Valid             | Valid          | Negatif        | Valid             | Error / input tidak valid         |
| 4   | Valid           | Valid             | Valid          | Valid          | < Total           | Gagal: Uang kurang                |
| 5   | Valid           | Valid             | Valid          | Valid          | Kosong / bukan angka | Error input                   |
| 6   | Valid           | Valid             | Valid          | Valid          | = Total           | Transaksi berhasil, kembalian 0  |

# Hasil Test Case

---

## 🔐 1. Fitur Login

| No | Username        | Password       | Role          | Expected Result                    | Status Pengujian |
|-----|-----------------|----------------|---------------|----------------------------------|------------------|
| 1   | Valid           | Valid          | Admin         | Berhasil login                   | ✅               |
| 2   | Valid           | Valid          | Kasir         | Berhasil login                   | ✅               |
| 3   | Valid           | Valid          | Tidak dipilih | Gagal login / peringatan         | ❌               |
| 4   | Valid           | Salah          | Admin         | Gagal login                     | ❌               |
| 5   | Valid           | Salah          | Kasir         | Gagal login                     | ❌               |
| 6   | Tidak terdaftar | Valid          | Admin         | Gagal login                     | ❌               |
| 7   | Tidak terdaftar | Salah          | Kasir         | Gagal login                     | ❌               |
| 8   | Kosong          | Kosong         | Kosong        | Gagal login / wajib isi           | ❌               |

---

## 📦 2. Fitur Penambahan Barang

| No | Kode Barang     | Nama Barang    | Harga Barang  | Stok Barang      | Satuan     | Expected Result                   | Status Pengujian |
|-----|-----------------|----------------|---------------|------------------|------------|----------------------------------|------------------|
| 1   | Valid unik      | Valid          | > 0           | Valid angka      | Valid      | Barang berhasil ditambahkan       | ✅               |
| 2   | Kosong          | Valid          | > 0           | Valid angka      | Valid      | Gagal tambah / error              | ❌               |
| 3   | Valid unik      | Kosong         | > 0           | Valid angka      | Valid      | Gagal tambah / error              | ❌               |
| 4   | Valid unik      | Valid          | 0 / negatif   | Valid angka      | Valid      | Gagal simpan (harga tidak valid) | ❌               |
| 5   | Valid unik      | Valid          | > 0           | Kosong / huruf   | Valid      | Gagal / error input stok          | ❌               |
| 6   | Duplikat kode   | Valid          | > 0           | Valid angka      | Valid      | Gagal (kode barang duplikat)     | ❌               |

---

## 👤 3. Fitur Penambahan User

| No | Username        | Password           | Role           | Expected Result                  | Status Pengujian |
|-----|-----------------|--------------------|----------------|--------------------------------|------------------|
| 1   | Valid unik      | ≥ 6 karakter       | Admin / Kasir  | User berhasil ditambahkan       | ✅               |
| 2   | Kosong          | Valid              | Admin / Kasir  | Gagal / error                  | ❌               |
| 3   | Sudah ada       | Valid              | Admin / Kasir  | Gagal / error                  | ❌               |
| 4   | Valid unik      | Kosong / < 6 karakter | Admin / Kasir | Ditolak                       | ❌               |
| 5   | Valid unik      | Valid              | Tidak dipilih  | Gagal tambah / warning         | ❌               |

---

## 💰 4. Fitur Transaksi

| No | Kode Barang     | Jumlah Beli (Qty) | Harga          | Total          | Uang Bayar        | Expected Result                    | Status Pengujian |
|-----|-----------------|-------------------|----------------|----------------|-------------------|----------------------------------|------------------|
| 1   | Valid           | > 0               | Valid          | Valid          | ≥ Total           | Transaksi berhasil, kembalian ditampilkan | ✅               |
| 2   | Valid           | 0 / negatif       | Valid          | Valid          | Valid             | Gagal transaksi                   | ❌               |
| 3   | Valid           | Valid             | Valid          | Negatif        | Valid             | Error / input tidak valid         | ❌               |
| 4   | Valid           | Valid             | Valid          | Valid          | < Total           | Gagal: Uang kurang                | ❌               |
| 5   | Valid           | Valid             | Valid          | Valid          | Kosong / bukan angka | Error input                   | ❌               |
| 6   | Valid           | Valid             | Valid          | Valid          | = Total           | Transaksi berhasil, kembalian 0  | ✅               |

# 🧪 Analisa Hasil Test
| No | Fitur                  | Test Case Gagal | Penyebab Kegagalan Utama                              | Rekomendasi Perbaikan                                                                 |
|----|------------------------|-----------------|--------------------------------------------------------|----------------------------------------------------------------------------------------|
| 1  | Login                  | 3, 4, 5, 6, 7, 8 | Role tidak dipilih, password salah, akun tidak terdaftar, input kosong | Tambahkan validasi role wajib, pesan kesalahan spesifik, validasi input kosong        |
| 2  | Penambahan Barang      | 2, 3, 4, 5, 6    | Field kosong, harga/stok tidak valid, kode duplikat    | Validasi semua field wajib diisi, input numerik positif, cek duplikasi kode           |
| 3  | Penambahan User        | 2, 3, 4, 5       | Username kosong atau duplikat, password kurang dari 6 karakter, role tidak dipilih | Validasi panjang password, cek username unik, role wajib dipilih                      |
| 4  | Transaksi              | 2, 3, 4, 5       | Qty = 0/negatif, total negatif, uang bayar kurang, input bukan angka | Validasi Qty > 0, hitung total dari Qty × Harga, uang bayar harus angka & ≥ total    |

---

## 🔧 Detail Rekomendasi Per Fitur

### 1. Login

| Masalah                        | Solusi                                                                 |
|-------------------------------|------------------------------------------------------------------------|
| Role tidak dipilih             | Tambahkan validasi agar role wajib dipilih sebelum login              |
| Password salah / akun tak ada | Tampilkan pesan: "Password salah" / "Akun tidak ditemukan"            |
| Field kosong                   | Validasi frontend agar semua field wajib diisi                        |

---

### 2. Penambahan Barang

| Masalah                           | Solusi                                                                 |
|----------------------------------|------------------------------------------------------------------------|
| Kode / nama barang kosong        | Validasi wajib isi semua field                                        |
| Harga 0 atau negatif             | Validasi harga harus > 0                                              |
| Stok kosong / bukan angka        | Validasi input hanya angka dan tidak boleh kosong                     |
| Kode barang duplikat             | Tambahkan pengecekan kode barang sebelum simpan                       |

---

### 3. Penambahan User

| Masalah                            | Solusi                                                                 |
|-----------------------------------|------------------------------------------------------------------------|
| Username kosong / sudah ada       | Validasi username unik dan tidak boleh kosong                         |
| Password < 6 karakter             | Validasi panjang minimal 6 karakter                                   |
| Role tidak dipilih                | Validasi agar role wajib dipilih sebelum menyimpan                    |

---

### 4. Transaksi

| Masalah                               | Solusi                                                                 |
|--------------------------------------|------------------------------------------------------------------------|
| Qty = 0 atau negatif                  | Validasi Qty harus > 0                                                 |
| Total negatif                        | Periksa kembali rumus perhitungan Total                                |
| Uang bayar < total                   | Tambahkan validasi: "Uang tidak cukup"                                 |
| Uang bayar kosong / bukan angka      | Validasi input uang bayar harus angka dan tidak boleh kosong           |

---

## ✅ Tindak Lanjut

- Lakukan **perbaikan sistem** sesuai rekomendasi di atas.
- **Uji ulang** semua test case yang sebelumnya gagal.
- **Perbarui status** pada tabel test case sesuai hasil pengujian terbaru.
- Dokumentasikan hasil test ulang sebagai versi baru pengujian.

