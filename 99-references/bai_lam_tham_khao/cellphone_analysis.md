# Phân tích bài làm tham khảo: CellphoneS

Tài liệu nguồn: `CellPhones.pdf` / `CellPhones.md`  
Đề tài: *Tìm hiểu hệ thống quy trình nghiệp vụ của công ty CellphoneS*  
Mục đích file này: rút cấu trúc bài làm để nhóm áp dụng cho Hasaki.

---

## 1. Cấu trúc tổng thể bài làm

| Chương | Nội dung chính |
|--------|----------------|
| Chương 1 | Giới thiệu công ty: lịch sử, quy mô, tổ chức, hoạt động kinh doanh |
| Chương 2 | Process architecture: phân loại quy trình Quản lý / Cốt lõi / Hỗ trợ |
| Chương 3 | Mô hình hóa BPMN + phân tích định tính & định lượng cho từng quy trình chọn |
| Chương 4 | Kết luận |

Điểm đáng học: mỗi quy trình BPMN đều có **mô tả văn bản → tác nhân → khách hàng quy trình → kết quả → bảng VA/BVA/NVA → bảng lãng phí → bảng thời gian/chi phí**.

---

## 2. Process architecture của CellphoneS (12 quy trình)

Bài làm phân **3 nhóm**, tổng **12 quy trình** (đúng “đẹp” theo yêu cầu 12–14).

### 2.1. Quy trình quản lý / chiến lược (4)

| # | Quy trình | Ý chính |
|---|-----------|---------|
| 1 | Hoạch định chiến lược kinh doanh | Kế hoạch thị trường, sản phẩm, cạnh tranh |
| 2 | Quản lý và mở rộng chuỗi cửa hàng | Mở chi nhánh, theo dõi hiệu suất cửa hàng |
| 3 | Quản lý kho vận | Xuất – nhập – tồn tại kho tổng |
| 4 | Quản lý quan hệ nhà cung cấp | Tìm, đánh giá, hợp tác NCC |

### 2.2. Quy trình cốt lõi (4)

| # | Quy trình | Ý chính |
|---|-----------|---------|
| 5 | Bán hàng và tư vấn khách hàng | Offline + online |
| 6 | Xử lý đơn hàng và vận chuyển | Xác nhận, đóng gói, giao hàng |
| 7 | Bảo hành và sửa chữa sản phẩm | Tiếp nhận lỗi, sửa/đổi trả |
| 8 | Chăm sóc khách hàng sau bán | Khiếu nại, hỗ trợ sử dụng |

### 2.3. Quy trình hỗ trợ (4)

| # | Quy trình | Ý chính |
|---|-----------|---------|
| 9 | Tuyển dụng và đào tạo nhân sự | HR |
| 10 | Tài chính – kế toán | Doanh thu, chi phí, lương |
| 11 | Kiểm soát chất lượng (QC) | Chuẩn hàng trước khi bán |
| 12 | Công nghệ thông tin | Ổn định hệ thống, xử lý sự cố |

---

## 3. 6 quy trình được mô hình hóa BPMN (2–2–2)

Yêu cầu đồ án: **2 quản lý + 2 cốt lõi + 2 hỗ trợ**. CellphoneS chọn như sau:

| Nhóm | Quy trình chọn BPMN | Lý do hợp lý |
|------|---------------------|--------------|
| Quản lý | Phê duyệt nhà cung cấp | Nhiều nhánh: đã có trong CSDL? đạt sơ bộ? đạt pháp lý? |
| Quản lý | Kiểm kê kho | Có/không lệch tồn, xử lý chênh lệch |
| Cốt lõi | Mua hàng online | Thanh toán, tồn kho, giao hàng, COD… |
| Cốt lõi | Chăm sóc khách hàng | Phân loại yêu cầu, leo thang xử lý |
| Hỗ trợ | Tuyển dụng | Lọc hồ sơ, phỏng vấn, đạt/không đạt |
| Hỗ trợ | Công nghệ thông tin | Tiếp nhận ticket, mức độ sự cố, escalate |

**Lưu ý:** Trong mục lục, cả 6 quy trình đều được phân tích định tính **và** định lượng. Theo rubric hiện tại của lớp (2 định tính + 2 định lượng), nhóm Hasaki **không bắt buộc** phân tích đủ 6; chỉ cần chọn 2 + 2 rõ ràng.

---

## 4. Cách bài làm mô tả mỗi quy trình (template)

