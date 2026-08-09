# Nhận xét phần quy trình cốt lõi của Phúc — Mua hàng online

**Nguồn:** `Quy Trình Mua Hàng Online - Hasaki.md`  
**Đối chiếu:** `01-requirements/yeu_cau_do_an.md`, `02-research/research.md` (đặc biệt §4.3 — B2), `03-core/core_bpmn.md`, slides FBPM Ch.2 (nhận diện / ranh giới), Ch.3 (mô hình hóa), Ch.6 (định tính), Ch.7 (định lượng).  
**Phạm vi nhận xét:** quy trình cốt lõi mà Phúc đang làm (mua hàng / đơn online) — ranh giới, mức nghiệp vụ vs kỹ thuật, và sự khớp thực tế Hasaki / cùng ngành.

### Mã dùng trong file này

| Mã | Ý nghĩa |
|----|---------|
| **P1** | Quy trình Phúc đang mô tả: *Mua hàng trực tuyến (Online Purchasing Process)* |
| **B2** | Quy trình tham chiếu trong `research.md`: *Xử lý đơn hàng online và giao hàng (Order-to-Delivery)* |

---

## 1. Tóm tắt nhanh

Phúc đã làm **đủ khung đồ án** cho một quy trình cốt lõi: xếp đúng nhóm core, đủ bốn yếu tố (tác nhân, khách hàng quy trình, kết quả, mô tả), có nguồn trang hỗ trợ Hasaki, có giả định rõ, có gợi ý lane / activity / gateway, có phỏng vấn, và đã viết phân tích định tính + định lượng + kiến nghị. Đây là phần mạnh hơn nhiều bài chỉ dừng ở mô tả.

**Bối cảnh nhóm:** Phúc và Quang **cố ý tách** hai quy trình kế tiếp — P1 (mua / xác nhận đơn) rồi Q1 (giao NowFree 2H, file BPMN của Quang). Cách tách này **hợp lý về vận hành** nếu P1 kết thúc bằng sự kiện *đơn xác nhận — sẵn sàng fulfill 2H* và Q1 chỉ làm đoạn giao. Khi đó feedback “P1 kết thúc sớm” không có nghĩa bắt buộc gộp mọi thứ vào một sơ đồ, mà là: **(1)** đừng bắt đầu P1 từ duyệt/giỏ, **(2)** phải có bảng bàn giao rõ với Q1, **(3)** trên kiến trúc nhóm vẫn gọi chuỗi đầy đủ là B2 (*Order-to-Delivery*). Chi tiết Q1: xem `../quang/01_feedback_quang.md`.

Điểm cần sửa lớn nhất phía P1: **ranh giới** đang **bắt đầu sớm** (duyệt web / giỏ hàng) so với trigger chuẩn “Đặt hàng”; nội dung đang **lạm dụng góc kỹ thuật / hệ thống** (Frontend–Backend, Inventory Lock, Anti-Fraud, API, Deep-Link…) hơn góc **nghiệp vụ**. Phần “kết thúc ở OMS / đẩy kho” **chấp nhận được trong mô hình tách P1→Q1**, miễn là handoff khớp BPMN Quang.

| Hạng mục | Hiện trạng P1 | Đánh giá ngắn |
|----------|---------------|---------------|
| Nhóm quy trình | Core — đúng | Giữ |
| Tên / phạm vi so với B2 | “Mua hàng online” ≈ duyệt → xác nhận đơn | Thiếu đoạn soạn–giao **trên cùng sơ đồ** — chấp nhận nếu bàn giao sang **Q1** (Quang); vẫn phải bỏ đoạn duyệt/giỏ khỏi instance |
| Bốn yếu tố rubik | Có đủ | Tốt |
| Bằng chứng Hasaki | Có link trang hỗ trợ | Tốt; cần tách rõ giả định |
| Mô hình BPMN (gợi ý) | 4 lane, 13 activity, 6 XOR | Lane theo tầng IT — cần chỉnh |
| Phân tích định tính | VA/BVA/NVA, lãng phí, xương cá | Có; giải pháp đang nghiêng tech |
| Phân tích định lượng | Thời gian / chất lượng / chi phí | Có khung; **chu kỳ đang gồm thời gian xem hàng** — lệch lý thuyết + research |

---

## 2. Phúc đã làm được gì

