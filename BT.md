# 📚 HỆ THỐNG QUẢN LÝ THƯ VIỆN

## 🔍 TỔNG QUAN DỰ ÁN

Hệ thống Quản lý Thư viện là một ứng dụng Java được xây dựng nhằm quản lý hiệu quả các hoạt động của thư viện học thuật. Dự án được thiết kế để minh họa và áp dụng đầy đủ các nguyên lý lập trình hướng đối tượng (OOP) cùng với việc sử dụng cấu trúc dữ liệu ArrayList trong Java.

## 🎯 MỤC ĐÍCH XÂY DỰNG

### Mục đích học tập:

- **Thực hành OOP**: Áp dụng 4 nguyên lý cơ bản của lập trình hướng đối tượng
- **Quản lý Collection**: Sử dụng ArrayList để quản lý tập hợp các đối tượng
- **Thiết kế hệ thống**: Xây dựng một hệ thống hoàn chỉnh với nhiều lớp tương tác
- **Xử lý nghiệp vụ**: Triển khai logic nghiệp vụ thực tế của thư viện

### Mục đích thực tiễn:

- **Quản lý tài liệu**: Theo dõi sách, tạp chí, DVD trong thư viện
- **Quản lý người dùng**: Quản lý sinh viên, giáo viên, thủ thư
- **Quản lý mượn/trả**: Kiểm soát việc cho mượn và thu hồi tài liệu
- **Báo cáo thống kê**: Cung cấp thông tin tổng quan về hoạt động thư viện

## 🏛️ KIẾN TRÚC HỆ THỐNG

### Phân tầng ứng dụng:

```
┌─────────────────────────────────────┐
│           PRESENTATION LAYER         │
│              (Main.java)             │
├─────────────────────────────────────┤
│           BUSINESS LAYER             │
│            (Library.java)            │
├─────────────────────────────────────┤
│            ENTITY LAYER              │
│    (Document, User, BorrowRecord)    │
└─────────────────────────────────────┘
```

### Cấu trúc lớp (Class Hierarchy):

```
Document (Abstract)
├── Book
├── Magazine
└── DVD

User (Abstract)
├── Student
├── Teacher
└── Librarian

Standalone Classes:
├── BorrowRecord
├── Library
└── Main
```

## 📊 MÔ HÌNH DỮ LIỆU

### 1. Thực thể Tài liệu (Document Entity)

**Lớp cha trừu tượng**: Document

- Chứa thông tin cơ bản: ID, tiêu đề, nhà xuất bản, trạng thái
- Định nghĩa các phương thức trừu tượng cho các lớp con

**Các lớp con cụ thể**:

- **Book** (Sách): Thêm thông tin tác giả, số trang, thể loại
- **Magazine** (Tạp chí): Thêm số phát hành, tháng, danh mục
- **DVD**: Thêm thời lượng, đạo diễn, thể loại

### 2. Thực thể Người dùng (User Entity)

**Lớp cha trừu tượng**: User

- Chứa thông tin cơ bản: ID người dùng, tên, email, danh sách mượn
- Định nghĩa giới hạn mượn khác nhau cho từng loại người dùng

**Các lớp con cụ thể**:

- **Student** (Sinh viên): Giới hạn 3 tài liệu, có mã SV, chuyên ngành
- **Teacher** (Giáo viên): Giới hạn 5 tài liệu, có mã GV, khoa, môn dạy
- **Librarian** (Thủ thư): Giới hạn 10 tài liệu, có ca làm, quyền quản lý

### 3. Thực thể Phiếu mượn (BorrowRecord Entity)

- Ghi lại thông tin về việc mượn tài liệu
- Tính toán ngày hết hạn, phí phạt (nếu có)
- Theo dõi trạng thái: đang mượn, quá hạn, đã trả

## ⚙️ CHỨC NĂNG HỆ THỐNG

### 🔧 Quản lý Tài liệu

1. **Thêm tài liệu mới**

   - Kiểm tra trùng lặp ID
   - Hỗ trợ nhiều loại: sách, tạp chí, DVD
   - Tự động đặt trạng thái "có sẵn"

2. **Tìm kiếm tài liệu**

   - Tìm theo ID chính xác
   - Tìm theo tên (hỗ trợ tìm kiếm mờ)
   - Lọc theo trạng thái có sẵn

3. **Quản lý tồn kho**
   - Hiển thị tất cả tài liệu
   - Hiển thị chỉ tài liệu có sẵn
   - Thống kê theo loại tài liệu

### 👥 Quản lý Người dùng

1. **Đăng ký người dùng mới**

   - Hỗ trợ 3 loại: sinh viên, giáo viên, thủ thư
   - Kiểm tra trùng lặp thông tin
   - Thiết lập giới hạn mượn tự động

