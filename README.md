# ci4-test

## Install Codeiginter 4
- Download manual dari web resmi Codeiginter
- copy dan extrak di htdocs atau public_html
- Masukan perintah berikut untuk install Codeiginter 4
<br>`composer install -vvv`
- Ubah `env` menjadi `.env`
- Ubah isi .env 
<br> `CI_ENVIRONMENT = production`
<br>menjadi
<br>`CI_ENVIRONMENT = development`

sumber :
<br>https://www.petanikode.com/codeigniter4-install/

## Konfigurasi Codeiginter 4 tanpa /Public
- Pindahkan `public/index.php` dan `public/.htaccess` ke `/index.php` dan `/.htaccess1`
- Edit pada index.php
<br>`require FCPATH . '../app/Config/Paths.php';` 
<br>menjadi
<br>`require FCPATH . 'app/Config/Paths.php';` 
- Edit app/Config/App.php
<br> `public string $uriProtocol = 'PATH_INFO';`
<br>menjadi
<br>`public string $uriProtocol = 'REQUEST_URI';`
- Tambahkan .htaccess bagian akhir
<code>
DirectoryIndex index.php
RewriteEngine On
RewriteCond %{SCRIPT_FILENAME} !-d
RewriteCond %{SCRIPT_FILENAME} !-f
RewriteRule ^ index.php [L]
RewriteRule !^(public/|index\.php) [NC,F]
</code>

Sumber :
<code>
https://jenusdy.medium.com/menghilangkan-public-dan-index-php-pada-codeigniter-4-c40fca863709
</code>