| Việc | Nhận xét |
|------|----------|
| Xác định P1 là quy trình cốt lõi | Đúng hướng: tạo giá trị / doanh thu trực tiếp từ khách |
| Đủ tác nhân, khách hàng quy trình, kết quả, mô tả bằng lời | Khớp yêu cầu liệt kê quy trình |
| Nêu chính sách công bố Hasaki (đặt hàng, VNPAY, NowFree, hạn mức, chống thương lái…) | Có nền bằng chứng; phần giả định OMS / anti-fraud đã ghi chú — đúng phương pháp |
| Gợi ý cổng XOR theo quy tắc nghiệp vụ (>5 triệu, COD/trả trước, vùng 2H, tồn, gian lận) | Các câu hỏi cổng **có tính nghiệp vụ** — giữ được |
| Phân tích VA/BVA/NVA + lãng phí + Fishbone | Đúng hướng FBPM Ch.6 |
| Có bảng thời gian / KPI / chi phí và kiến nghị | Có khung FBPM Ch.7 + cải tiến |

---

## 3. Tên chuẩn và vị trí trong kiến trúc (Hasaki / cùng ngành)

| Trong bài Phúc | Trong thực tế / cùng ngành | Trong `research.md` |
|----------------|----------------------------|---------------------|
| Online Purchasing Process / Mua hàng trực tuyến | Thường gọi *Order Capture*, *Checkout*, hoặc đoạn đầu của *Order-to-Cash* / *Order-to-Delivery* | **Một phần** của **B2**, không phải toàn bộ B2 |
| Kết thúc khi OMS xác nhận + đẩy kho | Chuỗi bán lẻ TMĐT mỹ phẩm thường kéo đến **giao thành công / hủy có kiểm soát** | B2 kết thúc: giao thành công hoặc hủy (+ hoàn nếu cần) |

**Gợi ý đặt tên nếu giữ phạm vi hiện tại:** *Tiếp nhận và xác nhận đơn hàng online* (Order Capture / Order Confirmation).  
**Gợi ý nếu muốn khớp B2 và cam kết 2 giờ Hasaki:** *Xử lý đơn hàng online và giao hàng* (*Order-to-Delivery*) — bổ sung soạn–đóng gói–bàn giao–giao–ngoại lệ giao.

**Lệch nhỏ khác:** “Khách hàng của quy trình” đang gồm cả *đặt lịch dịch vụ* — đó thuộc **B3 (Clinic)**, không nên nhét vào P1/B2.

---

## 4. Ranh giới quy trình (*process boundary*) — trọng tâm cần sửa

Theo checklist slides FBPM Ch.2 (có *case* quan sát được; phạm vi không quá lớn / không quá nhỏ) và `research.md` §4.3:

| Câu hỏi ranh giới | P1 hiện tại | Nên chỉnh theo B2 / lý thuyết |
|-------------------|-------------|-------------------------------|
| Đối tượng theo dõi (*case*) | Chưa nêu rõ mã đơn | **Một mã đơn hàng** |
| Sự kiện mở (*trigger*) | Khách **truy cập** web/app, tìm kiếm, thêm giỏ | Khách bấm **Đặt hàng** (đã có quyết định mua; hệ thống tạo mã đơn). Duyệt / giỏ bỏ dở = **chưa** có lần chạy |
| Kết thúc | Đơn COD/trả trước hợp lệ → đẩy sang kho; hoặc hủy (thanh toán lỗi, anti-fraud, hết tồn, khách hủy qua tổng đài) | Thêm (nếu làm B2 đầy đủ): **giao thành công** / hủy sau giao thất bại có kiểm soát; đổi trả sau nhận = **B4** (ngoài) |
| Trong phạm vi | Duyệt → giỏ → checkout → VNPAY → OMS → khóa tồn → SMS → đẩy kho | Từ tạo đơn: thanh toán (hoặc COD), xác nhận, soạn–đóng gói–giao, ngoại lệ giao / hủy |
| Ngoài phạm vi | (Chưa tách rõ) | Xem hàng / so sánh / giỏ bỏ dở; mở cửa hàng (A1); tồn chiến lược (A3); clinic (B3); đổi trả (B4) |

### Vì sao “bắt đầu từ tìm kiếm” là vấn đề

- Khách có thể xem app Hasaki rất lâu mà **không đặt** → không có mã đơn, không soạn, không áp dụng cam kết giờ nhận.  
- FBPM Ch.7: thời gian chu kỳ (*cycle time*) đo trên **một lần chạy quy trình** (từ bắt đầu đến kết thúc instance).  
- `research.md`: **không** cộng thời gian xem / lựa hàng vào chu kỳ B2.  
→ Bảng định lượng P1 đang lấy 120–180 giây “tìm kiếm–thêm giỏ” vào tổng 3,5–5,5 phút là **đo trải nghiệm checkout**, không phải chu kỳ nghiệp vụ đơn hàng.

### Vì sao “dừng khi đẩy sang kho” là vấn đề (nếu P1 = quy trình cốt lõi chính của Hasaki)