2. **Tra cứu thông tin**
   - Tìm người dùng theo ID
   - Hiển thị lịch sử mượn
   - Kiểm tra trạng thái tài khoản

### 📋 Quản lý Mượn/Trả

1. **Cho mượn tài liệu**

   - Kiểm tra tình trạng tài liệu
   - Kiểm tra giới hạn mượn của người dùng
   - Cập nhật trạng thái tự động
   - Ghi lại thông tin mượn

2. **Thu hồi tài liệu**
   - Xác nhận người trả
   - Cập nhật trạng thái tài liệu
   - Tính toán phí phạt (nếu có)
   - Ghi nhận thời gian trả

### 📈 Báo cáo và Thống kê

1. **Thống kê tổng quan**

   - Tổng số tài liệu/người dùng
   - Tỷ lệ tài liệu đang cho mượn
   - Phân loại theo từng nhóm

2. **Phân tích dữ liệu**
   - Top tài liệu được mượn nhiều
   - Thống kê theo loại người dùng
   - Báo cáo tình trạng quá hạn

## 🔐 NGUYÊN LÝ LẬP TRÌNH ÁP DỤNG

### 1. Tính Kế thừa (Inheritance)

- **Cây thừa kế Document**: Book, Magazine, DVD kế thừa từ Document
- **Cây thừa kế User**: Student, Teacher, Librarian kế thừa từ User
- **Tái sử dụng code**: Các thuộc tính và phương thức chung được định nghĩa ở lớp cha

### 2. Tính Đa hình (Polymorphism)

- **Method Overriding**: Các lớp con override abstract methods của lớp cha
- **Runtime Polymorphism**: Cùng một interface nhưng hành vi khác nhau
- **Collection Polymorphism**: ArrayList<Document> có thể chứa Book, Magazine, DVD

### 3. Tính Đóng gói (Encapsulation)

- **Access Modifiers**: Private fields, public methods, protected inheritance
- **Data Hiding**: Dữ liệu nhạy cảm được bảo vệ
- **Controlled Access**: Truy cập dữ liệu thông qua getter/setter methods

### 4. Tính Trừu tượng (Abstraction)

- **Abstract Classes**: Document và User là các lớp trừu tượng
- **Abstract Methods**: Ép buộc lớp con phải implement
- **Interface-like Design**: Định nghĩa contract cho các lớp con

## 💾 CẤU TRÚC DỮ LIỆU

### ArrayList Usage:

```java
// Quản lý collection trong Library class
ArrayList<Document> documents    // Danh sách tất cả tài liệu
ArrayList<User> users           // Danh sách tất cả người dùng

// Quản lý mượn trong User class
ArrayList<Document> borrowedDocuments // Tài liệu đang mượn
```

### Lợi ích của ArrayList:

- **Dynamic Sizing**: Tự động mở rộng kích thước
- **Type Safety**: Generic types đảm bảo type safety
- **Rich API**: Nhiều methods hữu ích (add, remove, contains, iterator)
- **Performance**: Truy cập ngẫu nhiên O(1), tìm kiếm O(n)

## 🎮 HƯỚNG DẪN SỬ DỤNG

### Compilation và Execution:

```bash
# Biên dịch tất cả files
javac Baitap/*.java

# Chạy chương trình demo
java Baitap.Main
```

### Demo Workflow:

1. **Khởi tạo thư viện** với tên và địa chỉ
2. **Thêm tài liệu** đa dạng (sách, tạp chí, DVD)
3. **Đăng ký người dùng** các loại khác nhau
4. **Mô phỏng cho mượn** với các quy tắc nghiệp vụ
5. **Hiển thị thống kê** và báo cáo tổng quan

## 📋 KẾT LUẬN

Hệ thống Quản lý Thư viện này không chỉ là một bài tập lập trình đơn thuần mà còn là một dự án minh họa hoàn chỉnh cho việc áp dụng các nguyên lý OOP trong thực tế. Thông qua dự án này, sinh viên có thể:

- ✅ **Hiểu sâu về OOP**: Thực hành trực tiếp 4 nguyên lý cơ bản
- ✅ **Quản lý Collection**: Thành thạo việc sử dụng ArrayList
- ✅ **Thiết kế hệ thống**: Học cách phân tích và thiết kế một hệ thống hoàn chỉnh
- ✅ **Xử lý nghiệp vụ**: Triển khai logic nghiệp vụ phức tạp
- ✅ **Kỹ năng debug**: Phát triển khả năng tìm và sửa lỗi
- ✅ **Best practices**: Học các quy tắc viết code sạch và maintainable
