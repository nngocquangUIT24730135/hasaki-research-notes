# Quy trình B4 — Đổi trả hoặc hoàn tiền (*Return-to-Resolve*)

**Doanh nghiệp:** Hasaki Beauty & Clinic  
**Chính sách (ưu tiên):** [Đổi trả – hoàn tiền](https://hotro.hasaki.vn/doi-tra-hoan-tien.html) (30 ngày, từ 01/06/2024)  
**Ranh giới SoT:** [research.md](../../02-research/research.md) §4.3  
**BPMN:** [b4-doi-tra-hoac-hoan-tien.bpmn](./b4-doi-tra-hoac-hoan-tien.bpmn) · [b4-doi-tra-hoac-hoan-tien-layouted.bpmn](./b4-doi-tra-hoac-hoan-tien-layouted.bpmn) · [b4-doi-tra-hoac-hoan-tien-manual.bpmn](./b4-doi-tra-hoac-hoan-tien-manual.bpmn)  
**Ngày:** 09/08/2026  

> Luồng chính bám trang Hasaki. Hai pool **white-box** đồng bộ bằng message flow. Bước nội bộ (cập nhật hệ thống đơn hàng, kiểm tồn, hết hàng khi đổi) là **suy luận vận hành** — ghi rõ. **Không** khẳng định bắt buộc hoàn khi hết hàng muốn đổi.

---

## 1. Hồ sơ quy trình

| Trường | Nội dung |
|--------|----------|
| **Tên** | Đổi trả hoặc hoàn tiền |
| **Ai tham gia** | Khách hàng; NV cửa hàng / CSKH; kho; kế toán (hoàn tiền) |
| **Khách của quy trình** | Người muốn đổi hàng hoặc trả hàng lấy lại tiền |
| **Khi nào bắt đầu** | Khách mang hàng tới cửa hàng (không gọi), hoặc liên hệ CSKH / tổng đài trước |
| **Kết thúc** | (1) Đổi mới xong; (2) Hoàn tiền xong; (3) Không hỗ trợ đổi trả |

### 1.1. Chính sách đổi trả (website Hasaki)

> Từ ngày 01/06/2024, đổi trả trong vòng 30 ngày.

| | Sản phẩm lỗi (nhà cung cấp) | Sản phẩm lỗi (người sử dụng) | Sản phẩm không lỗi |
|--|----------------------------|------------------------------|--------------------|
| **1 – 30 ngày** | Đổi mới — Trả không thu phí | Không hỗ trợ đổi trả | Đổi mới |
| **31 ngày trở đi** | Không hỗ trợ đổi trả | | |

### 1.2. Cách bắt đầu (hai nhánh rõ)

| Thực tế | Thể hiện trên sơ đồ |
|---------|---------------------|
| Mang tới cửa hàng **không gọi** | Khách: X_C1 → mang tới CH; Hasaki: X0 → tiếp nhận walk-in → nhận & kiểm |
| Liên hệ CSKH trước, rồi **mang tới cửa hàng** | Khách: liên hệ → X_C2 mang CH; Hasaki: ghi nhận → hướng dẫn → X1 cửa hàng |
| Liên hệ CSKH trước, rồi **gửi online** | Khách: đóng gói gửi + báo mã VĐ; Hasaki: ghi mã → nhận & kiểm bưu phẩm |

### 1.3. Suy luận vận hành (có nhãn)

| Bước | Ghi chú |
|------|---------|
| Cập nhật yêu cầu đổi trả / hoàn tiền trên hệ thống đơn hàng | Theo dõi trên đơn mua |
| Kiểm còn hàng; hết hàng → hỏi SP khác hoặc trả–hoàn | Website không mô tả; **không** ghi bắt buộc hoàn |

---

## 2. Luồng BPMN

### Pool Khách hàng

```text
Nhu cầu đổi trả phát sinh
  → X_C1 Đến cửa hàng luôn hay liên hệ trước?
       ├─ Đến CH luôn → Mang SP tới cửa hàng (không gọi)
       └─ Liên hệ trước → Liên hệ tổng đài/CSKH
            → (← hướng dẫn từ Hasaki) X_C2 Mang CH hay gửi online?
                 ├─ Mang tới cửa hàng theo hướng dẫn
                 └─ Đóng gói gửi bưu điện → Báo mã vận đơn
  → Kết quả xử lý?
       ├─ Không hỗ trợ → Nhận thông báo → Kết thúc
       ├─ Đổi hoặc hoàn xong → Nhận hàng đổi / tiền hoàn → Kết thúc
       └─ Hết hàng muốn đổi → Chọn SP khác hoặc trả → Nhận đổi/hoàn → Kết thúc
```

### Pool Hasaki

```text
Yêu cầu đổi trả được tiếp nhận
  → X0 Walk-in hay liên hệ CSKH trước?
       ├─ Walk-in → Tiếp nhận → Nhận và kiểm tại cửa hàng
       └─ Liên hệ → Ghi nhận → Xác nhận lý do + hướng dẫn
            → X1 Mang tới cửa hàng hay trả online?
                 ├─ Cửa hàng → Nhận và kiểm tại cửa hàng
                 └─ Online → Ghi nhận mã VĐ → Nhận và kiểm hàng gửi về
  → Xét điều kiện theo bảng 30 ngày
  → X2 Theo bảng chính sách…?
       ├─ Không hỗ trợ → giải thích → Kết thúc
       ├─ Chỉ đổi mới → Cập nhật hệ thống → kiểm còn hàng …
       └─ Đổi mới hoặc trả không thu phí → Cập nhật hệ thống → X3 Đổi | Trả
  Kiểm còn hàng (X4):
       ├─ Còn → giao/gửi đổi → xử lý hàng → Kết thúc đổi
       └─ Hết → Thông báo → X5 SP khác | Trả hàng → (đổi lại / hoàn)
```

### Message flow (đồng bộ hai pool)

| Hướng | Nội dung |
|-------|----------|
| Khách → Hasaki | Walk-in / liên hệ → *start* tiếp nhận |
| Hasaki → Khách | Hướng dẫn bước tiếp (sau liên hệ) |
| Khách → Hasaki | SP tại cửa hàng; bưu phẩm; mã vận đơn |
| Hasaki → Khách | Không hỗ trợ / hết hàng / hàng đổi / tiền hoàn |

### Cổng XOR nghiệp vụ (Hasaki)

| Mã | Câu hỏi | Nhánh |
|----|---------|-------|
| X0 | Đến cửa hàng luôn hay liên hệ CSKH trước? | Walk-in / Liên hệ |
| X1 | Mang tới cửa hàng hay trả hàng online? | Cửa hàng / Online (sau liên hệ) |
| X2 | Theo bảng chính sách 30 ngày, được hỗ trợ thế nào? | Không hỗ trợ / Chỉ đổi mới / Đổi hoặc trả không thu phí |
| X3 | Khách chọn đổi mới hay trả không thu phí? | Đổi / Trả (chỉ khi X2 cho phép cả hai) |
| X4 | Sản phẩm muốn đổi còn hàng? | Còn / Hết *(suy luận)* |
| X5 | Khách chọn phương án nào? | SP khác / Trả hàng *(suy luận)* |

**Không vẽ:** chuỗi cổng checklist; tách kênh hoàn chi tiết; nhánh “chờ nhập hàng”; hoàn bằng mã phiếu quà.

---

## 3. Bằng chứng và phỏng vấn

**Bằng chứng:** [Đổi trả Hasaki](https://hotro.hasaki.vn/doi-tra-hoan-tien.html).  
**Hỏi thêm:** tỷ lệ walk-in vs liên hệ trước; hết hàng khi đổi xử lý thế nào; thời gian hoàn VNpay thực tế.

---

## 4. Phân tích định tính (rút gọn)

| Hoạt động | VA / BVA / NVA |
|-----------|----------------|
| Xét điều kiện; giao đổi; hoàn tiền; giải thích từ chối | VA |
| Tiếp nhận; kiểm SP; cập nhật hệ thống; hướng dẫn gửi online | BVA |
| Chờ bưu phẩm; chờ hoàn cổng TT; chọn lại SP khi hết hàng | NVA / chờ |

---

## 5. Định lượng (ước lượng — đổi tại cửa hàng, còn hàng)

| Bước | Phút |
|------|------|
| Tiếp nhận + kiểm SP | 8 |
| Xét điều kiện + cập nhật hệ thống | 12 |
| Kiểm còn hàng + giao đổi | 8 |
| Xử lý hàng trả | 4 |
| **Chu kỳ** | **~32** |

Hoàn thẻ/VNpay đo bằng **ngày làm việc** (website), không gộp vào 32 phút.

---

## 6. Checklist

- [x] Hai pool white-box + message flow đồng bộ (walk-in / liên hệ / online)
- [x] Khớp bảng chính sách X2 + phương thức hoàn website  
- [x] Hết hàng khi đổi: suy luận, không bắt buộc hoàn  
- [ ] Số liệu phỏng vấn thay ước lượng  
