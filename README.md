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

Cek instalasi Apache dengan membuka laman http://localhost:80

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
      
      
Ubah    /var/www/html/.htaccess

        sudo nano /var/www/html/.htaccess

        Options -Indexes
        RewriteEngine On
        RewriteRule ^([a-zA-Z0-9_-]+)$ index.php?note=$1

        <IfModule mod_headers.c>
        Header set X-Robots-Tag: "noindex, nofollow"
        </IfModule>

        <Files "docker-compose.yml">  
            Order Allow,Deny
            Deny from all
        </Files>

        # Uncomment the lines below to enable basic authentication.
        # See https://httpd.apache.org/docs/current/programs/htpasswd.html for generating your .htpasswd

        # AuthType basic
        # AuthName "website.name"
        # AuthUserFile "/home/user/update-path-to.htpasswd"
        # Require valid-user
 
Ubah access file .htaccess 
    
         sudo chmod 644 /var/www/html/.htaccess

ganti base_url ke localhost

        cd /var/www/html
        sudo nano index.php

ganti $base_url menjadi
    
        $base_url = 'http://localhost';


## Cara Pemakaian

- Buka aplikasi "Minimalist-web-notepad"
- Tulis apa yang ingin anda tulis di notepad 
- Ubah link URL dengan nama sesuka mu,salah satu contohnya : whatever
- Tulisan akan otomatis di simpan oleh sistem aplikasi 
  Berikut dibawah ini adalah hasil screenshootnya :
 ![SS 1](https://user-images.githubusercontent.com/47513269/75785797-e06def00-5d96-11ea-9366-ff0e62883d80.png)
 ![ss 2](https://user-images.githubusercontent.com/47513269/75786092-58d4b000-5d97-11ea-99b8-8bb29466701a.png)
![ss 3](https://user-images.githubusercontent.com/47513269/75786131-67bb6280-5d97-11ea-8fb2-6c6a29453e19.png)

 
 
## Pembahasan

- Pendapat anda tentang aplikasi web ini
    - kelebihan
    1. Fleksibel
    2. Mudah digunakan
    3. Ringan dijalankan
    4. Dapat menyimpan secara otomatis
    - kekurangan
    1. Hanya bisa memasukkan string atau data,tidak bisa menampilkan gambar
    2. Fitur Minim 
- Bandingkan dengan aplikasi web lain yang sejenis
(SHRIB)

## Referensi

https://notes.orga.cat or https://notes.orga.cat/whatever.
https://www.digitalocean.com/community/tutorials/how-to-set-up-mod_rewrite-for-apache-on-ubuntu-14-04
http://www.apache.org/licenses/LICENSE-2.0
