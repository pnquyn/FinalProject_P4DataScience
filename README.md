# README

## 1. Giới thiệu Dự án và Thông tin Nhóm

Dự án này phân tích **Online Shoppers Purchasing Intention Dataset**, tập trung vào việc hiểu hành vi người dùng trên website thương mại điện tử và dự đoán khả năng mua hàng (Revenue). Dữ liệu được thu thập ở **mức session** và phản ánh hành vi duyệt web, thông tin kỹ thuật, yếu tố mùa vụ và các chỉ số từ Google Analytics.

**Thành viên Nhóm:**

**Team Members:**

| Student ID | Name |
| ------ | ---- |
| 23127361 |  Thạch Ngọc Hân    |
| 23127466 |  Phan Như Quỳnh    |
| 23127488 |  Lê Thị Minh Thư    |

## 2. Nguồn Dataset và Mô tả

Dataset được lấy từ UCI Machine Learning Repository, bao gồm **10 thuộc tính số** và **8 thuộc tính phân loại**, mỗi dòng tương ứng với **một phiên truy cập (session)** của người dùng.

Dưới đây là bảng tổng hợp metadata của các thuộc tính chính trong dataset:

| Thuộc tính              | Kiểu dữ liệu    | Ý nghĩa                                                    | Ghi chú                         |
| ----------------------- | --------------- | ---------------------------------------------------------- | ------------------------------- |
| Administrative          | Numerical       | Số trang loại Administrative được xem                      | Đếm số lượng trang              |
| Administrative Duration | Numerical       | Tổng thời gian xem các trang Administrative                | Tính bằng giây                  |
| Informational           | Numerical       | Số trang loại Informational được xem                       | Trang FAQ, chính sách…          |
| Informational Duration  | Numerical       | Tổng thời gian xem các trang Informational                 |                                 |
| ProductRelated          | Numerical       | Số trang sản phẩm được xem                                 | Quan trọng cho dự đoán mua hàng |
| ProductRelated Duration | Numerical       | Tổng thời gian xem trang sản phẩm                          |                                 |
| BounceRate              | Numerical       | Bounce rate của **trang đầu tiên** trong session           | Từ Google Analytics             |
| ExitRate                | Numerical       | Exit rate của **trang cuối** trong session                 |                                 |
| PageValue               | Numerical       | Giá trị trung bình của các trang trong hành trình mua hàng | GA định nghĩa                   |
| SpecialDay              | Numerical (0–1) | Mức độ gần tới ngày đặc biệt                               | Ví dụ Valentine, Black Friday   |
| OperatingSystems        | Categorical       | Hệ điều hành của thiết bị truy cập                         | Windows, iOS, Android…          |
| Browser                 | Categorical       | Trình duyệt sử dụng                                        | Chrome, Firefox…                |
| Region                  | Categorical       | Mã khu vực địa lý của người truy cập                       | Từ GA, không phải quốc gia      |
| TrafficType             | Categorical       | Loại nguồn truy cập                                        | Direct, Organic, Referral…      |
| VisitorType             | Categorical     | Người dùng mới hay quay lại                                | Returning, New                  |
| Weekend                 | Boolean         | Truy cập vào cuối tuần                                     | True/False                      |
| Month                   | Categorical     | Tháng trong năm                                            | Jan–Dec                         |
| Revenue                 | Boolean         | Session có dẫn đến mua hàng không                          | Nhãn (Label)                    |

## 3. Danh sách các câu hỏi nghiên cứu
Dự án tập trung trả lời các câu hỏi nghiên cứu sau:
* 1. Mỗi nguồn traffic đóng góp như thế nào vào doanh thu, tương tác, ý định mua và thu hút khách mới trong toàn bộ funnel marketing?
* 2. Tại sao cùng là thời điểm có lượng truy cập đạt đỉnh, nhưng hiệu suất chuyển đổi lại trái ngược nhau giữa Tháng 5 và Tháng 11?
* 3. Chỉ số `PageValues` (Giá trị trang) đóng vai trò quyết định như thế nào trong việc định hình hành vi mua hàng và phân loại khách hàng trong phễu chuyển đổi?
* 4. Cuộc chiến giữa "Săn mới" và "Giữ cũ": Nhóm khách hàng nào (`VisitorType`) thực sự mang lại hiệu quả chuyển đổi cao hơn?
* 5. Làm thế nào để phân định các nhóm chân dung khách hàng (`Customer Personas`) dựa trên hành vi duyệt web nhằm cá nhân hóa chiến lược tiếp cận?
* 6. Làm thế nào để tối ưu hóa việc phân loại khách hàng bằng cách dự đoán khả năng mua hàng dựa trên sự tương tác giữa giá trị trang (`Page Values`) và các hành vi tương tác phi tuyến tính (`Duration` & `Exit Rates`) trong bối cảnh áp lực thời gian của các ngày lễ (`Special Days`)?

