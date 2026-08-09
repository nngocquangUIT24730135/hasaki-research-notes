# Tài liệu nghiên cứu đồ án — Hasaki Beauty & Clinic

Bộ tài liệu phục vụ đồ án môn **Hệ thống quản trị quy trình nghiệp vụ** (*Business Process Management*), phân tích **Hasaki Beauty & Clinic** (hasaki.vn), tập trung nhóm **quy trình cốt lõi** (*core processes*).

---

## Cách tư duy làm đồ án (nguyên tắc làm việc)

Đây là khung suy nghĩ nhóm dùng khi nghiên cứu và viết tài liệu — cũng là cách prompt / định hướng khi làm việc với trợ lý AI.

### 1. Tham khảo bài mẫu cùng môn (cùng kiểu mô hình kinh doanh)

- Lấy [bài CellphoneS](./99-references/bai_lam_tham_khao/) làm **mẫu trình bày và cấu trúc đồ án** (kiến trúc ba lớp, đủ bốn yếu tố mỗi quy trình, mô hình hóa, phân tích định tính / định lượng).  
- **Bản chất gần cùng mô hình kinh doanh:** bán lẻ đa kênh (cửa hàng + kênh số), xử lý đơn, giao hàng, đổi trả / chăm sóc sau bán.  
- **Khác ngành hàng** (điện thoại / thiết bị số vs mỹ phẩm & clinic) → **học cách làm, không copy nghiệp vụ** hay chính sách của CellphoneS sang Hasaki.

### 2. Bám lý thuyết môn học (Fundamentals of BPM)

- Nền tảng khái niệm và phương pháp lấy từ slide / giáo trình **Fundamentals of Business Process Management** trong [99-references/slides](./99-references/slides/) (nhận diện quy trình, kiến trúc, ranh giới, mô hình hóa BPMN, phân tích định tính VA/BVA/NVA và lãng phí, phân tích định lượng thời gian chu kỳ…).  
- Thuật ngữ môn học viết tiếng Việt dễ hiểu, mở ngoặc tiếng Anh khi cần (*process boundary*, *cycle time*, *Order-to-Delivery*…).

### 3. Research theo thứ tự bằng chứng → cùng ngành → suy luận hợp lý

1. **Hasaki trên internet trước:** trang hỗ trợ, chính sách đặt hàng / giao hàng / đổi trả, thông tin công bố (ghi nguồn).  
2. **Doanh nghiệp cùng ngành / cùng mô hình:** bán lẻ mỹ phẩm–chăm sóc cá nhân đa kênh, giao nhanh từ cửa hàng / điểm gần khách (chuỗi tương tự trong nước hoặc quốc tế).  
3. **Suy luận sát thực tế:** chỉ khi Hasaki không công bố chi tiết nội bộ (ví dụ xử lý hết hàng lúc soạn, ưu tiên đơn 2 giờ). Mọi suy luận phải **ghi chú rõ**, không giả làm quan sát thực địa.

Nhóm **không** khẳng định toàn bộ bước trong tài liệu là quy trình nội bộ đang chạy đúng từng phút tại Hasaki.

### 4. Tập trung nghiệp vụ, không sa vào kỹ thuật

- Sơ đồ và phân tích nói về **ai làm gì**, **quyết định nghiệp vụ nào**, **kết quả nào đóng lần chạy** (đặt hàng → giao / hủy; đổi hàng hoặc hoàn tiền…).  
- **Không** lấy tầng Frontend / Backend, API, khóa tồn tạm, thuật toán chống gian lận… làm xương sống mô hình. Nếu cần nhắc hệ thống, chỉ ở mức năng lực vận hành hoặc chú thích suy luận ngành.  
- Làn (*lane*) gắn **vai trò nghiệp vụ** (kho / cửa hàng, đơn vị giao, chăm sóc đơn), không gắn tầng phần mềm.

### 5. Nguồn chuẩn và đồng bộ

- **`02-research/research.md`** là **nguồn chuẩn** (*source of truth*) cho mô hình kinh doanh, kiến trúc và ranh giới.  
- `03-core` phải khớp research. Lệch ranh giới hoặc chính sách → **sửa research trước**, rồi mới cascade sang core / BPMN / phân tích.

---

## Giới hạn phương pháp (nhắc lại nhanh)

