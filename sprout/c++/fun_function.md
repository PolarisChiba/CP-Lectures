---
tags: 資訊之芽 語法班
---

# C++ 好用function

---

## sort

* 排序一個數列
* sort(begin, end, compare)
* compare 那一項若不寫，預設為小於

---

### example 1

排序一個vector裡面的元素

```cpp=
#include <bits/stdc++.h>
using namespace std;

int main() {
    vector<int> v(10);
    for (auto &i : v) cin >> i;
    sort(v.begin(), v.end());
    for (auto i : v)
        cout << i << " ";
    cout << "\n";
}
```

---

### example 2

排序一個陣列裡的元素

```cpp=
#include <bits/stdc++.h>
using namespace std;

int main() {
    int a[10];
    for (int i = 0; i < 10; ++ i) cin >> a[i];
    sort(a, a + 10);
    for (int i = 0; i < 10; ++ i) 
        cout << a[i] << " \n"[i == 9];
}
```

---

### compare

```cpp=
sort(v.begin(), v.end(), greater<int>());
sort(v.begin(), v.end(), less<int>());
sort(v.begin(), v.end(), [](int a, int b) {
    return a < b;
});
```

---

### complexity

* $O(n\log{n})$
* 在 $n$ 很大時使用quicksort
* 在 $n$ 很小的時候換使用 $O(n^2)$ 的演算法

---

## iota

* iota(begin, end, start)
* *begin = start
* *(begin + 1) = start + 1
* $\cdots$
* *(begin + i) = start + i

---

### example 1 

將一個vector裡的元素設為 $1, 2, \cdots, 10$

```cpp=
#include <bits/stdc++.h>
using namespace std;

int main() {
    vector<int> v(10);
    iota(v.begin(), v.end(), 1);
    for (auto i : v)
        cout << i << " ";
    cout << "\n";
}
```

---

### example 2

將一個陣列的元素設為 $3, 4, 5, \cdots$

```cpp=
#include <bits/stdc++.h>
using namespace std;

int main() {
    int a[100];
    iota(a, a + 100, 3);
    for (auto i : a)
        cout << i << " ";
    cout << "\n";
}
```

---

### complextiy

* $O(n)$

---

## reverse

* reverse(begin, end)
* 將 begin 到 end 裡的元素反轉過來

---

### example

將一個vector裡的元素設為 $10, 9, \cdots, 1$

```cpp=
#include <bits/stdc++.h>
using namespace std;

int main() {
    vector<int> v(10);
    iota(v.begin(), v.end(), 1);
    reverse(v.begin(), v.end());
    for (auto i : v)
        cout << i << " ";
    cout << "\n";
}
```

---

### complexity

* $O(n)$

---

## next_permutation

* 枚舉下一個字典序的排列
* $1, 2, 3\rightarrow 1, 3, 2\rightarrow 2, 1, 3$
* $\rightarrow 2, 3, 1\rightarrow 3, 1, 2\rightarrow 3, 2, 1$
* $\rightarrow 1, 2, 3$
* 從字典序最大回到最小時會回傳false
* 其餘時候回傳true

---

### example

從字典序小到大枚舉 $1, 2, 3, 4$ 的所有排列

```cpp=
#include <bits/stdc++.h>
using namespace std;

int main() {
    vector<int> v(4);
    iota(v.begin(), v.end(), 1);
    do {
        for (auto i : v)
            cout << i << " ";
        cout << "\n";
    } while (next_permutation(v.begin(), v.enD()));
}
```

---

### prev_permutation

* 枚舉上一個字典序的排列
* 從字典序最小回到最大時會回傳false
* 其餘時候回傳true

---

### example

從字典序大到小枚舉 $1, 2, 3, 4$ 的排列

```cpp=
#include <bits/stdc++.h>
using namespace std;

int main() {
    vector<int> v(4);
    iota(v.begin(), v.end(), 1);
    reverse(v.begin(), v.end());
    do {
        for (auto i : v)
            cout << i << " ";
        cout << "\n";
    } while (prev_permutation(v.begin(), v.enD()));
}
```

---

### complexity

* 一次操作最差為 $O(n)$
* 平均下來，一次操作為 $O(1)$
* 即使有數字重複也會正常運作

---

### example 1

由字典序小到大，枚舉所有輸入的排列

```cpp=
#include <bits/stdc++.h>
using namespace std;

int main() {
    vector<int> v(4);
    for (auto &i : v) cin >> i;
    sort(v.begin(), v.end());
    do {
        for (auto i : v)
            cout << i << " ";
        cout << "\n";
    } while (next_permutation(v.begin(), v.enD()));
}
```

---

### example 2

由字典序大到小，枚舉所有輸入的排列

```cpp=
#include <bits/stdc++.h>
using namespace std;

int main() {
    vector<int> v(4);
    for (auto &i : v) cin >> i;
    sort(v.begin(), v.end(), greater<int>());
    do {
        for (auto i : v)
            cout << i << " ";
        cout << "\n";
    } while (prev_permutation(v.begin(), v.end()));
}
```

---

## fill

* fill(begin, end, element)
* 將begin到end - 1的元素設為element

---

### example

將vector裡面的元素全部設為 $10^9 + 7$

```cpp=
#include <bits/stdc++.h>
using namespace std;

int main() {
    vector<int> v(10);
    fill(v.begin(), v.end(), 1000000007);
    for (auto i : v)
        cout << i << " ";
    cout << "\n";
}
```

---

### complexity

* $O(n)$

