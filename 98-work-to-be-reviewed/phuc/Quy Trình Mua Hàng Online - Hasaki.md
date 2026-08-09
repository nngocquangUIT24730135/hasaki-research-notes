# **Báo Cáo Phân Tích Và Mô Hình Hóa Quy Trình Mua Hàng Trực Tuyến Tại Hasaki.vn**

Lưu ý học thuật: Nội dung dưới đây được xây dựng dựa trên các chính sách công khai của Hasaki về đặt hàng, thanh toán, vận chuyển và đổi trả sản phẩm, kết hợp với các thông lệ quản trị quy trình nghiệp vụ (Business Process Management \- BPM) trong lĩnh vực bán lẻ thương mại điện tử. Một số bước xử lý nội bộ về hệ thống quản lý đơn hàng (OMS) và kiểm soát giao dịch được giả định hợp lý nhằm phục vụ mục đích mô hình hóa BPMN và phân tích vận hành.

## **Chương 2\. Hệ thống quy trình nghiệp vụ mua hàng online**

### **2.1. Thông tin chung**

Tên quy trình: Quy trình mua hàng trực tuyến (Online Purchasing Process).  
Nhóm quy trình: Quy trình cốt lõi (Core Process).  
Trong mô hình kinh doanh thương mại điện tử (TMĐT) bán lẻ mỹ phẩm của Hasaki, quy trình mua hàng trực tuyến đóng vai trò là "xương sống" nghiệp vụ. Quy trình này trực tiếp tiếp nhận nhu cầu mua sắm của khách hàng trên kênh số, chuyển đổi các tương tác duyệt web hoặc ứng dụng thành đơn hàng hợp lệ, đồng thời kích hoạt toàn bộ chuỗi cung ứng phía sau bao gồm thanh toán, khóa giữ tồn kho, đóng gói và vận chuyển. Sự liền mạch của quy trình này quyết định trực tiếp đến tỷ lệ chuyển đổi giao dịch, trải nghiệm người dùng và doanh thu thương mại của doanh nghiệp.

### **2.2. Các tác nhân tham gia**

Quy trình mua hàng trực tuyến đòi hỏi sự phối hợp chặt chẽ giữa các tác nhân người dùng và hệ thống tự động:

> * Khách hàng: Tìm kiếm sản phẩm, kiểm tra giỏ hàng, nhập thông tin nhận hàng, áp dụng mã ưu đãi hoặc phiếu mua hàng, lựa chọn phương thức vận chuyển và thực hiện thanh toán.  
> * Giao diện Website/Ứng dụng Hasaki (Frontend): Hiển thị thông tin sản phẩm, tính toán giá trị giỏ hàng, kiểm tra điều kiện áp dụng khuyến mãi, tiếp nhận thông tin người dùng và cung cấp giao diện đặt hàng.  
> * Hệ thống Quản lý Đơn hàng (OMS) & ERP (Backend): Tiếp nhận đơn hàng, kiểm tra số lượng tồn kho theo thời gian thực, quét hạn mức mua hàng, xác nhận đơn và phân luồng dữ liệu xử lý.  
> * Cổng thanh toán trung gian (VNPAY / Ngân hàng liên kết): Xác thực thông tin tài khoản, xử lý giao dịch tài chính trực tuyến đối với các phương thức trả trước như VNPAY-QR, Ví VNPAY, Thẻ ATM nội địa hoặc Thẻ quốc tế Visa/Mastercard.  
> * Bộ phận Chăm sóc khách hàng (Hasaki Care / Hotline 1800 6324): Tiếp nhận và xử lý các yêu cầu hỗ trợ điều chỉnh, thay đổi thông tin hoặc hủy đơn hàng theo yêu cầu của khách hàng trước khi đơn được xuất kho.  
> * Hệ thống Kho vận & Fulfillment: Tiếp nhận đơn hàng đã được hệ thống xác nhận để thực hiện quy trình lấy hàng, kiểm tra chất lượng, đóng gói và bàn giao cho bộ phận giao hàng.

### **2.3. Khách hàng của quy trình**

Khách hàng của quy trình bao gồm tất cả các cá nhân có nhu cầu mua sắm mỹ phẩm, sản phẩm chăm sóc cá nhân hoặc đặt lịch dịch vụ thông qua website Hasaki.vn hoặc ứng dụng di động Hasaki trên phạm vi toàn quốc.

### **2.4. Kết quả có thể xảy ra**

Sau khi quy trình mua hàng trực tuyến kết thúc, hệ thống sẽ ghi nhận một trong các kết quả nghiệp vụ sau:

