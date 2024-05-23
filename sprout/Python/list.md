---
tags: 資訊之芽 語法班
---

# Python - List

---

* 我們已經學會如何處理大量資料了
* 那麼如果想要儲存大量的資料呢？

---

* List
* 可以裝許多資料的結構

---

* 使用中括號將資料包起來

```python=
L = [1, 2, 3]
print(L)
```

---

* 使用中括號來取出資料
* index 是從 $0$ 開始

```python=
L = [1, 2, 3]
print(L[1])
```

---

* 也可以修改 List 中的元素

```python=
L = [1, 2, 3]
L[1] = 'Sprout'
print(L)
```

---

* List 中的資料可以有不同型態

```python=
L = [False, 'False', 0]
print(type(L[0]))
print(type(L[1]))
print(type(L[2]))
```

---

* List 裡面也可以裝 List

```python=
L = ['a', ['b', 'c'], 'd']
print(type(L[0]))
print(type(L[1]))
print(type(L[2]))
```

---

* List 也可以是空的

```python=
L = []
print(L)
```

---

* 將 List1 塞到其他 List2 裡面

```python=
List1 = ['a', 'b', 'c']
List2 = [List1, 'd']
print(List1)
print(List2)
```

---

* List 是能儲存大量資料的結構
* 資料的型態可以不相同
* 資料是按順序儲存的
* 因此可以使用 index 來存取、修改

---

* 搭配 for-loop 來使用

```python=
L = ['a', ['b', 'c'], 'd']
for i in range(3):
    print(L[i])
```

---

* 要存取 List 中的元素可以利用中括號
* 另外，List 也支援使用中括號進行截取

```python=
L = [0, 1, 2, 3, 4, 5]
print(L[3])
print(L[1: 4])
```

---

* ``L[start: end]``
* 截取 List 中 $start\sim end - 1$ 的元素
* 並回傳一個 List 回來

---

* 也可以倒著截取

```python=
L = [0, 1, 2, 3, 4, 5]
print(L[4: 1: -1])
```

---

* ``L[start: end: step]``
* 從 start 開始
* 一次增加 step
* 直到 end 為止（不包含 end）

---

* ``L[start: end: step]``
* start 預設為 $0$
* end 預設為 List 的長度
* step 預設為 $1$

---

```python=
L = [0, 1, 2, 3, 4, 5]
print(L[: ])
print(L[1: ])
print(L[: 3])
print(L[: : 2])
```

---

* 如果存 List 結尾數回來，可以使用負數

```python=
L = [-5, -4, -3, -2, -1]
print(L[-1])
print(L[-4: -2])
print(L[-2: -4]) # empty
print(L[-5: -2: 2])
print(L[-2: -5: -2])
```

---

* 對資料的修改也可以使用 ``L[start: end]`` 語法

```python=
L = ['a', 'b', 'c']
L[0: 0] = [1, 2, 3]
print(L)
```

---

* 也可以透過 ``L[start: end]`` 的方式進行刪除

```python=
L = [0, 1, 2, 3, 4, 5]
L[1: 4] = []
print(L)
```

---

* ``L[strat: end: step]`` 也能夠對資料修改
* 強烈建議不要這樣做

```python=
L = ['a', 'b', 'c', 'd', 'e']
L[0: 5: 2] = [1, 2, 3]
print(L)
```

---

* List 支援加法運算
* 將兩個 List 接在一起

```python=
L = [1, 2, 3]
print(L + [4, 5, 6])
```

---

* List 支援乘法運算
* 乘多少就是複製幾遍

```python=
L = [1, 2, 3]
print(L * 3)
```

---

* 使用 in 可以判斷元素是否存在 List 內

```python=
L = [0, 1, 2, 3, 4, 5]
print('a' in L)
print('a' not in L)
print(1 in L)
```

---

* List 是 iterable 的
* 可以做為 for-loop 的對象

```python=
L = [0, 1, 2, 3, 4, 5]
for i in L:
    print(i)
```

---

* List 也可以由 iterabel 的物件來產生
* EX : 使用 range()、string 來產生 List

```python=
L = list(range(2, 11, 2))
print(L)
L = list('abcde')
print(L)
```

---

* ``[0, 1, 2]`` 和 ``range(0, 3)`` 的差別
* 在於前者是 List 的物件，並實際建立起來了
* 但是後者則不會實際建立，而是用到時才計算下一個值並回傳

---

* python 中有許多 fuction 或 method
* 可以對 List 進行操作

---

* ``len`` 可以取得 List 的長度

```python=
L = ['a', ['b', 'c'], 'd', [[[]]]]
print(len(L))
```

---

* 搭配 ``len`` 和 for-loop

```python=
L = [1, 2, 3, 4, 5, 6]
for i in range(len(L)):
    print(L[i])
```

---

* ``append(ojb)`` 將一個物件放到 List 最後方

```python=
L = [1, 2, 3]
L.append(4)
print(L)
```

---

* ``extend(List)`` 是延伸這個 List

```python=
L = [1, 2, 3]
L.extend([4, 5, 6])
print(L)
```

