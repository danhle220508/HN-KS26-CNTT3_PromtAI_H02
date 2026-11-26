# BÀI LÀM PHA 2 – HACKATHON 02

- **Mã đề:** 09
- **Họ tên:Lê Đức Anh**
- **Lớp:CNTT3**
- **Link repository Pha2:https://github.com/danhle220508/HN-KS26-CNTT3_PromtAI_H02**
- **Công cụ AI đã dùng (ChatGPT/Claude/Gemini):gemini**

> Pha 2 (20 phút cuối). Mỗi mục: mở cuộc trò chuyện mới, gửi nguyên văn prompt đã viết trong bai_lam_pha1.md, dán câu trả lời và link chia sẻ vào đây. Xong, kéo thả file này vào repository Pha2.

## 4.2. Trích xuất tin nhắn đặt chỗ workshop ra JSON

**KET QUA AI**

```text
[
  {
    "ma_lop": "NANTAY",
    "ngay_hoc": "2026-12-13",
    "nguoi_lon": 2,
    "tre_em": 1,
    "ca_hoc": "chieu",
    "ghi_chu": null
  },
  {
    "ma_lop": "BANXOAY",
    "ngay_hoc": "2027-01-10",
    "nguoi_lon": 3,
    "tre_em": 0,
    "ca_hoc": null,
    "ghi_chu": "1 người bị đau cổ tay"
  },
  {
    "ma_lop": "VEGOM",
    "ngay_hoc": null,
    "nguoi_lon": 4,
    "tre_em": 0,
    "ca_hoc": "sang",
    "ghi_chu": "1 bạn đi xe lăn"
  }
]
```

**Link trò chuyện:https://share.gemini.google/2G6c58CI4gv4**

## 4.3. Báo giá bằng Chain-of-Thought

**KET QUA AI**

```text
```python
gia_banxoay = 550000
nguoi_lon = 5
tien_nguoi_lon = nguoi_lon * gia_banxoay

# 2 trẻ em (8 tuổi và 12 tuổi) -> 6 đến 12 tuổi tính 70% giá người lớn; bé 4 tuổi -> miễn phí (0)
tre_em_tinh_phi = 2
gia_tre_em_1 = gia_banxoay * 0.70
tien_tre_em = tre_em_tinh_phi * gia_tre_em_1

# Tiền học = tiền người lớn + tiền trẻ em
tien_hoc = tien_nguoi_lon + tien_tre_em

# Giảm giá nhóm: từ 5 người lớn trở lên được giảm 5% trên tiền học
giam_gia = tien_hoc * 0.05
tien_hoc_sau_giam = tien_hoc - giam_gia

# Phí nung và giao: 80.000 đồng/sản phẩm * 4 sản phẩm
so_san_pham = 4
gia_nung_giao = 80000
phi_nung_giao = so_san_pham * gia_nung_giao

# Tổng tiền
tong_tien = tien_hoc_sau_giam + phi_nung_giao

print(f"tien_nguoi_lon: {tien_nguoi_lon:,.0f}")
print(f"gia_tre_em_1: {gia_tre_em_1:,.0f}")
print(f"tien_tre_em: {tien_tre_em:,.0f}")
print(f"tien_hoc: {tien_hoc:,.0f}")
print(f"giam_gia: {giam_gia:,.0f}")
print(f"tien_hoc_sau_giam: {tien_hoc_sau_giam:,.0f}")
print(f"phi_nung_giao: {phi_nung_giao:,.0f}")
print(f"tong_tien: {tong_tien:,.0f}")


```

```text
tien_nguoi_lon: 2,750,000
gia_tre_em_1: 385,000
tien_tre_em: 770,000
tien_hoc: 3,520,000
giam_gia: 176,000
tien_hoc_sau_giam: 3,344,000
phi_nung_giao: 320,000
tong_tien: 3,664,000


