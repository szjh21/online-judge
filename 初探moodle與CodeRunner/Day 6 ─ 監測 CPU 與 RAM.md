---
tags: 專題
---

# Day 6 ─ 監測 CPU 與 RAM

## 前言

這個部分我們沒有做，因為我們都是使用的機器都是 VM，「監測」這件事應該是由 Host 管理。

順帶提一下常見的開源監測工具：

1. Zabbix
2. LibreNMS
3. Prometheus + Grafana

## 無窮迴圈

[CPU time](https://github.com/trampgeek/jobe#run_spec-parameters) 預設值 ( 也是最大值 ) 為 5 秒。雖然 jobe 的 [GitHub](https://github.com/trampgeek/jobe/blob/master/application/libraries/LanguageTask.php#L40-L62) 是說最少要設定 2 秒，但是實際跑過之後，設定 1 秒好像也行。

假設 CPU time 設定為 1 秒，遇到無窮迴圈，3 秒後會回應 TLE，我覺得這個 response 的秒數可以接受，可是這樣的 3 秒就讓我電腦的 CPU 飆到快 100%，這個就有點誇張。

附註：學生尚無反應此情形，那就這樣吧。XD

```cpp=
#include<iostream>
using namespace std ;

int main(){
  while(1) cout << "hello" ;
}
```

## jobe server 掛掉

使用者能收到以下的資訊。

![](https://i.imgur.com/nPGW9Es.png)