| Loại nội dung | Cách dùng |
|---------------|-----------|
| Thông tin công bố Hasaki | Ưu tiên; kèm đường dẫn |
| Chuẩn / thực hành cùng ngành | Bổ sung khi thiếu chi tiết công bố |
| Suy luận hợp lý | Có nhãn rõ; không bịa thành “đã quan sát nội bộ” |

---

## Cấu trúc thư mục

```text
hasaki-research-notes/
├── README.md                 ← File này (cách tư duy + bản đồ đọc)
├── 01-requirements/          Yêu cầu / thang điểm đồ án
├── 02-research/              Nghiên cứu mô hình kinh doanh & kiến trúc quy trình (SoT)
├── 03-core/                  Quy trình cốt lõi, phân tích và hướng dẫn vẽ BPMN
├── 98-work-to-be-reviewed/   Bản nháp / feedback thành viên (không phải SoT)
└── 99-references/            Bài mẫu CellphoneS + slide Fundamentals of BPM
```

| Thư mục | Nội dung |
|---------|----------|
| [01-requirements](./01-requirements/) | Diễn giải rubik (thang điểm) đồ án |
| [02-research](./02-research/) | **Nguồn chuẩn:** kiến trúc; B2 = một quy trình từ Đặt hàng đến giao/hủy (gồm 2H và giao thường); B4 = đổi trả hoặc hoàn tiền; không đo thời gian xem app |
| [03-core](./03-core/) | Năm quy trình cốt lõi; phân tích sâu B2 & B4; hướng dẫn BPMN — phải khớp `02-research` |
| [99-references](./99-references/) | CellphoneS (mẫu trình bày) + slides FBPM (lý thuyết) |

---

## Thứ tự đọc đề xuất

1. File này — nắm **cách tư duy**  
2. [Yêu cầu đồ án](./01-requirements/yeu_cau_do_an.md)  
3. [Nghiên cứu tổng quan](./02-research/research.md)  
4. [Câu chuyện khách hàng B2 & B4](./03-core/core_cau_chuyen.md)  
5. [Quy trình cốt lõi](./03-core/core.md)  
6. [Phân tích nghiệp vụ B2 & B4](./03-core/ba_model_b2_b4.md)  
7. [Hướng dẫn vẽ BPMN](./03-core/core_bpmn.md)  
8. Khi cần: [slides FBPM](./99-references/slides/) · [bài CellphoneS](./99-references/bai_lam_tham_khao/)

---

## Hai quy trình chọn để mô hình hóa (nhóm cốt lõi)

| Mã | Tên tiếng Việt | Chuỗi đầu–cuối (EN) | File hướng dẫn vẽ |
|----|----------------|---------------------|-------------------|
| B2 | Xử lý đơn hàng online và giao hàng (gồm giao nhanh 2 giờ và giao thường) | *Order-to-Delivery* | [core_bpmn.md](./03-core/core_bpmn.md) — phần A |
| B4 | Đổi trả hoặc hoàn tiền | *Return-to-Resolve* | [core_bpmn.md](./03-core/core_bpmn.md) — phần B |

File `.bpmn` nhóm tự vẽ trên Camunda Modeler hoặc bpmn.io theo hướng dẫn trên.

---

## Thuật ngữ viết tắt thường gặp

| Viết tắt / thuật ngữ | Nghĩa |
|----------------------|--------|
| BPMN | *Business Process Model and Notation* — ký hiệu chuẩn để vẽ sơ đồ quy trình nghiệp vụ |
| XOR | Cổng điều kiện loại trừ (*exclusive gateway* — chỉ đi một nhánh) |
| COD | Thanh toán khi nhận hàng (*cash on delivery*) |
| VA / BVA / NVA | Tăng giá trị / tăng giá trị kinh doanh / không tăng giá trị (*value-adding / business value-adding / non-value-adding*) |
| Ranh giới quy trình | *Process boundary* |
| Kiến trúc quy trình | *Process architecture* |
| Thời gian chu kỳ | *Cycle time* |
| Khách hàng của quy trình | *Process customer* |
| Sự kiện kích hoạt | *Trigger* |
| Đối tượng theo dõi / lần chạy | *Case* / *process instance* |

Chi tiết thuật ngữ nghiệp vụ Hasaki nằm trong từng chương.
