# 🧪 Matriks Pengujian (Testing Matrix)

| Test Case | Login           | Barang          | User             | Transaksi       | Hasil         |
|-----------|------------------|------------------|-------------------|------------------|---------------|
| TC1       | Valid            | Lengkap & Valid  | Admin Valid       | Tunai - 1 Item   | ✅ Valid      |
| TC2       | Valid            | Harga Negatif    | Kasir Tanpa Nama  | Kartu - 5 Item   | ✅ Valid      |
| TC3       | Valid            | Stok Kosong      | Role Tidak Valid  | QRIS - >10 Item  | ❌ Tidak Valid|
| TC4       | Password Salah   | Lengkap & Valid  | Kasir Tanpa Nama  | QRIS - >10 Item  | ✅ Valid      |
| TC5       | Password Salah   | Harga Negatif    | Role Tidak Valid  | Tunai - 1 Item   | ❌ Tidak Valid|
| TC6       | Password Salah   | Stok Kosong      | Admin Valid       | Kartu - 5 Item   | ✅ Valid      |
| TC7       | Username Kosong  | Lengkap & Valid  | Role Tidak Valid  | Kartu - 5 Item   | ❌ Tidak Valid|
| TC8       | Username Kosong  | Harga Negatif    | Admin Valid       | QRIS - >10 Item  | ✅ Valid      |
| TC9       | Username Kosong  | Stok Kosong      | Kasir Tanpa Nama  | Tunai - 1 Item   | ❌ Tidak Valid|


