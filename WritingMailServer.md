# Mail Server là gì ? Tìm hiểu MX Record ? Tìm hiểu DKIM, SPF, PTR ? 
# Trả lời : 
## Mail Server là gì ? 
- Là hệ thống máy chủ được cấu hình riêng theo tên miền của doanh nghiệp dùng để gửi và nhận mail. Bên cạnh tính năng lưu trữ và sắp xếp email trên Internet, mail server còn dùng giao tiếp thư tín, quản lý truyền thông nội bộ, giao dịch thương mại,...Thao tác nhanh chóng, ổn định, an toàn, khả năng phục hồi dữ liệu cao. Mail Server về cơ bản là Dedicated Server hay Cloud Server được cấu hình để gủi và nhận thư điện tử , nó có thông số đầy đủ như một server bình thường như Ram, CPU, Storage,...ngoài ra nó còn một số thông số liên quan đến yếu tố email như số lượng tài khoản mail, email fowarde, mail list,...
---

## Tìm hiểu MX Record ? 
- MX Record là viết tắt của Mail Exchanger Record được định nghĩa là một bản ghi trong DNS zone dùng để định vị Mail Server cho một Domain. Một tên miền có thể được gán bởi nhiều bản ghi MX, việc này giúp cho các email của bạn không bị mất đi dữ liệu nếu ngưng hoạt động một thời gian.
#### Các bước trỏ MX Record của tên miền 
Thay đổi MX Record được thực hiện để chuyển hướng từ xa một email đến một máy chủ. Bên cạnh đó, nó cũng có tác dụng như bản sao lưu tạm thời trong trường hợp mail server nội bộ bị hỏng hoặc gặp sự cố.
##### Các bước sau giúp trỏ MX Record của tên miền khác:
1. Bước 1: Truy cập Cpanel 
2. Bước 2: Click biểu tượng MX Entry 
3. Bước 3: Chọn domain có vấn đề từ danh sách thả xuống 
4. Bước 4: Click **Automaticcally Detect Configuration** sau đó nhấn **Change**
5. Bước 5: Trong **Thêm bảng ghi mới**, nhập bất cứ thứ gì được cung cấp bởi server cho giá trị Đích. Ưu tiên thường sẽ bằng 0.
6. Bước 6: Nhấn nút **Add New Record**
##### Trỏ MX record đến đến một server khác sử dụng cùng một tên miền
1. Bước 1: Đăng nhập vào Cpanel nơi DNS của bạn được lưu trữ 
2. Bước 2: Nhấn vào biểu tượng MX Entry 
3. Bước 3: Chọn tên miền có vấn đề từ danh sách thả xuống 
4. Bước 4: Chọn **Automatically Detect Configuration** và nhấn **Change**
5. Bước 5: Trong **Add New Record**, nhập bất cứ thứ gì được cung cấp bởi server cho giá trị Đích. Ưu tiên thường sẽ bằng 0.
6. Bước 6: Nhấn **Add New Record** 
7. Bước 7: Chuyển đến trang chủ Cpanel và nhấp vào biểu tượng Trình soạn thảo DNS đơn giản.
8. Bước 8: Chọn cùng một tên miền từ trình đơn thả xuống.
9. Bước 9: Trong **Add An A Record** nhập bất cứ điều gì bạn đặt cho đích MX trong trường **Name**
10. Bước 10: Trong trường **Địa chỉ** nhập địa chỉ IP của máy chủ khác 
11. Nhấn vào nút **Add A Record** 
---
## Tìm hiểu về DKIM, SPF, PTR ? 
### DKIM 
 - DKIM có vai trò cực kỳ quan trọng trong việc xác nhận giả mạo và những spam mail được sử dụng nhiều hiện nay. DKIM là viết tắt của DomainKeys Identified Mail - Một phương thức giúp xác nhận Email thông qua chữ ký số giúp tránh email giả mạo. Một kỹ thuật thường được sử dụng trong lừa đảo và spam email. DKIM cho phép người nhận kiểm tra xem email được xác nhận từ một tên miền cụ thể có thực sự được chủ sở hữu ủy quyền hay không? Nó sẽ gắn chứ ký điện tử, được liên kết với tên miền nào vào mỗi email gửi đi. hệ thống người nhận có thể xác minh điều này bằng cách tra cứu mã khóa công khai (Public-key cryptography) của người gửi được xuất bản trong DNS.
