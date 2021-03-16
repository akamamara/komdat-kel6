# komdat-kel6
Hasil project UTS mata kuliah Komunikasi Data dan Jaringan

## Sekilas Tentang


## Instalasi
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
CREATE DATABASE paste;
GRANT ALL PRIVILEGES ON *.* TO 'akamamara'@'localhost' IDENTIFIED BY '213465@#Qw';
```
5. Konfigurasi nginx
```
$ sudo apt update
$ sudo apt install php-fpm
```
6. Modifikasi beberapa konfigurasi dalam file `/etc/nginx/sites-available/default`
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
    fastcgi_pass unix:/run/php/php7.0-fpm.sock;
}
location ~ /\.ht {
    deny all;
}
```
7. Lakukan restart untuk service NGINX
```
$ sudo systemctl restart nginx.service
```
8. Upload seluruh file ke dalam direktori kita


## Konfigurasi
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
![Configuration - IP Bans]()
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


## Otomatisasi

## Cara Pemakaian

## Pembahasan

## Referensi
* [ComputerForGeeks - Install PHP 7.3 on Ubuntu 18.04 / Ubuntu 16.04 / Debian](https://computingforgeeks.com/how-to-install-php-7-3-on-ubuntu-18-04-ubuntu-16-04-debian/)
* [GitHub - Paste 2.2](https://github.com/jordansamuel/PASTE)
* [InMotionHosting - How to Create a MySQL Database Using the Command Line](https://www.inmotionhosting.com/support/website/how-to-create-a-database-using-mysql-from-the-command-line/)
* [Medium - Instalasi NGINX dan PHP-FPM pada Ubuntu 16.04](https://medium.com/@dataq/instalasi-nginx-dan-php-fpm-pada-ubuntu-16-04-41d4a13e3148)
