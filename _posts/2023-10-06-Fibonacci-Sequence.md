---
title: Về dãy số Fibonacci
date: 2023 Oct 06
categories: [Math, Fibonacci Sequence]
tags: [math, fibonacci, matrix]
math: true
excerpt_separator: <!--excerpt-end-->
---

<!--excerpt-start-->
Bài viết này sẽ trình bày về chuỗi Fibonacci và các thuật toán trong Python để tìm số trong chuỗi Fibonacci ở vị trí cho trước. Mình cũng sẽ thảo luận về hiệu suất và khả năng xử lý của các thuật toán này.
<!--excerpt-end-->


## Giới thiệu
Dãy số Fibonacci là một dãy số quen thuộc bắt đầu bằng chuỗi:

$$ 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89 \dots$$

Số thứ $n$ trong dãy số Fibonacci được kí hiệu là $F_n$ hoặc $F(n)$ (trong bài viết này sẽ dùng cả 2 cách viết), ta có $F_0 = 0$ và $F_1 = 1$, và với $n > 1$:

$$F_n = F_{n-1} + F_{n-2}$$

Ví dụ với n = 4: <br>
$ F_4 = F_3 + F_2 = 2 + 1 = 3 $

![Fibonacci Sequence light](/assets/img/fibonacci-sequence/fibonacci-sequence-light.png){: .light }
![Fibonacci Sequence dark](/assets/img/fibonacci-sequence/fibonacci-sequence-dark.png){: .dark }

## Tìm số Fibonacci tại vị trí n

### Sử dụng vòng lặp

#### Ý tưởng
Ta có thể tạo một phương trình vòng lặp đơn giản với ý tưởng như sau:
- Bước 1: Bắt đầu với `a = 0` và `b = 1`
    - Lúc này a là $F_0$, b là $F_1$
- Bước 2: Cập nhật giá trị a thành $F_1$ và b thành giá trị tiếp theo $F_2 = F_1 + F_0$
- Bước 3: Tiếp tục lặp lại bước 2 đến khi a là giá trị $F_n$ cần tìm
- Bước 4: Trả về a

#### Thuật toán

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

#### Giới thiệu phương trình Binet

Phương trình Binet tính giá trị của $F_n$ như sau:

$$ F_n = \frac{1}{\sqrt{5}}\Bigg(\bigg(\frac{1 + \sqrt{5}}{2}\bigg)^{n} - \bigg(\frac{1 - \sqrt{5}}{2}\bigg)^{n}\Bigg) $$


Đặt tỉ lệ vàng $\varphi = \dfrac{1 + \sqrt{5}}{2}$ <br>
Ta cũng có thể biến đổi $\dfrac{1 - \sqrt{5}}{2} = 1 - \varphi = -\dfrac{1}{\varphi} = -\varphi^{-1} $

Phương trình có thể viết rút gọn thành:

$$ F_n = \frac{\varphi^{n} - (-\varphi)^{-n} }{\sqrt{5}} = \frac{\varphi^n - (-\varphi)^{-n}}{2\varphi - 1} $$

#### Thuật toán

```python
def fibonacci_binet_formula(n: int) -> int:
    phi = (1 + 5**(1/2))/2  # phi là ký hiệu của tỉ lệ vàng
    fibo_n = ( phi**n - (-phi)**(-n) )/(2*phi - 1)
    return int(fibo_n)
```

#### Thuật toán (phiên bản rún gọn)

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

