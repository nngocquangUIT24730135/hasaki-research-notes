# Nhận xét phần quy trình cốt lõi của Quang — Giao hàng 2H (BPMN)

**Nguồn:** `hasaki-van-chuyen-2h-manual-layouted-v2.bpmn`  
**Bối cảnh nhóm:** Quang và Phúc **cố ý tách** thành hai quy trình nối tiếp — Phúc: tiếp nhận / xác nhận đơn online (**P1**); Quang: thực hiện giao hàng NowFree 2H (**Q1**).  
**Đối chiếu:** `02-research/research.md` (§4.3 B2, §5 NowFree), `03-core/core_bpmn.md`, `01_feedback_phuc.md`, slides FBPM Ch.2–3 (ranh giới, pool/lane), Ch.6–7 nếu sau này viết phân tích.  
**File liên quan:** nhận xét Phúc — `../phuc/01_feedback_phuc.md`.

## Quyết định hướng nhóm (P1 ↔ Q1) — đọc trước

Câu hỏi: Quang **bổ sung giao thường 48H** vào quy trình đang tách, hay **Phúc + Quang gộp thành một quy trình**?

**Đã chốt trong nguồn chuẩn nhóm** ([research.md](../../02-research/research.md) §4.3): **gộp thành một quy trình B2** (*Order-to-Delivery*) — từ Đặt hàng đến giao/hủy, có **cả nhánh NowFree 2 giờ và giao thường**. Không liệt kê “mua hàng online” và “giao 2H” thành hai quy trình cốt lõi độc lập trên kiến trúc.

**Lý do nghiệp vụ (tóm tắt):** cùng một mã đơn và cùng cam kết với khách; 2H/thường chỉ là lựa chọn hình thức giao; giá trị kết thúc khi nhận hàng (hoặc hủy có kiểm soát); sơ đồ theo vai trò nghiệp vụ, không theo tầng kỹ thuật.

| Việc cần làm | Chi tiết |
|--------------|----------|
| Sản phẩm nộp | **Một** hồ sơ + **một** sơ đồ B2 (có cổng tách 2H vs thường) |
| Phúc | Đóng góp quy tắc đặt hàng / thanh toán (nghiệp vụ); bỏ browse khỏi chu kỳ; bỏ lane Frontend/Backend |
| Quang | Đóng góp nhánh soạn–giao 2H và nối nhánh giao thường / đối tác; không giữ Q1 như core riêng |
| Cặp core điểm | B2 gộp + B4 đổi trả |
| Tài liệu NowFree | `nowfree_2h_noi_dung.md` dùng như nội dung **nhánh 2H** trong B2 |

**Nếu tạm giữ hai hình để chia việc:** chỉ là phân đoạn nội bộ của B2, cùng mã đơn — kiến trúc và báo cáo vẫn ghi **một** B2. Chi tiết đánh giá BPMN hiện tại ở các mục dưới.

### Mã dùng trong file này

| Mã | Ý nghĩa |
|----|---------|
| **Q1** | Quy trình trên BPMN của Quang: *Hasaki — Quy trình giao hàng 2H* |
| **P1** | Quy trình Phúc: *Mua hàng trực tuyến* (checkout → xác nhận OMS) |
| **B2** | Tham chiếu research: *Order-to-Delivery* (Đặt hàng → giao / hủy) |

---

## 1. Tóm tắt nhanh

BPMN của Quang **mạnh về nghiệp vụ vận hành 2H**: pool Khách + Hasaki, lane theo vai trò (Hệ thống / Nhân viên cửa hàng / Shipper), trigger bằng *message* “Đơn hàng 2H được đặt”, có đủ nhánh hết tồn thực tế, gọi xác nhận lịch, soạn–bàn giao–giao, hẹn lại trong 3 ngày, hủy–hoàn, và phiếu 100K khi trễ đủ điều kiện. So với P1 của Phúc, Q1 **ít bị lạm dụng technical** hơn rõ rệt.

Điểm cần chốt (nếu **chưa** gộp B2): **giao diện nối P1 → Q1**, và Q1 chỉ là **phân đoạn fulfillment nhánh NowFree** của B2. **Hướng khuyến nghị:** gộp P1+Q1 thành một B2 có cả 2H và 48H — xem mục **Quyết định hướng nhóm** ở đầu file. Nếu tạm giữ tách, phải mô tả rõ trong báo cáo để không bị hiểu là hai SoT mâu thuẫn với B2 gộp.

