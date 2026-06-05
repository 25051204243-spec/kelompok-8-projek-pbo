# Projek game Supermarket Cashier Simulator
Pemain mengelola simulasi kasir dengan memandu pelanggan berbelanja, menuntaskan transaksi melalui kalkulator dan metode pembayaran yang bervariasi, serta menjaga efisiensi waktu agar saldo kas toko terus bertambah.
# Anggota
Dirly Rahmat Priambudi		(25051204039)
Azzarah Andina Rohmatul Izzah	(25051204041)
Naila Ni’ma Maulavia			(25051204043)
Sahira Ramadani Fitrania		(25051204243)
# Fitur Utama
1. Gameplay & Kontrol Karakter
- Pergerakan: Menggunakan tombol WASD atau Panah untuk menjelajahi area supermarket.
- Interaksi: Menekan tombol E untuk mengambil 3 jenis barang (Soda, Roti, Susu) dari rak ke dalam keranjang belanja.
- Siklus Pelanggan: Pelanggan berganti otomatis setelah transaksi selesai. Setiap pelanggan memiliki batas waktu 60 detik (Time Attack). Jika habis, mereka akan marah dan pergi.

2. Sistem Kasir & Mekanisme Checkout
- Scanner: Pemain memindahkan barang dari keranjang ke area kasir dan melakukan scan satu per satu.
- Kalkulator POS Mini: Memiliki fungsi tombol angka, Tambah (+), Total, Clear, dan PAY.
- Metode Pembayaran: * Tunai: Menghitung uang diterima dan uang kembalian secara otomatis.
- Non-Tunai: Simulasi pembayaran menggunakan kartu ATM/Debit (langsung pas tanpa kembalian).
- Struk Transaksi: Mencetak nota yang berisi nomor nota, daftar barang, total bayar, uang diterima, kembalian, dan metode pembayaran.

3. Sistem Skor, Ekonomi, & Tutorial
- Skor & Kepuasan: Melacak jumlah pelanggan yang puas vs pelanggan yang kecewa (akibat kehabisan waktu).
- Pendapatan Toko: Kas toko bertambah setelah transaksi berhasil dan total uang ditampilkan di layar.
- Tutorial: Sistem pesan bantuan memberikan petunjuk langkah demi langkah bagi pemain.

4. Audio & Antarmuka Visual
- Visual (UI): Menampilkan background supermarket, rak, keranjang, mesin kasir, uang/kartu, dan progress bar waktu pelanggan.
- Audio: Efek suara tombol kasir, efek suara pembayaran sukses, dan musik latar (backsound) yang berputar terus-menerus.

5. Implementasi Fitur OOP (Pemrograman Berorientasi Objek)
- Enkapsulasi: Menyembunyikan data sensitif menggunakan private attribute (__keranjang, __uang_toko).
- Abstraksi: Menggunakan abstract class (MetodePembayaran) sebagai cetak biru sistem pembayaran.
- Inheritance (Pewarisan): Kelas BayarTunai dan BayarNonTunai mewarisi sifat dari kelas induknya.
- Polimorfisme: Fungsi hitung_transaksi() yang memiliki cara kerja berbeda pada metode tunai dan non-tunai.
- Protected Attribute: Menggunakan _nama yang hanya boleh diakses internal atau oleh kelas turunannya.
# Cara Menjalankan Projek
1. Fase Belanja (Shopping State)
- Kontrol Karakter: Gunakan tombol W, A, S, D atau Tombol Panah pada keyboard untuk menggerakkan lingkaran karakter pelanggan menjelajahi area supermarket.
- Mengambil Barang: Dekati salah satu dari tiga rak yang tersedia (SODA, ROTI, atau SUSU). Berdirilah tepat di depan rak tersebut, lalu tekan tombol E.
- Indikator Tas: Setiap kali berhasil, teks bantuan di bawah layar akan memberi tahu barang apa yang diambil dan jumlah isi keranjangmu akan bertambah.

2. Fase Menuju Kasir (Antre)
- Memicu Area Kasir: Setelah keranjang terisi barang, gerakkan karaktermu ke arah kanan bawah menuju meja kasir kayu.
- Perubahan Status: Begitu karakter menyentuh area pemicu pembayaran (pemicu_bayar_rect), game akan otomatis mengunci pergerakan karakter dan layar akan berubah masuk ke mode kasir (Checkout Monitor). Waktu Time Attack 60 detik mulai berjalan mundur!