> Phương trình Binet cần tính toán chính xác với số thập phân, và Python có một số [hạn chế trong việc lưu trữ giá trị thập phân](https://docs.python.org/3/tutorial/floatingpoint.html) dẫn đến khả năng sai số khi tính các số Fibonacci lớn. Vì vậy trong thực tế sẽ ít được sử dụng.
{: .prompt-danger }


### Sử dụng hàm đệ quy

#### Ý tưởng

Hàm đệ quy đi tìm $F_n$ bằng cách truy ngược về giá trị ban đầu là $F_1$ và $F_0$, ta có:

$$ \begin{aligned}
F_n &= F_{n-1} + F_{n-2} \\
F_{n-1} &= F_{n-2} + F_{n-3} \\
F_{n-2} &= F_{n-3} + F_{n-4} \\
&\dots \\
F_3 &= F_2 + F_1 \\
F_2 &= F_1 + F_0 \\
\end{aligned} $$

Thay $F_1 = 1$ và $F_0 = 0$, như vậy từ đấy ta tính ngược lên các giá trị $F_3, F_4, \dots$, ta tìm được giá trị $F_n$

#### Thuật toán

Code python khi triển khai rất gọn
```python
def fibonacci_recursive(n: int) -> int:
    if n <= 1:
        return n # fib(0) = 0 và fib(1) = 1
    return fibonacci_recursive(n-1) + fibonacci_recursive(n-2)
```

> Tuy nhiên, cách làm này tốn rất nhiều tài nguyên của máy và bị lặp lại phép tính nhiều lần.
{: .prompt-danger }

#### Thuật toán (cải tiến)

Để cải thiện thuật toán, ta sẽ lưu trữ các giá trị đã tính toán, để tránh phải lặp lại nhiều lần.

Sau đây là code đệ quy tham khảo từ trang [realpython.com](https://realpython.com/fibonacci-sequence-python/#optimizing-the-recursive-algorithm-for-the-fibonacci-sequence)

```python
cache = {0: 0, 1: 1}    # Tạo cache để lưu trữ, mặc định có F0=0, F1=1

def fibonacci_recursive(n: int) -> int:
    if n in cache:      # Kiểm tra xem vị trí này đã được tính chưa
        return cache[n]
    cache[n] = fibonacci_recursive(n-1) + fibonacci_recursive(n-2)
    return cache[n]
```

> Việc sử dụng hàm đệ quy để tính toán sẽ tạo ra rất nhiều vòng lặp, dẫn đến tình trạng tràn bộ nhớ `stack overflow`, và đối với hàm này thì máy của mình không thể chạy được với n > 2933
{: .prompt-warning }

### Sử dụng ma trận

#### Dạng ma trận của số Fibonacci

Ta có thể tìm số Fibonacci tại vị trí n, $F(n)$, trong phép tính sau:

$$
\begin{bmatrix}
    1 & 1 \\
    1 & 0
\end{bmatrix} ^ {n}
=
\begin{bmatrix}
    F(n+1) & F(n) \\
    F(n) & F(n-1)
\end{bmatrix}
$$

Để tìm $F(n)$, ta có thể luỹ thừa ma trận $\begin{bmatrix} 1 & 1 \\ 0 & 1 \end{bmatrix}$ đến bậc n. Nội dung bên dưới sẽ cố gắng chứng minh phương trình này trước khi đi vào code ứng dụng.

#### Chứng minh trực tiếp

Trước khi suy luận phương trình trực tiếp, ta cần thống nhất rằng ở đây [dãy số Fibonacci có thể mở rộng theo chiều âm](https://en.wikipedia.org/wiki/Generalizations_of_Fibonacci_numbers#Extension_to_negative_integers). Từ phương trình:

$$ F(n+1) = F(n) + F(n-1) $$

Ta có hệ phương trình như sau:

$$ \begin{aligned}
    \begin{cases}
        F(n+1) &= F(n) + F(n-1) \\
        F(n) &= F(n)
    \end{cases}
\end{aligned} $$

Hệ phương trình này tương đương với phép tính ma trận sau:

$$\begin{aligned}
    \begin{bmatrix}
        F(n+1) \\
        F(n)
    \end{bmatrix}
    &= 
    \begin{bmatrix}
        1 & 1 \\
        1 & 0
    \end{bmatrix}
    \begin{bmatrix}
        F(n) \\
        F(n-1)
    \end{bmatrix} \\[2ex] 

    &= 
    \begin{bmatrix}
        1 & 1 \\
        1 & 0
    \end{bmatrix}

    \begin{bmatrix}
        1 & 1 \\
        1 & 0
    \end{bmatrix}

    \begin{bmatrix}
        F(n-1) \\
        F(n-2)
    \end{bmatrix} \\[2ex] 

    &= 
    \begin{bmatrix}
        1 & 1 \\
        1 & 0
    \end{bmatrix} ^ {2}

    \begin{bmatrix}
        F(n-1) \\
        F(n-2)
    \end{bmatrix} \\[2ex] 

    &= 
    \begin{bmatrix}
        1 & 1 \\
        1 & 0
    \end{bmatrix} ^ {3}

    \begin{bmatrix}
        F(n-2) \\
        F(n-3)
    \end{bmatrix} \\

    &\dots \\
    
    &= 
    \begin{bmatrix}
        1 & 1 \\
        1 & 0
    \end{bmatrix} ^ {n}

    \begin{bmatrix}
        F(1) \\
        F(0)
    \end{bmatrix} \;\;\; (I) \\

\end{aligned}$$

Tương tự ta cũng có:

$$  
\begin{bmatrix}
    F(n) \\
    F(n-1)
\end{bmatrix}
= 
\begin{bmatrix}
    1 & 1 \\
    1 & 0
\end{bmatrix} ^ {n}
\begin{bmatrix}
    F(0) \\
    F(-1)
\end{bmatrix} \;\;\; (II)
$$

Thay $F(-1) = 1$, $F(0) = 0$, $F(1) = 1$ vào phương trình $(I)$ và $(II)$, ta có hệ:

$$ \begin{aligned}
    \begin{cases}

        \begin{bmatrix}
            F(n+1) \\
            F(n)
        \end{bmatrix}
        &= 
        \begin{bmatrix}
            1 & 1 \\
            1 & 0
        \end{bmatrix} ^ {n}

        \begin{bmatrix}
            1 \\
            0
        \end{bmatrix} \\[2ex]

        \begin{bmatrix}
            F(n) \\
            F(n-1)
        \end{bmatrix}
        &= 
        \begin{bmatrix}
            1 & 1 \\
            1 & 0
        \end{bmatrix} ^ {n}

        \begin{bmatrix}
            0 \\
            1
        \end{bmatrix} \\

    \end{cases}
\end{aligned} $$

Sử dụng tính chất sau:

$$
\begin{cases}
    a = Mb \\
    c = Md
\end{cases}

\implies

\begin{bmatrix}
a \\ 
c
\end{bmatrix}
=
M
\begin{bmatrix}
b \\ 
d
\end{bmatrix}
$$

Ta được:

$$
\begin{bmatrix}
    F(n+1) & F(n) \\
    F(n) & F(n-1)
\end{bmatrix}
=
\begin{bmatrix}
    1 & 1 \\
    1 & 0
\end{bmatrix} ^ {n}
\begin{bmatrix}
    1 & 0 \\
    0 & 1
\end{bmatrix}
=
\begin{bmatrix}
    1 & 1 \\
    1 & 0
\end{bmatrix} ^ {n}
$$

Sau khi tối giản ma trận đơn vị, ta có được phương trình cần chứng minh.

#### Chứng minh bằng quy nạp

Với $n = 1$, ta có: $$\begin{bmatrix} 1 & 1 \\ 1 & 0 \end{bmatrix} = \begin{bmatrix} F(2) & F(1) \\ F(1) & F(0) \end{bmatrix}$$

Giả sử mệnh đề đúng với với $n \geq 1 $, tức là:

$$\begin{bmatrix} 
1 & 1 \\ 
1 & 0 
\end{bmatrix} ^ {n}
= 
\begin{bmatrix} 
F(n+1) & F(n) \\ 
F(n) & F(n-1) 
\end{bmatrix}$$

Ta cần chứng minh mệnh đề đúng với $n+1$, ta xét:

$$
\begin{align}
\begin{bmatrix} 
1 & 1 \\ 
1 & 0 
\end{bmatrix} ^ {n+1}

&= \begin{bmatrix} 
1 & 1 \\ 
1 & 0 
\end{bmatrix} ^ {n}
\begin{bmatrix} 
1 & 1 \\ 
1 & 0 
\end{bmatrix} \\[2ex]

&= \begin{bmatrix} 
F(n+1) & F(n) \\ 
F(n) & F(n-1) 
\end{bmatrix}
\begin{bmatrix} 
1 & 1 \\ 
1 & 0 
\end{bmatrix} \\[2ex]

&= \begin{bmatrix} 
F(n+1) + F(n) & F(n+1) + 0 \\ 
F(n) + F(n-1) & F(n) + 0
\end{bmatrix} \\[2ex]

&= \begin{bmatrix} 
F(n+2) & F(n+1) \\ 
F(n+1) & F(n)
\end{bmatrix}

\end{align}
$$

Vậy mệnh đề đúng với mọi số nguyên n

#### Thuật toán ứng dụng


### Sử dụng phương pháp fast doubling (tạm dịch tính nhanh bình phương)

## Các nguồn tham khảo
- Algorithms for Competitive Programming:
    - [Fibonacci Numbers](https://cp-algorithms.com/algebra/fibonacci-numbers.html)
- Wikipedia:
    - [Fibonacci Sequence](https://en.wikipedia.org/wiki/Fibonacci_sequence)
    - [Generalizations of Fibonacci numbers](https://en.wikipedia.org/wiki/Generalizations_of_Fibonacci_numbers#Extension_to_negative_integers)
- Art of Problems Solving:
    - [Binet Formula](https://artofproblemsolving.com/wiki/index.php/Binet%27s_Formula)
- Proof Wiki:
    - [Cassini's Identity](https://proofwiki.org/wiki/Cassini%27s_Identity/Lemma) (Fibonacci Q-Matrix)
- Math World:
    - [Fibonacci Number](https://mathworld.wolfram.com/FibonacciNumber.html)
    - [Fibonacci Q-Matrix](https://mathworld.wolfram.com/FibonacciQ-Matrix.html)

Hình ảnh được tạo bằng công cụ [Figma](https://www.figma.com/) <br>
Ảnh động được tạo bằng công cụ [ezgif.com](https://ezgif.com/)