| Hạng mục | Hiện trạng Q1 | Đánh giá ngắn |
|----------|---------------|---------------|
| Nhóm / bản chất | Cốt lõi — đoạn giao nhanh sau khi đặt | Đúng; là phần sau của B2 |
| Ranh giới mở | Message start: đơn 2H được đặt | Tốt cho quy trình thứ hai |
| Ranh giới đóng | Giao đúng hạn / trễ+phiếu / trễ miễn trừ / hủy hết hàng / hủy+hoàn | Đủ outcome nghiệp vụ |
| Pool / lane | Khách + Hasaki; 3 lane vai trò | Đúng hướng FBPM / `core_bpmn` |
| XOR quyết định (Hasaki) | ~6 cổng có nhãn câu hỏi + 2 cổng gộp | Có ý nghĩa; gần ngưỡng rubik |
| Góc technical vs nghiệp vụ | Tên việc = phân công CH, kiểm tồn, soạn, giao, phiếu… | **Nghiệp vụ tốt** — giữ |
| Tài liệu kèm (mô tả 4 yếu tố, phân tích) | Chưa thấy trong thư mục `quang/` | Cần bổ sung nếu Q1 là 1 trong 2 core nộp điểm |
| Khớp P1 | P1 dừng ở đẩy kho; Q1 bắt đầu khi đơn 2H đặt | Cần bảng *handoff* thống nhất |

---

## 2. Quang đã làm được gì

| Việc | Nhận xét |
|------|----------|
| Collaboration: 2 pool + message flow | Đúng bài BPMN nâng cao (FBPM Ch.3): khách không nằm trong cùng lane “Frontend” |
| Lane theo vai trò vận hành | Hệ thống / NV cửa hàng–kho / Shipper — khớp gợi ý `core_bpmn` |
| Trigger có chú thích | “App đã cho phép chọn 2H; phí & ETA gốc đã chốt lúc đặt” — đúng hướng ranh giới với bước cam kết trên màn hình |
| Nhánh hết tồn thực tế lúc soạn/kiểm tại CH | Suy luận chuẩn ngành hợp lý; khác tồn “ảo” lúc browse |
| Gọi xác nhận địa chỉ/giờ + miễn trừ voucher nếu khách hẹn muộn | Gần chính sách NowFree / thực tế chuỗi; có ghi chú trên hình |
| Vòng giao thất bại → hoàn hàng → hẹn lại 3 ngày → hủy–hoàn | Khớp chính sách hủy không liên lạc / hoàn trong 30 ngày (mức mô hình) |
| Phiếu 100K khi trễ: **một** cổng “Đủ điều kiện?” thay vì xẻ từng tiêu chí thành nhiều XOR | Đúng nguyên tắc `core_bpmn` (activity/gateway + điều kiện, không checklist-gateway) |
| Customer dùng *event-based gateway* chờ tin nhắn | Mô hình hóa phía khách gọn, không vẽ UI |

---

## 3. Tách P1 + Q1 có ổn không? (góc kiến trúc & cùng ngành)

**Có thể chấp nhận** nếu nhóm trình bày đúng:

```text
P1  Tiếp nhận & xác nhận đơn online     →  (sự kiện bàn giao)
Q1  Thực hiện giao NowFree 2H           →  giao / hủy
```

Đây là cách **phân rã B2** thành hai quy trình tuần tự (end-to-end vẫn là Order-to-Delivery), phổ biến khi muốn:

- P1 tập trung quy tắc checkout / thanh toán / chống gian lận;  
- Q1 tập trung SLA 2H, cửa hàng, shipper, đền bù.

| Cách hiểu | Đúng / rủi ro |
|-----------|----------------|
| P1 + Q1 = hai mắt xích của **một** chuỗi giá trị B2 | Đúng — nên vẽ thêm sơ đồ kiến trúc nhỏ nối hai quy trình |
| P1 và Q1 = hai “core” độc lập không liên quan | Sai — dễ trùng / hổng (thanh toán ở đâu? đơn 48H ai làm?) |
| Q1 thay cho toàn bộ B2 | Thiếu — chưa phủ giao thường / 3PL |

