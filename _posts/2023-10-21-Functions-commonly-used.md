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

$$
\begin{align*}
    \text{tổng} &= \text{số hạng} + \text{số hạng}  \\
                &= \text{hạng tử} + \text{hạng tử}  \\
                &= \text{số cộng} + \text{số cộng}
\end{align*}
$$

<!-- -------------------------------------------------------- -->
Phép trừ ($-$)

$$ \text{hiệu} = \text{số bị trừ} - \text{số trừ}  $$

<!-- -------------------------------------------------------- -->
Phép nhân ($\times$)

$$
\begin{align*}
    \text{tích} &= \text{thừa số} + \text{thừa số}  \\
                &= \text{nhân tử} + \text{nhân tử}
\end{align*}
$$

<!-- -------------------------------------------------------- -->
Phép chia ($\div$)

$$
    \text{phân số}
    = \text{thương}
    = \text{tỷ số}
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

$$
\begin{align*}
    a^xa^y  &= a^{x+y}  \\
    (ab)^x  &= a^xb^x   \\
    (a^x)^y &= a^{xy}   \\
    \frac{a^x}{a^y} &= a^{x-y}
\end{align*}
$$

Với $a > 0$, $b > 0$ và với mọi giá trị $x$ và $y$, với $p$ và $q$ là số nguyên, $q \neq 0$ ta có:

$$
\begin{align*}
    a^{p/q}         &= \sqrt[q]{a^p}            \\
    \frac{a^x}{b^x} &= \Big(\frac{a}{b}\Big)^x  \\
    a^{-x}          &= \frac{1}{a^x}            \\
    a^0             &= 1
\end{align*}
$$

## Hàm Logarit

Nếu $x = b^y$ thì $y$ được gọi là logarit cơ số $b$ của $x$ và:

$$ log_{\text{cơ số}}{\text{(số đối logarit)}} = log_b{x} = y $$

**Các phép toán với logarit**: Với $a,b,c > 0$, $a \neq 1$ và $r$ là số thực bất kì, ta có:

$$
\begin{align*}
    log_a(a^x)      &= x    \\
    a^{log_a(x)}    &= x    \\
    log_a(bc)       &= log_a(b) + log_a(c) \\
    log_a{\Big(\frac{b}{c}\Big)} &= log_a(b) - log_a(c) \\
    log_a(b^r)      &= rlog_a(b)    \\
\end{align*}
$$

**Logarit và số tự nhiên**: Hàm $log_e(x)$ còn được viết là $ln(x)$, hàm logarit của $e$ có một số tính chất sau:

$$
\begin{align*}
    ln(e)   &= log_e(e)   = 1    \\
    ln(e^5) &= log_e(e^5) = 5    \\
    ln(1)   &= log_e(1)   = 0
\end{align*}
$$

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
\begin{align*}
    \frac{\partial y}{\partial x_1}
    &= \frac{\partial}{\partial x_1}(5x_1 + 10x_1x_2 + 3(x_2)^2) \\[1ex]
    &= \frac{\partial}{\partial x_1}(5x_1) + \frac{\partial}{\partial x_1} (10x_1x_2) + \frac{\partial}{\partial x_1}(3(x_2)^2) \\[1ex]
    &= 5 + 10x_2 + 0 \\[1ex]
    &= 10x_2 + 5
\end{align*}
$$

$$ 
\begin{align*}
    \frac{\partial y}{\partial x_2}
    &= \frac{\partial}{\partial x_2}(5x_1 + 10x_1x_2 + 3(x_2)^2) \\[1ex]
    &= \frac{\partial}{\partial x_2}(5x_1) + \frac{\partial}{\partial x_2} (10x_1x_2) + \frac{\partial}{\partial x_2}(3(x_2)^2) \\[1ex]
    &= 0 + 10x_1 + 3.2x_2 \\[1ex]
    &= 10x_1 + 6x_2
\end{align*}
$$


## Ma trận - Các loại ma trận

Cho $m$, $n$ là các số nguyên dương. Một ma trận cấp $m \times n$ là một bảng số hình chữ nhật gồm $m.n$ số $a_{ij} \in \mathbb{R}$ ($i = 1, \dots, m; j = 1, \dots, n$) được xếp thành $m$ dòng và $n$ cột. Ta gọi $a_{ij}$ là giá trị nằm ở dòng thứ $i$ và cột thứ $j$. Ma trận thường được ký hiệu bởi các chữ in hoa $A, B, C, \dots$ như sau:

