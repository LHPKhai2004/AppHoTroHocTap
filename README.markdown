# Ứng Dụng Hỗ Trợ Học Tập

## Tổng Quan
Ứng dụng Hỗ trợ Học tập là một ứng dụng di động trên nền tảng Android, được phát triển như một dự án cuối kỳ cho môn Lập trình Mobile tại Trường Đại học Sư phạm Kỹ thuật Thành phố Hồ Chí Minh (HCMUTE). Ứng dụng nhằm hỗ trợ người dùng học tiếng Anh thông qua các tính năng tương tác như học từ vựng, luyện nghe, làm bài trắc nghiệm, và bảng xếp hạng cạnh tranh. Dự án tích hợp cả phần giao diện người dùng (Android) và phần hậu cần (API) để mang lại trải nghiệm học tập liền mạch.

## Tính Năng
Ứng dụng cung cấp các tính năng cốt lõi sau:

1. **Đăng Nhập Người Dùng**  
   - **Mục Tiêu**: Xác thực danh tính người dùng để truy cập ứng dụng.  
   - **Đầu Vào**: Tên người dùng, mật khẩu.  
   - **Đầu Ra**: Truy cập thành công vào màn hình chính (LayoutActivity) hoặc thông báo lỗi nếu thông tin không hợp lệ.  
   - **Giá Trị**: Đảm bảo an toàn dữ liệu, cá nhân hóa trải nghiệm học tập và lưu trữ mã xác thực.

2. **Đăng Ký Tài Khoản**  
   - **Mục Tiêu**: Hỗ trợ người dùng mới tạo tài khoản để sử dụng ứng dụng.  
   - **Đầu Vào**: Tên người dùng, email, mật khẩu, mã OTP xác minh.  
   - **Đầu Ra**: Tài khoản được tạo thành công và chuyển hướng đến đăng nhập, hoặc thông báo lỗi nếu thông tin không hợp lệ.  
   - **Giá Trị**: Thu hút người dùng mới, mở rộng cơ sở người dùng và cung cấp lộ trình học tập cá nhân hóa.

3. **Quên Mật Khẩu**  
   - **Mục Tiêu**: Cho phép người dùng khôi phục quyền truy cập tài khoản khi quên mật khẩu.  
   - **Đầu Vào**: Email, mã OTP, mật khẩu mới.  
   - **Đầu Ra**: Đặt lại mật khẩu thành công hoặc thông báo lỗi nếu email không tồn tại hoặc OTP không hợp lệ.  
   - **Giá Trị**: Cải thiện trải nghiệm người dùng, đảm bảo không mất quyền truy cập vào tài khoản.

4. **Học Từ Vựng**  
   - **Mục Tiêu**: Giúp người dùng học và ghi nhớ từ vựng tiếng Anh theo chủ đề.  
   - **Đầu Vào**: Lựa chọn chủ đề từ vựng từ TopicActivity.  
   - **Đầu Ra**: Hiển thị danh sách từ vựng với nghĩa, ví dụ và hình ảnh minh họa (nếu có).  
   - **Giá Trị**: Xây dựng vốn từ vựng hiệu quả, hỗ trợ giao tiếp và đọc hiểu tiếng Anh.

5. **Luyện Nghe**  
   - **Mục Tiêu**: Phát triển kỹ năng nghe tiếng Anh thông qua các bài nghe thực tế.  
   - **Đầu Vào**: Nhấn vào bài nghe trong ListeningActivity.  
   - **Đầu Ra**: Phát âm thanh, hiển thị câu hỏi trắc nghiệm liên quan và thông báo đáp án đúng/sai; lưu kết quả nếu cần.  
   - **Giá Trị**: Nâng cao khả năng nghe hiểu, cải thiện phản xạ ngôn ngữ trong các tình huống thực tế.

6. **Bảng Xếp Hạng**  
   - **Mục Tiêu**: Khuyến khích người dùng cạnh tranh và duy trì động lực học tập thông qua xếp hạng điểm số.  
   - **Đầu Vào**: Điểm số từ các bài kiểm tra (trong MultipleChoiceActivity) và thời gian hoàn thành.  
   - **Đầu Ra**: Hiển thị bảng xếp hạng với tên người dùng, điểm số và thời gian.  
   - **Giá Trị**: Tạo động lực học tập, thúc đẩy tinh thần cạnh tranh lành mạnh.

