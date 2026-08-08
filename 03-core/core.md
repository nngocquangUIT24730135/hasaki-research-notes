# Quy trình cốt lõi (*core processes*) — Hasaki Beauty & Clinic

**Phạm vi:** các nội dung đồ án gắn nhóm **quy trình cốt lõi (*core processes*)**.  
**Nguồn khung:** [nghiên cứu tổng quan — SoT](../02-research/research.md), [yêu cầu đồ án](../01-requirements/yeu_cau_do_an.md).  
**Phân tích sâu B2 và B4:** [ba_model_b2_b4.md](./ba_model_b2_b4.md) · [core_bpmn.md](./core_bpmn.md).  
**Mức mô hình:** kết hợp *thông tin công bố* trên trang hỗ trợ Hasaki và *suy luận theo chuẩn ngành* khi không có sổ tay nội bộ. Nhóm không khẳng định đã quan sát từng bước tại kho/cửa hàng Hasaki. Ranh giới (*process boundaries*) B2/B4 và cách đo thời gian chu kỳ (*cycle time*) **bám** `02-research/research.md`.  
**Ngày:** 08/08/2026

---

## 0. Đối chiếu với thang điểm đồ án (phần cốt lõi)

| Mục trong rubik | Nội dung file này đáp ứng |
|-----------------|---------------------------|
| Liệt kê quy trình (≥ 3 cốt lõi) | **5** quy trình B1–B5; mỗi quy trình đủ tác nhân (*actors*), mô tả bước, khách hàng quy trình (*process customer*), kết quả (*outcomes*) |
| Kiến trúc quy trình (*process architecture*) | Sơ đồ vị trí nhóm cốt lõi trong toàn bộ kiến trúc |
| Mô hình hóa 2 quy trình cốt lõi | Chọn **B2** và **B4**; hướng dẫn vẽ tại `core_bpmn.md` |
| Cổng điều kiện (*gateways*) nhiều hơn 7 | B2 thiết kế ~10 cổng vận hành thật; B4 ~7 cổng có nghĩa (không xẻ checklist thẩm định) — xem `core_bpmn.md` |
| Bằng chứng và phỏng vấn (*evidence* / *interview*) | Mục 3: bằng chứng + 10 câu định tính + 10 câu định lượng |
| Phân tích định tính (*qualitative analysis*) 2 quy trình | Mục 4: B2 và B4 |
| Phân tích định lượng (*quantitative analysis*) 2 quy trình | Mục 5: B2 và B4 (số liệu có chú thích ước lượng) |
| Trình bày | Mục 6: checklist nội dung đưa vào Word / slide |

**Hai quy trình chọn để vẽ sơ đồ và phân tích sâu:**

| Mã | Tên | Lý do chọn |
|----|-----|------------|
| B2 | Xử lý đơn hàng trực tuyến và giao hàng (gồm giao nhanh 2 giờ) | Đặc trưng Hasaki; nhiều nhánh quyết định; đủ chính sách công bố |
| B4 | Đổi trả sản phẩm và hoàn tiền (30 ngày) | Chính sách rõ; nhiều điều kiện; phù hợp phân tích định tính và định lượng |

---

## 1. Vị trí nhóm cốt lõi trong kiến trúc quy trình (*process architecture*)

Quy trình **cốt lõi** tạo và giao giá trị trực tiếp cho khách hàng cuối.

```text
┌────────────── QUẢN LÝ (ngoài phạm vi file này) ──────────────┐
│ A1 Chiến lược │ A2 Nhà cung cấp │ A3 Tồn kho │ A4 Chất lượng │
└────────────────────────────┬────────────────────────────────┘
                             │ tồn khả dụng / hàng được phép bán
┌────────────────────────────▼────────────────────────────────┐
│ CỐT LÕI                                                     │
│  B1 Bán hàng và tư vấn tại cửa hàng                         │
│  B2 Đơn online và giao hàng (kể cả 2 giờ)  ← vẽ sơ đồ + PT  │
│  B3 Đặt lịch và thực hiện Clinic / Spa                      │
│  B4 Đổi trả và hoàn tiền                   ← vẽ sơ đồ + PT  │
│  B5 Chăm sóc khách hàng và khiếu nại                        │
└────────────────────────────┬────────────────────────────────┘
┌────────────────────────────▼────────────────────────────────┐
│ HỖ TRỢ (ngoài phạm vi): C1 Nhân sự │ C2 Tài chính │ C3 Tiếp thị │ C4 Công nghệ │
└─────────────────────────────────────────────────────────────┘
```

