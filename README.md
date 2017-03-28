# Aplikasi Web "PageKit"
<h1 align="center"><img src="https://pagekit.com/storage/pagekit-logo.svg" width="500px"></h1>

[Sekilas Tentang](#sekilas-tentang) | [Instalasi](#instalasi) | [Konfigurasi](#konfigurasi) | [Otomatisasi](#otomatisasi) | [Maintenance](#maintenance) | [Cara Pemakaian](#cara-pemakaian) | [Pembahasan](#pembahasan) | [Referensi](#referensi)
:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:

## Sekilas Tentang 

PageKit merupakan aplikasi web *content management system*. PageKit digunakan untuk membangun *web* dengan mudah. PageKit memiliki beberapa fitur, di antaranya, menyediakan pengaturan untuk membuat halaman baru (contoh: membuat halaman untuk *blog*, mengorganisasi *file*, dan personalisasi *web*.


## Instalasi
#### Kebutuhan
- Apache 2.2+ atau Nginx
- MySQL Server 5.1+ atau SQLite 3
- PHP versi 5.5.9+
- Ekstensi PHP yang harus aktif: JSON, Session, ctype, Tokenizer, SimpleXML, DOM, mbstring, PCRE 8.0+, ZIP dan PDO dengan *driver* MySQL atau SQLite
- (*opsional*) Ekstensi PHP: curl, iconv, XML Parser, APC atau XCache untuk *caching*

#### Cara instalasi
1. Unduh arsip ZIP instalasi Pagekit dan simpan ke dalam direktori pagekit. 
```
$ mkdir pagekit
$ cd pagekit
$ wget http://rajamuda.cf/pagekit-1.0.11.zip
```

2. *Unzip* arsip yang sudah terunduh. 
```
$ unzip pagekit-1.0.11.zip
```

3. Pindahkan direktori pagekit ke /var/www/html/ (direktori sekarang "pagekit")
```
$ sudo mv ../pagekit/ /var/www/html/
```

4. Selanjutnya buka http://localhost (localhost -> alamat IP atau URL kamu). Selanjutnya ikuti langkah-langkah untuk konfigurasi.
	- Pengaturan Bahasa
	![](http://rajamuda.cf/images/komdat/1.png)
    
	- Konfigurasi Database
	![](http://rajamuda.cf/images/komdat/2.PNG)
    
	- Pengaturan Informasi Situs
	![](http://rajamuda.cf/images/komdat/3.PNG)
    
	- Selesai! (Tampilan halaman *admin*)
	![](http://rajamuda.cf/images/komdat/4.PNG)


## Konfigurasi

Pastikan pada konfigurasi Apache, *module* ``mod_rewrite`` sudah dalam keadaan diaktifkan. Untuk melihat *module* mana yang sudah aktif, ketikkan perintah ``apache2ctl -M``.  Jika belum ada di *list*, ketikkan perintah ``sudo a2enmod rewrite`` pada terminal kemudian *restart* apache dengan mengetikkan perintah ``sudo service apache2 restart``. 

Selanjutnya, cek juga file konfigurasi ``apache2.conf`` yang terletak di ``/etc/apache2/``. 
```
$ cat /etc/apache2/apache2.conf
....
<Directory /var/www/>
	Options Indexes FollowSymLinks
	AllowOverride None
	Require all granted
</Directory>
....
```

Jika pengaturan *AllowOverride* pada direktori */var/www* masih *None*, ubah menjadi *All* agar ``mod_rewrite`` bisa dijalankan dengan sepenuhnya.
```
$ sudo nano /etc/apache2/apache2.conf
....
<Directory /var/www/>
	Options Indexes FollowSymLinks
	AllowOverride All
	Require all granted
</Directory>
....
```
Kemudian simpan (ctrl+o) dan keluar (ctrl+x)


## Otomatisasi
Secara *default* di dalam arsip instalasi PageKit, terdapat *executable file* ``pagekit`` yang digunakan untuk menjalankan beberapa perintah CLI, di antaranya:
```
Usage:
  command [options] [arguments]

Options:
  -h, --help            Display this help message
  -q, --quiet           Do not output any message
  -V, --version         Display this application version
      --ansi            Force ANSI output
      --no-ansi         Disable ANSI output
  -n, --no-interaction  Do not ask any interactive question
  -v|vv|vvv, --verbose  Increase the verbosity of messages: 1 for normal output, 2 for more verbose output and 3 for debug

Available commands:
  archive              Archives an extension or theme
  build                Builds a .zip release file
  clearcache           Clears the system cache
  help                 Displays help for a command
  install              Installs a Pagekit package
  list                 Lists commands
  migrate              Migrates Pagekit
  self-update          Checks for newer Pagekit versions and installs the latest
  setup                Setup a Pagekit installation
  start                Starts the built-in web server
  uninstall            Uninstalls a Pagekit package
  update               Updates dependencies of Pagekit packages
 extension
  extension:translate  Generates extension's translation .pot/.po/.php files
 translation
  translation:fetch    Fetches current translation files from languages repository
```

## Maintenance

PageKit menyediakan fitur *maintenance* apabila admin web ingin melakukan perbaikan pada situs. 
1. Pada halaman *dashboard* admin (http://<your URL>/admin/dashboard), klik tombol *hamburger* di pojok kiri atas, kemudian pilih ikon *Site*
![](http://rajamuda.cf/images/komdat/7.PNG)
2. Pada halaman *site*, pilih tab *Settings*, kemudian pilih submenu *Maintenance*
![](http://rajamuda.cf/images/komdat/5.PNG)
3. Setelah itu, centang *Put the site offline and show the offline message.*, kemudian isikan pesan yang akan ditampilkan untuk memberitahukan bahwa situs sedang ada perbaikan (opsional), lalu tambahkan gambar (opsional).
![](http://rajamuda.cf/images/komdat/8.PNG)
4. Terakhir, tekan tombol *Save* kemudian coba akses kembali situsnya (dalam keadaan tidak *login* sebagai admin).
![](http://rajamuda.cf/images/komdat/9.PNG)

## Cara Pemakaian

- Tampilan aplikasi web
- Fungsi-fungsi utama
- Isi dengan data real/dummy (jangan kosongan) dan sertakan beberapa screenshot


## Pembahasan

Aplikasi web PageKit merupakan CMS yang bisa dikatakan baru, namun memiliki beberapa fitur yang diunggulkan, di antaranya:
1. Dibangun menggunakan *framework* PHP Symfony dan Vue.js
2. Tampilan yang modern dan *responsive*, namun tetap terlihat sederhana
3. Proses instalasi dan konfigurasi yang sangat mudah dan serba otomatis
4. Terdapat editor teks berupa Markdown dan HTML
5. Terdapat *file manager* untuk mengatur *file* apa saja yang diunggah ke server
6. Personalisasi dan pengaturan halaman situs yang tidak rumit

Namun, dari keunggulan yang diberikan, masih terdapat beberapa kekurangan, di antaranya:
1. Variasi tema dan ekstensi (*plugin*) yang diberikan masih terbilang sedikit
2. Walaupun terbilang mudah, tidak seperti wordpress yang memiliki *live preview*, untuk mengatur tata letak *widget* yang akan ditampilkan di situs masih menggunakan menu *dropdown*.

## Referensi
1. [About | PageKit](https://pagekit.com/about) - PageKit
2. [How To Rewrite URLs with mod_rewrite for Apache on Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/how-to-rewrite-urls-with-mod_rewrite-for-apache-on-ubuntu-16-04) - DigitalOcean
3. [Installation | PageKit](https://pagekit.com/docs/getting-started/installation) - PageKit
3. [CLI | Pagekit](https://pagekit.com/docs/developer/cli) - PageKit
