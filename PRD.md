# PRD ClassWallet

# 1. Apa yang Akan Dibangun

ClassWallet adalah aplikasi web untuk mencatat tabungan siswa dan keuangan kelas XI RPL. Aplikasi memiliki dua jenis pengguna, yaitu Admin/Bendahara dan Anggota/Siswa.

Admin dapat mengelola siswa, mencatat pembayaran, pemasukan, pengeluaran, bukti pembayaran, dan membuat laporan. Siswa dapat melihat tabungan, status pembayaran, riwayat transaksi, serta bukti miliknya sendiri.

# 2. Apa yang Dibutuhkan untuk Membangun

- PHP untuk menjalankan proses aplikasi.
- MySQL untuk menyimpan akun, siswa, transaksi, dan data keuangan.
- Apache dan Laragon untuk menjalankan aplikasi secara lokal.
- HTML, CSS, dan JavaScript untuk membuat antarmuka yang responsif.
- Penyimpanan file untuk foto profil dan bukti pembayaran.
- Browser pada komputer atau ponsel untuk mengakses aplikasi.

# 3. Siapa yang Menggunakan Sistem

## Admin/Bendahara

Admin bertanggung jawab mengelola seluruh data kelas. Admin dapat menambah dan mengedit siswa, mencatat pembayaran, mengelola pemasukan dan pengeluaran, melihat bukti, serta membuat laporan.

## Anggota/Siswa

Siswa dapat masuk ke akun masing-masing untuk melihat jumlah yang sudah dibayar, target, kekurangan, status pembayaran, riwayat transaksi, dan bukti miliknya. Siswa tidak dapat mengubah nominal atau melihat data pribadi siswa lain.

# 4. Fitur yang Akan Dibangun

## Login dan Logout

Pengguna masuk menggunakan username atau email dan password. Setelah login, sistem menampilkan dashboard sesuai role pengguna. Logout mengakhiri sesi login.

## Dashboard Admin

Menampilkan saldo kelas, total pemasukan, total pengeluaran, target pembayaran, jumlah siswa lunas dan belum lunas, grafik keuangan, serta transaksi terbaru.

## Data Siswa

Admin dapat menambah, mengedit, mencari, mengurutkan, memfilter, dan melihat detail siswa. Data siswa mencakup identitas, NIS, kelas, nomor absen, target pembayaran, dan akun login.

## Tabungan Siswa

Admin mencatat pembayaran berdasarkan siswa, nominal, tanggal, jenis pembayaran, metode, catatan, dan bukti. Sistem menghitung total pembayaran, kekurangan, serta status secara otomatis.

## Pemasukan dan Pengeluaran

Admin mencatat pemasukan selain pembayaran siswa dan seluruh pengeluaran kelas. Setiap catatan memengaruhi saldo kelas.

## Bukti Pembayaran

Admin dapat mengunggah bukti berupa JPG, JPEG, PNG, atau PDF. Siswa hanya dapat melihat bukti yang berkaitan dengan transaksinya sendiri.

## Dashboard Anggota

Menampilkan jumlah tabungan siswa, target, persentase progres, kekurangan, status, dan riwayat pembayaran miliknya.

## Riwayat dan Laporan

Admin dapat mencari serta memfilter transaksi. Laporan keuangan dapat dipilih berdasarkan periode, dicetak, dan diekspor ke PDF atau Excel.

## Profil dan Pengaturan

Pengguna dapat melihat profilnya. Admin mengatur nama aplikasi, kelas, tahun ajaran, target default, nama bendahara, tema, dan pengaturan pendaftaran.

# 5. Alur Setiap Fitur

## Alur Login

1. Pengguna membuka halaman login.
2. Pengguna memasukkan username/email dan password.
3. Sistem memeriksa akun dan password.
4. Admin diarahkan ke Dashboard Admin, sedangkan siswa diarahkan ke Dashboard Anggota.

## Alur Pembayaran

1. Admin membuka menu Tabungan.
2. Admin memilih siswa dan mengisi data pembayaran.
3. Admin mengunggah bukti jika tersedia.
4. Sistem menyimpan transaksi.
5. Total pembayaran, kekurangan, status siswa, pemasukan, dan saldo dihitung ulang.

## Alur Pengeluaran

1. Admin membuka menu Pengeluaran.
2. Admin mengisi nama, kategori, nominal, tanggal, keperluan, dan catatan.
3. Sistem menyimpan pengeluaran.
4. Saldo kelas berkurang sesuai nominal pengeluaran.

## Alur Siswa Melihat Tabungan

1. Siswa login ke akun miliknya.
2. Sistem menampilkan tabungan, target, kekurangan, dan status.
3. Siswa dapat membuka riwayat serta bukti pembayarannya sendiri.

## Alur Laporan

1. Admin membuka menu Laporan.
2. Admin memilih periode.
3. Sistem menghitung data keuangan sesuai periode.
4. Admin melihat, mencetak, atau mengunduh laporan.

# 6. Hasil yang Diharapkan

ClassWallet memudahkan bendahara mengelola keuangan kelas dan membantu siswa memantau pembayaran secara mandiri. Semua angka ditampilkan dalam Rupiah dan dihitung dari data transaksi yang tersimpan.