7. **Trắc Nghiệm Từ Vựng**  
   - **Mục Tiêu**: Kiểm tra và củng cố kiến thức từ vựng, ngữ pháp qua các câu hỏi trắc nghiệm.  
   - **Đầu Vào**: Lựa chọn đáp án trong MultipleChoiceActivity.  
   - **Đầu Ra**: Hiển thị kết quả đúng/sai, điểm số và chuyển hướng đến ResultActivity khi hoàn thành.  
   - **Giá Trị**: Giúp người dùng ôn tập hiệu quả, đánh giá trình độ và cải thiện kỹ năng ngôn ngữ.

## Giao Diện Người Dùng
Ứng dụng sở hữu giao diện trực quan và thân thiện, được thiết kế để tối ưu hóa trải nghiệm học tập. Dưới đây là mô tả giao diện cho từng tính năng chính:

1. **Đăng Nhập Người Dùng (LoginActivity)**  
   - **Bố Cục**: Giao diện đơn giản với hai trường `EditText` cho tên người dùng và mật khẩu, một `Button` để đăng nhập, và các liên kết `TextView` cho đăng ký và khôi phục mật khẩu.  
   - **Thành Phần**: Trường nhập liệu, nút đăng nhập, liên kết điều hướng.  
   - **Mục Đích**: Cung cấp điểm truy cập an toàn và dễ dàng vào ứng dụng.

2. **Đăng Ký Tài Khoản (SignUpActivity)**  
   - **Bố Cục**: Biểu mẫu với các trường `EditText` cho tên người dùng, email, mật khẩu và xác nhận mật khẩu, sau đó là trường nhập OTP (hiển thị sau khi đăng ký). Bao gồm một `Button` để gửi và một `ProgressBar` cho trạng thái tải.  
   - **Thành Phần**: Trường nhập liệu, bố cục xác minh OTP, nút gửi, chỉ báo tiến trình.  
   - **Mục Đích**: Hướng dẫn người dùng tạo tài khoản với phản hồi xác nhận rõ ràng.

3. **Quên Mật Khẩu (ForgotPasswordActivity)**  
   - **Bố Cục**: Giao diện dựa trên hộp thoại với ba giai đoạn: nhập email, xác minh OTP, và đặt lại mật khẩu. Mỗi giai đoạn sử dụng `AlertDialog` với các thành phần `EditText` và `Button`.  
   - **Thành Phần**: Trường nhập email, OTP, mật khẩu, nút hành động, tùy chọn hủy.  
   - **Mục Đích**: Đơn giản hóa quá trình khôi phục mật khẩu theo từng bước.

4. **Học Từ Vựng (TopicActivity & VocabularyActivity)**  
   - **Bố Cục**: TopicActivity hiển thị một `ListView` các chủ đề với `Toolbar` để điều hướng. VocabularyActivity hiển thị `ListView` các từ vựng, mỗi từ bao gồm từ, nghĩa và hình ảnh (nếu có).  
   - **Thành Phần**: ListView, Toolbar, TextView (từ/nghĩa), ImageView (hình minh họa).  
   - **Mục Đích**: Sắp xếp từ vựng theo chủ đề để dễ dàng truy cập và học tập trực quan.

5. **Luyện Nghe (ListeningActivity)**  
   - **Bố Cục**: Bao gồm phần điều khiển media với các `Button` (bắt đầu, dừng, tiếp theo), một `SeekBar` cho tiến trình âm thanh, và `TextView` để theo dõi thời gian. Có `ImageView` cho hình ảnh ngữ cảnh và các `RadioButton` để chọn đáp án.  
   - **Thành Phần**: Nút điều khiển media, SeekBar, hiển thị thời gian, hình ảnh, nhóm radio.  
   - **Mục Đích**: Cung cấp giao diện tương tác cho việc học và kiểm tra dựa trên âm thanh.

6. **Bảng Xếp Hạng (LeaderBoardActivity)**  
   - **Bố Cục**: Một `ListView` hiển thị người dùng được xếp hạng với một `Toolbar` để điều hướng. Mỗi mục trong danh sách hiển thị tên người dùng, điểm số, thời gian, và biểu tượng xếp hạng (`ImageView`).  
   - **Thành Phần**: ListView, Toolbar, TextView (tên/điểm/thời gian), ImageView (hạng).  
   - **Mục Đích**: Truyền cảm hứng cho người dùng thông qua việc hiển thị thứ hạng.

