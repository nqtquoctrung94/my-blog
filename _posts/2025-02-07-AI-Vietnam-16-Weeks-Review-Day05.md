---
title: Review cho AIO 2025 - Tuần 1 - Ngày 5
date: 2025 Feb 07
categories: [Algorithm, Python, AI Vietnam]
tags: [algorithm]
math: true
excerpt_separator: <!--excerpt-end-->
hidden: true
---

<!--excerpt-start-->
Nội dung ngày 5 trong 16 tuần Review trước khi vào học chương trình AIO 2025.
<!--excerpt-end-->

## Giới thiệu

Để theo dõi toàn bộ nội dung ôn tập, vui lòng tham khảo tại bài viết [16 tuần review cho AIO 2025]({% post_url 2025-02-01-AI-Vietnam-16-Weeks-Review %})

## Tuần 01 - Python Cơ bản

> Nội dung chính:<br>- **Lập trình**: Ôn tập về kỹ thuật lập trình với Python, cú pháp cơ bản (khai báo biến, vòng lặp, điều kiện), cách xây dựng hàm<br>- **Toán**: Sử dụng Python để cài đặt các công thức Toán cơ bản trong giải tích cơ bản
{: .prompt-info }

### Ngày 05: While-loop exercise

[Phương pháp Newton (Newton's Method)](https://en.wikipedia.org/wiki/Newton%27s_method), còn được gọi là phương pháp Newton-Raphson, là một phương pháp số học để tìm gần đúng của các nghiệm của một hàm số thực. Cụ thể, phương pháp này thường được sử dụng để tìm gần đúng của các nghiệm của phương trình $f(x) = 0$

Ngoài ứng dụng trong tìm nghiệm của một hàm số, phương pháp Newton còn có ứng dụng trong máy học (Machine Learning) trong việc tìm nghiệm của đạo hàm của hàm loss. Tuy nhiên đây là phương pháp không phổ biến bằng thuật toán gradient descent.

![Newton's Method light](/my-blog/assets/img/20250207-AI-Vietnam-16-Weeks-Review-Day05/newton-method-light.png){: .light }
![Newton's Method dark](/my-blog/assets/img/20250207-AI-Vietnam-16-Weeks-Review-Day05/newton-method-dark.png){: .dark }

Ở bài này, chúng ta sẽ dùng phương pháp Newton để tính căn bậc hai cho một số dương a. Chúng ta thực hiện các bước sau:
- Khởi tạo $x_0 = a$ với $a$ là số dương cần tính căn bậc hai
- Khởi tạo $n = 0$ để xác định số vòng lặp
- Khởi tạo $\epsilon$ gọi là ngưỡng sai số cho phép. Ta sẽ đặt một giá trị $\epsilon$ rất nhỏ làm điều kiện dừng cho vòng lặp.
- Xây dựng hàm $f(x) = x^2 - a$. Với mỗi vòng lặp, ta xem $x_n$ (ở bước đầu tiên là $x_0$) là lời giải cho bài toán.
- Cải thiện xấp xỉ $x_n$ bằng xấp xỉ $x_{n+1}$ theo công thức:
$$ x_{n+1} = x_n - \frac{f(x_n)}{f'(x_n)} $$
- So sánh $x_{n+1}$ và $x_n$:
  - Nếu $\lvert x_{n+1} - x_n \rvert < \varepsilon$, ta dừng quá trình lặp và trả về $x_{n+1}$ là nghiệm gần đúng của phương trình.
  - Nếu $\lvert x_{n+1} - x_n \rvert \geq \varepsilon$, ta tiếp tục thực hiện cải thiện xấp xỉ.

#### Bài tập

Cài đặt hàm find_square_root(a) tìm căn bậc hai cho một số $a$ bất kì với $\epsilon = 0.001$

{% highlight python %}
# Yêu cầu:
def find_square_root(a):
  """
  Find the square root of number a
  """
  EPSILON = 0.001
  ##### Your code here #####

# Output kỳ vọng:
find_square_root(2) -> 1.4142135623746899
find_square_root(3) -> 1.7320508100147276
{% endhighlight %}

<div style="padding: 15px; border-radius: 6px; border: 1px solid #e9ecef; margin: 20px 0;">
<details>
  <summary style="cursor: pointer; font-weight: bold">Đáp án (Click để xem)</summary>

<br>

Vì phương pháp Newton sử dụng cả giá trị hàm $f(x)$ và đạo hàm $f'(x)$. Ta tách riêng hai phép tính này thành hai hàm f(x) và f_dif(x). Khi đó, hàm find_square_root() sẽ chỉ tập trung vào việc thực hiện vòng lặp của thuật toán Newton.

Vậy ta có:
$$ f(x) = x^2 - a $$

{% highlight python %}
def f(x):
  return x*x - a
{% endhighlight %}

$$ f'(x) = 2x $$

{% highlight python %}
def f_dif(x,a):
  return 2*x
{% endhighlight %}

{% highlight python %}
def find_square_root(a):
  """
  Find the square root of number a
  """
  EPSILON = 0.001
  x_current = a
  while True:
    x_new = x_current - f(x_current,a)/f_dif(x_current)

    if abs(x_new - x_current) < EPSILON:
      break     # Thoát khỏi vòng lặp khi đã tìm được nghiệm
    
    x_current = x_new
  
  return x_new  
{% endhighlight %}

Một lời giải khác nếu không sử dụng hàm riêng cho $f(x)$ và $f'(x)$, và chúng ta lưu lại toàn bộ các bước cập nhật $x$:

{% highlight python %}
def find_square_root(a):
    """Find the square root of number a"""

    EPSILON = 0.001

    if a < 0:
        print("Square root of negative number is invalid")
        return None
    if a == 0:
        return 0
    if a > 0:
        base = 0
        update = a
        cache = [a]
        while abs(update - base) >= EPSILON:
            base = update
            update = base - (base**2 - a)/(2*base)
            cache.append(update)
        return cache
{% endhighlight %}

</details>
</div>