$$
A =
\begin{bmatrix}
a_{11} & a_{12} & \cdots & a_{1n} \\
a_{21} & a_{22} & \cdots & a_{2n} \\
\vdots & \vdots & \ddots & \vdots \\
a_{m1} & a_{m2} & \cdots & a_{mn}
\end{bmatrix}
= (a_{ij})_{m \times n}
$$

<!-- -------------------------------------------------------- -->
Với $m = 1$, ma trận ở thành `ma trận dòng`:

$$
A = (a_{ij})_{1 \times n} = 
\begin{bmatrix}
a_{11} & a_{12} & \cdots & a_{1n}
\end{bmatrix}
$$

<!-- -------------------------------------------------------- -->
Với $n = 1$, ma trận ở thành `ma trận cột`:

$$
A = (a_{ij})_{m \times 1} = 
\begin{bmatrix}
a_{11} \\
a_{21} \\
\vdots \\
a_{m1} 
\end{bmatrix}
$$

<!-- -------------------------------------------------------- -->
Với $m = n$, ma trận ở thành `ma trận vuông`:

$$
A =
\begin{bmatrix}
a_{11} & a_{12} & \cdots & a_{1n} \\
a_{21} & a_{22} & \cdots & a_{2n} \\
\vdots & \vdots & \ddots & \vdots \\
a_{n1} & a_{n2} & \cdots & a_{nn}
\end{bmatrix}
$$


<!-- -------------------------------------------------------- -->
Với $m = n$ và tất cả phần tử nằm ngoài đường chéo chính đều bằng 0, ma trận ở thành `ma trận chéo`:

$$
A =
\begin{bmatrix}
a_{11} &      0 & \cdots &      0 \\
     0 & a_{22} & \cdots &      0 \\
\vdots & \vdots & \ddots & \vdots \\
     0 &      0 & \cdots & a_{nn}
\end{bmatrix}
$$


<!-- -------------------------------------------------------- -->
Với $m = n$, tất cả phần tử nằm ngoài đường chéo chính đều bằng 0, và tất cả phần tử nằm trên đường chéo đều bằng 1, ma trận ở thành `ma trận đơn vị`, ký hiệu là $I_n$:

$$
I_n =
\begin{bmatrix}
     1 &      0 & \cdots &      0 \\
     0 &      1 & \cdots &      0 \\
\vdots & \vdots & \ddots & \vdots \\
     0 &      0 & \cdots &      1
\end{bmatrix}
$$


<!-- -------------------------------------------------------- -->
Với $m = n$, tất cả phần tử nằm dưới (hoặc nằm trên) đường chéo chính đều bằng 0, ma trận ở thành `ma trận tam giác`:

$$
A_{\text{tam giác trên}} =
\begin{bmatrix}
a_{11} & a_{12} & \cdots & a_{1n} \\
     0 & a_{22} & \cdots & a_{2n} \\
\vdots & \vdots & \ddots & \vdots \\
     0 &      0 & \cdots & a_{nn}
\end{bmatrix}

\: \text{hoặc} \:

A_{\text{tam giác dưới}} = 
\begin{bmatrix}
a_{11} &      0 & \cdots &      0 \\
a_{21} & a_{22} & \cdots &      0 \\
\vdots & \vdots & \ddots & \vdots \\
a_{n1} & a_{n2} & \cdots & a_{nn}
\end{bmatrix}

$$


## Phép toán trên Ma trận

<!-- -------------------------------------------------------- -->
**Phép cộng**

$$
\begin{bmatrix}
a_{11} & \cdots & a_{1n} \\
\vdots & \ddots & \vdots \\
a_{m1} & \cdots & a_{mn}
\end{bmatrix}

+

\begin{bmatrix}
b_{11} & \cdots & b_{1n} \\
\vdots & \ddots & \vdots \\
b_{m1} & \cdots & b_{mn}
\end{bmatrix}

=

\begin{bmatrix}
a_{11} + b_{11} & \cdots & a_{1n} + b_{1n} \\
         \vdots & \ddots &          \vdots \\
a_{m1} + b_{m1} & \cdots & a_{mn} + b_{mn}
\end{bmatrix}
$$

<!-- -------------------------------------------------------- -->
**Tích vô hướng**

$$
\lambda

.

\begin{bmatrix}
a_{11} & \cdots & a_{1n} \\
\vdots & \ddots & \vdots \\
a_{m1} & \cdots & a_{mn}
\end{bmatrix}

=

\begin{bmatrix}
\lambda a_{11} & \cdots & \lambda a_{1n} \\
        \vdots & \ddots &         \vdots \\
\lambda a_{m1} & \cdots & \lambda a_{mn}
\end{bmatrix}
$$

<!-- -------------------------------------------------------- -->
**Phép nhân ma trận**

