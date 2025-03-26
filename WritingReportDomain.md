# Câu hỏi: Domain là gì ? Các trạng thái của Domain ? Subdomain là gì ? Virtual host là gì ?
# Trả lời : 

## Domain là gì ? 
- Mỗi website trên môi trường Internet đều cần có một địa chỉ, địa chỉ này được gọi là địa chỉ IP (Internet Protocol - Giao thức Internet) phức tạp và khó nhớ. Chính vì lý do này mà domain (tên miền) xuất hiện nhằm cung cấp một địa chỉ dễ đọc dễ nhớ hơn so với địa chỉ IP, ví dụ thay vì phải nhớ và tìm kiếm 142.251.10.139 cho việc truy cập google thì ta chỉ cần gõ google.com.
---

## Các trạng thái của Domain ? 
- Trạng thái tên miền cho biết hoạt động hiện tại và các thao tác có thể tiến hành với tên miền đó 
### Trạng thái tên miền tại Đơn vị Cấp phát tên miền (Registry)
| Status | Ý nghĩa | Nên làm gì |
| --- | ---| ---------------------- |
| OK/Active | Tên miền hoạt động bình thường sau khi đăng kí | Nên yêu cầu các nhà đăng kí thực hiện các trạng thái hạn chế nhằm ngăn chặn chuyển đổi, xóa hoặc cập nhật trái phép vaò tên miền |
| addPeriod | Trạng thái sau khi vừa đăng kí tên miền | Không có vấn đề nào phát sinh với tên miền. Đây là trạng thái được đặt sau vài ngày đầu đã đăng kí tên miền | 
| autoRenewPeriod | Thời gian tự động gia hạn tên miền. Trạng thái này cho phép nhà đăng kí hủy việc gia hạn tên miền nhưng phải chi trả một khoản phí cho nhà cung cấp | Sau khi đăng kí tự động gia hạn tên miền, trạng thái này sẽ được đặt trong một khoản thời gian giới hạn |
| inactive | Trạng thái này cho biết tên miền đã được đăng kí nhưng Name Server chưa thể liên kết với tên miền | Liên hệ với nhà đăng kí để yêu cầu xử lý |
| pendingCreate | Tên miền đang chờ được đăng kí | Yêu cầu tạo tên miền đã được xác nhận và đang chờ xử lý | 
| pendingDelete | Tên miền hết hạn đăng ký và chuẩn bị xóa | Chờ tên miền trở lại trạng thái tự do, sau đó có thể đăng kí lại |
| pendingRenew | Tên miền đang chờ gia hạn | Yêu cầu gia hạn tên miền đã được tiếp nhận và trong quá trình xử lý | 
| pendingRestore | Tên miền đã hết hạn đang chờ về trạng thái khôi phục (Active). Trong thời gian này nếu nhà đăng kí không thực hiện yêu cầu khôi phục nào thì tên miền sẽ trở về trạng thái redemptionPeriod | Theo dõi tên miền trong 7 ngày để xác minh nhà đăng kí đã thực hiện yêu cầu khôi phục tên miền. Nếu tên miền chuyển về trạng thái redemptionPeriod hãy liên hệ với nhà đăng kí để được hỗ trợ | 
| pendingTransfer | Tên miền chờ chuyển đổi nhà đăng kí | Trường hợp bạn không chuyển đổi tên miền thì hãy liên hệ với nhà đăng ký để yêu cầu họ từ chối yêu cầu chuyển tên miền. Sau đó, đưa về trạng thái clientTransferProhibited (Cấm chuyển đổi nhà đăng ký) |
| pendingUpdate | Tên miền đang chờ cập nhật | Nếu bạn không yêu cầu cập nhật thêm thông tin, liên hệ với nhà đăng ký để được giúp đỡ | 
| redemptionPeriod | Tên miền đã hết hạn và rơi vào trạng thái cần thanh toán phí gia hạn nếu bạn muốn tiếp tục sử dụng | Nếu bạn muốn giữ tên miền của mình không bị xóa, bạn cần liên hệ ngay với nhà đăng ký trước khi tên miền bị xóa. Thông thường, thời gian này sẽ kéo dài trong 30 ngày | 
| renewPeriod | Trạng thái tên miền được gia hạn | Trạng thái này được đặt trong một khoảng thời gian giới hạn cho việc xác nhận gia hạn tên miền với nhà đăng ký |
| serverDeleteProhibited | Ngăn tên miền của bạn bị xóa | Trạng thái này thường được ban hành trong các trường hợp tranh chấp pháp lý, theo yêu cầu hoặc khi có trạng thái redemptionPeriod. Đây không phải là một trạng thái phổ biến, muốn gỡ bỏ trạng thái này phải liên hệ với nhà đăng ký tên miền | 
| serverHold | Trạng thái tên miền không được kích hoạt trong DNS | Để kiểm tra thông tin, bạn phải liên hệ với nhà đăng ký | 
| serverRenewProhibited | Trạng thái tên miền không thể được gia hạn. Trạng thái này không thông dụng vì chỉ có hiệu lực trong quá trình tranh chấp pháp lý | Để gỡ bỏ trạng thái này, hãy yêu cầu nhà đăng ký liên hệ với cơ quan cấp phát. Quá trình này có thể mất thời gian hơn so với clientRenewProhibited. Do đó, bạn cần kiên nhẫn đợi họ xử lý yêu cầu | 
| serverTransferProhibited | Trạng thái không cho phép transfer tên miền | Đây cũng là trạng thái trên miền không phổ biến, thường được ban hành trong các trường hợp tranh chấp pháp lý hoặc theo yêu cầu. Bạn phải liên hệ với nhà đăng ký khi muốn gỡ bỏ | 
| serverUpdateProhibited | Trạng thái không cho phép cập nhật tên miền | Đây cũng là trạng thái trên miền không phổ biến, thường được ban hành trong các trường hợp tranh chấp pháp lý hoặc theo yêu cầu. Cần liên hệ với nhà đăng ký tên miền để có thể gỡ bỏ | 
| transferPeriod | Đây là trạng thái cho phép sau khi transfer tên miền thành thông thì nhà đăng ký mới có thể yêu cầu nhà cung cấp xóa tên miền | Trạng thái này sẽ được đặt trong một khoảng thời gian giới hạn sau khi bạn chuyển tên miền sang nhà đăng ký mới. Nếu bạn không yêu cầu chuyển tên miền thì hãy liên hệ với nhà đăng ký ban đầu để kiểm tra, nhằm tránh bị mất tên miền | 
### Trạng thái tên miền tại Nhà đăng kí tên miền (Registrar)
| Status | Ý nghĩa | Nên làm gì |
| --- | -----------|------------|
| clientDeleteProhibited | Cấm hủy domain/ Không cho phép xóa tên miền | Trạng thái thể hiện không thể xóa tên miền, giúp ngăn chặn việc xóa trái phép do chiếm quyền điều khiển hay gian lận |
| clientHold | Trạng thái tạm ngừng tên miền (suspend tên miền) | Với trạng thái này, DNS tên miền của bạn sẽ không hoạt động. Đối với tên miền Việt Nam, nếu bạn chưa hoàn thành hồ sơ đăng ký sẽ bị khóa ở cấp nhà đăng ký. Để gỡ bỏ trạng thái này, bạn hãy liên hệ với nhà cung cấp để được trợ giúp |
| clientRenewProhibited | Cấm gia hạn tên miền/ Không cho phép gia hạn tên miền| Đây là một trạng thái không phổ biến, thường được ban hành khi có các tranh chấp về pháp lý. Bạn chỉ cần liên hệ với nhà đăng ký để gia hạn hoặc xóa trạng thái này | 
| clientTransferProhibited | Trạng thái không cho phép transfer tên miền (Cấm chuyển đổi nhà đăng ký) | Trạng thái này mang ý nghĩa không thể chuyển đổi nhà đăng ký tên miền, điều này giúp ngăn chặn trái phép khi bị chiếm quyền điều khiển hoặc lừa đảo | 
| clientUpdateProhibited | Cấm cập nhật thông tin/ Không cho phép cập nhật thông tin | Đây là trạng thái cho biết không thể cập nhật tên miền, giúp ngăn chặn các cập nhật tên miền trái phép từ kẻ xấu | 
---