- Bên cạnh đó DKIM còn có khả năng chặn các email giả mạo. Đối với các email với mục đích giả mạo, lừa đảo, email spam chứa mã độc...
  + Khóa công khai thường được công bố trên DNS dưới dạng TXT record 
  + Khi gửi email, chữ ký sẽ được chèn lên đầu với trường DKIM-Signature.
#### DKIM hoạt động như thế nào ? 
DKIM sử dụng các bản ghi DNS dưới dạng TXT record với định dạng đặc biệt. Khi cặp khóa riêng / chung được tạo, khóa chung sẽ được thêm vào DNS của domain.
- **Ở bên gửi:**
Ban đầu sẽ tạo ra cặp khóa public/private key sau đó chuyển publuc key lên khai báo TXT record trên DNS dứng đúng với doamin gửi mail. Sau đó cấu hình mail server sử dụng private key để ký vào email trước khi gửi email (Khóa này lưu trên server nên không thể giả mạo)
- **Ở bên nhận:**
Nhận email ở bên gửi và kiểm tra email có thông điệp được mã hóa do cấu hình DKIM. Query DNS để lấy public key của domain bên gửi rồi giải mã, khi giải mã đúng thì xác nhận nguồn gửi và nhận email đảm bảo, khi giải mã không đúng thì phụ thuộc vào chính sách bên nhận có thể là từ chố hoặc chuyển đến thư spam.

### SPF 
Sender Policy Framework (SPF) là một kỹ thuật xác thực email được sử dụng để chống lại việc giả mạo email. Việc thiết lập SPF record giúp ngăn chặn những kẻ có mục đích xấu sử dụng domain của bạn để gửi email xấu. Những email này còn được gọi là giả mạo email (email spoofing).
#### TXT SPF record là gì ? 
TXT SPF record là một TXT record, là một phần của DNS của domain. Nó liệt kê tất cả cá hostname / địa chỉ IP được ủy quyền và thay mặt cho domain của bạn gửi email.
#### tác dụng của TXT SPF record là gì ? 
Một số bên nhận email luôn yêu cầu phải có SPF. Nếu chưa publish TXT SPF record cho domain, email của bạn có thể bị đánh dấu là spam. Thậm chí email có thể bị trả lại. Nếu một email được gửi qua một mail server chưa được liệt kê SPF record thì email đó có thể bị đánh dấu là spam. Record được thiết lập đúng cách sẽ cải thiện khả năng gửi email. Hơn thế nữa nó sẽ giúp bảo vệ domain khỏi các email độc hại.
#### Cách tạo TXT SPF record 
#### Bước 1: Thu thập tất cả các địa chỉ IP được sử dụng để gửi mail. 
#### Bước 2: Tạo TXT SPF record 
+ Record phải luôn bắt đầu bằng số phiên bản `v = spf1` (phiên bản 1) tag này xác định là SPF, từng có phiên bản thứ hai là senderID nhưng đã bị ngừng.
+ Sau khi thêm version tag `v = spf1`, follow theo tất cả địa chỉ IP đươcj ủy quyền gửi mail. 
##### Ví dụ: 
    `v = spf1 ip4: 34.243.61.237 ip6: 2a05: d018: e3: 8c00: bb71: dea8: 8b83: 851e`
