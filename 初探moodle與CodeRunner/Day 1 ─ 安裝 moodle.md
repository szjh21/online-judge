---
tags: 專題
---

# Day 1 ─ 安裝 moodle

![](https://i.imgur.com/5ebyRO0.png)

## 參考教學

- [How to install Moodle CMS on Centos 7](https://www.linuxhelp.com/how-to-install-moodle-cms-on-centos-7)
- [moodle installation guide for Ubuntu](https://docs.moodle.org/38/en/Step-by-step_Installation_Guide_for_Ubuntu)

---

## 環境確認

- 作業系統：CentOS 7。
- 去[官網](https://download.moodle.org/releases/latest/)確認 moodle、PHP、DBMS 的版本，然後安裝相對應版本的 LAMP。

![](https://i.imgur.com/JdCr4Ti.png)

## 安裝 PHP 相關套件

70 表示 PHP 版本為 `7.0`。

```
yum install php70w php70w-curl php70w-gd php70w-intl php70w-ldap php70w-mysql php70w-pspell php70w-xml php70w-xmlrpc php70w-zip php70w-common php70w-opcache 
php70w-mbstring php70w-soap
```

## 讓 moodle 兼容 MariaDB

- MariaDB 的設定檔在 `/etc/my.cnf.d/server.cnf`
- 需要啟用「InnoDB 引擎」，才能使 MariaDB 與 moodle 兼容
- 在設定檔中加入以下的內容

```javascript=
[client]
default-character-set=utf8mb4

[mysqld]
default_storage_engine = innodb
innodb_file_per_table = 1
innodb_file_format = Barracuda
innodb_large_prefix

charactor-set-server=utf8mb4
collation-server = utf8mb4_unicode_ci
skip-character-set-client-handshake

[mysql]
default-character-set=utf8mb4
```

## 建立 moodle 用的資料庫

以 root 身分登入。

```
# mysql -u root -p
```

**注意：指令的結尾記得要加上分號。**

建立名為 `moodle` 的資料庫。

```
create database moodle;
```

允許 `admin` 這個帳號可以使用 `moodle` 這個資料庫

```
grant all privileges on moodle.* to ' admin' @' localhost';
```

離開資料庫。

```
exit;
```

---

## 安裝 moodle

用 git 安裝，或從[官網](https://download.moodle.org/)下載壓縮檔皆可，這裡我們採用從官網下載的方法。

### 修改權限

```
chmod -R 755 /var/www/html/moodle
```

## 讓 apache 成為根目錄的擁有者

```
# chown -R apache:apache /var/www/
# systemctl restart httpd
```

## 建立 `moodledata`

### moodledata 是 moodle 存儲上傳數據的資料夾

```
# mkdir /var/moodledata
```

### 修改權限

```
chown -R www-data /var/moodledata
chmod -R 777 /var/moodledata
```

---

## 設定 moodle

網址輸入 `127.0.0.1/moodle`，然後將 data directory 更改為 `/var/moodledata`

![](https://i.imgur.com/Wepq8PA.png)

### 資料庫選擇 MariaDB ( 預設選項是 MySQL )

![](https://i.imgur.com/DeejLQ4.png)

### 填入資料庫的相關資訊

![](https://i.imgur.com/5vfGcq8.png)

### 建立 config.php

在 `config.php` 中貼上一段程式碼。

其中要我們設一個網址，就只能從設定的那個網址進。

### 設定網站管理員

![](https://i.imgur.com/RVSQALI.png)

## 成功

moodle 就這樣建置完成了。

---

## 後記：可能遇到的問題

以下問題皆是由我的組員 perry 幫忙解決的。

1. php 套件安裝：跟 remi repo 有關，明明有安裝，系統卻抓不到。
2. 讓 moodle 擁有兩個 IP。