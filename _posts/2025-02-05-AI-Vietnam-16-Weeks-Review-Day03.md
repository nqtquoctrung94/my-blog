---
title: Review cho AIO 2025 - Tuần 1 - Ngày 3
date: 2025 Feb 05
categories: [Algorithm, Python, AI Vietnam]
tags: [algorithm]
math: true
excerpt_separator: <!--excerpt-end-->
hidden: true
---

<!--excerpt-start-->
Nội dung ngày 3 trong 16 tuần Review trước khi vào học chương trình AIO 2025.
<!--excerpt-end-->

## Giới thiệu

Để theo dõi toàn bộ nội dung ôn tập, vui lòng tham khảo tại bài viết [16 tuần review cho AIO 2025]({% post_url 2025-02-01-AI-Vietnam-16-Weeks-Review %})

> Nội dung chính của tuần 1:<br>
- **Lập trình**: Ôn tập về kỹ thuật lập trình với Python, cú pháp cơ bản (khai báo biến, vòng lặp, điều kiện), cách xây dựng hàm
- **Toán**: Sử dụng Python để cài đặt các công thức Toán cơ bản trong giải tích cơ bản
{: .prompt-info }

## Ngày 03: Cấu trúc vòng lặp while-loop

### Mô tả
- Sự ngẫu nhiên là một đặc điểm cơ bản của các hiện tượng trong thực tế. Nó thể hiện qua việc kết quả của một thí nghiệm không thể dự đoán trước được một cách chính xác. **Ví dụ:** Chọn ngẫu nhiên hai số a và b sao cho tổng của $a + b$ bằng 40, câu hỏi đặt ra rằng, chúng ta phải tạo ngẫu nhiên bao nhiêu lần để thỏa mãn điều kiện trên?

- **Cấu trúc vòng lặp While-loop:** Vòng lặp while là một cấu trúc điều khiển trong Python cho phép thực thi một khối mã nhiều lần miễn là điều kiện cho trước vẫn còn đúng. Cấu trúc câu lệnh như sau:

### Cú pháp

{% highlight python %}
while condition:
  # Thực hiện các lệnh bên trong vòng lặp
{% endhighlight %}

### Bài tập: về sự ngẫu nhiên - Dùng vòng lặp While

- Chọn ngẫu nhiên hai số a và b thuộc từ 1 đến 20 sao cho tổng của $a + b$ bằng 40, câu hỏi đặt ra rằng, chúng ta phải tạo ngẫu nhiên bao nhiêu lần để thỏa mãn điều kiện trên?

{% highlight python %}
# Yêu cầu:
import random

def random_number_with_condition(total):
  # Set a random value that is the same between devices
  random.seed(0)
  ##### Your code here #####

# Output kỳ vọng:
random_number_with_condition(40) -> 266 lần
random_number_with_condition(20) -> 32 lần
random_number_with_condition(35) -> 96 lần
{% endhighlight %}

<div style="padding: 15px; border-radius: 6px; border: 1px solid #e9ecef; margin: 20px 0;">
<details>
  <summary style="cursor: pointer; font-weight: bold">Đáp án (Click để xem)</summary>

<br>

{% highlight python %}
import random

def random_number_with_condition(total):
  # Set a random value that is the same between devices
  random.seed(0)
  a = 0
  b = 0
  random_times = 0

  while a + b != total:
    a = random.randint(1,20)
    b = random.randint(1,20)
    random_times += 1
  
  print(f"{random_times} lần")
{% endhighlight %}

hoặc chúng ta có thể trình bày như sau

{% highlight python %}
import random

def random_number_with_condition(total):
  random.seed(0) # Để giá trị ngẫu nhiên giữa các máy đều như nhau
  random_times = 0
  sum = 0

  while(sum != total):
    x1 = random.randint(1,20)
    x2 = random.randint(1,20)

    sum = x1 + x2
    random_times += 1

  print(f"{random_times} lần")
{% endhighlight %}

</details>
</div>


