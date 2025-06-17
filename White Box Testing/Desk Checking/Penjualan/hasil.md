# ✅ Hasil Uji (Test Case) - Cetak Bukti Transaksi (`transaksi_selesai.php`)

## 📄 Deskripsi
Uji coba dilakukan terhadap tampilan dan fungsionalitas cetak struk setelah transaksi selesai, termasuk data pelanggan, barang, serta perhitungan total, bayar, dan kembalian.

---

## ⚙️ Lingkungan Uji
- Bahasa: PHP
- Database: MySQL
- File Uji: `transaksi_selesai.php`
- Data Dummy: transaksi dan detail barang

---

## ✅ Test Case 1 - Tampil Struk Lengkap

**Input:**
- URL Parameter: `idtrx=1`
- Tabel `transaksi`:
  | id_transaksi | nomor  | tanggal_waktu        | nama    | total | bayar | kembali |
  |--------------|--------|----------------------|---------|-------|--------|----------|
  | 1            | 123456 | 2025-06-17 12:00:00  | kasir1  | 25000 | 30000  | 5000     |
  
- Tabel `transaksi_detail`:
  | id_barang | nama       | qty | harga | total |
  |-----------|------------|-----|--------|--------|
  | 1         | Minyak Goreng | 2   | 10000  | 20000 |
  | 2         | Sabun        | 1   | 5000   | 5000  |

**Langkah Desk Checking:**
1. Ambil data transaksi berdasarkan `idtrx`
2. Ambil data detail barang menggunakan `INNER JOIN` ke tabel `barang`
3. Tampilkan:
   - Header toko
   - Nomor transaksi dan waktu
   - List barang, qty, harga, dan total
   - Total pembayaran, jumlah bayar, dan kembalian
4. Format angka menggunakan `number_format()`
5. Tampilan HTML rapi dan informatif

**Output yang Diharapkan:**
- Struk tampil lengkap dan benar
- Format angka dan tanggal sesuai
- Tidak ada error

**Status:** ✅ LULUS

---

## ✅ Test Case 2 - Transaksi Tidak Ditemukan

**Input:**
- URL Parameter: `idtrx=9999` (tidak ada di database)

**Langkah Desk Checking:**
- Query `SELECT * FROM transaksi WHERE id_transaksi='9999'` menghasilkan `false`
- `mysqli_fetch_assoc` akan mengembalikan `null`
- Akses terhadap `$trx['nomor']` akan menghasilkan error

**Output yang Diharapkan:**
- Penanganan error ditampilkan atau dialihkan ke halaman error

**Catatan:** Belum ada validasi jika transaksi tidak ditemukan.

**Status:** ❌ Gagal - Butuh validasi

---

## ✅ Test Case 3 - Format Tanggal dan Uang

**Input:**
- Tanggal transaksi: `2025-06-17 12:00:00`
- Bayar: `30000`
- Kembali: `5000`

**Langkah Desk Checking:**
- Tanggal diformat dengan `date('d-m-Y H:i:s')` → `17-06-2025 12:00:00`
- Harga diformat dengan `number_format()` → `30,000`, `5,000`, dst.

**Output yang Diharapkan:**
- Format sesuai standar lokal
- Tanggal mudah dibaca

**Status:** ✅ LULUS

---

## ✅ Test Case 4 - Barang Tidak Ada di Detail

**Input:**
- Transaksi valid, tapi tidak ada barang di `transaksi_detail`

**Langkah Desk Checking:**
- Loop `while($row = mysqli_fetch_array($detail))` tidak menampilkan apapun

**Output yang Diharapkan:**
- Tidak tampil data barang
- Total tetap 0

**Status:** ✅ LULUS (kosong wajar)

---

## 📌 Rekomendasi Perbaikan
- ❗ Tambahkan validasi jika `id_trx` tidak ditemukan
- ✅ Tambahkan tombol "Kembali" atau "Cetak Struk"
- ✅ Tambahkan CSS untuk tampilan cetak lebih baik
- ✅ Pertimbangkan menambahkan QR Code atau ID transaksi unik

---

## 🗂️ Struktur Tabel Terkait
- `transaksi(id_transaksi, tanggal_waktu, nomor, total, nama, bayar, kembali)`
- `transaksi_detail(id_transaksi_detail, id_transaksi, id_barang, harga, qty, total, diskon)`
- `barang(id_barang, nama, ...)`

---

## 📝 Catatan Umum
- Proses cetak bukti transaksi berjalan dengan benar
- Validasi minimal dibutuhkan agar lebih tahan terhadap kesalahan input


