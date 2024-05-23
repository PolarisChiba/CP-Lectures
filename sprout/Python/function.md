---
tags: 資訊之芽 語法班
---

# Python - Function

---

* Function
* 將一段程式碼包起來
* 可以針對其進行呼叫

---

* Example

```python=
def sleep():
    print('zzz')

sleep()
sleep()
```

---

* 好處
* 程式碼只要寫一次，就能重複使用
* 比較不容易出錯

---

* Function
* 可以呼叫（callable）的物件
* 可以傳參數（parameter）進去
* 可以有 return 的值，或是 ``None``

---

```python=
def sleep():
    print('zzz')

res = sleep()
print(res)
```

---

```python=
def plus(a, b):
    return a + b

res = plus(1, 2)
print(res)

print(plus(1 + 1, 2))
```

---

* Return value
* 可以回傳任何型別的資料
* 沒寫 return 的話會自動回傳 ``None``

---

* 將兩個資料以 tuple 包住來回傳

```python=
def DivMod(a, b):
    return a // b, a % b

x, y = DivMod(5, 2)
print(x)
print(y)
```

---

* 遇到 return 就會結束函式

```python=
def f(L):
    for i in L:
        if i == 0:
            print("woof")
            return False
    print("meow")
    return True

f([1, 2, 0, 3])
f([1, 2, 3, 4])

```

---

* Function 本身是一個物件
* 不建議亂動 python 內建的函式

```python=
output = print
output('hello')

print = input
output(print())
```

---

* parameter
* 有兩種方法可以傳參數
* 按照順序傳
* 按照名稱傳

---

* 按照順序傳
* 精簡的寫法

```python=
def output(a, b):
    print(b)
    print(a)
    
output(1 + 1, 3)
```

---

* 按照名稱傳
* 易讀、較不容易出錯

```python=
def output(first, second):
    print(second)
    print(first)

output(first = 1 + 1, second = 3)
output(second = 3, first = 1 + 1)
```

---

* Default Value
* 可以在定義 function 的時候預設參數的值
* Ex：input 函式的 prompt 參數預設為 ``None``

---

* 沒有傳參數的話，會使用預設值
* 反之有傳的話，會覆蓋掉預設值

```python=
def Tax(money, rate=0.5):
    return money * (1 + rate)

Tax(100)
Tax(100, 99)
```

---

* 有預設值的參數，必須放在沒有的後面

```python=
# Error
def Tax(money=1000, rate):
    return money * (1 + rate)
```

---

* 預設值只會在定義時被計算一次

```python=
import random
def randomNum(a = random.randint(1, 10000)):
    return a

for i in range(10):
    print(randomNum())
```

---

* 設定後就不會再改了

```python=
woof = "woof"
def shout(x = woof):
    print(x)

woof = "meow"
shout()
```

---

* 會輸出甚麼？

```python=
def Tax(money, rate = 0.5):
    print(money * (1 + rate))
    rate += 0.1
    
Tax(100)
Tax(100)
```

---

* 可變長度參數
* 不需要將參數包成 tuple 或 list

```python=
print(max(1, 2))
print(max(1, 2, 3))
print(max(1, 2, 3, 4))
```

---

* 可變長度參數
* 在參數前面打個 ``*``
* 傳進去的東西會轉成 tuple

```python=
def shout(*woof):
    print(type(woof))
    for i in woof:
        print(i)

shout("woof")
shout("woof", "meow")

shout(("woof", "meow"))
```

---

* 會輸出甚麼？

```python=
def shout(*woof):
    print(woof)

shout(("woof", "meow"))
```

---

* 拆解參數
* 將傳進去的參數，前面加上 ``*``

```python=
def shout(*woof):
    for i in woof:
        print(i)

woof = ("woof", "meow")
shout(woof)
shout(*woof)
```

---

* More Example

```python=
L = list(map(int, input().split()))
print(list(range(*L)))

A = (5, 1)
B = (4, 3, 2)
print(max(A, B))
print(max(*A, *B))
```

---

* 總結
* Function 是將一段程式碼包起來
* 可以接受參數
* 可以回傳資料

---

