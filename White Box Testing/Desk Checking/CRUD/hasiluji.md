# 📋 Hasil Uji CRUD Barang - Metode Desk Checking

## 🧪 Tujuan
Memastikan bahwa semua fungsi CRUD (Create, Read, Update, Delete) bekerja sesuai harapan tanpa error menggunakan metode desk checking.

---

## ✅ Test Case 1 - Tambah Barang (Create)

**Input:**
- Nama Barang: Pensil
- Kode Barang: P001
- Harga: 3000
- Jumlah: 100

**Langkah-langkah Desk Checking:**
1. Periksa apakah form dikirim (`isset($_POST['simpan'])`)
2. Simpan input ke variabel `$nama`, `$kode_barang`, `$harga`, `$jumlah`
3. Jalankan query `INSERT INTO barang ...`
4. Redirect ke halaman `index.php?page=barang`

**Output yang Diharapkan:**  
Data tersimpan dan user diarahkan kembali ke halaman list barang.

---

## ✅ Test Case 2 - Edit Barang (Update)

**Input:**
- ID Barang: 1
- Nama Barang: Pensil 2B
- Harga: 3500
- Jumlah: 120

**Langkah-langkah Desk Checking:**
1. Periksa apakah form update dikirim dan ID tersedia
2. Perbarui data dengan query `UPDATE barang ...`
3. Redirect ke `index.php?page=barang`

**Output yang Diharapkan:**  
Data pada ID 1 diperbarui sesuai input.

---

## ✅ Test Case 3 - Hapus Barang (Delete)

**Input:**
- ID Barang: 1 (melalui `$_GET['delete_id']`)

**Langkah-langkah Desk Checking:**
1. Periksa apakah parameter `delete_id` ada
2. Jalankan query `DELETE FROM barang WHERE id_barang='1'`
3. Set session message dan redirect ke `index.php?page=barang`

**Output yang Diharapkan:**  
Barang dengan ID 1 dihapus dari database.

---

## ✅ Test Case 4 - Validasi Input Kosong

**Input:**  
Semua field kosong

**Langkah-langkah Desk Checking:**
1. Form tetap dikirim tapi tidak ada validasi input di sisi server
2. Query tetap dijalankan dan data kosong masuk

**Rekomendasi:**  
Tambahkan validasi:
```php
if (empty($nama) || empty($kode_barang) || empty($harga) || empty($jumlah)) {
    // tampilkan pesan error
}