+ Tiếp theo có thể thêm include tag cho mọi tổ chứ bên thứ ba được sử dụng để thay bạn gửi mail, ví dụ: `include:thirdpartydomain.com.`
+ Khi đã triển khai tất cả các địa chỉ IP và bao gồm các tag nên kết thức record của mình bằng tag ` ~ all ` hoặc ` - all `. Tag all là một phần quan trọng của record vì nó cho biết chính sách nào được áp dụng khi ISP phát hiện server không được liệt kê trong record. Nếu server không liệt kê trong record gửi email, mọi hoạt động sẽ được xử lý theo chính sách.
##### Tag `all` có cá điểm đánh dấu cơ bản sau :
+ `- all` Fail - các server không được liệt kê trong SPF Record không được phép gửi các email (các email không tuân thủ sẽ bị từ chối).
+ `~ all` Softfail - nếu email được nhận từ một server không được liệt kê, email đó sẽ được đánh dấu là soft fail (email sẽ được chấp nhận nhưng được đánh dấu).
+ `+ all` Không nên dùng option này vì tag này cho phép server bất kỳ gửi email từ domain của bạn.
##### Sau khi xác định SPF record, record có thể trông giống như sau:
    `v = spf1 ip4: 34.243.61.237 ip6: 2a05: d018: e3: 8c00: bb71: dea8: 8b83: 851e include: thirdpartydomain.com -all`
+ Đối với các domain không gửi email, nên publish record sau v = spf1 -all
*Lưu ý rằng SPF record không được vượt quá 255 ký tự và có tối đa 10 include tag, còn được gọi là "lookups"*
#### Bước 3: Publish SPF record vào DNS
- Login vào domain account tại nhà cung cấp domain host của bạn 
- Tìm trang để update DNS record cho domain (như: DNS management hay name server management)
- Chọn domain muốn sửa đổi các record 
- Mở DNS manager 
- Login và domain account tại nhà cung cấp domain host của bạn 
- Tạo TXT record mới trong phần TXT (text)
- Đặt Host field thành tên doamain của bạn 
- Điền vào TXT Value với SPF record của bạn (tức là `v = spf1 a mx include: exampledomain.com ~ all`)
- Chỉ định Time To Live (TTL), enter 3600 hoặc để mặc định
- **Save** hoặc **Add record** để publish SPF TXT record vào DNS.
- *Record mới có thể mất đến 48 giơ để có hiệu lực*
#### Bước 4: Kiểm tra SPF record bằng SPF record Checker
SPF record được cấu hình chính xác khi: 
- SPF record Checker đã tìm thấy SPF record 
- Không vượt quá tối đa 10 lần lookups
- Địa chỉ IP được cấu hình là địa chỉ thực được sử dụng để gửi email.

---
### PTR 
- PTR hay Pointer Record là một loại bản ghi trong hệ thống DNS được sử dụng để ánh xạ một địa chỉ IP thành một tên miền. Nó hoạt động theo chiều ngược lại so với các bản ghi DNS thông thường: thay vì ánh xạ tên miền thành địa chỉ IP (như bản ghi A hoặc AAAA) nó ánh xạ địa chỉ IP thành tên miền.
- Các trường hợp sử dụng PTR record bao gồm: 
  + Xác minh địa chỉ IP
  + Bộ lọc spam và phòng chống lừa đảo 
  + Xác định danh tính máy chủ
  #### Các bản ghi PTR được định dang
        `xx.xx.xx.xx.in-addr.arpa. IN PTR example.com.`
    + Trong đó 
    + `xx.xx.xx.xx` là địa chỉ IP muốn ánh xạ thành tên miền 
    + `in-addr-arpa` phần cố định của định dạng PTR 
    + `IN PTR` xác định đây là một bản ghi PTR (phần quan trọng)
    + `example.com` tên miền muốn ánh xạ địa chỉ IP đến. Thông thường, nó là tên miền chính hoặc một tên miền con tùy thuộc vào cách muốn cấu hình nó.