---

## find

* find(begin, end, element)
* 從begin到end之間尋找是否有等於element的元素
* 如果有的話則回傳那格的指標或iterator
* 沒有的話則回傳end

---

### example

尋找一個vector內是否有sprout這個字串

```cpp=
#include <bits/stdc++.h>
using namespace std;

int main() {
    vector<string> v(4);
    for (auto &i : v) cin >> i;
    auto it = find(v.begin(), v.end(), "sprout");
    cout << (it == v.end() ? "NO\n" : "YES\n");
}
```

---

### complexity

* O(n)

---

## lower_bound

* lower_bound(begin, end, element)
* 只能由小排序到大的序列中使用
* 尋找begin到end中，第一個大於等於element的元素位置
* 若不存在則回傳end

---

### example

尋找vector內，第一個大於等於 $7$ 的元素是多少

```cpp=
#include <bits/stdc++.h>
using namespace std;

int main() {
    vector<int> v(5);
    for (auto &i : v) cin >> i;
    sort(v.begin(), v.end());
    auto it = lower_bound(v.begin(), v.end(), 7);
    if (it == v.end())
        cout << "NO\n";
    else
        cout << *it << "\n";
}
```

---

### complexity

* $O(\log{n})$
* 使用在已經排序好的數列時，比find快

---

### upper_bound

* upper_bound(begin, end, element)
* 只能由小排序到大的序列中使用
* 尋找begin到end中，第一個大於element的元素位置
* 若不存在則回傳end

---

### example

尋找vector內，第一個大於 $7$ 的元素是多少

```cpp=
#include <bits/stdc++.h>
using namespace std;

int main() {
    vector<int> v(5);
    for (auto &i : v) cin >> i;
    sort(v.begin(), v.end());
    auto it = upper_bound(v.begin(), v.end(), 7);
    if (it == v.end())
        cout << "NO\n";
    else
        cout << *it << "\n";
}
```

---

## is_sorted

* is_sorted(begin, end, compare)
* 判斷一個序列是否已經排序好了
* compare不寫的話預設為小於

---

### example 1

判斷一個vector內的元素是否由小到大排序好了

```cpp=
#include <bits/stdc++.h>
using namespace std;

int main() {
    vector<int> v(5);
    for (auto &i : v) cin >> i;
    cout << (is_sorted(v.begin(), v.end()) ? "YES\n" : "NO\n");
}
```

---

### example 2

判斷一個vector內的元素是否由大到小排序好了

```cpp=
#include <bits/stdc++.h>
using namespace std;

int main() {
    vector<int> v(5);
    for (auto &i : v) cin >> i;
    cout << (is_sorted(v.begin(), v.end(), greater<int>()) ? "YES\n" : "NO\n");
}
```

---

### complexity

* $O(n)$

---

## binary_search

* binary_search(begin, end, element)
* 只能用在排序好的序列上
* 若begin到end - 1之間有element，回傳true
* 否則回傳false

---

### example

尋找一個vector內是否有7

```cpp=
#include <bits/stdc++.h>
using namespace std;

int main() {
    vector<int> v(5);
    for (auto &i : v) cin >> i;
    sort(v.begin(), v.end());
    cout << (binary_search(v.begin(), v.end(), 7) ? "YES\n" : "NO\n");
}
```

---

### complexity

* $O(\log{n})$
* 比使用find還快

---

## random_shuffle

* random_shuffle(begin, end)
* 將begin到end - 1的元素隨意打亂

---

### example

將一個vector裡的元素打亂順序

```cpp=
#include <bits/stdc++.h>
using namespace std;

int main() {
    vector<int> v(5);
    for (auto &i : v) cin >> i;
    random_shuffle(v.begin(), v.end());
    for (auto i : v)
        cout << i << " ";
    cout << "\n";
}
```

---

### complexity

* $O(n)$

---

## nth_element

* nth_element(begin, pos, end)
* 將begin到end - 1中，排序好時應該在pos的元素歸位

---

### example

找出一個vector內第四小的元素

```cpp=
#include <bits/stdc++.h>
using namespace std;

int main() {
    vector<int> v(7);
    iota(v.begin(), v.end(), 1);
    nth_element(v.begin(), v.begin() + 4, v.end());
    for (auto i : v)
        cout << i << " ";
    cout << "\n";
}
```

---

### complexity

* $O(n)$
* 這個的複雜度分析挺有趣
* 有興趣的人可以去翻翻看

---

## accumulate

* accumulate(begin, end, start, plus)
* 將begin到end - 1的所有數字加起來，再加上start的值

---

### example

求出一個vector內所有數字的和

```cpp=
#include <bits/stdc++.h>
using namespace std;

int main() {
    vector<int> v(5);
    for (auto &i : v) cin >> i;
    cout << accumulate(v.begin(), v.end(), 0, plus<int>()) << "\n";
}
```

---

### complexity

* $O(n)$

---

## unique

* unique(begin, end)
* 只能用在排序好的序列上
* 將begin到end - 1中重複的數字移除
* 會回傳移除後，序列末端位置的指標

---

### example

將vector內重複的數字移除

```cpp=
#include <bits/stdc++.h>
using namespace std;

int main() {
    vector<int> v(7);
    for (auto &i : v) cin >> i;
    sort(v.begin(), v.end());
    v.resize(unique(v.begin(), v.end()) - v.begin());
    for (auto i : v)
        cout << i << " ";
    cout << "\n";
}
```

---

### complexity

* $O(n)$