* 練習題 [neoj 3051](https://neoj.sprout.tw/problem/3051)
* 題目會輸入很多數字，最後會接一個字串 ``'num'`` 或 ``'str'``
* 若是 ``'num'``，則將輸入的數字加總後輸出
* 若是 ``'str'``，則將輸入的數字當成字串接起來輸出
* EX：
* 1 2 3 num $\rightarrow$ 6
* 1 2 3 4 5 str $\rightarrow$ 12345

---

* 範例解答

```python=
def plus(args):
    t = args[:-1]
    if args[-1] == 'str':
        return "".join(t)
    else:
        return sum(map(int, t))

print(plus(input().split()))
```

---

* Symbol Table
* 控制 global/local scope

---

* 會輸出甚麼？

```python=
a = 10

def f():
    print(a)

f()
```

---

* 會輸出甚麼？

```python=
a = 10

def f():
    a = 5
    print(a)

f()
```

---

* 會輸出甚麼？

```python=
a = 10

def f():
    print(a)
    a = 5

f()
```

---

* 每個物件都有自己的 symbol table
* 維護物件本身可以使用到的「symbol」
* 使用 ``dir()`` 函式可以查看 symbol table

---

* Example
* 會優先使用自己 symbol table 裡查到的

```python=
a = 10

def f():
    a = 5
    print(dir())

print(dir())
f()
```

---

* 如果在自己的 symbol table 找不到
* 就會往上一層去找
* 到了 global 還是找不到，就會有 Error

```python=
a = 10
def f():
    print(dir(), a)

print(dir())
f()
```

---

* 在函式中
* 變數 read、write 參照的 symbol table 要一致

```python=
a = 10

def f():
    print(a) # global
    a = 5 # local, Error

f()
```

---

* 可以使用 global 來指定使用 global 變數
* 那個變數就不會出現在 local 的 symbol table 中

```python=
a = 10

def f():
    global a
    print(a)
    a = 5
    print(dir())
    
f()
print(a)
```

---

* 不建議在函式中更改 global 變數的值
* 因為容易出錯、而且會讓架構變複雜

---

* 總結
* 用到的變數，會從 local 來找
* 找不到的話往 global 找
* 再找不到就是 Error

---

* 會輸出甚麼？

```python=
L = [1, 2, 3]
def f(L):
    del L[0]

f(L)
print(L)
```

---

* pass by reference
* import ctypes 後使用 id 可以查看 address

```python=
import ctypes

L = [1, 2, 3]

def f(L):
    del L[0]
    print(id(L))

print(id(L))
f(L)
```

---



```python=
import ctypes

a = 10

def f(a):
    a = 5
    print(id(a))

print(id(a))
f(a)
```

---

```python=
import ctypes

a = 10

def f(a):
    a = 10
    print(id(a))

print(id(a))
f(a)
```

---

* 總結
* 代號就只是代號
* 資料是存在記憶體的 address 上
* 重點是代號指向了哪個 address

---

* 練習題：[neoj 3005](https://neoj.sprout.tw/problem/3005)
* 輸出時請使用 ``print(ans, end='')``

---

* 範例解答

```python=
def price(money, rate):
    return money * rate

n = int(input())
ans = 0
max_price = -1

for i in range(n):
    money, rate = map(int, input().split())
    now_price = price(money, rate)
    if now_price < max_price or max_price == -1:
        ans = i
        max_price = now_price

print(ans, end='')
```

---

* 能不能按照 tuple 第二個值排序？

```python=
L = [('a', 3), ('b', 2), ('c', 1)]
M = L[:]
M.sort()
print(M)
```

---

* plug-in function

```python=
def cmp(tup):
    return tup[1]

L = [('a', 3), ('b', 2), ('c', 1)]
M = L[:]
M.sort(key=cmp)
print(M)
```

---

* lambda 表達式
* 匿名的函式
* ``lambda arg1, arg2, ...: expression``
* 等同於以下：

```python=
def f(arg1, arg2, ...):
    return expression
```

---

* 使用 lambda 可以讓程式更簡潔

```python=
L = [('a', 3), ('b', 2), ('c', 1)]
M = L[:]
M.sort(key=lambda tup: tup[1])
print(M)
```

---

* 搭配使用 map、lambda

```python=
L = [1, 2, 3]
print(list(map(lambda x: x**2, L)))
```

---

* map 可以接受多個參數
* 以下程式碼是否能改得更精簡？

```python=
A = [1, 2, 3]
B = [3, 2, 1]
C = [1, 3, 2]
print(list(map(lambda a, b, c: max(a, b, c), A, B, C)))
```

---

* 總結
* 善用 lambda 可以讓程式碼精簡
* 並且能夠使思考更高階

---

* Recursive Function 遞迴函式
* 重複呼叫函式自己

---

* Example

```python=
def recursive_hello(n):
    print(n)
    recursive_hello(n + 1)

recursive_hello(0)
```

---

* 遞迴函式需要一個終止條件
* 避免無限執行下去

---

* Example

```python=
def recursive_hello(n):
    if n == 10:
        return
    print(n)
    recursive_hello(n + 1)

recursive_hello(0)
```

---

* Recursive Function
* Base case：終止條件，然後 return
* Recursive case：呼叫（直接或間接）自己

---

* 要注意 Base case 是否會發生

```python=
def recursive_hello(n):
    if n == -1:
        return
    print(n)
    recursive_hello(n + 1)

recursive_hello(0) # Error
```

---

* 間接呼叫自己

```python=
def A(n):
    print(f"A{n}")
    B(n)

def B(n):
    if n == 0:
        return
    print(f"B{n}\n")
    A(n - 1)

A(10)
```

---

* Example 階乘
* $n!=1\times 2\times\cdots n$

```python=
def fac(n):
    if n == 1:
        return 1
    return n * fac(n - 1)

print(fac(10))
```

---

* 遞迴函式會使用 stack 來實作

---

* Example 費氏數列
* ~~效率很低落~~

```python=
def fib(n):
    if n == 0 or n == 1:
        return 1
    return fib(n - 1) + fib(n - 2)

print(fib(4))
```

---

* Example 計算元素數量

```python=
L = [1, [[2, 3], 4], [5, 6, 7]]
print(len(L))

def count_num(L):
    if type(L) != list:
        return 1
    
    c = 0
    for i in L:
        c = c + count_num(i)
    return c

print(count_num(L))
```

---

* 總結
* 遞迴就是重複自己本身
* 並且要注意必須會終止

---

* 練習題 [neoj 3403](https://neoj.sprout.tw/problem/3403/)
* 有點難，有興趣的同學可以自行挑戰。

---

* 回顧
* Function 的基本架構
* global/local scope
* pass by reference
* lambda 函式
* 遞迴函式

---

* $Thanks$