> * Đơn hàng được khởi tạo thành công dưới hình thức Thanh toán khi nhận hàng (COD) và tự động chuyển sang quy trình xử lý kho.  
> * Đơn hàng thanh toán trực tuyến (VNPAY/Visa/ATM) được xác thực thành công và tự động chuyển sang quy trình xử lý kho.  
> * Đơn hàng bị hệ thống tự động hủy do giao dịch thanh toán trực tuyến không thành công hoặc người dùng không hoàn tất thanh toán trong thời gian quy định.  
> * Đơn hàng bị hệ thống tự động hủy không cần thông báo trước do vượt quá giới hạn số lượng sản phẩm cho phép hoặc phát hiện dấu hiệu mua đi bán lại.  
> * Đơn hàng bị hủy trực tiếp theo yêu cầu của khách hàng thông qua tổng đài hỗ trợ trước khi chuyển cho đơn vị vận chuyển.  
> * Đơn hàng bị hủy do hệ thống phát hiện hết hàng tồn kho tại thời điểm xử lý dữ liệu.

### **2.5. Mô tả quy trình bằng lời**

Quy trình bắt đầu khi khách hàng truy cập vào hệ thống website Hasaki.vn hoặc ứng dụng di động Hasaki. Khách hàng thực hiện tìm kiếm sản phẩm mong muốn bằng cách gõ từ khóa trên thanh tìm kiếm, duyệt qua danh mục sản phẩm, các chương trình giảm giá Flash Sale hoặc danh mục thương hiệu. Khi chọn được sản phẩm, khách hàng xem chi tiết thông số, thời hạn sử dụng, chương trình quà tặng kèm và chọn thêm sản phẩm vào giỏ hàng hoặc bấm mua ngay.  
Tại màn hình giỏ hàng, khách hàng kiểm tra lại danh sách sản phẩm, điều chỉnh số lượng mua. Khách hàng có thể nhập mã Phiếu mua hàng Hasaki hoặc các mã giảm giá trực tuyến khả dụng để trừ trực tiếp vào giá trị đơn hàng. Khi chọn tiến hành đặt hàng, hệ thống yêu cầu khách hàng đăng nhập tài khoản thành viên (hoặc đăng ký mới), đăng nhập qua Google/Facebook, hoặc chọn đặt hàng không cần đăng nhập nhưng phải cung cấp đầy đủ họ tên, số điện thoại và email nhận thông báo.  
Sau khi tiếp nhận địa chỉ giao hàng, hệ thống tự động phân tích khu vực địa lý. Nếu địa chỉ nằm trong khu vực nội thành TP.HCM hoặc Hà Nội thuộc phạm vi đáp ứng dịch vụ, hệ thống hiển thị tùy chọn "Giao hàng nhanh NowFree 2H" bên cạnh tùy chọn "Giao hàng thông thường 48H". Đối với các tỉnh thành khác, hệ thống tự động áp dụng phương thức Vận chuyển giao hàng nhanh.  
Tiếp theo, khách hàng lựa chọn phương thức thanh toán. Hệ thống thiết lập một quy tắc quản trị bắt buộc: đối với các đơn hàng có tổng giá trị lớn hơn 5.000.000 VNĐ, hệ thống chỉ chấp nhận phương thức "Thanh toán trực tuyến". Đối với các đơn hàng dưới 5.000.000 VNĐ, khách hàng có thể chọn thanh toán COD (trả tiền mặt khi nhận hàng) hoặc Thanh toán trực tuyến qua cổng VNPAY bằng mã VNPAY-QR, ví điện tử VNPAY, thẻ ATM nội địa hoặc thẻ Visa/Mastercard (được miễn phí giao dịch).  
Trường hợp khách hàng chọn Thanh toán trực tuyến, giao diện sẽ chuyển hướng sang cổng thanh toán VNPAY để người dùng thực hiện quét mã QR hoặc xác thực OTP ngân hàng. Nếu giao dịch thất bại, hệ thống ghi nhận trạng thái chưa thanh toán và cho phép khách hàng thực hiện thanh toán lại từ trang Quản lý đơn hàng. Nếu thanh toán thành công hoặc khách hàng chọn hình thức COD, đơn hàng sẽ được đẩy về hệ thống quản lý đơn hàng OMS.  
Tại OMS, hệ thống tự động thực hiện hai luồng kiểm tra chính: kiểm tra số lượng tồn kho khả dụng và kiểm tra thuật toán chống gian lận (Anti-Fraud) nhằm phát hiện các đơn hàng vượt hạn mức cá nhân hoặc có dấu hiệu thu gom mua đi bán lại. Nếu đơn hàng vi phạm chính sách mua sắm, hệ thống tự động hủy đơn mà không gửi thông báo. Nếu đơn hàng hợp lệ, OMS tự động chuyển trạng thái sang đã xác nhận, gửi email/SMS thông báo đặt hàng thành công đến khách hàng, đồng thời chuyển dữ liệu đơn hàng sang bộ phận kho để bắt đầu quy trình lấy hàng, đóng gói và vận chuyển.

