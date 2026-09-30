# SRS ClassWallet

# 1. Sistem yang Akan Dibangun

ClassWallet adalah sistem web untuk mengelola tabungan siswa dan keuangan seluruh kelas di sekolah.

Sistem memiliki tiga role:

- `super_admin`
- `treasurer`
- `student`

# 2. Teknologi Sistem

- **Frontend:** Next.js, React, TypeScript.
- **Database:** Supabase PostgreSQL.
- **Authentication:** Supabase Auth.
- **Storage:** Supabase Storage.
- **Security:** Row Level Security.

# 3. Struktur Akses

# Super Admin

Dapat mengakses:

- Seluruh kelas.
- Seluruh siswa.
- Bendahara.
- Transaksi.
- Pemasukan.
- Pengeluaran.
- Laporan.

# Bendahara

Hanya dapat mengakses data kelasnya sendiri.

# Siswa

Hanya dapat melihat pembayaran dan data miliknya sendiri.

# 4. Struktur Data

Tabel utama:

| Tabel | Fungsi |
|---|---|
| `profiles` | Menyimpan akun dan role. |
| `majors` | Menyimpan jurusan. |
| `classes` | Menyimpan data kelas. |
| `students` | Menyimpan siswa. |
| `transactions` | Menyimpan pembayaran siswa. |
| `income` | Menyimpan pemasukan tambahan. |
| `expenses` | Menyimpan pengeluaran. |
| `payment_proofs` | Menyimpan bukti pembayaran. |
| `activity_logs` | Menyimpan aktivitas pengguna. |

# 5. Pemisahan Data Kelas

Setiap data transaksi memiliki `class_id`.

Contoh:

```text
XI RPL → class_id XI RPL
XI DKV 1 → class_id XI DKV 1
```

Bendahara hanya dapat membaca data dengan `class_id` miliknya.

Admin dapat membaca seluruh `class_id`.

# 6. Autentikasi

1. Pengguna login menggunakan email dan password.
2. Supabase Auth memeriksa akun.
3. Sistem membaca role.
4. Admin diarahkan ke dashboard Admin.
5. Bendahara diarahkan ke dashboard kelas.
6. Siswa diarahkan ke dashboard siswa.

# 7. Pembayaran Siswa

1. Bendahara memilih siswa.
2. Mengisi nominal, tanggal, metode, dan catatan.
3. Bukti pembayaran dapat diunggah.
4. Data disimpan ke `transactions`.
5. Sistem menghitung total pembayaran dan status secara otomatis.

# 8. Perhitungan

- **Total pembayaran** = seluruh transaksi pembayaran siswa.
- **Kekurangan** = target − total pembayaran.
- **LUNAS** = total pembayaran ≥ target.
- **BELUM LUNAS** = total pembayaran < target.
- **Total pemasukan** = pembayaran siswa + pemasukan tambahan.
- **Saldo** = pemasukan − pengeluaran.

# 9. Laporan

Admin dapat melihat laporan:

- Per kelas.
- Per jurusan.
- Per tingkat.
- Seluruh sekolah.

Bendahara hanya dapat melihat laporan kelasnya.

# 10. Supabase Storage

Digunakan untuk menyimpan:

- Bukti pembayaran.
- Foto profil.

Format file:

- JPG
- JPEG
- PNG
- PDF

Maksimal **5 MB**.

# 11. Keamanan

- Password dikelola oleh Supabase Auth.
- Row Level Security wajib aktif.
- Bendahara tidak dapat membuka kelas lain.
- Siswa tidak dapat membuka data siswa lain.
- Data input harus divalidasi.
- Aktivitas penting dicatat dalam audit log.

# 12. Struktur Routing

```text
/login

/admin
/admin/kelas
/admin/jurusan
/admin/bendahara
/admin/laporan

/bendahara
/bendahara/siswa
/bendahara/tabungan
/bendahara/pemasukan
/bendahara/pengeluaran
/bendahara/laporan

/siswa
/siswa/tabungan
/siswa/riwayat
/siswa/profile
```

# 13. Hasil Akhir Sistem

ClassWallet menggunakan **Next.js dan Supabase** untuk mengelola keuangan **27 kelas**.

Data setiap kelas dipisahkan, Bendahara hanya mengelola kelasnya, siswa hanya melihat datanya sendiri, dan Admin Sekolah dapat melihat laporan seluruh kelas.