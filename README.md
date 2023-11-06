# ci4-test



## Konfigurasi Codeiginter 4 tanpa /Public

- Pindahkan `public/index.php` dan `public/.htaccess` ke `/index.php` dan `/.htaccess1`
- Edit pada index.php
<br>`require FCPATH . '../app/Config/Paths.php';` 
<br>menjadi
<br>`require FCPATH . 'app/Config/Paths.php';` 
<br>
- Edit app/Config/App.php
<br> `public string $uriProtocol = 'PATH_INFO';`
<br>menjadi
<br>`public string $uriProtocol = 'REQUEST_URI';`
- Tambahkan .htaccess bagian akhir
<br>
```
DirectoryIndex index.php
RewriteEngine On
RewriteCond %{SCRIPT_FILENAME} !-d
RewriteCond %{SCRIPT_FILENAME} !-f
RewriteRule ^ index.php [L]
RewriteRule !^(public/|index\.php) [NC,F]
```