## **Chương 3\. Mô hình hóa quy trình BPMN**

### **3.1. Phương pháp thu thập thông tin**

Sơ đồ BPMN và cấu trúc quy trình được tổng hợp từ các chính sách vận hành công khai và các quy định nghiệp vụ thực tế của Hasaki:  
Bằng chứng thu thập:

> * Hướng dẫn đặt hàng trực tuyến và quy trình checkout trên Website Hasaki.vn.  
> * Chính sách thanh toán trực tuyến qua cổng VNPAY và quy định miễn phí giao dịch.  
> * Quy định giao dịch chung, quy định hạn chế số lượng mua và chính sách phòng chống thương lái mua đi bán lại.  
> * Hướng dẫn áp dụng Phiếu mua hàng và mã giảm giá trực tuyến.  
> * Chính sách vận chuyển, giao hàng NowFree 2H và giao hàng toàn quốc.  
> * Các kênh liên lạc chính thức, quy định xác nhận đơn hàng qua email/SMS và quy trình hỗ trợ qua Hotline 1800 6324\.

Tài liệu tham khảo nghiệp vụ:

> * Chính sách đổi trả và quy trình hoàn tiền qua ngân hàng/VNPAY.  
> * Mô hình quản trị quy trình nghiệp vụ (BPM) trong ngành bán lẻ thương mại điện tử.

Giả định mô hình hóa:

> * Các bước xử lý hạ tầng nội bộ bao gồm kiểm tra thuật toán Anti-Fraud, khóa giữ hàng tồn kho tạm thời (Inventory Lock) và đồng bộ trạng thái OMS được mô hình hóa theo tiêu chuẩn vận hành của các hệ thống TMĐT quy mô lớn.

### **3.2. Đề xuất các Lane**

Nhằm thể hiện rõ ranh giới trách nhiệm trong mô hình BPMN chuẩn 2.0, quy trình được phân chia thành 4 Lane nghiệp vụ:

> * Lane 1: Khách hàng (Customer) – Tác nhân khởi tạo tương tác, chọn hàng, nhập thông tin và thực hiện thanh toán.  
> * Lane 2: Giao diện Web/App Hasaki (Frontend System) – Tiếp nhận thao tác, kiểm tra logic đầu vào, hiển thị khuyến mãi và chuyển hướng thanh toán.  
> * Lane 3: Cổng thanh toán VNPAY & Hệ thống OMS (Backend System) – Xử lý giao dịch tài chính, kiểm tra số lượng tồn kho, kiểm tra quy tắc Anti-Fraud và xác nhận đơn hàng.  
> * Lane 4: Hệ thống Kho & Vận chuyển (Fulfillment) – Tiếp nhận đơn hàng hoàn tất để thực hiện xuất kho và giao vận.

### **3.3. Gợi ý các Activity**

Để mô hình BPMN đạt độ bao phủ nghiệp vụ cao nhưng vẫn tối ưu hóa không gian hiển thị, quy trình bao gồm 13 Activity cốt lõi:

> 1. Tìm kiếm và chọn sản phẩm vào giỏ hàng.  
> 2. Nhập thông tin người nhận và địa chỉ giao hàng.  
> 3. Áp dụng mã giảm giá hoặc Phiếu mua hàng Hasaki.  
> 4. Lựa chọn phương thức vận chuyển (NowFree 2H hoặc Giao thường).  
> 5. Lựa chọn phương thức thanh toán (COD hoặc Trực tuyến).  
> 6. Chuyển hướng và xác thực giao dịch trên Cổng thanh toán VNPAY.  
> 7. Quét thuật toán kiểm tra hạn mức mua hàng và chống mua đi bán lại.  
> 8. Kiểm tra số lượng tồn kho khả dụng tại hệ thống.  
> 9. Thực hiện khóa giữ tồn kho tạm thời cho đơn hàng. 10\. Tự động xác nhận đơn hàng trên OMS.  
> 10. Phân phát email và tin nhắn SMS thông báo đặt hàng thành công.  
> 11. Cập nhật trạng thái đơn hàng trên trang Quản lý đơn hàng người dùng.  
> 12. Đẩy thông tin đơn hàng đã xác nhận sang quy trình xử lý kho và vận chuyển.

### **3.4. Gateway đề xuất**

Mô hình BPMN ứng dụng 6 Gateway quyết định (Exclusive Gateways) để điều hướng luồng dữ liệu:

