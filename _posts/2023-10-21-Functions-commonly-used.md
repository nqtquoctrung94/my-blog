---
title: Các phép toán thường sử dụng
date: 2023 Oct 21
categories: [Algorithm]
tags: [algorithm]
math: true
excerpt_separator: <!--excerpt-end-->
---

<!--excerpt-start-->
Bài viết này để lưu lại các kiến thức về Đại số, Thuật toán mà mình đã học qua.
<!--excerpt-end-->


## Phép tính số học và tên gọi

<!-- -------------------------------------------------------- -->
Phép cộng ($+$)

$$\begin{align}
    \text{tổng} &= \text{số hạng} + \text{số hạng}  \\
                &= \text{hạng tử} + \text{hạng tử}  \\
                &= \text{số cộng} + \text{số cộng}
\end{align}$$

<!-- -------------------------------------------------------- -->
Phép trừ ($-$)

$$ \text{hiệu} = \text{số bị trừ} - \text{số trừ}  $$

<!-- -------------------------------------------------------- -->
Phép nhân ($\times$)

$$\begin{align}
    \text{tích} &= \text{thừa số} + \text{thừa số}  \\
                &= \text{nhân tử} + \text{nhân tử}
\end{align}$$

<!-- -------------------------------------------------------- -->
Phép chia ($\div$)

$$
    \begin{matrix} 
        \text{phân số} \\ 
        \text{thương} \\ 
        \text{tỷ số}  
    \end{matrix}
    = \frac{\text{số bị chia}}{\text{số chia}}
    = \frac{\text{tử số}}{\text{mẫu số}}
$$

<!-- -------------------------------------------------------- -->
Lũy thừa

$$ \text{lũy thừa} = {\text{cơ số}}^{\text{số mũ}}$$

<!-- -------------------------------------------------------- -->
Căn bậc n ($\sqrt[n]{}$)

$$ \text{căn} = \sqrt[\displaystyle \text{bậc}]{\text{số dưới căn}} $$

<!-- -------------------------------------------------------- -->
Logarit (log)

$$ \text{logarit} = log_{\text{cơ số}}{\text{(số đối logarit)}}$$



<!-- -------------------------------------------------------- -->
## Hàm lũy thừa $a^n$

$$ {\text{cơ số}}^{\text{số mũ}} = a^n  = \underbrace{a \times a \times \dots \times a}_\text{nhân n lần}$$

**Các tính chất thường sử dụng**

Với $a > 0$, $b > 0$ và với mọi giá trị $x$ và $y$, ta có:

$$ \begin{align}
    a^xa^y  &= a^{x+y}  \\
    (ab)^x  &= a^xb^x   \\
    (a^x)^y &= a^{xy}   \\
    \frac{a^x}{a^y} &= a^{x-y}
\end{align} $$

Với $a > 0$, $b > 0$ và với mọi giá trị $x$ và $y$, với $p$ và $q$ là số nguyên, $q \neq 0$ ta có:

$$ \begin{align}
    a^{p/q}         &= \sqrt[q]{a^p}            \\
    \frac{a^x}{b^x} &= \Big(\frac{a}{b}\Big)^x  \\
    a^{-x}          &= \frac{1}{a^x}            \\
    a^0             &= 1
\end{align} $$

## Hàm Logarit

Nếu $x = b^y$ thì $y$ được gọi là logarit cơ số $b$ của $x$ và:

$$ log_{\text{cơ số}}{\text{(số đối logarit)}} = log_b{x} = y $$

**Các phép toán với logarit**: Với $a,b,c > 0$, $a \neq 1$ và $r$ là số thực bất kì, ta có:

$$ \begin{align}
    log_a(a^x)      &= x    \\
    a^{log_a(x)}    &= x    \\
    log_a(bc)       &= log_a(b) + log_a(c) \\
    log_a{\Big(\frac{b}{c}\Big)} &= log_a(b) - log_a(c) \\
    log_a(b^r)      &= rlog_a(b)    \\
\end{align} $$

**Logarit và số tự nhiên**: Hàm $log_e(x)$ còn được viết là $ln(x)$, hàm logarit của $e$ có một số tính chất sau:

$$ \begin{align}
    ln(e)   &= log_e(e)   = 1    \\
    ln(e^5) &= log_e(e^5) = 5    \\
    ln(1)   &= log_e(1)   = 0
\end{align} $$