## 4. Key Findings Summary
Dựa trên quá trình phân tích dữ liệu và mô hình hóa, dự án rút ra 3 kết luận cốt lõi:

* **Chỉ số `PageValues` là yếu tố dự báo số 1:** Đây là biến quan trọng nhất quyết định hành vi mua hàng. Tỷ lệ chuyển đổi tăng vọt từ **3.9%** (khi PageValues = 0) lên **38.4%** (khi PageValues > 0). Chiến lược UX cần tập trung điều hướng người dùng vào các trang giá trị thay vì chỉ giữ chân họ ở lại lâu.
* **Nghịch lý Mùa vụ (Tháng 5 vs Tháng 11):** Lượng truy cập cao không đồng nghĩa với hiệu quả cao. Tháng 5 đạt đỉnh về traffic nhưng tỷ lệ chuyển đổi thấp (chủ yếu xem lướt). Ngược lại, Tháng 11 có traffic thấp hơn nhưng đạt doanh thu kỷ lục nhờ tệp khách hàng có mục đích mua sắm rõ ràng.
* **Sự áp đảo của Khách hàng mới:** Trái với giả định thông thường, **Khách hàng mới (New Visitors)** mới là động lực tăng trưởng chính với tỷ lệ chuyển đổi ~25%. Trong khi đó, Khách hàng quay lại có tỷ lệ thoát trang (Bounce Rate) cao gấp 4 lần.
* **Sự thật về Khách hàng quay lại:** Mô hình học máy đã đánh giá **trọng số âm** cho biến số "Khách hàng quay lại". Dữ liệu thực tế chứng minh rằng nhóm khách cũ trong tập dữ liệu này thường chỉ vào để so sánh giá hoặc kiểm tra thông tin rồi thoát nhanh, thay vì thực hiện hành vi mua hàng trung thành như kỳ vọng.

## 5. File Structure Explanation
* `01_Overview&DataCollection.ipynb`: Giới thiệu bài toán, tải dữ liệu và giải thích ý nghĩa các biến.
* `02_DataExploration.ipynb`: Khám phá dữ liệu (EDA), kiểm tra phân phối, xử lý giá trị thiếu (Missing values) và ngoại lai (Outliers).
* `03_DataAnalysis.ipynb`: Phân tích chuyên sâu sử dụng thuật toán, kĩ thuật trả lời các câu hỏi phân tích.
* `04_Modeling.ipynb`: Xây dựng và huấn luyện mô hình dự đoán (Random Forest), đánh giá mô hình qua Confusion Matrix.
* `05_Summary.ipynb`: Tổng kết dự án, đúc kết insight và định hướng phát triển trong tương lai.
```
├── 01_Overview&DataCollection.ipynb  
├── 02_DataExploration.ipynb       
├── 03_DataAnalysis.ipynb         
├── 04_Modeling.ipynb           
├── 05_Summary.ipynb                  
├── data ──├
├          ├── online_shoppers_intention.csv
└── README.md
```

## 6. How to Run Instructions
Để chạy dự án này trên máy cá nhân, vui lòng thực hiện lần lượt các bước sau qua Terminal (MacOS/Linux) hoặc Command Prompt (Windows):

### Bước 1: Cài đặt môi trường & Jupyter
Đảm bảo máy tính đã có Python. Cài đặt Jupyter Notebook nếu bạn chưa có:
```bash
pip install notebook
```
### Bước 2: Cài đặt các thư viện phụ thuộc
Chạy lệnh sau để cài đặt toàn bộ các thư viện cần thiết cho dự án:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

### Bước 3: Bố trí dữ liệu
Đảm bảo file dataset `online_shoppers_intention.csv` được đặt trong thư mục data với các

### Bước 4: Khởi chạy và thực thi
Đảm bảo file dataset `online_shoppers_intention.csv` được đặt trong thư mục data với các
* Khởi chạy và thực thi
```bash
jupyter notebook
```
* Chạy tuần tự các file 
    * `01_Overview&DataCollection.ipynb`
    * `02_DataExploration.ipynb`
    * `03_DataAnalysis.ipynb`
    * `04_Modeling.ipynb`
    * `05_Summary.ipynb`

## 7. Dependencies List
* `pandas` (Xử lý Dataframe)
* `numpy` (Tính toán số học)
* `matplotlib` (Trực quan hóa cơ bản)
* `seaborn` (Trực quan hóa nâng cao)
* `scikit-learn` (Các thuật toán Machine Learning: K-Means, Random Forest, Metrics)