---
title: Review cho AIO 2025 - Tuần 1 - Ngày 4
date: 2025 Feb 06
categories: [Algorithm, Python, AI Vietnam]
tags: [algorithm]
math: true
excerpt_separator: <!--excerpt-end-->
hidden: true
---

<!--excerpt-start-->
Nội dung ngày 4 trong 16 tuần Review trước khi vào học chương trình AIO 2025.
<!--excerpt-end-->

## Giới thiệu

Để theo dõi toàn bộ nội dung ôn tập, vui lòng tham khảo tại bài viết [16 tuần review cho AIO 2025]({% post_url 2025-02-01-AI-Vietnam-16-Weeks-Review %})

## Tuần 01 - Python Cơ bản

> Nội dung chính:<br>- **Lập trình**: Ôn tập về kỹ thuật lập trình với Python, cú pháp cơ bản (khai báo biến, vòng lặp, điều kiện), cách xây dựng hàm<br>- **Toán**: Sử dụng Python để cài đặt các công thức Toán cơ bản trong giải tích cơ bản
{: .prompt-info }

### Ngày 04: While Loop with continue and break keywords

- Trong Python, câu lệnh `while` được sử dụng để tạo một vòng lặp, trong đó các biểu thưucs được kiểm tra và nếu điều kiện đúng, khối mã lệnh bên trong vòng lặp sẽ được thực thi. Cách lệnh `break` và `continue` được sử dụng để kiểm soát luồng của vòng lặp

![While Loop with continue and break light](/my-blog/assets/img/20250205-AI-Vietnam-16-Weeks-Review-Day03/while-loop-with-continue-break-light.png){: .light }
![While Loop with continue and break dark](/my-blog/assets/img/20250205-AI-Vietnam-16-Weeks-Review-Day03/while-loop-with-continue-break-dark.png){: .dark }

- Câu lệnh `break` được sử dụng để thoát khỏi vòng lặp ngay lặp tức.
- Câu lệnh `continue` được sử dụng để bỏ qua phần còn lại của vòng lặp và chuyển đến lần lặp tiếp theo

#### Cú pháp

{% highlight python %}
while condition_1:
  # Thực hiện các lệnh bên trong vòng lặp
  if condition_2:
    continue
  # Thực hiện các lệnh còn lại bên trong vòng lặp nếu không thoải điều kiện condition_2
{% endhighlight %}


{% highlight python %}
while condition_1:
  # Thực hiện các lệnh bên trong vòng lặp
  if condition_2:
    break
  # Thực hiện các lệnh còn lại bên trong vòng lặp nếu không thoải điều kiện condition_2
{% endhighlight %}


#### Bài tập

Cài đặt hàm find_divisible_number(a) tìm số gnuyeen dương nhỏ nhất lớn hơn 100 và chia hết cho số nguyên dương a

{% highlight python %}
# Yêu cầu:
def find_divisible_number(a):
  """
  Find the smallest integer that is greater than 100 and divisible by the interger a
  """
  ##### Your code here #####

# Output kỳ vọng:
find_divisible_number(5) -> 105
find_divisible_number(17) -> 102
{% endhighlight %}

<div style="padding: 15px; border-radius: 6px; border: 1px solid #e9ecef; margin: 20px 0;">
<details>
  <summary style="cursor: pointer; font-weight: bold">Đáp án (Click để xem)</summary>
<br>

{% highlight python %}
def find_divisible_number(a):
  """
  Find the smallest integer that is greater than 100 and divisible by the interger a
  """
  # Bắt đầu từ 101 vì chúng ta chỉ xét số lớn hơn 100
  number = 101

  # Lặp lại vòng lặp cho đến khi kết quả phép chia có số dư bằng 0 => số chia hết cho a
  while True:
    if number % a == 0:
      break       # Nếu tìm thấy số chia hết cho a rồi thì thoát khỏi vòng lặp
    number += 1
  return number
{% endhighlight %}


</details>
</div>