---
title: Về dãy số Fibonacci
date: 2023 Oct 06
categories: [Math, Fibonacci Sequence]
tags: [math, fibonacci]
math: true
excerpt_separator: <!--end_summary-->
---

Bài viết này giới thiệu về dãy số Fibonacci và các thuật toán để tìm số trong chuỗi tại một vị trí được cho trước.

<!--end_summary-->

## Giới thiệu
Dãy số Fibonacci là một dãy số quen thuộc bắt đầu bằng chuỗi:

$$ 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89 \dots$$

Số thứ $n$ trong dãy số Fibonacci được kí hiệu là $F_n$, ta có $F_0 = 0$ và $F_1 = 1$, và với $n > 1$:

$$F_n = F_{n-1} + F_{n-2}$$

Ví dụ với n = 4: <br>
$ F_4 = F_3 + F_2 = 2 + 1 = 3 $

![Minh hoạ dãy số Fibonacci](/assets/img/fibonacci-sequence/fibonacci-sequence-sample.png)

## Tìm số Fibonacci tại vị trí n

### Sử dụng vòng lặp
Ta có thể tạo một phương trình vòng lặp đơn giản với ý tưởng như sau:
- Bước 1: Bắt đầu với `a = 0` và `b = 1`
    - Lúc này a là $F_0$, b là $F_1$
- Bước 2: Cập nhật giá trị a thành $F_1$ và b thành giá trị tiếp theo $F_2 = F_1 + F_0$
- Bước 3: Tiếp tục lặp lại bước 2 đến khi a là giá trị $F_n$ cần tìm
- Bước 4: Trả về a

```python
def fibonacci_linear_loop(n: int) -> int:
    a = 0
    b = 1
    for loop in range(n):
        next_fibonacci = a + b
        a = b
        b = next_fibonacci
    return a
```

> Python cho phép cập nhật nhiều giá trị cùng một lúc. Vì thế, ta có thể viết lại code ở dạng tối giản hơn.
{: .prompt-tip }

```python
# Từ
a = 0
b = 1

# Sẽ trở thành
a, b = 0, 1
```

Và ta cũng không cần giá trị trung gian `next_fibonacci` trong vòng lặp nữa
```python
# Từ
next_fibonacci = a + b
a = b
b = next_fibonacci

# Sẽ trở thành
a, b = b, a + b
```

Thay vào code ban đầu, ta có:
```python
def fibonacci_linear_loop(n: int) -> int:
    a, b = 0, 1
    for loop in range(n):
        a, b = b, a + b
    return a
```

### Sử dụng phương trình Binet

Phương trình Binet tính giá trị của $F_n$ như sau:

$$ F_n = \frac{1}{\sqrt{5}}\Bigg(\bigg(\frac{1 + \sqrt{5}}{2}\bigg)^{n} - \bigg(\frac{1 - \sqrt{5}}{2}\bigg)^{n}\Bigg) $$


Đặt tỉ lệ vàng $\varphi = \dfrac{1 + \sqrt{5}}{2}$ <br>
Ta cũng có thể biến đổi $\dfrac{1 - \sqrt{5}}{2} = 1 - \varphi = -\dfrac{1}{\varphi} = -\varphi^{-1} $

Phương trình có thể viết rút gọn thành:

$$ F_n = \frac{\varphi^{n} - (-\varphi)^{-n} }{\sqrt{5}} = \frac{\varphi^n - (-\varphi)^{-n}}{2\varphi - 1} $$

```python
def fibonacci_binet_formula(n: int) -> int:
    phi = (1 + 5**(1/2))/2  # phi là ký hiệu của tỉ lệ vàng
    fibo_n = ( phi**n - (-phi)**(-n) )/(2*phi - 1)
    return int(fibo_n)
```

Ta nhận xét rằng giá trị $ \Bigg\| \bigg(\dfrac{1 - \sqrt{5}}{2} \bigg)^{\displaystyle n} \Bigg\| < 1 $, và giá trị này tiến rất nhanh về $0$ khi $n$ tăng. Vì thế, ta có thể tính vắn tắt giá trị $F_n$ theo:

$$ F_n = \Bigg[ \frac{ \big(\frac{1 +\sqrt{5}}{2}\big)^{n}} {\sqrt{5}} \Bigg] = \Bigg[ \frac{\varphi^{n}}{2\varphi - 1} \Bigg] $$

Với ngoặc vuông [ ] là phép làm tròn đến giá trị nguyên gần nhất.

Đoạn mã python cho phương trình vắn tắt

```python
def fibonacci_binet_formula_short(n: int) -> int:
    sqrt5 = 5**(1/2)
    fibo_n = ((1 + sqrt5)/2)**n / sqrt5
    return int(round(fibo_n))

# Hoặc
def fibonacci_binet_formula_short(n: int) -> int:
    phi = (1 + 5**(1/2))/2  # phi là ký hiệu của tỉ lệ vàng
    fibo_n = (phi**n)/(2*phi - 1)
    return int(round(fibo_n))
```

> Phương trình Binet cần tính toán với số thập phân, dẫn đến khả năng sai số. Vì thế trong thực tế sẽ ít được sử dụng.
{: .prompt-danger }


### Sử dụng hàm đệ quy

Đây có lẽ là hàm được mọi người thích dùng nhất


## Các nguồn tham khảo
- [Algorithms for Competitive Programming](https://cp-algorithms.com/algebra/fibonacci-numbers.html)
- [Wikipedia](https://en.wikipedia.org/wiki/Fibonacci_sequence)
- [Art of Problems Solving](https://artofproblemsolving.com/wiki/index.php/Binet%27s_Formula)


Hình ảnh được mình tạo bằng công cụ [Figma](https://www.figma.com/) <br>
Ảnh động (gif) được mình tạo bằng công cụ [ezgif.com](https://ezgif.com/)