---
tags: 資訊之芽 語法班
---

# Python - For-loop

---

複習：上週講過了 while。

```python=
i = 0
while i != 10:
    print(i)
    i = i + 1
```

---

使用 for-loop 來達成。

```python=
for i in range(10):
    print(i)
```

---

要處理的東西很規律時
就可以考慮使用 for-loop

---

* 對序列元素逐一執行
* 有個變數會隨之改變

```python=
for i in range(10):
    print(i)
```

---

* ``range()`` 函數
* 造出一個順序

---

* range(3) $\Rightarrow 0, 1, 2$
* range(2, 4) $\Rightarrow 2, 3$

---

給定首尾、輸出其中的整數

```python=
start = int(input())
end = int(input())
for i in range(start, end + 1):
    print(i)
```

---

* 小故事：高斯計算出 $1+2+\cdots+100$
* 請寫個程式計算 $a$ 到 $b$ 的總和。

---

$a$ 到 $b$ 的總和。

```python=
a = int(input())
b = int(input())
sum = 0
for i in range(a, b + 1):
    sum = sum + i
print(sum)
```

---

* 能不能造出反向的順序？
* EX：$3, 2, 1, 0$

---

解法一

```python=
for i in range(0, 4):
    print(3 - i)
```

---

解法二

```python=
for i in range(3, -1, -1):
    print(i)
```

---

* ``range()`` 也可以往下減
* EX：``range(2, -2, -1)`` $\Rightarrow 2, 1, 0, -1$

---

* ``range(start, end, step)``
* 從 $start$ 開始
* 一次增加 $step$
* 直到等於或超過 $end$

---

* EX: ``range(5, 0, -2)`` $\Rightarrow 5, 3, 1$

```python=
for i in range(5, 0, -2):
    print(i)
```

---

* ``range(start, end, step)``
* $start$ : 預設為 $0$
* $end$ : 一定要指定
* $step$ : 預設為 $1$，可正可負
* 都要是整數

---

* 也可以將 ``range()`` 想像成整數的等差數列

---

* 輸出 $1\sim 10$ 中的偶數
* 如何使用 for range 來得到？

---

* 從 $2$ 開始
* 一次加 $2$
* 直到等於或超過 $11$

```python=
for i in range(2, 11, 2):
    print(i)
```

---

* 和 ``while`` 一樣
* 可以搭配 if 等語法來使用

```python=
for i in range(1, 11):
    if i % 2 == 0:
        print(i)
```

---

* for-loop 與 while 的比較
* for-loop 通常用於規律的順序
* while 則用於不確定順序時，~~或是懶得想的時候~~

---

* 輸出 $1\sim 10$ 中的偶數

```python=
i = 1
while i <= 10:
    if i % 2 == 0:
        print(i)
    i = i + 1
```

---

* 練習題
* [Sprout OJ 3088](https://neoj.sprout.tw/problem/3088/)

---

```python=
n = int(input())
for i in range(1, n + 1):
    if i % 5 == 0:
        pass
    else:
        print(i)
```

---

```python=
n = int(input())
for i in range(1, n + 1):
    if i % 5 != 0:
        print(i)
```

---

* for-loop 裡面也可以有 for-loop
* EX: 印出三行 $0\ 1\ 2$

```python=
for i in range(3):
    for j in range(3):
        print(j, end=' ')
    print()
```

---

* 練習題
* [Sprout OJ 3089](https://neoj.sprout.tw/problem/3089/)

---

```python=
n = int(input())
for i in range(1, 10):
    if i == n:
        continue
    for j in range(1, 10):
        if j != n:
            print(str(i) + "*" + str(j) + "=" + str(i * j), end=' ')
    print()
```

---

* 練習題
* [Sprout OJ 3020](https://neoj.sprout.tw/problem/3020/)

---

解法一

```python=
n = int(input())
for i in range(1, n + 1):
    for j in range(1, i + 1):
        print("*", end="")
    print()
```

---

解法二

```python=
n = int(input())
for i in range(1, n + 1):
    print("*" * i)
```

---

* 所以說 ``range`` 到底會產生甚麼？

```python=
print(range(1, 3))
```

---

* iterable 可迭代的
* 意思是有一個特定的順序
* ``range(a, b)`` 會產生 $a\sim b-1$ 的 iterable 順序
* 因此變數才能夠逐一抓到下一個數字

```python=
a = int(input())
b = int(input())
for i in range(a, b):
    print(i)
```

---

* ``int`` 不是 iterable 的
* 以下 code 會造成 TypeError

```python=
for i in 3:
    print(i)
```

---

* 判斷物件是否為 iterable
* ``hasattr(object, '__iter__')``

```python=
print(hasattr(range(1, 3), '__iter__')) # True
print(hasattr(100, '__iter__')) # False
```

---

* 回家作業
* [Sprout OJ 3031](https://neoj.sprout.tw/problem/3031/)
* [Sprout OJ 3034](https://neoj.sprout.tw/problem/3034/)