# LIS

## 問題

給定一個序列 $S$，求其中的最長遞增子序列長度。
（遞增指的是嚴格遞增）

$|S|\le 10^5$。

## Remark

* 嚴格遞增：$S_i < S_{i+1}$。
* 非嚴格遞增：$S_i \le S_{i+1}$。

## dp 狀態

$f(i, j)\equiv$ $S[1\cdots i]$ 中長度為 $j$ 的遞增子序列中，結尾最小是多少。 

## 舉例

$S=\{3, 6, 4, 8, 11, 1, 8\}$

| i & j | 1   | 2   | 3   |  4  |
|:-----:| --- | --- | --- |:---:|
|   1   | 3   | inf | inf | inf |
|   2   | 3   | 6   | inf | inf |
|   3   | 3   | 4   | inf | inf |
|   4   | 3   | 4   | 8   | inf |
|   5   | 3   | 4   | 8   | 11  |
|   6   | 1   | 4   | 8   | 11  |
|   7   | 1   | 4   | 8   | 11  |

## 性質

$f(i)$ 會是遞增的（除了 inf 以外）。
最佳子結構。

## 轉移

$$f(i, j) = \cases{\min{(f(i-1,j),\ a[i])} & If \(f(i-1,j-1) < a[i]\) \\ f(i-1, j) & Otherwise}$$

也就是說：

$$f(i, j) = \cases{a[i] & If \(f(i-1,j-1) < a[i]\) and $f(i-1,j) \ge a[i]$ \\ f(i-1, j) & Otherwise}$$

令 $k$ 是最大的數字使得 $f(i-1,k-1) < a[i]$。

* 對於所有 $t \ge k$，都有 $f(i-1, t) \ge a[i]$。
* 對於所有 $t < k$，都有 $f(i-1, t) < a[i]$。

因此，就只有 $k$ 滿足 $a[i] \ge f(i-1, k)$ 且 $f(i-1,k-1) < a[i]$。

$f(i)$、$f(i-1)$ 之間只會有一格改變。
那一格會是第一個 $k$ 使得 $f(i-1,k)\le a[i]$。
所以可以使用二分搜來找出那一格。

## 程式碼

```cpp=
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    vector<int> ans;
    for (int i = 1; i <= n; ++ i) {
        int x;
        cin >> x;
        auto it = lower_bound(ans.begin(), ans.end(), x);
        if (it == ans.end()) ans.push_back(x);
        else *it = x;
    }
    cout << (int)ans.size() << "\n";
}
```