Cho hai ma trận $$ A = (a_{ij})_{m \times n} \; \text{và} \; B = (b_{ij})_{n \times s} $$

Phép nhân chỉ thực hiện được khi số cột của $A$ bằng số dòng của $B$.

$$
\underbrace{
\begin{bmatrix}
a_{11} & a_{12} & \cdots & a_{1n}\\
\vdots & \vdots & \ddots & \vdots\\
a_{i1} & a_{i2} & \cdots & a_{in}\\
\vdots & \vdots & \ddots & \vdots\\
a_{m1} & a_{m2} & \cdots & a_{mn}
\end{bmatrix}
}_{m\times n}

\; \times \;

\underbrace{
\begin{bmatrix}
b_{11} & \cdots & b_{1j} & \cdots & b_{1s}\\
b_{21} & \cdots & b_{2j} & \cdots & b_{2s}\\
\vdots & \ddots & \vdots & \ddots & \vdots\\
b_{n1} & \cdots & b_{nj} & \cdots & b_{ns}
\end{bmatrix}
}_{n\times s}

=

\underbrace{
\begin{bmatrix}
c_{11} & \cdots & c_{1j} & \cdots & c_{1s}\\
\vdots & \ddots & \vdots & \ddots & \vdots\\
c_{i1} & \cdots & c_{ij} & \cdots & c_{is}\\
\vdots & \ddots & \vdots & \ddots & \vdots\\
c_{m1} & \cdots & c_{mj} & \cdots & c_{ms}
\end{bmatrix}
}_{m\times s}

$$

Với mỗi phần tử $c_{ij}$ là tổng các tích của dòng thứ $i$ của $A$ và cột thứ $j$ của $B$. Ta minh họa phép tính như sau:

$$
c_{ij}
=
\sum^{n}_{k=1} a_{ik}b_{kj}
=
a_{i1}b_{1j} + a_{i2}b_{2j} + \: \dots \: + a_{in}b_{nj}
$$


<!-- -------------------------------------------------------- -->
**Chuyển vị ma trận**

Ma trận chuyển vị của $A$ được ký hiệu là $A^T$.

Với $$A = (a_{ij})_{m \times n}$$ và $$A^T = (a'_{ij})_{n \times m}$$ thì $$a'_{ji} = a_{ij}$$ với mọi $i = 1, \dots, m$ và $j = 1, \dots, n$

Ví dụ:

$$
A =
\begin{bmatrix}
1 & 2 & 3 \\
4 & 5 & 6 \\
\end{bmatrix}

\; \text{thì} \;

A^T =
\begin{bmatrix}
1 & 4 \\
2 & 5 \\
3 & 5 \\
\end{bmatrix}

$$


<!-- -------------------------------------------------------- -->
**Nghịch đảo ma trận**

Cho trước ma trận vuông $A$ có $n$ cột và $n$ dòng, nếu tồn tại ma trận $A^{-1}$ thỏa điều kiện:

$$ AA^{-1} = A^{-1}A = I_n $$

Ta có 2 kết luận: 
- ma trận $A$ có thể nghịch đảo, và được gọi là ma trận khả nghịch
- ma trận $A^{1}$ được gọi là ma trận nghịch đảo của ma trận $A$

Để xác định ma trận nghịch đảo, đối với phương pháp tính tay và trong trường học, ta thường áp dụng phương pháp khử Gauss – Jordan:

$$
\underbrace{
\left[
\begin{array}{cccc|cccc}
a_{11} & a_{12} & \cdots & a_{1n} & 1 & 0 & \cdots & 0\\
a_{21} & a_{22} & \cdots & a_{2n} & 0 & 1 & \cdots & 0\\
\vdots & \vdots & \ddots & \vdots & \vdots & \vdots & \ddots & \vdots\\
a_{n1} & a_{n2} & \cdots & a_{nn} & 0 & 0 & \cdots & 1
\end{array}
\right]
}_{A \mid I_n}
\;
\xrightarrow{\text{Gauss--Jordan}}
\;
\underbrace{
\left[
\begin{array}{cccc|cccc}
1 & 0 & \cdots & 0 & b_{11} & b_{12} & \cdots & b_{1n}\\
0 & 1 & \cdots & 0 & b_{21} & b_{22} & \cdots & b_{2n}\\
\vdots & \vdots & \ddots & \vdots & \vdots & \vdots & \ddots & \vdots\\
0 & 0 & \cdots & 1 & b_{n1} & b_{n2} & \cdots & b_{nn}
\end{array}
\right]
}_{I_n \mid A^{-1}}
$$

Tổng quát hơn, ta thường áp dụng ma trận phụ hợp

$$ A^{-1} = \frac{1}{det(A)} A^{*}$$