###### tags: `專題` `Coderunner`

# Coderunner 出題: function

## 一般步驟

要出函式的題目，以C++為例，題型選擇`cpp_function`

![](https://i.imgur.com/P1UVTaE.png)

測資設置:
    * Test case的程式碼最後一行沒加分號沒關係，但如果有多行程式碼須注意。Extra template data也是一樣。

![](https://i.imgur.com/NECx5pf.png)


## 背景原理

Coderunner使用Twig Template Engine產生送給Jobe Sandbox執行的程式碼，並分析回傳的結果來評分。在Coderunner中每個題型都有各自的template。

以`cpp_function`的template為例:
```
#include <iostream>
#include <fstream>
#include <string>
#include <cmath>
#include <vector>
#include <algorithm>

using namespace std;
#define SEPARATOR "#<ab@17943918#@>#"

{{ STUDENT_ANSWER }}

int main() {
{% for TEST in TESTCASES %}
   {
    {{ TEST.extra }};
    {{ TEST.testcode }};
   }
    {% if not loop.last %}cout << SEPARATOR << endl;{% endif %}
{% endfor %}
    return 0;
}
```
* `{{ STUDENT_ANSWER }}`: 學生繳交的程式碼
* `{{ TEST.extra }}`: Extra template data的內容
* `{{ TEST.testcode }}`: Test case的內容

若使用下面的Test case設置

![](https://i.imgur.com/zrECSsE.png)

而學生繳交的程式碼如下

```cpp=
void hello(){
  cout << "hello world";
}
```

則會產生下列的程式碼

```cpp=
#include <iostream>
#include <fstream>
#include <string>
#include <cmath>
#include <vector>
#include <algorithm>

using namespace std;
#define SEPARATOR "#<ab@17943918#@>#"

void hello(){
  cout << "hello world";
}

int main() {
   {
    int run = 1;
run++;;
    hello();
   }
    cout << SEPARATOR << endl;   {
    int run = 2;
run++;;
    hello();
   }
        return 0;
}
```