7. **Trắc Nghiệm Từ Vựng (MultipleChoiceActivity & ResultActivity)**  
   - **Bố Cục**: MultipleChoiceActivity bao gồm một `TextView` cho câu hỏi, một `RadioGroup` với bốn `RadioButton` lựa chọn, và các `Button` để gửi và tiếp tục. ResultActivity hiển thị một `TextView` cho điểm số cuối cùng và một `Button` để quay lại menu chính.  
   - **Thành Phần**: Hiển thị câu hỏi, nút radio, nút hành động, hiển thị điểm số.  
   - **Mục Đích**: Cung cấp giao diện bài kiểm tra rõ ràng và hấp dẫn với phản hồi tức thì.

## Chi Tiết Kỹ Thuật
### Phần FrontEnd (Mobile)
- **Công Nghệ**: Android Studio  
- **Ngôn Ngữ**: Java  
- **Framework**: Android SDK  
- **Thư Viện Chính**:
  - **Retrofit**: Để giao tiếp với API.
  - **Picasso**: Để tải hình ảnh trong bài luyện nghe.
  - **MediaPlayer**: Để phát âm thanh trong bài luyện nghe.
- **Kiến Trúc**:
  - Các Activity (ví dụ: LoginActivity, SignUpActivity, VocabularyActivity) xử lý giao diện và tương tác người dùng.
  - Các Adapter (ví dụ: TopicAdapter, VocabularyAdapter) tùy chỉnh hiển thị ListView.
  - SharedPreferences lưu trữ dữ liệu người dùng (ví dụ: tên người dùng, mã thông báo).
  - AsyncTask và ProgressBarAnimation tạo trải nghiệm màn hình khởi động mượt mà.

### Phần BackEnd (API)
- **Công Nghệ**:
  - **Framework**: Spring Boot  
  - **Ngôn Ngữ**: Java (JDK 17)  
  - **Cơ Sở Dữ Liệu**: MySQL 8.0  
  - **Môi Trường Phát Triển**: IntelliJ IDEA  
- **Bộ Điều Khiển**:
  - **AuthenticationController**: Quản lý đăng nhập, đăng ký, khôi phục mật khẩu, và xác minh OTP.
  - **TopicController**: Xử lý danh sách chủ đề.
  - **VocabularyController**: Quản lý danh sách từ vựng theo chủ đề.
  - **UserPointController**: Quản lý dữ liệu bảng xếp hạng và điểm số người dùng.
- **API**: Các API RESTful để lấy chủ đề, từ vựng, câu hỏi, và cập nhật điểm số.

### Các Activity Chính
- **WelcomeActivity**: Hiển thị màn hình chào với thanh tiến trình động trước khi chuyển hướng đến LoginActivity.
- **LayoutActivity**: Trung tâm chính sau khi đăng nhập, cho phép điều hướng đến bài trắc nghiệm, từ vựng, luyện nghe, và bảng xếp hạng.
- **LoginActivity, SignUpActivity, ForgotPasswordActivity**: Xử lý xác thực và quản lý tài khoản người dùng.
- **TopicActivity, VocabularyActivity**: Hỗ trợ học từ vựng theo chủ đề.
- **ListeningActivity**: Cung cấp bài tập nghe với câu hỏi trắc nghiệm.
- **MultipleChoiceActivity, ResultActivity**: Quản lý bài trắc nghiệm và hiển thị kết quả.
- **LeaderBoardActivity**: Hiển thị xếp hạng người dùng dựa trên hiệu suất bài kiểm tra.

## Link Figma
- Thiết kế giao diện:  https://www.figma.com/design/IoUiMht6sYNXOpXK1LTh1T/Design-mobile-app?node-id=0-1&t=sxfKVVyXTqjW9bV2-1

## Cài Đặt
1. **Yêu Cầu Trước**:
   - Android Studio (khuyến nghị phiên bản mới nhất).
   - Thiết bị/emulator Android chạy API cấp 21 trở lên.
   - Máy chủ hậu cần với các API RESTful đã được triển khai (tham khảo tài liệu hậu cần).