- Giá trị khách cảm nhận và SLA NowFree nằm ở **giao hàng**, không chỉ ở email “đặt thành công”.  
- Lane “Kho & Vận chuyển” gần như chỉ là **điểm kết thúc / bàn giao**, chưa có activity soạn–giao–hẹn lại.  
- Cùng ngành (bán lẻ đẹp / TMĐT): mô hình *Order-to-Delivery* mới phản ánh xương sống vận hành đa kênh.

**Hai hướng chọn (chọn một, đừng lẫn):**

1. **Thu hẹp có chủ đích + bàn giao Q1 (đúng ý nhóm Phúc–Quang):** P1 = từ **Đặt hàng** → xác nhận OMS; đổi tên cho khớp; định lượng chỉ sau Đặt hàng; fulfillment NowFree = **Q1** của Quang — bắt buộc có bảng handoff chung.  
2. **Mở rộng P1 thành B2 một sơ đồ:** thêm soạn–gói–giao — khi đó không cần Q1 trùng phạm vi.

---

## 5. Có đang lạm dụng góc kỹ thuật hơn nghiệp vụ?

**Có — khá rõ**, dù phần cổng XOR và một số quy tắc (>5 triệu, NowFree, chống thương lái) vẫn mang tính nghiệp vụ tốt.

| Biểu hiện trong bài | Góc kỹ thuật | Góc nghiệp vụ môn BPM mong đợi |
|---------------------|--------------|--------------------------------|
| Lane: Frontend / Backend OMS+VNPAY / Fulfillment | Tầng phần mềm | Vai trò / bên tham gia: Khách; Hệ thống Hasaki; Cổng thanh toán (**bể bơi riêng**); Kho/cửa hàng; Đối tác giao hàng |
| Activity: khóa tồn tạm, quét anti-fraud, deep-link, cache trình duyệt | Cơ chế IT | Việc nghiệp vụ: xác nhận đơn, kiểm tra đủ điều kiện bán, thông báo khách, soạn hàng, giao hàng |
| Phỏng vấn: real-time vs batch, tiêu chí thuật toán fraud, công suất Flash Sale, OTP | Hạ tầng / thuật toán | SLA xác nhận đơn, tỷ lệ giao đúng hẹn, tỷ lệ hủy sau đặt, thời gian xử lý ngoại lệ, phối hợp kho–shipper |
| Lãng phí → giải pháp ZNS, Local Storage, Auto-complete, Deep-Link | Backlog sản phẩm số | Đổi quy tắc / bước / bàn giao (ví dụ: cho phép hủy trên app trong cửa sổ ngắn — Phúc có ý self-service: **giữ**, đây mới là cải tiến quy trình) |
| Chi phí / đơn: cloud, phí cổng, SMS, bảo trì OMS | Chi phí IT đơn vị | Chi phí / thời gian theo bước nghiệp vụ và chờ (FBPM Ch.7) |
| `core_bpmn.md` | — | *Không vẽ cơ sở dữ liệu hay giao diện lập trình* |

**Slides FBPM Ch.3:** lane dùng để phân **nguồn lực / người tham gia** trong pool; hệ thống phần mềm có thể là một lane, nhưng **không** biến sơ đồ thành kiến trúc Frontend–Backend. Đối tác ngoài (VNPAY, hãng vận chuyển) nên là **pool** + luồng tin nhắn, không gộp chung “Backend” với OMS nội bộ.

**Mức chấp nhận giả định kỹ thuật:** Anti-fraud, khóa tồn, OMS — được phép nếu gắn nhãn *suy luận chuẩn ngành* (Phúc đã có đoạn giả định). Không nên để chúng **chiếm đa số** activity / câu hỏi / kiến nghị.

---

## 6. Đối chiếu phân tích định tính / định lượng với slides

### Định tính (FBPM Ch.6)

| Điểm | Nhận xét |
|------|----------|
| VA / BVA / NVA | Có bảng — đúng hướng. Một số bước “thanh toán lại khi lỗi” = NVA là hợp lý. |
| Lãng phí | Có Hold / Overdo; thêm Defect, Motion — ổn. Rubik môn học thường nhấn Move / Hold / Overdo. |
| Giải pháp cải tiến | Đang nghiêng tech; nên thêm 1–2 cải tiến **luồng nghiệp vụ** (cửa sổ hủy/sửa trên app; thông báo khi hủy anti-fraud; tách rõ bàn giao kho–giao). |
| Fishbone | Phong phú; một phần nguyên nhân là UX/IT — giữ nhưng gắn với **kết quả nghiệp vụ** (đơn hủy, giao trễ), không chỉ “OTP chậm”. |

### Định lượng (FBPM Ch.7 + research §4.3)