**Ranh giới nhanh (*process boundaries*) giữa các quy trình cốt lõi:**

| Quy trình | Đối tượng theo dõi | Không gộp với |
|-----------|--------------------|---------------|
| B1 | Giao dịch tại quầy / lượt tư vấn | Đơn online (B2), lịch clinic (B3) |
| B2 | Mã đơn trên kênh của Hasaki (sau Đặt hàng) | Duyệt ứng dụng không đặt; đổi trả sau nhận (B4); hoạch định tồn (A3 — chỉ đọc tồn khả dụng) |
| B3 | Lượt hẹn / liệu trình | Đơn bán lẻ kèm (nếu có thì mở B1 hoặc B2 mới) |
| B4 | Yêu cầu đổi / trả | Đơn gốc đã kết thúc ở B1 hoặc B2 |
| B5 | Yêu cầu hỗ trợ / khiếu nại | Có thể chuyển sang B4 nếu bản chất là đổi trả |

---

## 2. Năm quy trình cốt lõi (đủ bốn yếu tố theo rubik)

### B1. Bán hàng và tư vấn tại cửa hàng

| Trường | Nội dung |
|--------|----------|
| **Tác nhân (*actors*)** | Khách hàng; nhân viên tư vấn; thu ngân; kho cửa hàng; hệ thống bán hàng tại quầy / thành viên |
| **Khách hàng của quy trình (*process customer*)** | Khách mua hoặc được tư vấn tại cửa hàng |
| **Kết quả có thể (*outcomes*)** | (1) Giao dịch hoàn tất; (2) Chỉ tư vấn, không mua; (3) Giới thiệu / đặt lịch Clinic (mở B3 nếu khách đồng ý) |

**Các bước:**

1. Khách đến cửa hàng, nêu nhu cầu.  
2. Nhân viên tư vấn, kiểm tra tồn và chương trình khuyến mãi.  
3. Khách quyết định mua hoặc không.  
4. Nếu mua: thanh toán, trừ tồn, xuất hóa đơn theo yêu cầu.  
5. Giao hàng tại quầy; có thể gợi ý dịch vụ Clinic.  
6. Kết thúc lượt bán / tư vấn.

---

### B2. Xử lý đơn hàng trực tuyến và giao hàng (gồm giao nhanh 2 giờ)

| Trường | Nội dung |
|--------|----------|
| **Tác nhân (*actors*)** | Khách; hệ thống website/ứng dụng; cổng thanh toán; nhân viên kho/cửa hàng; đối tác vận chuyển / nhân viên giao; chăm sóc khách hàng – vận hành đơn |
| **Khách hàng của quy trình (*process customer*)** | Khách đặt trên Hasaki.vn / ứng dụng |
| **Kết quả có thể (*outcomes*)** | (1) Giao thành công và đã thanh toán; (2) Hủy có kiểm soát (+ hoàn trong 30 ngày nếu đã trả trước); (3) Giao thành công kèm phiếu 100.000đ nếu giao 2 giờ trễ đủ điều kiện |

**Nguồn:** trang hỗ trợ đặt hàng / vận chuyển 2 giờ / quy trình giao hàng; chia giai đoạn theo chuẩn chu kỳ xử lý đơn bán lẻ (xem `ba_model_b2_b4.md`).

| Giai đoạn | Nội dung chính |
|-----------|----------------|
| 1. Cam kết giao hàng (trên màn hình trước khi đặt) | Theo địa chỉ hiện lựa chọn vận chuyển; kiểm điều kiện 2 giờ (vùng, giá trị đơn, hàng sẵn tại kho gần); tính phí; khách chọn vận chuyển và thanh toán (đơn trên 5 triệu chỉ thanh toán trước). *Chưa có mã đơn nếu khách dừng.* |
| 2. Tạo đơn và sẵn sàng soạn | **Kích hoạt:** bấm Đặt hàng → tạo mã đơn; nếu thanh toán trước thì phải thành công mới soạn; nếu thanh toán khi nhận thì soạn sau khi tạo đơn; đơn 2 giờ nên được ưu tiên soạn *(suy luận ngành)* |
| 3. Soạn – đóng gói – bàn giao | Xác nhận còn hàng lúc soạn; soạn; đóng gói chuẩn Hasaki; bàn giao đơn vị giao |
| 4. Giao đến khách | Giao tận nơi; thu tiền nếu thanh toán khi nhận; khách ký nhận (không đồng kiểm; nên quay video khi mở) |
| 5. Ngoại lệ và đóng đơn | Giao không thành → hẹn lại; không liên lạc **3 ngày** → hủy và hoàn; điểm không giao được → đổi địa chỉ hoặc hủy; giao 2 giờ trễ → xét phiếu 100.000đ |

