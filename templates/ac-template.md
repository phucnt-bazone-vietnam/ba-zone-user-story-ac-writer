# Acceptance Criteria Template · BA Zone

> Format: Given-When-Then (Gherkin syntax)  
> Tối thiểu 3 AC cho mỗi User Story: Happy path + Edge case + Negative path
>
> Template chuẩn của **BA Zone** · Digital School — by **Phúc NT**

---

## AC1: [Tên scenario - Happy path]

**Given** [tiền điều kiện 1]  
**And** [tiền điều kiện 2 - nếu có]

**When** [hành động chính của user]

**Then** [kết quả chính - đo lường được]  
**And** [kết quả phụ 1 - nếu có]  
**And** [kết quả phụ 2 - nếu có]

---

## AC2: [Tên scenario - Edge case / Validation]

**Given** [bối cảnh edge case]

**When** [hành động trigger edge case]

**Then** [hệ thống xử lý đúng]  
**And** [thông báo / hành vi cụ thể]

---

## AC3: [Tên scenario - Negative path / Error]

**Given** [bối cảnh lỗi]

**When** [hành động dẫn đến lỗi]

**Then** [hệ thống xử lý lỗi đúng]  
**And** [hiển thị thông báo lỗi cụ thể]  
**And** [không có side effect không mong muốn]

---

## Checklist trước khi commit AC

- [ ] Mỗi AC chỉ test 1 scenario duy nhất
- [ ] Given/When/Then đều đo lường được (có số liệu, trạng thái rõ)
- [ ] Không chứa từ mơ hồ: "nhanh", "phù hợp", "user-friendly", "An toàn"
- [ ] Không chứa logic implementation (API name, DB table, code)
- [ ] Không mô tả UI cụ thể (màu, vị trí pixel)
- [ ] Đã có tối thiểu: 1 happy + 1 edge + 1 negative
- [ ] QA có thể viết test case từ AC này

---
*BA Zone · Digital School — by Phúc NT*

