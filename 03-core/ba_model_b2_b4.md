# Phân tích nghiệp vụ chi tiết — Quy trình B2 và B4

**Vai trò tài liệu:** làm rõ nghiệp vụ hai quy trình cốt lõi (*core processes*) đã chọn để vẽ sơ đồ BPMN, theo góc nhìn phân tích quy trình (*process analysis*) và phân tích nghiệp vụ.  
**Phương pháp:** (1) Chính sách công bố của Hasaki = quy tắc nghiệp vụ (*business rules*) quan sát được; (2) Chuẩn vận hành bán lẻ / giao nhanh / đổi trả mỹ phẩm = bổ sung bước khi Hasaki không công bố sổ tay nội bộ; (3) Tách rõ **thông tin công bố** và **suy luận theo chuẩn ngành**.  
**Ngày:** 08/08/2026  
**File liên quan:** [core_bpmn.md](./core_bpmn.md), [core.md](./core.md), [research.md](../02-research/research.md).

---

## 0. Nguồn và cách dùng

### 0.1. Thông tin công bố Hasaki (ưu tiên khi mâu thuẫn)

| Chủ đề | Đường dẫn |
|--------|-----------|
| Đặt hàng, lựa chọn vận chuyển và thanh toán | https://hotro.hasaki.vn/huong-dan-dat-hang.html |
| Giao nhanh 2 giờ (NowFree) | https://hotro.hasaki.vn/van-chuyen-2h.html |
| Quy trình giao hàng, phí ship, giao không thành, đối tác vận chuyển, đơn trên 5 triệu | https://hotro.hasaki.vn/quy-trinh-giao-hang.html |
| Đổi trả 30 ngày, hoàn tiền | https://hotro.hasaki.vn/doi-tra-hoan-tien.html |

### 0.2. Chuẩn ngành dùng để bổ sung bước chưa công bố

| Khung | Áp dụng | Ý chính bằng tiếng Việt |
|-------|---------|-------------------------|
| Chu kỳ xử lý đơn: tạo đơn → sẵn sàng soạn → soạn–đóng gói–bàn giao → giao đến khách (*order cycle*) | B2 | Đo thời gian chu kỳ (*cycle time*) từ sau Đặt hàng (không gồm xem hàng trên ứng dụng); chia giai đoạn trên sơ đồ |
| Giao trong ngày / vài giờ | B2 NowFree | Giờ cắt đơn, hàng đợi ưu tiên, cửa sổ lấy hàng của đơn vị giao, cam kết và bù đắp |
| Lấy hàng từ cửa hàng giao đơn online | B2 | Tồn khả dụng → soạn → đóng gói → giao → xác nhận đã giao |
| Đổi trả ngành mỹ phẩm | B4 | Tiếp nhận → thẩm định → nhận hàng → kiểm tra → xử lý hàng trả → đổi hoặc hoàn |

---

# Phần I — Quy trình B2: Đơn online và giao hàng

## I.1. Mục đích nghiệp vụ

| | |
|--|--|
| **Vấn đề cần giải quyết** | Khách muốn nhận đúng sản phẩm, đúng thời gian cam kết, thanh toán rõ ràng; Hasaki muốn hoàn tất đơn với chi phí giao kiểm soát và tồn tại điểm lấy hàng chính xác. |
| **Giá trị với khách** | Cam kết rõ → nhận hàng → thanh toán xong. |
| **Giá trị với doanh nghiệp** | Doanh thu ghi nhận; giao đúng–đủ–đúng hạn; giảm hủy và giao lại; giảm chi phí phiếu bù. |
| **Trong phạm vi** | Sau khi khách bấm Đặt hàng: tạo đơn, thanh toán, phân bổ–soạn–đóng gói, **giao nhanh 2 giờ hoặc giao thường**, ngoại lệ, bù khi trễ 2 giờ, hủy có hoàn. Các bước trên màn hình trước khi đặt (địa chỉ, đề xuất cam kết, chọn vận chuyển / thanh toán) có thể hiện trên sơ đồ nhưng **chưa** mở lần chạy nếu chưa Đặt hàng. |
| **Ngoài phạm vi** | Duyệt ứng dụng / xem hàng / giỏ bỏ dở; hoạch định tồn chiến lược (A3); đổi trả sau khi đã nhận (B4); Clinic (B3); đơn trên sàn (quy tắc sàn khác). |
| **Một quy trình, không hai core** | Không tách “tiếp nhận đơn” và “giao 2H” thành hai quy trình cốt lõi trên kiến trúc: cùng mã đơn, cùng cam kết dịch vụ với khách. Giao 2 giờ / giao thường là **nhánh** trong B2. Chi tiết lập luận: [research.md](../02-research/research.md) §4.3. Tập trung activity theo **vai trò nghiệp vụ**, không theo tầng kỹ thuật. |

