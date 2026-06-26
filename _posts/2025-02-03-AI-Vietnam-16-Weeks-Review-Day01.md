---
title: Review cho AIO 2025 - Tuần 1 - Ngày 1
date: 2025 Feb 03
categories: [Algorithm, Python, AI Vietnam]
tags: [algorithm]
math: true
excerpt_separator: <!--excerpt-end-->
hidden: true
---

<!--excerpt-start-->
Nội dung ngày 1 trong 16 tuần Review trước khi vào học chương trình AIO 2025.
<!--excerpt-end-->

## Giới thiệu

Để theo dõi toàn bộ nội dung ôn tập, vui lòng tham khảo tại bài viết [16 tuần review cho AIO 2025]({% post_url 2025-02-01-AI-Vietnam-16-Weeks-Review %})

## Tuần 01 - Python Cơ bản

> Nội dung chính:<br>- **Lập trình**: Ôn tập về kỹ thuật lập trình với Python, cú pháp cơ bản (khai báo biến, vòng lặp, điều kiện), cách xây dựng hàm<br>- **Toán**: Sử dụng Python để cài đặt các công thức Toán cơ bản trong giải tích cơ bản
{: .prompt-info }

### Ngày 01: Cấu trúc If-Else

Cấu trúc if-else là một cấu trúc điền kiện trong lập trình, đước sử dụng để kiểm tra điền kiện logic và thực hiện các đoạn mã khác nhau dựa trên kết quả của điều kiện
- **if:** kiểm tra điều kiện. Nếu điều kiện đúng thì thực hiện khối lệnh bên trong
- **else:** khi điều kiện if là sai, thì sẽ thực thi điều kiện trong else
- **elif (nếu có, sau if và trước else):** Kiểm tra điều kiện bổ sung nếu điều kiện trước đó là sai

#### Cú pháp

{% highlight python %}
if điều_kiện_1:
    # Lệnh sẽ chạy khi điều_kiện_1 đúng
elif điều_kiện_2:
    # Lệnh sẽ chạy khi điều_kiện_1 sai và điều_kiện_2 đúng
elif điều_kiện_3:
    # Lệnh sẽ chạy khi cả 2 điều kiện trên sai và điều_kiện_3 đúng
else:
    # Lệnh sẽ chạy khi tất cả các điều kiện trên đều sai
{% endhighlight %}

#### Ví dụ

{% highlight python %}
x = 10
if x > 0:
    print("x là số dương")
elif x == 0:
    print("x bằng 0")
else:
    print("x là số âm")
{% endhighlight %}

#### Bài tập 1: Tính lịch Can Chi

Can Chi là một hệ thống tính toán giờ, ngày, tháng, năm âm lịch của người Trung Quốc cổ đại. Can Chi có 10 thiên can và 12 địa chi. Để tính được can chi, chúng ta dựa vào quy tắc sau đây

- Can: lấy năm sinh chia cho 10 và lấy phần dư. Kết quả Can sẽ tương ứng với bảng bên dưới

| Phần dư |    0 |   1 |    2 |   3 |    4 |  5 |    6 |    7 |   8 |  9 |
|--------:|-----:|----:|-----:|----:|-----:|---:|-----:|-----:|----:|---:|
|     Can | Canh | Tân | Nhâm | Quý | Giáp | Ất | Bính | Đinh | Mậu | Kỷ |

- Chi: lấy năm sinh chia cho 12 và lấy phần dư. Kết quả Chi sẽ tương ứng với bảng bên dưới

| Phần dư |    0 |   1 |    2 |   3 |  4 |   5 |   6 |   7 |    8 |  9 |  10 |  11 |
|--------:|-----:|----:|-----:|----:|---:|----:|----:|----:|-----:|---:|----:|----:|
|     Chi | Thân | Dậu | Tuất | Hợi | Tý | Sửu | Dần | Mẹo | Thìn | Tỵ | Ngọ | Mùi |



Đề bài yêu cầu: Hoàn thành đoạn code bên dưới, dựa vào giá trị nhập năm sinh để xác định tuổi theo lịch Can Chi, kết quả trả về sẽ có dạng '`lịch Can` `lịch Chi`'

{% highlight python %}
# Yêu cầu:
def calculate_can_chi_calendar(year):
    result = ''
    ##### Your code here #####
    return result

# Output kỳ vọng:
calculate_can_chi_calendar(2025) -> Ất Tỵ
calculate_can_chi_calendar(2024) -> Giáp Thìn
calculate_can_chi_calendar(1997) -> Đinh Sửu
{% endhighlight %}

<div style="padding: 15px; border-radius: 6px; border: 1px solid #e9ecef; margin: 20px 0;">
<details>
  <summary style="cursor: pointer; font-weight: bold">Đáp án (Click để xem)</summary>

Theo yêu cầu của đề, chúng ta chỉ có thể sử dụng if-else để thiết lập hàm, cho nên chúng ta sẽ xét từng trường hợp như sau

