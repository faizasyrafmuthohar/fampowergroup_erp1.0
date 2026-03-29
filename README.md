Fam Power Group ERP v1.0

Deskripsi
ERP berbasis web untuk mengelola operasional bisnis PET, mencakup produksi, keuangan, dan manajemen data karyawan. Sistem ini dibuat dengan pendekatan single HTML file + React CDN sehingga mudah dijalankan tanpa setup kompleks.

---

Teknologi yang digunakan

* HTML + React (tanpa build tools)
* Supabase (database & authentication)
* Vercel (hosting)
* Recharts (grafik)
* jsPDF (export laporan)

---

Cara menjalankan

1. Upload file HTML ke Vercel
2. Pastikan Supabase sudah dibuat
3. Isi URL dan API key di bagian berikut:

window.__db_url = 'YOUR_URL';
window.__db_key = 'YOUR_KEY';

4. Buka website → login → langsung digunakan

---

Struktur database (minimal)

Tabel users:

* id (uuid)
* last_login (timestamp)

Tambahkan kolom last_login dengan SQL:
ALTER TABLE users ADD COLUMN last_login TIMESTAMP;

---

Login & last login

Sistem login menggunakan Supabase Auth.
Setiap user login, waktu terakhir login akan disimpan ke database.

Contoh implementasi:

await db.from("users").upsert({
id: user.id,
last_login: new Date().toISOString()
});

---

Fitur utama

* Dashboard (ringkasan bisnis & grafik)
* Produksi (input bahan PET & tracking)
* Keuangan (OPEX, penjualan, hutang/piutang)
* Data karyawan & absensi
* Laporan PDF
* Manajemen akun

---

Catatan

* Pastikan semua tabel di Supabase sudah sesuai
* API key jangan disebar ke publik
* Sistem belum menggunakan role/permission

---

Troubleshooting

Data tidak tersimpan:

* Cek koneksi Supabase
* Pastikan nama tabel & kolom benar

Login berhasil tapi last login tidak update:

* Pastikan kolom last_login sudah dibuat
* Gunakan upsert, bukan update

---

Catatan akhir

Project ini dirancang untuk operasional internal dengan fokus pada kemudahan deploy dan fleksibilitas pengembangan.

"We used to dream about it, now we are living the journey."
