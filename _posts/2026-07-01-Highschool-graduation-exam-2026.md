---
title: Về điểm thi tốt nghiệp THPT 2026
date: 2026 Jul 01
categories: [Algorithm, Python, Web Crawling]
tags: [algorithm, python, math, web-crawling]
math: true
excerpt_separator: <!--excerpt-end-->
---

<!--excerpt-start-->
Sau khi Bộ Giáo dục và Đào tạo công bố kết quả kỳ thi tốt nghiệp THPT 2026, mình đã nghiên cứu xem liệu năm nay số nguồn nào để thu thập dữ liệu điểm thi để tự thực hiện các phân tích thống kê hay không. Trong bài viết này mình sẽ viết về quá trình tìm hiểu, cách xác định API, xây dựng chương trình thu thập dữ liệu, làm sạch dữ liệu và chuẩn bị cho bước phân tích sau đó.
<!--excerpt-end-->

## Các nguồn tra cứu điểm thi

Các trang cho phép tra cứu điểm thi mà mình biết:

- Từ Bộ Giáo Dục và Đào Tạo:

|--:|---------------------------------------------------------|
| 1 | <https://tracuudiem.thitotnghiepthpt.edu.vn/>           |
| 2 | <https://thisinh.thitotnghiepthpt.edu.vn/Account/Login> |

- Tra cứu theo Sở Giáo dục & Đào tạo từng tỉnh thành:

| No. | Sở                      | Link tra cứu                                                 |
|-----|-------------------------|--------------------------------------------------------------|
|   1 | Sở GD&ĐT Hà Nội         | <https://tracuu.hanoi.edu.vn/>                               |
|   2 | Sở GD&ĐT Cao Bằng       | <https://tradiem.khaothicaobang.edu.vn/>                     |
|   3 | Sở GD&ĐT Tuyên Quang    | <http://diemthi.tuyenquang.edu.vn/>                          |
|   4 | Sở GD&ĐT Điện Biên      | <https://tracuudiem.dienbien.edu.vn/>                        |
|   5 | Sở GD&ĐT Lai Châu       | <http://diemthithpt.laichau.edu.vn/>                         |
|   6 | Sở GD&ĐT Sơn La         | <https://diemthitotnghiep.sogddt.sonla.gov.vn/>              |
|   7 | Sở GD&ĐT Lào Cai        | <https://laocai.tsdc.vnedu.vn/tracuu>                        |
|   8 | Sở GD&ĐT Thái Nguyên    | <https://diemthi.thainguyen.edu.vn/>                         |
|   9 | Sở GD&ĐT Lạng Sơn       | <https://tracuudiem.langson.edu.vn/>                         |
|  10 | Sở GD&ĐT Quảng Ninh     | <https://quangninh.edu.vn/>                                  |
|  11 | Sở GD&ĐT Bắc Ninh       | <https://diemthi.bacninh.edu.vn/>                            |
|  12 | Sở GD&ĐT Phú Thọ        | <https://tracuudiem.phutho.edu.vn/>                          |
|  13 | Sở GD&ĐT Hải Phòng      | <https://diemthithpt.haiphong.gov.vn/>                       |
|  14 | Sở GD&ĐT Hưng Yên       | <http://diemthi.hungyen.edu.vn/>                             |
|  15 | Sở GD&ĐT Ninh Bình      | <https://tracuudiemnb.ninhbinh.edu.vn/>                      |
|  16 | Sở GD&ĐT Thanh Hóa      | <http://thitn.thanhhoa.edu.vn/>                              |
|  17 | Sở GD&ĐT Nghệ An        | <https://giaoducso.nghean.gov.vn/trang-chu/tra-cuu-diem-thi> |
|  18 | Sở GD&ĐT Hà Tĩnh        | <http://tracuudiemthi.hatinh.edu.vn/>                        |
|  19 | Sở GD&ĐT Quảng Trị      | <https://diemthi.quangtri.edu.vn/>                           |
|  20 | Sở GD&ĐT TP Huế         | <https://tracuudiem2.thuathienhue.edu.vn/>                   |
|  21 | Sở GD&ĐT Đà Nẵng        | <https://tracuudiem.danang.edu.vn/>                          |
|  22 | Sở GD&ĐT Quảng Ngãi     | <https://diemthi.quangngai.edu.vn/>                          |
|  23 | Sở GD&ĐT Gia Lai        | <http://diemthi.gialai.edu.vn:8080/>                         |
|  24 | Sở GD&ĐT Khánh Hoà      | <https://diemthi.khanhhoa.edu.vn/>                           |
|  25 | Sở GD&ĐT Đắk Lắk        | <https://diemthi.daklak.edu.vn/>                             |
|  26 | Sở GD&ĐT Lâm Đồng       | <https://diemthi.lamdongtructuyen.vn/>                       |
|  27 | Sở GD&ĐT Đồng Nai       | <https://tracuudiem.dongnai.edu.vn/>                         |
|  28 | Sở GD&ĐT TP Hồ Chí Minh | <https://diemthi.hcm.edu.vn/>                                |
|  29 | Sở GD&ĐT Tây Ninh       | <https://tracuudiem2026.tayninh.edu.vn/>                     |
|  30 | Sở GD&ĐT Đồng Tháp      | <http://tracuudiem.dongthap.edu.vn/>                         |
|  31 | Sở GD&ĐT Vĩnh Long      | <https://tracuudiem.vinhlong.edu.vn/>                        |
|  32 | Sở GD&ĐT An Giang       | <https://tracuu.angiang.edu.vn/>                             |
|  33 | Sở GD&ĐT Cần Thơ        | <https://diemthithpt.ctu.edu.vn/>                            |
|  34 | Sở GD&ĐT Cà Mau         | <http://diemthithpt.camau.edu.vn/>                           |

