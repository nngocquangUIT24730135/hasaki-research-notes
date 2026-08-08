# Tài liệu nghiên cứu đồ án — Hasaki Beauty & Clinic

Bộ tài liệu phục vụ đồ án môn **Hệ thống quản trị quy trình nghiệp vụ**, phân tích công ty **Hasaki Beauty & Clinic** (hasaki.vn), tập trung nhóm **quy trình cốt lõi**.

## Giới hạn phương pháp (đọc trước)

Trong các file dưới đây, nhóm phân biệt hai loại nội dung:

1. **Thông tin công bố:** lấy từ website, trang hỗ trợ khách hàng, báo chí (có ghi nguồn).  
2. **Suy luận theo chuẩn ngành:** dùng khi Hasaki không công bố quy trình nội bộ chi tiết (ví dụ cách chia ca soạn hàng, xử lý hết hàng lúc lấy hàng). Các bước này được ghi chú rõ để không nhầm với quan sát thực địa.

Nhóm **không** khẳng định toàn bộ nội dung là quy trình đang chạy đúng từng bước bên trong Hasaki.

## Cấu trúc thư mục

```text
deep_research/
├── README.md                 ← File này
├── 01-requirements/          Yêu cầu / thang điểm đồ án
├── 02-research/              Nghiên cứu mô hình kinh doanh & kiến trúc quy trình
├── 03-core/                  Quy trình cốt lõi, phân tích và hướng dẫn vẽ BPMN
└── 99-references/            Tài liệu tham khảo (bài mẫu cùng môn)
```

| Thư mục | Nội dung |
|---------|----------|
| [01-requirements](./01-requirements/) | Diễn giải rubik (thang điểm) đồ án |
| [02-research](./02-research/) | **Nguồn chuẩn:** mô hình kinh doanh, kiến trúc, ranh giới (B2 bắt đầu khi Đặt hàng; không đo thời gian xem ứng dụng), giao hàng 2 giờ |
| [03-core](./03-core/) | Năm quy trình cốt lõi; phân tích sâu hai quy trình vẽ BPMN — phải khớp `02-research` |
| [99-references](./99-references/) | Bài mẫu CellphoneS — học cách trình bày, không copy nghiệp vụ |

## Thứ tự đọc đề xuất

1. [Yêu cầu đồ án](./01-requirements/yeu_cau_do_an.md)  
2. [Nghiên cứu tổng quan](./02-research/research.md)  
3. [Câu chuyện khách hàng B2 & B4](./03-core/core_cau_chuyen.md) — đọc trước để hình dung  
4. [Quy trình cốt lõi](./03-core/core.md)  
5. [Phân tích nghiệp vụ B2 & B4](./03-core/ba_model_b2_b4.md)  
6. [Hướng dẫn vẽ BPMN](./03-core/core_bpmn.md)  

## Hai quy trình chọn để mô hình hóa (nhóm cốt lõi)

| Mã | Tên tiếng Việt | File hướng dẫn vẽ |
|----|----------------|-------------------|
| B2 | Xử lý đơn hàng trực tuyến và giao hàng (gồm giao nhanh 2 giờ) | [core_bpmn.md](./03-core/core_bpmn.md) — phần A |
| B4 | Đổi trả sản phẩm và hoàn tiền | [core_bpmn.md](./03-core/core_bpmn.md) — phần B |

File sơ đồ BPMN (định dạng `.bpmn`) nhóm tự vẽ trên Camunda Modeler hoặc bpmn.io theo hướng dẫn trên.

## Thuật ngữ viết tắt thường gặp

| Viết tắt | Nghĩa tiếng Việt |
|----------|------------------|
| BPMN | Ký hiệu chuẩn để vẽ sơ đồ quy trình nghiệp vụ |
| XOR | Cổng điều kiện loại trừ (chỉ đi một nhánh) |
| COD | Thanh toán khi nhận hàng |
| VA / BVA / NVA | Hoạt động tăng giá trị / tăng giá trị kinh doanh / không tăng giá trị (dùng khi phân tích định tính) |

Chi tiết thuật ngữ nghiệp vụ Hasaki nằm trong từng chương.
