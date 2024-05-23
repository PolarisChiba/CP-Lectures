---
tags: 資訊之芽 語法班
---

# Python - Algorithm

---

* Algorithm 演算法
* 解決問題的方法
* 由一連串運算，將輸入轉變為所要的輸出

---

* EX
* 有三十張考卷，請按照分數排序
* 給定航班時間，計算從台灣到匈牙利所需時間
* 詢問班上有幾個人身高高於 170 公分

---

* EX
* 計算 $a\sim b$ 中有多少數字不是 $c$ 的倍數

---

* EX
* 計算 $a\sim b$ 中有多少數字不是 $c$ 的倍數
* 輸入：$a, b, c\in Z^+$

```python=
a = int(input())
b = int(input())
c = int(input())
ans = 0
for i in range(a, b + 1):
    if i % c != 0:
        ans = ans + 1
print(ans)
```

---

* 分析演算法
* 好的演算法：正確、有效率、記憶體要求小
* 壞的演算法：！（好的演算法）

---

* EX
* 計算 $a\sim b$ 中有多少數字不是 $c$ 的倍數
* 請分析以下演算法

```python=
a = int(input())
b = int(input())
c = int(input())
ans = 0
for i in range(a, b + 1):
    if i % c != 0:
        ans = ans + 1
print(ans)
```

---

* EX
* 計算 $a\sim b$ 中有多少數字不是 $c$ 的倍數
* 請分析以下演算法

```python=
a = int(input())
b = int(input())
c = int(input())
interval = list(range(a, b + 1))
ans = 0
for i in interval:
    if i % c != 0:
        ans = ans + 1
print(ans)
```

---

* EX
* 計算 $a\sim b$ 中有多少數字不是 $c$ 的倍數
* 請分析以下演算法

```python=
a = int(input())
b = int(input())
c = int(input())
print((a + b - 1) * (c - 1) / c)
```

---

* EX
* 計算 $a\sim b$ 中有多少數字不是 $c$ 的倍數
* 請分析以下演算法

```python=
a = int(input())
b = int(input())
c = int(input())
print((b - a + 1) - a / c + (b - 1) / c)
```

---

* Model
* Random-Access Machine (RAM)
* 單次對記憶體存取僅需單位時間
* 指令會按照順序一個接一個執行

---

* 藉由分析演算法以比較其優劣
* 正確性、執行時間、空間大小？

---

* EX：GOOGLE MAP
* Which is better?
* 花十分鐘精確定位目前位置
* 花一秒定位，誤差為三公尺

---

* 重要性
* 正確性 $\approx$ 執行時間 $>$ 記憶體空間

---

* Which is better?
* 一秒執行完，$70\%$ 正確的演算法
* 一天執行完，$100\%$ 正確的演算法

---

* Running Time 執行時間
* 電腦執行演算法時所需要的「基本」指令數量
* 是一個以 input size 決定的函數
* 電腦大約一秒能夠執行 $10^8 \sim 10^9$ 個「基本」指令

---

* EX
* 以下演算法的執行時間（大概）為何？

```python=
a = int(input())
b = int(input())
c = int(input())
ans = 0
for i in range(a, b + 1):
    if i % c != 0:
        ans = ans + 1
print(ans)
```

---

* EX
* 以下演算法的執行時間（大概）為何？

```python=
L = list(range(1, 100))
print(max(L))
```

---

* 基本指令
* $+, -, \times, \div,$ memory access ... etc.
* 夠簡單的才算
* 或者能寫成一行機器語言的

---

```python=
L = range(1, 100) # 約要 100 個基本指令
L = list(L) # 約要 100 個指令
ans = max(L) # 約要 100 個指令
print(ans) # 約要 1 個指令
```

---

* EX 
* 以下演算法的執行時間（大概）為何？

```python=
a = int(input())
b = int(input())
c = int(input())
ans = 0
for i in range(a, b + 1):
    if i % c != 0:
        ans = ans + 1
print(ans)
```

---

* EX
* 請比較以下兩個演算法

```python=
A = []
L = [0] * 1000000
while len(L):
    A.append(L.pop(0))

A = []
L = [0] * 1000000
while len(L):
    A.append(L.pop())
```

