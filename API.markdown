# Tài Liệu API ProjectMobile

## Tổng Quan
API ProjectMobile cung cấp một tập hợp các điểm cuối (endpoint) để quản lý xác thực người dùng, chủ đề, từ vựng, điểm số người dùng, và câu hỏi cho một ứng dụng di động. API hỗ trợ các thao tác như đăng ký người dùng, đăng nhập, khôi phục mật khẩu, quản lý chủ đề và từ vựng, tạo và lấy điểm số người dùng, cũng như tạo, lấy, cập nhật, và xóa câu hỏi. Tất cả phản hồi từ API đều ở định dạng JSON, và một số điểm cuối yêu cầu xác thực bằng Bearer Token.

## URL Cơ Sở
```
http://localhost:8989/v1/api
```

## Xác Thực
- **Bearer Token**: Yêu cầu cho các điểm cuối liên quan đến quản lý chủ đề, từ vựng, điểm số người dùng, và câu hỏi. Token được lấy thông qua điểm cuối `/auth/login` và phải được bao gồm trong tiêu đề `Authorization` dưới dạng `Bearer <token>` cho các yêu cầu cần xác thực.

## Các Điểm Cuối (Endpoints)

### 1. Đăng Nhập Người Dùng
#### **POST** `/auth/login`
Xác thực người dùng và trả về một Bearer Token để sử dụng cho các yêu cầu tiếp theo.

- **Dữ Liệu Yêu Cầu (Request Body)**:
  ```json
  {
    "username": "chuỗi",
    "password": "chuỗi"
  }
  ```
- **Ví Dụ**:
  ```json
  {
    "username": "haodo",
    "password": "Hao1234@"
  }
  ```
- **Phản Hồi (200 OK)**:
  ```json
  {
    "result": true,
    "data": {
      "result": true,
      "token": "chuỗi"
    },
    "message": "Đăng nhập thành công"
  }
  ```
- **Ví Dụ Phản Hồi**:
  ```json
  {
    "result": true,
    "data": {
      "result": true,
      "token": "eyJhbGciOiJIUzUxMiJ9..."
    },
    "message": "Đăng nhập thành công"
  }
  ```

### 2. Xác Minh Tài Khoản
#### **POST** `/auth/verify`
Xác minh tài khoản người dùng bằng email và mã OTP (Mật khẩu Một Lần).

- **Dữ Liệu Yêu Cầu**:
  ```json
  {
    "email": "chuỗi",
    "otp": "chuỗi"
  }
  ```
- **Ví Dụ**:
  ```json
  {
    "email": "dohao11129003@gmail.com",
    "otp": "683854"
  }
  ```
- **Phản Hồi (200 OK)**:
  ```json
  {
    "result": true,
    "message": "Xác minh thành công"
  }
  ```

### 3. Đăng Ký Tài Khoản
#### **POST** `/auth/register`
Đăng ký một tài khoản người dùng mới và gửi mã OTP đến email đã cung cấp.

- **Dữ Liệu Yêu Cầu**:
  ```json
  {
    "username": "chuỗi",
    "email": "chuỗi",
    "password": "chuỗi"
  }
  ```
- **Ví Dụ**:
  ```json
  {
    "username": "haodo",
    "email": "dohao1129003@gmail.com",
    "password": "Hao1234@"
  }
  ```
- **Phản Hồi (200 OK)**:
  ```json
  {
    "result": true,
    "message": "Đăng ký thành công. Một mã OTP đã được gửi đến email của bạn"
  }
  ```

### 4. Quên Mật Khẩu
#### **POST** `/auth/forget-password`
Gửi email đặt lại mật khẩu đến địa chỉ email được cung cấp.

- **Dữ Liệu Yêu Cầu**:
  ```json
  {
    "email": "chuỗi"
  }
  ```
- **Ví Dụ**:
  ```json
  {
    "email": "haotinh2003@gmail.com"
  }
  ```
- **Phản Hồi (200 OK)**:
  ```json
  {
    "result": true,
    "message": "Gửi email thành công"
  }
  ```

### 5. Đặt Lại Mật Khẩu
#### **POST** `/auth/reset-password`
Đặt lại mật khẩu cho địa chỉ email được chỉ định.

- **Dữ Liệu Yêu Cầu**:
  ```json
  {
    "email": "chuỗi",
    "password": "chuỗi"
  }
  ```