> * Gateway 1: Giá trị đơn hàng có vượt quá 5.000.000 VNĐ không? (Nếu Có \-\> Bắt buộc chọn Thanh toán trực tuyến; Nếu Không \-\> Cho phép chọn COD hoặc Trực tuyến).  
> * Gateway 2: Phương thức thanh toán được chọn là gì? (Luồng COD hay Luồng Thanh toán trực tuyến).  
> * Gateway 3: Giao dịch thanh toán trực tuyến qua VNPAY có thành công không? (Nếu Thành công \-\> Chuyển sang xử lý OMS; Nếu Thất bại \-\> Chuyển sang giao diện thanh toán lại hoặc hủy đơn).  
> * Gateway 4: Địa chỉ nhận hàng có đáp ứng điều kiện giao NowFree 2H không? (Nếu Đáp ứng \-\> Hiển thị tùy chọn NowFree 2H; Nếu Không \-\> Chỉ áp dụng Giao hàng thông thường).  
> * Gateway 5: Đơn hàng có vi phạm quy định giới hạn số lượng hoặc có dấu hiệu mua đi bán lại không? (Nếu Vi phạm \-\> Hệ thống tự động hủy đơn; Nếu Hợp lệ \-\> Chuyển sang kiểm tra tồn kho).  
> * Gateway 6: Tồn kho hệ thống có đủ số lượng đáp ứng không? (Nếu Đủ \-\> Khóa hàng và Xác nhận đơn; Nếu Khuyết thiếu \-\> Thông báo hết hàng và Hủy đơn).

### **3.5. Bộ câu hỏi phỏng vấn**

Nhằm thu thập dữ liệu chuyên sâu để tối ưu hóa quy trình, bộ câu hỏi phỏng vấn các bên liên quan được thiết kế theo 4 nhóm chuẩn:  
Câu hỏi định tính có cấu trúc:

> 1. Quy trình kết nối dữ liệu giữa giao diện Web/App và hệ thống OMS diễn ra theo cơ chế real-time hay theo chu kỳ thời gian (batch process)?  
> 2. Thuật toán kiểm tra và gắn cờ đơn hàng có dấu hiệu mua đi bán lại dựa trên các tiêu chí kỹ thuật cụ thể nào?  
> 3. Khi giao dịch qua VNPAY bị gián đoạn, thời gian tối đa để hệ thống giữ trạng thái chờ thanh toán lại là bao lâu trước khi tự động hủy?  
> 4. Hệ thống xử lý thế nào khi khách hàng kết hợp đồng thời Phiếu mua hàng Hasaki và thanh toán trực tuyến cho một đơn hàng?  
> 5. Quy định bắt buộc thanh toán trực tuyến cho đơn hàng trên 5 triệu đồng được kiểm tra tại bước nào trong giao diện checkout?

Câu hỏi định tính không cấu trúc:

> 1. Những nguyên nhân chính khiến khách hàng dừng thao tác tại bước thanh toán (Cart Abandonment) là gì?  
> 2. Bộ phận CSKH thường gặp những vướng mắc gì khi hỗ trợ khách hàng thay đổi thông tin đơn hàng vừa đặt thành công?  
> 3. Điểm nghẽn kỹ thuật lớn nhất khi đồng bộ dữ liệu tồn kho giữa kênh bán hàng trực tuyến và hệ thống cửa hàng bán lẻ là gì?  
> 4. Các trường hợp khách hàng phản ánh về việc đơn hàng bị tự động hủy do nghi ngờ mua đi bán lại được xử lý hậu kiểm như thế nào?  
> 5. Đánh giá của bộ phận vận hành về trải nghiệm thanh toán VNPAY-QR so với thanh toán qua thẻ quốc tế Visa/Mastercard?

Câu hỏi định lượng có cấu trúc:

> 1. Tỷ lệ đơn hàng thanh toán trực tuyến thành công ngay trong lần giao dịch đầu tiên đạt bao nhiêu %?  
> 2. Tỷ lệ đơn hàng bị hệ thống tự động hủy do vi phạm quy định hạn mức mua sắm chiếm bao nhiêu % tổng lượng đơn?  
> 3. Thời gian trung bình để hệ thống OMS hoàn tất kiểm tra và gửi email/SMS xác nhận đơn là bao nhiêu giây? 4\. Bao nhiêu % khách hàng lựa chọn hình thức đặt hàng không cần đăng nhập tài khoản?  
> 4. Chi phí bình quân tính trên mỗi tin nhắn SMS/ZNS xác nhận đơn hàng là bao nhiêu?

Câu hỏi định lượng không cấu trúc:

> 1. Trong các đợt Flash Sale lớn, lưu lượng truy cập tối đa mà hệ thống checkout có thể xử lý trước khi xuất hiện độ trễ là bao nhiêu?  
> 2. Tỷ lệ khách hàng gặp sự cố không nhận được mã xác thực OTP khi đăng ký hoặc đặt hàng là bao nhiêu %?  
> 3. Tỷ lệ đơn hàng hoàn tiền thành công đúng cam kết (3-5 ngày làm việc cho thẻ ngân hàng, 15-90 ngày cho thẻ Visa) đối với đơn online bị hủy là bao nhiêu %?  
> 4. Tỷ lệ chuyển đổi (Conversion Rate) từ bước thêm vào giỏ hàng đến khi hoàn tất đặt hàng là bao nhiêu?  
> 5. Mức độ chênh lệch về tỷ lệ hoàn hàng (RTO) giữa đơn COD và đơn Thanh toán trực tuyến là bao nhiêu %?