| Điểm | Nhận xét |
|------|----------|
| Chu kỳ đang gồm tìm kiếm 120–180s | **Lệch** — bỏ khỏi chu kỳ instance; chỉ đo từ Đặt hàng (hoặc từ thanh toán thành công → sẵn sàng soạn) |
| Tổng 3,5–5,5 phút | Là thời gian checkout, **không** phải chu kỳ Order-to-Delivery (thường tính bằng giờ với đơn 2H / 48H) |
| KPI Cart Conversion, công suất Flash Sale | Chỉ số sản phẩm / marketing — bổ trợ được, nhưng KPI quy trình B2 nên nhấn: tỷ lệ giao đúng hẹn, tỷ lệ hủy sau xác nhận, thời gian xác nhận đơn, tỷ lệ hết hàng lúc soạn… |
| Số liệu % rất cụ thể (78%, 91,5%…) | Cần ghi rõ **giả định / ước lượng**; tránh đọc như số nội bộ Hasaki đã đo |

---

## 7. Chi tiết mô hình hóa BPMN cần chỉnh

| Vấn đề | Chi tiết trong bài | Hướng sửa |
|--------|--------------------|-----------|
| Lane theo tầng IT | Frontend / Backend gộp VNPAY+OMS | Tách pool VNPAY; lane nội bộ theo vai trò nghiệp vụ |
| Fulfillment gần như trống | Chỉ “đẩy sang kho” | Nếu B2: thêm activity soạn–gói–giao; nếu chỉ Order Capture: bỏ lane này hoặc vẽ thành sự kiện kết thúc / liên kết quy trình sau |
| Đánh số activity | Mục 9 và 10 bị trùng / nhảy | Rà lại danh sách 13 bước |
| 6 XOR | Đủ cho điểm gateway trung bình–khá | Nếu mở B2 đầy đủ, sẽ cần thêm cổng giao thành / thất bại, hẹn lại… (xem `core_bpmn.md`) |
| Đổi trả trong tài liệu tham khảo | Có link đổi trả + KPI hoàn tiền | Đúng là nguồn liên quan, nhưng **không** thuộc phạm vi P1 — ghi ngoài phạm vi để khỏi lẫn B4 |

---

## 8. Việc cần cải thiện (theo thứ tự)

### Ưu tiên 1 — Khóa ranh giới P1

Viết một bảng 5 dòng: *case / trigger / outcomes / process customer / trong–ngoài phạm vi*.  
Chọn hướng **thu hẹp (Order Capture)** hoặc **mở rộng (B2 đầy đủ)** và đổi tên cho khớp.

### Ưu tiên 2 — Giảm mật độ kỹ thuật trên sơ đồ và phỏng vấn

Đổi lane sang nghiệp vụ; đưa VNPAY / 3PL ra pool ngoài; activity đặt tên việc làm (xác nhận đơn, kiểm tra đủ điều kiện bán…); thuật ngữ Inventory Lock / Anti-Fraud để chú thích hoặc gộp vào một bước BVA.

### Ưu tiên 3 — Sửa định lượng theo chu kỳ đúng

Bỏ thời gian duyệt/giỏ khỏi chu kỳ; nếu giữ P1 hẹp thì đo “Đặt hàng → xác nhận / hủy”; nếu làm B2 thì đo đến giao / hủy và dùng đơn vị phút–giờ phù hợp NowFree / 48H.

### Ưu tiên 4 — Cân bằng kiến nghị cải tiến

Giữ các ý self-service hủy/sửa đơn, thông báo khi hủy nghi ngờ gian lận, đồng bộ tồn (ở mức quy tắc vận hành). Giảm hoặc chuyển phần Deep-Link / Local Storage / AI scoring sang phụ lục “gợi ý hệ thống”.

### Ưu tiên 5 — Đồng bộ với tài liệu nhóm

Khớp tên và ranh giới với `research.md` B2 và `core_bpmn.md` để tránh một thành viên vẽ “mua hàng đến OMS”, thành viên khác vẽ “đơn đến giao” như hai SoT khác nhau.

---

## 9. Kết luận

P1 của Phúc **có nền tảng tốt** (bằng chứng Hasaki, đủ bốn yếu tố, đã phân tích định tính/định lượng), nhưng đang mô tả chủ yếu **đoạn checkout–xác nhận đơn** bằng ngôn ngữ **hệ thống TMĐT**, trong khi quy trình cốt lõi then chốt của Hasaki / cùng ngành — và của bộ research nhóm — là **Order-to-Delivery** với ranh giới từ **Đặt hàng** đến **giao / hủy**, không đo thời gian xem app. Nên ưu tiên sửa **process boundary + giảm technical bias**, rồi mới chốt BPMN và số liệu chu kỳ.
