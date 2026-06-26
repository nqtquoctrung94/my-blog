---
title: Review cho AIO 2025 - Tuần 1 - Ngày 2
date: 2025 Feb 04
categories: [Algorithm, Python, AI Vietnam]
tags: [algorithm]
math: true
excerpt_separator: <!--excerpt-end-->
hidden: true
---

<!--excerpt-start-->
Nội dung ngày 2 trong 16 tuần Review trước khi vào học chương trình AIO 2025.
<!--excerpt-end-->

## Giới thiệu

Để theo dõi toàn bộ nội dung ôn tập, vui lòng tham khảo tại bài viết [16 tuần review cho AIO 2025]({% post_url 2025-02-01-AI-Vietnam-16-Weeks-Review %})

## Tuần 01 - Python Cơ bản

> Nội dung chính:<br>- **Lập trình**: Ôn tập về kỹ thuật lập trình với Python, cú pháp cơ bản (khai báo biến, vòng lặp, điều kiện), cách xây dựng hàm<br>- **Toán**: Sử dụng Python để cài đặt các công thức Toán cơ bản trong giải tích cơ bản
{: .prompt-info }

### Ngày 02: Cấu trúc vòng lặp for-loop

Vòng lặp for-loop trong Python được sử dụng để lặp qua các phần tử trong một chuỗi (sequence) như danh sách, chuỗi ký tự, tuple, từ điển (dictionary) hoặc dải giá trị số (range).

#### Cú pháp

{% highlight python %}
for variable in sequence:
  # Thực hiện các lệnh bên trong vòng lặp
{% endhighlight %}

#### Ví dụ

{% highlight python %}
# Ví dụ 1: Lặp qua một danh sách
numbers = {1, 2, 3, 4, 5}
for n in numbers:
  print(n)

# Output
1
2
3
4
5
{% endhighlight %}

{% highlight python %}
# Ví dụ 2: Lặp qua một dải số
for i in range(5):
  print(i)

# Output, range(5) tạo ra các số từ 0 đến 4
0
1
2
3
4
{% endhighlight %}

{% highlight python %}
# Ví dụ 3: Lặp qua một chuỗi ký tực
for char in "Python":
  print(char)

# Output
P
y
t
h
o
n
{% endhighlight %}

#### Bài tập 1: Tính lãi suất tiền gửi ngân hàng

Số $e$ (hay còn gọi là hằng số Euler) là một số vô tỷ xuất hiện trong nhiều lĩnh vực toán học và khoa học, bao gồm cả lĩnh vực tài chính. Trong ngân hàng, số $e$ được sử dụng để tính lãi suất kép, một phương pháp tính lãi suất trong đó tiền lãi được cộng vào số tiền gốc để tính lãi cho các kỳ hạn tiếp theo. Công thức tổng quát của số $e$ như sau:

$$e = \lim_{n \to \infty} \left(1 + \frac{1}{n} \right)^{n}$$

Giả sử: chúng ta có 1 dollar, và gởi vào ngân hàng và được nhận lãi mỗi ngày, vậy điều gì sẽ xảy ra nếu chúng ta gởi trong 1 năm, số tiền nhận được là bao nhiêu? Để trả lời câu hỏi này, chúng ta sẽ áp dụng:
- Bước 1: Tiền nhận được sau 1 ngày gửi là: $1 + \frac{1}{365}
- Bước 2: lặp lại cách tình này cho 1 năm, ta được công thức của e là: $\left(1 + \frac{1}{n} \right)^{n}$

{% highlight python %}
# Yêu cầu:
def compute_interest(money, period):
  ##### Your code here #####

# Output kỳ vọng:
compute_interest(1, 12) -> 2.613
compute_interest(1, 365) -> 2.714
compute_interest(1, 730) -> 2.716
{% endhighlight %}

<div style="padding: 15px; border-radius: 6px; border: 1px solid #e9ecef; margin: 20px 0;">
<details>
  <summary style="cursor: pointer; font-weight: bold">Đáp án (Click để xem)</summary>

<br>
Đầu tiên để tránh hiểu lầm, phương trình cơ bản cho lãi suất kép được phát biểu như sau:<br>

$$ \text{A} = \text{P} \left(1 + \frac{r}{n}\right)^{nt} $$