---

* 以下演算法的執行時間（大概）為何？

```python=
L = list(map(int, input().split()))
L.sort()
print(L)
```

---

* 排序是怎麼做的？

---

* 排序
* 輸入：$n$ 個數字
* 輸出：$n$ 個數字由小到大排

---

* 選擇排序
* 找到最小的，放到最前面
* 對剩下的數字重複做同樣的事情

---

* 令 $n=|L|$
* 選擇排序的執行時間（大概）為何？

```python=
L = list(map(int, input().split())) # n
for i in range(len(L)): # n
    mn = i # n
    for j in range(i, len(L)): # ?
        if L[j] < L[mn]:
            mn = j
        else:
            break
    L[i], L[mn] = L[mn], L[i] # n
print(L) # 1
```

---

* 準確計算執行時間太繁雜了
* 估計即可（差不多就好）

---

* $\Theta$ notation：$f(n) = \Theta(g(n))$
* 存在 $c_1, c_2, n_0$ 使得對所有 $n\ge n_0$
* $0\le c_1 g(n)\le f(n)\le c_2 g(n)$

---

* $f(n) = \Theta(g(n))$ 
* 代表 $g(n)$ 長遠來看和 $f(n)$ 平手

---

* EX
* $2n+10000=\Theta(n)$
* $3n^2-6n=\Theta(n^2)$

---

* 小技巧
* 保留最大的項、並移除係數
* $3n^2-6n=\Theta(n^2)$

---

* 執行時間：$\Theta(n^2)$？

```python=
L = list(map(int, input().split())) # n
for i in range(len(L)): # n
    mn = i # n
    for j in range(i, len(L)): # <= n + (n - 1) + ... + 1
        if L[j] < L[mn]:
            mn = j
        else:
            break
    L[i], L[mn] = L[mn], L[i] # n
print(L) # 1
```

---

令 $n=|L|$

* 最好情況：$n = \Theta(n)$
* 最差情況：$\frac{n\times (n-1)}{2} = \Theta(n^2)$
* 平均情況：$\frac{n\times (n-1)}{4} = \Theta(n^2)$

---

* 還是太麻煩

---

* big-$O$ notation：$f(n) = O(g(n))$
* 存在 $c, n_0$ 使得對所有 $n\ge n_0$
* $0\le f(n)\le cg(n)$

---

* $f(n) = O(g(n))$ 
* 代表 $g(n)$ 長遠來看能夠壓制 $f(n)$

---

* EX
* $2n+10000=O(n^2)$
* $3n^2-6n=O(n^2)$
* $100\log{n}=O(n)$

---

* 執行時間：$O(n^2)$

```python=
L = list(map(int, input().split())) # n
for i in range(len(L)): # n
    mn = i # n
    for j in range(i, len(L)): # <= n + (n - 1) + ... + 1
        if L[j] < L[mn]:
            mn = j
        else:
            break
    L[i], L[mn] = L[mn], L[i] # n
print(L) # 1
``` 

---

* 執行時間是 $n^2$ 代表最差情況是 $O(n^2)$
* 這又被稱為「演算法的時間複雜度」

---

* 插入排序
* 每回合多考慮一個數字
* 並且插入（往前交換）到正確的位置

---

* 插入排序的執行時間為何？

```python=
L = list(map(int, input().split()))
for i in range(len(L)):
    for j in range(i - 1, -1, -1):
        if L[j] > L[j + 1]:
            L[j], L[j + 1] = L[j + 1], L[j]
        else:
            break
print(L)    
```

---

* 猴子排序
* 打亂並檢查是否排好
* 執行時間為何？

```python=
import random
L = list(map(int, input().split()))
while True:
    ok = True
    for i in range(len(L) - 1):
        if L[i] > L[i + 1]:
            ok = False
    if ok:
        break
    else:
        random.shuffle(L)
print(L)
```

---

* 泡沫排序
* 大的往後推、小的往前推
* 正確性？

```python=
L = list(map(int, input().split()))
for i in range(len(L)):
    for j in range(len(L) - 1):
        if L[j] > L[j + 1]:
            L[j], L[j + 1] = L[j + 1], L[j]
print(L)
```