**Cùng ngành (bán lẻ đẹp / dark store / giao nhanh):** quy trình fulfillment 2H sau khi đơn *committed* là chuẩn; hiếm khi gộp chung “duyệt catalog” vào cùng instance giao hàng — nên hướng tách của nhóm **hợp lý hơn** P1 đang bắt đầu từ tìm kiếm (xem feedback Phúc).

---

## 4. Ranh giới Q1 và bàn giao từ P1

### 4.1. Hồ sơ ranh giới đề xuất cho Q1

| Thuộc tính | Trên BPMN hiện tại | Nên khóa trong báo cáo |
|------------|--------------------|------------------------|
| *Case* | (ngầm) đơn 2H | Một **mã đơn** đã chọn NowFree |
| *Trigger* | Message: Đơn hàng 2H được đặt | Sự kiện từ P1: **đơn đã xác nhận / sẵn sàng fulfill 2H** (thanh toán COD chấp nhận hoặc trả trước thành công — do P1 bảo đảm) |
| *Outcomes* | Giao đúng hạn; giao trễ + phiếu; giao trễ miễn trừ; hủy hết hàng; hủy + hoàn | Giữ; ghi rõ COD chưa thu thì “hoàn tiền” chỉ áp đơn trả trước |
| Trong phạm vi | Phân công CH → ETA → kiểm tồn thực tế → (gọi xác nhận) → soạn–giao → ngoại lệ → phiếu 100K | Giữ |
| Ngoài phạm vi | Duyệt app; chọn COD/VNPAY; anti-fraud; đơn 48H/3PL; đổi trả sau nhận (B4) | Nêu rõ thuộc P1 hoặc quy trình khác |

### 4.2. Bảng handoff P1 → Q1 (bắt buộc viết chung)

| Trường | P1 (Phúc) phải chốt trước khi gửi | Q1 (Quang) nhận và giả định đúng |
|--------|-----------------------------------|----------------------------------|
| Hình thức giao | Khách chọn **NowFree 2H**, địa chỉ thuộc vùng | Không hỏi lại “có phải 2H?” — chỉ fulfill 2H |
| Thanh toán | COD được phép hoặc trả trước **thành công** | Không vẽ lại cổng VNPAY; hủy–hoàn chỉ khi đã thu tiền |
| Cam kết giờ / phí | ETA gốc & phí đã chốt trên màn đặt | Task “Gắn ETA đã chốt” = **ghi nhận / đồng bộ**, không tự ý đổi cam kết |
| Tồn | Có thể đã kiểm tồn mềm lúc đặt | Q1 kiểm **tồn thực tế tại CH** — được phép lệch → hủy |
| Sự kiện mở Q1 | Kết thúc P1 kiểu: *Đơn xác nhận — chờ fulfill 2H* | Start message khớp đúng tên sự kiện đó |

**Lệch cần sửa trên sơ đồ khách hàng:** Start khách = “Muốn nhận hàng nhanh trong ngày” + task “Đặt đơn 2H” đang **lấn sang P1**. Phía khách của Q1 nên bắt đầu từ *đã đặt / chờ xác nhận giao* (hoặc chỉ các catch message), để hai quy trình không cùng vẽ bước Đặt hàng.

---

## 5. Technical vs nghiệp vụ

| Khía cạnh | Đánh giá |
|-----------|----------|
| So với P1 | Q1 **nghiệp vụ rõ** hơn nhiều (soạn, giao, hẹn, phiếu) |
| Tên task | Phần lớn ổn; “Gắn ETA…” có thể đổi thành “Ghi nhận giờ giao đã cam kết” cho dễ hiểu |
| Điều kiện phiếu 100K trên sequence flow | Nhiều cờ kỹ thuật trong expression — **giữ một cổng**, chuyển chi tiết vào **bảng quyết định / chú thích** (đã có hướng đúng) |
| Shipper nội bộ | Phù hợp giả định NowFree; ghi chú nếu thực tế có đối tác ngoài thì pool riêng |
| Không vẽ Frontend/API/OMS lock | Tốt — đúng tinh thần `core_bpmn` |