## I.2. Bảng nhà cung cấp – đầu vào – quy trình – đầu ra – khách hàng (*SIPOC*)

| Bên cung cấp | Đầu vào | Quy trình | Đầu ra | Khách hàng nhận kết quả |
|--------------|---------|-----------|--------|-------------------------|
| Khách | Giỏ hàng và lựa chọn trên màn hình đặt hàng (trước khi đặt); sau Đặt hàng: xác nhận / thanh toán | B2 | Đơn hoàn tất hoặc hủy có kiểm soát | Khách đặt online |
| Hệ thống tồn và quản lý đơn | Lựa chọn vận chuyển, giờ nhận dự kiến, phí, giữ tồn | | Mã đơn, trạng thái | Chăm sóc khách hàng / kho |
| Kho – cửa hàng | Tồn vật lý, nhân sự soạn | | Kiện đã đóng gói | Đối tác vận chuyển |
| Cổng thanh toán / đối tác vận chuyển | Kết quả thanh toán, năng lực giao | | Kết quả thanh toán, xác nhận đã giao / tiền thu hộ | Bộ phận tài chính Hasaki |

## I.3. Các giai đoạn chu kỳ đơn — ánh xạ Hasaki

```text
[1] Tiếp nhận và cam kết giao hàng
[2] Tạo đơn và sẵn sàng soạn hàng
[3] Soạn – đóng gói – bàn giao
[4] Giao đến khách
[5] Xử lý ngoại lệ và đóng đơn
```

| Giai đoạn | Thực hành ngành | Thông tin công bố Hasaki | Suy luận khi vẽ sơ đồ |
|-----------|-----------------|--------------------------|----------------------|
| Cam kết | Địa lý + tồn + giờ cắt → hiện thời gian cam kết | Vùng áp dụng + tồn kho gần + bảng giờ đặt→nhận; phí 90.000đ | Làn Hệ thống kiểm trước khi khách chọn |
| Giao nhanh | Công bố giờ cắt rõ | Bảng giờ; giao đến 18 giờ, cả tuần | So sánh giờ giao thực tế với giờ dự kiến ở cổng cuối |
| Sẵn sàng soạn | Tự động sau thanh toán; ưu tiên đơn nhanh | Thanh toán trước hoặc khi nhận; đơn trên 5 triệu chỉ trả trước | Đơn 2 giờ vào hàng đợi ưu tiên |
| Soạn–đóng gói | Đường đi lấy hàng, quét mã, kiểm trước khi giao | Đóng gói theo chuẩn Hasaki | Cổng “còn hàng lúc soạn?” |
| Giao | Lộ trình, liên hệ, xác nhận đã giao, thu hộ | Giao; fail → hẹn lại; 3 ngày → hủy + hoàn; đối tác thu hộ | Các cổng giao thành công / hẹn lại / đổi địa chỉ |
| Đóng đơn | Đúng giờ cam kết; bù đắp | Phiếu 100.000đ nếu trễ đủ điều kiện | Cổng xét phiếu |

## I.4. Danh mục quy tắc nghiệp vụ (*business rules* — gắn cổng trên sơ đồ)

