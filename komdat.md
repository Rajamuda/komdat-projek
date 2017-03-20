# Aplikasi Web "PageKit"


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
``$ mkdir pagekit``
``$ cd pagekit``
``$ wget http://rajamuda.cf/pagekit-1.0.11.zip``

2. *Unzip* arsip yang sudah terunduh. 
``$ unzip pagekit-1.0.11.zip``

3. Pindahkan direktori pagekit ke /var/www/html/ (direktori sekarang "pagekit")
``$ sudo mv ../pagekit/ /var/www/html/``

4. Selanjutnya buka http://localhost (localhost -> alamat IP atau URL kamu). Selanjutnya ikuti langkah-langkah untuk konfigurasi.
	- Pengaturan Bahasa
	![](http://rajamuda.cf/images/komdat/1.png)
    
	- Konfigurasi Database
	![](http://rajamuda.cf/images/komdat/2.PNG)
    
	- Pengaturan Informasi Situs
	![](http://rajamuda.cf/images/komdat/3.PNG)
    
	- Selesai! (Tampilan halaman *admin*)
	![](http://rajamuda.cf/images/komdat/4.PNG)


## Konfigurasi (opsional)

Pastikan pada konfigurasi Apache, *module* ``mod_rewrite`` sudah dalam keadaan diaktifkan. Untuk melihat *module* mana yang sudah aktif, ketikkan perintah ``apache2ctl -M``.  Jika belum ada di *list*, ketikkan perintah ``sudo a2enmod rewrite`` pada terminal kemudian *restart* apache dengan mengetikkan perintah ``sudo service apache2 restart``. 


## Otomatisasi

(**_tidak ada_**)


## Cara Pemakaian

- Tampilan aplikasi web
- Fungsi-fungsi utama
- Isi dengan data real/dummy (jangan kosongan) dan sertakan beberapa screenshot


## Pembahasan

- Pendapat anda tentang aplikasi web ini
	- pros:
	- cons:
- Bandingkan dengan aplikasi web kelompok lain yang sejenis


## Referensi

Cantumkan tiap sumber informasi yang anda pakai.