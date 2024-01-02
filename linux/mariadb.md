# MariaDB

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

## Cara Memberikan Hak Akses User ke Database

```bash
GRANT ALL PRIVILEGES ON database.* TO 'username'@'localhost' WITH GRANT OPTION;
```

## Cara Refresh/Flush Hak Akses

```bash
FLUSH PRIVILEGES;
```
