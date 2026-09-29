# SRS ClassWallet

# 1. Sistem Apa yang Akan Dibangun

ClassWallet adalah sistem informasi berbasis web untuk mengelola tabungan siswa, pemasukan, pengeluaran, dan laporan keuangan satu kelas.

Sistem memiliki dua role:

- **Admin/Bendahara:** mengelola seluruh data dan transaksi kelas.
- **Anggota/Siswa:** melihat data tabungan dan transaksi miliknya sendiri.

# 2. Dengan Apa Sistem Dibangun

- **Backend:** PHP native.
- **Database:** MySQL.
- **Koneksi database:** PDO.
- **Frontend:** HTML, CSS, dan JavaScript.
- **Web server lokal:** Apache melalui Laragon.
- **Penyimpanan file:** folder privat untuk bukti pembayaran dan foto profil.

Kode dipisahkan menjadi bagian konfigurasi, controller, tampilan, database, dan folder publik agar mudah dikembangkan.

# 3. Rancangan Alur Sistem pada Setiap Fitur

## Autentikasi

1. Pengguna mengirim username/email dan password.
2. Sistem mencari akun aktif pada database.
3. Sistem memeriksa password yang tersimpan dalam bentuk hash.
4. Jika benar, sistem membuat sesi login.
5. Sistem memeriksa role sebelum membuka setiap halaman yang dilindungi.

## Pengelolaan Siswa

1. Admin mengisi formulir data siswa.
2. Sistem memvalidasi data.
3. Sistem menyimpan akun pada tabel `users` dan profil siswa pada tabel `students`.
4. Data ditampilkan pada daftar siswa dan halaman detail.
5. Siswa yang masih memiliki transaksi tidak dapat dihapus sebelum transaksi tersebut ditangani.

## Pembayaran Siswa

1. Admin memilih siswa dan mengisi nominal, tanggal, jenis, metode, serta catatan.
2. Sistem memvalidasi bahwa nominal pembayaran lebih dari Rp0.
3. Data disimpan pada tabel `transactions`.
4. Jika ada bukti, informasi file disimpan pada tabel `payment_proofs`.
5. Sistem menghitung ulang total pembayaran, kekurangan, status, dan saldo saat halaman dibuka.
6. Tindakan Admin dicatat dalam riwayat aktivitas.

## Pemasukan dan Pengeluaran

1. Admin mengisi formulir pemasukan atau pengeluaran.
2. Data disimpan pada tabel `income` atau `expenses`.
3. Sistem menggabungkan arus kas untuk menghitung total uang masuk, uang keluar, dan saldo.

## Akses Bukti Pembayaran

1. Pengguna meminta bukti pembayaran.
2. Sistem memeriksa sesi login.
3. Admin dapat membuka seluruh bukti; siswa hanya dapat membuka bukti miliknya.
4. Jika berhak, sistem menampilkan file dari penyimpanan privat.

## Laporan

1. Admin memilih periode laporan.
2. Sistem membaca transaksi, pemasukan, dan pengeluaran sesuai periode.
3. Sistem menghitung ringkasan keuangan dan rekap siswa.
4. Hasil ditampilkan pada halaman laporan atau diekspor ke PDF dan Excel.

# 4. Alur Data

Data utama disimpan dalam tabel berikut:

| Tabel | Fungsi |
|---|---|
| `users` | Menyimpan akun, password hash, dan role. |
| `students` | Menyimpan NIS, kelas, nomor absen, dan target pembayaran. |
| `transactions` | Menyimpan pembayaran siswa. |
| `income` | Menyimpan pemasukan selain pembayaran siswa. |
| `expenses` | Menyimpan pengeluaran kelas. |
| `payment_proofs` | Menyimpan informasi bukti transaksi. |
| `settings` | Menyimpan pengaturan aplikasi dan kelas. |
| `activity_logs` | Menyimpan riwayat tindakan penting. |

Alur data pembayaran:

1. Admin mengisi formulir pembayaran.
2. Pembayaran disimpan di `transactions`.
3. Sistem mengambil seluruh pembayaran siswa untuk menghitung total dan status.
4. Hasil perhitungan ditampilkan pada dashboard, detail siswa, riwayat, dan laporan.

# 5. Input dan Output Sistem

| Proses | Input | Output |
|---|---|---|
| Login | Username/email dan password | Sesi login atau pesan kesalahan. |
| Data siswa | Nama, NIS, kelas, absen, akun, target | Profil dan daftar siswa. |
| Pembayaran | Siswa, nominal, tanggal, jenis, metode, catatan, bukti | Riwayat pembayaran dan status terbaru. |
| Pemasukan | Nama, kategori, nominal, tanggal, catatan | Total pemasukan dan saldo terbaru. |
| Pengeluaran | Nama, kategori, nominal, tanggal, keperluan | Total pengeluaran dan saldo terbaru. |
| Laporan | Periode laporan | Rekap keuangan, PDF, Excel, atau tampilan cetak. |

# 6. Aturan Perhitungan

- **Total pembayaran siswa** = jumlah seluruh transaksi pembayaran siswa.
- **Kekurangan** = target pembayaran − total pembayaran. Jika hasilnya negatif, kekurangan ditampilkan Rp0.
- **Status LUNAS** = total pembayaran siswa sama dengan atau lebih besar daripada target.
- **Status BELUM LUNAS** = total pembayaran siswa masih di bawah target.
- **Total pemasukan kelas** = pembayaran siswa + pemasukan tambahan.
- **Saldo kelas** = total pemasukan kelas − total pengeluaran kelas.

Contoh: target siswa Rp20.000 dan total pembayaran Rp10.000 menghasilkan status BELUM LUNAS dengan kekurangan Rp10.000.

# 7. Persyaratan Keamanan dan Tampilan

- Password disimpan dalam bentuk hash.
- Setiap halaman dan proses Admin memeriksa role pada server.
- Siswa hanya dapat mengakses data miliknya.
- Form perubahan data memakai perlindungan CSRF.
- Input divalidasi sebelum disimpan.
- Bukti pembayaran hanya menerima JPG, JPEG, PNG, atau PDF dengan batas 5 MB.
- Tampilan menggunakan bahasa Indonesia, format Rupiah, dan responsif pada komputer maupun ponsel.

# 8. Batas Sistem Saat Ini

ClassWallet belum memproses pembayaran melalui bank atau payment gateway. Status LUNAS menunjukkan bahwa nominal target sudah tercapai, bukan bahwa transfer telah diverifikasi otomatis. Sistem saat ini digunakan untuk satu kelas dan belum menyimpan kolom NISN.