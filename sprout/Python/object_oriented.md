---
tags: 資訊之芽 語法班
---

# 物件導向

---

* 物件
* 泛指所有在程式中可以被變數代表的東西
* 正式來說，則是資料與其行為的包裝

---

* Python 中的物件
* 42
* [1, 3, 2]
* "Hello"
* {1, 2, "a"}
* {1: "Mon", 2: "Tues"}
* ...etc



---

* Python 中的物件
* 物件有其相對應的「行為」

```python=
print([1, 3, 2].index(2))
```

---

* class 即為製作物件的藍圖
* 定義物件型別的名稱
* 定義物件內有哪些資料
* 定義物件可以做出甚麼事情
* 定義物件是怎麼被製造出來的

---

* Python 中資料型別都是 class
* 內建型別：int、str、list
* import numpy
* 使用者自行定義

---

* 程序導向 VS 物件導向

```python=
L1 = [1, 3, 2]
print(sorted(L1))

L2 = [1, 3, 2]
L2.sorted()
print(L2)
```

---

* 物件導向：資料與其能做的事情
* 程序導向：函式描述資料間的交互作用

---

* 物件導向的好處
* 自行定義有意義的資料型別
* 程式碼的架構更好
* 可以創建許多實例

---

* 情境，你是廠商
* 客戶需要在二維平面上維護多邊形
* 包含長方形、圓形
* 需要能夠加入圖形、刪除圖形
* 需要能夠知道形狀的面積
* 並且能詢問圖形的形狀

---

* 程序導向

```python=
import math

rectangles = []
circles = []

def Shape(shape):
    if (shape in rectangles)
        return "rectangle"
    if (shape in circles)
        return "circle"
    return "none"

def Area(shape):
    if (shape in rectangles)
        return shape[0] * shape[1]
    if (shape in circles)
        return shape[0] * shape[0] * math.pi

def AddShape(shape):
    if (len(shape) == 2)
        rectangles.append(shape)
    if (len(shape) == 1)
        circles.append(shape)

def RemoveShape(shape):
    if (len(shape) == 2 and shape in rectangles)
        rectangles.remove(shape)
    if (len(shape) == 1)
        circles.remove(shape)
```

---

* 情境，你是廠商
* 客戶需要在二維平面上維護多邊形
* 包含長方形、圓形、「菱形」
* 需要能夠加入圖形、刪除圖形
* 需要能夠知道形狀的面積
* 並且能詢問圖形的形狀

---

* 物件導向

```python=
import math

class Rectangle:
    def __init__(self, w, h):
        self._w = w
        self._h = h
    def get_shape(self):
        return "rectangle"
    def get_area(self):
        return self._w * self._h
class Circle:
    def __init__(self, r):
        self._r = r
    def get_shape(self):
        return "cricle"
    def get_area(self):
        return self._r * self._r * math.pi
class Diamond:
    def __init__(self, w, h):
        self._w = w
        self._h = h
    def get_shape(self):
        return "diamond"
    def get_area(self):
        return self._w * self._h / 2
```

---

* 物件導向

```python=
import math

class Shape:
    def get_shape(self):
        pass
    def get_area(self):
        pass

class Rectangle(Shape):
    def __init__(self, w, h):
        self._w = w
        self._h = h
    def get_shape(self):
        return "rectangle"
    def get_area(self):
        return self._w * self._h
class Circle(Shape):
    def __init__(self, r):
        self._r = r
    def get_shape(self):
        return "cricle"
    def get_area(self):
        return self._r * self._r * math.pi
class Diamond(Shape):
    def __init__(self, w, h):
        self._w = w
        self._h = h
    def get_shape(self):
        return "diamond"
    def get_area(self):
        return self._w * self._h / 2
```

---

* 物件導向
* 維護圖形的 List