| Mã | Quy tắc | Nguồn | Cổng |
|----|---------|-------|------|
| QĐ-B2-01 | Nội thành Thành phố Hồ Chí Minh và Hà Nội: có thể có 2 giờ và 48 giờ; nơi khác: giao nhanh thường | Công bố đặt hàng | G1 |
| QĐ-B2-02 | NowFree miễn phí nếu đơn ≥ 90.000đ; dưới 90.000đ phí 10.000đ | Công bố 2 giờ | Tính phí |
| QĐ-B2-03 | NowFree khi địa chỉ thuộc danh sách và hàng sẵn tại kho gần | Công bố 2 giờ | G1 |
| QĐ-B2-04 | Khách phải chọn hình thức 2 giờ | Công bố | G2 |
| QĐ-B2-05 | Đơn trên 5.000.000đ → chỉ thanh toán trước | Công bố giao hàng | G3 |
| QĐ-B2-06 | Thanh toán khi nhận hoặc trả trước (nếu không bị QĐ-05) | Công bố | G4 |
| QĐ-B2-07 | Hệ thống tạo đơn khi bấm Đặt hàng | Công bố | Tạo đơn |
| QĐ-B2-08 | Giao thường: 24–48 giờ nội thành; 3–6 ngày tỉnh | Công bố | Nhánh không 2 giờ |
| QĐ-B2-09 | Giao không thành lần 1 → liên hệ hẹn lại / điểm nhận | Công bố | G7 → chăm sóc khách hàng |
| QĐ-B2-10 | Không liên lạc 3 ngày → hủy + hoàn trong 30 ngày nếu đã trả | Công bố | G8 |
| QĐ-B2-11 | Địa điểm không giao được → đổi địa chỉ hoặc hủy | Công bố | G9 |
| QĐ-B2-12 | Không đồng kiểm; khách nên quay video khi mở | Công bố | Ràng buộc khi nhận hàng |
| QĐ-B2-13 | NowFree trễ hơn giờ dự kiến + giao thành công + không miễn trừ → phiếu 100.000đ | Công bố | G10 |
| QĐ-B2-14 | Phí ship theo có/không cửa hàng (ngưỡng 90.000 / 249.000đ) | Công bố | Tính phí |
| QĐ-B2-15 | Đơn 2 giờ được ưu tiên soạn | Suy luận ngành | Chú thích bước soạn |
| QĐ-B2-16 | Giữ tồn lúc cam kết; xác nhận lúc soạn; hết hàng → ngoại lệ | Suy luận ngành | G6 |
| QĐ-B2-17 | Kiểm địa chỉ trước cam kết giảm giao thất bại | Suy luận ngành | Gộp vào xác định vùng |

## I.5. Ma trận phân công trách nhiệm (rút gọn)

Ký hiệu: C = chịu trách nhiệm chính; T = thực hiện; H = được hỏi ý; N = được thông báo.

| Nhóm việc | Hệ thống | Kho/cửa hàng | Đối tác vận chuyển | Chăm sóc khách hàng | Khách |
|-----------|----------|--------------|--------------------|---------------------|-------|
| Cam kết vận chuyển / tồn / phí | C/T | H | — | — | H |
| Tạo đơn / thanh toán | C/T | — | — | N | T (thao tác) |
| Soạn – đóng gói | H | C/T | N | N | — |
| Giao / thu hộ | N | N | C/T | H | T (nhận) |
| Hẹn lại / hủy 3 ngày | H | H | H | C/T | H |
| Phiếu khi giao 2 giờ trễ | H | — | — | C/T | N |

## I.6. Trạng thái đơn (để đặt tên sự kiện kết thúc)

```text
Đang chọn hàng → Đã đặt
  → Chờ thanh toán trước | Đã thanh toán | Cho phép thu hộ
  → Đã phân bổ / Đưa vào soạn → Đang soạn → Đã đóng gói → Đã bàn giao
  → Đang giao → Đã giao (thành công)
       ↘ Giao không thành → Hẹn lại → …
       ↘ Không giao được điểm → Đổi địa chỉ | Hủy
  → Đã hủy (+ Đã hoàn tiền nếu trả trước)
```

Trên sơ đồ BPMN chỉ cần hai kết thúc chính: **Giao thành công** và **Đơn bị hủy**.

## I.7. Phân loại ngoại lệ

| Mã | Tình huống | Cách xử lý chuẩn | Cổng |
|----|------------|------------------|------|
| N1 | Thanh toán thất bại | Thử lại / bỏ | G5 |
| N2 | Hết hàng lúc soạn | Đổi điểm / đổi sản phẩm / hủy | G6 |
| N3 | Giao không thành | Hẹn lại trong 3 ngày | G7, G8 |
| N4 | Địa điểm không phục vụ | Đổi địa chỉ / hủy | G9 |
| N5 | Trễ so với cam kết 2 giờ | Xét phiếu 100.000đ | G10 |
| N6 | Bất khả kháng / lỗi phía khách | Không cấp phiếu | G10 nhánh Không |

## I.8. Chỉ số đo lường đề xuất (*process performance measures*)