{% highlight python %}
def calculate_can_chi_calendar(year):
  can = ''
  chi = ''

  if year % 10 == 0:
    can = 'Canh'
  elif year % 10 == 1:
    can = 'Tân'
  elif year % 10 == 2:
    can = 'Nhâm'
  elif year % 10 == 3:
    can = 'Quý'
  elif year % 10 == 4:
    can = 'Giáp'
  elif year % 10 == 5:
    can = 'Ất'
  elif year % 10 == 6:
    can = 'Bính'
  elif year % 10 == 7:
    can = 'Đinh'
  elif year % 10 == 8:
    can = 'Mậu'
  else:
    can = 'Kỷ'

  if year % 12 == 0:
    chi = 'Thân'
  elif year % 12 == 1:
    chi = 'Dậu'
  elif year % 12 == 2:
    chi = 'Tuất'
  elif year % 12 == 3:
    chi = 'Hợi'
  elif year % 12 == 4:
    chi = 'Tý'
  elif year % 12 == 5:
    chi = 'Sửu'
  elif year % 12 == 6:
    chi = 'Dần'
  elif year % 12 == 7:
    chi = 'Mão'
  elif year % 12 == 8:
    chi = 'Thìn'
  elif year % 12 == 9:
    chi = 'Tỵ'
  elif year % 12 == 10:
    chi = 'Ngọ'
  else:
    chi = 'Mùi'

  result = can + ' ' + chi
  return result
{% endhighlight %}


Nếu không bị giới hạn về việc sử dụng if-else, chúng ta có thể sử dụng list và sẽ có một bài giải gọn gàng hơn

{% highlight python %}
# Ví dụ về sử dụng list

lst_can = ['Canh', 'Tân', 'Nhâm', 'Quý', 'Giáp', 'Ất', 'Bính', 'Đinh', 'Mậu', 'Kỷ']
lst_chi = ['Thân', 'Dậu', 'Tuất', 'Hợi', 'Tý', 'Sửu', 'Dần', 'Mão', 'Thìn', 'Tỵ', 'Ngọ', 'Mùi']

year = int(input('Nhập vào năm: '))
can_index = year % 10
chi_index = year % 12
print(lst_can[can_index] + " " + lst_chi[chi_index])
{% endhighlight %}

</details>
</div>

#### Bài tập 2: Hàm kích hoạt - Activate function

**Activate Function** thường được sử dụng trong các mô hình học máy để áp dụng một hàm kích hoạt lên đầu ra của một tầng (layer). Hàm này sẽ giúp chuyển đổi dữ liệu đầu vào thành một không gian mong muốn hoặc không gian phi tuyến, giúp mô hình có thể học được các mẫu phức tạp. Một số hàm kích hoạt phổ biến bao gồm: *ReLU*, *Sigmoid*, và *Tanh*, mỗi hàm phù hợp với các nhiệm vụ và kiến trúc khác nhau.

Trong bài tập này, chúng ta sẽ chỉ tập áp dụng hàm if-else dựa vào logic của các Activate Function, hơn là đề cập sâu về tính chất của chúng.

##### 1. ReLU (Rectified Linear Unit)

$$
\begin{equation*}
\text{ReLU}(x) =
\begin{cases}
x & \text{nếu } x > 0 \\
0 & \text{nếu } x \le 0
\end{cases}
\end{equation*}
$$

{% highlight python %}
# Yêu cầu:
def relu(x):
    ##### Your code here #####

# Output kỳ vọng:
relu(3) -> 3
relu(-2) -> 0
relu(0) -> 0
{% endhighlight %}

<div style="padding: 15px; border-radius: 6px; border: 1px solid #e9ecef; margin: 20px 0;">
<details>
  <summary style="cursor: pointer; font-weight: bold">Đáp án (Click để xem)</summary>

{% highlight python %}
def relu(x):
    if x > 0:
        return x
    else:
        return 0
{% endhighlight %}

Mở rộng một xíu về ReLU <br>

1/ Một trong những cách khác để define ReLU đó là:

$$
\begin{equation*}
\text{ReLU}(x) = \max(0, x)
\end{equation*}
$$

Vì thế hàm này cũng có thể rút ngắn thành

{% highlight python %}
def ReLU(x):
    return max(0, x)
{% endhighlight %}

2/ Về mặt toán học, chúng ta cũng có thể viết lại hàm ReLU thành:

$$
\begin{equation*}
\text{ReLU}(x) = \frac{x + |x|}{2}
\end{equation*}
$$

- Với $x > 0$, thì $|x| = x$, nên $\text{ReLU}(x) = (x + x)/2 = x$ <br>
- Với $x \le 0$, thì $|x| = -x$, nên $\text{ReLU}(x) = (x - x)/2 = 0$

</details>
</div>

##### 2. Leaky ReLU

$$
\begin{equation*}
\text{Leaky ReLU}(x) =
\begin{cases}
x & \text{nếu } x > 0 \\
\alpha x & \text{nếu } x \le 0
\end{cases}
\end{equation*}
$$

{% highlight python %}
# Yêu cầu:
def leaky_relu(x, alpha=0.01):
    ##### Your code here #####

# Output kỳ vọng:
leaky_relu(3) -> 3
leaky_relu(-2) -> -0.02
leaky_relu(0) -> 0
{% endhighlight %}

