# Quy trình B4 — Đổi trả hoặc hoàn tiền (*Return-to-Resolve*)

**Doanh nghiệp:** Hasaki Beauty & Clinic  
**Mức mô hình:** Level 2 (mô tả nghiệp vụ)  
**Phong cách:** Hai pool **white-box** — khách hàng chi tiết theo hành trình; Hasaki lộ bước vận hành (không black-box)  
**Chính sách (ưu tiên):** [Đổi trả – hoàn tiền](https://hotro.hasaki.vn/doi-tra-hoan-tien.html) (30 ngày, từ 01/06/2024)  
**BPMN:** [b4-doi-tra-hoac-hoan-tien.bpmn](./b4-doi-tra-hoac-hoan-tien.bpmn)  
**Ngày:** 09/08/2026  

> Level 2: kênh tiếp nhận → nhận hàng → chốt phương án → thực hiện. Chi tiết bảng 30 ngày / hết hàng / kênh hoàn là Level 3 hoặc ghi chú — không nhồi vào sơ đồ này.

---

## 1. Hồ sơ quy trình

| Trường | Nội dung |
|--------|----------|
| **Tên** | Đổi trả hoặc hoàn tiền |
| **Ai tham gia** | Khách hàng; NV cửa hàng / CSKH; kho; kế toán (hoàn tiền) |
| **Khách của quy trình** | Người muốn đổi hàng hoặc trả hàng lấy lại tiền |
| **Khi nào bắt đầu** | Khách mang hàng tới cửa hàng, hoặc liên hệ tổng đài / fanpage |
| **Kết thúc** | (1) Đổi hàng xong; (2) Hoàn tiền xong; (3) Không hỗ trợ đổi trả |

### 1.1. Chính sách đổi trả (website Hasaki)

> Từ ngày 01/06/2024, đổi trả trong vòng 30 ngày.

| | Sản phẩm lỗi (nhà cung cấp) | Sản phẩm lỗi (người sử dụng) | Sản phẩm không lỗi |
|--|----------------------------|------------------------------|--------------------|
| **1 – 30 ngày** | Đổi mới — Trả không thu phí | Không hỗ trợ đổi trả | Đổi mới |
| **31 ngày trở đi** | Không hỗ trợ đổi trả | | |

Chi tiết bảng trên được **áp dụng khi chốt phương án** (task Hasaki), không tách thành nhiều cổng trên sơ đồ L2.

---

## 2. Luồng Level 2 (hai pool white-box)

### Pool Khách hàng (white-box)

```text
Nhu cầu đổi trả phát sinh
  → Mang tới CH luôn hay liên hệ trước?
       ├─ (a) Mang sản phẩm đến cửa hàng Hasaki
       └─ (b) Liên hệ tổng đài / fanpage
            → Nhận hướng dẫn bước tiếp (← Hasaki)
            → Mang tới CH hay gửi hàng?
                 ├─ (b1) Đồng ý mang sản phẩm đến cửa hàng
                 └─ (b2) Gửi hàng theo hướng dẫn của Hasaki
  → Chờ Hasaki nhận và kiểm sản phẩm
  → Xác nhận phương án giải quyết với Hasaki   ← handshake (message flow hai chiều)
  → Phương án đã thống nhất?
       ├─ Không hỗ trợ → Nhận thông báo → Kết thúc
       ├─ Chốt hoàn tiền → Nhận tiền hoàn → Kết thúc
       └─ Chốt nhận SP thay thế → Nhận SP mới / thay thế → Kết thúc
```

### Pool Hasaki (white-box Level 2 — không black-box)

```text
Yêu cầu đổi trả được tiếp nhận
  → Walk-in hay liên hệ trước?
       ├─ Walk-in → Tiếp nhận → Nhận và kiểm tại cửa hàng
       └─ Liên hệ → Ghi nhận → Hướng dẫn bước tiếp (→ khách)
            → Mang tới CH hay gửi hàng?
                 ├─ Mang tới CH → Nhận và kiểm tại cửa hàng
                 └─ Gửi hàng → Nhận và kiểm hàng gửi về
  → Xét điều kiện đổi trả theo chính sách
  → Xác nhận phương án giải quyết với khách hàng   ← nghiệp vụ quan trọng
  → Phương án đã thống nhất?
       ├─ Không hỗ trợ → Giải thích → Kết thúc
       ├─ Hoàn tiền → Thực hiện hoàn tiền → Kết thúc
       └─ Đổi / SP thay thế → Giao / gửi SP → Kết thúc
```

### Message flow (đồng bộ)

| Hướng | Nội dung |
|-------|----------|
| Khách → Hasaki | Mang tới CH (walk-in) / liên hệ tổng đài–fanpage |
| Hasaki → Khách | Hướng dẫn mang CH hoặc gửi hàng về đâu |
| Khách → Hasaki | Mang theo hướng dẫn / gửi hàng |
| **Hasaki → Khách** | **Đề xuất phương án giải quyết** |
| **Khách → Hasaki** | **Xác nhận đồng ý phương án giải quyết** |
| Hasaki → Khách | Không hỗ trợ / hoàn tiền / giao SP đổi |

> Bước **xác nhận phương án giải quyết** là tương tác hai bên (không gộp vào “xét điều kiện” nội bộ): Hasaki đề xuất sau khi xét chính sách; khách xác nhận trước khi thực hiện hoàn / đổi.

### Cổng XOR (gọn L2)

| Pool | Câu hỏi | Nhánh |
|------|---------|-------|
| KH | Mang tới CH luôn hay liên hệ? | (a) / (b) |
| KH | Mang tới CH hay gửi hàng? | (b1) / (b2) |
| KH | Phương án đã thống nhất? | Không hỗ trợ / Hoàn / Đổi |
| Hasaki | Walk-in hay liên hệ? | Walk-in / Liên hệ |
| Hasaki | Mang tới CH hay gửi hàng? | CH / Online |
| Hasaki | Phương án đã thống nhất? | Không hỗ trợ / Hoàn / Đổi |

**Không vẽ ở L2:** tách nhánh bảng 30 ngày; kiểm tồn / hết hàng; chi tiết kênh hoàn; disposition hàng trả.

---

## 3. Bằng chứng và phỏng vấn

**Bằng chứng:** [Đổi trả Hasaki](https://hotro.hasaki.vn/doi-tra-hoan-tien.html).  
**Hỏi thêm:** tỷ lệ walk-in vs liên hệ; hết hàng khi đổi; thời gian hoàn thực tế (đưa vào L3 nếu cần).

---

## 4. Phân tích định tính (rút gọn)

| Hoạt động | VA / BVA / NVA |
|-----------|----------------|
| Xác nhận phương án với khách; giao đổi; hoàn tiền; giải thích từ chối | VA |
| Tiếp nhận; kiểm SP; xét điều kiện; hướng dẫn gửi hàng | BVA |
| Chờ Hasaki nhận và kiểm; chờ hoàn | NVA / chờ |

---

## 5. Checklist

- [x] Level 2: hai pool white-box (KH hành trình; Hasaki không black-box)
- [x] Kênh (a)/(b)/(b1)/(b2) + xác nhận phương án (message flow hai chiều) + hoàn / đổi / từ chối
- [ ] Số liệu phỏng vấn thay ước lượng
- [ ] Chi tiết chính sách / tồn kho (Level 3) nếu cần
