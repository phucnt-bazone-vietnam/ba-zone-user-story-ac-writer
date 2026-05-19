# user-story-ac-writer · BA Zone

> Skill Claude AI giúp BA/PO viết User Story và Acceptance Criteria đạt 
> chuẩn INVEST + Given-When-Then, sẵn sàng cho dev estimate và QA viết test case.
>
> Phát triển bởi **Phúc NT** trong khuôn khổ chương trình **Digital School** 
> của **BA Zone** — cộng đồng Business Analyst & Product Owner Việt Nam.

---

## 📋 Tính năng chính

- ✅ Enforce 6 tiêu chí INVEST (Independent, Negotiable, Valuable, Estimable, Small, Testable)
- ✅ Sinh AC theo format Gherkin Given-When-Then
- ✅ Tự động self-check chất lượng trước khi xuất
- ✅ Hỗ trợ 3 mode: viết mới / refine US sẵn có / bổ sung AC
- ✅ Đề xuất split khi story quá lớn
- ✅ 7 ví dụ mẫu cho domain EdTech & Digital School (đã generic hóa tên thương hiệu)

## 📁 Cấu trúc

```
user-story-ac-writer/
├── SKILL.md                          # File chính - hướng dẫn Claude
├── templates/
│   ├── user-story-template.md        # Template US trống
│   └── ac-template.md                # Template AC Gherkin
├── references/
│   ├── invest-criteria.md            # Giải thích INVEST chi tiết
│   └── examples.md                   # 7 ví dụ EdTech / Digital School
└── checklists/
    └── quality-checklist.md          # Self-review trước khi xuất
```

## 🚀 Cách sử dụng

### Cách 1: Upload vào Claude Project
1. Clone repo về máy: `git clone <repo-url>`
2. Vào claude.ai → Projects → tạo project mới
3. Upload toàn bộ folder `user-story-ac-writer/` vào project knowledge
4. Chat với Claude trong project đó, ví dụ:
   - "Viết US cho tính năng đặt lịch mentor"
   - "Refine user story này theo INVEST: ..."
   - "Bổ sung AC cho US-001"

### Cách 2: Deploy vào môi trường có /mnt/skills/user/
1. Copy folder skill vào `/mnt/skills/user/user-story-ac-writer/`
2. Claude sẽ tự động phát hiện và trigger khi gặp request phù hợp

## 🎯 Trigger phrases

Skill sẽ tự kích hoạt khi user nói:
- "viết user story", "viết US", "tạo user story"
- "viết AC", "viết acceptance criteria"
- "user story chuẩn INVEST"
- "AC theo Given-When-Then"
- "refine user story", "review US này"
- "split user story"
- Paste feature description + "viết story đi"

## 📊 Ví dụ output

```markdown
## US-MENTOR-BOOK-001: Đặt lịch tư vấn 1-on-1 với Mentor BA Zone

**As a** học viên Digital School đang theo học chương trình BA Advanced
**I want to** đặt lịch tư vấn 1-on-1 với mentor có chuyên môn phù hợp
**So that** nhận được hướng dẫn cụ thể cho bài tập mà không cần chờ buổi học chung

### INVEST Self-check
| Tiêu chí | Đánh giá | Ghi chú |
|----------|----------|---------| 
| Independent | ✅ | Login và profile đã có |
| Negotiable | ✅ | Để mở thêm payment method sau |
| ...

### Acceptance Criteria
**AC1: Đặt lịch thành công - happy path**
- Given học viên chọn Mentor Phúc NT, slot 15/06/2026 lúc 20:00
- And còn 1 session 1-on-1 trong gói tháng
- When học viên xác nhận đặt lịch
- Then hệ thống tạo booking, gửi link Meet và trừ 1 session quota trong 30s
...
```

## 🛠️ Tùy chỉnh theo domain công ty

Sau khi test xong skill với các ví dụ mặc định, bạn có thể điều chỉnh nội dung để skill hoạt động tốt hơn với domain nghiệp vụ của công ty mình:

### 1. Cập nhật ví dụ trong `references/examples.md`

Thay thế các ví dụ EdTech / Digital School hiện có bằng ví dụ từ domain thực tế của công ty bạn (e-commerce, fintech, healthcare, logistics, v.v.). Khi Claude đọc ví dụ quen thuộc với domain của bạn, output sẽ tự nhiên bám sát ngữ cảnh nghiệp vụ hơn.

```
# Ví dụ: Nếu công ty bạn làm e-commerce
→ Thay "đặt lịch mentor" bằng "đặt hàng", "theo dõi vận chuyển", "quản lý wishlist"
→ Thay persona "học viên" bằng "khách hàng", "seller", "admin"
```

### 2. Tinh chỉnh nội dung trong `SKILL.md`

Bổ sung vào phần context của SKILL.md các thông tin đặc thù:
- Tên hệ thống / module nội bộ
- Thuật ngữ nghiệp vụ riêng của công ty
- Các persona người dùng thực tế
- Quy ước đặt tên User Story (prefix ID, format, v.v.)

### 3. Kết quả sau khi tùy chỉnh

Skill sẽ tự động sinh User Story và AC bám sát đúng domain, dùng đúng thuật ngữ, và phù hợp với quy trình nội bộ của team bạn — thay vì output chung chung.

---

## 🤝 Đóng góp

Pull requests welcome. Khi đóng góp:
1. Tạo branch mới: `git checkout -b feat/improve-xxx`
2. Test skill với tối thiểu 3 trường hợp khác nhau
3. Cập nhật `references/examples.md` nếu thêm pattern mới
4. Submit PR với mô tả rõ ràng

## 📝 License

MIT License — xem file [LICENSE](LICENSE)

## 👤 Tác giả & Attribution

Phát triển bởi **Phúc NT** · [BA Zone](https://bazone.org) · Digital School  

Đây là sp của **BA Zone**. Bạn được tự do sử dụng và fork repo này
theo điều khoản MIT License, với điều kiện **giữ nguyên thông tin tác giả** 
(Phúc NT / BA Zone) trong mọi bản phân phối lại.

Vui lòng **không** xóa attribution hoặc tái phân phối repo này dưới tên khác 
mà không có sự cho phép của BA Zone.

---
*BA Zone — Cộng đồng BA/PO Việt Nam*
https://bazone.org/