```python=
import math

class Shape:
    def get_shape(self):
        pass
    def get_area(self):
        pass

class Rectangle(Shape):
    def __init__(self, w, h):
        self._w = w
        self._h = h
    def get_shape(self):
        return "rectangle"
    def get_area(self):
        return self._w * self._h
class Circle(Shape):
    def __init__(self, r):
        self._r = r
    def get_shape(self):
        return "cricle"
    def get_area(self):
        return self._r * self._r * math.pi
class Diamond(Shape):
    def __init__(self, w, h):
        self._w = w
        self._h = h
    def get_shape(self):
        return "diamond"
    def get_area(self):
        return self._w * self._h / 2

class ShapeList:
    def __init__(self):
        self._shapelist = []
    def append(self, shape):
        if issubclass(type(shape), Shape):
            if shape not in self._shapelist:
                self._shapelist.append(shape)
    def remove(self, shape):
        if shape in self._shapelist:
            self._shapelist.remove(shape)
```

---

* 物件導向
* 容易擴充

```python=
import math

class Shape:
    def get_shape(self):
        pass
    def get_area(self):
        pass

class Rectangle(Shape):
    def __init__(self, w, h):
        self._w = w
        self._h = h
    def get_shape(self):
        return "rectangle"
    def get_area(self):
        return self._w * self._h
class Circle(Shape):
    def __init__(self, r):
        self._r = r
    def get_shape(self):
        return "cricle"
    def get_area(self):
        return self._r * self._r * math.pi
class Diamond(Shape):
    def __init__(self, w, h):
        self._w = w
        self._h = h
    def get_shape(self):
        return "diamond"
    def get_area(self):
        return self._w * self._h / 2

class ShapeList:
    def __init__(self):
        self._shapelist = []
    def append(self, shape):
        if issubclass(type(shape), Shape):
            if shape not in self._shapelist:
                self._shapelist.append(shape)
    def remove(self, shape):
        if shape in self._shapelist:
            self._shapelist.remove(shape)
    def size(self):
        return len(self._shapelist)
    def print(self):
        for shape in self._shapelist:
            print(shape.get_shape(), shape.get_area())
            print()
```

---

* 客戶不太會在意是如何實作的
* 廠商要提供的是「執行介面」
* 恰好這就是物件導向的長處

---

* 情境：客戶需要維護二維平面上的點
* 能建構點
* 能計算離原點的距離
* 在 iteractive mode 下有漂亮的表示法
* 能改變座標
* 能計算共有幾個點被造出來

---

* 建構點

```python=
class Point:
    def __init__(self, x, y):
        self._x = x
        self._y = y
```

---

* 離原點的距離

```python=
import math

class Point:
    def __init__(self, x, y):
        self._x = x
        self._y = y
    def r(self):
        return math.hypot(self._x, self._y)
```

---

* 表示法

```python=
import math

class Point:
    def __init__(self, x, y):
        self._x = x
        self._y = y
    def r(self):
        return math.hypot(self._x, self._y)
    def __repr__(self):
        return f"Point({self._x}, {self._y})"
```

---

* 改變座標

```python=
import math

class Point:
    def __init__(self, x, y):
        self._x = x
        self._y = y
    def r(self):
        return math.hypot(self._x, self._y)
    def __repr__(self):
        return f"Point({self._x}, {self._y})"
    def move_to(self, x, y):
        self._x = x
        self._y = y
    def move_by(self, dx, dy):
        self._x += dx
        self._y += dy
```

---

* property
* 讓 method 用起來像是屬性一樣
* 並且造出來的「屬性」是無法被修改的

```python=
import math

class Point:
    def __init__(self, x, y):
        self._x = x
        self._y = y
    @property
    def r(self):
        return math.hypot(self._x, self._y)
    def __repr__(self):
        return f"Point({self._x}, {self._y})"
    def move_to(self, x, y):
        self._x = x
        self._y = y
    def move_by(self, dx, dy):
        self._x += dx
        self._y += dy
```

---

* 想計算共有多少 Point 被造出來
* class 自身的屬性

```python=
import math

class Point:
    count = 0
    def __init__(self, x, y):
        self._x = x
        self._y = y
        self._serial = Point.count
        Point.count += 1
    @property
    def r(self):
        return math.hypot(self._x, self._y)
    def __repr__(self):
        return f"Point({self._x}, {self._y})"
    def move_to(self, x, y):
        self._x = x
        self._y = y
    def move_by(self, dx, dy):
        self._x += dx
        self._y += dy
```

---

* 將程式碼儲存到 ``Point.py``
* 客戶要用的時候 import Point
* 即可使用，而無須理解細節