---
tags: 專題
---

# Day 4 ─ 安裝 jobe server

## 前言

Code runner 的 [GitHub](https://github.com/trampgeek/moodle-qtype_coderunner#sandbox-configuration) 有提到：背後運作的 judge server 是官方提供用來「嘗試」用的，所以我們必須自己架設一個 judge server，我們稱為 jobe server。

## 徒手安裝失敗

整個過程都有照著 jobe 的 [GitHub](https://github.com/trampgeek/jobe#installation) 一步一步的做，最後仍失敗，查看 log `/var/log/jobe` 的內容：

```
exception: call to undefined function sem_get()
```

找到這篇解答：[在 Linux 下編譯安裝PHP 7.3.10](https://commandnotfound.cn/php/2/17/PHP-7.3.6)，204g4hk4g4ru,6eji3b/6b06g4g 1942k7
但是測試結果仍然是失敗的，於是我們就考慮使用 Docker 了。

## Docker 安裝，輕鬆又快

從 Docker hub 把 [trampgeek/jobeinabox](https://hub.docker.com/r/trampgeek/jobeinabox/) 這個 image 拉下來使用，一步一步照著網頁上的說明操作即可。

## 調整 jobe server 的 IP

![](https://i.imgur.com/HId1Op8.png)

## 關閉防火牆

[network connectivity to Docker CE container on CentOS 8](https://serverfault.com/questions/987686/no-network-connectivity-to-from-docker-ce-container-on-centos-8)

## 測試成功

有 access log。

![](https://i.imgur.com/zZOvh7q.png)