---

* 桶子排序
* 將數值放到對應的桶子裡，再算每個數字出現幾次
* 時間複雜度？

```python=
L = list(map(int, input().split()))
bucket = [0] * 10
for i in L:
    bucket[i] = bucket[i] + 1
ans = []
for i, v in enumerate(bucket):
    ans.extend([i] * v)
print(ans)
```

---

* 練習
* 給定兩個由小到大排好的數列 $A$、$B$
* 請將兩個數列合併成一個由小到大排好的數列
* 並分析演算法的時間複雜度

---

* EX
* $A=\{1, 4, 5\}$
* $B=\{2, 3, 6\}$
* $\Rightarrow \{1, 2, 3, 4, 5, 6\}$

---

```python=
def Merge(A, B):
    C = A + B
    C.sort()
    return C
```

---

* 執行時間：還不知道

---

* 觀察
* 每次將 $A$、$B$ 最小的挑出來打架

---

```python=
def Merge(A, B):
    C = []
    while len(A) and len(B):
        if A[0] < B[0]:
            C.append(A.pop(0))
        else:
            C.append(B.pop(0))
    C.extend(A)
    C.extend(B)
    return C
```

---

* 執行時間：$O(|A|^2 + |B|^2)$

---

* 刪除太花時間了
* 改成挑最大的人出來打架

---

```python=
def Merge(A, B):
    C = []
    while len(A) and len(B):
        if A[-1] > B[-1]:
            C.append(A.pop())
        else:
            C.append(B.pop())
    C.extend(reversed(A))
    C.extend(reversed(B))
    C.reverse()
    return C
```

---

* 執行時間：$O(|A|+|B|)$

---

* 排序
* 輸入：長度為 $n$ 的數列 $L$
* 輸出：$L$ 中的數字由小到大排

---

* $n=1$
* 本身就是 sorted

---

* $n=2$
* ``Merge(L[0:1], L[1:2])``

---

* $n=4$
* ``Merge(``
    ``Merge(L[0:1], L[1:2]),``
    ``Merge(L[2:3], L[3:4])``
    ``)``

---

* Merge Sort
* 將數列拆成兩半
* 分別將兩邊排好（遞迴）
* 再將兩邊合併起來

---

```python!
def MergeSort(L):
    if len(L) == 1:
        return L
    mid = len(L) // 2
    Left = MergeSort(L[0 : mid])
    Right = MergeSort(L[mid : len(L)])
    return Merge(Left, Right)
```

---

* Merge Sort 時間複雜度
* $O(n\log{n})$

---

* 時間複雜度：$n\log{n}$？

```python!
L = list(map(int, input().split()))
L.sort()
print(L)
```

---

* 當 $n\le 30$ 的時候
* 插入排序是最有效率的，WHY？

---

* 計算時間複雜度的時候省略了常數
* 但常數依然存在，並且影響了效率

---

* $n$ 小的時候採用相對暴力的方法
* $n$ 大的時候採用 $n\log{n}$ 的演算法

```python!
L = list(map(int, input().split()))
L.sort()
print(L)
```

---

* $n\le 30$：$O(n^2)$？
* $n > 30$：$O(nlog{n})$？

```python!
L = list(map(int, input().split()))
L.sort()
print(L)
```

---

* 將 $\le 30$ 的情況看成常數
* 時間複雜度 $O(n\log{n})$

---

* 練習：計算以下運算的時間複雜度
```python!
# L : list
L.reverse()
L.pop(0)
L.pop(-1)
L.insert(0, 0)
L.insert(-1, 0)
L.extend(L)
```

---

* 練習：計算以下運算的時間複雜度
```python!
# s : set
s.add(3) # O(1) by hash
s.remove(3) # O(1) by hash
s = s1 | s2 # O(|s1| + |s2|)
s = s1 & s2 # O(min(|s1|, |s2|))
```

---

![](https://hackmd.io/_uploads/HyxlOOgwn.png =400x400)

---

* [各種排序影片](https://www.youtube.com/watch?v=kPRA0W1kECg)

---

* Thanks