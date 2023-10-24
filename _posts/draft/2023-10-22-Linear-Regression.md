---
title: Về phương trình hồi quy tuyến tính
date: 2024 Oct 22
categories: [Machine Learning, Linear Regression]
tags: [machine learning, linear regression]
math: true
excerpt_separator: <!--excerpt-end-->
---

<!--excerpt-start-->
Linear Regression, hay còn gọi là phương trình hồi quy tuyến tính, là một phương trình cực kì phổ biến. Đường này còn có tên gọi khác là đường xu hướng (trend line).
<!--excerpt-end-->

##  Thiết lập phương trình hồi quy tuyến tính với 1 giá trị

### Xác định mục tiêu

Giả sử chúng ta có một bảng thống kê các lần chi tiêu cho bộ phận Marketing (cột `Marketing`) và lợi nhuận thu về từ các lần vận hành (cột `Profit`):

| Marketing | Profit |
|:---:|:---:|
| 472 | 192 |
| 444 | 192 |
| 408 | 191 |
| 383 | 183 |
| ... | ... |
| 164 | 78 |
| 148 | 71 |
| 36  | 70 |

Biểu diễn bằng biểu đồ phân tán (scatter plot chart)

![Marketing vs Profit chart light](/assets/img/linear-regression/sample-scatter-light.png){: .light }
![Marketing vs Profit chart dark](/assets/img/linear-regression/sample-scatter-dark.png){: .dark }

Mục tiêu của chúng ta là cần tìm một phương trình đường thẳng, mà ở đó ta có thể biểu diễn được mối quan hệ giữa chi phí cho `Marketing` và lợi nhuận `Profit` thu về. Phương trình cần tìm của chúng ta có dạng như sau:

$$\text{Profit} = w_0 + w_1 \times \text{Marketing}$$

### Sai số giữa giá trị dự đoán và thực tế

Giả định chúng ta đoán mò phương trình $\hat{y} = h(x)$ (h là viết tắt cho hypothesis) với $w_0 = 50$ và $w_1 = 0.2$:

$$ \text{Profit dự đoán} = h(x) = \hat{y} = 50 + 0.2 \times \text{Marketing}$$

Chúng ta có giá trị dự đoán như sau

| Marketing | Profit | h(x) = <br>50 + 0.2*Mkt |
|-----------|--------|-------------------------|
|       472 |    192 |                   161.6 |
|       444 |    192 |                   153.2 |
|       408 |    191 |                   142.4 |
|       ... |    ... |                     ... |
|       164 |     78 |                    69.2 |
|       148 |     71 |                    64.4 |
|        36 |     70 |                    30.8 |

Chúng ta có thể tính được sai số (độ chênh lệch) giữa giá trị dự đoán $h(x)$ và giá trị thực tế `Profit` bằng cách tính khoảng cách đơn giản. Chúng ta thiết lập phương trình tính sai số tại giá trị ngẫu nhiên $x_i$:

$$
\begin{align}
    \text{sai số tại $x_i$} &= |\text{Profit tại $x_i$} - \text{Dự đoán tại $x_i$}| \\
                        e_i &= |y_i - h(x_i)|
\end{align}
$$

![Distance between real value vs predict light](/assets/img/linear-regression/sample-before-loss-function-light.png){: .light }
![Distance between real value vs predict dark](/assets/img/linear-regression/sample-before-loss-function-dark.png){: .dark }

Kết quả thu về được như sau

| Marketing | Profit | Profit dự đoán = <br>50 + 0.2*Mkt | Sai số = <br> abs(Dự đoán - Thực tế) |
|-----------|--------|-----------------------------------|--------|
|       472 |    192 |                             161.6 |   30.4 |
|       444 |    192 |                             153.2 |   38.8 |
|       408 |    191 |                             142.4 |   48.6 |
|       ... |    ... |                               ... |    ... |
|       164 |     78 |                              69.2 |    8.8 |
|       148 |     71 |                              64.4 |    6.6 |
|        36 |     70 |                              30.8 |   39.2 |

> So với các tài liệu khác, các cách viết này đều như nhau: <br>  $\hat{y} = h_\theta(x) = h(x) = \theta_0 + \theta_1x = w_0 + w_1x $ 
{: .prompt-info }


### Hàm mất mát và Hàm chi phí

Để mô hình dự đoán được chính xác, ta cần phải giảm giá trị của `sai số` đến mức nhỏ nhất. 

Trước tiên, chúng ta nhắc đến phép ước lượng thường thấy trong thống kê, phương trình sai số toàn phương trung bình (Mean Square Error):

$$ 
\begin{align}
\text{MSE} &= \frac{1}{n} [(y_1 - \hat{y}_1)^2 + (y_2 - \hat{y}_2)^2 + \dots + (y_n - \hat{y}_n)^2] \\
           &= \frac{1}{n} \sum_{j=1}^n (y_j - \hat{y_j})^2
\end{align}
$$

Hàm mất mát (đôi khi cũng được gọi là hàm chi phí) tại điểm $x_i$ được biểu hiện như sau:

$$ l^{(i)}(w_0, w_1) = 1/2 (\hat{y_i} - y_i)^2 $$

Hàm 

## Các nguồn tham khảo và mở rộng

- https://www.scribbr.com/statistics/simple-linear-regression/
- https://online.stat.psu.edu/stat462/node/79/
- https://trituenhantao.io/machine-learning-co-ban/bai-3-linear-regression-hoi-quy-tuyen-tinh/
- https://machinelearningcoban.com/2016/12/28/linearregression/
- https://d2l.aivivn.com/chapter_linear-networks/linear-regression_vn.html#cac-thanh-phan-co-ban-cua-hoi-quy-tuyen-tinh
- https://www.ncl.ac.uk/webtemplate/ask-assets/external/maths-resources/statistics/regression-and-correlation/simple-linear-regression.html
- https://www.youtube.com/playlist?list=PLoROMvodv4rMiGQp3WXShtMGgzqpfVfbU
- https://cs229.stanford.edu/main_notes.pdf
- https://viblo.asia/p/tim-hieu-cong-thuc-toan-cua-phuong-phap-hoi-quy-tuyen-tinh-qua-bai-toan-du-bao-xa-lu-understanding-the-linear-regression-E375z7mdKGW
- https://bvag.com.vn/wp-content/uploads/2013/01/k2_attachments_PHAN-TICH-HOI-QUY-TUYEN-TINH-DON-GIAN.pdf