Requirements:
1. composer [download](https://getcomposer.org/download/)
2. npm [download](https://nodejs.org/en/download)
3. PHP versi 8.1 atau lebih tinggi (lewat [XAMPP](https://www.apachefriends.org/download.html), lewat [Laragon](https://laragon.org/download/)). 
- Apabila anda sudah install php lewat XAMPP tetapi versi lama ikuti petunjuk berikut di [link ini](https://dev.to/alfianandinugraha/cara-mudah-upgrade-php7-ke-php8-di-xampp-4h4h) untuk update php ke versi baru. 
- Apabila anda sudah install php lewat laragon tetapi versi lama ikuti petunjuk berikut di [link ini](https://laragon.org/docs/quick-add.html) untuk update php ke versi baru.

Instalasi:
1)	Unduh atau clone repositori ini.

2)	Apabila anda unduh melalui website github maka ekstrak file yang telah diunduh

3)	Buka cmd atau terminal dan pindah lokasi ke folder aplikasi

4)	Di cmd atau terminal anda ketik `composer install` dan tekan enter. Tunggu sampai proses selesai.

5)	Di cmd atau terminal anda ketik `npm install` dan tekan enter. Tunggu sampai proses selesai.
 
6)	Di dalam folder aplikasi cari file bernama `.env.example`,  salin dan tempel file tersebut dan ubah nama file salinan menjadi `.env`
 
7)	Buka file `.env` dan atur pengaturan database sesuai dengan database yang anda punya
 
8)	Di cmd atau terminal anda ketik `php artisan key:generated` dan tekan enter. Tunggu sampai proses selesai.
 
9)	Di cmd atau terminal anda ketik `php artisan migrate` dan tekan enter. Tunggu sampai proses selesai.
 
- Apabila terjadi kegagalan, buka file dengan nama `php.ini` yang ada di folder php (apabila melalui XAMPP, ada di dalam folder XAMPP atau di dalam folder laragon/bin/php jika melalui laragon) dan temukan kalimat extension untuk database anda seperti ini `;extension=pdo_mysql` dan hapus titik koma diawalan kalimat menjadi `extension=pdo_mysql` (contoh database mysql).

10)	Apabila nama database yang ada di file `.env` tidak ada maka akan mucul tampilan pemberitahuan `database ‘[nama database]’ does not exist on the ‘[database]’ connection`. Ketik `yes` dan tekan enter. Tunggu sampai proses selesai.
 
11)	Ketik `npm run dev` dan tekan enter.
 
12)	Buka cmd atau terminal baru dan pindah lokasi ke folder aplikasi.

13)	Ketik `php artisan serve` di cmd atau terminal yang baru dibuka. Tunggu sampai proses berjalan seperti pada gambar di bawah ini.
 
14)	Buka browser pilihan anda dan buka halaman http://localhost:8000 atau http://127.0.0.1:8000