## **Chương 4\. Phân tích quy trình**

### **4.1. Phân tích giá trị gia tăng**

Phân tích giá trị gia tăng giúp nhận diện các bước trực tiếp đóng góp giá trị cho khách hàng (Value-Added \- VA), các bước phục vụ công tác quản trị bắt buộc (Business Value-Added \- BVA), và các bước không tạo ra giá trị (Non-Value-Added \- NVA).  
| Hoạt động trong quy trình | Phân loại | Giải thích nghiệp vụ | | :--- | :--- | :--- | | Tìm kiếm và chọn sản phẩm | VA | Khách hàng chủ động tiếp cận thông tin, lựa chọn sản phẩm phù hợp với nhu cầu cá nhân. | | Áp dụng mã giảm giá / Phiếu mua hàng | VA | Mang lại lợi ích tài chính trực tiếp cho khách hàng thông qua chính sách ưu đãi. | | Nhập thông tin người nhận và địa chỉ | BVA | Hoạt động bắt buộc để doanh nghiệp có đủ dữ liệu thực hiện nghĩa vụ giao hàng. | | Tùy chọn phương thức vận chuyển | VA | Tạo giá trị cá nhân hóa, cho phép khách hàng chọn nhận nhanh 2H hoặc giao thường. | | Kiểm tra hạn mức giá trị đơn hàng (\>5M) | BVA | Kiểm soát rủi ro tài chính nội bộ, ngăn ngừa tình trạng bùng hàng đối với đơn trị giá lớn. | | Xác thực thanh toán qua Cổng VNPAY | BVA | Đảm bảo tính an toàn giao dịch, bảo mật dữ liệu thẻ và xác nhận nghĩa vụ thanh toán. | | Kiểm tra chống mua đi bán lại (Anti-Fraud) | BVA | Bảo vệ hệ sinh thái giá, đảm bảo ngân sách khuyến mãi đến đúng người tiêu dùng cuối. | | Khóa giữ tồn kho tự động trên OMS | BVA | Đảm bảo tính chính xác của đơn hàng, tránh xung đột tồn kho khi bán đa kênh. | | Gửi email/SMS xác nhận đơn hàng | VA | Cung cấp thông tin xác nhận chính thức, tạo sự an tâm cho khách hàng sau thanh toán. | | Thực hiện thanh toán lại khi giao dịch lỗi | NVA | Thao tác phát sinh do sự cố mạng hoặc lỗi người dùng, làm gián đoạn trải nghiệm. |  
Phân tích sâu sắc bản chất nghiệp vụ cho thấy, quy trình mua hàng trực tuyến của Hasaki có sự cân bằng cao giữa các hoạt động tạo giá trị cho khách hàng (VA) và các hoạt động kiểm soát rủi ro doanh nghiệp (BVA). Việc thiết lập quy tắc bắt buộc thanh toán trực tuyến đối với đơn hàng có giá trị trên 5.000.000 VNĐ tuy làm gia tăng một bước BVA có tính cản trở nhẹ, nhưng là giải pháp triệt tiêu rủi ro hoàn hàng (RTO) đối với các kiện hàng giá trị cao. Mặt khác, các bước NVA như thao tác thanh toán lại do lỗi cổng giao dịch đang được giảm thiểu bằng việc lưu trữ đơn hàng ở trạng thái chờ trên hệ thống quản lý, giúp người dùng không phải lặp lại việc chọn hàng từ đầu.

### **4.2. Phân tích lãng phí**

Việc áp dụng nguyên lý vận hành Lean vào quy trình mua hàng trực tuyến giúp phát hiện và loại bỏ các dạng lãng phí thao tác và dữ liệu:

| Loại lãng phí Lean | Biểu hiện thực tế trong quy trình mua hàng Online | Hướng cải tiến nghiệp vụ đề xuất |
| :---- | :---- | :---- |
| Hold (Thời gian chờ) | Khách hàng phải chờ tin nhắn OTP xác thực tài khoản hoặc chờ cổng VNPAY phản hồi trạng thái. | Tích hợp hạ tầng xác thực Zalo Notification Service (ZNS) tốc độ cao và tối ưu băng thông kết nối API. |
| Overdo (Thao tác thừa) | Người dùng không đăng nhập phải nhập lại toàn bộ thông tin địa chỉ từ đầu cho mỗi lần đặt hàng. | Ứng dụng công nghệ lưu trữ bộ nhớ đệm (Browser Cache/Local Storage) để tự động điền thông tin cũ. |
| Defect (Lỗi dữ liệu) | Khách hàng nhập sai định dạng số điện thoại hoặc chọn sai phường/xã dẫn đến lỗi tạo đơn trên OMS. | Tích hợp thư viện tự động gợi ý địa chỉ chuẩn hóa (Auto-complete Address) ngay khi nhập. |
| Motion (Di chuyển số) | Khách hàng phải chuyển đổi qua lại giữa ứng dụng Hasaki và ứng dụng Banking để quét mã QR. | Tích hợp phương thức Deep-Link tự động mở thẳng ứng dụng ngân hàng khi khách hàng chọn VNPAY-QR. |

