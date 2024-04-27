# PHP

```bash
$ sudo apt-get install software-properties-common
$ sudo add-apt-repository ppa:ondrej/php # Press enter when prompted.
$ sudo apt update
```

# Composer

```bash
$ php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
$ php composer-setup.php
$ php -r "unlink('composer-setup.php');"
$ sudo mv composer.phar /usr/local/bin/composer
```

# SQLSRV

## Langkah 1. Menginstal PHP (Ubuntu dengan PHP-FPM)

```bash
sudo su
add-apt-repository ppa:ondrej/php -y
apt-get update
apt-get install php8.1 php8.1-dev php8.1-fpm php8.1-xml -y --allow-unauthenticated

systemctl status php8.1-fpm
```

## Langkah 2. Menginstal prasyarat (Ubuntu dengan PHP-FPM)

> Instal driver ODBC untuk Ubuntu dengan mengikuti instruksi tentang Menginstal driver Microsoft ODBC untuk SQL Server (Linux). Pastikan juga untuk menginstal unixodbc-dev paket. Ini digunakan oleh pecl perintah untuk menginstal driver PHP. (https://learn.microsoft.com/id-id/sql/connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server?view=sql-server-ver16)

## Langkah 3. Instal driver PHP untuk Microsoft SQL Server (Ubuntu dengan PHP-FPM)

```bash
sudo pecl config-set php_ini /etc/php/8.1/fpm/php.ini
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
printf "; priority=20\nextension=sqlsrv.so\n" > /etc/php/8.1/mods-available/sqlsrv.ini
printf "; priority=30\nextension=pdo_sqlsrv.so\n" > /etc/php/8.1/mods-available/pdo_sqlsrv.ini
exit
sudo phpenmod -v 8.1 sqlsrv pdo_sqlsrv
```

## Langkah 4. Menginstal dan mengonfigurasi nginx (Ubuntu dengan PHP-FPM)

```bash
sudo apt-get update
sudo apt-get install nginx
sudo systemctl status nginx
```

## Langkah 5. Mulai ulang nginx dan uji sampel skrip (Ubuntu dengan PHP-FPM)

```bash
sudo systemctl restart nginx.service
```
