# INVEST Criteria - Giải thích chi tiết

> INVEST là bộ 6 tiêu chí do Bill Wake đề xuất năm 2003, dùng để đánh giá 
> chất lượng User Story trong Agile/Scrum.
>
> Tài liệu này được biên soạn bởi **Phúc NT** cho chương trình **Digital School**
> của **BA Zone** — cộng đồng Business Analyst & Product Owner Việt Nam.

---

## I - Independent (Độc lập)

### Định nghĩa
Story phải có thể được phát triển, test, và deploy độc lập với các story khác. 
Tránh phụ thuộc cứng giữa các story.

### Tại sao quan trọng?
- Cho phép sắp xếp ưu tiên linh hoạt
- Tránh blocker khi 1 story bị delay
- Dễ chia việc trong team

### Dấu hiệu vi phạm
- Story B chỉ làm được sau khi story A xong
- Phải merge cùng lúc 2-3 story mới deploy được
- Test một story phải có data từ story khác

### Cách fix
- Gộp các story phụ thuộc thành 1 story lớn hơn (nếu nhỏ)
- Tách dependency ra thành story riêng + đặt ưu tiên trước
- Dùng mock data / stub để test độc lập

### Ví dụ (Digital School)

❌ **Vi phạm**: 
- US-1: Tạo tài khoản học viên
- US-2: Enroll khóa học (chỉ test được sau khi US-1 xong)

✅ **Đạt chuẩn**:
- US-1: Tạo tài khoản học viên (test với DB seed)
- US-2: Enroll khóa học (test với account học viên có sẵn trong test data)

---

## N - Negotiable (Có thể thương lượng)

### Định nghĩa
Story là "lời mời thảo luận", không phải hợp đồng cứng. Chi tiết implementation 
được làm rõ trong quá trình refinement và development.

### Tại sao quan trọng?
- Tận dụng kinh nghiệm dev/QA để tìm giải pháp tốt hơn
- Linh hoạt thay đổi khi có thông tin mới
- Tránh over-specification quá sớm

### Dấu hiệu vi phạm
- Story dài 3 trang mô tả từng pixel UI
- Chỉ định công nghệ cụ thể (phải dùng React, phải dùng Redis)
- Mô tả thuật toán chi tiết trong story

### Cách fix
- Giữ story ngắn gọn, focus vào "what" và "why"
- Đẩy chi tiết "how" sang AC hoặc tech design doc
- Dùng wireframe thay vì pixel-perfect mockup ở giai đoạn story

### Ví dụ (Digital School)

❌ **Vi phạm**:
"As a học viên, I want to login using a 256-bit AES encrypted JWT token stored 
in localStorage with refresh token rotation every 15 minutes..."

✅ **Đạt chuẩn**:
"As a học viên đã đăng ký, I want to đăng nhập an toàn vào BA Zone so that 
I can access my courses without repeated authentication."
(Chi tiết bảo mật để dev/security team thiết kế)

---

## V - Valuable (Có giá trị)

### Định nghĩa
Mỗi story phải mang lại giá trị rõ ràng cho user, business, hoặc cả hai.
Không có story "vì kỹ thuật yêu cầu".

### Tại sao quan trọng?
- Đảm bảo mọi effort đều có ROI
- Giúp PO ưu tiên đúng
- Stakeholder hiểu được tại sao cần làm

### Dấu hiệu vi phạm
- Phần "So that" rỗng hoặc lặp lại "I want"
- Story chỉ có giá trị cho dev (refactor, upgrade lib) - không có user value
- Không trả lời được câu "Nếu không làm thì sao?"

### Cách fix
- Viết phần "So that" theo công thức: business outcome + measurable
- Tech debt nên đóng gói thành story có giá trị business (giảm bug, tăng tốc)
- Hỏi "Why?" 5 lần để tìm giá trị thật

### Ví dụ (Digital School)

❌ **Vi phạm**:
"As a developer, I want to upgrade video player từ v2 lên v4 so that 
we use the latest version."

✅ **Đạt chuẩn**:
"As a học viên, I want video bài giảng load trong vòng 3 giây so that 
tôi không bỏ học giữa chừng khi kết nối mạng yếu."
(Upgrade video player là một phần solution, không phải mục tiêu)

---

## E - Estimable (Có thể ước lượng)

### Định nghĩa
Dev team phải có khả năng ước lượng effort để hoàn thành story (dù không 
cần chính xác tuyệt đối).

### Tại sao quan trọng?
- Giúp planning sprint
- Phát hiện story quá lớn hoặc quá mơ hồ sớm
- Set expectation cho stakeholder