Với mỗi quy trình BPMN, CellphoneS trình bày đủ 4 yếu tố yêu cầu:

1. **Tác nhân** – ai tham gia (lane/pool trong BPMN)  
2. **Mô tả văn bản** – kể lại luồng xử lý bằng lời  
3. **Khách hàng của quy trình** – người/bộ phận *nhận kết quả* (không nhất thiết là khách mua hàng cuối)  
4. **Kết quả của quy trình** – đầu ra thành công / thất bại có kiểm soát  

### Ví dụ rút từ “Phê duyệt nhà cung cấp”

| Thành phần | Nội dung bài làm |
|------------|------------------|
| Tác nhân | Quản lý NCC, Mua hàng, Pháp lý, NCC tiềm năng |
| Khách hàng quy trình | Bộ phận quản lý NCC (nhận NCC đã được duyệt) |
| Kết quả | Hợp đồng ký thành công **hoặc** NCC lưu CSDL chờ lần sau |
| Phân tích định tính | Bảng VA / BVA / NVA + bảng lãng phí Move/Hold/Overdo |
| Phân tích định lượng | Thời gian từng bước + chi phí nhân sự |

---

## 5. Cách bài làm làm phân tích

### Định tính

- **Giá trị gia tăng:** gắn nhãn mỗi hoạt động = VA / BVA / NVA, ghi người thực hiện, đề xuất khắc phục NVA.  
- **Lãng phí:** Move (di chuyển), Hold (chờ), Overdo (làm thừa) — liệt kê, mô tả, khắc phục.  
- **Các bên liên quan:** rubric cho phép chọn Pareto / Root-cause / Fishbone; bài CellphoneS nghiêng về bảng VA + lãng phí (nhóm Hasaki nên **bổ sung rõ 1 mô hình** trong 3 loại để khớp rubric).

### Định lượng

- **Thời gian:** bảng min/max hoặc thời gian từng bước.  
- **Chi phí:** quy đổi thời gian nhân sự × đơn giá.  
- **Chất lượng:** bài làm đề cập trong tóm tắt nhưng bảng chi tiết chủ yếu là thời gian + chi phí → nhóm Hasaki nên **thêm chỉ số chất lượng** (tỷ lệ lỗi, tỷ lệ hoàn tất đúng hạn…).

---

## 6. Điểm mạnh / điểm cần cải khi học theo bài này

**Điểm mạnh**

- Architecture đủ 12 quy trình, phân nhóm rõ.  
- 6 BPMN đúng tỷ lệ 2–2–2.  
- Mỗi quy trình có mô tả + tác nhân + khách hàng quy trình + kết quả.  
- Có bảng phân tích, không chỉ vẽ hình.

**Điểm cần làm tốt hơn cho đồ án Hasaki**

- Công khai **đếm cổng điều kiện (XOR/OR)** để đạt mốc >7 cổng (1 điểm).  
- Tách rõ **2 quy trình chỉ phân tích định tính** và **2 quy trình chỉ/định lượng sâu** theo rubric (tránh dàn trải như bài mẫu).  
- Chọn quy trình **đặc trưng ngành** (với Hasaki: O2O, NowFree 2H, Clinic, đổi trả 30 ngày, duyệt NCC merchant) thay vì copy nguyên quy trình điện thoại/sửa chữa.  
- Ghi **nguồn tham khảo** rõ ràng (bài CellphoneS khá mỏng về citation công khai).

---

## 7. Mapping nhanh: CellphoneS → Hasaki

| CellphoneS | Hasaki (gợi ý tương đương) |
|------------|----------------------------|
| Phê duyệt NCC | Phê duyệt / hợp tác nhà cung cấp (merchant.hasaki.vn) |
| Kiểm kê kho | Quản lý tồn kho đa kênh O2O |
| Mua hàng online | Xử lý đơn online + giao NowFree 2H |
| Chăm sóc KH | CSKH / khiếu nại hotline 1800 6310 |
| Tuyển dụng | Tuyển dụng nhân sự cửa hàng & Clinic |
| IT | Xử lý sự cố hệ thống / Hasaki Work |
| Bảo hành–sửa chữa | Đổi trả 30 ngày **hoặc** đặt lịch & điều trị Clinic |

Nghiệp vụ Hasaki (Core): xem [`../../03-core/`](../../03-core/) và nghiên cứu tổng quan [`../../02-research/research.md`](../../02-research/research.md).