2. **Các Bước**:
   - Sao chép kho lưu trữ: `git clone <repository_url>`.
   - Mở dự án trong Android Studio.
   - Đồng bộ hóa dự án với Gradle để tải các phụ thuộc.
   - Cấu hình URL cơ sở API hậu cần trong `RetrofitClient.java`.
   - Xây dựng và chạy ứng dụng trên emulator hoặc thiết bị thực.

## Sử Dụng
1. Khởi động ứng dụng để xem màn hình chào (WelcomeActivity).
2. Đăng ký tài khoản mới hoặc đăng nhập bằng thông tin hiện có.
3. Điều hướng qua menu chính (LayoutActivity) để:
   - Học từ vựng bằng cách chọn chủ đề.
   - Luyện nghe với các bài tập âm thanh.
   - Làm bài trắc nghiệm để kiểm tra kiến thức.
   - Xem xếp hạng trên bảng xếp hạng.
4. Đăng xuất qua menu trong LayoutActivity khi hoàn tất.

## Cấu Trúc Dự Án
```
study-support-app/
├── app/
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/
│   │   │   │   ├── com/
│   │   │   │   │   ├── example/
│   │   │   │   │   │   ├── apphoctienganh/
│   │   │   │   │   │   │   ├── activity/
│   │   │   │   │   │   │   │   ├── ForgotPasswordActivity.java
│   │   │   │   │   │   │   │   ├── LayoutActivity.java
│   │   │   │   │   │   │   │   ├── LeaderBoardActivity.java
│   │   │   │   │   │   │   │   ├── ListeningActivity.java
│   │   │   │   │   │   │   │   ├── LoginActivity.java
│   │   │   │   │   │   │   │   ├── MultipleChoiceActivity.java
│   │   │   │   │   │   │   │   ├── ResultActivity.java
│   │   │   │   │   │   │   │   ├── SignUpActivity.java
│   │   │   │   │   │   │   │   ├── TopicActivity.java
│   │   │   │   │   │   │   │   ├── VocabularyActivity.java
│   │   │   │   │   │   │   │   ├── WelcomeActivity.java
│   │   │   │   │   │   │   ├── adapter/
│   │   │   │   │   │   │   │   ├── LeaderBoardAdapter.java
│   │   │   │   │   │   │   │   ├── TopicAdapter.java
│   │   │   │   │   │   │   │   ├── VocabularyAdapter.java
│   │   │   │   │   │   │   ├── api/
│   │   │   │   │   │   │   │   ├── ApiService.java
│   │   │   │   │   │   │   │   ├── RetrofitClient.java
│   │   │   │   │   │   │   ├── model/
│   │   │   │   │   │   │   ├── support/
│   │   │   ├── res/
│   │   │   │   ├── layout/
│   │   │   │   │   ├── activity_welcome.xml
│   │   │   │   │   ├── activity_login.xml
│   │   │   │   │   ├── activity_sign_up.xml
│   │   │   │   │   ├── activity_forgot_email.xml
│   │   │   │   │   ├── activity_layout.xml
│   │   │   │   │   ├── activity_topic.xml
│   │   │   │   │   ├── activity_vocabulary.xml
│   │   │   │   │   ├── activity_listening.xml
│   │   │   │   │   ├── activity_quiz.xml
│   │   │   │   │   ├── activity_result.xml
│   │   │   │   │   ├── activity_leader_board.xml
│   │   │   │   ├── drawable/
│   │   │   │   │   ├── sport.png
│   │   │   │   │   ├── environment.png
│   │   │   │   │   ├── top1.png
│   │   │   │   │   ├── top2.png
│   │   │   │   │   ├── top3.png
│   │   │   │   │   ├── default_topic.png
│   │   │   │   ├── raw/
│   │   │   │   │   ├── ets_toeic_2018_test_3_1.mp3
│   │   │   │   │   ├── ets_toeic_2018_test_3_3.mp3
├── README.md
```

## Đóng Góp
Dự án này được phát triển trong khuôn khổ một môn học tại trường đại học. Chúng tôi hoan nghênh các đóng góp để sửa lỗi, cải tiến tính năng, hoặc nâng cao tài liệu. Vui lòng thực hiện theo các bước sau:
1. Sao chép kho lưu trữ.
2. Tạo một nhánh mới (`git checkout -b feature/your-feature`).
3. Ghi nhận thay đổi (`git commit -m "Thêm tính năng của bạn"`).
4. Đẩy lên nhánh (`git push origin feature/your-feature`).
5. Mở một yêu cầu kéo.
