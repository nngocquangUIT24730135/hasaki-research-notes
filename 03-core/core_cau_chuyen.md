# Câu chuyện khách hàng — Hai quy trình cốt lõi (*core processes*) B2 và B4

**Mục đích:** giúp người chưa từng mua hàng tại Hasaki hình dung doanh nghiệp vận hành thế nào qua **câu chuyện**, trước khi đọc sơ đồ BPMN hay bảng phân tích.  
**Hai quy trình được kể:**  
- **B2** (*Order-to-Delivery*) — Từ lúc khách **bấm Đặt hàng** trên website/ứng dụng đến khi nhận hàng (kể cả giao nhanh 2 giờ). Thời gian xem / lựa hàng trước đó không thuộc quy trình vận hành đơn.  
- **B4** (*Return-to-Refund*) — Từ lúc muốn đổi/trả đến khi đổi hàng, hoàn tiền, hoặc bị từ chối theo chính sách.  

**Nguồn chính sách đổi trả:** [Đổi trả – hoàn tiền](https://hotro.hasaki.vn/doi-tra-hoan-tien.html)  
**Nguồn đặt hàng / giao 2 giờ / giao hàng:** trang hỗ trợ Hasaki (đặt hàng, vận chuyển 2 giờ, quy trình giao hàng).  
**Ranh giới chuẩn (*process boundary*):** [research.md](../02-research/research.md) §4.3.  

> Đây là **câu chuyện minh họa** bám chính sách công bố và logic vận hành đã mô tả trong `core.md` / `ba_model_b2_b4.md`. Chi tiết nội bộ (ai soạn hàng đúng phút nào) có thể khác thực tế từng cửa hàng.

---

## Nhân vật xuyên suốt

**Lan** sống tại Thành phố Hồ Chí Minh, hay mua mỹ phẩm online.  
**Mai** là bạn Lan, ở tỉnh chưa có cửa hàng Hasaki gần nhà.  

Hasaki với họ là: cửa hàng xanh quen thuộc + website/ứng dụng để đặt hàng + đôi khi đặt lịch chăm sóc da tại Clinic. Phần câu chuyện dưới đây chỉ xoay quanh **mua online – nhận hàng** và **đổi trả**.

---

## Chương 1 — Lan đặt hàng giao nhanh 2 giờ (quy trình B2, trường hợp thuận lợi / *happy path*)

Một chiều thứ Bảy, Lan hết kem chống nắng. Trên ứng dụng Hasaki, sản phẩm còn biểu tượng gợi ý giao nhanh. Cô chọn địa chỉ căn hộ (nằm trong vùng được hỗ trợ giao 2 giờ), thấy hệ thống đề xuất:

- Giao nhanh trong khoảng 2 giờ (NowFree), và  
- Giao trong 48 giờ.  

Đơn của Lan trên 90.000đ nên phí giao 2 giờ **miễn phí**. Cô chọn giao 2 giờ, thanh toán trước bằng mã QR, bấm **Đặt hàng**. Màn hình hiện mã đơn để tra cứu.

Phía Hasaki (khách không nhìn thấy hết các bước nội bộ, nhưng đây là trình tự hợp lý của B2): hệ thống kiểm tra địa chỉ thuộc vùng áp dụng, xác nhận hàng còn tại kho hoặc cửa hàng gần nhất xử lý giao nhanh, tạo đơn và đưa vào soạn với mức ưu tiên cao vì đã cam kết khung giờ. Nhân viên tại điểm lấy hàng soạn đúng tuýp kem, đóng gói theo quy cách, bàn giao cho nhân viên giao hàng hoặc đối tác vận chuyển. Trong khung giờ nhận dự kiến trên ứng dụng, người giao liên hệ Lan; cô kiểm tra và ký nhận.

**Kết thúc câu chuyện này:** đơn **giao thành công**. Quy trình B2 kết thúc ở trạng thái đã giao và đã thanh toán.

**Điểm cần nhớ khi đọc sơ đồ B2:**  
Quy trình không bắt đầu từ bước giao hàng tận nơi. Trình tự hợp lý là: **xác định và cam kết điều kiện giao** (địa chỉ, tồn hàng, hình thức vận chuyển, thanh toán) → **tạo đơn** → **soạn và đóng gói** → **giao đến khách**. Giao tận nơi chỉ là giai đoạn phía sau của cùng một quy trình.

---

## Chương 2 — Mai ở tỉnh: giao thường và thanh toán khi nhận hàng (B2, nhánh khác)

Mai đặt cùng tuýp kem nhưng giao về tỉnh. Ứng dụng **không** hiện giao 2 giờ — chỉ còn hình thức giao nhanh theo khu vực (thường vài ngày). Đơn dưới ngưỡng miễn phí vận chuyển tại nơi không có cửa hàng Hasaki nên Mai trả thêm phí theo bảng công bố. Cô chọn **thanh toán khi nhận hàng**.

Sau khi đặt, hệ thống vẫn tạo đơn. Kho hoặc cửa hàng soạn hàng và bàn giao đối tác vận chuyển. Hai ngày sau, nhân viên giao liên hệ Mai; cô kiểm tra kiện trước khi ký nhận (theo chính sách công bố: không đồng kiểm — khách nên quay video khi mở hàng nếu cần đối chiếu sau). Mai trả tiền mặt cho nhân viên giao.

**Kết thúc:** giao thành công; tiền thu hộ được đối soát về Hasaki.

**Điểm cần nhớ:** cùng quy trình B2, nhánh **không giao 2 giờ** và nhánh **thanh toán khi nhận** khác với trường hợp của Lan, nhưng vẫn theo cùng trình tự chính: tạo đơn → soạn hàng → giao hàng → kết thúc đơn.

---

## Chương 3 — Khi giao không thành và quy tắc 3 ngày (B2, ngoại lệ)

Lan đặt thêm một đơn giao 48 giờ vào giờ làm việc. Lần giao thứ nhất, nhân viên giao không liên lạc được với cô. Theo chính sách giao hàng công bố, Hasaki hoặc đơn vị vận chuyển sẽ **liên hệ để sắp xếp lại** hoặc hướng dẫn nhận hàng tại điểm giao nhận.

Nếu vẫn không liên lạc được trong **3 ngày**, phía Hasaki thông báo **hủy đơn** và hoàn các khoản Lan đã thanh toán trước trong vòng **30 ngày**.

**Điểm cần nhớ:** trên sơ đồ B2, lần giao không thành công chưa phải điểm kết thúc. Còn nhánh hẹn giao lại và nhánh hủy đơn có kiểm soát (kèm hoàn tiền nếu đã thanh toán trước).

---

## Chương 4 — Giao 2 giờ bị trễ: phiếu 100.000đ (B2, cam kết dịch vụ)

Một lần khác, Lan chọn NowFree. Giờ nhận dự kiến trên đơn là trước 16:00. Thực tế hàng tới 17:10, trạng thái cuối vẫn là giao thành công, và không thuộc trường hợp miễn trừ (thiên tai, Lan hẹn lại ngày nhận, sai số điện thoại…).

Theo chính sách vận chuyển 2 giờ, đủ điều kiện thì Lan được **phiếu mua hàng 100.000đ** (gắn tài khoản, không chuyển nhượng; có thể dùng cho dịch vụ Clinic theo trang hỗ trợ).

**Điểm cần nhớ:** với đơn giao 2 giờ, quy trình B2 chưa nhất thiết kết thúc ngay khi đã giao thành công. Nếu giao muộn hơn giờ dự kiến và đủ điều kiện theo chính sách, còn nhánh **bù đắp bằng phiếu mua hàng**.

---

## Chương 5 — Đúng hàng nhưng “sai màu”: bước sang quy trình B4

Đây là tình huống gắn trực tiếp ví dụ trên trang đổi trả Hasaki:

> *“Sản phẩm không đúng như yêu cầu của khách hàng do Hasaki soạn sai sản phẩm hoặc lấy nhầm tông màu, loại sản phẩm.”*  
> — [Đổi trả – hoàn tiền](https://hotro.hasaki.vn/doi-tra-hoan-tien.html)

Lan đặt **son tông hồng đất**. Đơn giao thành công (B2 đã đóng). Khi mở hộp (có quay video), bên trong là **tông đỏ**. Tem còn nguyên, chưa dùng.

Lúc này **không còn là B2**. Lan bắt đầu **B4 — đổi trả**:

1. Cô liên hệ hotline / đến cửa hàng Hasaki gần nhà (Thành phố Hồ Chí Minh được khuyến khích mang tới showroom), nêu lý do *giao nhầm tông*, mang theo đơn và **quà tặng kèm** nếu lúc mua có quà.  
2. Nhân viên làm **một lần thẩm định** theo bảng chính sách: còn trong **30 ngày**? Mua từ Hasaki? Không thuộc loại trừ? Nguyên nhân (ở đây: Hasaki soạn sai / nhầm tông)?  
3. Kết luận đạt điều kiện → trong 1–30 ngày được **đổi mới** hoặc **trả không thu phí**.  
4. Tại cửa hàng, Lan được xem và chọn đúng tông hồng đất còn hàng; hoặc nếu muốn trả tiền, hoàn theo cách đã thanh toán (tiền mặt / chuyển khoản / cổng thanh toán…).

**Kết thúc tốt:** đổi đúng tông — B4 kết thúc ở “đổi hàng xong”.  
Nếu trả tiền và thanh toán trước bằng cổng thanh toán: B4 kết thúc ở “hoàn tiền xong” sau thời hạn công bố (ví dụ vài ngày làm việc tùy loại thẻ).

**Điểm then chốt về ranh giới hai quy trình:**  
- B2 kết thúc khi đơn **đã giao thành công** hoặc **đã hủy** trong quá trình giao.  
- Việc phát hiện sai hàng / sai tông **sau khi nhận** thuộc **quy trình B4** (đổi trả), dù nguyên nhân có thể phát sinh từ bước soạn hàng trong B2.

---

## Chương 6 — Cùng chính sách đổi trả, nhiều kết quả khác nhau (B4)

Cùng trang [đổi trả](https://hotro.hasaki.vn/doi-tra-hoan-tien.html), bạn của Lan gặp các tình huống khác. Các tình huống này giúp hiểu **bảng quyết định trong một lần thẩm định** (và vài nhánh luồng thật: cửa hàng / bưu điện, đổi / trả, hình thức hoàn) — không phải mỗi dòng dưới đây là một cổng XOR riêng trên sơ đồ:

| Câu chuyện ngắn | Nhóm theo chính sách | Kết quả thường gặp |
|-----------------|----------------------|--------------------|
| Tuýp serum **bị nứt** khi nhận, lỗi do vận chuyển | Lỗi phía vận chuyển / nhà cung cấp, trong 30 ngày | Đổi mới hoặc trả không thu phí |
| Kem **gần hết hạn dùng** rõ rệt | Được nêu trong trường hợp nhận đổi trả | Đổi / trả theo chính sách |
| Đổi ý muốn tông khác, **còn nguyên hộp–tem, chưa dùng**, trong 30 ngày | Sản phẩm không lỗi | **Đổi mới** (không phải mọi trường hợp đều hoàn tiền theo bảng tóm tắt) |
| Đã **bôi thử** son một lần rồi muốn trả | Lỗi / tình trạng phía người dùng hoặc đã sử dụng | **Không hỗ trợ** đổi trả |
| Muốn trả **quà tặng** kèm đơn | Thuộc trường hợp không áp dụng | **Không hỗ trợ** |
| Đến ngày **thứ 35** mới mang đi đổi | Quá 30 ngày (từ ngày 31 trở đi) | **Không hỗ trợ** |
| Mai ở tỉnh: gửi bưu điện sản phẩm lỗi + báo mã vận đơn | Cách thức đổi trả công bố | Hasaki nhận hàng rồi xử lý đổi / gửi lại hoặc hoàn |

Mỗi dòng trên là **một kết quả có thể** của hoạt động thẩm định (hoặc của cổng đổi/trả / kênh tiếp nhận). Chi tiết vẽ: [core_bpmn.md](./core_bpmn.md) phần B.

---

## Chương 7 — Nhìn toàn cảnh: hai quy trình nối nhau thế nào?

```text
  Lan mở ứng dụng → chọn hàng → chọn giao 2H/48H → đặt hàng
           │
           ▼
     ┌─────────── B2: Đơn online & giao hàng ───────────┐
     │  Cam kết → Tạo đơn → Soạn → Giao → (Hẹn lại/Hủy) │
     │  Có thể: phiếu 100k nếu 2H trễ đủ điều kiện        │
     └─────────────────────┬────────────────────────────┘
                           │
              Đã giao thành công (hoặc hủy xong)
                           │
         Nếu sau đó phát hiện sai tông / lỗi / muốn đổi…
                           ▼
     ┌─────────── B4: Đổi trả & hoàn tiền ──────────────┐
     │  Tiếp nhận → Thẩm định 30 ngày → Nhận/kiểm hàng  │
     │  → Đổi mới  /  Hoàn tiền  /  Từ chối              │
     └──────────────────────────────────────────────────┘
```

**Tóm tắt cho người mới tiếp cận:**  
- **B2:** xử lý đơn từ khi khách **bấm Đặt hàng** (có mã đơn) đến khi giao thành công (đúng cam kết thời gian và hàng hóa), hoặc hủy đơn có kiểm soát khi không giao được. Xem hàng trên ứng dụng mà không đặt **không** mở B2.  
- **B4:** sau khi khách đã nhận hàng, nếu có nhu cầu đổi/trả trong khung 30 ngày và đủ điều kiện chính sách, Hasaki thực hiện đổi hàng hoặc hoàn tiền; nếu không đủ điều kiện thì từ chối có giải thích.

---

## Gợi ý dùng file này trong báo cáo / thuyết trình

1. Mở đầu slide bằng **Chương 1 + Chương 5** (đặt 2 giờ → nhận nhầm tông → đổi trả): một mạch dễ nhớ.  
2. Khi chỉ sơ đồ BPMN B2: nhắc lại Chương 1–4.  
3. Khi chỉ sơ đồ BPMN B4: nhắc lại Chương 5–6 và dẫn đúng câu *soạn sai / nhầm tông màu* từ trang hỗ trợ.  
4. Nhấn mạnh ranh giới (*process boundary*): đơn đã giao thành công vẫn có thể phát sinh đổi trả; khi đó chuyển sang quy trình B4, không kéo dài B2. Thời gian xem hàng trước Đặt hàng không thuộc phân tích định lượng (*quantitative analysis*) B2.

---

## Tài liệu liên quan trong thư mục

| File | Đọc tiếp khi… |
|------|----------------|
| [core.md](./core.md) | Cần định nghĩa đầy đủ năm quy trình cốt lõi và phân tích |
| [ba_model_b2_b4.md](./ba_model_b2_b4.md) | Cần quy tắc nghiệp vụ và giai đoạn chi tiết |
| [core_bpmn.md](./core_bpmn.md) | Cần vẽ cổng điều kiện trên sơ đồ |
| [Đổi trả – hoàn tiền (Hasaki)](https://hotro.hasaki.vn/doi-tra-hoan-tien.html) | Đối chiếu từng tình huống Chương 5–6 với chính sách gốc |
