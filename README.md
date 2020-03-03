# Laporan Komdat : Virtual Private Server : minimalist-web-notepad
[minimalist-web-notepad](https://github.com/pereorga/minimalist-web-notepad)
Minimalist web notepad merupakan webapp yang memungkinkan user untuk mencatat apapun pada halaman yang disediakan oleh aplikasi dengan tampilan yang sederhana dan url dinamis sehingga bisa diakses dimana saja oleh user dengan alamat note yang user tentukan.

# Virtual Private Server
VPS adalah singkatan dari Virtual Private Server. VPS adalah sebuah tipe server yang menggunakan teknologi virtualisasi untuk membagi hardware server fisik menjadi beberapa server virtual yang di hosting di infrastruktur fisik yang sama

Hal ini dapat membantu mengimprovisasi tingkat fleksibilitas yang tersedia pada administrator sistem dalam hal pemilihan konfigurasi software yang dapat mereka jalankan. Selain itu, ini juga dapat memberikan keuntungan yang signifikan dalam hal skalabilitas dari daya pemrosesan (processing power), RAM, dan disk space dengan biaya yang lebih rendah daripada menggunakan hardware fisik tradisional.

# Panduan Instalasi
[komdat 1 : Virtual Private Server](https://github.com/pereorga/minimalist-web-notepad)

Instalasi LAMP (Linux Apache MySQL PHP)
Buka terminal di komputer host, dan akses VM dengan username dan password student.

# akses vm dari host ( ID : student, pw : student )
ssh student@localhost -p 2200

# set repo
    sudo tee /etc/apt/sources.list << !
    deb http://repo.apps.cs.ipb.ac.id/ubuntu bionic          main restricted universe multiverse
    deb http://repo.apps.cs.ipb.ac.id/ubuntu bionic-updates  main restricted universe multiverse
    deb http://repo.apps.cs.ipb.ac.id/ubuntu bionic-security main restricted universe multiverse
    !

# instal apache, mysql, php
    sudo apt update

    sudo apt install apache2 php mysql-server

    sudo apt install php-mysql php-gd php-mbstring php-xml php-curl

    sudo service apache2 restart

* Cek instalasi Apache dengan membuka laman http://localhost:80

      cd /var/www/html

      sudo git clone http://github.com/pereorga/minimalist-web-notepad

      cd /var/www/html/minimalist-web-notepad

      sudo a2enmod rewrite

      sudo service apache2 restart


      sudo nano /etc/apache2/sites-enabled/000-default.conf

      /etc/apache2/sites-available/default
      <Directory /var/www/html>
                      Options Indexes FollowSymLinks MultiViews
                      AllowOverride All
                      Order allow,deny
                      allow from all
      </Directory>

      sudo service apache2 restart

      sudo nano /var/www/html/.htaccess

      /var/www/html/.htaccess
      RewriteEngine on

      sudo chmod 644 /var/www/html/.htaccess


#ganti base_url ke localhost

## Konfigurasi (opsional)

Setting server tambahan yang diperlukan untuk meningkatkan fungsi dan kinerja aplikasi, misalnya:
- batas upload file
- batas memori
- dll

Plugin untuk fungsi tambahan
- login dengan Google/Facebook
- editor Markdown
- dll


## Cara Pemakaian

- Buka aplikasi "Minimalist-web-notepad"
- Tulis apa yang ingin anda tulis di notepad 
- Ubah link URL dengan nama sesuka mu,salah satu contohnya : whatever
- Tulisan akan otomatis di simpan oleh sistem aplikasi 
 Berikut dibawah ini adalah hasil screenshootnya :
 
 
## Pembahasan

- Pendapat anda tentang aplikasi web ini
    - kelebihan
    - kekurangan
- Bandingkan dengan aplikasi web lain yang sejenis


## Referensi

https://notes.orga.cat or https://notes.orga.cat/whatever.
https://www.digitalocean.com/community/tutorials/how-to-set-up-mod_rewrite-for-apache-on-ubuntu-14-04
http://www.apache.org/licenses/LICENSE-2.0