- Tra cứu trên các trang báo

| No. | Báo            | Link tra cứu                                                                    |
|-----|----------------|---------------------------------------------------------------------------------|
|   1 | Báo Dân Trí    | <https://dantri.com.vn/giao-duc/tuyen-sinh/tra-cuu-diem.htm>                    |
|   2 | Báo Tiền Phong | <https://tienphong.vn/tra-cuu-diem-thi.html>                                    |
|   3 | Báo Tuổi Trẻ   | <https://tuoitre.vn/diem-thi.htm>                                               |
|   4 | Báo Vietnamnet | <https://vietnamnet.vn/giao-duc/diem-thi/tra-cuu-diem-thi-tot-nghiep-thpt-2026> |
|   5 | Báo VnExpress  | <https://diemthi.vnexpress.net/>                                                |


## Về cấu trúc số báo danh

Cấu trúc số báo danh của thí sinh được hiểu như sau

![Cấu trúc số báo danh THPT light](/my-blog/assets/img/20260701-Highschool-exam-2026/ID-structure-light.png){: .light }
![Cấu trúc số báo danh THPT dark](/my-blog/assets/img/20260701-Highschool-exam-2026/ID-structure-dark.png){: .dark }


## Thu thập dữ liệu điểm thi

### Lựa chọn nguồn

Trong số các nguồn bên trên, mình đã chọn Báo Tuổi Trẻ vì nhận thấy khi gửi request kiểm tra điểm, trang web trả về theo API.

![Request URL khi tra cứu điểm một thí sinh trên trang Tuổi Trẻ](/my-blog/assets/img/20260701-Highschool-exam-2026/request-url.png)

Tuy nhiên, việc lấy dữ liệu theo từng Số báo danh cực kỳ chậm, và không phải số báo danh nào cũng search được (ví dụ 01000014, 01000015, 01000017) và với 35 hội đồng thi, việc xác định được điểm dừng và loop qua từng số báo danh như vậy thực sự không dành cho người bình thường. 

Mình bắt đầu kiểm tra mã JavaScript của trang để xem liệu có endpoint nào trả về nhiều kết quả cùng lúc hay không. Khi sử dụng `Ctrl + Shift + F` và tìm theo keyword `diem-thi-thpt`, mình đã tìm ra được đường link sau `/api/diem-thi-thpt.htm?pageindex=1&size=100`

![Tìm API để](/my-blog/assets/img/20260701-Highschool-exam-2026/find-api.png)

Vậy là mình đã tìm được API để lấy nhiều dữ liệu điểm cùng một lúc.

{% highlight code%}
GET /api/diem-thi-thpt.htm
{% endhighlight %}

Parameters

| Name      | Type | Required | Description             |
|-----------|------|----------|-------------------------|
| pageindex | int  | No       | Số trang                |
| size      | int  | No       | Số lượng dòng mỗi trang |
| year      | int  | No       | Năm học                 |

### Lựa chọn phương pháp

Từ đây mình xây dựng một code đơn giản để lấy trang dữ liệu đầu tiên như sau

{% highlight python%}

import requests
import json

response = requests.get(
    url = "https://s6.tuoitre.vn/api/diem-thi-thpt.htm",
    params = {
        "pageindex": 1,
        "size": 5,
        "year": 2026
    }
)

