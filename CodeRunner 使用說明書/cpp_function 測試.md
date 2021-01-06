---
tags: 專題
---

# cpp_function 測試

## reference

請參考 `cpp_function 說明.md`。

## 初步測試結果

function：IsPrime(num)。

![](https://i.imgur.com/pDSg0Am.png)

如果 test case 沒有 void，會編譯錯誤，所以它加上了 void。

![](https://i.imgur.com/iZH9LS6.png)


結果是空白的。

![](https://i.imgur.com/aPTVQrP.png)

---

> [name=perryOnCrack]
> 幾件事情:
> 1. Test case 裡面是要放測試用的程式碼片段，所以以這題為例，應該要寫成像這樣
> ```
> int num;
> cin >> num;
> IsPrime(num);
> ```
> 2. Anwesr box preload 裡面放的東西會全部給學生，**function題型只需要學生寫function而已**，所以不建議這樣把整個程式碼給學生，學生會被誤導。
> 以這題來講，Anwesr box preload 建議是寫這樣就好:
> ```
> void IsPrime(int num) {
>
> }
> ```

照做了，但結果長這樣： 

![](https://i.imgur.com/PevE53n.png)

> [name=perryOnCrack]
> 它的using namespace
> 我要看一下學校系統內的coderunner裡的template
> 把customise勾起來
> ![](https://i.imgur.com/b18y8bF.png)
> 然後到下面一點的 Customisation 把 template 裡面的東西貼上來
> ![](https://i.imgur.com/xGlSbN6.png)

![](https://i.imgur.com/2VUhpfj.png)

確定是用 cpp_function? 已解決 能跑了

👍 3Q

能不能問個那個Extra template data的用處?

只是放在test case前的程式碼而已
所以寫這樣的話
![](https://i.imgur.com/Uer5UqB.png)
這個test case實際在跑會是這樣
```cpp=
int run = 1;
run++;
hello();
```