Đo trên **đơn đã tạo** (sau Đặt hàng). Không đo thời gian xem / lựa hàng trên ứng dụng — xem [research.md](../02-research/research.md) §4.3.

| Chỉ số | Cách hiểu | Giai đoạn |
|--------|-----------|-----------|
| Tỷ lệ đúng giờ cam kết | Phần trăm giao không muộn hơn giờ dự kiến lúc đặt | Giao đến khách |
| Đúng hàng – đủ – đúng hạn | Giao đúng sản phẩm, đủ số lượng, đúng hạn | Đóng đơn |
| Giao thành công lần đầu | Phần trăm thành công ở lần giao thứ nhất | Giao |
| Thời gian tạo đơn → bắt đầu soạn | Độ trễ trước khi lấy hàng *(đoạn thời gian chu kỳ)* | Sẵn sàng soạn |
| Thời gian soạn → bàn giao | Hiệu quả kho/cửa hàng | Soạn–đóng gói |
| Thời gian chu kỳ tạo đơn → nhận | Tổng từ sau Đặt hàng đến giao thành công | Toàn lần chạy |
| Tỷ lệ hủy (3 ngày / hết hàng) | — | Ngoại lệ |
| Chi phí phiếu bù | Tổng phiếu 100.000đ / doanh thu đơn 2 giờ | Đóng đơn |

## I.9. Quyết định khi vẽ sơ đồ

1. Nên vẽ từ bước địa chỉ và kiểm điều kiện để hiện đủ cổng cam kết; đây là **bước trên màn hình trước khi đặt** — sự kiện bắt đầu lần chạy là khách bấm Đặt hàng / đơn được tạo. Định lượng chỉ trên lần chạy đã Đặt hàng.  
2. Làn Hệ thống chịu cam kết, thanh toán và trạng thái.  
3. Đối tác vận chuyển là làn hoặc bể bơi riêng — không vẽ nội bộ hãng ship.  
4. Cổng hết hàng lúc soạn: ghi chú suy luận ngành.  
5. Cổng phiếu 100.000đ chỉ trên nhánh đơn 2 giờ đã giao thành công.

Chi tiết danh sách hoạt động và cổng B2: [core_bpmn.md](./core_bpmn.md) phần A.

---

# Phần II — Quy trình B4: Đổi trả hoặc hoàn tiền (*Return-to-Resolve*)

## II.1. Mục đích nghiệp vụ

| | |
|--|--|
| **Vấn đề** | Sau khi mua, khách muốn đổi/trả; Hasaki phải áp dụng cửa sổ 30 ngày và điều kiện tem/hình thức (đặc thù mỹ phẩm) để bảo vệ biên lợi nhuận và tuân thủ. |
| **Giá trị với khách** | Có kết luận rõ: đổi / hoàn / từ chối có lý do trong thời hạn. |
| **Giá trị với doanh nghiệp** | Giữ niềm tin; giảm lạm dụng; tối ưu xử lý hàng trả; kiểm soát chi phí thu hồi hàng. |
| **Trong phạm vi** | Tiếp nhận → thẩm định → nhận hàng → quyết **đổi hàng** hoặc **trả và hoàn** → xử lý hàng trả. |
| **Ngoài phạm vi** | Khiếu nại không phải đổi trả (B5); đơn đang giao (B2); bảo hành ngoài chính sách Hasaki. |
| **Tên chuỗi đầu–cuối** | Tiếng Việt: *Đổi trả hoặc hoàn tiền*; tiếng Anh: *Return-to-Resolve* (không dùng *Return-to-Refund*). |

## II.2. Bảng nhà cung cấp – đầu vào – quy trình – đầu ra – khách hàng (*SIPOC*)

| Bên cung cấp | Đầu vào | Quy trình | Đầu ra | Khách hàng nhận kết quả |
|--------------|---------|-----------|--------|-------------------------|
| Khách | Yêu cầu, sản phẩm, chứng từ, quà kèm | B4 | Đổi / hoàn / từ chối | Khách |
| Hệ thống đơn / máy bán hàng | Lịch sử đơn, ngày nhận, cách thanh toán | | Quyết định theo chính sách | Nhân viên / chăm sóc khách hàng |
| Kho | Hàng trả, tồn hàng đổi | | Phiếu đổi / hàng nhập lại hoặc loại | Kho / ngành hàng |
| Cổng thanh toán / ngân hàng | Lệnh hoàn | | Tiền về khách | Khách |