**Đổi cơ số logarit**: Với $a,b > 0$ và $a \neq 1$, $b \neq 1$:

$$log_a(x) = \frac{log_b(x)}{log_b(a)} $$

với mọi số thực $x > 0$

**Hàm logarit là hàm đơn điệu**: Với $x_1$, $x_2$:

$$x_1 \leq x_2 \ \implies log(x_1) \leq log(x_2) $$

## Đạo hàm một biến

Đạo hàm là một bước rất quan trọng của hầu hết các thuật toán tối ưu trong Học máy và Học sâu.

**Định nghĩa của đạo hàm**

Giả sử ta có hàm $f(x)$, đạo hàm của $f$ được định nghĩa là

$$ f'(x) = \lim_{h \to 0} \frac{f(x+h) - f(x)}{h}$$

nếu giới hạn lim tồn tại. 

**Tính chất của đạo hàm**

Cho $y = f(x)$, trong các tài liệu , các cách viết sau là tương đương nhau:

$$
    f'(x) 
    = y' 
    = \frac{dy}{dx} 
    = \frac{df}{dx} 
    = \frac{d}{dx}f(x) 
    = Df(x) 
    = D_x f(x) 
$$

- $DC = 0$ (với $C$ là hằng số)
- $De^x = e^x$
- $Dln(x) = \frac{1}{x}$


Một số quy tắc:

- Quy tắc luỹ thừa: 

$$(x^n)' = n.x^{n-1}$$

- Quy tắc nhân hằng số: 

$$[Cf(x)]' = C.f(x)' $$

- Quy tắc tổng: 

$$[f(x) + g(x)]' = f(x)' + g(x)'$$

- Quy tắc nhân: 

$$[f(x)g(x)]' = f(x)'g(x) + f(x)g(x)'$$

- Quy tắc đạo hàm phân thức:

$$\bigg[ \frac{f(x)}{g(x)} \bigg]' = \frac{ f(x)'g(x) + f(x)g(x)' }{ g(x)^2 }  $$

## Đạo hàm riêng cho hàm nhiều biến

Với $y = f(x_1, x_2, \dots, x_n)$ là hàm có $n$ biến. Đạo hàm riêng của $y$ theo $x_i$ là

$$\frac{\partial y}{\partial x_i} = \lim_{h \to 0} \frac{f(x_1, \dots,x_{i-1}, x_i + h, x_{i+1} \dots, x_n) - f(x_1, \dots, x_i, \dots, x_n)}{h} $$

Đối với đạo hàm theo $x_i$, ta có thể xem các giá trị $x_1, \dots, x_n$ (không bao gồm $x_i$) là các hằng số, và tính đạo hàm $y$ theo $x_i$

Các ký hiệu đạo hàm riêng sau có ý nghĩa tương đương:

$$
    \frac{\partial y}{\partial x_i} 
    = \frac{\partial f}{\partial x_i} 
    = f_{x_i}
    = f_i
    = D_i f
    = D_{x_i} f
$$

Ví dụ:

Giả sử ta có phương trình 

$$y = f(x_1, x_2)= 5x_1 + 10x_1x_2 + 3(x_2)^2$$

Đạo hàm của $y$ theo $x_1$ và $x_2$ lần lượt là:

$$ 
\begin{align}
    \frac{\partial y}{\partial x_1}
    &= \frac{\partial}{\partial x_1}(5x_1 + 10x_1x_2 + 3(x_2)^2) \\[1ex]
    &= \frac{\partial}{\partial x_1}(5x_1) + \frac{\partial}{\partial x_1} (10x_1x_2) + \frac{\partial}{\partial x_1}(3(x_2)^2) \\[1ex]
    &= 5 + 10x_2 + 0 \\[1ex]
    &= 10x_2 + 5
\end{align}
$$

$$ 
\begin{align}
    \frac{\partial y}{\partial x_2}
    &= \frac{\partial}{\partial x_2}(5x_1 + 10x_1x_2 + 3(x_2)^2) \\[1ex]
    &= \frac{\partial}{\partial x_2}(5x_1) + \frac{\partial}{\partial x_2} (10x_1x_2) + \frac{\partial}{\partial x_2}(3(x_2)^2) \\[1ex]
    &= 0 + 10x_1 + 3.2x_2 \\[1ex]
    &= 10x_1 + 6x_2
\end{align}
$$