<div style="padding: 15px; border-radius: 6px; border: 1px solid #e9ecef; margin: 20px 0;">
<details>
  <summary style="cursor: pointer; font-weight: bold">Đáp án (Click để xem)</summary>

{% highlight python %}
def leaky_relu(x, alpha=0.01):
    if x > 0:
        return x
    else:
        return alpha * x
{% endhighlight %}

</details>
</div>

##### 3. Sigmoid

$$
\begin{equation*}
\text{Sigmoid}(x) =
\frac{1}{1 + e^{-x}}
\end{equation*}
$$

{% highlight python %}
# Yêu cầu:
import math

def sigmoid(x):
    ##### Your code here #####

# Output kỳ vọng:
sigmoid(0) -> 0.5
sigmoid(2) -> 0.8808
sigmoid(-2) -> 0.1192
{% endhighlight %}

<div style="padding: 15px; border-radius: 6px; border: 1px solid #e9ecef; margin: 20px 0;">
<details>
  <summary style="cursor: pointer; font-weight: bold">Đáp án (Click để xem)</summary>
<br>
Trước khi đi vào đáp án, chúng ta cần xét về tính ổn định số học (numerical stability) trong lập trình.<br>

Xét:<br> 
$$\text{Sigmoid}(x) = \frac{1}{1 + e^{-x}}$$
khi $x \to - \infty$, giá trị $e^{-x} \to \infty$, việc này vượt quá khả năng lưu trữ số thực của máy tính, dẫn đến lỗi tràn số dữ liệu (overflow).<br>
<br>
Để giải quyết vấn đề này, chúng ta cần chia thành hai trường hợp:<br>
1. Khi $x \ge 0$: Số mũ $-x$ sẽ luôn $\le 0$. Đại lượng $e^{-x}$ tiến dần về $0$, đảm bảo phép tính $1 / (1 + e^{-x})$ được tính toán ổn định.<br>
2. Khi $x < 0$: Chúng ta áp dụng chuẩn hóa số mũ (exp-normalize trick), biến đổi công thức thành $\frac{e^x}{e^x + 1}$. Lúc này số mũ $x$ là số âm, đại lượng $e^x$ tiến dần về $0$ và hoàn toàn tránh được hiện tượng tràn số.<br>
<br>
Đọc thêm tại: <a href="https://timvieira.github.io/blog/post/2014/02/11/exp-normalize-trick/" target="_blank" rel="noopener">Exp-Normalize Trick - Numerically stable sigmoid function</a>

{% highlight python %}
import math

def sigmoid(x):
    if x >= 0:
        return 1 / (1 + math.exp(-x))
    else:
        return math.exp(x) / (1 + math.exp(x))
{% endhighlight %}

</details>
</div>

##### 4. Tanh

$$
\begin{equation*}
\text{Tanh}(x) =
\frac{e^{x} - e^{-x}}{e^{x} + e^{-x}}
\end{equation*}
$$

{% highlight python %}
# Yêu cầu:
import math

def tanh(x):
    ##### Your code here #####

# Output kỳ vọng:
tanh(0) -> 0.0
tanh(2) -> 0.964
tanh(150) -> 1
{% endhighlight %}

<div style="padding: 15px; border-radius: 6px; border: 1px solid #e9ecef; margin: 20px 0;">
<details>
  <summary style="cursor: pointer; font-weight: bold">Đáp án (Click để xem)</summary>

{% highlight python %}
# Yêu cầu:
import math

def tanh(x):
    ex = math.exp(x)
    enx = math.exp(-x)
    if ex + enx != 0:
        return (ex - enx) / (ex + enx)
    else:
        return 0
{% endhighlight %}

<b>Nhận xét:</b> Mặc dù chúng ta áp dụng if-else để kiểm tra điều kiện mẫu số khác 0, nhưng ta dễ dàng chứng minh được mẫu số này sẽ không bao giờ triệt tiêu với mọi x thuộc tập số thực.<br>
Mẫu số chỉ có thể bằng 0 khi x là số phức, tuy nhiên trường hợp này nằm ngoài phạm vi xử lý của các bài toán Machine Learning thông thường nên không cần xét tới ở đây.

</details>
</div>

##### 5. ELU (Exponential Linear Unit)

$$
\begin{equation*}
\text{ELU}(x) =
\begin{cases}
x & \text{nếu } x > 0 \\
\alpha(e^{x} - 1) & \text{nếu } x \le 0
\end{cases}
\end{equation*}
$$

{% highlight python %}
# Yêu cầu:
import math

def elu(x, alpha=1.0):
    ##### Your code here #####

# Output kỳ vọng:
elu(3) -> 3
elu(-1) -> -0.6321
elu(0) -> 0
{% endhighlight %}

<div style="padding: 15px; border-radius: 6px; border: 1px solid #e9ecef; margin: 20px 0;">
<details>
  <summary style="cursor: pointer; font-weight: bold">Đáp án (Click để xem)</summary>

{% highlight python %}
import math 

def elu(x, alpha=1.0):
    if x > 0:
        return x
    else:
        return alpha * (math.exp(x) - 1)
{% endhighlight %}

</details>
</div>

