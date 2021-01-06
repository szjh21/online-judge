---
tags: 專題
---

# Day 3 ─ 安裝與測試 Code Runner

## 前言

官方的外掛主要有 [Virtual Programming Lab](https://moodle.org/plugins/mod_vpl) 和 [Code Runner](https://moodle.org/plugins/qtype_coderunner) 這兩種，我們選擇的 Code Runner。

## 安裝

過程很簡單，只要照著 [GitHub](https://github.com/trampgeek/moodle-qtype_coderunner#installing-coderunner-from-scratch) 上的說明操作即可。

## 新增測驗卷

![](https://i.imgur.com/7zwHUoa.png)

## 新增試題

![](https://i.imgur.com/Jp4I3Rf.png)

## 測試

SELinux 會擋住 jobe server，關閉 moodle 那台的 SELinux 後再測試後就會成功。

![](https://i.imgur.com/nDh0lZk.png)