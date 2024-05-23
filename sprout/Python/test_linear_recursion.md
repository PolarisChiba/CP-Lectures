---
tags: 資訊之芽 語法班
---

# Python班2023認證考 - linear recursion

## 題目敘述

在此題中，我們稱呼線性遞迴是滿足以下條件的數列：

$$
F_i=\begin{cases}
1 & \text{If } 1\le i \le m \\
a_1\times F_{i-1} + a_2\times F_{i-2}+\cdots + a_m\times F_{i-m} & \text{Otherwise}
\end{cases}
$$

舉例來說，對於費氏數列來說，就是 $m=2$、$a_1 = a_2 = 1$ 的線性遞迴數列。

現在給你 $a_1\sim a_m$，還有一個正整數 $n$，請計算 $F_n$。

## 輸入說明

輸入包含兩行。

第一行會有一個數列，代表 $a_1, a_2, \cdots, a_m$，保證此數列長度 $\le 5$、並且 $0\le a_i\le 10$。

第二行會有一個正整數，代表 $n$，保證 $1\le n\le 20$。

## 輸出說明

請輸出 $F_n$。

### Sample input 1

```
1 1
8
```

### Sample output 1

```
21
```

### Sample input 2

```
1 2 3
10
```

### Sample output 2

```
861
```