```

1. **Tiền người lớn (lớp BANXOAY):**

$$5 \times 550.000 = 2.750.000\text{ đồng}$$


2. **Tiền trẻ em:**
* Trẻ 8 tuổi và 12 tuổi (từ 6 đến 12 tuổi, tính 70% giá người lớn): mỗi bé $550.000 \times 70\% = 385.000\text{ đồng}$; 2 bé là:

$$2 \times 385.000 = 770.000\text{ đồng}$$


* Bé 4 tuổi (dưới 6 tuổi đi kèm): miễn phí ($0\text{ đồng}$).
* Tổng tiền trẻ em: $770.000 + 0 = 770.000\text{ đồng}$.


3. **Tiền học:**

$$2.750.000 + 770.000 = 3.520.000\text{ đồng}$$


4. **Giảm giá nhóm:**
* Nhóm có 5 người lớn (đạt mức từ 5 người lớn trở lên), giảm 5% trên tiền học:

$$3.520.000 \times 5\% = 176.000\text{ đồng}$$


* Tiền học sau giảm:

$$3.520.000 - 176.000 = 3.344.000\text{ đồng}$$




5. **Phí nung và giao (4 sản phẩm, không giảm giá):**

$$4 \times 80.000 = 320.000\text{ đồng}$$


6. **Tổng tiền:**

$$3.344.000 + 320.000 = 3.664.000\text{ đồng}$$



[RESULT: 3.664.000 đồng]

**Link trò chuyện:https://share.gemini.google/xJB5rHWuix1Y**

### b) Kiểm tra kết quả AI

đúng

## 4.4. Dây chuyền xử lý khiếu nại – kết quả Trạm 1

**KET QUA AI**

```text
{
  "loai_su_co": "hong_san_pham",
  "so_khach": 3,
  "so_san_pham_bi_hong": 5,
  "tom_tat": "Khách phản ánh 5/6 sản phẩm gốm bị nứt vỡ khi nhận hàng, yêu cầu xưởng giải quyết."
}
```

**Link trò chuyện:https://share.gemini.google/69Lokx81cgzS**

## 4.5. Prompt chấm bài theo Rubric

**KET QUA AI**

```text
| Tiêu chí | Điểm | Minh chứng | Đề xuất sửa |
| --- | --- | --- | --- |
| **Đúng thông tin (50%)** | 5.0/5.0 | "Lớp vẽ gốm bên em 200k" và "Chị đổi trước 1 ngày thì free": Đã nêu thông tin về mức phí và điều kiện đổi lịch. *(Lưu ý: Thiếu dữ liệu chuẩn đối chiếu nên chấm dựa trên việc có cung cấp đủ 2 nhóm thông tin theo đề bài).* | "Chi phí tham gia lớp vẽ gốm bên em là 200.000 VNĐ/người. Bên em hỗ trợ đổi lịch miễn phí nếu chị báo trước tối thiểu 1 ngày." |
| **Đầy đủ (30%)** | 1.5/3.0 | "Có gì chị nhắn em nha!": Trả lời được 2 thông tin cơ bản (giá, đổi lịch) nhưng thiếu hoàn toàn phần kêu gọi hành động (mời khách cung cấp ngày học, ca học, số người để đặt chỗ). | "Để bên em hỗ trợ giữ chỗ, chị vui lòng cung cấp thêm thông tin về ngày học, ca học và số lượng người tham gia nhé ạ." |
| **Giọng điệu (20%)** | 0.5/2.0 | "Hi chị ơi!", "200k thôi nè, vui lắm luôn.", "free nha chị.", "nhắn em nha!": Sử dụng từ ngữ mang tính văn nói, suồng sã ("Hi", "nè", "vui lắm luôn", "free", "nha"), thiếu tính chuyên nghiệp trong giao tiếp khách hàng. | "Chào chị ạ! Chi phí lớp vẽ gốm bên em là 200.000 VNĐ. Chị sẽ được hỗ trợ đổi lịch miễn phí nếu thông báo trước 1 ngày ạ. Chị phản hồi giúp em để được hỗ trợ tốt nhất nhé ạ!" |
| **Tổng điểm** | **7.0/10** |  |  |
```

**Link trò chuyện:https://share.gemini.google/jvdDiO03lYDP**