---

* ``append`` 與 ``extend`` 的比較

```python=
L1 = [1, 2, 3]
L1.append([4, 5, 6])
print(L1)

L2 = [1, 2, 3]
L2.extend([4, 5, 6])
print(L2)
```

---

* ``insert(index, obj)`` 是將物件插入到 index 前面

```python=
L = [0, 1, 2, 3, 4, 5]
L.insert(3, "Hello")
print(L)
```

---

* ``pop()`` 是刪除最後的元素並回傳

```python=
L = [0, 1, 2, 3, 4, 5]
print(L.pop())
print(L)
```

---

* ``pop(index)`` 是刪除特定位置的元素並回傳

```python=
L = [0, 1, 2, 3, 4, 5]
print(L.pop(3))
print(L)
print(L.pop(-2))
print(L)
```

---

* ``remove(obj)`` 移除第一個出現的 obj 元素

```python=
L = ['a', 'b', 'c', 'b']
L.remove('b')
print(L)
```

---

* ``remove`` 不能移除沒出現的元素
* 會產生 ValueError

```python=
L = ['a', 'b', 'c', 'b']
L.remove('z')
```

---

* ``clear`` 清空整個 List

```python=
L = [1, 2, 3]
L.clear()
print(L)
```

---

* ``reverse`` 將數列進行翻轉

```python=
L = [0, 1, 2, 3]
L.reverse()
print(L)
```

---

* ``reversed`` 會建立一個 iterator
* 但不會更動原本的 List

```python=
L = [0, 1, 2, 3]
print(reversed(L))
print(list(reversed(L)))
print(L)
```

---

* ``sort`` 可以將 List 排序
* 要求資料間能夠比大小

```python=
L1 = [2, 1, 4, 3]
L1.sort()
print(L1)

L2 = [1, [2, 3]]
L2.sort() # Error
```

---

* ``sorted`` 回傳排序好的 List
* 但不會更動原本的 List

```python=
L = [2, 1, 4, 3]
print(sorted(L))
print(L)
```

---

* ``index(obj, start, end)``
* 尋找 [start, end - 1] 內第一個等於 obj 的元素
* 但要求找的元素必須在 List 內

```python=
L = ['a', 'b', 'c', 'b']
print(L.index('b'))
print(L.index('b', 2))
print(L.index('b', 2, 4))
print(L.index('b', 2, 3)) #ValueError
```

---

* ``count(obj)`` 統計 obj 出現的次數

```python=
L = ['a', 'b', 'c', 'b']
print(L.count('b'))
```

---

* 會輸出甚麼？

```python=
L1 = [0, 1, 2, 3]
L2 = L1
L1[0] = 100
print(L1)
print(L2)
```

---

* 使用等於的話，兩個 List 會指向同個物件
* 換句話說，同個物件有著 L1、L2 兩個名字
* 再利用名字去修改物件

---

* 解決方法：``copy``、``L1[: ]``

```python=
L = [0, 1, 2, 3]
L1 = L
L2 = L.copy()
L3 = L[: ]

L[0] = 100
print(L1)
print(L2) 
print(L3)
```

---

* 同個概念也出現在 for-loop 中

```python=
L = [0, 1, 2, 3]

for i in L:
    i = 0
print(L)

for i in range(len(L)):
    L[i] = 0
print(L)
```

---

* ``max`` 回傳 List 內最大的元素
* ``min`` 回傳 List 內最小的元素
* ``sum`` 回傳 List 內元素的加總

```python=
L = [0, 1, 2, 3]
print(max(L), min(L), sum(L))
```

---

* 可以使用 ``enumerate`` 來生成 List 的 iterator

```python=
L = ['a', 'b', 'c', 'd']
enu = enumerate(L)
for i, j in enu:
    print(i, j)
```

---

* 可以搭配 ``split`` 函數來將輸入轉為 List

```python=
L = input().split()
print(L)
```

---

* 可以使用 ``map(func, obj)`` 函數來處理 List 內的元素

```python=
L = input().split()
print(L)

L = list(map(int, L))
print(L)
```

---

* 練習題
* [Sprout OJ 327](https://neoj.sprout.tw/problem/327/)

---

```python=
L = input().split()
for i in range(len(L)):
    print(L[len(L) - i - 1])
```

---

```python=
L = input().split()
for i in reversed(L):
    print(i)
```

---

```python=
L = input().split()
L.reverse()
for i in L: print(i)
```

---

* map 與 lambda 的搭配可以寫成一行
* 並且降低程式碼的可讀性，所以強烈不推薦

```python=
print(''.join(list(map(lambda x:x + '\n', reversed(input().split())))), end = '')
```

---

* 練習題
* [Sprout Oj 3032](https://neoj.sprout.tw/problem/3032/)

---

```python=
L = input().split()
L = list(map(int, L))
positive = 0
negative = 0
for i in L:
    if i > 0:
        positive = positive + i
    else:
        negative = negative + i
print(positive)
print(negative)
```

---

* 回家作業
* [Sprout OJ 2005](https://neoj.sprout.tw/problem/2005/)