response_json = json.loads(response.text)
print(response_json)

{% endhighlight %}

Ta có được response như sau

{% highlight python%}
{
    "data":[
        {"SOBAODANH":"04003148","TOAN":"2.1","VA":"5.5","LI":"","HO":"","SI":"","SU":"3.75","DI":"2.5","KTPL":"","TI":"","CNCN":"","CNNN":"","NN":"","MON_NN":"","NGAY_SINH":"---","file_name":""},
        {"SOBAODANH":"04003153","TOAN":"7.5","VA":"7.5","LI":"7","HO":"","SI":"","SU":"","DI":"","KTPL":"","TI":"","CNCN":"","CNNN":"","NN":"6.75","MON_NN":"N1","NGAY_SINH":"---","file_name":""},
        {"SOBAODANH":"04003167","TOAN":"3","VA":"4","LI":"2","HO":"","SI":"","SU":"4.1","DI":"","KTPL":"","TI":"","CNCN":"","CNNN":"","NN":"","MON_NN":"","NGAY_SINH":"---","file_name":""},
        {"SOBAODANH":"04003169","TOAN":"4.35","VA":"6.5","LI":"","HO":"","SI":"","SU":"7.75","DI":"","KTPL":"","TI":"","CNCN":"","CNNN":"","NN":"3","MON_NN":"N1","NGAY_SINH":"---","file_name":""},
        {"SOBAODANH":"04003172","TOAN":"3.5","VA":"4.5","LI":"2.85","HO":"","SI":"","SU":"4.95","DI":"","KTPL":"","TI":"","CNCN":"","CNNN":"","NN":"","MON_NN":"","NGAY_SINH":"---","file_name":""}
    ],
    "total":1208863,
    "success":true
}

{% endhighlight %}

Sau khi nhận được JSON, bước tiếp theo là chuyển dữ liệu thành DataFrame để thuận tiện cho việc xử lý.

{% highlight python%}

import pandas as pd

df = pd.DataFrame.from_records(response_json['data'])
df

{% endhighlight %}

Kết quả nhận được sẽ trông như vầy

| SOBAODANH | TOAN |  VA |   LI | HO | SI |   SU |  DI | KTPL | TI | CNCN | CNNN |   NN | MON_NN | NGAY_SINH | file_name |
|----------:|-----:|----:|-----:|---:|---:|-----:|----:|-----:|---:|-----:|-----:|-----:|-------:|----------:|----------:|
|  04003148 |  2.1 | 5.5 |      |    |    | 3.75 | 2.5 |      |    |      |      |      |        |       --- |           |
|  04003153 |  7.5 | 7.5 |    7 |    |    |      |     |      |    |      |      | 6.75 |     N1 |       --- |           |
|  04003167 |    3 |   4 |    2 |    |    |  4.1 |     |      |    |      |      |      |        |       --- |           |
|  04003169 | 4.35 | 6.5 |      |    |    | 7.75 |     |      |    |      |      |    3 |     N1 |       --- |           |
|  04003172 |  3.5 | 4.5 | 2.85 |    |    | 4.95 |     |      |    |      |      |      |        |       --- |           |

