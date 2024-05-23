---
tags: 資訊之芽 語法班
---

# 一些C++有用的技巧

---

## 亂數

- 模擬扔一顆骰子一萬次，每次出現的數字
- 舉辦抽獎活動時，隨機抽中一個人
- 樂透公司要產生每期的中獎號碼
- 助教講師在生測資時，要生出夠隨機的數字

---

## 方法一，黑箱

```cpp=
#include <iostream>
using namespace std;

int s[6] = {1, 3, 6, 4, 2, 5};

int main() {
    int n;
    cin >> n;
    for (int i = 0; i < n; ++ i)
        cout << s[i % 6] << "\n";
}
```

---

## 缺點

- 不夠隨機
- 很可能被看破手腳
- ~~然後就被炎上~~

---

## 方法二

使用「看起來」很複雜的函數來生成。

```cpp=
#include <iostream>
using namespace std;

int main() {
    int n;
    int x = 0;
    for (int i = 0; i < n; ++ i) {
        cout << x + 1 << "\n";
        x = (x * x * x + 1) % 6;
    }
}
```

---

## 亂數的要求

- 難以預測、複雜
- 週期非常長
- 數字分布均勻

---

## 線性同餘方法

- 種子seed：$X_0$
- $X_{j+1} \equiv (A \times X_{j} + B)\mod M$
- 生成出來的數字都小於$M$
- 所以$M$要夠大

---

## 線性同餘方法

```cpp=
#include <iostream>
using namespace std;

int main() {
    int n; 
    cin >> n;
    long long x = 123;
    long long a = 3451, b = 54321, m = 1e9 + 7;
    for (int i = 1; i <= n; ++ i) {
        cout << x % 6 + 1 << "\n";
        x = (a * x + b) % m;
    }
}
```

---

## 線性同餘方法

