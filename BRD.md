BRD — ClassWallet
Business Requirements Document
Kelas: XI RPL, SMK Negeri 6 Jakarta · Tahun ajaran 2026/2027
1. Latar belakang masalah
Bendahara kelas perlu mencatat tabungan atau iuran setiap siswa, pemasukan lain, dan pengeluaran. Kelas beranggotakan 36 siswa dengan target awal Rp20.000 per siswa, sehingga target keseluruhan Rp720.000. Ketika pembayaran dicatat terpisah dalam buku, chat, atau spreadsheet, bendahara harus menghitung total, kekurangan, status lunas, dan saldo secara manual. Bukti pembayaran juga dapat terpisah dari catatan transaksi. Siswa perlu cara untuk memeriksa pembayaran miliknya tanpa meminta rekap satu per satu.


2. Alur yang ada saat ini
Alur manual yang menjadi dasar kebutuhan aplikasi:
1. Siswa menyerahkan uang atau mengirim bukti pembayaran kepada bendahara.
2. Bendahara mencatat nama, tanggal, dan nominal pada catatan kelas.
3. Bendahara menjumlah pembayaran tiap siswa, lalu membandingkannya dengan target.
4. Pemasukan tambahan dan pengeluaran dicatat, kemudian saldo kelas dihitung ulang.
5. Untuk membuat laporan, bendahara menyalin dan mengecek ulang angka dari catatan tersebut.
6. Siswa bertanya kepada bendahara jika ingin mengetahui sisa tagihan atau riwayatnya.
Alur ini merupakan gambaran proses yang hendak diperbaiki; cara pencatatan sebelum aplikasi digunakan dapat berbeda di kelas.



3. Alur yang diinginkan
1. Admin/Bendahara masuk ke ClassWallet dan mengelola akun siswa serta target pembayaran.
2. Saat menerima pembayaran, Admin memilih siswa, mengisi nominal, waktu, jenis, metode, catatan, dan bukti jika tersedia.
3. Sistem menyimpan transaksi dan menghitung ulang jumlah dibayar, kekurangan, status LUNAS/BELUM LUNAS, pemasukan, serta saldo.
4. Admin mencatat pemasukan tambahan dan pengeluaran di menu masing-masing.
5. Admin memantau dashboard, menelusuri riwayat, dan membuat laporan sesuai periode.
6. Anggota/Siswa masuk untuk melihat tabungan, target, progres, transaksi, dan bukti miliknya sendiri.

4. Tujuan bisnis
Tujuan	Ukuran keberhasilan
Catatan keuangan tertib	Setiap transaksi memiliki nominal, tanggal, kategori/metode, pencatat, serta bukti jika diunggah.
Perhitungan konsisten	Saldo sama dengan seluruh pemasukan dikurangi seluruh pengeluaran yang tercatat.
Status pembayaran jelas	LUNAS jika total pembayaran siswa mencapai target; jika belum, sistem menunjukkan kekurangannya.
Transparansi yang sesuai peran	Admin melihat data kelas; siswa hanya melihat data pribadinya.
Laporan mudah dibuat	Admin dapat memilih periode dan mengekspor PDF/Excel atau mencetak laporan.


5. Pemangku kepentingan
- Bendahara/Admin: memasukkan dan mengoreksi data, memantau saldo, membuat laporan, dan bertanggung jawab atas ketepatan catatan.
- Siswa/Anggota: memeriksa pembayaran sendiri serta bukti yang berkaitan dengan akunnya.
- Kelas: memperoleh rekap tabungan dan penggunaan uang kelas yang dapat ditelusuri.

6. Aturan dan batasan bisnis
- Total pembayaran siswa adalah jumlah transaksi pembayaran siswa tersebut. Kekurangan tidak boleh bernilai negatif.
- Status LUNAS dihitung dari pembayaran >= target, bukan diisi manual.
- Pemasukan kelas mencakup pembayaran siswa dan pemasukan lain. Pengeluaran mengurangi saldo kelas, tetapi tidak mengurangi catatan pembayaran siswa.
- Hanya Admin boleh menambah, mengedit, atau menghapus catatan keuangan.
- Bukti pembayaran opsional; status LUNAS berarti target nominal tercapai, bukan verifikasi otomatis dari bank.
- Aplikasi saat ini dipakai untuk satu kelas. Belum tersedia pembayaran online, verifikasi transfer otomatis, serta kolom NISN.

7. Kriteria penerimaan bisnis
1. Siswa bertarget Rp20.000 yang membayar Rp10.000 tampil BELUM LUNAS dengan kekurangan Rp10.000.
2. Setelah membayar Rp10.000 lagi, siswa tampil LUNAS dengan kekurangan Rp0.
3. Pengeluaran Rp5.000 mengurangi saldo Rp5.000 tanpa mengubah pembayaran siswa.
4. Siswa tidak dapat membuka data siswa lain atau halaman Admin dengan mengetik URL.
5. Angka dashboard, riwayat, dan laporan bersumber dari transaksi yang tersimpan.