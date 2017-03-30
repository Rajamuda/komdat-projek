# Aplikasi Web "PageKit"
<h1 align="center"><img src="https://pagekit.com/storage/pagekit-logo.svg" width="500px"></h1>

[Sekilas Tentang](#sekilas-tentang) | [Instalasi](#instalasi) | [Konfigurasi](#konfigurasi) | [Otomatisasi](#otomatisasi) | [Maintenance](#maintenance) | [Cara Pemakaian](#cara-pemakaian) | [Pembahasan](#pembahasan) | [Referensi](#referensi)
:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:

## Sekilas Tentang 
[`^ kembali ke atas ^`](#aplikasi-web-pagekit)

PageKit merupakan aplikasi web *content management system*. PageKit digunakan untuk mempermudah pengguna dalam membangun situs web. PageKit memiliki beberapa fitur, di antaranya, menyediakan pengaturan untuk membuat halaman baru (contoh: membuat halaman untuk *blog*, mengorganisasi *file*, dan personalisasi *web*).


## Instalasi
[`^ kembali ke atas ^`](#aplikasi-web-pagekit)

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
[`^ kembali ke atas ^`](#aplikasi-web-pagekit)

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
[`^ kembali ke atas ^`](#aplikasi-web-pagekit)

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
[`^ kembali ke atas ^`](#aplikasi-web-pagekit)

PageKit menyediakan fitur *maintenance* apabila admin web ingin melakukan perbaikan pada situs. 
1. Pada halaman *dashboard* admin (http://URL/admin/dashboard), klik tombol *hamburger* di pojok kiri atas, kemudian pilih ikon *Site*
![](http://rajamuda.cf/images/komdat/7.PNG)
2. Pada halaman *site*, pilih tab *Settings*, kemudian pilih submenu *Maintenance*
![](http://rajamuda.cf/images/komdat/5.PNG)
3. Setelah itu, centang *Put the site offline and show the offline message.*, kemudian isikan pesan yang akan ditampilkan untuk memberitahukan bahwa situs sedang ada perbaikan (opsional), lalu tambahkan gambar (opsional).
![](http://rajamuda.cf/images/komdat/8.PNG)
4. Terakhir, tekan tombol *Save* kemudian coba akses kembali situsnya (dalam keadaan tidak *login* sebagai admin).
![](http://rajamuda.cf/images/komdat/9.PNG)

## Cara Pemakaian
[`^ kembali ke atas ^`](#aplikasi-web-pagekit)

1. Tampilan aplikasi web
	1. Tampilan utama (*default*)
	![](http://rajamuda.cf/images/komdat/6.PNG)
	2. Tampilan halaman blog (*default*)
	![](http://rajamuda.cf/images/komdat/11.PNG)
	3. *Dashboard admin*
	![](http://rajamuda.cf/images/komdat/10.png)

2. Fungsi-fungsi utama
	1. Register *User* Baru
		* Fungsi ini digunakan apabila ada *guest* yang ingin menjadi penulis blog atau agar dapat menulis komentar di blog. Langkah pertama, lihat *widgets Login* yang terletak di *sidebar* kanan. Kemudian, klik tombol *Sign Up*
	
		![](http://rajamuda.cf/images/komdat/12.png)
	
		* Setelah itu, isikan semua *field* yang diberikan
	
		![](http://rajamuda.cf/images/komdat/13.png)
	
		* Setalahnya, klik tombol *Sign Up* dan akan muncul pemberitahuan bahwa *user* telah berhasil didaftarkan.
	
		![](http://rajamuda.cf/images/komdat/14.png)
	
		* Lakukan login, kemudian akses http://YourURL/admin/.
	
		![](http://rajamuda.cf/images/komdat/15.png)
	
	2. Buat Pos
		* Untuk membuat *post*, di halaman *dashboard admin*, klik *hamburger button* yang terletak di pojok kiri atas, kemudian pilih *Blog*
	
		![](http://rajamuda.cf/images/komdat/16.png)

		* Setelah itu, klik tombol *Add Post*

		![](http://rajamuda.cf/images/komdat/17.png)

		* Isikan *post* yang ingin dibuat, setelah selesai klik tombol *Save*

		![](http://rajamuda.cf/images/komdat/18.png)
	
	3. Buat *Page* Baru
		* Untuk membuat *page*, dari halaman *dashboard admin*, klik *hamburger button* yang terletak di pojok kiri atas, kemudian pilih *Site*

		![](http://rajamuda.cf/images/komdat/19.png)

		* Setelah itu, klik tombol *Add Page*, kemudian pilih *Page*

		![](http://rajamuda.cf/images/komdat/20.png)

		* Isikan *page* yang ingin dibuat sesuai *field* yang tersedia, kemudian klik tombol *Save*

		![](http://rajamuda.cf/images/komdat/21.png)
	
	4. Mengganti Tema
		* Unduh koleksi tema di halaman *Marketplace* dan pilih tab Tema

		![](http://rajamuda.cf/images/komdat/22.PNG)

		* Pilih salah satu tema, kemudian klik

		![](http://rajamuda.cf/images/komdat/23.PNG)

		* Setelah terunduh, klik tombol *Enable* untuk mengaktifkan tema

		![](http://rajamuda.cf/images/komdat/24.PNG)

		* Tema yang telah terunduh dapat dilihat di halaman *System* dan pilih tab *Theme*

		![](http://rajamuda.cf/images/komdat/25.PNG)
		![](http://rajamuda.cf/images/komdat/26.PNG)
	
	5. Menambahkan Widget
		* Buka halaman *Site* melalui menu di *hamburger button*, kemudian pilih tab *Widgets*
	
		![](http://rajamuda.cf/images/komdat/27.PNG)

		* Klik tombol *Add Widgets*

		![](http://rajamuda.cf/images/komdat/28.PNG)

		* Pilih salah satu kategorinya, *Menu* untuk menambahkan *list* halaman, *Text* untuk menambahkan ukiran kata-kata, dan *Link* untuk menambahkan pranala ke halaman lain.

		![](http://rajamuda.cf/images/komdat/29.PNG)

		* Isikan *field* yang perlu isi, kemudian atur tata letaknya di menu *dropdown* sebelah kanan

		![](http://rajamuda.cf/images/komdat/30.PNG)

		* Setelah selesai, klik *Save*. Cek halaman awal apakah *widget* sudah berhasil ditambahkan.

		![](http://rajamuda.cf/images/komdat/31.PNG)
	
	6. Manajemen *User* dan Mengatur *Permission* berdasarkan *role*
		* Buka halaman *Users* melalui menu di *hamburger button*
	
		![](http://rajamuda.cf/images/komdat/32.PNG)

		* Diberikan *list* *user* yang sudah terdaftar, apabila *role*-nya adalah *admin*, maka ia bisa menghapus/memblokir *user*

		![](http://rajamuda.cf/images/komdat/33.PNG)

		* Untuk mengatur *Permission* untuk *Role* tiap-tiap *user*, klik tab *Permission*.
		* Di situ, kita bisa memberikan/melepas izin untuk tiap jenis aktivitas yang dapat dilakukan.

		![](http://rajamuda.cf/images/komdat/34.PNG)


## Pembahasan
[`^ kembali ke atas ^`](#aplikasi-web-pagekit)

Aplikasi web PageKit merupakan CMS yang bisa dikatakan baru, namun memiliki beberapa fitur yang diunggulkan, di antaranya:
1. Dibangun menggunakan *framework* PHP Symfony dan Vue.js
2. Tampilan yang modern dan *responsive*, namun tetap terlihat sederhana
3. Proses instalasi dan konfigurasi yang sangat mudah dan serba otomatis
4. Terdapat editor teks berupa Markdown dan HTML
5. Terdapat *file manager* untuk mengatur *file* apa saja yang diunggah ke server
6. Personalisasi dan pengaturan halaman situs yang tidak rumit
7. Pengaturan kontrol *cache*

Namun, dari keunggulan yang diberikan, masih terdapat beberapa kekurangan, di antaranya:
1. Variasi tema dan ekstensi (*plugin*) yang diberikan masih terbilang sedikit, selain itu hanya bisa menggunakan tema yang disediakan, tidak dapat dikustomisasi atau dibuat sendiri.
2. Walaupun terbilang mudah, tidak seperti wordpress yang memiliki *live preview*, untuk mengatur tata letak *widget* yang akan ditampilkan di situs masih menggunakan menu *dropdown*.

### Perbandingan dengan aplikasi web 'Subrion'
Sama halnya dengan PageKit, Subrion merupakan CMS yang digunakan untuk mempermudah pengguna membangun situs web. Dengan berbagai macam fitur yang ditawarkan, terdapat beberapa kesamaan, di antaranya:
1. Subrion dapat digunakan untuk membuat situs blog
2. Memiliki *user management* lengkap dengan *permission* sesuai *role*-nya
3. Kustomisasi halaman (membuat baru, menghapus, mengubah status (aktif/inaktif/draft))
4. Terdapat *storage management* untuk mengatur *file-file* yang terunggah ke server

Namun ada beberapa hal yang perlu diperhatikan sebagai ciri pembeda.
1. Halaman *admin* PageKit memiliki tampilan sederhana (tidak banyak *content* yang ditampilkan dalam suatu halaman, sedangkan Subrion terkesan menampilkan banyak *content*
2. Terdapat fitur unik di Subrion, yaitu adanya fitur *SQL Tools*, tanpa perlu membuka *phpMyAdmin* kita dapat melihat isi *database*-nya
3. Subrion juga dilengkapi dengan fitur keamanan di antaranya HTTPS, anti-CSRF, Build-in Captcha), sedangkan PageKit hanya pengaturan HTTPS saja yang ada

## Referensi
[`^ kembali ke atas ^`](#aplikasi-web-pagekit)

1. [About | PageKit](https://pagekit.com/about) - PageKit
2. [How To Rewrite URLs with mod_rewrite for Apache on Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/how-to-rewrite-urls-with-mod_rewrite-for-apache-on-ubuntu-16-04) - DigitalOcean
3. [Installation | PageKit](https://pagekit.com/docs/getting-started/installation) - PageKit
3. [CLI | Pagekit](https://pagekit.com/docs/developer/cli) - PageKit