## II.3. Sáu giai đoạn đổi trả ngành — ánh xạ Hasaki

```text
1. Tiếp nhận → 2. Thẩm định điều kiện
→ 3. Đưa hàng về (mang tới cửa hàng / gửi bưu điện) → 4. Nhận và kiểm tra
→ 5. Xử lý hàng trả (bán lại / loại / trả nhà cung cấp)
→ 6. Kết toán (đổi hàng / hoàn tiền / từ chối)
```

| Giai đoạn | Thực hành ngành | Thông tin công bố Hasaki | Suy luận |
|-----------|-----------------|--------------------------|----------|
| Tiếp nhận | Cổng tự phục vụ, lý do chuẩn | Báo nhân viên + lý do + số điện thoại / địa chỉ; Thành phố Hồ Chí Minh ưu tiên cửa hàng; tỉnh gửi bưu điện | Cổng chọn kênh tiếp nhận |
| Thẩm định | Quy tắc theo cửa sổ thời gian, vệ sinh, loại trừ | Bảng 30 ngày; lỗi nhà sản xuất / vận chuyển / cận hạn / soạn sai; loại trừ khuyến mãi đặc biệt, quà, tem, đã dùng… | **Một** hoạt động thẩm định + bảng quyết định; cổng X3 = Đạt / Từ chối |
| Vận chuyển chiều ngược | Nhãn gửi, đơn vị vận chuyển | Tự mang hoặc tự gửi + báo mã | Khách mang/gửi hàng |
| Kiểm tra | Tem, lô, còn bán được không | “Nguyên hộp, tem, chưa dùng”; lỗi nhà sản xuất / vận chuyển | Tại cửa hàng thường **gộp trong thẩm định**; gửi bưu điện: hoạt động nhận rồi đối chiếu |
| Xử lý hàng trả | Bán lại hoặc hủy (hàng đã mở thường không bán lại) | Không công bố chi tiết | Nên có trên sơ đồ sau khi chấp nhận |
| Kết toán | Ưu tiên đổi hơn hoàn thuần | Đổi mới; trả không phí nếu lỗi nhà sản xuất; hoàn theo tiền mặt / chuyển khoản / cổng thanh toán / phiếu quà | Cổng đổi/trả và hình thức hoàn |

**Đặc thù mỹ phẩm:** hàng đã mở hoặc mất tem thường **không** đưa lại kệ bán vì vệ sinh. Chính sách Hasaki phản ánh qua điều kiện “chưa sử dụng / không bóc tem” với trường hợp đổi ý; trường hợp lỗi nhà sản xuất vẫn được đổi/trả.

## II.4. Danh mục quy tắc nghiệp vụ (*business rules*)

Tiêu chí trong bảng 30 ngày (QĐ-B4-01 … 06) gắn **hoạt động thẩm định** và bảng quyết định §II.5 — không mỗi tiêu chí một cổng XOR. Cột “Cổng / chỗ trên sơ đồ” chỉ ghi khi luồng thật sự rẽ nhánh.

