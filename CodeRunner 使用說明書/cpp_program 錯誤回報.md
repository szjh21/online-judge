---
tags: 專題
---

# cpp_program 錯誤回報

## 1. 沒有用到的變數

### 程式碼

```cpp=
#include <iostream>
using namespace std;

int main(){
 int a;
 int b ;
 cin >> a;
 cout << a+1;
}
```

### 錯誤訊息

會跟你說第幾行，哪個變數是沒用到的。

![](https://i.imgur.com/FMT9K4g.png)

### 原因

g++ 引數`-Wall`和`-Werror` ( 詳細請見 [gcc-gnu 官網](https://gcc.gnu.org/onlinedocs/gcc/Warning-Options.html#Warning-Options) )。

* `-Werror`: 視所有警告(Warning)為錯誤(Error)。
* `-Wall`: 簡單來講是啟動了一堆警告，但是都是可容易避免的。



![](https://i.imgur.com/7mNWZBg.png)

---

## 2. unsigned int vs  int

### 程式碼

```cpp=
#include <iostream>
#include <string>
using namespace std;

int main(){
    string a;
    cin >> a;
    for(unsigned int i=0;i<a.size();i++){
        cout << a[i];
    }
}
```

### 錯誤訊息

![](https://i.imgur.com/l5DFUY9.png)

![](https://i.imgur.com/kqfziOY.png)

### 原因

一樣是因為 g++ 引數，關於 int 可以參考 stackoverflow 上的這篇[文章](https://stackoverflow.com/questions/7488837/why-is-int-rather-than-unsigned-int-used-for-c-and-c-for-loops)。

---

## 3. 無法辨識最後一個空格

有沒有印出最後一個空格都會給對。

```cpp=
#include <iostream>
using namespace std;

int main(){
    for(int i=1;i<=5;i++){
        cout << i << " ";
    }
}
```

![](https://i.imgur.com/xrwNPy0.png)

最後面埋空格沒被檢查是coderunner的問題，它的grader不知道為什麽把他忽略掉了。

## 4. 不要 `#include <bits/stdc++.h>`

有用到什麼函式就 include 什麼。因為 `bits/stdc++.h` 是有用 Precompiled header 時才用的，我們編譯器沒有設置用 Precompiled header，所以導致編譯時都得再解析過 `bits/stdc++.h` 裡面 include 的 headers，進而導致 g++ 用過多記憶體。詳情可參考 [C++ Using Precompiled Headers](https://gcc.gnu.org/onlinedocs/gcc/Precompiled-Headers.html)。