Qua thông tin bên trên và thêm một chút testing, mình cũng nhận ra một số đặc điểm:
- Có thể request lên đến 10,000 dòng dữ liệu một lúc
- Có tổng cộng 1,208,863 dòng dữ liệu (điều này đúng với [thông tin mà báo chí đã đưa](https://vnexpress.net/hon-1-2-trieu-thi-sinh-dang-ky-thi-tot-nghiep-dong-ky-luc-5069379.html), năm nay có số lượng thí sinh cao kỷ lục)
- Như vậy sẽ cần request khoản 121 lần --> Mình sẽ cố định số vòng lặp này trong code luôn
- Số báo danh có số 0 đằng trước, nên nếu lưu dữ liệu dưới dạng int sẽ bị mất format
- Đôi khi server sẽ bị quá tải sẽ trả về lỗi `429 Too Many Requests` hoặc `502 Bad Gateway`

Với các thông tin sau, mình bắt đầu triển khai thu thập dữ liệu, với định hướng là:
- Sẽ request dữ liệu với số page chạy từ 1 đến 121
- Nếu gặp lỗi, retry sau khi nghỉ một vài giây ngẫu nhiên
- Mỗi lần request sẽ lưu lại 1 file csv, việc này giúp cho máy không phải lưu toàn bộ data cào được trong RAM trong quá trình cào 121 trang dữ liệu và giảm thiểu rủi ro nếu ngắt quãng giữa chừng thì không bị mất hết.
- Vì đây là API công khai được website sử dụng để phục vụ người dùng, bài viết chỉ nhằm mục đích nghiên cứu kỹ thuật. Khi thu thập dữ liệu, mình sẽ giới hạn thời gian giữa các request để tránh gây tải không cần thiết lên máy chủ.
- Kết hợp 121 file csv thành 1 data lớn hoàn chỉnh sau khi cào xong.

### Triển khai thu thập dữ liệu

Sau đây là code mà mình đã sử dụng để thu thập dữ liệu. Ở đây thay vì sử dụng `requests.get()` theo cách truyền thống, mình sử dụng `requests.Session()` để tái sử dụng kết nối HTTP giữa các request, giúp giảm thời gian thiết lập kết nối và cải thiện tốc độ khi tải nhiều trang liên tiếp.

{% highlight python%}

import requests
import random
import time
import pandas as pd

session = requests.Session()

for page in range(1, 122):  # Lặp từ trang 1 đến 121
    retry = 0

    while True:

        r = session.get(
            "https://s6.tuoitre.vn/api/diem-thi-thpt.htm",
            params = {
                "pageindex": page
                , "size": 10000
                , "year": 2026
            },
            timeout=60,
        )

        # Nếu gặp lỗi, thử lại với một mẫu thời gian ngẫu nhiên
        # Càng gặp lỗi sẽ chờ càng lâu
        if r.status_code in (429, 500, 502, 503, 504):
            retry += 1
            wait = min(120, 5 * retry) + random.uniform(0, 2)
            print(f"{r.status_code} on page {page}, retry in {wait:.1f}s")
            time.sleep(wait)
            continue

        r.raise_for_status()

        pd.DataFrame(r.json()["data"]).to_csv(
            f"crawl/page_{page:03}.csv",
            index=False
        )

        print(f"Saved page {page}")
        time.sleep(10)
        break
            
{% endhighlight %}

Tổng thời gian cho quá trình này sẽ khoảng 3 phút

{% highlight python%}
Records: 1,208,863
Downloaded: ~47 MB
Runtime: ~123 seconds
Average request: 1.0153 seconds
{% endhighlight %}

Sau khi đã lưu xong, mình kết hợp dữ liệu lại về 1 khối data hoàn chỉnh

{% highlight python%}

import glob
import pandas as pd

crawled_files = glob.glob("crawl/page_*.csv")
df = pd.concat(
    (pd.read_csv(file, dtype=str) for file in crawled_files),
    ignore_index=True
)

df.to_csv("clean/scores_2026_combined.csv", index=False)
print(df.shape)

{% endhighlight %}

Kết quả sẽ nhận dữ liệu với 1,208,863 dòng và 16 cột. Trùng khớp với số lượng dòng đã xác định ở bước trước đó.

{% highlight python%}
(1208863, 16)
{% endhighlight %}


## Làm sạch dữ liệu

### Về Mã hội đồng thi

Như đã đề cập, 2 ký tự đầu tiên của thí sinh là số mã phòng thi, từ đây mình có thể xác định được khu vực thi của từng thí sinh.

Năm nay có một sự thay đổi lớn về đơn vị hành chính sau sáp nhập, vì thế số lượng hội đồng thi cũng đã được điều chỉnh so với các năm trước. Mình tham khảo mã hội đồng thi theo nội dung trên [báo Thư Viện Pháp Luật](https://thuvienphapluat.vn/phap-luat/ho-tro-phap-luat/danh-sach-ma-so-gddt--ma-hoi-dong-thi-tot-nghiep-thpt-2026-huong-dan-dien-phieu-dang-ky-du-thi-tot--264599.html) và đã chuẩn bị một dictionary như sau:

{% highlight python%}
city_code = {
     '01' : 'Thành phố Hà Nội'
    ,'04' : 'Tỉnh Cao Bằng'
    ,'08' : 'Tỉnh Tuyên Quang'
    ,'11' : 'Tỉnh Điện Biên'
    ,'12' : 'Tỉnh Lai Châu'
    ,'14' : 'Tỉnh Sơn La'
    ,'15' : 'Tỉnh Lào Cai'
    ,'19' : 'Tỉnh Thái Nguyên'
    ,'20' : 'Tỉnh Lạng Sơn'
    ,'22' : 'Tỉnh Quảng Ninh'
    ,'24' : 'Tỉnh Bắc Ninh'
    ,'25' : 'Tỉnh Phú Thọ'
    ,'31' : 'Thành phố Hải Phòng'
    ,'33' : 'Tỉnh Hưng Yên'
    ,'37' : 'Tỉnh Ninh Bình'
    ,'38' : 'Tỉnh Thanh Hóa'
    ,'40' : 'Tỉnh Nghệ An'
    ,'42' : 'Tỉnh Hà Tĩnh'
    ,'44' : 'Tỉnh Quảng Trị'
    ,'46' : 'Thành phố Huế'
    ,'48' : 'Thành phố Đà Nẵng'
    ,'51' : 'Tỉnh Quảng Ngãi'
    ,'52' : 'Tỉnh Gia Lai'
    ,'56' : 'Tỉnh Khánh Hòa'
    ,'66' : 'Tỉnh Đắk Lắk'
    ,'68' : 'Tỉnh Lâm Đồng'
    ,'75' : 'Tỉnh Đồng Nai'
    ,'79' : 'Thành phố Hồ Chí Minh'
    ,'80' : 'Tỉnh Tây Ninh'
    ,'82' : 'Tỉnh Đồng Tháp'
    ,'86' : 'Tỉnh Vĩnh Long'
    ,'91' : 'Tỉnh An Giang'
    ,'92' : 'Thành phố Cần Thơ'
    ,'96' : 'Tỉnh Cà Mau'
    ,'99' : 'Cục Quân huấn - Nhà trường, Bộ Quốc phòng'
}
{% endhighlight %}

### Về Môn thi Ngoại ngữ

Khi kiểm tra dữ liệu cột `MON_NN`:

{% highlight python%}
df['MON_NN'].value_counts(dropna=False)

# Output
MON_NN
NaN    864636
N1     334547
N4       7382
N7        928
N6        596
N3        430
N5        281
N2         63
Name: count, dtype: int64
{% endhighlight %}

Dựa vào thứ tự ngôn ngữ trên [báo Thư Viện Pháp Luật](https://thuvienphapluat.vn/phap-luat/ho-tro-phap-luat/danh-muc-chung-chi-ngoai-ngu-ky-thi-tot-nghiep-thpt-2026-chi-tiet-theo-thong-tu-132026ttbgddt-ra-sa-258130.html), mình chuẩn bị dictionary để map ngôn ngữ như sau:

{% highlight python%}
language_code = {
    "N1": "English",
    "N2": "Russian",
    "N3": "French",
    "N4": "Chinese",
    "N5": "German",
    "N6": "Japanese",
    "N7": "Korean",
}
{% endhighlight %}

### Làm sạch dữ liệu

Là một người lười, mình luôn thường gom các bước clean dữ liệu về cùng một chỗ, và đây là hướng đi của mình

{% highlight python%}
df_clean = pd.DataFrame({
    'SBD'       : df['SOBAODANH'],
    'TP'        : df['SOBAODANH'].str[:2].map(city_code),
    'Ten_NN'    : df['MON_NN'].astype(str).map(language_code),   # Ngôn ngữ của môn Ngoại ngữ
    'Toán'      : df['TOAN'].astype(float),  
    'Văn'       : df['VA'].astype(float),    
    'Ngoại ngữ' : df['NN'].astype(float),    

    # Các môn Khoa Học Tự Nhiên
    'Lí'        : df['LI'].astype(float),    
    'Hóa'       : df['HO'].astype(float),    
    'Sinh'      : df['SI'].astype(float),    

    # Các môn Khoa Học Xã Hội
    'Sử'        : df['SU'].astype(float),    
    'Địa'       : df['DI'].astype(float),    

    # Các môn khác
    'Tin'       : df['TI'].astype(float),    
    'KTPL'      : df['KTPL'].astype(float),     # Giáo Dục Kinh Tế Pháp Luật
    'CNCN'      : df['CNCN'].astype(float),     # Công nghệ - Công nghiệp
    'CNNN'      : df['CNNN'].astype(float),     # Công nghệ - Nông nghiệp
})

df_clean = df_clean.sort_values(by = 'SBD', ascending=True).reset_index(drop=True)
{% endhighlight %}

## Tổng kết

Trong bài viết này, mình đã trình bày quá trình tìm hiểu API, thu thập dữ liệu điểm thi, và xây dựng một quy trình làm sạch dữ liệu để chuẩn bị cho bước phân tích.

Nếu có thời gian, mình sẽ tiếp tục chia sẻ phần phân tích dữ liệu cũng như một số thống kê thú vị rút ra từ bộ dữ liệu này. 

Hình ảnh được tạo bằng công cụ [Figma](https://www.figma.com/) và screenshot trong quá trình làm.