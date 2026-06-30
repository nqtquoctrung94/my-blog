---
title: Review cho AIO 2025 - Tuần 2 - Ngày 7
date: 2025 Feb 11
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

## Ngày 07: List CRUD

### Mô tả
Ở bài tập trước, ta đã làm quen với cách tạo và truy xuất các phần tử có trong List. Phần này, ta sẽ làm quen với thêm, đọc, sửa, xóa (Create, Read, Update, Delete, gọi tắt là CRUD) các phần tử trong List

| Chức năng                                 | Câu lệnh                                                                 |
|:------------------------------------------|:-------------------------------------------------------------------------|
| Tạo mới danh sách                         | list = [1, 'a', 3], hoặc<br>list(tuple) (bọc list vào 1 tuple cho trước) |
| Thêm phần tử vào cuối                     | list.append(value)                                                       |
| Thêm phần tử vào vị trí index             | list.insert(index_position, value)                                       |
| Xóa phần tử đầu tiên của giá trị chỉ định | list.remove(value)                                                       |
| Xóa phần tử tại vị trí index              | list.pop(index_position)                                                 |
| Cập nhật phần tử tại vị trí index         | list[index_position] = new_value                                         |


### Bài tập 1: Tạo mới một List có tên là lst_data, gồm các số chẵn từ 1 đến 12

{% highlight python %}
# Output kỳ vọng:
[2, 4, 6, 8, 10, 12]
{% endhighlight %}

<div style="padding: 15px; border-radius: 6px; border: 1px solid #e9ecef; margin: 20px 0;">
<details>
  <summary style="cursor: pointer; font-weight: bold">Đáp án (Click để xem)</summary>

{% highlight python %}
# Cách 1:
lst_data = []
for i in range(1, 13):
  if i % 2 == 0:
    lst_data.append(i)
print(lst_data)
{% endhighlight %}

{% highlight python %}
# Cách 2:
lst_data = [i for i in range(1, 13) if i % 2 == 0]
print(lst_data)
{% endhighlight %}

</details>
</div>


### Bài tập 2 Xóa tất cả các số chia hết cho 3 trong lst_data vừa tạo

{% highlight python %}
# Output kỳ vọng:
[2, 4, 8, 10]
{% endhighlight %}

<div style="padding: 15px; border-radius: 6px; border: 1px solid #e9ecef; margin: 20px 0;">
<details>
  <summary style="cursor: pointer; font-weight: bold">Đáp án (Click để xem)</summary>

{% highlight python %}
# Cách 1:
for i in lst_data:
  if i % 3 == 0:
    lst_data.remove(i)
print(lst_data)
{% endhighlight %}

{% highlight python %}
# Cách 2:
lst_data = [i for i in lst_data if i % 3 != 0]
print(lst_data)
{% endhighlight %}

</details>
</div>


### Bài tập 3: Thêm vào cuối lst_data các số từ 1 đến 3, và thêm vào vị trí index = 3 một chuỗi các số từ 6 đến 8

{% highlight python %}
# Output kỳ vọng:
[2, 4, 8, 6, 7, 8, 10, 1, 2, 3]
{% endhighlight %}

<div style="padding: 15px; border-radius: 6px; border: 1px solid #e9ecef; margin: 20px 0;">
<details>
  <summary style="cursor: pointer; font-weight: bold">Đáp án (Click để xem)</summary>

{% highlight python %}
# Cách 1
# Thêm vào cuối lst_data các số từ 1 đến 3
for i in range(1, 4):
  lst_data.append(i)
# Thêm vào vị trí index = 3 một chuỗi các số từ 6 đến 8
value = 6
position = 3
for i in range(3):
  lst_data.insert(position, value)
  position += 1
  value += 1

print(lst_data)
{% endhighlight %}

{% highlight python %}
# Cách 2
# Thêm vào cuối lst_data các số từ 1 đến 3
lst_data = lst_data + [i for i in range(1, 4)]
# Thêm vào vị trí index = 3 một chuỗi các số từ 6 đến 8
lst_data = lst_data[:3] + [i for i in range(6, 9)] + lst_data[3:]

print(lst_data)
{% endhighlight %}

</details>
</div>


### Bài tập 4: Nếu các số trong list lst_data chia hết cho 2 hoặc chia hết cho 5 thì cập nhật thành số 0

{% highlight python %}
# Output kỳ vọng:
[0, 0, 0, 0, 7, 0, 0, 1, 0, 3]
{% endhighlight %}

<div style="padding: 15px; border-radius: 6px; border: 1px solid #e9ecef; margin: 20px 0;">
<details>
  <summary style="cursor: pointer; font-weight: bold">Đáp án (Click để xem)</summary>

{% highlight python %}
# Cách 1:
for index, value in enumerate(lst_data):
  if (value % 2 == 0) or (value % 5 == 0):
    lst_data[index] = 0

print(lst_data)
{% endhighlight %}

{% highlight python %}
# Cách 2:
lst_data = [0 if (i % 2  == 0) or (i % 5 == 0) else i for i in lst_data]
print(lst_data)
{% endhighlight %}

</details>
</div>