[一些使用線性同餘方法的地方](https://en.wikipedia.org/wiki/Linear_congruential_generator#Parameters_in_common_use)

---

## C++內建亂數

- 決定種子：srand(int)
- 輸出亂數：rand()

---

## 亂數的種子

- 現在的時間
- time(NULL)

---

## C++內建亂數

```cpp=
#include <iostream>
#include <cstdlib>
#include <time.h>
using namespace std;

int main() {
    srand(time(NULL));
    int n;
    cin >> n;
    for (int i = 1; i <= n; ++ i)
        cout << rand() % 6 + 1 << "\n";
}
```

---

## 亂數總結

- 要注意，線性同餘方法生成的並非「真正的亂數」
- 真正的亂數必須是無跡可尋的
- 但幾乎無法產生真正的亂數，所以使用線性同餘方法就很夠了
- 而C++的rand的實作也是基於線性同餘方法

---

## 型別轉換

- 輸入兩個整數，求兩者相除後的浮點數值
- 有一個bool陣列，想要求其中有幾個一

---

## 型別轉換

- 顯性轉型：由coder主動告訴編譯器如何改變變數的型態
- 隱性轉型：由編譯器在編譯時默默進行轉型

---

## 隱性轉型

編譯器偷偷的將bool轉換成了int。

```cpp=
#include <iostream>
using namespace std;

int main() {
    bool b[3] = {0, 1, 0};
    int sum = 0;
    for (int i = 0; i < 3; ++ i)
        sum += b[i];
    cout << sum << "\n";
}
```

---

## 型別的「大小」

- bool：8位元
- int：32位元
- long long：64位元
- 數字的型別之間會有大小的差別
- 隱式轉換，在不同型別間做運算時，會將小的型態轉成大的

---

## 隱性轉型

```cpp=
#include <iostream>
using namespace std;

int main() {
    // 10000, 2.12345
    // 100000, 2.12345
    int a = 10000;
    float b = 2.12345;
    b += a;
    cout << b << "\n";
    cout << typeid(b).name() << "\n";
}
```

---

## 隱性轉型

```cpp=
#include <iostream>
using namespace std;

int main() {
    // 10000, 2.12345
    // 100000, 2.12345
    int a = 10000;
    float b = 2.12345;
    a += b;
    cout << a << "\n";
    cout << typeid(a).name() << "\n";
}
```

---

## 強制型別轉換

使用小括號來進行型別轉換。

```cpp=
#include <iostream>
using namespace std;

int main() {
    int a, b;
    cin >> a >> b;
    cout << (double)a / (double)b << "\n";
}
```

---

## 強制型別轉換

```cpp=
#include <iostream>
using namespace std;

int main() {
    double a, b;
    cin >> a >> b;
    cout << (int)a / (int)b << "\n";
}
```

---

## const casting

用來改變帶有const的指標，極度不推薦使用。

```cpp=
#include <iostream>
using namespace std;

int main() {
    int x = 50;
    const int* y = &x
    cout << "previous: " << *y << "\n";
    int* z = const_cast<int *>(y);
    *z = 100;
    cout<< "new: " << *y << "\n";
}
```

---

## static casting

在數字型態的轉換上，與強制型別轉化類似

```cpp=
#include <iostream>
using namespace std;

int main() {
    int a, b;
    cin >> a >> b;
    cout << static_cast<double>(a) / static_cast<double>(b) << "\n";
}
```

---

## static casting

使用g++ -Wconversion來編譯
會跳出警告

```cpp=
#include <iostream>
using namespace std;

int main() {
    double a = 0.1;
    int b = a;
}
```

---

## static casting

使用g++ -Wconversion來編譯
告訴編譯器我知道自己在做甚麼，不需要跳出警告

```cpp=
#include <iostream>
using namespace std;

int main() {
    double a = 0.1;
    int b = static_cast<int>(a);
}
```

---

## 轉型總結

- C++還有支援一些不同的轉型方法，但目前不會用到
- 以目前來說，使用強制型別轉換即可
- 轉型的時候，有時候會喪失資料
- 像是從浮點數轉成整數時，要特別留意

---

## auto

- 有時候不清楚變數的型別是甚麼
- 或者是想要編譯器來幫你處理的

---

## auto

```cpp=
#include <iostream>
using namespace std;

int main() {
    double a = 3.2;
    auto b = a / 2;
    cout << b << "\n";
    cout << typeid(b).name() << "\n";
}
```

---

## auto

```cpp=
#include <iostream>
using namespace std;

int main() {
    int x = 5;
    int *y = &x;
    auto z = *y;
    cout << z << "\n";
    cout << typeid(z).name() << "\n";
}
```

---

## auto

auto也能夠用在遍歷陣列上

```cpp=
#include <iostream>
using namespace std;

int main() {
    int a[3] = {0, 1, 2};
    for (auto i : a)
        cout << i << "\n";
}
```

---

同樣的寫法也可以具體的指定變數

```cpp=
#include <iostream>
using namespace std;

int main() {
    int a[3] = {0, 1, 2};
    for (int i : a)
        cout << i << "\n";
}
```

---

## auto

要注意長度

```cpp=
#include <iostream>
using namespace std;

int main() {
    int a[4] = {0, 1, 2};
    for (int i : a)
        cout << i << "\n";
}
```

---

## auto 

編譯器不知道型別，可能會出錯

```cpp=
#include <iostream>
using namespace std;

int main() {
    // auto a; Error
    auto a = 10;
    cout << a << "\n";
    cout << typeid(a).name() << "\n";
}
```

---

## auto 總結

- auto 是很方便的東西
- 未來可能會遇到型別名稱很長或很複雜的變數
- 像是`std::set<int>::iterator`等等
- 這時候用auto就會方便許多
- 要注意，有時候編譯器會不知道型別是甚麼，這時候就會出錯

---

## pair

- 將兩個變數包在一起
- 在很多時候，可以讓程式碼更俐落

---

## pair

需要`include<utility>`
有著first與second兩個屬性

```cpp=
#include <iostream>
#include <utility>
using namespace std;

int main() {
    pair<int, double> a = make_pair(1, 0.3);
    cout << a.first << " " << a.second << "\n";
    // cout << a << "\n";   Error
    a.first += 1;
    a.second *= 3;
    cout << a.first << " " << a.second << "\n";
}
```

---

## pair

也可以用在陣列上

```cpp=
#include <iostream>
#include <utility>
using namespace std;

int main() {
    pair<int, double> a[100];
    int n;
    cin >> n;
    for (int i = 1; i <= n; ++ i) 
        cin >> a[i].first >> a[i].second;
    for (int i = 1; i <= n; ++ i)
        cout << a[i].first << " " << a[i].second;
}
```

---

## pair

搭配auto服用

```cpp=
#include <iostream>
#include <utility>
using namespace std;

int main() {
    pair<int, double> a[100];
    int n;
    cin >> n;
    for (int i = 1; i <= n; ++ i) 
        cin >> a[i].first >> a[i].second;
    for (int i = 1; i <= n; ++ i) {
        auto b = a[i];
        cout << b.first << " " << b.second << "\n";
    }
}
```

---

## 總結

- 亂數、亂數種子
- 轉型、強制型別轉換
- auto
- pair

---