**Hồ sơ rút gọn:** kích hoạt = bấm Đặt hàng; đối tượng theo dõi = mã đơn. Duyệt ứng dụng / xem hàng **ngoài** quy trình. Chỉ số gợi ý: tỷ lệ giao đúng giờ cam kết; tỷ lệ giao thành công lần đầu; thời gian từ tạo đơn đến bắt đầu soạn; chi phí phiếu bù đắp. Thời gian chu kỳ đo từ tạo đơn (sau Đặt hàng) — xem mục 5 và [research.md](../02-research/research.md) §4.3.

---

### B3. Đặt lịch và thực hiện dịch vụ Clinic / Spa

| Trường | Nội dung |
|--------|----------|
| **Tác nhân (*actors*)** | Khách; lễ tân; bác sĩ / kỹ thuật viên; thu ngân clinic; hệ thống đặt lịch |
| **Khách hàng của quy trình (*process customer*)** | Khách sử dụng dịch vụ |
| **Kết quả có thể (*outcomes*)** | (1) Liệu trình hoàn tất và thanh toán; (2) Dời lịch; (3) Hủy theo quy định; (4) Mua thêm sản phẩm → mở B1 hoặc B2 nếu phát sinh |

**Các bước (tham chiếu ngành + mô hình Clinic công bố):** đặt lịch → xác nhận khung giờ và chuyên môn → check-in và tư vấn → thực hiện liệu trình → thanh toán và hẹn lần sau nếu cần.

> Không mô tả chi tiết kỹ thuật y khoa khi chưa có tài liệu hoặc khảo sát thực địa.

---

### B4. Đổi trả sản phẩm và hoàn tiền

| Trường | Nội dung |
|--------|----------|
| **Tác nhân (*actors*)** | Khách; nhân viên cửa hàng / chăm sóc khách hàng; kho; kế toán / cổng hoàn tiền; quản lý (khi vượt thẩm quyền) |
| **Khách hàng của quy trình (*process customer*)** | Khách yêu cầu đổi hoặc trả |
| **Kết quả có thể (*outcomes*)** | (1) Đổi hàng xong; (2) Hoàn tiền xong theo cách đã thanh toán; (3) Từ chối có giải thích; (4) Quản lý duyệt rồi mới (1)(2)(3) |

