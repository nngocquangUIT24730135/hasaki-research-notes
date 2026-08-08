# Yêu cầu đồ án — Hệ thống quản trị quy trình nghiệp vụ (*Business Process Management*)

Tài liệu này diễn giải lại **thang điểm đánh giá (rubik)** của giảng viên để nhóm dễ theo dõi khi làm báo cáo. Mỗi mục lớn tối đa **10 điểm**.

## Cách quy đổi điểm thành phần

Khi tiêu chí cho điểm theo tỷ lệ hoàn thành:

| Mức đạt tiêu chí | Điểm quy ra |
|------------------|-------------|
| Từ 75% trở lên | 1 |
| Từ 25% đến dưới 75% | 0,5 |
| Dưới 25% | 0 |

---

## 1. Liệt kê tối thiểu 10 quy trình (*process identification*) — 10 điểm

Mỗi quy trình đạt yêu cầu được 1 điểm. Tổng số quy trình tối thiểu là **10**.

Trong đó:

| Nhóm quy trình | Số lượng tối thiểu | Giải thích |
|----------------|-------------------|------------|
| Quy trình quản lý (*management processes*) | 3 | Quy trình định hướng, kiểm soát (ví dụ: hoạch định, duyệt nhà cung cấp, quản lý tồn kho) |
| Quy trình cốt lõi (*core processes*) | 3 | Quy trình tạo giá trị trực tiếp cho khách hàng (bán hàng, giao hàng, đổi trả…) |
| Quy trình hỗ trợ (*support processes*) | 3 | Quy trình hỗ trợ vận hành (nhân sự, tài chính, công nghệ thông tin…) |
| Vẽ kiến trúc quy trình (*process architecture*) | — | Thêm 1 điểm nếu có sơ đồ kiến trúc bao quát đủ tổng số quy trình đã liệt kê |

**Với mỗi quy trình, báo cáo cần nêu đủ bốn nội dung:**

1. **Tác nhân (*actors*):** ai (hoặc hệ thống nào) tham gia thực hiện.  
2. **Mô tả bằng lời:** các bước chính của quy trình.  
3. **Khách hàng của quy trình (*process customer*):** bên nhận kết quả đầu ra (có thể là khách mua hàng hoặc bộ phận nội bộ).  
4. **Kết quả có thể xảy ra (*outcomes*):** đầu ra thành công và các trường hợp kết thúc có kiểm soát (ví dụ: hủy đơn, từ chối đổi trả).

---

## 2. Mô hình hóa quy trình (*process modeling*) — 10 điểm

| Nội dung | Điểm |
|----------|------|
| Mô hình hóa 2 quy trình quản lý | 3 |
| Mô hình hóa 2 quy trình cốt lõi | 3 |
| Mô hình hóa 2 quy trình hỗ trợ | 3 |

Hình thức nộp liên quan phần mô hình:

- Slide thuyết trình: trình bày sâu **1** quy trình.  
- Báo cáo Word: có mô hình của ít nhất **2** quy trình.

### Độ phức tạp — cổng điều kiện (*gateways*)

**Cổng điều kiện (*gateway*)** là ký hiệu trên sơ đồ BPMN thể hiện chỗ quy trình phải chọn nhánh (ví dụ: đủ điều kiện giao 2 giờ hay không). Trong môn học thường dùng cổng **XOR** (chỉ đi đúng một nhánh).

| Số cổng điều kiện trên một sơ đồ | Điểm |
|----------------------------------|------|
| Nhiều hơn 7 | 1 |
| Nhiều hơn 5 | 0,75 |
| Nhiều hơn 3 | 0,5 |
| Các trường hợp còn lại | 0 |

Khi chấm, giảng viên còn xem: tách nhánh và gộp nhánh (*split/join*) có đúng không; ký hiệu BPMN có sai không; hoạt động (*activity*) trong quy trình có hợp lý không.

---

## 3. Phương pháp thực hiện — 10 điểm

### 3.1. Dựa trên bằng chứng (*evidence-based*)

Nhóm cần thu thập và trình bày (nếu có):

- Mô tả quy trình hiện có (tài liệu công ty hoặc trang chính sách công khai)  
- Sơ đồ tổ chức  
- Kế hoạch làm việc  
- Thuật ngữ và sổ tay  
- Biểu mẫu (biên bản họp, kịch bản phỏng vấn…)  

### 3.2. Phỏng vấn (*interview*)

Cần đủ bộ câu hỏi với các đối tượng liên quan:

| Loại câu hỏi | Số lượng tối thiểu | Cơ cấu |
|--------------|-------------------|--------|
| Câu hỏi định tính (*qualitative*) | 10 | 5 câu có cấu trúc (chọn đáp án / khoảng) + 5 câu không cấu trúc (mở) |
| Câu hỏi định lượng (*quantitative*) | 10 | 5 câu có cấu trúc + 5 câu không cấu trúc |