| Mã | Quy tắc | Nguồn | Cổng / chỗ trên sơ đồ |
|----|---------|-------|------------------------|
| QĐ-B4-01 | Cửa sổ 30 ngày từ mua hoặc nhận hàng (từ 01/06/2024) | Công bố | Trong hoạt động thẩm định (§II.5) |
| QĐ-B4-02 | Phải mua từ Hasaki | Công bố | Trong hoạt động thẩm định (§II.5) |
| QĐ-B4-03 | Loại trừ: quà tặng, khuyến mãi đặc biệt, quá hạn, bóc tem, đã dùng, hỏng bao bì do khách | Công bố | Trong hoạt động thẩm định (§II.5) |
| QĐ-B4-04 | Lỗi người dùng → không hỗ trợ | Công bố | Trong hoạt động thẩm định (§II.5) |
| QĐ-B4-05 | Lỗi nhà sản xuất / vận chuyển / cận–hết hạn / soạn sai → đổi mới hoặc trả không phí (trong hạn) | Công bố | Thẩm định đạt → X5 Đổi hoặc Trả |
| QĐ-B4-06 | Không lỗi (đổi ý) trong hạn + đủ hình thức → đổi mới | Công bố | Thẩm định đạt → X5 Đổi |
| QĐ-B4-07 | Đổi sản phẩm chính → mang quà tặng kèm | Công bố | X2 hồ sơ đủ / bổ sung |
| QĐ-B4-08 | Thành phố Hồ Chí Minh khuyến khích cửa hàng; tỉnh gửi bưu điện | Công bố | X1 |
| QĐ-B4-09 | Hoàn tiền mặt nếu đã trả tiền mặt tại cửa hàng | Công bố | X7 |
| QĐ-B4-10 | Chuyển khoản 3–5 ngày làm việc nếu trả bằng thẻ ngân hàng | Công bố | X7 |
| QĐ-B4-11 | Cổng thanh toán: 3–8 ngày thẻ nội địa; 15–90 ngày thẻ quốc tế; hoặc trừ đơn sau | Công bố | X7 |
| QĐ-B4-12 | Phiếu quà → chuyển mã sang đơn sau | Công bố | X7 |
| QĐ-B4-13 | Trả tại nhà: hoàn sau khi Hasaki nhận được hàng | Công bố | Thứ tự: nhận hàng trước hoạt động hoàn tiền |
| QĐ-B4-14 | Đổi hàng cần còn tồn sản phẩm thay thế | Suy luận ngành | X6 |
| QĐ-B4-15 | Tranh chấp / ngoại lệ → quản lý duyệt | Suy luận vận hành | X4 |
| QĐ-B4-16 | Sau nhận: bán lại nếu còn điều kiện; không thì loại | Suy luận ngành mỹ phẩm | Hoạt động xử lý hàng trả |

## II.5. Bảng quyết định thẩm định (*decision table* — rút gọn)

Dùng **trong** hoạt động *Thẩm định theo chính sách đổi trả* trên sơ đồ. Kết quả bảng → cổng X3 (Đạt / Từ chối), không vẽ mỗi cột thành một cổng.

| Trong 30 ngày? | Từ Hasaki? | Loại trừ? | Ai gây lỗi? | Hình thức / lỗi nhà sản xuất–vận chuyển? | Kết quả |
|----------------|------------|-----------|-------------|------------------------------------------|---------|
| Không | * | * | * | * | Từ chối |
| Có | Không | * | * | * | Từ chối |
| Có | Có | Có | * | * | Từ chối |
| Có | Có | Không | Người dùng | * | Từ chối |
| Có | Có | Không | Nhà sản xuất / vận chuyển / sai / cận hạn | * | Cho đổi hoặc trả |
| Có | Có | Không | Không lỗi (đổi ý) | Hình thức đạt | Cho **đổi** |
| Có | Có | Không | Không lỗi | Hình thức không đạt | Từ chối |

## II.6. Ma trận phân công trách nhiệm

| Nhóm việc | Nhân viên / chăm sóc khách hàng | Quản lý | Kho | Kế toán | Khách |
|-----------|----------------------------------|---------|-----|---------|-------|
| Tiếp nhận và thẩm định | Chịu trách nhiệm chính / thực hiện | Được hỏi | — | — | Thực hiện |
| Duyệt ngoại lệ | Thực hiện | Chịu trách nhiệm chính | — | — | Được hỏi |
| Nhận / xuất hàng đổi | Được hỏi | — | Chịu trách nhiệm chính | — | Thực hiện (mang/gửi) |
| Hoàn tiền | Được hỏi | Được thông báo | Được thông báo | Chịu trách nhiệm chính | Được thông báo |
| Xử lý hàng trả | Được thông báo | Được hỏi | Chịu trách nhiệm chính | — | — |

## II.7. Trạng thái yêu cầu đổi trả

```text
Đã gửi yêu cầu → Đang thẩm định → (Từ chối | Được chấp nhận)
Được chấp nhận → Chờ khách gửi/mang hàng → Đã nhận → Đã kiểm tra
  → (Đổi hàng xong | Hoàn tiền xong)
Đã kiểm tra → Đã xử lý hàng trả (song song / ghi nhận)
```

Sự kiện kết thúc trên sơ đồ: **Từ chối** | **Đổi hàng xong** | **Hoàn tiền xong**.

## II.8. Ngoại lệ thường gặp

