# BÀI LÀM PHA 2 (ĐỀ LUYỆN TẬP CHỦ ĐỀ CHẠY AFFILIATE)

- **Họ tên:Vũ Nam Tùng**
- **Lớp:CNTT3**
- **Link repository Pha2:**
- **Công cụ AI đã dùng (ChatGPT/Claude/Gemini):Gemini**

> Pha 2 (20 phút cuối). Mỗi mục: mở cuộc trò chuyện mới, gửi nguyên văn prompt đã viết trong bai_lam_pha1.md, dán câu trả lời và link chia sẻ vào đây. Xong, kéo thả file này vào repository Pha2.

## 4.2. Trích xuất tin nhắn đăng ký gói Affiliate ra JSON

**KET QUA AI**

```text
[
  {
    "ma_goi": "TT",
    "ngay_bat_dau": "2026-12-20",
    "creator_chinh": 2,
    "thuc_tap_sinh": 1,
    "hang_tai_khoan": "thuong",
    "ghi_chu": null
  },
  {
    "ma_goi": "SP",
    "ngay_bat_dau": "2027-01-08",
    "creator_chinh": 3,
    "thuc_tap_sinh": 0,
    "hang_tai_khoan": null,
    "ghi_chu": "một bạn đang bó bột chân cần ngồi bàn gần cửa ra vào"
  },
  {
    "ma_goi": "PRO",
    "ngay_bat_dau": null,
    "creator_chinh": 4,
    "thuc_tap_sinh": 0,
    "hang_tai_khoan": "vip",
    "ghi_chu": "mượn thêm đèn trợ sáng và phông xanh để quay mẫu"
  }
]
```

**Link trò chuyện:https://share.gemini.google/N9vjHEcbbQm4**

## 4.3. Báo giá gói Affiliate bằng Chain-of-Thought

**KET QUA AI**

````text
```python
creator_price = 1_500_000
num_creators = 4
creator_total = creator_price * num_creators

intern_price = creator_price * 0.6
num_interns = 2 # 16 and 17 years old (15 <= age < 18)
intern_total = intern_price * num_interns

# 7 year old child (< 15, waiting area, no equipment) -> free (0)
child_total = 0

package_total = creator_total + intern_total + child_total

# Discount: >= 4 main creators -> 10% off total package (creator + intern)
discount = package_total * 0.10
package_after_discount = package_total - discount

# Mic rental: 2 sets * 250,000 VND (no discount)
mic_price = 250_000
num_mics = 2
mic_total = mic_price * num_mics

grand_total = package_after_discount + mic_total

print(f"Creator total: {creator_total:,.0f}")
print(f"Intern total: {intern_total:,.0f}")
print(f"Package total: {package_total:,.0f}")
print(f"Discount: {discount:,.0f}")
print(f"After discount: {package_after_discount:,.0f}")
print(f"Mic total: {mic_total:,.0f}")
print(f"Grand total: {grand_total:,.0f}")


````

```text
Creator total: 6,000,000
Intern total: 1,800,000
Package total: 7,800,000
Discount: 780,000
After discount: 7,020,000
Mic total: 500,000
Grand total: 7,520,000


```

- Tiền Creator chính: 4 × 1.500.000 = 6.000.000 đồng
- Tiền thực tập sinh: 2 × (1.500.000 × 60%) = 2 × 900.000 = 1.800.000 đồng (bé 7 tuổi dưới 15 tuổi ngồi khu chờ được miễn phí: 0 đồng)
- Tổng tiền gói: 6.000.000 + 1.800.000 = 7.800.000 đồng
- Giảm giá team: 7.800.000 × 10% = 780.000 đồng (tiền gói sau giảm: 7.800.000 - 780.000 = 7.020.000 đồng)
- Phụ thu thuê mic: 2 × 250.000 = 500.000 đồng
- Tổng tiền: 7.020.000 + 500.000 = 7.520.000 đồng

[RESULT: 7.520.000 đồng]

````

**Link trò chuyện:https://share.gemini.google/Gy272OzLABK9**

### b) Kiểm tra kết quả AI

đúng

## 4.4. Dây chuyền xử lý khiếu nại – kết quả Trạm 1

**KET QUA AI**

```text
{
"loai_su_co": "sai_phong",
"so_khach": 3,
"so_ca_bi_anh_huong": 2,
"tom_tat": "Team 3 người bị xếp sai phòng học thường, thiếu đèn livestream và cách âm trong 2 ca đầu."
}
````

**Link trò chuyện:https://share.gemini.google/mU47gN2fYTkL**

## 4.5. Prompt chấm bài theo Rubric

**KET QUA AI**

```text
| Tiêu chí | Điểm | Minh chứng | Đề xuất sửa |
| --- | --- | --- | --- |
| Đúng thông tin | 0/5,0 | - Nguyên văn: `"Gói TikTok Affiliate bên mình giá chỉ 1.200.000đ/người thôi"` -> Sai mức giá chuẩn (1.500.000 đồng/Creator chính).<br>

<br>- Nguyên văn: `"Bạn báo huỷ trước 5 ngày thì được hoàn lại đủ 100% tiền nha"` -> Sai chính sách hoàn tiền: huỷ trước 5 ngày (thuộc khoảng từ 3 đến 6 ngày) chỉ được hoàn 50%, hoàn 100% áp dụng khi huỷ từ 7 ngày trở lên. | `"Gói TikTok Affiliate (TT) có mức phí 1.500.000 đồng/Creator chính. Theo chính sách của trung tâm, nếu bạn báo huỷ trước ngày bắt đầu 5 ngày (trong khoảng từ 3 đến 6 ngày), bạn sẽ được hoàn lại 50% học phí."` |
| Đầy đủ | 1,5/3,0 | - Đã trả lời hai câu hỏi về giá và chính sách huỷ (dù thông tin sai).<br>

<br>- Thiếu lời mời khách hàng cung cấp ngày đợt thực chiến và số lượng suất muốn đăng ký (không có câu hỏi/lời mời nào đề cập hai nội dung này trong toàn bộ bài làm). | `"Để VietAffiliate hỗ trợ giữ chỗ chính xác, bạn cho mình xin thông tin đợt thực chiến bạn dự kiến tham gia và số lượng suất cần đăng ký nhé."` |
| Giọng điệu | 0/2,0 | - Nguyên văn: `"Dạ hello bạn nha!"`, `"nha"`, `"cứ chốt lẹ kẻo hết slot nè!"` -> Xưng hô và dùng từ ngữ suồng sã, thiếu chuyên nghiệp, tạo áp lực chốt đơn.<br>

<br>- Nguyên văn: `"đăng ký xong gắn link là nổ đơn hoa hồng trăm triệu luôn ạ"` -> Cam kết hoa hồng/doanh thu ảo, gây hiểu lầm và rủi ro uy tín cho trung tâm. | `"Chào bạn, cảm ơn bạn đã quan tâm đến chương trình tại VietAffiliate. Kết quả kinh doanh phụ thuộc vào năng lực triển khai và thị trường của từng học viên, trung tâm không cam kết mức hoa hồng cố định."` |

Tổng điểm: 1,5/10
```

**Link trò chuyện:https://share.gemini.google/VlVsHEmT9iXK**