Phân tích mô hình vận hành cho thấy lãng phí về thời gian chờ (Hold) và thao tác thừa (Overdo) là hai yếu tố làm giảm đáng kể tỷ lệ hoàn thành đơn hàng. Khi khách hàng gặp rào cản về thời gian chờ nhận mã OTP hoặc phải điền lại các thông tin địa chỉ phức tạp, tâm lý đắn đo mua sắm sẽ gia tăng, dẫn đến việc thoát khỏi ứng dụng. Do đó, việc đơn giản hóa trải nghiệm nhập liệu đóng vai trò quyết định trong việc cải thiện hiệu quả quy trình.

### **4.3. Phân tích nguyên nhân theo Fishbone**

Hiện tượng đơn hàng trực tuyến bị hủy hoặc gián đoạn xuất phát từ nhiều nguyên nhân gốc rễ được phân bổ chi tiết qua 5 nhóm yếu tố cấu thành.  
Về phương diện Con người (Customer & Operations): Khách hàng thường xuyên gặp sai sót trong quá trình nhập dữ liệu địa chỉ nhận hàng hoặc nhập sai số điện thoại liên lạc khiến hệ thống không thể xác nhận đơn. Bên cạnh đó, một bộ phận người tiêu dùng lớn tuổi hoặc ít quen thuộc với công nghệ số thường gặp khó khăn khi thao tác xác thực OTP, quét mã VNPAY-QR hoặc đăng nhập ứng dụng ngân hàng. Ngoài ra, yếu tố tâm lý thay đổi quyết định mua sắm ngẫu nhiên của khách hàng sau khi cân nhắc về chi phí cũng là nguyên nhân phổ biến khiến giỏ hàng bị bỏ dở.  
Về phương diện Quy trình nghiệp vụ (Business Rules): Chính sách cứng áp đặt thanh toán trực tuyến bắt buộc cho các đơn hàng trị giá trên 5.000.000 VNĐ tạo ra rào cản lớn đối với những khách hàng không có tài khoản ngân hàng hoặc thẻ thanh toán quốc tế. Đồng thời, quy tắc tự động hủy đơn không thông báo đối với các đơn bị hệ thống nghi ngờ có dấu hiệu mua đi bán lại đôi khi hủy nhầm đơn của các khách hàng cá nhân có nhu cầu mua sắm thực sự cho gia đình. Thêm vào đó, việc quy định khách hàng muốn thay đổi sản phẩm hoặc hủy đơn phải gọi trực tiếp đến tổng đài Hotline 1800 6324 mà không thể thao tác nhanh trên giao diện số cũng làm gia tăng thời gian xử lý.  
Về phương diện Hệ thống công nghệ (System & Infrastructure): Sự chậm trễ trong việc đồng bộ dữ liệu tồn kho giữa hệ thống bán lẻ tại cửa hàng và hệ thống kho trung tâm lên website trong các đợt Flash Sale dễ dẫn đến tình trạng đơn hàng đã thanh toán thành công nhưng bị hủy do hết hàng thực tế. Sự cố gián đoạn đường truyền hoặc quá tải máy chủ kết nối giữa Hasaki và Cổng thanh toán VNPAY làm cho giao dịch bị gián đoạn giữa chừng. Lỗi nghẽn mạng viễn thông dẫn đến việc tin nhắn OTP gửi chậm quá thời hạn xác thực cũng gây ảnh hưởng trực tiếp đến khả năng hoàn tất đơn hàng.  
Về phương diện Phương thức thanh toán (Payment Gateway): Hạn mức giao dịch chuyển tiền hàng ngày của tài khoản ngân hàng khách hàng bị vượt quá khiến cổng VNPAY từ chối giao dịch. Hệ thống ngân hàng phát hành thẻ thực hiện bảo trì định kỳ vào khung giờ đêm khiến các giao dịch trả trước không thể xác thực. Ngoài ra, tính năng tự động chặn giao dịch của các thẻ thanh toán quốc tế (Visa/Mastercard) khi phát hiện dấu hiệu rủi ro ảo cũng khiến tỷ lệ thanh toán thất bại gia tăng.  
Về phương diện Dữ liệu và Chương trình khuyến mãi (Data & Promotions): Việc hiển thị các mã giảm giá hoặc mã Phiếu mua hàng Hasaki đã hết hạn hoặc hết lượt sử dụng trên giao diện Checkout gây ra sự bối rối cho người dùng. Thêm vào đó, các điều kiện ràng buộc áp dụng mã quá phức tạp (như giới hạn danh mục sản phẩm, giới hạn giá trị tối thiểu) nhưng hệ thống không hiển thị lý do từ chối rõ ràng khiến khách hàng hủy bỏ toàn bộ giỏ hàng.