| Mã | Tình huống | Xử lý |
|----|------------|-------|
| N1 | Thiếu chứng từ / thiếu quà kèm | Yêu cầu bổ sung rồi thẩm định lại |
| N2 | Không còn hàng để đổi | Đề xuất trả tiền hoặc chờ hàng |
| N3 | Khách tranh chấp khi bị từ chối | Chuyển quản lý |
| N4 | Hoàn tiền cổng chậm / lỗi | Thử lại + thông báo thời hạn |
| N5 | Hàng gửi thất lạc | Chăm sóc khách hàng phối hợp đơn vị vận chuyển |

## II.9. Chỉ số đo lường đề xuất (*process performance measures*)

| Chỉ số | Ý nghĩa |
|--------|---------|
| Thời gian từ yêu cầu đến kết luận | Phút tại cửa hàng / ngày nếu gửi bưu điện và hoàn tiền |
| Tỷ lệ xử lý xong trong một lần tiếp xúc | — |
| Tỷ lệ từ chối | Theo dõi vừa chống lạm dụng vừa kiểm tra đào tạo |
| Tỷ lệ đổi so với hoàn | Đổi giúp giữ doanh thu hơn hoàn thuần |
| Tỷ lệ hoàn đúng hạn công bố | Theo từng cách thanh toán gốc |
| Tỷ lệ hàng trả bán lại được | Chất lượng xử lý hàng trả |

## II.10. Quyết định khi vẽ sơ đồ

1. Thẩm định điều kiện **trước** khi tốn công vận chuyển chiều ngược khi có thể.  
2. **Một** hoạt động thẩm định + bảng §II.5; cổng sau thẩm định chỉ hỏi Đạt / Từ chối — không xẻ 30 ngày / tem / loại trừ thành chuỗi XOR.  
3. Tách nhánh **Đổi** và **Trả** sau khi đạt điều kiện.  
4. Có bước xử lý hàng trả sau khi nhận — ghi chú suy luận ngành.  
5. Cổng hình thức hoàn bám **cách khách đã thanh toán**, không gộp một việc “hoàn tiền” chung.  
6. Có cổng kênh tiếp nhận (cửa hàng / gửi tỉnh) và vòng bổ sung hồ sơ nếu thiếu chứng từ / quà kèm.  
7. Ưu tiên đúng nghiệp vụ hơn số cổng; rubik >7 không phải lý do để tách checklist.

---

## III. Khoảng trống cần xác minh thực địa (không bịa trên sơ đồ)

| Khoảng trống | Ảnh hưởng | Cách thể hiện trên mô hình |
|--------------|-----------|----------------------------|
| Thuật toán chọn điểm lấy / tách giỏ hàng | Chi tiết cổng hết hàng | Một nhánh “xử lý hết hàng” chung |
| Tỷ lệ lấy từ cửa hàng so với tổng kho | Tên làn kho | Gọi là “điểm lấy hàng kho/cửa hàng” |
| Giao nội bộ hay thuần đối tác | Bể bơi | “Đối tác vận chuyển / giao hàng” |
| Mức tiền nhân viên được tự duyệt đổi trả | Cổng quản lý | Có làn Quản lý |
| Hoàn không cần nhận hàng với đơn giá trị thấp | Không thấy trên chính sách Hasaki | **Không vẽ** |
| Cổng đổi trả tự phục vụ trên ứng dụng | Chưa rõ | Tiếp nhận qua nhân viên / tổng đài / cửa hàng |

---

## IV. Đồng bộ tài liệu trong thư mục

| File | Nội dung liên quan |
|------|-------------------|
| [core_bpmn.md](./core_bpmn.md) | Danh sách phần tử, quy tắc → cổng, giai đoạn, xử lý hàng trả |
| [core.md](./core.md) | Hồ sơ B2/B4, phân tích định tính và định lượng |
| [research.md](../02-research/research.md) | Ghi chú mức mô hình = thông tin công bố + suy luận ngành |

---

## Tài liệu ngành đã tham khảo

1. Phân rã chu kỳ xử lý đơn (thời gian tạo đơn → soạn → giao)  
2. Hướng dẫn vận hành giao trong ngày / vài giờ  
3. Mô hình lấy hàng từ cửa hàng giao đơn online  
4. Khung giao chặng cuối  
5. Thực hành đổi trả ngành mỹ phẩm (tiếp nhận, kiểm tra, xử lý hàng trả, ưu tiên đổi)  

Đường dẫn chi tiết từng bài đã dùng khi nghiên cứu được liệt kê trong [research.md](../02-research/research.md) phần tài liệu tham khảo.
