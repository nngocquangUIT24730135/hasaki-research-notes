# Nội dung bổ sung — Quy trình giao hàng NowFree 2 giờ (Q1)

**File BPMN kèm theo:** `hasaki-van-chuyen-2h-manual-layouted-v2.bpmn`  
**Mục đích:** điền các phần chữ còn thiếu theo rubik `01-requirements/yeu_cau_do_an.md` để kèm sơ đồ mô hình hóa quy trình cốt lõi.  
**Vị trí kiến trúc:** phân đoạn fulfillment của chuỗi **B2 — Xử lý đơn hàng online và giao hàng** (*Order-to-Delivery*), **chỉ nhánh NowFree 2H**. Quy trình tiếp nhận / xác nhận đơn online (P1 — phần Phúc) bàn giao sang Q1 bằng sự kiện *đơn 2H đã xác nhận, sẵn sàng thực hiện giao*.

> **Phương pháp:** ưu tiên chính sách công bố trên trang hỗ trợ Hasaki; bước nội bộ (phân công cửa hàng, gọi xác nhận trước khi soạn, kiểm tồn thực tế tại quầy) ghi là *suy luận theo chuẩn ngành giao nhanh từ cửa hàng* — không khẳng định đã quan sát sổ tay nội bộ.

---

## 0. Ánh xạ với yêu cầu đồ án

| Mục rubik | Nội dung trong file này |
|-----------|-------------------------|
| §1 Bốn yếu tố liệt kê quy trình | Mục 1 |
| §2 Mô hình hóa (mô tả BPMN, gateway) | Mục 2 + file `.bpmn` |
| §3.1 Bằng chứng | Mục 3.1 |
| §3.2 Phỏng vấn 10+10 | Mục 3.2 |
| §4.1 Phân tích định tính | Mục 4 |
| §4.2 Phân tích định lượng | Mục 5 |

---

## 1. Hồ sơ quy trình (đủ bốn yếu tố)

| Trường | Nội dung |
|--------|----------|
| **Tên quy trình** | Thực hiện giao hàng nhanh NowFree 2 giờ (*Store-Fulfillment-to-Delivery* — nhánh 2H của B2) |
| **Nhóm** | Quy trình cốt lõi (*core process*) |
| **Đối tượng theo dõi (*case*)** | Một mã đơn hàng đã chọn NowFree 2H |
| **Sự kiện kích hoạt (*trigger*)** | Nhận thông điệp *Đơn hàng 2H được đặt / đã xác nhận* từ quy trình tiếp nhận đơn (P1). Trên BPMN: start message *Đơn hàng 2H được đặt*. |
| **Khách hàng của quy trình (*process customer*)** | Khách đã đặt đơn NowFree trên website / ứng dụng Hasaki (người nhận hàng) |

### 1.1. Tác nhân (*actors*)

| Tác nhân | Vai trò trên sơ đồ |
|----------|-------------------|
| Khách hàng | Xác nhận lịch khi được gọi; nhận hàng; nhận thông báo hủy / phiếu 100.000đ |
| Hệ thống Hasaki | Phân công cửa hàng / kho gần nhất; ghi nhận giờ giao đã cam kết (ETA gốc); xét phiếu 100K; hủy và hoàn tiền (đơn đã thanh toán trước) |
| Nhân viên cửa hàng / kho gần nhất | Kiểm tồn thực tế; gọi xác nhận địa chỉ & giờ giao; soạn–đóng gói; bàn giao shipper; hoàn hàng về cửa hàng; liên hệ hẹn giao lại |
| Shipper (đội giao nhanh 2H) | Giao hàng; liên hệ khách; ghi nhận giao thành công / thất bại |

### 1.2. Khách hàng của quy trình

Khách đã hoàn tất đặt đơn NowFree (đã chọn địa chỉ thuộc vùng áp dụng, đã chốt ETA gốc và phí lúc đặt ở P1).  
**Không** gồm: khách chỉ đang duyệt app; khách chọn giao 48H / đối tác 3PL; khách đang yêu cầu đổi trả sau khi đã nhận (B4).

### 1.3. Kết quả có thể xảy ra (*outcomes*)

