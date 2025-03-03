# MariaDB

## Installation

```bash
$ sudo apt-get install mariadb-server
```

## Cara Melihat Semua User

```bash
SELECT User, Host FROM mysql.user;
```

## Cara Tambah User

```bash
CREATE USER 'username'@'localhost' IDENTIFIED BY 'password';
```

## Cara Ubah Password User

```bash
ALTER USER 'username'@'localhost' IDENTIFIED BY 'password';
```

## Hapus User

```bash
DROP USER 'username'@'localhost';
```

## Create Database

```bash
CREATE DATABASE demo;
```

## Cara Memberikan Hak Akses User ke Database

```bash
GRANT ALL PRIVILEGES ON demo.* TO 'username'@'%' WITH GRANT OPTION;
```

## Cara Refresh/Flush Hak Akses

```bash
FLUSH PRIVILEGES;
```