**Nguồn:** [Đổi trả – hoàn tiền](https://hotro.hasaki.vn/doi-tra-hoan-tien.html) (30 ngày từ 01/06/2024) và chuẩn đổi trả ngành mỹ phẩm.

| Giai đoạn | Nội dung chính |
|-----------|----------------|
| 1. Tiếp nhận | Khách báo lý do và liên hệ; Thành phố Hồ Chí Minh ưu tiên đến cửa hàng; tỉnh có thể gửi bưu điện; đổi sản phẩm chính nên mang quà tặng kèm |
| 2. Thẩm định | Còn 30 ngày? Mua từ Hasaki? Thuộc loại trừ? Lỗi do người dùng → từ chối; lỗi nhà sản xuất / vận chuyển / cận hạn / soạn sai → cho đổi hoặc trả; đổi ý + đủ hình thức → đổi mới — **một lần thẩm định** theo bảng, không tách mỗi tiêu chí thành cổng trên sơ đồ |
| 3. Nhận và kiểm hàng | Tại cửa hàng thường gộp khi thẩm định; gửi bưu điện: nhận kiện rồi đối chiếu |
| 4. Xử lý kết quả | Đổi (cần còn hàng thay thế — *suy luận ngành*) hoặc hoàn: tiền mặt / chuyển khoản 3–5 ngày / cổng thanh toán 3–8 hoặc 15–90 ngày / phiếu quà → mã đơn sau; trả tại nhà: hoàn **sau** khi nhận được hàng |
| 5. Xử lý hàng trả | Đưa lại bán nếu đủ điều kiện; hàng đã mở / mất tem thường không bán lại *(suy luận ngành mỹ phẩm)* |

---

### B5. Chăm sóc khách hàng và khiếu nại

| Trường | Nội dung |
|--------|----------|
| **Tác nhân (*actors*)** | Khách; tổng đài / chăm sóc khách hàng; cửa hàng; clinic; kho; kế toán liên quan |
| **Khách hàng của quy trình (*process customer*)** | Khách cần hỗ trợ hoặc khiếu nại |
| **Kết quả có thể (*outcomes*)** | (1) Yêu cầu được đóng; (2) Chuyển sang B4 hoặc B2; (3) Chuyển cấp cao / bồi thường theo chính sách |

**Các bước:** tiếp nhận → phân loại → xử lý trong thẩm quyền hoặc chuyển bộ phận → phản hồi và đóng yêu cầu.

---

## 3. Phương pháp thực hiện (phần cốt lõi)

### 3.1. Bằng chứng (*evidence*)

| Loại | Trạng thái | Cách lấy |
|------|------------|----------|
| Chính sách / hướng dẫn công bố | Có | Trang hỗ trợ: đặt hàng, 2 giờ, giao hàng, đổi trả |
| Sơ đồ tổ chức | Tham chiếu khối chức năng | Từ nghiên cứu tổng quan; xác minh khi phỏng vấn |
| Ca soạn hàng 2 giờ | Chưa có nội bộ | Phỏng vấn quản lý cửa hàng / điều phối đơn |
| Thuật ngữ | Một phần | Bảng dưới |
| Biểu mẫu | Chưa có | Xin phiếu đổi trả, biên bản giao nhận nếu được |
| Quan sát thực tế | Khuyến nghị | Đặt thử đơn 2 giờ và đơn 48 giờ; tìm hiểu đổi trả tại cửa hàng |

| Thuật ngữ | Nghĩa |
|-----------|--------|
| NowFree | Giao nhanh khoảng 2 giờ theo khung giờ dự kiến |
| Tồn khả dụng để cam kết giao | Hàng hệ thống còn dám hứa giao tại một điểm |
| ĐTVC | Đối tác vận chuyển |
| COD | Thanh toán khi nhận hàng |
| Xác nhận đã giao | Bằng chứng giao thành công (ký nhận / trạng thái trên hệ thống) |
| Đối tượng theo dõi (*case*) | Thực thể gắn một lần chạy quy trình (*process instance*) (mã đơn, yêu cầu đổi trả…) |

### 3.2. Bộ câu hỏi phỏng vấn (đủ 10 + 10)

**Đối tượng gợi ý:** điều phối đơn; nhân viên soạn hàng; nhân viên giao / đối tác vận chuyển; nhân viên đổi trả; chăm sóc khách hàng; lễ tân Clinic.

#### Định tính (*qualitative*) — 10 câu (5 có cấu trúc + 5 không cấu trúc)

**Có cấu trúc:**

1. Khi đơn giao 2 giờ được tạo, bộ phận nào nhận thông báo trước: kho cửa hàng gần nhất / tổng kho / đối tác vận chuyển?  
2. Nếu lúc soạn mới hết hàng dù lúc đặt còn hiện 2 giờ, xử lý chuẩn là: hủy / đổi điểm lấy / gọi khách đổi sản phẩm / khác?  
3. Giao không thành lần 1: ai gọi khách và trong khoảng thời gian nào (&lt;2 giờ / trong ngày / ngày hôm sau)?  
4. Đổi trả tại cửa hàng: nhân viên tự quyết đến mức giá trị nào trước khi cần quản lý?  
5. Yêu cầu “giao 2 giờ trễ”: có danh mục kiểm tra điều kiện phiếu 100.000đ không, hay xử lý theo cảm tính?

**Không cấu trúc:**

6. Anh/chị mô tả một ca giao 2 giờ suýt trễ gần đây và cách xử lý.  
7. Điểm nào trong đổi trả khiến khách tranh cãi nhiều nhất?  
8. Soạn đơn 2 giờ và đơn 48 giờ tại cửa hàng khác nhau thế nào?  
9. Clinic và bán lẻ phối hợp ra sao khi khách vừa điều trị vừa muốn mua sản phẩm?  
10. Nếu chỉ được cải một việc để giảm khiếu nại giao hàng, anh/chị chọn việc gì? Vì sao?

#### Định lượng (*quantitative*) — 10 câu (5 có cấu trúc + 5 không cấu trúc)

**Có cấu trúc:**

1. Tỷ lệ đơn giao 2 giờ đúng giờ dự kiến tuần gần nhất: &lt;80% / 80–90% / 90–95% / &gt;95% / không đo?  
2. Thời gian soạn–đóng gói trung bình đơn 2 giờ: &lt;10 / 10–20 / 20–40 / &gt;40 phút?  
3. Tỷ lệ đơn cần giao từ lần 2 trở lên: &lt;5% / 5–10% / 10–20% / &gt;20%?  
4. Thời gian xử lý một yêu cầu đổi trả tại cửa hàng: &lt;15 / 15–30 / 30–60 / &gt;60 phút?  
5. Tỷ lệ yêu cầu đổi trả bị từ chối: &lt;10% / 10–25% / 25–40% / &gt;40%?

**Không cấu trúc (xin khoảng số):**

6. Một ngày cao điểm, cửa hàng xử lý khoảng bao nhiêu đơn online lấy hàng tại chỗ?  
7. Chi phí giao chặng cuối trung bình mỗi đơn 2 giờ và đơn thường khác nhau khoảng bao nhiêu?  
8. Thời gian hoàn tiền qua cổng thanh toán khách thường phản ánh thực tế bao lâu so với cam kết?  
9. Thời gian chờ tổng đài mục tiêu và thực tế?  
10. Tỷ lệ đơn hủy vì không liên lạc được khách (quy tắc 3 ngày) khoảng bao nhiêu mỗi tháng?

> Nếu chưa phỏng vấn được: báo cáo ghi rõ *ước lượng có chú thích* (mục 5) và kế hoạch thu thập.

---

## 4. Phân tích định tính (*qualitative process analysis*) — B2 và B4

**Nhắc lại ký hiệu:** VA = tăng giá trị cho khách (*value-adding*); BVA = cần cho doanh nghiệp (*business value-adding*); NVA = không tăng giá trị (*non-value-adding*). Lãng phí (*waste*): di chuyển thừa (Move), chờ/giữ (Hold), làm thừa (Overdo).

### 4.1. Quy trình B2

> Phân loại VA/BVA/NVA theo chuỗi hoạt động trên sơ đồ (kể cả bước cam kết trên màn hình đặt hàng). **Thời gian chu kỳ định lượng (mục 5) chỉ đo từ sau Đặt hàng** — không cộng thời gian xem / lựa hàng trên ứng dụng ([research.md](../02-research/research.md) §4.3).

#### Giá trị gia tăng

| # | Hoạt động | Giai đoạn | Loại | Khắc phục nếu cần |
|---|-----------|-----------|------|-------------------|
| 1 | Khách chọn địa chỉ, vận chuyển, thanh toán (trên màn hình trước khi đặt; chưa chắc có đơn) | 1 | VA | — |
| 2 | Hệ thống kiểm điều kiện 2 giờ, tồn, phí, giờ nhận dự kiến | 1 | BVA | Giảm tồn ảo; kiểm địa chỉ |
| 3 | Tạo mã đơn và thông báo (sau Đặt hàng) | 2 | BVA | — |
| 4 | Chờ / thử lại thanh toán trước | 2 | NVA (chờ) | Ví điện tử, thông báo lỗi rõ |
| 5 | Ưu tiên đưa đơn 2 giờ vào soạn | 2 | BVA | Hàng đợi ưu tiên |
| 6 | Soạn và đóng gói | 3 | VA | Quét mã; khung giờ soạn riêng |
| 7 | Chờ đơn vị giao nhận kiện | 3 | NVA (chờ) | Nhân viên giao sẵn giờ cao điểm |
| 8 | Giao và thu tiền khi nhận | 4 | VA | — |
| 9 | Gọi hẹn lại khi giao không thành | 5 | BVA | Kịch bản liên hệ chuẩn |
| 10 | Hủy sau 3 ngày + hoàn tiền | 5 | BVA | Xác minh số điện thoại lúc đặt |
| 11 | Cấp phiếu 100.000đ khi trễ đủ điều kiện | 5 | BVA | Ưu tiên giảm nguyên nhân trễ |

#### Lãng phí

| Loại | Hiện tượng | Khắc phục |
|------|------------|-----------|
| Di chuyển thừa | Chuyển điểm lấy vì tồn ảo | Chốt tồn chặt hơn; kiểm kê định kỳ tại điểm giao nhanh |
| Chờ | Chờ thanh toán, chờ shipper, chờ khách nghe máy | Giới hạn thời gian thanh toán; kênh liên hệ đa dạng |
| Làm thừa | Gọi lặp không kịch bản; đóng gói lại vì soạn sai | Danh mục kiểm tra soạn hàng; mẫu tin nhắn chăm sóc khách hàng |

#### Mô hình xương cá (*fishbone / Ishikawa*) — “Giao 2 giờ không đúng giờ dự kiến”

```text
                    Giao không đúng giờ cam kết
                              │
     Người          Phương pháp       Máy móc / hệ thống    Hàng hóa         Môi trường
       │                 │                  │                  │                │
 Thiếu người giao   Giờ cam kết lỏng   Ứng dụng chậm      Hết hàng tại điểm  Kẹt xe, mưa
 Soạn chậm giờ cao điểm  Không ưu tiên đơn 2 giờ  Quét mã lỗi   Đóng gói lại   Sự kiện bất khả kháng
 Khách không nghe máy  Sai vùng cam kết     Sai địa chỉ
```

### 4.2. Quy trình B4

> Khớp mô hình BPMN: **một** hoạt động thẩm định theo bảng chính sách; cổng XOR chỉ ở chỗ luồng khác nhau (kênh tiếp nhận, hồ sơ đủ/thiếu, đạt/từ chối, đổi/trả, còn hàng, hình thức hoàn). Tiêu chí 30 ngày / tem / loại trừ nằm **trong** thẩm định, không phải từng dòng VA riêng cho mỗi cổng.

#### Giá trị gia tăng

| # | Hoạt động | Giai đoạn | Loại | Khắc phục nếu cần |
|---|-----------|-----------|------|-------------------|
| 1 | Tiếp nhận yêu cầu và lý do | 1 | BVA | Mẫu thu thập đủ trường |
| 2 | Kiểm hồ sơ (chứng từ, quà kèm); yêu cầu bổ sung nếu thiếu | 1 | BVA / NVA nếu phải đi lại | Danh mục kiểm tra trước khi thẩm định |
| 3 | Thẩm định theo bảng 30 ngày *(một lần: hạn, nguồn mua, loại trừ, lỗi, hình thức)* | 2 | BVA | Bảng quyết định một trang |
| 4 | Khách giải thích lại nhiều lần / thiếu thông tin lúc đầu | 1 | NVA | Hỏi đủ một lần |
| 5 | Đối chiếu hàng khi nhận gửi bưu điện *(tại cửa hàng thường gộp trong thẩm định)* | 3 | VA | Ảnh, video chuẩn |
| 6 | Đổi hàng | 4 | VA | Đảm bảo còn hàng đổi |
| 7 | Chờ quản lý duyệt tranh chấp | 2 | NVA (chờ) | Rõ mức thẩm quyền |
| 8 | Hoàn tiền theo cách đã thanh toán | 4 | VA | Báo trước thời hạn hoàn |
| 9 | Xử lý hàng trả (bán lại / loại) | 5 | BVA | Quy định rõ hàng mỹ phẩm đã mở |
| 10 | Từ chối và giải thích | 2 | BVA | Đào tạo giao tiếp |

#### Lãng phí (*waste*) và xương cá (*fishbone*)

| Loại | Hiện tượng | Khắc phục |
|------|------------|-----------|
| Di chuyển thừa | Gửi bưu điện qua lại vì thiếu quà kèm / thiếu mã đơn | Danh mục kiểm tra trước khi gửi |
| Chờ | Chờ hoàn tiền thẻ quốc tế lâu → phát sinh khiếu nại; chờ quản lý duyệt case rõ chính sách | Thông báo thời hạn; bảng quyết định + mức thẩm quyền |
| Làm thừa | Tách / kiểm lại từng tiêu chí như nhiều cấp dù đã có bảng một trang | Một lần thẩm định + bảng quyết định |

```text
                 Khiếu nại / từ chối đổi trả
                           │
  Người        Chính sách / cách làm     Chứng cứ          Kênh
    │                  │                    │                │
 Nhân viên hiểu sai   Bảng 30 ngày phức tạp  Thiếu video mở hàng  Cửa hàng và gửi bưu điện lệch nhau
 Khách kỳ vọng đổi ý tự do  Loại trừ khuyến mãi / quà tặng  Mất hóa đơn   Bưu điện chậm
```

---

## 5. Phân tích định lượng (*quantitative process analysis*) — B2 và B4

> Chưa có số liệu nội bộ. Bảng dưới là **ước lượng có kiểm soát**. Đơn giá nhân sự giả định 80.000đ/giờ (khoảng 1.333đ/phút). Khi có phỏng vấn, thay bằng số đo.
>
> **Phương pháp đo (khớp [research.md](../02-research/research.md) §4.3 và giáo trình BPM):** *thời gian chu kỳ (cycle time)* = từ bắt đầu đến kết thúc một lần chạy quy trình; *thời gian xử lý (processing time)* = thời gian đang làm việc; *thời gian chờ (waiting time)* = chờ / hàng đợi. **Không** đo thời gian khách xem / lựa hàng trên ứng dụng (chưa mở lần chạy). Cột *Điển hình* dùng làm thời gian chu kỳ chính; thấp / cao = biên độ ước lượng, không phải phân phối xác suất.

### 5.1. Quy trình B2 (kịch bản giao 2 giờ + thanh toán trước)

Ranh giới: **bắt đầu** = tạo đơn sau Đặt hàng; với thanh toán trước, soạn bắt đầu sau thanh toán thành công. Các bước trên màn hình trước khi đặt (địa chỉ, chọn vận chuyển) **không** vào bảng.

| Giai đoạn / bước | Loại | Thấp nhất | Điển hình | Cao nhất (phút) |
|------------------|------|-----------|-----------|-----------------|
| Thanh toán trước (xác nhận cổng) | Xử lý | 1 | 3 | 15 |
| Chờ đưa vào soạn | Chờ | 0 | 5 | 20 |
| Soạn – đóng gói | Xử lý | 5 | 15 | 35 |
| Chờ bàn giao người giao | Chờ | 2 | 10 | 25 |
| Giao chặng cuối | Xử lý | 15 | 40 | 90 |
| **Tổng thời gian chu kỳ** (tạo đơn → nhận) | | **23** | **~73** | **~185** |

Ước lượng tách theo cột điển hình: thời gian xử lý ≈ 3 + 15 + 40 = **58 phút**; thời gian chờ ≈ 5 + 10 = **15 phút**; **hiệu suất thời gian chu kỳ** ≈ 58 / 73 ≈ **79%** (ước lượng — chờ cao điểm làm hiệu suất giảm).

Cam kết NowFree theo **giờ nhận dự kiến** (thường cửa sổ khoảng 2 giờ) → giá trị điển hình cần nằm trong cửa sổ đã hiện lúc đặt (thường dưới khoảng 120 phút từ lúc đặt trong khung giờ ban ngày).

| Chỉ số chất lượng | Định nghĩa | Mục tiêu gợi ý (chưa đo nội bộ) |
|-------------------|------------|----------------------------------|
| Đúng giờ cam kết | Tỷ lệ giao không muộn hơn giờ dự kiến lúc đặt | ≥ 95% |
| Giao thành công lần đầu | Tỷ lệ thành công ở lần giao thứ nhất | ≥ 90% |
| Đơn hoàn hảo | Đúng hàng, đủ số lượng, không hỏng | ≥ 98% |
| Tỷ lệ phát phiếu 100.000đ | Trên tổng đơn giao 2 giờ | Càng thấp càng tốt nếu đúng giờ cao |

| Chi phí biến đổi điển hình / đơn 2 giờ (không trễ) | Ước lượng |
|-----------------------------------------------------|-----------|
| Nhân sự soạn–đóng gói ~15 phút *(chỉ thời gian xử lý)* | ~20.000đ |
| Chăm sóc khách hàng phân bổ ~3 phút | ~4.000đ |
| Giao chặng cuối đô thị | 25.000–40.000đ |
| **Cộng** | **~50.000–65.000đ** |
| Nếu trễ đủ điều kiện | +100.000đ phiếu |

**Khắc phục gắn số:** giảm thời gian chờ bàn giao khoảng 10 phút → tăng khả năng đúng giờ → giảm nguy cơ mất 100.000đ/đơn.

### 5.2. Quy trình B4 (đổi tại cửa hàng)

**Thời gian chu kỳ** tại cửa hàng đo từ **tiếp nhận yêu cầu** đến ghi nhận xong (không gồm thời gian khách đi đường tới cửa hàng). Hoàn tiền qua cổng thanh toán đo bằng **ngày** theo chính sách (chuyển khoản 3–5; cổng thanh toán 3–8 hoặc 15–90 ngày làm việc).

**Giả định kịch bản điển hình:** hồ sơ đủ lần đầu (không vòng bổ sung); **một** lần thẩm định theo bảng (không cộng thời gian từng tiêu chí như nhiều cổng); không cần quản lý duyệt; đổi hàng tại chỗ (không đo ngày chờ bưu điện).

| Giai đoạn / bước | Loại | Thấp nhất | Điển hình | Cao nhất (phút) |
|------------------|------|-----------|-----------|-----------------|
| Tiếp nhận + kiểm hồ sơ | Xử lý | 3 | 7 | 15 |
| Thẩm định theo bảng chính sách | Xử lý | 5 | 12 | 25 |
| Quản lý duyệt (nếu có) | Chờ | 0 | 0 | 30 |
| Đổi hàng (kèm đối chiếu tem / tồn) | Xử lý | 3 | 8 | 20 |
| Ghi nhận xử lý hàng trả | Xử lý | 2 | 5 | 10 |
| **Tổng tại cửa hàng** | | **13** | **~32** | **~100** |

Điển hình (không duyệt quản lý): thời gian xử lý ≈ 7+12+8+5 = **32 phút**; thời gian chờ ≈ **0**; hiệu suất thời gian chu kỳ ≈ **~100%** trên nhánh thuận (ước lượng). Nếu có tranh chấp, cộng thêm phút chờ quản lý → tổng điển hình có duyệt ≈ **37 phút**, hiệu suất ≈ 32/37 ≈ **86%**.

| Chỉ số | Mục tiêu gợi ý (chưa đo nội bộ) |
|--------|----------------------------------|
| Xử lý xong trong một lần tiếp xúc | ≥ 85% |
| Quyết định đúng chính sách (kiểm mẫu) | ≥ 98% |
| Hoàn tiền đúng hạn công bố | ≥ 90% |

| Hạng mục chi phí | Ước lượng |
|------------------|-----------|
| Nhân sự điển hình đổi tại cửa hàng (nhánh thuận) | ~32 phút xử lý × 1.333 ≈ **43.000đ** |
| Gửi hàng từ tỉnh | 20.000–40.000đ / yêu cầu *(ngoài bảng phút tại quầy)* |
| Hàng không bán lại được | tùy trường hợp |

---

## 6. Nội dung đưa vào Word / slide

| Sản phẩm | Nội dung phần cốt lõi |
|----------|------------------------|
| Báo cáo Word | Kiến trúc (nhấn 5 quy trình cốt lõi); đủ bốn yếu tố B1–B5; hình BPMN B2 và B4; bảng định tính và định lượng; tài liệu tham khảo |
| Slide | Nên chọn **B2** (giao 2 giờ) trình bày sâu: sơ đồ + vài điểm giá trị gia tăng / lãng phí / chỉ số |

---

## 7. Danh mục kiểm tra

- [x] Có 5 quy trình cốt lõi, đủ bốn yếu tố  
- [x] Có vị trí trong kiến trúc  
- [x] Chọn B2 và B4; có file phân tích và hướng dẫn vẽ  
- [x] Bằng chứng + 10 câu định tính + 10 câu định lượng  
- [x] Phân tích định tính và định lượng B2, B4  
- [ ] Vẽ file `.bpmn` trên phần mềm  
- [ ] Thay số ước lượng bằng số phỏng vấn khi có  

---

## 8. Tài liệu tham khảo

1. https://hotro.hasaki.vn/huong-dan-dat-hang.html  
2. https://hotro.hasaki.vn/van-chuyen-2h.html  
3. https://hotro.hasaki.vn/quy-trinh-giao-hang.html  
4. https://hotro.hasaki.vn/doi-tra-hoan-tien.html  
5. https://hasaki.vn/gioi-thieu-hasaki-clinic-spa.html  
6. [Nghiên cứu tổng quan](../02-research/research.md)  
7. [Yêu cầu đồ án](../01-requirements/yeu_cau_do_an.md)  
8. [Phân tích nghiệp vụ B2 và B4](./ba_model_b2_b4.md)  
9. [Hướng dẫn vẽ BPMN](./core_bpmn.md)  
