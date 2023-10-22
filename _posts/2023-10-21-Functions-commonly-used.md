---
title: Các tính chất và phép toán thường sử dụng
date: 2023 Oct 21
categories: [Algorithm, Math Function]
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
    ln(e)   &= log_e(e)   &= 1    \\
    ln(e^5) &= log_e(e^5) &= 5    \\
    ln(1)   &= log_e(1)   &= 0
\end{align} $$

**Đổi cơ số logarit**: Với $a,b > 0$ và $a \neq 1$, $b \neq 1$:

$$log_a(x) = \frac{log_b(x)}{log_b(a)} $$

với mọi số thực $x > 0$

**Hàm logarit là hàm đơn điệu**: Với $x_1$, $x_2$:

$$x_1 \leq x_2 \ \implies log(x_1) \leq log(x_2) $$