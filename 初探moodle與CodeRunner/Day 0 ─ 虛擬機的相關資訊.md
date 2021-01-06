# Day 0 ─ 虛擬機的相關資訊

## 前言

1. 基本上我們只會碰到 CenrOS 7 與 CentOS 8。
2. 請自行上網 google 搜尋 ZeroTier 的使用方式。
3. 如果有停電，請遠端連上 Teamviewer，從 Host 重開 VM。( 螢幕解鎖方式如圖所示 )

- ID：1 427 383 920
- 密碼：李龍盛

![](https://i.imgur.com/h0vRFEm.png)

---

## CentOS 7

- 用途：moodle 操作
- 校內虛擬 IP：`10.17.173.32`
- ZeroTier IP: `10.147.17.206`

### 資料庫

- 管理者：root / password

### moodle

- 管理員：admin / Password123#
- 學生：ricardo69 / Ricardo69#
- 老師：teacher / Teacher456#

---

## CentOS 8

- 用途：作為 jobe server
- IP 皆為 Static IP
- 總共有4台：
    * centos7_jobe (Jobe00)：
        * 校內: `10.16.173.225`
        * ZeroTier: `10.147.17.99`

    * centos8 (Jobe01)：
        * 校內: `10.16.173.226`
        * ZeroTier: `10.147.17.251`
        * 此台jobe功能暫時關閉，單獨只做proxy

    * centos_0305 (Jobe02)：
        * 校內: `10.16.173.229`
        * ZeroTier: `10.147.17.71`
        * 目前學校ecourse是連到這台

    * jobe03 (0924建立)：
        * 校內: `10.17.173.34`

    * jobe04 (0924建立)：
        * 校內: `10.17.173.35`

---

## CentOS 6

- 用途：學校的 moodle
- Dynamic IP：`10.19.173.137`


### 相關設定

- Linux root 密碼：123456**
- MySQL root 密碼：123456**
- Apache：`/usr/local/apache`
- MySQL：`/usr/local/mysql`

### moodle

- admin / 123456** ( 管理員 )
- student / Student123# ( 學生 )
- teacher / Teacher456# ( 老師 )