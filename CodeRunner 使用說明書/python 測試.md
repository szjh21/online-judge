---
tags: 專題
---

# python 測試

## 目的

嘗試 import 常用的 library 看看是否可行。

## math

### 程式碼

```
import math
print(math.e)
```

### 結果

```
2.71828
```

---

## thread

### 程式碼

```
import threading
import time
# 子執行緒，也就是你第二個需要執行的程式
def two_job():
	print('thread %s is running...' % threading.current_thread().name)
	for i in range(5):
		print("我是第二個程式：", i)
		time.sleep(0.5)
# 設定子執行緒
t = threading.Thread(target = two_job)
# 執行他
t.start()
print('thread %s is running...' % threading.current_thread().name)
# 這邊開始寫你主要程式碼的工作
for i in range(2):
	print("我是主要程式碼", i)
	time.sleep(1)
t.join()
print('thread %s is running...' % threading.current_thread().name)
print("Done.")
```

### 結果

```
thread Thread-1 is running...
我是第二個程式： 0
thread MainThread is running...
我是主要程式碼 0
我是第二個程式： 1
我是主要程式碼 1
我是第二個程式： 2
我是第二個程式： 3
我是第二個程式： 4
thread MainThread is running...
Done.
```

---

## numpy

### 程式碼

```
import numpy as np
```

### 結果

```
ModuleNotFoundError: No module named 'numpy'
```

### 疑問

numpy 竟然無法被 import？