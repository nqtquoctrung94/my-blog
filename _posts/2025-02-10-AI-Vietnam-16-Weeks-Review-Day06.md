---
title: Review cho AIO 2025 - Tuần 2 - Ngày 6
date: 2025 Feb 10
categories: [Algorithm, Python, AI Vietnam]
tags: [algorithm]
math: true
excerpt_separator: <!--excerpt-end-->
hidden: true
---

<!--excerpt-start-->
Nội dung ngày 6 trong 16 tuần Review trước khi vào học chương trình AIO 2025.
<!--excerpt-end-->

## Giới thiệu

Để theo dõi toàn bộ nội dung ôn tập, vui lòng tham khảo tại bài viết [16 tuần review cho AIO 2025]({% post_url 2025-02-01-AI-Vietnam-16-Weeks-Review %})

> Nội dung chính của tuần 2:<br>
- **Lập trình**: Danh sách (list), tuple, từ điển (dictionary), tập hợp (set) trong Python
- **Cấu trúc dữ liệu**: Làm quen với Ngắn xếp (stack), hàng đợi (queue)
- **Toán**: Ứng dụng cấu trúc dữ liệu để giải các bài toán số học (ví dụ: Convert text to vector using BoW, đo độ tương đồng cosine giữa các vector, etc). Làm quen với các giải thuật DSA cơ bản như Giải thuật tìm kiếm (tuyến tính, nhị phân) và sắp xếp (bubble sort, selection sort)
{: .prompt-info }

## Ngày 06: List Creation and Accessing

### Mô tả
List là một kiểu dữ liệu cơ bản trong Python, được sử dụng để lưu trữ tập hợp các phần tử có thứ tự. List có thể chứa bất kỳ kiểu dữ liệu nào, bao gồm số nguyên, chuỗi, số thập phân, danh sách con, v.v.

Đặc điểm của List:
- **Có thứ tự**: Các phần tử trong list được sắp xếp theo thứ tự nhất định.
- **Có thể thay đổi**: List có thể được thêm, xóa, thay đổi phần tử sua khi được tạo.
- **Có thể chứa nhiều kiểu dữ liệu**: List có thể chứa bất kỳ kiểu dữ liệu nào, không nhất thiết phải đồng nhất.
- **Có thể truy cập bằng chỉ mục**: Mỗi phần tử trong list có một chỉ mục bắt đầu từ 0

![List Index light](/my-blog/assets/img/20250210-AI-Vietnam-16-Weeks-Review-Day06/list-index-light.png){: .light }
![List Index dark](/my-blog/assets/img/20250210-AI-Vietnam-16-Weeks-Review-Day06/list-index-dark.png){: .dark }

### Bài tập 1: Tạo mới 1 list gồm các số từ 1 đến 10

{% highlight python %}
# Output kỳ vọng:
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
{% endhighlight %}

<div style="padding: 15px; border-radius: 6px; border: 1px solid #e9ecef; margin: 20px 0;">
<details>
  <summary style="cursor: pointer; font-weight: bold">Đáp án (Click để xem)</summary>

{% highlight python %}
# Cách 1:
list_data = []
for i in range(1, 11):
  list_data.append(i)
print(list_data)
{% endhighlight %}

{% highlight python %}
# Cách 2:
list_data = [i for i in range(1, 11)]
print(list_data)
{% endhighlight %}

</details>
</div>


### Bài tập 2: In ra kết quả 5 phần tử đầu tiên có trong list trên

{% highlight python %}
# Output kỳ vọng:
[1, 2, 3, 4, 5]
{% endhighlight %}

<div style="padding: 15px; border-radius: 6px; border: 1px solid #e9ecef; margin: 20px 0;">
<details>
  <summary style="cursor: pointer; font-weight: bold">Đáp án (Click để xem)</summary>

{% highlight python %}
print(list_data[:5])
{% endhighlight %}

</details>
</div>


### Bài tập 3: In ra kết quả phần tử có giá trị không chia hết cho 2 (dùng kết hợp với vòng lặp for)

{% highlight python %}
# Output kỳ vọng:
[1, 3, 5, 7, 9]
{% endhighlight %}


<div style="padding: 15px; border-radius: 6px; border: 1px solid #e9ecef; margin: 20px 0;">
<details>
  <summary style="cursor: pointer; font-weight: bold">Đáp án (Click để xem)</summary>

{% highlight python %}
for number in list_data:
  if (number % 2 != 0):
    print(number)
{% endhighlight %}

</details>
</div>


### Bài tập 4: In ra kết quả tổng các giá trị trong list (dùng kết hợp với vòng lặp for)

{% highlight python %}
# Output kỳ vọng:
55
{% endhighlight %}

<div style="padding: 15px; border-radius: 6px; border: 1px solid #e9ecef; margin: 20px 0;">
<details>
  <summary style="cursor: pointer; font-weight: bold">Đáp án (Click để xem)</summary>

{% highlight python %}
total = 0
for number in list_data:
  total += number
print(total)
{% endhighlight %}

</details>
</div>