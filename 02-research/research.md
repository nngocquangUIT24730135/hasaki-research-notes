# Nghiên cứu mô hình kinh doanh Hasaki và kiến trúc quy trình (*process architecture*)

**Đối tượng nghiên cứu:** Công ty Hasaki Beauty & Clinic ([hasaki.vn](https://hasaki.vn/))  
**Ngày tổng hợp:** 08/08/2026  

## Phạm vi và giới hạn phương pháp

| Loại nội dung | Cách xử lý trong báo cáo |
|---------------|--------------------------|
| Sự kiện / chính sách công bố | Trích từ website Hasaki, trang hỗ trợ, báo chí; kèm đường dẫn và thời điểm nguồn |
| Kiến trúc quy trình (*process architecture*) | *Kiến trúc tham chiếu* suy ra từ mô hình kinh doanh và chuẩn phân loại quy trình bán lẻ — **không** khẳng định đây là sổ tay nội bộ đã quan sát tại Hasaki |
| Số liệu quy mô | Nhiều nguồn lệch nhau theo năm; luôn ghi năm nguồn, không gộp thành một con số “chính thức” |

### Bảng chú thích thuật ngữ

| Thuật ngữ / viết tắt | Giải thích |
|----------------------|------------|
| Bán hàng đa kênh (*omnichannel retail*) | Khách mua và nhận hàng qua nhiều kênh (cửa hàng, website, ứng dụng, sàn thương mại điện tử) nhưng trải nghiệm gắn với cùng một thương hiệu |
| Kiến trúc quy trình (*process architecture*) | Danh mục các quy trình nghiệp vụ được phân nhóm (quản lý / cốt lõi / hỗ trợ), có đầu vào–đầu ra rõ |
| Ranh giới quy trình (*process boundary*) | Xác định quy trình bắt đầu–kết thúc ở đâu, đối tượng theo dõi là gì, việc gì thuộc quy trình khác |
| Định danh quy trình (*process identification*) | Xác định danh mục và phạm vi các quy trình trong tổ chức (theo khung FBPM) |
| Quy trình quản lý / cốt lõi / hỗ trợ (*management / core / support processes*) | Ba lớp trong kiến trúc quy trình |
| Khách hàng của quy trình (*process customer*) | Bên nhận kết quả đầu ra của quy trình (không nhất thiết là khách mua hàng) |
| Sự kiện kích hoạt (*trigger*) | Sự kiện mở một lần chạy quy trình mới |
| Đối tượng theo dõi / lần chạy (*case* / *process instance*) | Thực thể gắn một lần thực hiện quy trình (ví dụ mã đơn) |
| Kết quả (*outcome*) | Trạng thái kết thúc có kiểm soát của một lần chạy |
| Tồn khả dụng để cam kết giao | Số lượng hàng hệ thống còn “dám” hứa giao tại một điểm kho/cửa hàng tại thời điểm khách đặt |
| Thời gian chu kỳ (*cycle time*) | Thời gian từ bắt đầu đến kết thúc một lần chạy quy trình |
| NowFree | Tên dịch vụ giao nhanh khoảng 2 giờ của Hasaki (theo trang hỗ trợ) |
| COD | Thanh toán khi nhận hàng (*cash on delivery*) |
| ĐTVC | Đối tác vận chuyển |
| BPMN | *Business Process Model and Notation* — chuẩn ký hiệu vẽ sơ đồ quy trình nghiệp vụ |
| Cổng điều kiện (*gateway*), XOR | Chỗ chọn nhánh trên sơ đồ; XOR = chỉ đi một nhánh |
| Bể bơi / làn (*pool* / *lane*) | Khung tổ chức / vai trò trên sơ đồ BPMN |
| Phân tích định tính / định lượng (*qualitative / quantitative process analysis*) | Phân tích giá trị–lãng phí / đo thời gian–chi phí–chất lượng |
| Giá trị gia tăng / lãng phí (*value-added analysis* / *waste analysis*) | Phân loại VA–BVA–NVA và nguồn lãng phí (Move / Hold / Overdo) |

---

## 1. Hasaki đang kinh doanh gì?

### 1.1. Định vị

Hasaki là **chuỗi bán lẻ mỹ phẩm và chăm sóc cá nhân đa thương hiệu**, kết hợp **phòng khám / spa da liễu (Clinic)**, vận hành **đa kênh** (cửa hàng + website/ứng dụng + sàn thương mại điện tử), và dùng mạng cửa hàng như **điểm tồn gần khách** để cam kết giao nhanh (NowFree khoảng 2 giờ tại vùng đủ điều kiện).

Slogan công bố: *“Chất lượng thật – Giá trị thật”* ([tuyendung.hasaki.vn/intro](https://tuyendung.hasaki.vn/intro)).

### 1.2. Ba trụ giá trị tại điểm bán

Theo truyền thông đầu tư quốc tế (BeautyMatter, 11/2023) và trang Clinic của Hasaki, mỗi điểm bán mang tính **cửa hàng – spa – kho nhỏ**:

1. **Bán lẻ mỹ phẩm:** phân phối nhiều nhãn, giá cạnh tranh, cam kết chính hãng, hóa đơn.  
2. **Clinic / Spa:** trị liệu da, thẩm mỹ không phẫu thuật, liệu trình — tăng giá trị đơn hàng trung bình và gắn kết dài hạn.  
3. **Kho nhỏ phục vụ giao nhanh:** cùng địa điểm (hoặc kho gần) xử lý đơn online khu vực lân cận.

Nguồn: [BeautyMatter](https://beautymatter.com/articles/alibaba-invests-in-vietnamese-beauty-retailer-hasaki); [Giới thiệu Hasaki Clinic](https://hasaki.vn/gioi-thieu-hasaki-clinic-spa.html).

### 1.3. Kênh tiếp cận khách hàng

| Kênh | Vai trò |
|------|---------|
| Cửa hàng vật lý | Tư vấn, mua ngay, đổi trả tại chỗ, tạo niềm tin “hàng thật” |
| Website / ứng dụng | Tra cứu sản phẩm, đặt hàng, giao 2 giờ / 48 giờ / giao thường, đặt lịch Clinic |
| Sàn thương mại điện tử | Mở rộng độ phủ và khuyến mãi; quy tắc giao hàng thường theo sàn — **khác** luồng NowFree trên kênh của Hasaki |
| Tổng đài | 1800 6324 (hỗ trợ); 1800 6310 (khiếu nại — theo truyền thông) |

### 1.4. Mô hình kinh doanh (khung chín khối — tóm tắt)

| Khối | Nội dung |
|------|----------|
| Đề xuất giá trị | Chính hãng, giá tốt, nhận hàng nhanh, đổi trả có điều kiện khoảng 30 ngày, clinic tiện lợi |
| Phân khúc khách | Người mua mỹ phẩm phổ thông nhạy khuyến mãi; khách cần chăm sóc da |
| Kênh | Cửa hàng, kênh số của Hasaki, sàn, clinic |
| Quan hệ khách hàng | Thành viên, tích điểm, phiếu mua hàng; bù đắp khi giao 2 giờ trễ (phiếu 100.000đ đủ điều kiện) |
| Nguồn doanh thu | Bán lẻ; dịch vụ clinic |
| Nguồn lực then chốt | Mạng cửa hàng–clinic, tồn phân tán, thương hiệu tin cậy, danh mục nhiều nhãn, nền tảng số |
| Hoạt động then chốt | Mua hàng và kiểm tra chất lượng; phân phối tồn; bán đa kênh; cam kết và thực hiện giao nhanh; vận hành clinic; chăm sóc sau bán |
| Đối tác | Nhà cung cấp / nhãn hàng ([merchant.hasaki.vn](https://merchant.hasaki.vn/nha-cung-cap)); đối tác vận chuyển; cổng thanh toán; sàn; nhà đầu tư |
| Cấu trúc chi phí | Mặt bằng, nhân sự, tồn kho, khuyến mãi, giao chặng cuối, công nghệ |

### 1.5. Thị trường và cạnh tranh

- Thị trường làm đẹp và chăm sóc cá nhân Việt Nam được truyền thông nêu khoảng **2,2 tỷ USD**, tăng trưởng khoảng **7%/năm** (quanh thương vụ Alibaba năm 2023).  
- Đối thủ gần: Guardian, Medicare, Beauty Box, các cửa hàng online thuần.  
- Điểm khác tương đối của Hasaki: **clinic gắn chuỗi**, phủ tỉnh, định vị phổ thông/khuyến mãi; Guardian mạnh cửa hàng tại đô thị lớn, từng truyền thông giao nhanh khoảng 4 giờ với ngưỡng đơn khác.

Nguồn: [Báo Đầu Tư 12/12/2023](https://baodautu.vn/cuoc-choi-moi-cua-chuoi-ban-le-my-pham-d204820.html); [Tomorrow Marketers](https://blog.tomorrowmarketers.org/case-study-chien-luoc-dau-tu-thay-duoc-gi-tu-thuong-vu-alibaba-rot-von-vao-hasaki-viet-nam/).

### 1.6. Quy mô — đối chiếu nguồn (không gộp)

| Chỉ số | Giá trị | Nguồn / thời điểm |
|--------|---------|-------------------|
| Thành lập | 4/2016 | Trang tuyển dụng Hasaki |
| Cửa hàng + clinic | >140 | BeautyMatter / Báo Đầu Tư, ~11–12/2023 |
| Cột mốc 100 cửa hàng + 17 clinic / 33 tỉnh | ~2023 | [VnExpress](https://vnexpress.net/chuoi-lam-dep-hasaki-can-moc-100-chi-nhanh-4592175.html) |
| Tự công bố trang tuyển dụng | 200+ cửa hàng, 18 clinic, 2.500+ nhân viên | Truy cập 2026 |
| Thành viên / người mua mỗi tháng | 3,8 triệu / ~750.000 | BeautyMatter, 11/2023 |
| Mục tiêu thị phần | ≥35% năm 2027 | BeautyMatter / Báo Đầu Tư |
| Đầu tư | Alibaba (AIDC) cổ phần thiểu số; Excelsior trước đó | BeautyMatter / CB Insights, 11/2023 |

---

## 2. Nhóm công ty cùng loại

### 2.1. Đặc điểm chung

Công ty thuộc nhóm nghiên cứu khi phần lớn thỏa:

1. Có mạng điểm bán vật lý chuyên ngành làm đẹp / sức khỏe.  
2. Có kênh bán số riêng (website/ứng dụng), ngoài sàn.  
3. Tồn hàng tại nhiều điểm; đơn online có thể lấy từ cửa hàng hoặc kho nhỏ gần khách.  
4. Cam kết thời gian giao gắn địa lý và tồn (không chỉ giao nhiều ngày từ một tổng kho).  
5. (Tuỳ chọn) Dịch vụ tại chỗ (clinic/spa) tạo bán chéo.

### 2.2. So sánh nhanh

| Công ty / nhóm | Điểm gần Hasaki | Điểm khác |
|----------------|-----------------|-----------|
| Guardian, Watsons, Medicare | Chuỗi làm đẹp–sức khỏe đa kênh | Clinic gắn chuỗi yếu hơn; cam kết giao khác |
| Beauty Box | Chuỗi cửa hàng mỹ phẩm | Phân khúc cao cấp hơn |
| Olive Young (Hàn Quốc) | Nền tảng làm đẹp + cửa hàng + giao trong ngày | Kho đô thị tự động hóa quy mô lớn hơn |
| Ulta, Sephora (Mỹ) | Lấy hàng từ cửa hàng để giao đơn online | Ít mô hình giao vài giờ kiểu Việt Nam; clinic không phải trụ chính |
| Chuỗi nhà thuốc Việt Nam | Cửa hàng làm điểm lấy hàng, giao nhanh | Ngành hàng và quy định hành nghề khác |
| Giao hàng nhanh tiện lợi (ví dụ GrabMart) | Cam kết theo giờ | Không sở hữu thương hiệu làm đẹp + clinic |

### 2.3. Xu hướng quốc tế liên quan

Ngành bán lẻ làm đẹp đang biến cửa hàng thành **điểm lấy hàng giao đơn online**, không chỉ nơi trưng bày:

- Chuỗi Ulta mở rộng lấy hàng từ cửa hàng quy mô lớn, dùng hệ thống điều phối đơn thông minh.  
- Sephora coi giao nhận thuận tiện là trụ cột giữ chân khách.  
- Olive Young vận hành kho nhỏ trong đô thị, giao trong ngày trung bình khoảng dưới một giờ đến vài giờ.  

**Hàm ý:** NowFree của Hasaki là biến thể địa phương của mô hình *lấy hàng từ cửa hàng / kho nhỏ gần khách*: đặt tồn gần nhu cầu, hệ thống chọn điểm lấy, giao bán kính ngắn.

---

## 3. Kiến trúc quy trình tham chiếu (*reference process architecture*)

### 3.1. Cơ sở

- Khung phân loại quy trình bán lẻ (APQC — tổ chức nghiên cứu năng suất Hoa Kỳ) giúp đặt tên và phân nhóm quy trình, có yếu tố bán hàng đa kênh.  
- Kiến trúc quy trình (*process architecture*) = danh mục quy trình ngang (đầu–cuối), có bên chịu trách nhiệm, sự kiện kích hoạt (*trigger*) và kết quả (*outcome*) — khác sơ đồ tổ chức dọc theo phòng ban.

> Phần dưới là **kiến trúc tham chiếu** cho nhóm công ty cùng loại. Chỉ chỗ gắn đường dẫn Hasaki mới là chính sách quan sát được từ bên ngoài.

### 3.2. Chuỗi giá trị rút gọn

```text
Hoạch định và mở điểm bán
  → Duyệt nhà cung cấp / nhập hàng + kiểm tra chất lượng
  → Phân bổ tồn (tổng kho ↔ cửa hàng ↔ kho giao nhanh)
  → Tạo nhu cầu (tiếp thị, khuyến mãi)
  → Tiếp nhận đơn / lịch (cửa hàng | web–ứng dụng | sàn | clinic)
  → Cam kết giao (thời gian, phí, nguồn hàng)
  → Thực hiện (soạn–đóng gói–giao | bán quầy | liệu trình)
  → Thanh toán và đối soát
  → Sau bán (đổi trả, khiếu nại, thành viên)
  ← Hỗ trợ: nhân sự, công nghệ, tài chính, pháp chế
```

### 3.3. Danh mục khoảng 13 quy trình

Tên trong ngoặc theo kiểu **chuỗi giá trị đầu–cuối** (ví dụ *Order-to-Delivery*, *Procure-to-Pay*): nhấn mạnh điểm bắt đầu và kết thúc nghiệp vụ, dễ đối chiếu khung phân loại quốc tế.

#### A. Quy trình quản lý (Management Processes)

| Mã | Quy trình | Khách hàng của quy trình (*process customer*) | Kết quả điển hình (*typical outcomes*) |
|----|-----------|--------------------------|-------------------|
| A1 | Hoạch định chiến lược và mở rộng mạng cửa hàng / clinic (*Strategy-to-Expansion*) | Ban điều hành, khối phát triển chuỗi | Kế hoạch địa điểm, ngân sách, chỉ tiêu được duyệt |
| A2 | Phê duyệt và hợp tác nhà cung cấp / nhãn hàng (*Source-to-Contract*) | Bộ phận mua hàng và kho | Hợp đồng và dữ liệu nhà cung cấp, hoặc từ chối |
| A3 | Quản lý tồn kho đa kênh (*Plan-to-Stock*) | Các kênh bán và giao hàng | Tồn đồng bộ; lệnh điều chuyển / đặt mua; cảnh báo cận hạn dùng |
| A4 | Kiểm soát chất lượng nhập hàng và chống hàng giả (*Inspect-to-Release*) | Kho / ngành hàng | Lô được phép bán, hoặc cách ly / trả nhà cung cấp |

Cổng nhà cung cấp Hasaki công bố bốn bước: đăng ký → xác thực → ký hợp đồng → nhận hỗ trợ ([merchant.hasaki.vn](https://merchant.hasaki.vn/nha-cung-cap)).

#### B. Quy trình cốt lõi (Core Processes)

| Mã | Quy trình | Khách hàng của quy trình (*process customer*) | Kết quả điển hình (*typical outcomes*) |
|----|-----------|--------------------------|-------------------|
| B1 | Bán hàng và tư vấn tại cửa hàng (*Visit-to-Cash*) | Khách tại cửa hàng | Giao dịch hoàn tất, hoặc chỉ tư vấn |
| B2 | Xử lý đơn hàng online và giao hàng — gồm giao nhanh 2 giờ (*Order-to-Delivery*) | Khách đặt trên kênh của Hasaki | Giao thành công, hoặc hủy có kiểm soát (+ hoàn tiền nếu cần) |
| B3 | Đặt lịch và thực hiện dịch vụ Clinic / Spa (*Appointment-to-Service*) | Khách dùng dịch vụ | Liệu trình xong và thanh toán; hoặc dời / hủy |
| B4 | Đổi trả và hoàn tiền (*Return-to-Refund*) | Khách yêu cầu đổi / trả | Đổi, hoàn, hoặc từ chối theo điều kiện |
| B5 | Chăm sóc khách hàng và khiếu nại (*Issue-to-Resolution*) | Khách cần hỗ trợ | Yêu cầu được đóng, hoặc chuyển cấp cao hơn |

#### C. Quy trình hỗ trợ (Support Processes)

| Mã | Quy trình | Khách hàng của quy trình (*process customer*) | Kết quả điển hình (*typical outcomes*) |
|----|-----------|--------------------------|-------------------|
| C1 | Tuyển dụng và đào tạo (*Hire-to-Deploy*) | Quản lý điểm bán / clinic | Nhân sự nhận việc, hoặc từ chối |
| C2 | Tài chính – đối soát doanh thu đa kênh (*Reconcile-to-Close*) | Lãnh đạo / kiểm soát nội bộ | Sổ khớp kênh; lệch được xử lý |
| C3 | Tiếp thị và cấu hình khuyến mãi (*Campaign-to-Launch*) | Khối bán hàng | Chương trình sẵn sàng chạy; có đo hiệu quả |
| C4 | Xử lý sự cố hệ thống công nghệ thông tin (*Incident-to-Restore*) | Người dùng nội bộ | Dịch vụ được khôi phục |

### 3.4. Sơ đồ kiến trúc (nhìn nhanh)

```text
┌─────────────── QUẢN LÝ (Management) ────────────────┐
│ A1 Chiến lược & mở mạng (*Strategy-to-Expansion*)   │
│ A2 Phê duyệt NCC (*Source-to-Contract*)             │
│ A3 Tồn kho đa kênh (*Plan-to-Stock*)                │
│ A4 Chất lượng nhập hàng (*Inspect-to-Release*)      │
└─────────────────────────────────────────────────────┘
┌─────────────── CỐT LÕI (Core) ──────────────────────┐
│ B1 Bán tại cửa hàng (*Visit-to-Cash*)               │
│ B2 Đơn online & giao (*Order-to-Delivery*)          │
│ B3 Clinic / Spa (*Appointment-to-Service*)          │
│ B4 Đổi trả & hoàn tiền (*Return-to-Refund*)         │
│ B5 CSKH & khiếu nại (*Issue-to-Resolution*)         │
└─────────────────────────────────────────────────────┘
┌─────────────── HỖ TRỢ (Support) ────────────────────┐
│ C1 Tuyển dụng & đào tạo (*Hire-to-Deploy*)          │
│ C2 Tài chính – đối soát (*Reconcile-to-Close*)      │
│ C3 Tiếp thị & khuyến mãi (*Campaign-to-Launch*)     │
│ C4 Sự cố CNTT (*Incident-to-Restore*)               │
└─────────────────────────────────────────────────────┘
```

### 3.5. Năng lực hệ thống thường cần (suy luận ngành)

Không khẳng định phần mềm nội bộ Hasaki. Để chạy kiến trúc trên, doanh nghiệp cùng loại thường cần: danh mục và giá; tồn theo từng điểm; quản lý đơn và trạng thái; máy bán hàng tại quầy; soạn hàng tại cửa hàng; kết nối đối tác vận chuyển và thanh toán khi nhận; đặt lịch clinic; thành viên / phiếu mua hàng; cổng nhà cung cấp; tiếp nhận sự cố công nghệ.

---

## 4. Ranh giới quy trình (*process boundaries*)

### 4.1. Một ranh giới rõ cần trả lời

1. Đối tượng theo dõi (*case object*) là gì? (mã đơn, yêu cầu đổi trả, lịch hẹn…)  
2. Sự kiện nào mở trường hợp mới (*trigger*)?  
3. Kết quả nào đóng trường hợp (*outcome* — thành công và ngoại lệ có kiểm soát)?  
4. Ai nhận kết quả đầu ra (*process customer*)?  
5. Giao với quy trình khác bằng sự kiện nào — không “nuốt” cả quy trình kia?

### 4.2. Quy tắc tách ranh giới (*process boundary rules*)

| Đúng | Sai |
|------|-----|
| Một mã đơn / một yêu cầu đổi trả trong một sơ đồ vận hành | Nhét cả “hành trình khách hàng trọn đời” hoặc thời gian xem ứng dụng vào cùng quy trình đơn |
| Kết thúc bằng trạng thái nghiệp vụ (giao xong / hủy) | Kết thúc bằng mục tiêu mơ hồ (“khách vui”) |
| A3 cung cấp tồn khả dụng; B2 tiêu thụ khi cam kết và soạn hàng | Nhét hoạch định tồn cả quý vào sơ đồ đơn online |
| B2 khác B3 | Một luồng ứng dụng gồm cả mua hàng và điều trị |
| B4 bắt đầu khi khách yêu cầu đổi trả | Mọi đơn giao xong đều kéo dài sang đổi trả trên cùng sơ đồ |
| Đối tác vận chuyển là bên ngoài (bể bơi riêng (*pool*) hoặc hộp đen) | Vẽ chi tiết nội bộ hãng vận chuyển như của Hasaki |

### 4.3. Ranh giới các quy trình then chốt

**B2 — Xử lý đơn hàng online và giao hàng (*Order-to-Delivery*)**

| Thuộc tính | Nội dung |
|------------|----------|
| Đối tượng theo dõi (*case*) | Mã đơn hàng |
| Kích hoạt (*trigger*) | Khách bấm **Đặt hàng** (thể hiện quyết định mua; hệ thống tạo mã đơn) |
| Kết thúc (*end outcomes*) | Giao thành công và đã thanh toán, hoặc hủy có thông báo (+ hoàn nếu đã trả trước) |
| Chuẩn bị trên màn hình trước khi đặt (trước kích hoạt) | Chọn địa chỉ; hệ thống đề xuất hình thức vận chuyển / điều kiện 2 giờ / phí; khách chọn vận chuyển và phương thức thanh toán. Nếu khách dừng ở đây thì **chưa** có lần chạy quy trình (*process instance*) (chưa có mã đơn). |
| Trong phạm vi lần chạy quy trình (*process instance scope*) | Tạo đơn; thanh toán (trả trước hoặc khi nhận); soạn–đóng gói–bàn giao; giao; hẹn lại; hủy sau không liên lạc; phiếu bù khi giao 2 giờ trễ |
| Ngoài phạm vi (*out of scope*) | Duyệt ứng dụng / xem sản phẩm / so sánh / giỏ bỏ dở (**không** có mã đơn); mở cửa hàng (A1); ký nhà cung cấp (A2); đặt mua chiến lược (A3); đổi trả sau nhận (B4); clinic (B3) |
| Đo thời gian chu kỳ (*cycle time*) | Từ **tạo đơn** sau khi bấm Đặt hàng (kịch bản thanh toán trước: mốc sẵn sàng soạn = thanh toán thành công) đến giao thành công hoặc hủy và đóng trường hợp. **Không** cộng thời gian xem / lựa hàng trên ứng dụng. |

**Vì sao không đo thời gian xem hàng:** khách có thể mở ứng dụng Hasaki xem hàng lâu mà không đặt — không phát sinh mã đơn, không soạn, không giao, không áp dụng cam kết giờ nhận. Theo phân tích quy trình (thời gian chu kỳ = thời gian một lần chạy từ bắt đầu đến kết thúc; khung “từ lúc khách đưa đơn”), chỉ các đơn đã Đặt hàng mới vào mẫu định lượng. Chi tiết số liệu ước lượng: [core.md](../03-core/core.md) mục 5.

Chính sách công bố liên quan: option 2 giờ / 48 giờ tại nội thành Thành phố Hồ Chí Minh và Hà Nội ([hướng dẫn đặt hàng](https://hotro.hasaki.vn/huong-dan-dat-hang.html)); vùng NowFree trên trang hỗ trợ nêu Thành phố Hồ Chí Minh – Cần Thơ + danh sách khu vực; giao thường 24–48 giờ hoặc 3–6 ngày tùy vùng; đơn trên 5 triệu chỉ thanh toán trước; không liên lạc 3 ngày thì hủy và hoàn trong 30 ngày; không đồng kiểm; có đối tác vận chuyển.

Khi vẽ sơ đồ, vẫn có thể hiện giai đoạn **cam kết giao** (bước trên màn hình đặt hàng + kiểm hệ thống quanh lúc đặt) để đủ cổng điều kiện, rồi **tạo đơn và sẵn sàng soạn → soạn–đóng gói–bàn giao → giao đến khách → xử lý ngoại lệ**. Cam kết trên BPMN giúp hiểu quy tắc; **định lượng chỉ trên lần chạy đã Đặt hàng**. Các bước xếp ưu tiên đơn 2 giờ, xác nhận tồn lúc soạn là *suy luận chuẩn ngành* — xem [ba_model_b2_b4.md](../03-core/ba_model_b2_b4.md).

**B4 — Đổi trả (*Return-to-Refund*)**

| Thuộc tính | Nội dung |
|------------|----------|
| Đối tượng theo dõi (*case*) | Yêu cầu đổi / trả |
| Kích hoạt (*trigger*) | Khách gửi yêu cầu kèm thông tin liên hệ |
| Kết thúc (*outcomes*) | Đổi hàng / hoàn tiền / từ chối có lý do |
| Chính sách | Cửa sổ **30 ngày** từ 01/06/2024 ([đổi trả](https://hotro.hasaki.vn/doi-tra-hoan-tien.html)) |
| Đo thời gian chu kỳ (*cycle time*, tại cửa hàng) | Từ tiếp nhận yêu cầu đến đổi/từ chối/lập phiếu xong; không gồm đi đường của khách. Chi tiết ước lượng: [core.md](../03-core/core.md) mục 5.2 |
| Ghi chú khi vẽ BPMN | Tiêu chí chính sách nằm trong **một** hoạt động (*activity*) thẩm định + bảng quyết định (*decision table*); không xẻ mỗi tiêu chí thành cổng XOR (*XOR gateway*) — xem [core_bpmn.md](../03-core/core_bpmn.md) phần B |

Chi tiết phân tích nghiệp vụ và hướng dẫn vẽ: [ba_model_b2_b4.md](../03-core/ba_model_b2_b4.md), [core_bpmn.md](../03-core/core_bpmn.md).

### 4.4. Giao giữa các quy trình

```text
A2 Nhà cung cấp → A4 Kiểm tra chất lượng → A3 Tồn kho
                                              ↓ tồn khả dụng
                         B1 Bán cửa hàng   B2 Đơn online & giao hàng → Đối tác vận chuyển
                                              ↓ đã giao
                                         B4 Đổi trả ↔ B5 Chăm sóc khách hàng
                         B3 Clinic ← bán chéo / phiếu mua hàng
```

---

## 5. Mô hình giao hàng 2 giờ (NowFree)

### 5.1. Định nghĩa theo trang hỗ trợ

NowFree là dịch vụ **giao nhanh miễn phí trong khoảng 2 giờ** cho khách thuộc khu vực được liệt kê (trang hỗ trợ hiện nêu Thành phố Hồ Chí Minh – Cần Thơ và danh sách chi tiết trên web).  
Nguồn: [Vận chuyển 2H](https://hotro.hasaki.vn/van-chuyen-2h.html).

### 5.2. Điều kiện

1. Địa chỉ thuộc vùng áp dụng.  
2. Đơn từ 90.000đ: miễn phí; dưới 90.000đ: phí 10.000đ (vẫn có thể giao 2 giờ).  
3. Sản phẩm có sẵn tại kho gần nhất xử lý giao nhanh.  
4. Khách chọn hình thức giao nhanh 2 giờ.

Có bảng giờ đặt hàng → giờ nhận dự kiến; giao đến 18 giờ, thứ Hai đến Chủ nhật.  
Nếu giao trễ hơn giờ dự kiến, đơn giao thành công và đủ điều kiện → phiếu mua hàng 100.000đ (có miễn trừ bất khả kháng hoặc lỗi phía người nhận).

### 5.3. Lệch thông tin phủ sóng

| Nguồn | Nội dung về phủ sóng |
|-------|----------------------|
| Trang hỗ trợ (ưu tiên cho quy tắc) | Thành phố Hồ Chí Minh – Cần Thơ + danh sách khu vực |
| Báo Đầu Tư 2023 | Nhắc miễn phí 2 giờ tại nhiều tỉnh có chi nhánh |
| Thông điệp tiếp thị | Nhấn mạnh giao nhanh 2 giờ, đôi khi claim rộng |

**Nguyên tắc:** quy tắc trên sơ đồ bám trang hỗ trợ; số liệu phủ sóng coi là thông điệp theo thời điểm.

### 5.4. Phí vận chuyển chung

| Khu vực | Ngưỡng miễn phí | Phí dưới ngưỡng |
|---------|-----------------|-----------------|
| Tỉnh/thành **có** cửa hàng Hasaki | ≥ 90.000đ | 10.000đ |
| Tỉnh/thành **không** có cửa hàng | ≥ 249.000đ | 25.000đ |

Nguồn: [Quy trình giao hàng](https://hotro.hasaki.vn/quy-trinh-giao-hang.html).

### 5.5. Bảy tầng vận hành (khung ngành)

1. Thiết kế mạng điểm bán / kho theo bán kính thời gian  
2. Phân bổ mặt hàng tại điểm giao nhanh  
3. Tồn và tồn khả dụng theo từng điểm  
4. Cơ chế cam kết (địa lý + giỏ hàng + tồn → hiện / ẩn 2 giờ và giờ nhận dự kiến)  
5. Điều phối đơn tới điểm lấy hàng  
6. Soạn–đóng gói tại điểm  
7. Giao chặng cuối và xử lý khi trễ / giao lại / hủy  

### 5.6. Rủi ro và chỉ số nên theo dõi

Tất cả chỉ số dưới đây đo trên **đơn đã tạo** (sau Đặt hàng), không trên phiên chỉ xem ứng dụng. Thời gian soạn = từ đơn sẵn sàng soạn đến bàn giao đơn vị giao. Đúng giờ = giao không muộn hơn **giờ nhận dự kiến** lúc đặt (bảng NowFree), không phải thời gian khách xem danh mục sản phẩm.

| Rủi ro | Dấu hiệu | Chỉ số gợi ý |
|--------|----------|--------------|
| Tồn ảo | Hiện 2 giờ nhưng lúc soạn hết hàng | Độ chính xác tồn; tỷ lệ hủy / đổi điểm sau đặt |
| Quá tải cửa hàng | Đơn online làm chậm bán quầy | Số đơn 2 giờ mỗi giờ mỗi điểm; thời gian soạn (sau Đặt hàng) |
| Sai vùng cam kết | Đúng “gần” trên giấy nhưng giao trễ | Tỷ lệ đúng giờ theo từng khu vực nhỏ |
| Giao lần đầu thất bại | Gọi lại nhiều, hủy sau 3 ngày | Tỷ lệ giao thành công lần đầu |
| Chi phí bù đắp | Phát nhiều phiếu 100.000đ | Chi phí phiếu / doanh thu đơn 2 giờ |
| Cycle time kéo dài | Chờ soạn / chờ shipper / giao lại | Thời gian từ tạo đơn (hoặc TT trước thành công) đến nhận thành công |

---

## 6. Kết luận ngắn

1. Hasaki kết hợp bán lẻ đa nhãn, clinic và kênh số; cửa hàng vừa bán vừa làm điểm lấy hàng giao nhanh.  
2. Lợi thế bền vững hơn khuyến mãi đơn thuần nằm ở mạng điểm, độ tin chính hãng, khớp giữa cam kết tồn và thực giao, cùng vòng clinic.  
3. Kiến trúc khoảng 13 quy trình (quản lý / cốt lõi / hỗ trợ) đủ bao phủ nhóm công ty cùng loại.  
4. Ranh giới rõ giữa đơn online (B2), tồn kho (A3), clinic (B3) và đổi trả (B4) là điều kiện để phân tích và vẽ sơ đồ có ý nghĩa; với B2, xem hàng trên ứng dụng không mở quy trình — chỉ Đặt hàng mới mở lần chạy và mới đo thời gian chu kỳ.  
5. Giao 2 giờ là hệ thống nhiều tầng; chính sách công bố đủ để hiểu cam kết và bù đắp, chưa đủ để khẳng định thuật toán gán kho nội bộ.

---

## 7. Tài liệu tham khảo

### Hasaki

- https://hasaki.vn/  
- https://hasaki.vn/gioi-thieu-hasaki-clinic-spa.html  
- https://tuyendung.hasaki.vn/intro  
- https://hotro.hasaki.vn/van-chuyen-2h.html  
- https://hotro.hasaki.vn/huong-dan-dat-hang.html  
- https://hotro.hasaki.vn/quy-trinh-giao-hang.html  
- https://hotro.hasaki.vn/doi-tra-hoan-tien.html  
- https://merchant.hasaki.vn/nha-cung-cap  

### Báo chí / hồ sơ

- https://baodautu.vn/cuoc-choi-moi-cua-chuoi-ban-le-my-pham-d204820.html  
- https://beautymatter.com/articles/alibaba-invests-in-vietnamese-beauty-retailer-hasaki  
- https://blog.tomorrowmarketers.org/case-study-chien-luoc-dau-tu-thay-duoc-gi-tu-thuong-vu-alibaba-rot-von-vao-hasaki-viet-nam/  
- https://vnexpress.net/chuoi-lam-dep-hasaki-can-moc-100-chi-nhanh-4592175.html  

### Chuẩn ngành và tài liệu đồ án liên quan

- Khung phân loại quy trình bán lẻ APQC  
- [Phân tích nghiệp vụ B2 và B4](../03-core/ba_model_b2_b4.md)  
- [Quy trình cốt lõi](../03-core/core.md) · [Hướng dẫn vẽ BPMN](../03-core/core_bpmn.md)  