- **Ví Dụ**:
  ```json
  {
    "email": "haotinh2003@gmail.com",
    "password": "Hao1234@"
  }
  ```
- **Phản Hồi (200 OK)**:
  ```json
  {
    "result": true,
    "message": "Đặt lại mật khẩu thành công"
  }
  ```

### 6. Lấy Thông Tin Người Dùng
#### **GET** `/user/get`
Lấy thông tin chi tiết của người dùng đã xác thực.

- **Xác Thực**: Yêu cầu Bearer Token.
- **Phản Hồi (200 OK)**:
  ```json
  {
    "result": true,
    "data": {
      "account": {
        "username": "haodo",
        "email": "dohao11129003@gmail.com"
      }
    },
    "message": "Lấy thông tin người dùng thành công"
  }
  ```

### 7. Tạo Chủ Đề
#### **POST** `/topic/create`
Tạo một chủ đề mới. Yêu cầu xác thực.

- **Dữ Liệu Yêu Cầu**:
  ```json
  {
    "imageView": "chuỗi",
    "topic": "chuỗi"
  }
  ```
- **Ví Dụ**:
  ```json
  {
    "imageView": "imageView",
    "topic": "Sport"
  }
  ```
- **Phản Hồi (200 OK)**:
  ```json
  {
    "result": true,
    "message": "Tạo chủ đề thành công"
  }
  ```

### 8. Lấy Danh Sách Chủ Đề
#### **GET** `/topic/list`
Lấy danh sách tất cả các chủ đề. Yêu cầu xác thực.

- **Phản Hồi (200 OK)**:
  ```json
  {
    "result": true,
    "data": [
      {
        "id": "chuỗi",
        "imageView": "chuỗi",
        "topic": "chuỗi"
      }
    ],
    "message": "Lấy danh sách chủ đề thành công"
  }
  ```
- **Ví Dụ Phản Hồi**:
  ```json
  {
    "result": true,
    "data": [
      {
        "id": "UTETopicModel00000001",
        "imageView": "imageView",
        "topic": "Career"
      },
      {
        "id": "UTETopicModel00000002",
        "imageView": "imageView",
        "topic": "Sport"
      }
    ],
    "message": "Lấy danh sách chủ đề thành công"
  }
  ```

### 9. Cập Nhật Chủ Đề
#### **PUT** `/topic/update`
Cập nhật một chủ đề hiện có theo ID của nó. Yêu cầu xác thực.

- **Dữ Liệu Yêu Cầu**:
  ```json
  {
    "id": "chuỗi",
    "imageView": "chuỗi",
    "topic": "chuỗi"
  }
  ```
- **Ví Dụ**:
  ```json
  {
    "id": "UTETopicModel00000002",
    "imageView": "view",
    "topic": "Entertainment"
  }
  ```
- **Phản Hồi (200 OK)**:
  ```json
  {
    "result": true,
    "message": "Cập nhật chủ đề thành công"
  }
  ```

### 10. Xóa Chủ Đề
#### **DELETE** `/topic/delete/{topicId}`
Xóa một chủ đề theo ID của nó. Yêu cầu xác thực.

- **Tham Số Đường Dẫn**:
  - `topicId`: ID của chủ đề cần xóa (ví dụ: `UTETopicModel00000002`).
- **Phản Hồi (200 OK)**:
  ```json
  {
    "result": true,
    "message": "Xóa chủ đề thành công"
  }
  ```

### 11. Tạo Từ Vựng
#### **POST** `/vocabulary/create`
Tạo một mục từ vựng mới trong một chủ đề được chỉ định. Yêu cầu xác thực.

- **Dữ Liệu Yêu Cầu**:
  ```json
  {
    "image": "chuỗi",
    "word": "chuỗi",
    "answer": "chuỗi",
    "topicId": "chuỗi"
  }
  ```
- **Ví Dụ**:
  ```json
  {
    "image": "image",
    "word": "Engineer",
    "answer": "Kỹ sư",
    "topicId": "UTETopicModel00000001"
  }
  ```
- **Phản Hồi (200 OK)**:
  ```json
  {
    "result": true,
    "message": "Tạo từ vựng thành công"
  }
  ```

### 12. Lấy Danh Sách Từ Vựng
#### **GET** `/vocabulary/list/{topicId}`
Lấy danh sách các mục từ vựng cho một chủ đề cụ thể. Yêu cầu xác thực.