## Subdomain là gì ? 
Subdomain là một phần tùy chọn và nằm phía trước tên miền chính. Nó giúp chia nhỏ và tổ chức trang web hoặc ứng dụng của bạn thành các phần khác nhau. Ví dụ, trong “blog.tamsutuoihong.vn”, “blog” là subdomain. Một số lợi ích khi sử dụng subdomain:
1.  Tổ chức website rõ ràng 
2.  Cải thiện trải nghiệm người dùng
3.  Tối ưu hóa SEO
4.  Tăng cường khả năng bảo mật 
5.  Thích hợp cho nhiều dự án
   
### Quy trình hoạt động: 
1.  User truy cập subdomain trên browser
2.  Browser gửi request tới DNS Resolver (DNS Server của ISP)
3.  DNS Resolver truy vấn Root Name Server 
4.  Root Name Server chỉ dẫn DNS Resolver đến TLD Name Server 
5.  TLD Name Server chỉ dẫn DNS Resolver đến Authoritative Name Server 
6.  Authoritative Name Server sẽ tìm kiếm subdomain trong DB của mình sau đó sẽ trả về IP tương ứng với subdomain cho DNS Resolver 
7.  DNS Resolver trả lại IP cho Browser 
8.  Browser sử dụng Ip này để kết nối tới server chứa nội dung của subdomain và cuối cùng server đó sẽ trả về nội dung tương ứng cho browser và hiển thị cho user.
   
---
## Virtual host là gì ?
### Định nghĩa: 
Virtual Hosts là một tính năng trong web server và cũng là một phương thức lưu trữ, cho phép nhiều trang web hoặc tên miền hoạt động trên cùng một máy chủ vật lý hoặc một địa chỉ IP duy nhất. Đây là giải pháp hữu ích giúp tối ưu hóa tài nguyên máy chủ, giảm chi phí vận hành và đơn giản hóa việc quản lý hosting cho nhiều website.
### Ưu điểm :
Tiết kiệm chi phí hơn so với việc sử dụng dedicated server. Tối ưu cho các doanh nghiệp nhỏ hoặc cá nhân. Giảm tải áp lực trffic lên site. Tận dụng và quản lý tài nguyên linh hoạt. Khả năng mở rộng. Linh hoạt trong việc thiết lập từng trang web mà không ảnh hướng đến nhau.
### Nhược điểm : 
Hiệu năng hạn chế. Nếu một website trên cùng virtual host bị tấn công thì có thể ảnh hưởng đến các trang web khác. Bảo mật thấp hơn so với dedicated server. Không phù hợp với các ứng dụng phức tạp. Quản lý phức tạp. Giới hạn quyền kiểm soát. Ràng buộc tài nguyên.


  