3. Fase Scan Barang (Checkout State)
- Memindahkan ke Meja: Di atas meja kasir, klik gambar Keranjang Belanja (Basket). Ini akan mengeluarkan barang dari keranjang satu per satu ke atas meja scanner.
- Input Kalkulator POS: Lihat harga barang yang muncul di monitor scanner. Gunakan mouse untuk mengklik tombol angka pada mesin kasir mini, lalu wajib klik tombol + untuk menginput harga tersebut ke sistem.
- Selesaikan Antrean: Ulangi proses klik keranjang dan input harga sampai semua barang di dalam keranjang habis dan monitor memunculkan teks "Semua sukses di-scan!". Setelah itu, klik tombol PAY pada kalkulator.

4. Fase Pilihan & Eksekusi Pembayaran (Payment State)
- Pilih Metode: Layar akan menggelap dan memunculkan pop-up pilihan: Klik TUNAI atau NON-TUNAI.
- Jika memilih Tunai, sistem abstrak otomatis membulatkan total tagihan ke kelipatan 5 terdekat.
- Jika memilih Non-Tunai, tagihan akan pas sesuai harga belanjaan.
- Simulasi Serah Terima Fisik: Klik tombol hijau bertuliskan "MINTA UANG / KARTU". Pelanggan akan menaruh uang/kartu di meja kasir. Kamu harus mengklik gambar fisik uang/kartu tersebut di meja sebagai tanda kasir sudah menerimanya.

5. Cetak Struk & Ganti Pelanggan (Receipt State)
- Penyerahan Kembalian (Khusus Tunai): Struk nota belanja akan tercetak di layar. Jika metode yang digunakan adalah tunai dan ada uang kembalian, kamu harus mengklik gambar uang refund di meja kasir terlebih dahulu untuk menyerahkannya ke pelanggan.
- Siklus Selesai: Terakhir, klik tombol emas di bagian bawah struk (LEPAS STRUK & NEXT CUSTOMER). Pada detik ini, uang kas toko di kiri atas akan bertambah, skor pelanggan puas akan naik, dan game otomatis memunculkan pelanggan baru dengan variasi karakter yang berbeda.
# Penjelasan implementasi OOP
1. Abstraksi (Abstraction)
Tempat di kode: class MetodePembayaran(ABC) dan @abstractmethod.

Artinya: Kelas ini berfungsi sebagai cetak biru wajib (kontrak). Kelas induk tidak peduli bagaimana cara menghitung transaksi, yang penting semua kelas pembayaran anak wajib memiliki fungsi hitung_transaksi(). Kelas ini dikunci dan tidak bisa dibuat objeknya secara langsung.

2. Pewarisan (Inheritance)
Tempat di kode: class BayarTunai(MetodePembayaran) dan class RakBarang(ObjekStatis).

Artinya: Kelas anak otomatis mewarisi sifat dan fungsi dari kelas induk menggunakan perintah super().__init__().

BayarTunai mewarisi kerangka pembayaran.

RakBarang mewarisi fungsi koordinat kotak (Rect) Pygame dari ObjekStatis agar tidak perlu menulis ulang kode posisi objek.

3. Polimorfisme (Polymorphism)
Tempat di kode: Fungsi hitung_transaksi() yang ada di dalam BayarTunai dan BayarNonTunai.

Artinya: Satu nama fungsi yang sama, tetapi memiliki perilaku dan rumus yang berbeda tergantung objek yang memanggilnya.

Jika yang aktif BayarTunai, fungsi akan menghitung rumus pembulatan kelipatan 5 dan kembalian.

Jika yang aktif BayarNonTunai, fungsi langsung mengembalikan total tagihan pas tanpa kembalian.

4. Enkapsulasi (Encapsulation)
Tempat di kode: Atribut private __keranjang (di kelas pelanggan) dan __uang_toko (di kelas game).

Artinya: Menyembunyikan data sensitif agar tidak bisa diubah sembarangan dari luar kelas. Untuk mengakses dan mengubahnya, kode wajib menggunakan fungsi perantara:

Getter: get_keranjang() dan get_uang_toko() (untuk mengambil/melihat nilai data).

Setter: set_keranjang() dan set_uang_toko() (untuk mengubah data dengan validasi aman, misalnya mencegah uang toko bernilai minus).

5. Atribut Terproteksi (Protected Attribute)
Tempat di kode: self._nama (menggunakan satu garis bawah).

Artinya: Secara aturan/konvensi Python, tanda _ memperingatkan programmer agar variabel ini tidak diakses langsung dari luar sistem utama, tetapi masih bebas diakses secara internal oleh kelas turunannya sendiri (BayarTunai dan BayarNonTunai).