- **Tham Số Đường Dẫn**:
  - `topicId`: ID của chủ đề (ví dụ: `UTETopicModel00000001`).
- **Phản Hồi (200 OK)**:
  ```json
  {
    "result": true,
    "data": {
      "content": [
        {
          "id": "chuỗi",
          "image": "chuỗi",
          "word": "chuỗi",
          "answer": "chuỗi"
        }
      ],
      "totalElements": số nguyên,
      "totalPages": số nguyên
    }
  }
  ```
- **Ví Dụ Phản Hồi**:
  ```json
  {
    "result": true,
    "data": {
      "content": [
        {
          "id": "UTEVocabularyModel00000001",
          "image": "image",
          "word": "Doctor",
          "answer": "Bác sĩ"
        },
        {
          "id": "UTEVocabularyModel00000002",
          "image": "image",
          "word": "Engineer",
          "answer": "Kỹ sư"
        }
      ],
      "totalElements": 2,
      "totalPages": 1
    }
  }
  ```

### 13. Cập Nhật Từ Vựng
#### **PUT** `/vocabulary/update`
Cập nhật một mục từ vựng hiện có theo ID của nó. Yêu cầu xác thực.

- **Dữ Liệu Yêu Cầu**:
  ```json
  {
    "id": "chuỗi",
    "image": "chuỗi",
    "word": "chuỗi",
    "answer": "chuỗi",
    "topicId": "chuỗi"
  }
  ```
- **Ví Dụ**:
  ```json
  {
    "id": "UTEVocabularyModel00000001",
    "image": "image",
    "word": "Chef",
    "answer": "Đầu bếp",
    "topicId": "UTETopicModel00000001"
  }
  ```
- **Phản Hồi (200 OK)**:
  ```json
  {
    "result": true,
    "message": "Cập nhật từ vựng thành công"
  }
  ```

### 14. Xóa Từ Vựng
#### **DELETE** `/vocabulary/delete/{vocabularyId}`
Xóa một mục từ vựng theo ID của nó. Yêu cầu xác thực.

- **Tham Số Đường Dẫn**:
  - `vocabularyId`: ID của mục từ vựng cần xóa (ví dụ: `UTEVocabularyModel00000002`).
- **Phản Hồi (200 OK)**:
  ```json
  {
    "result": true,
    "message": "Xóa từ vựng thành công"
  }
  ```

### 15. Tạo Điểm Số Người Dùng
#### **POST** `/user-point/create`
Tạo một mục điểm số người dùng mới. Yêu cầu xác thực.

- **Dữ Liệu Yêu Cầu**:
  ```json
  {
    "point": số nguyên
  }
  ```
- **Ví Dụ**:
  ```json
  {
    "point": 80
  }
  ```
- **Phản Hồi (200 OK)**:
  ```json
  {
    "result": true,
    "message": "Tạo điểm số người dùng thành công"
  }
  ```

### 16. Lấy Danh Sách Điểm Số Người Dùng
#### **GET** `/user-point/list`
Lấy danh sách điểm số của người dùng đã xác thực. Yêu cầu xác thực.

- **Phản Hồi (200 OK)**:
  ```json
  {
    "result": true,
    "data": [
      {
        "id": "chuỗi",
        "user": {
          "account": {
            "username": "chuỗi",
            "email": "chuỗi"
          }
        },
        "point": số nguyên,
        "time": "chuỗi"
      }
    ]
  }
  ```
- **Ví Dụ Phản Hồi**:
  ```json
  {
    "result": true,
    "data": [
      {
        "id": "UTEUserPoint00000001",
        "user": {
          "account": {
            "username": "trinhhao",
            "email": "trinhthunghao2003@gmail.com"
          }
        },
        "point": 70,
        "time": "09/05/2025 11:20:01"
      },
      {
        "id": "UTEUserPoint00000002",
        "user": {
          "account": {
            "username": "haodo",
            "email": "dohao1129003@gmail.com"
          }
        },
        "point": 50,
        "time": "10/05/2025 09:15:30"
      }
    ]
  }
  ```

### 17. Tạo Câu Hỏi
#### **POST** `/question/create`
Tạo một câu hỏi mới. Yêu cầu xác thực.

- **Dữ Liệu Yêu Cầu**:
  ```json
  {
    "question": "chuỗi",
    "answer": "chuỗi",
    "allChoice": "chuỗi"
  }
  ```