| Kết quả | Ý nghĩa |
|---------|---------|
| Giao thành công đúng hạn | Nhận hàng không muộn hơn ETA gốc |
| Giao thành công trễ — đã cộng phiếu 100.000đ | Trễ ETA, đủ điều kiện đền bù theo chính sách NowFree |
| Giao thành công trễ — miễn trừ đền bù | Trễ nhưng thuộc miễn trừ (khách hẹn muộn hơn, lỗi người nhận, bất khả kháng, giao lại sau không liên hệ được…) |
| Hủy — hết hàng thực tế tại cửa hàng | Không đủ tồn khi kiểm tại điểm fulfill |
| Hủy & hoàn tiền đã thanh toán | Không liên lạc được để giao lại trong 3 ngày (theo quy trình giao hàng công bố); hoàn trong khung 30 ngày nếu đã trả trước |

### 1.4. Mô tả quy trình bằng lời

1. Hệ thống nhận đơn 2H đã xác nhận từ P1; phân công cửa hàng / kho gần nhất; ghi nhận ETA gốc đã chốt lúc đặt.  
2. Nhân viên kiểm **tồn thực tế** tại cửa hàng. Nếu không đủ → thông báo khách, hủy đơn, kết thúc.  
3. Nếu đủ tồn → gọi xác nhận địa chỉ và thời gian giao:  
   - Khách giữ lịch gốc → tiếp tục soạn;  
   - Khách hẹn lại muộn hơn → ghi nhận (miễn trừ phiếu 100K) rồi vẫn fulfill theo lịch mới;  
   - Không liên lạc được → ghi nhận và vẫn soạn / giao theo địa chỉ & ETA trên đơn (shipper gọi lại khi giao).  
4. Soạn hàng, đóng gói, bàn giao shipper.  
5. Shipper giao hàng: thành công → xét đúng hạn ETA hay trễ; nếu trễ → xét đủ điều kiện phiếu 100K hay miễn trừ.  
6. Nếu giao thất bại / không liên hệ được: hoàn hàng về cửa hàng → liên hệ hẹn giao lại trong 3 ngày. Hẹn được → giao lại; hết 3 ngày không liên lạc được → hủy đơn và hoàn tiền đã thanh toán (nếu có) trong 30 ngày.

### 1.5. Ranh giới (*process boundary*) và bàn giao từ P1

| | Trong phạm vi Q1 | Ngoài phạm vi Q1 |
|--|------------------|------------------|
| Thời điểm | Từ đơn 2H sẵn sàng fulfill đến giao / hủy có kiểm soát | Duyệt app, giỏ hàng, chọn COD/VNPAY, anti-fraud (P1); giao 48H/3PL; đổi trả sau nhận (B4) |
| Đo chu kỳ | Từ start Q1 → outcome đóng | Không cộng thời gian xem / lựa hàng trên app |

**Bảng bàn giao P1 → Q1**

| Trường | P1 đã chốt | Q1 giả định |
|--------|------------|-------------|
| Hình thức giao | NowFree 2H, địa chỉ thuộc vùng | Chỉ thực hiện nhánh 2H |
| Thanh toán | COD được chấp nhận hoặc trả trước thành công | Không vẽ lại cổng thanh toán; “hoàn tiền” chỉ khi đã thu trước |
| ETA & phí | Đã chốt trên màn đặt | Ghi nhận / đồng bộ, không tự đổi cam kết |
| Tồn mềm lúc đặt | Có thể đã kiểm | Q1 kiểm tồn thực tế tại CH — được phép lệch → hủy |

---

## 2. Mô hình hóa BPMN (khớp file `.bpmn`)

### 2.1. Cấu trúc sơ đồ

| Thành phần | Nội dung |
|------------|----------|
| Pool | (1) Khách hàng; (2) Hasaki — Quy trình giao hàng 2H |
| Lane (Hasaki) | Hệ thống; Nhân viên cửa hàng / kho gần nhất; Shipper |
| Liên kết | Luồng tin nhắn (*message flow*): đơn 2H; gọi xác nhận; thông báo hết hàng/hủy; giao hàng; liên hệ giao; hẹn giao lại; hủy & hoàn; cộng phiếu 100K |
| File | `hasaki-van-chuyen-2h-manual-layouted-v2.bpmn` |

### 2.2. Cổng điều kiện XOR phía Hasaki (đếm cho rubik)

| # | Nhãn cổng | Nhánh chính |
|---|-----------|-------------|
| 1 | Đủ tồn thực tế? | Đủ → gọi xác nhận / Không đủ → hủy hết hàng |
| 2 | Kết quả xác nhận lịch giao? | Giữ giờ gốc / Khách hẹn muộn hơn / Không liên lạc được |
| 3 | Giao hàng thành công? | Thành công → xét đúng hạn / Thất bại → hoàn hàng |
| 4 | Liên hệ được để giao lại? | Hẹn được → giao lại / Hết 3 ngày → hủy & hoàn |
| 5 | Giao đúng hạn ETA gốc? | Đúng hạn → kết thúc thành công / Trễ → xét phiếu |
| 6 | Đủ điều kiện phiếu 100K? | Đủ → cộng phiếu / Miễn trừ → kết thúc không phiếu |

