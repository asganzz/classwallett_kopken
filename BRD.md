# BRD ClassWallet

# 1. Latar Belakang Masalah

ClassWallet awalnya digunakan untuk satu kelas. Sekarang sistem dikembangkan menjadi **skala sekolah** agar setiap kelas memiliki pencatatan keuangan sendiri tetapi tetap bisa dipantau oleh Admin Sekolah.

Sistem menggunakan **Next.js** sebagai frontend dan **Supabase** sebagai database, autentikasi, serta penyimpanan file.

# 2. Alur yang Diinginkan

1. Admin Sekolah login ke ClassWallet.
2. Admin membuat akun Bendahara untuk setiap kelas.
3. Bendahara login dan hanya mengelola data kelasnya sendiri.
4. Bendahara mencatat pembayaran siswa, pemasukan, pengeluaran, dan bukti pembayaran.
5. Sistem menghitung saldo, kekurangan, serta status LUNAS/BELUM LUNAS otomatis.
6. Siswa dapat melihat pembayaran miliknya sendiri.
7. Admin Sekolah dapat melihat laporan dari seluruh kelas.

# 3. Pengguna Sistem

# Admin Sekolah

Admin dapat:

- Mengelola seluruh kelas.
- Membuat akun Bendahara.
- Melihat seluruh siswa dan transaksi.
- Melihat laporan setiap kelas.
- Melihat laporan seluruh sekolah.

# Bendahara Kelas

Bendahara dapat:

- Mengelola siswa kelasnya.
- Mencatat pembayaran.
- Mengelola pemasukan dan pengeluaran.
- Mengunggah bukti.
- Membuat laporan kelas.

Bendahara hanya dapat mengakses kelas yang diberikan kepadanya.

# Siswa

Siswa hanya dapat melihat:

- Total pembayaran.
- Target.
- Kekurangan.
- Status pembayaran.
- Riwayat dan bukti miliknya sendiri.

# 4. Struktur Kelas

ClassWallet digunakan untuk kelas X, XI, dan XII.

Setiap tingkat memiliki kelas:

- MPLB
- AKL 1
- AKL 2
- BR 1
- BR 2
- RPL
- DKV 1
- DKV 2
- Animasi

Total terdapat **27 kelas**.

# 5. Pemisahan Data Kelas

Data setiap kelas dipisahkan menggunakan `class_id`.

Contoh:

- Bendahara XI RPL hanya dapat melihat XI RPL.
- Bendahara XI DKV 1 hanya dapat melihat XI DKV 1.
- Admin Sekolah dapat melihat seluruh kelas.

Supabase Row Level Security digunakan untuk mengatur keamanan akses data.

# 6. Tujuan Bisnis

- Mempermudah pengelolaan keuangan seluruh kelas.
- Mengurangi kesalahan pencatatan.
- Memisahkan data antar kelas.
- Mempermudah Bendahara membuat laporan.
- Mempermudah Admin memantau kondisi keuangan seluruh kelas.

# 7. Aturan Bisnis

- Setiap Bendahara hanya mengelola satu kelas yang diberikan.
- Siswa hanya dapat melihat datanya sendiri.
- Pembayaran siswa dihitung sebagai pemasukan kelas.
- Status LUNAS jika pembayaran mencapai target.
- Saldo dihitung dari pemasukan dikurangi pengeluaran.
- Admin Sekolah dapat melihat seluruh laporan.

# 8. Hasil yang Diharapkan

ClassWallet menjadi sistem keuangan kelas terpusat untuk sekolah.

Setiap kelas memiliki data masing-masing, Bendahara dapat mengelola keuangan kelasnya, dan Admin Sekolah dapat memantau laporan seluruh kelas melalui satu aplikasi.