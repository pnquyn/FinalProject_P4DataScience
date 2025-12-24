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
| OperatingSystems        | Numerical       | Hệ điều hành của thiết bị truy cập                         | Windows, iOS, Android…          |
| Browser                 | Numerical       | Trình duyệt sử dụng                                        | Chrome, Firefox…                |
| Region                  | Numerical       | Mã khu vực địa lý của người truy cập                       | Từ GA, không phải quốc gia      |
| TrafficType             | Numerical       | Loại nguồn truy cập                                        | Direct, Organic, Referral…      |
| VisitorType             | Categorical     | Người dùng mới hay quay lại                                | Returning, New                  |
| Weekend                 | Boolean         | Truy cập vào cuối tuần                                     | True/False                      |
| Month                   | Categorical     | Tháng trong năm                                            | Jan–Dec                         |
| Revenue                 | Boolean         | Session có dẫn đến mua hàng không                          | Nhãn (Label)                    |

## 3. Research Questions List

## 4. Key Findings Summary

## 5. File Structure Explanation

## 6. How to Run Instructions

## 7. Dependencies List
