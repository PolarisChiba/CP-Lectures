# 進階 DP

## 矩陣快速冪

$a^x=\cases{a^{x/2}\times a^{x/2} \\ a^{(x-1)/2}\times a^{(x-1)/2}\times a}$

$O(\log(x))$

### 費氏數列

$$
\begin{bmatrix}
0 & 1 \\
1 & 1 
\end{bmatrix} \begin{bmatrix}
F_i \\
F_{i+1}
\end{bmatrix}= \begin{bmatrix}
F_{i+1} \\
F_{i+2}
\end{bmatrix}
$$

$$
\begin{bmatrix}
0 & 1 \\
1 & 1 
\end{bmatrix}^{n-1} \begin{bmatrix}
F_1 \\
F_2
\end{bmatrix}= \begin{bmatrix}
F_n \\
F_{n+1}
\end{bmatrix}
$$

### 線性遞迴

$x_{i} = a_1\times x_{i-1} + a_2\times x_{i-2} + \cdots$

EX：
$x_{i} = 3\times x_{i-1}+2\times x_{i-2} + 3$

$$
\begin{bmatrix}
1 & 0 & 0 \\
0 & 0 & 1 \\
1 & 2 & 3
\end{bmatrix} \begin{bmatrix}
3 \\
x_{i-2} \\
x_{i-1}
\end{bmatrix}= \begin{bmatrix}
3 \\
x_{i-1} \\
x_{i}
\end{bmatrix}
$$

## 單調隊列

使用一個 deque 維護可能的答案。

陣列的$k$-區間最大值

k=3
[1, 4, 3, 1, 2, 2]

{1}
{4}
{4, 3}
...
```cpp
deque<int> d;
d.push_back(1); // 加入新元素
d.pop_back(); // 沒用的、被蓋過去的
d.pop_front(); //過期的
d.front() // 維護區間最大值
```

$O(2n)$

### 賣漢堡

> https://neoj.sprout.tw/problem/188/

\begin{align}
dp[i] &= val[i] + \max_{j=i-k\sim i-1} dp[j] - c(i - j) \\
&=val[i] - ci + \max_{j=i-k\sim i-1} dp[j] + cj
\end{align}

$dp[i]-val[i]+ci=\max_{j=i-k\sim i-1}dp[j]+cj=\max_{j=i-k\sim i-1} dp'[j]$

dp: dp[j]
dp': dp[j]+cj

### 烏龜疊疊樂 - 易

> https://neoj.sprout.tw/problem/185/

$$
dp[i] =\max_{j=i+1\sim i+k} dp[j] + S[j]
$$

### 有限背包問題

$O(NM)$

> https://neoj.sprout.tw/problem/159/

$N$ 個物品、總體積 $M$。

第 $i$ 個物品有 $k_i$ 個、體積 $w_i$、價值 $v_i$。

$$
dp[i][j] = \max_{t=0\sim k_i \\ t\times w_i \le j} dp[i-1][j-t\times w_i] + v_i\times t
$$

按照 $j \mod w_i$ 的值分類，去做單調隊列。

$j=8$
$w_i = 2$


|  dp[i]  |  0  |  1  | 2   | 3   | 4   | 5   | 6    |  7   |   8   |
|:-------:|:---:|:---:| --- | --- | --- | --- | ---- |:----:|:-----:|
| dp[i-1] |  0  |  1  | 20  | 31  | 420 | 531 | 6420 | 7531 | 86420 |


$dp[i][a\times w_i +b]-a\times v_i=\max_{t=\max(0, a-k_i)\sim a} dp[i-1][t\times w_i +b]-t\times v_i$

## 斜率優化

### 烏龜疊疊樂


> [TIOJ 1676](https://tioj.ck.tp.edu.tw/problems/1676)

\begin{align}
dp[i] &= \max_{j=i+1\sim i+k} dp[j] + S[j] -(j-i)^2 \\
&= \max_{j=i+1\sim i+k} dp[j] + S[j] - j^2 + 2ij - i^2\\
dp[i] + i^2 &= \max_{j=i+1\sim i+k} 2ij + (dp[j] + S[j] - j^2)
\end{align}

## 題目

[TIOJ 2053](https://tioj.ck.tp.edu.tw/problems/2053)
[zj 525](https://zerojudge.tw/ShowProblem?problemid=b525)
[TIOJ 1136](https://tioj.ck.tp.edu.tw/problems/1136)
[TIOJ 2017](https://tioj.ck.tp.edu.tw/problems/2017)
[CSES 1159](https://cses.fi/problemset/task/1159)
[neoj 159](https://neoj.sprout.tw/problem/159/)
[這場的 E](https://codeforces.com/gym/101986)
[CF 1715E]( https://codeforces.com/problemset/problem/1715/E)