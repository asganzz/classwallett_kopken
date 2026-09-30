# PRD ClassWallet

# 1. Apa yang Akan Dibangun

ClassWallet adalah aplikasi web untuk mengelola tabungan siswa dan keuangan kelas dalam **skala sekolah**.

Sistem memiliki tiga pengguna:

- Admin Sekolah
- Bendahara Kelas
- Siswa

Admin dapat mengelola seluruh kelas, Bendahara mengelola kelasnya sendiri, dan siswa hanya melihat data pembayaran miliknya.

# 2. Teknologi yang Digunakan

- **Frontend:** Next.js, React, TypeScript.
- **UI:** Tailwind CSS dan komponen modern.
- **Database:** Supabase PostgreSQL.
- **Authentication:** Supabase Auth.
- **Storage:** Supabase Storage.
- **Security:** Supabase Row Level Security.

# 3. Dashboard Admin

Dashboard Admin menampilkan:

- Jumlah kelas.
- Jumlah siswa.
- Total pemasukan.
- Total pengeluaran.
- Total saldo.
- Jumlah siswa LUNAS dan BELUM LUNAS.
- Ringkasan setiap kelas.

Admin dapat memfilter berdasarkan kelas, jurusan, tingkat, dan periode.

# 4. Manajemen Kelas dan Bendahara

Admin dapat membuat dan mengelola:

- Kelas.
- Jurusan.
- Tahun ajaran.
- Akun Bendahara.

Setiap akun Bendahara dihubungkan dengan kelas tertentu.

# 5. Data Siswa

Bendahara dapat:

- Menambah siswa.
- Mengedit siswa.
- Mencari siswa.
- Memfilter data.
- Melihat detail pembayaran.

Data siswa meliputi nama, NIS, kelas, nomor absen, target, dan akun.

# 6. Tabungan dan Transaksi

Bendahara mencatat:

- Nama siswa.
- Nominal.
- Tanggal.
- Metode.
- Catatan.
- Bukti pembayaran.

Sistem otomatis menghitung:

- Total pembayaran.
- Kekurangan.
- Status LUNAS/BELUM LUNAS.
- Saldo kelas.

# 7. Pemasukan dan Pengeluaran

Bendahara dapat mencatat pemasukan tambahan dan pengeluaran kelas.

Setiap transaksi otomatis memengaruhi saldo kelas.

# 8. Laporan

Admin dan Bendahara dapat melihat laporan.

Laporan dapat difilter berdasarkan:

- Tanggal.
- Kelas.
- Jurusan.
- Tingkat.
- Tahun ajaran.

Laporan dapat dicetak atau diekspor ke PDF dan Excel.

# 9. Halaman Jurusan dan Kelas

Admin memiliki halaman untuk setiap jurusan dan kelas.

Contoh:

`/admin/jurusan/rpl`

`/admin/kelas/xi-rpl`

Halaman menampilkan data siswa, pemasukan, pengeluaran, saldo, dan laporan kelas.

# 10. Tampilan Sistem

ClassWallet harus memiliki:

- Responsive mobile dan desktop.
- Dark mode.
- Search.
- Filter.
- Sorting.
- Pagination.
- Notification/toast.
- Audit log.

# 11. Hasil yang Diharapkan

ClassWallet dapat digunakan untuk mengelola keuangan **27 kelas** dalam satu sistem.

Setiap Bendahara mempunyai dashboard kelas sendiri, sedangkan Admin Sekolah dapat melihat laporan seluruh kelas.