Nếu dưới 10 câu theo từng loại (theo ngưỡng rubik) thì phần câu hỏi đó được **0 điểm**.

**Giải thích nhanh:** câu hỏi *định tính* khai thác cách làm, nguyên nhân, trải nghiệm; câu hỏi *định lượng* xin số liệu (thời gian, tỷ lệ, chi phí…).

---

## 4. Phân tích quy trình — 10 điểm

### 4.1. Phân tích định tính (*qualitative analysis*) — 2 quy trình

Dùng bảng; phân tích trên quy trình. Mỗi mục theo thứ tự: **liệt kê → mô tả → đề xuất khắc phục**.

**(1) Phân tích giá trị gia tăng (*value-added analysis*)**

| Ký hiệu | Tên đầy đủ (tiếng Anh thường gặp trong giáo trình) | Ý nghĩa |
|---------|-----------------------------------------------------|---------|
| VA | Value-Adding | Hoạt động **tăng giá trị** cho khách hàng |
| BVA (còn gọi VBA) | Business Value-Adding | Hoạt động **cần cho doanh nghiệp** (kiểm soát, tuân thủ) nhưng khách không cảm nhận trực tiếp |
| NVA | Non-Value-Adding | Hoạt động **không tăng giá trị** (nên giảm hoặc loại) |

**(2) Phân tích lãng phí (*waste analysis*)**

| Loại (tên giáo trình) | Ý nghĩa |
|----------------------|---------|
| Move | Di chuyển thừa (hàng, giấy tờ, người) |
| Hold | Chờ / giữ / tồn đọng |
| Overdo | Làm thừa (lặp lại, kiểm tra quá mức không cần thiết) |

**(3) Phân tích nguyên nhân / các bên liên quan — chọn một trong ba**

- Biểu đồ Pareto (tập trung vào nguyên nhân chiếm nhiều nhất)  
- Phân tích nguyên nhân – kết quả  
- Mô hình xương cá (Fishbone): sắp xếp nguyên nhân theo nhóm Người – Phương pháp – Máy móc – Nguyên vật liệu – Môi trường…

### 4.2. Phân tích định lượng (*quantitative analysis*) — 2 quy trình

Tính toán trên quy trình bằng bảng; sau đó đề xuất khắc phục. Cần có:

1. **Thời gian** (từng bước hoặc tổng chu kỳ — *cycle time*)  
2. **Chất lượng** (liệt kê chỉ số, ví dụ tỷ lệ giao đúng hẹn)  
3. **Chi phí** (tính toán, thường quy từ thời gian nhân sự × đơn giá)  

---

## 5. Trình bày — Báo cáo — 10 điểm

### Slide

- Chính tả đúng  
- Font chữ: cỡ, màu, gạch đầu dòng nhất quán  
- Có đánh số trang, hình, bảng  
- Mỗi nhóm trình bày đúng thời gian quy định; quá giờ: mỗi 5 phút trừ 1 điểm  
- Bật camera khi báo cáo  

### Báo cáo Word

Theo mẫu báo cáo khóa luận của trường:  
https://httt.uit.edu.vn/cac-bieu-mau/

Yêu cầu hình thức:

- Chính tả; font nhất quán  
- Có mục lục trang, mục lục hình, mục lục bảng  
- Tiêu đề cho bảng biểu và hình ảnh  
- Tài liệu tham khảo  
- Nhãn hình đặt **dưới** hình; nhãn bảng đặt **trên** bảng  
- Có bảng chú thích viết tắt  

---

## Danh mục kiểm tra nhanh trước khi nộp

- [ ] Có từ 10 quy trình trở lên; mỗi quy trình đủ tác nhân (*actors*), mô tả bước, khách hàng quy trình (*process customer*), kết quả (*outcomes*)  
- [ ] Đủ ít nhất 3 quản lý, 3 cốt lõi (*core*), 3 hỗ trợ (*support*); có vẽ kiến trúc quy trình (*process architecture*)  
- [ ] BPMN: 2 quản lý + 2 cốt lõi + 2 hỗ trợ; chú ý cổng điều kiện (*gateways*), tách/gộp nhánh (*split/join*), ký hiệu  
- [ ] Slide trình bày sâu 1 quy trình; Word có ít nhất 2 mô hình  
- [ ] Bằng chứng (*evidence*) + phỏng vấn (*interview*): 10 câu định tính (*qualitative*) + 10 câu định lượng (*quantitative*) (mỗi loại 5 có cấu trúc / 5 không cấu trúc)  
- [ ] Phân tích định tính 2 quy trình + định lượng 2 quy trình (có bảng và hướng khắc phục)  
- [ ] Slide và Word đúng mẫu; bật camera; không quá giờ  