### **4.4. Phân tích định lượng**

Phân tích định lượng cung cấp góc nhìn đo lường chi tiết về hiệu năng vận hành của quy trình mua hàng trực tuyến thông qua 3 thước đo: Thời gian, Chất lượng và Chi phí.  
Thời gian xử lý giao dịch tiêu chuẩn:

| Hoạt động thành phần | Thời gian tiêu chuẩn |
| :---- | :---- |
| Tìm kiếm, xem thông tin và thêm sản phẩm vào giỏ hàng | 120 \- 180 giây |
| Áp dụng mã giảm giá / Phiếu mua hàng | 10 \- 20 giây |
| Nhập thông tin người nhận và địa chỉ giao hàng | 30 \- 60 giây (10 giây nếu tự động điền) |
| Lựa chọn phương thức vận chuyển và thanh toán | 15 \- 30 giây |
| Xác thực thanh toán qua Cổng VNPAY (nếu trả trước) | 20 \- 45 giây |
| Hệ thống OMS kiểm tra Anti-Fraud, kiểm tra tồn kho và xác nhận | 1 \- 3 giây |
| Phân phát tin nhắn SMS/Email thông báo đặt hàng thành công | 2 \- 5 giây |
| Tổng thời gian trung bình hoàn tất một đơn hàng online | \~ 3,5 \- 5,5 phút |

Chỉ số chất lượng vận hành quy trình (KPIs):

| Chỉ số đo lường chất lượng | Giá trị mục tiêu / Giả định vận hành |
| :---- | :---- |
| Tỷ lệ đặt hàng thành công từ giỏ hàng (Cart Conversion Rate) | 78% |
| Tỷ lệ thanh toán trực tuyến thành công ngay lần đầu (VNPAY/Visa) | 91,5% |
| Tỷ lệ đơn hàng bị tự động hủy do lỗi thanh toán không hoàn tất | 2,5% |
| Tỷ lệ đơn hàng bị tự động hủy do vi phạm quy định hạn mức / mua đi bán lại | 0,8% |
| Tỷ lệ đơn hàng bị hủy do sự cố hết hàng tồn kho thực tế | 0,3% |
| Tỷ lệ khách hàng khiếu nại về thông tin giao hàng sai lệch | \< 0,5% |

Chi phí vận hành công nghệ tính trên mỗi đơn hàng thành công:

| Khoản mục chi phí cấu thành | Chi phí ước tính (VNĐ / đơn hàng) |
| :---- | :---- |
|  | Chi phí hạ tầng máy chủ Cloud, băng thông Web/App |
| Phí xử lý giao dịch Cổng thanh toán (VNPAY/Visa \- Hasaki tài trợ) | 3.500 (Ước tính bình quân theo giá trị đơn) |
| Chi phí dịch vụ viễn thông (Gửi SMS OTP / Email / ZNS xác nhận) | 350 |
| Chi phí bảo trì phần mềm OMS, hệ thống kiểm soát gian lận | 800 |
| Chi phí nhân công tổng đài CSKH hỗ trợ đơn hàng online | 1.500 |
| Tổng chi phí vận hành quy trình số trên một đơn hàng | \~ 7.350 VNĐ |

Nghiên cứu định lượng cho thấy, việc miễn phí giao dịch thanh toán trực tuyến cho khách hàng làm phát sinh chi phí cổng thanh toán khá lớn cho Hasaki, nhưng bù lại, các đơn hàng trả trước có tỷ lệ hủy đơn và tỷ lệ hoàn hàng (RTO) gần như bằng 0%, giúp tiết kiệm đáng kể chi phí vận chuyển thu hồi so với hình thức COD.

### **4.5. Kiến nghị cải tiến**

