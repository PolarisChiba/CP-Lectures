# 二分搜

---

* 題目
* 給定一個由 $0$、$1$ 組成的數列
* 保證 $0$ 一定出現在 $1$ 前面
* 請求出最後一個出現 $0$ 的位置
* 若不存在請輸出 -1

---

* 數字範圍
* 數列長度至多 $10^5$

---

* 範例
* 輸入：00111
* 輸出：1

---

* 這樣對嗎？

```cpp=
#include <bits/stdc++.h>
using namespace std;

int main() {
    string s;
    cin >> s;
    int L = 0, R = (int)s.size() - 1;
    while (R - L > 1) {
        int mid = (L + R) >> 1;
        if (s[mid] == '0')
            L = mid;
        else
            R = mid;
    }
    if (s[L] == '0')
        cout << L << "\n";
    else
        cout << "-1\n";
}
```

---

* 反例：00000

---

* 將 ``L`` 放在 0 的格子上
* 將 ``R`` 放在 1 的格子上

---

```cpp=
#include <bits/stdc++.h>
using namespace std;
 
int main() {
    string s;
    cin >> s;
    if (s.back() == '0') {
        cout << (int)s.size() - 1 << "\n";
        return 0;
    }
    if (s.front() == '1') {
        cout << "-1\n";
        return 0;
    }

    int L = 0, R = (int)s.size() - 1;
    while (R - L > 1) {
        int mid = (L + R) >> 1;
        if (s[mid] == '0')
            L = mid;
        else
            R = mid;
    }
    cout << L << "\n";
}
```

---

* 另解
* 對答案的二進位制進行搜尋

---

```cpp=
#include <bits/stdc++.h>
using namespace std;
 
int main() {
    string s;
    cin >> s;
    if (s.back() == '0') {
        cout << (int)s.size() - 1 << "\n";
        return 0;
    }
    if (s.front() == '1') {
        cout << "-1\n";
        return 0;
    }

    int ans = 0, n = (int)s.size() - 1;
    for (int i = __lg(n); i >= 0; -- i) {
        if (ans + (1 << i) <= n && s[ans + (1 << i)] == '0')
            ans += (1 << i);
    }
    cout << ans << "\n";
}
```

---

* 題目
* 輸入一個遞增數列，$Q$ 筆詢問
* 每次給定一個 $x$
* 問第一個大於等於 $x$ 的位置在哪
* 還有第一個大於 $x$ 的位置在哪

---

* 範圍
* 數列長度 $\le 10^5$
* $Q\le 10^5$
* 數字都是 ``int`` 範圍

---

* ``lower_bound(beg, end, x)``
* 第一個大於等於 ``x`` 的位置
* ``upper_bound(beg, end, x)``
* 第一個大於 ``x`` 的位置

---

```cpp=
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    vector<int> v(n);
    for (auto &i : v) cin >> i;
    
    int q;
    cin >> q;
    while ( q -- ) {
        int x;
        cin >> x;
        cout << lower_bound(v.begin(), v.end(), x) - v.begin() << "\n";
        cout << upper_bound(v.begin(), v.end(), x) - v.begin() << "\n";
    }
}

```

---

* 題目
* 給定一個數列，並給定數字 $x$
* 求第一個前綴和 $\ge x$ 的位置
* 不存在的話請輸出 -1 

---

* 範圍
* 數列長度 $\le 10^5$
* $x\le 10^{18}$

---

```cpp=
#include <bits/stdc++.h>
using namespace std;
typedef long long ll;

int main() {
    int n;
    cin >> n;
    vector<ll> v(n);
    for (auto &i : v) cin >> i;
    ll x;
    cin >> x;
    
    int sum = 0;
    for (auto i : v) sum += i;
    if (sum < x) {
        cout << "-1\n";
        return 0;
    }
    if (v.front() >= x) {
        cout << "0\n";
        return 0;
    }
    
    int L = 0, R = n - 1;
    while (R - L > 1) {
        int mid = (L + R) >> 1;
        sum = 0;
        for (int i = 0; i <= mid; ++ i)
            sum += v[i];
        if (sum < x)
            L = mid;
        else
            R = mid;
    }
    cout << R << "\n";
}
```

---

* 練習題
* [zerojudge f815](https://zerojudge.tw/ShowProblem?problemid=f815)
* [zerojudge f581](https://zerojudge.tw/ShowProblem?problemid=f581)
* [zerojudge h084](https://zerojudge.tw/ShowProblem?problemid=h084)
* [zerojudge i401](https://zerojudge.tw/ShowProblem?problemid=i401)
* [zerojudge j125](https://zerojudge.tw/ShowProblem?problemid=j125)
* [tioj 1337](https://tioj.ck.tp.edu.tw/problems/1337)