Với:<br>
- $A$ là số tiền nhận cuối kỳ (tổng cả gốc lẫn lãi)<br>
- $P$ là số tiền gửi ban đầu<br>
- $r$ là lãi suất hằng năm<br>
- $t$ là thời gian gửi theo năm<br>
- $n$ là số lần tiền lãi được gộp vào gốc trong năm<br>
<br>
Bài toán của chúng ta cần tính theo các giá trị mặc định sau:<br>
- Tiền đưa vào $P = 1$ dollar<br>
- Lãi suất hằng năm $r = 100\% = 1$<br>
- Trong thời gian $t = 1$ năm<br>
- Được nhận lãi mỗi ngày, vậy tương ứng với gửi 15 ngày thì tiền lãi được gộp 15 lần, tương đương $n = 15$<br>
<br>
Rút gọn phép tính với các giá trị mặc định, ta có:<br>

$$ \text{A} = \text{P} \left(1 + \frac{r}{n}\right)^{nt} = 1 \cdot \left(1 + \frac{1}{n}\right)^{n \cdot 1} = \left(1 + \frac{1}{n}\right)^{n} $$

{% highlight python %}
def compute_interest(money, period):
  result = 1
  for i in range(period):
    result = result*(1 + 1/period)
  return result
{% endhighlight %}

Tại đây, chúng ta cũng có một tính chất đặc biệt của số $e$ là:

$$e = \lim_{n \to \infty} \left(1 + \frac{1}{n} \right)^{n} = \sum_{n=0}^{\infty} \frac{1}{n!} = 1 + \frac{1}{1!} + \frac{1}{2!} + \frac{1}{3!} + ... $$

Cho nên cũng có một cách giải khác như sau:

{% highlight python %}
import math

def compute_interest(money, period):
  result = 0
  for i in range(period):
    result = result + money/ math.factorial(i)
  return result
{% endhighlight %}

</details>
</div>

#### Bài tập 2: Thuật toán sàng số nguyên tố Eratosthenes

Thuật toán sàng số nguyên tố Eratosthenes (Sieve of Eratosthenes) là một trong những phương pháp cổ để sàng lọc toàn bộ số nguyên tố trong khoảng $[1, n]$.

{% highlight text %}
Algorithm: Kiểm tra số nguyên tố sử dụng sàng Eratosthenes
Require: Một số nguyên n >= 0
Ensure: Trả về True nếu n là số nguyên tố, ngược lại trả về False

 1: if n < 2 then
 2:   return False                      # Số nhỏ hơn 2 không phải là số nguyên tố
 3: end if
 4: Tạo một danh sách prime với n + 1 phần tử, tất cả được gắn True
 5: Gán prime[0] và prime[1] là False   # 0 và 1 không phải số nguyên tố
 6: for i = 2 do
 7:   if prime[i] = True then
 8:                                     # Đánh dấu tất cả các bội số của i từ i^2 đến n
 9:     for j = i^2 to n step i do
10:       prime[j] = False              # j là bội số của i, không phải số nguyên tố
11:     end for
12:   end if
13: end for
14: return prime[n]

{% endhighlight %}


{% highlight python %}
# Yêu cầu:
def is_prime_eratosthenes(n):
  ##### Your code here #####

# Output kỳ vọng:
is_prime_eratosthenes(7) -> True
is_prime_eratosthenes(10) -> False
is_prime_eratosthenes(2) -> True
is_prime_eratosthenes(1) -> False
{% endhighlight %}

<div style="padding: 15px; border-radius: 6px; border: 1px solid #e9ecef; margin: 20px 0;">
<details>
  <summary style="cursor: pointer; font-weight: bold">Đáp án (Click để xem)</summary>

{% highlight python %}
def is_prime_eratosthenes(n):
    if n < 2:
        return False
    
    # Create a boolean array "is_prime[0..n]" and initialize
    # all entries it as true. A value in is_prime[i] will
    # finally be false if i is Not a prime, else true.
    is_prime = [True] * (n + 1)
    is_prime[0] = is_prime[1] = False
    
    # Use Sieve of Eratosthenes to mark non-prime numbers as false
    for i in range(2, int(math.sqrt(n)) + 1):
        if is_prime[i]:
            # Update all multiples of i
            for j in range(i * i, n + 1, i):
                is_prime[j] = False
    
    return is_prime[n]
{% endhighlight %}

Thực tế, chúng ta cũng có thể làm một logic kiểm tra số nguyên tố đơn giản là xét tất cả các số từ 1 đến $\sqrt{n}$ xem $n$ có chia hết cho số nào không. Nếu có số mà n chia hết, thì đây không phải số nguyên tố.

{% highlight python %}
def is_prime(n):
    if n < 2:
        return False
    
    # Check divisibility up to square root of n
    for i in range(2, int(n ** 0.5) + 1):
        if n % i == 0:
            return False
            
    return True
{% endhighlight %}

</details>
</div>