### Dấu hiệu vi phạm
- Dev nói "không biết bao lâu, phải research thêm"
- Effort ước lượng chênh nhau quá lớn giữa các thành viên (>3 lần)
- Story chứa nhiều unknown technical risk

### Cách fix
- **Spike story**: tạo story riêng để research, ước lượng được sau khi spike xong
- Bổ sung context, constraint, tham khảo
- Chia nhỏ phần unknown ra để cô lập rủi ro

### Ví dụ (Digital School)

❌ **Vi phạm**:
"As a học viên, I want AI gợi ý lộ trình học phù hợp với tôi" 
(Không rõ AI dùng gì, data ở đâu, độ chính xác bao nhiêu)

✅ **Đạt chuẩn**:
- Spike US-1: "Research giải pháp recommendation phù hợp với 10.000 học viên 
  BA Zone, output: technical proposal trong 3 ngày"
- US-2: "Implement learning path recommendation theo proposal đã chốt từ US-1"

---

## S - Small (Nhỏ)

### Định nghĩa
Story đủ nhỏ để hoàn thành trong 1 sprint (thường 1-3 ngày làm việc của 
1 dev). Không phải càng nhỏ càng tốt - phải vừa đủ để có giá trị.

### Tại sao quan trọng?
- Giảm rủi ro khi planning
- Feedback loop nhanh hơn
- Dễ test và rollback

### Dấu hiệu vi phạm
- Story ước lượng > 5 ngày work
- AC vượt quá 7-8 scenarios
- Story chứa nhiều CRUD operations (Create + Read + Update + Delete)
- Tiêu đề có chữ "AND"

### Cách fix - Pattern split
1. **Theo CRUD**: tách Create / Read / Update / Delete riêng
2. **Theo persona**: Học viên / Mentor / Admin / HR Doanh nghiệp
3. **Theo data type**: Text / Video / File đính kèm
4. **Theo business rule**: Happy path / Validation / Permission
5. **Theo workflow step**: Đăng ký → Thanh toán → Enroll → Học
6. **Theo platform**: Web / Mobile App / API

### Ví dụ (Digital School)

❌ **Vi phạm**:
"As a học viên, I want to quản lý profile của tôi (xem, sửa tên, đổi mật khẩu, 
upload avatar, xóa tài khoản)"

✅ **Đạt chuẩn** - split thành:
- US-1: Xem thông tin profile cá nhân
- US-2: Cập nhật tên hiển thị
- US-3: Đổi mật khẩu
- US-4: Upload ảnh đại diện
- US-5: Yêu cầu xóa tài khoản

---

## T - Testable (Có thể test)

### Định nghĩa
Story phải có AC rõ ràng, đo lường được, để QA viết test case và xác nhận 
"done" hay chưa.

### Tại sao quan trọng?
- Tránh tranh cãi "done definition"
- Tự động hóa được test
- Stakeholder yên tâm sign-off

### Dấu hiệu vi phạm
- AC dùng từ mơ hồ: "nhanh", "đẹp", "user-friendly", "intuitive"
- AC không có điều kiện đo lường được
- Không có AC, chỉ có description

### Cách fix
- Mỗi AC phải có Given/When/Then cụ thể
- Đo lường: số liệu, trạng thái, message text cụ thể
- Định nghĩa "Done" rõ ràng

### Ví dụ (Digital School)

❌ **Vi phạm**:
"AC: Hệ thống phải phản hồi nhanh và hiển thị thông báo lỗi thân thiện"

✅ **Đạt chuẩn**:
"Given học viên nhập sai mật khẩu 3 lần liên tiếp
When học viên ấn Đăng nhập lần thứ 4
Then hệ thống hiển thị thông báo 'Tài khoản bị tạm khóa 15 phút vì lý do bảo mật' trong vòng 2 giây
And gửi email cảnh báo đến địa chỉ đã đăng ký"

---

## Quick Reference Card

| Tiêu chí | Câu hỏi 1 dòng |
|----------|----------------|
| Independent | Story này có chạy độc lập được không? |
| Negotiable | Có chỗ cho thảo luận, hay đã quá chi tiết? |
| Valuable | Học viên/BA Zone được lợi gì cụ thể? |
| Estimable | Dev ước lượng được effort không? |
| Small | Hoàn thành trong 1 sprint không? |
| Testable | QA viết được test case từ AC không? |

---

## Tham khảo thêm
- Bill Wake (2003) - "INVEST in Good Stories, and SMART Tasks"
- Mike Cohn - "User Stories Applied"
- Atlassian Agile Coach - User Story Best Practices

---
*Biên soạn bởi **Phúc NT** · BA Zone · Digital School*  
*Vui lòng dẫn nguồn khi sử dụng hoặc chia sẻ tài liệu này.*
