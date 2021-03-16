# Komunikasi Data dan Jaringan Kelompok 6
Hasil project UTS mata kuliah Komunikasi Data dan Jaringan

![PASTE](https://github.com/akamamara/komdat-p1-kel6/blob/main/images/logo.png)


[Sekilas Tentang](#sekilas-tentang) | [Instalasi](#instalasi) | [Konfigurasi](#konfigurasi) | [Cara Pemakaian](#cara-pemakaian) | [Pembahasan](#pembahasan) | [Referensi](#referensi)

## Sekilas Tentang
[`^gulir ke atas^`](#)

Paste adalah suatu aplikasi berbasis web yang memungkinkan para usernya untuk bisa berbagi kode program, teks biasa (plain text) ataupun hal lain yang berwujud teks. Paste dibangun menggunakan bahasa PHP. Paste ini merupakan salinan versi asli dari pastebin.com sebelum akhirnya dijual pada tahun 2010.

## Instalasi
[`^gulir ke atas^`](#)

### Kebutuhan Sistem
* Apache 2.X / Nginx
* PHP 5.3.7 (or later) with php-openssl & GD enabled [PHP7.+ recommended]
* MySQL 5.x+
### Proses Instalasi
1. Login ke dalam server menggunakan SSH. Disini kami menggunakan aplikasi mobaxterm.
```
$ ssh -p 2222 student@127.0.0.1
```
2. Install seluruh kebutuhan sistem yang diperlukan
```
$ sudo add-apt-repository ppa:ondrej/php
$ sudo apt-get update
$ sudo apt install nginx
$ sudo apt install mysql-server
$ sudo apt install php7.3 php7.3-fpm php7.3-mysql
```
3. Konfigurasi awal database
```
$ sudo mysql_secure_installation
```
4. Buat user serta database baru untuk Paste
```
$ sudo mysql
GRANT ALL PRIVILEGES ON *.* TO 'akamamara'@'localhost' IDENTIFIED BY '213465@#Qw';
CREATE DATABASE paste;
```
5. Unduh folder pada github paste dan pindahkan ke dalam direktori kita. Setelah itu unzip folder yang sudah di unduh tadi 
```
$ unzip “paste 2.2.zip”
```
6. Ubah nama folder yang telah di unzip menjadi `paste2.2`
```
$ mv jordansamuel-PASTE-217ac17 paste2.2 
```
7. Copy direktori “paste2.2” ke root web
```
$ sudo cp -R paste2.2 /var/www/
```
8. Ubah otorisasi kepemilikan ke user www-data
```
$ sudo chown -R www-data:www-data html
```
9. Ubah nama folder `paste2.2` menjadi html
```
$ sudo mv paste2.2 html
```
10. Ubah agar user dan group www-data dapat melakukan read dan execute
```
$ sudo chmod 755 *
```
11. Konfigurasi nginx
```
$ sudo apt update
$ sudo apt install php-fpm
```
12. Masuk ke dalam /etc/nginx/sites-available/default 
```
$ sudo nano /etc/nginx/sites-available/default
```
13. Modifikasi beberapa konfigurasi dalam `/etc/nginx/sites-available/default`
```
...
server {
    listen 80 default_server;
    listen [::]:80 default_server;
...
```
```
index index.php index.html index.htm index.nginx-debian.html;
```
```
location ~ \.php$ {
    include snippets/fastcgi-php.conf;
    fastcgi_pass unix:/run/php/php7.3-fpm.sock;
}
location ~ /\.ht {
    deny all;
}
```
14. Lakukan restart untuk service NGINX 
```
$ sudo systemctl restart nginx.service
```
15. Kunjungi alamat IP web server kita untuk meneruskan instalasi.
```
localhost:8000/install/
```
16. Isi data yang diperlukan untuk database information
![Instalasi - 16](https://github.com/akamamara/komdat-p1-kel6/blob/main/images/FireShot%20Capture%20005%20-%20Paste%202.0%20-%20Install%20-%20localhost.png)

17. Setelah install nanti akan keluar tampilan untuk masuk ke akun admin
![Instalasi - 17](https://github.com/akamamara/komdat-p1-kel6/blob/main/images/FireShot%20Capture%20011%20-%20Paste%202.0%20-%20Install%20-%20localhost.png)

18. Selesai submit akun admin nanti akan keluar tampilan seperti gambar dibawah dan kita sudah bisa masuk ke dashboard
![Instalasi - 18](https://github.com/akamamara/komdat-p1-kel6/blob/main/images/FireShot%20Capture%20014%20-%20Paste%202.0%20-%20Install%20-%20localhost.png)

19. Setelah proses instalasi selesai hapus atau ganti nama direktori install agar saat mengakses web kita tidak diarahkan ke direktori tersebut
```
$ sudo mv install install_bak
```
## Konfigurasi
[`^gulir ke atas^`](#)

Konfigurasi aplikasi, seluruhnya berada di dalam menu Configuration. Terdapat banyak hal yang bisa diatur di sini: site info, permissions, captcha settings dan mail settings.

### Site Info
Di bagian Site info, ada banyak hal yang berkaitan dengan informasi situs yang bisa diatur.
![Configuration - Site info](https://github.com/akamamara/komdat-p1-kel6/blob/main/images/FireShot%20Capture%20051%20-%20Paste%20-%20Configuration%20-%20localhost.png)
### Permissions
Di bagian Permissions, Berkaitan dengan perizinan penggunaan situs, apakah user harus punya akun dulu atau tidak sebelum bisa menggunakan Paste bisa diatur di sini.
![Configuration - Permissions](https://github.com/akamamara/komdat-p1-kel6/blob/main/images/FireShot%20Capture%20054%20-%20Paste%20-%20Configuration%20-%20localhost.png)
### Captcha
Di bagian Captcha, jika ingin menambahkan keamanan pada saat login, Captcha beserta pengaturannya bisa diaktifkan di bagian ini.
![Configuration - Captcha](https://github.com/akamamara/komdat-p1-kel6/blob/main/images/FireShot%20Capture%20057%20-%20Paste%20-%20Configuration%20-%20localhost.png)
### Mail Settings
Terakhir di menu Configuration, Mail Settings, hal-hal yang berkaitan dengan administrasi email user bisa diatur di sini.
![Configuration - Mail Settings](https://github.com/akamamara/komdat-p1-kel6/blob/main/images/FireShot%20Capture%20060%20-%20Paste%20-%20Configuration%20-%20paste.thareeq.id.png)


## Maintenance
[`^gulir ke atas^`](#)

Perawatan sistem dapat dilakukan dengan sangat mudah. Seluruh menu telah tersedia di dalam satu laman. Hal-hal yang bisa dilakukan diantaranya: Interface, Pastes, Users, IP Bans, Statistics, Ads, Pages, Sitemap, Task
### Interface
Digunakan untuk mengatur bahasa dan tema yang digunakan pada situs.
![Configuration - Interface](https://github.com/akamamara/komdat-p1-kel6/blob/main/images/FireShot%20Capture%20106%20-%20Paste%20-%20Interface%20-%20paste.thareeq.id.png)
### Pastes
Digunakan untuk melihat informasi tentang Pastes yang dibuat oleh para user.
![Configuration - Pastes](https://github.com/akamamara/komdat-p1-kel6/blob/main/images/FireShot%20Capture%20063%20-%20Paste%20-%20Pastes%20-%20paste.thareeq.id.png)
### Users
Digunakan untuk melihat data administrasi user.
![Configuration - Users](https://github.com/akamamara/komdat-p1-kel6/blob/main/images/FireShot%20Capture%20066%20-%20Paste%20-%20Users%20-%20paste.thareeq.id.png)
### IP Bans
Digunakan untuk menolak user menggunakan alamat IP yang digunakan.
![Configuration - IP Bans](https://github.com/akamamara/komdat-p1-kel6/blob/main/images/Web%20capture_16-3-2021_172152_paste.thareeq.id.jpeg)
### Statistics
Digunakan untuk memantau aktivitas yang terjadi di dalam situs
![Configuration - Statistics](https://github.com/akamamara/komdat-p1-kel6/blob/main/images/FireShot%20Capture%20069%20-%20Paste%20-%20Statistics%20-%20paste.thareeq.id.png)
### Ads
Digunakan untuk memasang iklan di dalam situs.
![Configuration - Ads](https://github.com/akamamara/komdat-p1-kel6/blob/main/images/FireShot%20Capture%20075%20-%20Paste%20-%20Ads%20-%20paste.thareeq.id.png)
### Pages
Digunakan sebagai catatan admin untuk membantu mendokumentasikan perubahan-perubahan yang dilakukan pada situs.
![Configuration - Pages](https://github.com/akamamara/komdat-p1-kel6/blob/main/images/FireShot%20Capture%20078%20-%20Paste%20-%20Pages%20-%20paste.thareeq.id.png)
### Sitemap
Digunakan untuk mengatur berapa kali update sitemap dalam kurun waktu tertentu dilakukan.
![Configuration - Sitemap](https://github.com/akamamara/komdat-p1-kel6/blob/main/images/FireShot%20Capture%20081%20-%20Paste%20-%20Sitemap%20-%20localhost.png)
### Task
Maintenance lain di atas hanya digunakan untuk pengamatan saja, sedangkan di bagian ini aksi-aksi yang bisa dilakukan oleh admin dikumpulkan.
![Configuration - Task](https://github.com/akamamara/komdat-p1-kel6/blob/main/images/FireShot%20Capture%20084%20-%20Paste%20-%20Tasks%20-%20localhost.png)

## Cara Pemakaian
[`^gulir ke atas^`](#)

Jika ingin mencobanya langsung bisa klik [di sini](https://paste.thareeq.id/). 
### Landing Page
Saat dibuka, Anda akan langsung diarahkan ke landing page. 
![User - Landing Page](https://github.com/akamamara/komdat-p1-kel6/blob/main/images/screencapture-paste-thareeq-id-A.png)
### Register
Jika sudah memiliki akun, anda bisa langsung login. Jika belum punya akun, maka anda harus register terlebih dahulu.
![User - Register](https://github.com/akamamara/komdat-p1-kel6/blob/main/images/screencapture-paste-thareeq-id-E.png)
### Login
Setelah akun selesai dibuat, silahkan login dengan memasukkan username dan password yang benar. Jika lupa password Anda bisa klik "Forgot Password?".
![User - Login](https://github.com/akamamara/komdat-p1-kel6/blob/main/images/screencapture-paste-thareeq-id-B.png)
### Halaman Utama
Setelah login, Anda akan langsung diarahkan ke halaman utamanya. Di sini Anda bisa langsung menuliskan kode program lalu menyimpannya. Di sini pula, Anda bisa mengatur judul Paste, jenis text, tanggal kedaluarsa, visibilitas, password, dan opsi enkripsi atau tidak.
![User - Halaman Utama - Kosong](https://github.com/akamamara/komdat-p1-kel6/blob/main/images/screencapture-paste-thareeq-id-C.png)
Setelah diisi, klik "Paste" untuk menyimpan.
![User - Halaman Utama - Isi](https://github.com/akamamara/komdat-p1-kel6/blob/main/images/screencapture-paste-thareeq-id-F.png)
### List Paste
Di ujung kanan atas halaman utama terdapat username Anda yang jika diklik akan memunculkan menu Pastes, Settings, dan Logout.
![User - Halaman Utama - Username](https://github.com/akamamara/komdat-p1-kel6/blob/main/images/screencapture-paste-thareeq-id-G.png)
Jika menu "Paste" diklik, Anda akan diarahkan ke laman daftar Paste yang anda miliki.
![User- Pastes](https://github.com/akamamara/komdat-p1-kel6/blob/main/images/screencapture-paste-thareeq-id-H.png)
### Profile
Jika menu "Settings diklik Anda akan diarahkan ke laman Profile Anda. Di sini anda bisa mengganti password Anda.
![User - Profile](https://github.com/akamamara/komdat-p1-kel6/blob/main/images/screencapture-paste-thareeq-id-D.png)


## Pembahasan
[`^gulir ke atas^`](#)

PASTE ditulis dalam bahasa pemrograman PHP yang support dengan penggunaan MySQL. Paste merupakan hasil fork dari pastebin.com sebelum akhirnya dijual pada tahun 2010. Aplikasi ini memiliki kelebihan, diantaranya:
* Build-in berbagai macam highlighting code sehingga enak dipandang mata
* Tampilannya simple dan tidak ribet
* Flexible untuk maintenance dan konfigurasi web yang diinginkan
* Memiliki pengaturan tambahan untuk paste, seperti password, paste dihapus setelah lebih dari rentang waktu tertentu, visibility, dan juga password.
* Build-in pengaturan ads bagi admin
* Bisa menambahkan pages selain tampilan awal paste saja

Kekurangan dari aplikasi ini adalah
* Kurangnya pemberitahuan bagi admin saat konfigurasi krusial belum terisi, seperti setting email, sehingga rawan untuk tertinggal ketika dilakukan konfigurasi
* Kurangnya dokumentasi untuk pengaturan custom, seperti pengaturan email, contoh penggunaan laman ads, dan juga sitemap.
* Tema yang diterapkan tidak berlaku untuk laman admin
* Instalasi yang menyulitkan jika diinstall di vm lokal, pada konfigurasi awal ia akan langsung redirect ke localhost tanpa port

## Referensi
* [ComputerForGeeks - Install PHP 7.3 on Ubuntu 18.04 / Ubuntu 16.04 / Debian](https://computingforgeeks.com/how-to-install-php-7-3-on-ubuntu-18-04-ubuntu-16-04-debian/)
* [GitHub - Paste 2.2](https://github.com/jordansamuel/PASTE)
* [InMotionHosting - How to Create a MySQL Database Using the Command Line](https://www.inmotionhosting.com/support/website/how-to-create-a-database-using-mysql-from-the-command-line/)
* [Medium - Instalasi NGINX dan PHP-FPM pada Ubuntu 16.04](https://medium.com/@dataq/instalasi-nginx-dan-php-fpm-pada-ubuntu-16-04-41d4a13e3148)
