---
tags: 專題
---

# Day 5 ─ 增加 jobe server

![](https://i.imgur.com/ggK1MV2.png)

## 前言

由於它是個外掛，所以應該把重心轉移到 coderunner 身上，而非網址。

## 新增 IP 欄位

在 `settings.php` 這個檔案，看到關鍵字 `jobe_host`，於是新增字串 `jobe_host2`。

```php=
<?php
$settings->add(new admin_setting_configtext(
        "qtype_coderunner/jobe_host2",
        get_string('jobe_host', 'qtype_coderunner'),
        get_string('jobe_host_desc', 'qtype_coderunner'),
        'jobe2.cosc.canterbury.ac.nz'));
?>
```

輸入新的 IP，它會幫我自動存進資料庫，我完全不用去處理資料庫的資料。( 太棒了 )

![](https://i.imgur.com/to7VykW.png)

## 將流量分散

- 關鍵字為 `jobe server`
- 找到了 `classes/jobesnadbox` 這個檔案
- 修改 `_constructor()` 當中的程式碼

## 隨機

```php=
<?php
$counter = rand(1,2);
  if($counter == 1)
    $this->jobeserver = get_config('qtype_coderunner', 'jobe_host');
  else
    $this->jobeserver = get_config('qtype_coderunner', 'jobe_host2');
```

## 輪流

由於每次發請求就相當於執行一個新的程式，所以每個請求所執行起來的記憶體區段都是不同的，既然記憶體不一樣 就代表你無法儲存狀態在記憶體中，要儲存狀態的話就要把它寫在不會被影響的地方，例如：資料庫、檔案、cache 等等。

解決方式：我們建立了 `number.txt`，並且再度開啟 SELinux。
附註：此方式雖然有 concurrent contorl 的問題，但應該不影響我們的分散運作。

```php=
<?php
$myfile = fopen("number.txt", "r") or die("Unable to open file!");
$num = fread($myfile,filesize("number.txt"));
$num++;
if ($num==13) {
    $num=1;
}

$myfile = fopen("number.txt", "w") or die("Unable to open file!");
fwrite($myfile, $num);

$myfile = fopen("number.txt", "r") or die("Unable to open file!");
$num = fread($myfile,filesize("number.txt"));
echo $num;
fclose($myfile);
?>
```