- **Ví Dụ**:
  ```json
  {
    "question": "She ___ her homework every day.",
    "answer": "does",
    "allChoice": "does do did doing"
  }
  ```
- **Phản Hồi (200 OK)**:
  ```json
  {
    "result": true,
    "message": "Tạo câu hỏi thành công"
  }
  ```

### 18. Lấy Câu Hỏi
#### **GET** `/question/get/{questionId}`
Lấy chi tiết của một câu hỏi cụ thể theo ID của nó. Yêu cầu xác thực.

- **Tham Số Đường Dẫn**:
  - `questionId`: ID của câu hỏi (ví dụ: `UTEQuestion00000001`).
- **Phản Hồi (200 OK)**:
  ```json
  {
    "result": true,
    "data": {
      "id": "chuỗi",
      "question": "chuỗi",
      "answer": "chuỗi",
      "allChoice": "chuỗi"
    },
    "message": "Lấy câu hỏi thành công"
  }
  ```
- **Ví Dụ Phản Hồi**:
  ```json
  {
    "result": true,
    "data": {
      "id": "UTEQuestion00000001",
      "question": "She ___ her homework every day.",
      "answer": "does",
      "allChoice": "does do did doing"
    },
    "message": "Lấy câu hỏi thành công"
  }
  ```

### 19. Lấy Danh Sách Câu Hỏi
#### **GET** `/question/list`
Lấy danh sách tất cả các câu hỏi. Yêu cầu xác thực.

- **Phản Hồi (200 OK)**:
  ```json
  {
    "result": true,
    "data": {
      "content": [
        {
          "id": "chuỗi",
          "question": "chuỗi",
          "answer": "chuỗi",
          "allChoice": "chuỗi"
        }
      ],
      "totalElements": số nguyên,
      "totalPages": số nguyên
    }
  }
  ```
- **Ví Dụ Phản Hồi**:
  ```json
  {
    "result": true,
    "data": {
      "content": [
        {
          "id": "UTEQuestion00000001",
          "question": "She ___ her homework every day.",
          "answer": "does",
          "allChoice": "does do did doing"
        },
        {
          "id": "UTEQuestion00000002",
          "question": "He ___ to the store yesterday.",
          "answer": "went",
          "allChoice": "went goes go gone"
        }
      ],
      "totalElements": 2,
      "totalPages": 1
    }
  }
  ```

### 20. Cập Nhật Câu Hỏi
#### **PUT** `/question/update`
Cập nhật một câu hỏi hiện có theo ID của nó. Yêu cầu xác thực.

- **Dữ Liệu Yêu Cầu**:
  ```json
  {
    "id": "chuỗi",
    "question": "chuỗi",
    "answer": "chuỗi",
    "allChoice": "chuỗi"
  }
  ```
- **Ví Dụ**:
  ```json
  {
    "id": "UTEQuestion00000001",
    "question": "She ___ a book last night.",
    "answer": "read",
    "allChoice": "read reads reading readed"
  }
  ```
- **Phản Hồi (200 OK)**:
  ```json
  {
    "result": true,
    "message": "Cập nhật câu hỏi thành công"
  }
  ```

### 21. Xóa Câu Hỏi
#### **DELETE** `/question/delete/{questionId}`
Xóa một câu hỏi theo ID của nó. Yêu cầu xác thực.

- **Tham Số Đường Dẫn**:
  - `questionId`: ID của câu hỏi cần xóa (ví dụ: `UTEQuestion00000001`).
- **Phản Hồi (200 OK)**:
  ```json
  {
    "result": true,
    "message": "Xóa câu hỏi thành công"
  }
  ```

## Xử Lý Lỗi
Tất cả các điểm cuối đều trả về một trường `result` trong phản hồi. Nếu `result` là `false`, một thông báo lỗi sẽ được cung cấp trong trường `message`.

- **Ví Dụ Phản Hồi Lỗi**:
  ```json
  {
    "result": false,
    "message": "Thông tin xác thực không hợp lệ"
  }
  ```

## Ghi Chú
- Đảm bảo rằng Bearer Token được bao gồm trong tiêu đề `Authorization` cho tất cả các điểm cuối yêu cầu xác thực.
- Tất cả các yêu cầu có dữ liệu thân (body) nên được gửi dưới dạng JSON thô.
- API mặc định chạy trên `localhost:8989` cho mục đích phát triển.