Ngoài ra có **2 cổng gộp** (sau xác nhận lịch; trước giao lại) — phục vụ *join*, không phải điểm quyết định nghiệp vụ mới.

> Rubik: **6** XOR quyết định → mức “nhiều hơn 5” (0,75 điểm độ phức tạp trên một sơ đồ). Các tiêu chí phiếu 100K gom trong **một** cổng + chú thích / bảng quyết định — tránh xẻ checklist thành nhiều cổng.

### 2.3. Bảng quyết định rút gọn — phiếu mua hàng 100.000đ

| Điều kiện | Cộng phiếu 100K? |
|-----------|------------------|
| Đã giao thành công nhưng **trễ hơn ETA gốc** | Xét tiếp |
| Khách đã chủ động hẹn lại muộn hơn lúc xác nhận lịch | Không (miễn trừ) |
| Đã giao lại sau lần không liên hệ được / lỗi phía người nhận | Không |
| Bất khả kháng theo chính sách | Không |
| Các trường hợp trễ còn lại (đủ điều kiện công bố) | Có |

Nguồn hướng dẫn: trang hỗ trợ vận chuyển 2H / NowFree Hasaki.

---

## 3. Phương pháp thực hiện

### 3.1. Bằng chứng (*evidence*)

| Loại | Nội dung / nguồn |
|------|------------------|
| Chính sách công bố | [Vận chuyển 2H](https://hotro.hasaki.vn/van-chuyen-2h.html); [Quy trình giao hàng](https://hotro.hasaki.vn/quy-trinh-giao-hang.html); [Hướng dẫn đặt hàng 2H](https://hotro.hasaki.vn/huong-dan-dat-hang-2h.html); [Hướng dẫn đặt hàng](https://hotro.hasaki.vn/huong-dan-dat-hang.html) |
| Quy tắc mô hình bám công bố | Vùng NowFree; phí theo ngưỡng đơn; bảng giờ đặt → giờ nhận; phiếu 100K khi trễ đủ điều kiện; không liên lạc 3 ngày → hủy & hoàn trong 30 ngày (đơn đã thanh toán) |
| Suy luận chuẩn ngành (ghi rõ trên báo cáo) | Phân công cửa hàng gần nhất; kiểm tồn thực tế tại quầy; gọi xác nhận lịch trước soạn; shipper nội bộ bán kính ngắn |
| Sơ đồ tổ chức (mức chức năng) | Khối vận hành cửa hàng / kho; đội giao nhanh; hệ thống đơn — tổng hợp từ thông tin công khai, không phải sơ đồ nội bộ chính thức |
| Kế hoạch làm việc (gợi ý khi khảo sát) | Ca soạn đơn 2H theo khung giờ nhận; checklist bàn giao shipper; nhật ký gọi khách / giao thất bại |
| Thuật ngữ | NowFree, ETA gốc, tồn thực tế, phiếu 100K, COD, hoàn trong 30 ngày |
| Biểu mẫu gợi ý | Biên bản giao nhận nội bộ cửa hàng–shipper; mẫu ghi nhận hẹn giao lại; kịch bản phỏng vấn (mục 3.2) |

### 3.2. Bộ câu hỏi phỏng vấn (đủ 10 định tính + 10 định lượng)

**Đối tượng gợi ý:** nhân viên cửa hàng / kho fulfill 2H; shipper; điều phối hoặc chăm sóc khách hàng xử lý đơn giao.

#### Định tính — 5 có cấu trúc

1. Khi đơn 2H vào cửa hàng, thứ tự ưu tiên soạn so với đơn giao thường là: (A) luôn ưu tiên 2H (B) theo ca cố định (C) tùy quản lý ca (D) không rõ.  
2. Kiểm tồn thực tế trước soạn được làm: (A) quét từng SKU trên hệ thống cửa hàng (B) nhìn kệ nhanh (C) cả hai (D) thường bỏ qua nếu hệ thống báo còn.  
3. Tỷ lệ ước lượng đơn phải gọi xác nhận địa chỉ/giờ trước khi soạn: (A) &lt;25% (B) 25–50% (C) 50–75% (D) &gt;75%.  
4. Khi không gọi được khách lúc xác nhận lịch, hướng xử lý phổ biến: (A) vẫn soạn theo địa chỉ đơn (B) giữ đơn chờ (C) hủy ngay (D) chuyển giao thường.  
5. Nguyên nhân giao trễ ETA gốc gặp nhiều nhất: (A) chờ soạn/tồn (B) kẹt xe / bán kính xa (C) khách không nghe máy (D) sai địa chỉ.

#### Định tính — 5 không cấu trúc

1. Anh/chị mô tả một ca điển hình từ lúc nhận lệnh đơn 2H đến lúc bàn giao shipper.  
2. Những tình huống nào cửa hàng phải từ chối / hủy đơn 2H dù app đã cho đặt?  
3. Khi shipper giao không thành công lần đầu, ai chịu trách nhiệm liên hệ hẹn lại và trong bao lâu?  
4. Anh/chị đánh giá thế nào về việc cộng phiếu 100.000đ khi giao trễ — có rõ tiêu chí miễn trừ trên thực địa không?  
5. Điểm phối hợp nào giữa hệ thống, cửa hàng và shipper dễ phát sinh sai sót nhất?

#### Định lượng — 5 có cấu trúc

1. Thời gian trung bình từ nhận lệnh đơn 2H đến bắt đầu soạn (phút): (A) &lt;5 (B) 5–15 (C) 15–30 (D) &gt;30.  
2. Thời gian soạn–đóng gói một đơn 2H điển hình (phút): (A) &lt;10 (B) 10–20 (C) 20–35 (D) &gt;35.  
3. Tỷ lệ giao thành công ngay lần đầu (ước lượng): (A) &lt;80% (B) 80–90% (C) 90–95% (D) &gt;95%.  
4. Tỷ lệ đơn 2H phải phát phiếu 100K vì trễ (ước lượng / tháng gần nhất): (A) &lt;1% (B) 1–3% (C) 3–5% (D) &gt;5%.  
5. Tỷ lệ đơn hủy vì hết hàng thực tế sau khi đã xác nhận trên app (ước lượng): (A) &lt;0,5% (B) 0,5–1% (C) 1–3% (D) &gt;3%.

#### Định lượng — 5 không cấu trúc

1. Theo quan sát của anh/chị, cửa sổ thời gian từ lúc đặt đến giờ nhận cam kết thường là bao nhiêu phút trong khung giờ ban ngày?  
2. Thời gian chờ shipper nhận bàn giao trung bình khoảng bao lâu vào giờ cao điểm?  
3. Chi phí / đơn giao 2H nội thành anh/chị biết hoặc ước lượng được những khoản nào (nhân sự soạn, xăng/shipper…)?  
4. Trong 3 ngày chờ giao lại, tỷ lệ cuối cùng vẫn phải hủy–hoàn roughly bao nhiêu?  
5. Số cuộc gọi trung bình liên quan một đơn 2H (xác nhận lịch + giao) là bao nhiêu?

---

## 4. Phân tích định tính (*qualitative analysis*)

Mỗi mục: **liệt kê → mô tả → đề xuất khắc phục**.

### 4.1. Phân tích giá trị gia tăng

| Hoạt động | Phân loại | Mô tả | Đề xuất khắc phục / giữ |
|-----------|-----------|--------|-------------------------|
| Soạn hàng và đóng gói | VA | Chuẩn bị đúng hàng để khách nhận | Giữ; checklist SKU / hạn dùng |
| Giao hàng đến tay khách | VA | Giá trị cốt lõi của NowFree | Tối ưu bán kính / ca shipper |
| Thông báo / cộng phiếu 100K khi trễ đủ điều kiện | VA | Bù trải nghiệm cam kết giờ | Giữ minh bạch điều kiện miễn trừ |
| Gọi xác nhận địa chỉ & giờ giao | BVA | Giảm giao thất bại, bảo vệ SLA | Chỉ gọi đơn rủi ro cao (địa chỉ mới, đơn lớn) để giảm NVA cảm nhận |
| Kiểm tồn thực tế tại cửa hàng | BVA | Tránh giao thiếu / hủy muộn | Đồng bộ tồn quầy–app (quy trình A3 hỗ trợ) |
| Ghi nhận ETA đã chốt | BVA | Cơ sở xét đúng hạn / phiếu | Tự động hóa từ P1, tránh nhập tay |
| Phân công cửa hàng gần nhất | BVA | Điều phối năng lực điểm fulfill | Giữ |
| Gọi lại / hẹn giao lại sau thất bại | BVA | Thu hồi đơn, giảm hủy oan | Cửa sổ tự phục vụ đổi giờ trên app |
| Chờ shipper / chờ khách nghe máy | NVA (Hold) | Không tăng giá trị cảm nhận | Xếp ca bàn giao; ưu tiên ZNS/SMS trước gọi |
| Soạn lại sau hoàn hàng về cửa hàng | NVA / Overdo | Lặp công khi giao thất bại | Xác nhận lịch chắc hơn với đơn rủi ro |

### 4.2. Phân tích lãng phí

| Loại | Biểu hiện trong Q1 | Đề xuất khắc phục |
|------|--------------------|-------------------|
| **Hold** | Chờ bàn giao shipper; chờ khách nghe máy; giữ đơn trong 3 ngày | Lịch shipper theo sóng đơn 2H; nhắc lịch tự động |
| **Move** | Hoàn hàng về cửa hàng rồi soạn / giao lại; di chuyển giữa kệ khi tồn ảo | Giảm lệch tồn; gom vị trí pick 2H |
| **Overdo** | Gọi xác nhận mọi đơn kể cả khách quen / địa chỉ cố định; kiểm tra trùng thông tin nhiều lần | Phân loại rủi ro; tin nhắn xác nhận một chạm |

### 4.3. Mô hình xương cá — “Giao NowFree trễ hơn ETA gốc”

**Hiện tượng:** Đơn giao thành công nhưng sau giờ nhận dự kiến đã chốt lúc đặt.

| Nhóm | Nguyên nhân gợi ý |
|------|-------------------|
| Người | Soạn chậm giờ cao điểm; shipper thiếu; khách không nghe máy lần đầu |
| Phương pháp | Gọi xác nhận kéo dài trước soạn; chưa ưu tiên hàng đợi 2H rõ |
| Máy móc / hệ thống | Lệch tồn app–quầy; ETA không khớp năng lực cửa hàng thực tế |
| Nguyên vật liệu | Hết hàng thực tế phải đổi điểm / hủy muộn |
| Môi trường | Kẹt xe, mưa, khung giờ cận 18h |

**Hướng xử lý ưu tiên:** giảm Hold bàn giao + siết tồn thực tế + chỉ gọi xác nhận có chọn lọc.

---

## 5. Phân tích định lượng (*quantitative analysis*)

> Chưa có số liệu nội bộ Hasaki. Bảng dưới là **ước lượng có kiểm soát** (cùng phương pháp `03-core/core.md`), đơn giá nhân sự giả định **80.000đ/giờ (~1.333đ/phút)**.  
> **Chu kỳ Q1:** từ *đơn 2H sẵn sàng fulfill* (start BPMN) đến giao thành công / hủy đóng case. **Không** gồm thời gian duyệt app hay checkout P1.

### 5.1. Thời gian (kịch bản thuận: đủ tồn, giữ lịch gốc, giao thành công lần đầu)

| Giai đoạn / bước | Loại | Thấp | Điển hình | Cao (phút) |
|------------------|------|------|-----------|------------|
| Phân công cửa hàng + ghi nhận ETA | Xử lý | 0,5 | 1 | 3 |
| Kiểm tồn thực tế | Xử lý | 1 | 3 | 8 |
| Gọi xác nhận lịch (nếu có) | Xử lý / chờ | 0 | 5 | 15 |
| Soạn – đóng gói | Xử lý | 5 | 15 | 35 |
| Chờ bàn giao shipper | Chờ | 2 | 10 | 25 |
| Giao chặng cuối | Xử lý | 15 | 40 | 90 |
| **Tổng chu kỳ Q1** (sẵn sàng fulfill → nhận) | | **~24** | **~74** | **~176** |

Ước lượng cột điển hình: xử lý ≈ 1+3+5+15+40 = **64 phút**; chờ ≈ 10 (+ một phần gọi) ≈ **10–15 phút**; hiệu suất chu kỳ ≈ 64/74 ≈ **86%** (giả định gọi xác nhận gọn).  
Cam kết NowFree thường là cửa sổ ~**120 phút** từ lúc đặt trong khung ban ngày — giá trị điển hình Q1 cần nằm trong phần còn lại của cửa sổ sau khi P1 đã chốt đặt hàng.

**Khắc phục gắn số:** giảm chờ bàn giao ~10 phút và rút gọi xác nhận không cần thiết → tăng tỷ lệ đúng ETA → giảm nguy cơ mất **100.000đ**/đơn phiếu.

### 5.2. Chất lượng

| Chỉ số | Định nghĩa | Mục tiêu gợi ý (chưa đo nội bộ) |
|--------|------------|----------------------------------|
| Đúng giờ cam kết | Giao không muộn hơn ETA gốc | ≥ 95% |
| Giao thành công lần đầu | Thành công ở lần giao thứ nhất | ≥ 90% |
| Hủy vì hết tồn thực tế | Trên tổng đơn 2H vào cửa hàng | Càng thấp càng tốt (&lt; 1%) |
| Phát phiếu 100K | Trên tổng đơn 2H giao thành công | Thấp nếu đúng giờ cao |
| Hủy sau 3 ngày không liên lạc | Trên đơn giao thất bại | Theo dõi để cải thiện liên hệ |

### 5.3. Chi phí (ước lượng / đơn 2H, nhánh thuận không trễ)

| Khoản | Ước lượng |
|-------|-----------|
| Nhân sự kiểm tồn + soạn–đóng gói (~18 phút xử lý) | ~24.000đ |
| Gọi xác nhận phân bổ (~3 phút) | ~4.000đ |
| Giao chặng cuối đô thị | 25.000–40.000đ |
| **Cộng biến đổi điển hình** | **~53.000–68.000đ** |
| Nếu trễ đủ điều kiện phiếu | **+100.000đ** (chi phí đền bù) |

**Khắc phục:** ưu tiên giảm tỷ lệ trễ đủ điều kiện phiếu (tác động chi phí lớn hơn vài phút soạn).

---

## 6. Đề xuất cải tiến (rút từ phân tích)

1. **Hàng đợi ưu tiên 2H** tại cửa hàng: giảm Hold trước soạn và trước bàn giao shipper.  
2. **Phân loại rủi ro trước khi gọi xác nhận:** chỉ gọi đơn địa chỉ mới / giá trị cao / khung giờ sát — giảm Overdo.  
3. **Đồng bộ tồn quầy–kênh online** (phối hợp quy trình quản lý tồn A3): giảm hủy hết hàng thực tế và Move hoàn hàng.  
4. **Tự phục vụ đổi giờ nhận** trên app trong cửa sổ ngắn: giảm vòng giao thất bại–hẹn lại.  
5. **Bảng quyết định phiếu 100K** công khai nội bộ ca làm việc: giảm tranh chấp miễn trừ.

---

## 7. Hình / chú thích đưa vào báo cáo Word

| Thành phần | Gợi ý |
|------------|--------|
| Hình BPMN | Chèn export từ `hasaki-van-chuyen-2h-manual-layouted-v2.bpmn`; nhãn hình **dưới** hình: *Hình X. Quy trình thực hiện giao hàng NowFree 2 giờ* |
| Bảng VA/lãng phí / thời gian | Nhãn bảng **trên** bảng |
| Viết tắt | NowFree, ETA, COD, XOR, VA/BVA/NVA, P1/Q1/B2 |

---

## 8. Tài liệu tham khảo (gợi ý)

1. Hasaki — Vận chuyển 2H: https://hotro.hasaki.vn/van-chuyen-2h.html  
2. Hasaki — Quy trình giao hàng: https://hotro.hasaki.vn/quy-trinh-giao-hang.html  
3. Hasaki — Hướng dẫn đặt hàng 2H: https://hotro.hasaki.vn/huong-dan-dat-hang-2h.html  
4. Hasaki — Hướng dẫn đặt hàng: https://hotro.hasaki.vn/huong-dan-dat-hang.html  
5. Tài liệu nhóm: `02-research/research.md` (§4.3, §5); `03-core/core_bpmn.md`; `03-core/core.md` (phương pháp định lượng)

---

## 9. Checklist trước khi nộp phần Q1

- [ ] Đủ bốn yếu tố (mục 1) trong Word  
- [ ] Hình BPMN + liệt kê ≥ 6 XOR quyết định (mục 2.2)  
- [ ] Bằng chứng + giả định ngành tách rõ (mục 3.1)  
- [ ] 10 câu định tính + 10 câu định lượng đúng cơ cấu 5+5 (mục 3.2)  
- [ ] Bảng định tính có liệt kê–mô tả–khắc phục (mục 4)  
- [ ] Bảng định lượng thời gian–chất lượng–chi phí; chu kỳ **không** gồm xem app (mục 5)  
- [ ] Đoạn nối P1 → Q1 thống nhất với phần Phúc (mục 1.5)