**Việc gọi xác nhận trước khi soạn:** thường là *suy luận vận hành* (không phải mọi đơn 2H đều công bố bước này trên trang hỗ trợ). Giữ được nếu gắn nhãn suy luận ngành — đừng viết như chính sách bắt buộc đã quan sát 100%.

---

## 6. Cổng điều kiện & chất lượng BPMN

| Loại | Số lượng (ước lượng) | Ghi chú |
|------|----------------------|---------|
| XOR quyết định phía Hasaki | 6 (đủ tồn; kết quả xác nhận lịch; giao OK?; giao lại?; đúng hạn?; đủ điều kiện phiếu?) | Mỗi cái đổi nhánh xử lý — đạt tiêu chí “có nghĩa” |
| XOR gộp (join) | 2 | Nên để trống tên hoặc ghi “Gộp sau xác nhận lịch” / “Gộp trước giao” cho dễ đọc |
| Event-based phía khách | 3 | Không tính như XOR nghiệp vụ rubik; vẫn đúng collaboration |
| XOR phía khách (có phiếu?) | 1 | Phản ánh kết quả từ Hasaki — ổn |

Rubik môn học: >5 XOR ≈ 0,75; >7 ≈ 1. Q1 standalone ~6 quyết định — **ổn**. Nếu ghép P1+Q1 trên báo cáo, **không cộng cổng hai sơ đồ** như một hình; mỗi sơ đồ tự đếm.

**Thiếu so với B2 đầy đủ trong `core_bpmn` (chấp nhận nếu chỉ làm nhánh 2H):** cổng chọn 2H/48H, COD vs trả trước, 3PL — thuộc P1 hoặc biến thể đơn thường. Nên một câu trong báo cáo: *Q1 chỉ phủ đơn NowFree.*

---

## 7. Việc còn thiếu ngoài file BPMN

Nếu Q1 là một trong **hai quy trình cốt lõi** nộp điểm mô hình hóa / phân tích:

| Hạng mục | Trạng thái | Cần làm |
|----------|------------|---------|
| Bốn yếu tố (tác nhân, mô tả, khách hàng quy trình, outcomes) | Chưa có file văn bản trong `quang/` | Viết 1–2 trang hồ sơ Q1 |
| Phân tích định tính / định lượng | Chưa thấy | Chu kỳ đo từ **start Q1** (đơn 2H sẵn sàng) → giao/hủy — đơn vị phút/giờ theo SLA 2H, **không** lấy thời gian duyệt app của P1 |
| Phỏng vấn | Chưa thấy | Hỏi NV cửa hàng / shipper / CSKH về tồn thực tế, gọi xác nhận, tỷ lệ giao trễ–phiếu 100K |
| Đồng bộ kiến trúc nhóm | P1 + Q1 + research B2 | Một hình: B2 = P1 rồi Q1 (nhánh 2H); nhánh 48H ghi “ngoài phạm vi Q1” |

---

## 8. Ưu tiên cải thiện

1. **Viết bảng handoff P1 → Q1** (mục 4.2) và thống nhất tên sự kiện trên cả hai tài liệu.  
2. **Thu gọn pool khách** của Q1: bỏ / chuyển bước “Đặt đơn” về P1.  
3. **Ghi phạm vi:** chỉ NowFree; ngoài = 48H, đổi trả, checkout.  
4. **Bổ sung hồ sơ quy trình + phân tích** nếu Q1 tính điểm core.  
5. Đổi nhãn join / một số task cho dễ thuyết trình; chuyển điều kiện phiếu 100K vào bảng quyết định ngắn.

---

## 9. Kết luận

Q1 của Quang là **mảnh fulfillment 2H chắc tay**, đúng tinh thần nghiệp vụ Hasaki/cùng ngành và **bổ sung đúng chỗ P1 đang cắt sớm**. Tách hai quy trình kế tiếp **ổn** nếu nhóm coi đó là phân rã B2 và khóa sạch *trigger/handoff*. Việc cần làm ngay không phải “vẽ thêm technical”, mà là **nối miệng với Phúc**, chỉnh ranh giới phía khách, và viết đủ phần chữ (hồ sơ + phân tích) đi kèm BPMN.
