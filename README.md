src
│
├── main
│   ├── java
│   │   └── com.example.shoeshop
│   │       ├── config           // Cấu hình (Security, CORS, Bean...)
│   │       ├── controller       // Xử lý API request
│   │       ├── dto              // Data Transfer Objects
│   │       ├── entity           // Các class ánh xạ bảng database
│   │       ├── exception        // Xử lý ngoại lệ tùy chỉnh
│   │       ├── repository       // Tầng DAO, giao tiếp database
│   │       ├── service          // Xử lý logic nghiệp vụ
│   │       └── util             // Các tiện ích dùng chung
│   │
│   └── resources
│       ├── application.properties // Cấu hình ứng dụng
│       └── static               // Tài nguyên tĩnh (nếu có)
│
└── test
└── java
└── com.example.shoeshop
├── controller       // Test Controller
├── service          // Test Service
└── repository       // Test Repository




I am planning to work on a project about selling shoes using Java Spring Boot, and I will only focus on the Backend. You need to play the role of a programmer with 30 years of experience in Java programming. You have gone through many projects and want to guide me as a new programmer to complete projects. You are always friendly and guide me on the best solution, comparing it with other solutions to highlight the advantages of your approach. Finally, you always present things in an easy-to-understand, comprehensive manner, without worrying about the length. You also always suggest other parts and ask me if I understand what you are saying.
và vì sao lại cho tôi dùng jpa repostiory mà không dùng cái hibernate thế 




-------------------------------------------------------------------------------
write unit test for this class sao cho đạt các tiêu chí sau: 

- Kiểm tra logic của từng method một cách độc lập, không phụ thuộc vào các thành phần bên ngoài.
- Mock AccountRepository để giả lập dữ liệu, giúp tách biệt Unit Test khỏi database.
- Đảm bảo mọi trường hợp đều được xử lý, bao gồm cả:
- Trường hợp thành công (Success Scenarios)
- Trường hợp thất bại (Failure Scenarios)
- Ngoại lệ (Exceptions)

đầu tiên là 2.1. Method: createAccount()
Tạo tài khoản thành công	Khi username và email chưa tồn tại, tạo tài khoản mới thành công.
Email đã tồn tại	Ném IllegalArgumentException khi email đã tồn tại trong database.
Username đã tồn tại	Ném IllegalArgumentException khi username đã tồn tại.
Thiếu Role và Status	Đảm bảo Role.USER và Status.ACTIVE được đặt mặc định.

2.2. Method: updateAccount()

Cập nhật thành công	Khi userId tồn tại, cập nhật thông tin thành công.
Tài khoản không tồn tại	Ném IllegalArgumentException khi userId không tồn tại.
Cập nhật Role và Status	Cập nhật Role và Status nếu có quyền (ví dụ: admin).
Không thay đổi Role và Status	Không thay đổi Role và Status khi không có quyền.

2.3. Method: deleteAccount()

Xóa tài khoản thành công	Khi userId tồn tại, tài khoản được xóa thành công.
Tài khoản không tồn tại	Ném IllegalArgumentException khi userId không tồn tại.

2.4. Method: findByUsername()

Trường hợp cần test	Mô tả
Tìm thấy tài khoản	Trả về Optional.of(Account) khi username tồn tại.
Không tìm thấy tài khoản	Trả về Optional.empty() khi username không tồn tại.

2.5. Method: findByEmail()

Tìm thấy tài khoản	Trả về Optional.of(Account) khi email tồn tại.
Không tìm thấy tài khoản	Trả về Optional.empty() khi email không tồn tại.

2.6. Method: findById()

Tìm thấy tài khoản	Trả về Optional.of(Account) khi userId tồn tại.
Không tìm thấy tài khoản	Trả về Optional.empty() khi userId không tồn tại.

2.7. Method: findAll()
Danh sách không rỗng	Trả về danh sách tài khoản khi có tài khoản trong database.
Danh sách rỗng	Trả về danh sách rỗng khi không có tài khoản nào.

2.8. Method: findByRole()
Tìm thấy tài khoản theo Role	Trả về danh sách tài khoản khi Role tồn tại.
Không tìm thấy tài khoản	Trả về danh sách rỗng khi Role không tồn tại.

2.9. Method: findByStatus()
Tìm thấy tài khoản theo Status	Trả về danh sách tài khoản khi Status tồn tại.
Không tìm thấy tài khoản	Trả về danh sách rỗng khi Status không tồn tại.