Để nâng cao hơn nữa hiệu quả vận hành của quy trình mua hàng trực tuyến \- xương sống thương mại điện tử của Hasaki, các giải pháp cải tiến công nghệ và nghiệp vụ cần được triển khai đồng bộ:  
Chuyển đổi sang mô hình Thanh toán 1 trang (One-Page Checkout): Doanh nghiệp nên tái cấu trúc giao diện đặt hàng bằng cách gom toàn bộ các bước chọn địa chỉ, phương thức vận chuyển, mã giảm giá và phương thức thanh toán vào một màn hình cuộn duy nhất. Giải pháp này giúp cắt giảm ít nhất 30% thời gian thao tác và giảm rủi ro khách hàng hủy bỏ giỏ hàng do quy trình quá nhiều bước.  
Ứng dụng cơ chế Khôi phục thanh toán thông minh (Smart Payment Recovery): Khi giao dịch trực tuyến qua VNPAY không thành công, thay vì bắt buộc khách hàng phải tự tìm vào mục Quản lý đơn hàng để thực hiện lại, hệ thống nên lập tức hiển thị một cửa sổ thông báo lỗi kèm tùy chọn "Thanh toán lại bằng mã QR mới" hoặc "Chuyển sang thanh toán COD" ngay tại màn hình. Điều này giúp cứu vãn các đơn hàng bị gián đoạn do sự cố mạng.  
Nâng cấp thuật toán Anti-Fraud bằng Trí tuệ nhân tạo (AI): Thay vì áp dụng quy tắc tự động hủy đơn cứng nhắc đối với các đơn hàng bị nghi ngờ mua đi bán lại, hệ thống nên tích hợp AI để chấm điểm rủi ro (Risk Scoring) dựa trên lịch sử nhận hàng, thiết bị truy cập và hành vi người dùng. Các đơn hàng nằm trong "vùng xám" sẽ được chuyển cho bộ phận CSKH xác minh nhanh qua điện thoại thay vì tự động hủy không thông báo, tránh làm tổn hại đến trải nghiệm của khách hàng trung thành.  
Phát triển tính năng Tự phục vụ (Self-Service Order Management): Tích hợp tính năng cho phép khách hàng trực tiếp bấm nút "Hủy đơn hàng" hoặc "Sửa địa chỉ giao hàng" trên ứng dụng Hasaki trong vòng 10-15 phút đầu sau khi đặt đơn (với điều kiện đơn chưa chuyển sang trạng thái Đang lấy hàng). Giải pháp này triệt tiêu thời gian chờ đợi của khách hàng khi phải gọi lên Hotline 1800 6324, đồng thời giảm tải áp lực chi phí nhân công cho tổng đài chăm sóc khách hàng.  
Tối ưu hóa khả năng Đồng bộ tồn kho Omnichannel theo thời gian thực: Đầu tư nâng cấp hạ tầng kết nối API giữa hệ thống quản lý kho ERP và nền tảng bán hàng trực tuyến. Việc cập nhật số lượng tồn kho theo thời gian thực (Real-time Inventory Matching) sẽ ngăn chặn triệt để tình trạng khách hàng đặt mua và thanh toán thành công cho các sản phẩm đã hết hàng tại kho thực tế.

#### **Nguồn trích dẫn**

1\. Đổi trả \- Hoàn tiền tại Hasaki, [https://hotro.hasaki.vn/doi-tra-hoan-tien.html](https://hotro.hasaki.vn/doi-tra-hoan-tien.html)  
2\. Hướng dẫn thanh toán trực tuyến VNPAY \- Hasaki.vn, [https://hotro.hasaki.vn/huong-dan-thanh-toan-truc-tuyen-vnpay.html](https://hotro.hasaki.vn/huong-dan-thanh-toan-truc-tuyen-vnpay.html)  
3\. Hướng dẫn đặt hàng tại Hasaki, [https://hotro.hasaki.vn/huong-dan-dat-hang.html](https://hotro.hasaki.vn/huong-dan-dat-hang.html)  
4\. Phiếu mua hàng tại Hasaki, [https://hotro.hasaki.vn/phieu-mua-hang.html](https://hotro.hasaki.vn/phieu-mua-hang.html)  
5\. Hướng dẫn đặt hàng 2H tại Hasaki, [https://hotro.hasaki.vn/huong-dan-dat-hang-2h.html](https://hotro.hasaki.vn/huong-dan-dat-hang-2h.html)  
6\. Đặt hàng tại Hasaki, [https://hotro.hasaki.vn/dat-hang-tai-hasaki.html](https://hotro.hasaki.vn/dat-hang-tai-hasaki.html)  
7\. Hướng Dẫn Nhận Biết Kênh Chính Thức Của Hasaki, [https://hotro.hasaki.vn/huong-dan-nhan-biet-kenh-chinh-thuc-cua-hasaki.html](https://hotro.hasaki.vn/huong-dan-nhan-biet-kenh-chinh-thuc-cua-hasaki.html)  
8\. Xin chào\! Chúng tôi có thể giúp gì cho bạn? \- Hasaki.vn, [https://hotro.hasaki.vn/quy-dinh-giao-dich-chung.html](https://hotro.hasaki.vn/quy-dinh-giao-dich-chung.html)  
