---
name: user-story-ac-writer
description: |
  Sinh User Story và Acceptance Criteria chuẩn INVEST + Given-When-Then 
  cho BA/PO. Skill enforce 6 tiêu chí INVEST (Independent, Negotiable, 
  Valuable, Estimable, Small, Testable) và format AC theo Gherkin syntax.
  Hỗ trợ 3 mode: viết mới từ feature description, refine US đang có,
  bổ sung AC cho US đã viết.
  
  Dùng khi user nói: "viết user story", "viết US", "tạo user story", 
  "viết AC", "viết acceptance criteria", "tạo AC cho story", 
  "user story chuẩn INVEST", "AC theo Given-When-Then", "AC Gherkin",
  "refine user story", "review US này", "US này đã chuẩn chưa",
  "bổ sung AC", "viết tiêu chí nghiệm thu", "story cho feature này",
  "split user story", "story quá to cần tách", kể cả khi paste 
  feature description + nói "viết story đi" hoặc upload PRD + 
  "tạo US list".
  
  KHÔNG dùng cho: viết PRD/URD/SRS toàn bộ (dùng prd-writer, srs-writer),
  viết test case kỹ thuật chi tiết (AC ≠ test case), viết Use Case 
  formal (dùng po-usecase-refiner), business rules (dùng 
  business-rule-generator).
author: Phúc NT @ BA Zone
source: https://github.com/ba-zone
---

# User Story & Acceptance Criteria Writer
> by **Phúc NT** — BA Zone & Digital School

## Mục đích
Skill này giúp BA/PO viết User Story và Acceptance Criteria đạt chuẩn 
chất lượng cao, sẵn sàng cho dev estimate và QA viết test case.

Được phát triển bởi **Phúc NT** trong khuôn khổ chương trình đào tạo 
**Digital School** của **BA Zone** — cộng đồng BA/PO Việt Nam.

## Workflow chuẩn

### Bước 1: Xác định mode
Hỏi user 1 trong 3 mode:
- **Mode A - Viết mới**: User cung cấp feature description, skill sinh 
  US + AC từ đầu
- **Mode B - Refine**: User có US/AC sẵn, skill review và đề xuất sửa
- **Mode C - Bổ sung AC**: User có US, cần thêm AC chi tiết

Nếu user paste content rõ ràng, tự suy luận mode và xác nhận lại 1 lần.

### Bước 2: Thu thập input bắt buộc
Cần đủ 4 thông tin trước khi sinh, hỏi nếu thiếu:
1. **Persona/User type**: Ai sẽ dùng tính năng? (Học viên, Mentor, Admin, Doanh nghiệp...)
2. **Goal**: User muốn làm gì?
3. **Business value**: Tại sao cần tính năng này?
4. **Context/Scope**: Tính năng nằm trong feature/module nào?

KHÔNG được tự bịa nếu user không cung cấp - phải hỏi.

### Bước 3: Sinh User Story theo template
Dùng format chuẩn 3 thành phần:

```
**US-[ID]**: [Tiêu đề ngắn gọn]

**As a** [persona cụ thể, không generic như "user"]
**I want to** [hành động cụ thể, đo lường được]
**So that** [business value rõ ràng, không lặp lại I want]
```

### Bước 4: Apply checklist INVEST
Trước khi xuất, tự kiểm tra US theo 6 tiêu chí:

| Tiêu chí | Câu hỏi kiểm tra | Nếu fail thì làm gì |
|----------|------------------|---------------------|
| **I**ndependent | Story có phụ thuộc story khác không? | Tách dependency hoặc gộp |
| **N**egotiable | Có để chỗ cho thảo luận không? | Bỏ chi tiết kỹ thuật cứng |
| **V**aluable | Mang lại giá trị gì cho user/business? | Viết lại phần "So that" |
| **E**stimable | Dev có ước lượng được effort không? | Bổ sung context/constraint |
| **S**mall | Hoàn thành trong 1 sprint không? | Split thành nhiều story |
| **T**estable | QA viết được test case không? | Bổ sung AC cụ thể |

