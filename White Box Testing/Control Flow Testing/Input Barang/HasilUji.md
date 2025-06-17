
# 🧪 Test Case: Halaman Login

## TC-001 — Login dengan kredensial valid ✅
**Deskripsi:** Memastikan pengguna dapat login dengan benar menggunakan `username` dan `password` yang valid.

**Preconditions:**
- Server berjalan dan halaman login dapat diakses.
- Akun `user123` sudah terdaftar dengan `password: pass123`.

**Langkah Uji:**
1. Buka halaman login.
2. Isi `username` dengan `user123`.
3. Isi `password` dengan `pass123`.
4. Klik **Sign in**.

**Hasil yang Diharapkan:**
- Pengguna diarahkan ke dashboard/halaman utama.
- Tidak muncul alert error (`alert-danger`).

---

## TC-002 — Salah password (username valid, password salah) ❌
**Deskripsi:** Login ditolak jika password keliru.

**Preconditions:**
- Akun `user123` sudah terdaftar.

**Langkah Uji:**
1. Buka halaman login.
2. Isi `username` dengan `user123`.
3. Isi `password` dengan `wrongpass`.
4. Klik **Sign in**.

**Hasil yang Diharapkan:**
- Alert merah muncul dengan teks seperti “Username/Password salah”.
- Tidak pindah halaman, tetap di login form.

---

## TC-003 — Username kosong ⚠️
**Deskripsi:** Tidak boleh login kalau username tidak diisi.

**Langkah Uji:**
1. Buka halaman login.
2. Kosongkan `username`.
3. Isi `password` dengan `pass123`.
4. Klik **Sign in**.

**Hasil yang Diharapkan:**
- Muncul alert/validasi “Username wajib diisi”.
- Form tidak terkirim.

---

## TC-004 — Password kosong ⚠️
**Deskripsi:** Tidak boleh login kalau password tidak diisi.

**Langkah Uji:**
1. Buka halaman login.
2. Isi `username` dengan `user123`.
3. Kosongkan `password`.
4. Klik **Sign in**.

**Hasil yang Diharapkan:**
- Alert/validasi “Password wajib diisi”.
- Form tidak terkirim.

---

## TC-005 — Fungsi *Remember Me* ☑️
**Deskripsi:** Memeriksa apakah centang *remember-me* mempertahankan sesi login.

**Langkah Uji:**
1. Login dengan centang checkbox *Sudah* (remember-me).
2. Tutup dan buka ulang browser.
3. Akses kembali halaman.

**Hasil yang Diharapkan:**
- Masih dalam kondisi login (tidak diminta login ulang).

---

## TC-006 — Spinner loading saat load awal
**Deskripsi:** Saat halaman dimuat, muncul spinner selama ~2,5 detik.

**Langkah Uji:**
1. Refresh atau buka halaman login.
2. Amati overlay spinner.

**Hasil yang Diharapkan:**
- Spinner overlay muncul saat load pertama (~2–3 detik).
- Spinner hilang secara otomatis setelah durasi selesai.

---

### 📌 Cara Menggunakan Template ini

| Field             | Keterangan |
|------------------|------------|
| **Test Case ID** | Gunakan format unik, misalnya `TC-001` |
| **Deskripsi**     | Ringkas tujuan dan kondisi uji |
| **Preconditions**| Kondisi awal yang harus terpenuhi |
| **Langkah Uji**   | Langkah-langkah yang terperinci |
| **Hasil yang Diharapkan** | Apa yang seharusnya terjadi |

> Setelah di-run, tambahkan kolom **Hasil Aktual** dan catat `Pass / Fail`, dengan bukti (screenshot/log).

---

🎯 **Keunggulan format ini**:
- Struktur yang konsisten dan mudah dipahami.
- Praktis untuk kolaborasi di GitHub dan mendukung otomasi (CI/CD).
- Bisa dikembangkan untuk uji fungsi tambahan seperti SQL‑injection atau session hijacking :contentReference[oaicite:1]{index=1}.

Kalau kamu ingin versi tambahan (BDD / Gherkin), atau mau di-parse otomatis, tinggal sesuaikan struktur ini. Semoga membantu dokumentasi dan proses QA-mu!
::contentReference[oaicite:2]{index=2}