Tham khảo chi tiết: `references/invest-criteria.md`

### Bước 5: Sinh Acceptance Criteria

Mỗi US cần **tối thiểu 3 AC**, format Given-When-Then:

```
**AC1: [Tên scenario - happy path]**
- **Given** [tiền điều kiện cụ thể]
- **When** [hành động user thực hiện]
- **Then** [kết quả mong đợi đo lường được]
- **And** [kết quả phụ nếu có]

**AC2: [Tên scenario - edge case/validation]**
...

**AC3: [Tên scenario - error/negative path]**
...
```

**Quy tắc viết AC tốt:**
- Bao quát đủ 3 loại: happy path, edge case, negative path
- Mỗi điều kiện trong Given/When/Then phải đo lường được (số liệu, 
  trạng thái rõ ràng)
- Tránh từ mơ hồ: "nhanh", "hợp lý", "user-friendly"
- Không viết logic implementation (đó là việc của dev)
- 1 AC = 1 scenario duy nhất, không gộp nhiều case

### Bước 6: Output cuối cùng
Trình bày theo format:

1. User Story (3 dòng As a / I want / So that)
2. INVEST Self-check (bảng đánh giá 6 tiêu chí với ✅/⚠️)
3. Acceptance Criteria (đánh số AC1, AC2, AC3...)
4. Notes (nếu có dependency, assumption, hoặc câu hỏi cần PO làm rõ)
5. Yêu cầu xem lại toàn bộ tài liệu trước khi xuất tài liệu. Hỏi định dạng tài liệu để user xác nhận trước khi xuất. 

## Anti-patterns - KHÔNG làm những điều sau

❌ **Persona generic**: "As a user" → ✅ "As a học viên Digital School 
   đã đăng ký khóa học và xác thực email"
   
❌ **Goal vague**: "I want to manage profile" → ✅ "I want to update 
   my email address"
   
❌ **Value lặp lại goal**: "So that I can manage profile" → ✅ "So that 
   I receive notifications at correct address"
   
❌ **AC mô tả UI**: "Then button turns blue" → ✅ "Then system displays 
   confirmation message"
   
❌ **AC chứa logic kỹ thuật**: "Then call API /v1/users/update" → 
   ✅ "Then user data is updated and persisted"

❌ **AC quá ít**: chỉ có 1 happy path → ✅ tối thiểu 3 AC bao quát các 
   nhánh

❌ **Story quá lớn**: 1 story cover cả CRUD → ✅ tách thành Create, 
   Read, Update, Delete riêng

## Khi nào cần split User Story?

Đề xuất split khi gặp các dấu hiệu:
- Story chứa từ "AND" trong tiêu đề ("Login AND register")
- Có nhiều persona khác nhau trong 1 story
- Story cover nhiều CRUD operation
- AC vượt quá 7-8 scenarios
- Dev ước lượng > 5 ngày làm việc

Pattern split phổ biến:
- Theo **CRUD**: tách Create / Read / Update / Delete
- Theo **persona**: tách Học viên / Mentor / Admin / Doanh nghiệp
- Theo **business rule**: tách Happy path / Validation / Permission
- Theo **data type**: tách theo loại data xử lý

## Tham khảo thêm

- `templates/user-story-template.md` - template trống điền vào
- `templates/ac-template.md` - template AC chuẩn Gherkin
- `references/invest-criteria.md` - giải thích sâu INVEST
- `references/examples.md` - 7 ví dụ mẫu cho EdTech & Digital School
- `checklists/quality-checklist.md` - checklist self-review trước khi xuất

---
*Skill được phát triển bởi Phúc NT · BA Zone · Digital School*  
*Vui lòng giữ nguyên attribution khi chia sẻ hoặc fork repo này.*
