# Câu hỏi: SSL là gì ? Có bao nhiêu cách chứng thực SSL ? CSR file dùng làm gì trong quá trình tạo SSL ? Sử dụng OpenSSL để gen file CSR sau đó request SSL cho domain tech.training.vietnix.tech ? Pem file là gì ? Private key ssl là gì ? PFX file là gì? Cách chuyển từ file crt file sang PFX file ?
# Trả lời: 

## SSL là gì ? Có bao nhiêu cách chứng thực SSL ?
### SSL là gì ? 
SSL (Secure Sockets Layer) là một tiêu chuẩn công nghệ bảo mật, giúp mã hóa dữ liệu truyền thông giữa trình duyệt và máy chủ web. SSL đảm bảo tính toàn vẹn, riêng tư và bảo mật của dữ liệu truyền tải. Một số vai trò chính của SSL bao gồm:

1. **Bảo mật thông tin bằng mã hóa**: Chuyển đổi thông tin từ dạng bản rõ sang bản mã (chỉ người nắm giữ khóa mới giải mã được).
2. **Cung cấp tính xác thực**: Đảm bảo thông tin được gửi đến đúng đích.
3. **Tăng độ uy tín cho website**.
4. **Bảo mật thanh toán trực tuyến**.
5. **Tối ưu SEO**.
### Các loại chứng thực SSL
1. **Domain Validation (DV SSL)**:  
   Xác thực tên miền, dành cho các website cá nhân với khả năng mã hóa cơ bản. Chỉ yêu cầu xác minh quyền sở hữu tên miền. Loại này có chi phí thấp và thời gian đăng ký nhanh.

2. **Organization Validation (OV SSL)**:  
   Xác thực dành cho các tổ chức/doanh nghiệp. Yêu cầu xác minh quyền sở hữu tên miền và thông tin doanh nghiệp. Tên doanh nghiệp sẽ được hiển thị trên chứng chỉ.

3. **Extended Validation (EV SSL)**:  
   Chứng chỉ xác thực mở rộng, có độ tin cậy cao nhất. Thường sử dụng cho các doanh nghiệp lớn. Quá trình đăng ký tuân thủ nghiêm ngặt quy định của CA (Certificate Authority).

4. **Wildcard SSL**:  
   Dành cho các website có nhiều subdomain. Chỉ cần một chứng chỉ duy nhất để bảo vệ tất cả subdomain.

5. **Subject Alternative Names (SAN SSL)**:  
   Cho phép bảo vệ nhiều tên miền khác nhau bằng một SSL duy nhất. Thường sử dụng trong các ứng dụng Microsoft Exchange Server, tiết kiệm chi phí và dễ quản lý.
---
  
## CSR file dùng làm gì trong quá trình tạo SSL ?
CSR (Certificate Signing Request) là một file chứa thông tin mã hóa của chủ sở hữu tên miền. File này được gửi đến nhà cung cấp dịch vụ SSL (CA) để xác nhận thông tin và cấp chứng chỉ. CSR bao gồm:

- Tên miền.
- Thông tin tổ chức.
- Thông tin liên lạc.
- Public key.
---
  
## Sử dụng OpenSSL để gen file CSR sau đó request SSL cho domain `tech.training.vietnix.tech`?
### Sử dụng OpenSSL để tạo file CSR:
#### Bước 1: Tạo private key:
    `openssl genrsa -out PrivateKey001.key 2048`
- Giải thích: 
    `openssl`: Sử dụng Open SSL trên hệ thống, 
    `genrsa`: option chỉ định tạo ra cặp khóa RSA, 
    `-out PrivateKey001.key`:  chỉ định tên cho file, key sẽ được lưu vào file có tên là PrivateKey001.key, 
    `2048`: độ dài của khóa RSA là 2048 bit
#### Sau đó kiểm tra key đã tạo thành công chưa bằng lệnh 
    `openssl rsa -in PrivateKey001.key -text -noout`
![text](./ImagersSSL/Screenshot%20from%202025-03-25%2015-10-53.png)
#### Trên GUI ta cũng thấy được key vừa tạo 
![text](./ImagersSSL/Screenshot%20from%202025-03-25%2015-22-59.png)
#### Bước 2: Tạo file CSR bằng private key vừa tạo bên trên 
    `openssl req -new -key PrivateKey001.key -out CSRFile001.csr`
- Giải thích: 
    `openssl req` dùng để  tạo CSR, 
    `-new` option chỉ định tạo một CSR mới, 
    `-key` option chỉ định private key được dùng để tạo file CSR, 
    `-out` option chỉ định tên file CSR được tạo.
- Sau khi chạy command trên thì yêu cầu một số thông tin như: 
  + Country Name (2 letter code): Mã quốc gia (VN, US,...)
  + State or Province Name: Tên bang hoặc tỉnh.
  + Locality Name (eg, city): Tên thành phố.
  + Organization Name: Tên tổ chức hoặc công ty.
  + Organizational Unit Name: Đơn vị hoặc phòng ban.
  + Common Name: Tên cá nhân hoặc tên miền (ví dụ: tech.training.vietnix.tech).
  + Email Address: Địa chỉ email liên lạc.
![text](./ImagersSSL/Screenshot%20from%202025-03-25%2016-01-41.png)
#### Kiểm tra file CSR được tạo bằng lệnh 
    `openssl req -in CSRFile001.csr -text -noout`
![text](./ImagersSSL/Screenshot%20from%202025-03-25%2016-02-09.png)
#### 2 file này cần giữ lại, file csr để đăng kí kích hoạt dịch vụ SSL, file key dùng để cài chứng chỉ SSL sau khi nhận được certificate.
---

### PEM File là gì ?
- PEM (Privacy Enhanced Mail) là một định dạng tệp được sử dụng rộng rãi để lưu trữ và truyền tải các chứng chỉ số, khóa mật mã, các dữ liệu bảo mật khác trong hệ thống mã hóa. File PEM thường có phần mở rộng là .pem, .crt, .cer hoặc .key và được mã hóa bằng Base64 
  > Base64 là một chương trình mã hóa chuỗi ký tự bằng cách dùng thay thế các ký tự trong bảng mã ASCII 8 bit thông dụng thành bảng mã 6 bit. Ký tự 64 trong Base64 là đại diện cho 64 ký tự (A-Za-z0-9+/) trong bãng mã ASCII..
---

### Private key ssl là gì ?
- Mỗi khi đăng kí một SSL, thì nhà cung cấp SSL sẽ cấp lại Certificate, Private Key, root CA. Để có được một SSL thì ta cần tạo một CSR trên server, quá trình tạo CSR trên server sẽ sinh ra private key và public key. Ta sẽ phải gửi CSR (có chứa public key) cho các tổ chức phát hành SSL (tức Certificate Authority - CA), phía tổ chức sẽ sử dụng thông tin CSR để tạo ra một cấu trúc dữ liệu phù hợp với private key mà ta đã giữ trên server, sau đó certificate sẽ được cấp sau khi thực hiện xác minh.
- Khi người dùng sử dụng https để truy cập website, browser sẽ kết nối và yêu cầu server xác thực. Server sẽ gửi một bản sao SSL Certificate và Public key. Browser sẽ kiểm tra Certificate và đối chiếu với chứng chỉ gốc CA, Cert phải còn hạn, Cert chưa bị hủy bới tổ chức phát hành, domain của cert phải khớp với domain của website được truy cập. Nếu thông tin đạt yêu cầu browser sẽ tạo một khóa riêng cho phiên kết nối đó (session key), khóa này được mã hóa bằng public key và gửi nó đến server. Server dùng private key để giải mã session key và gửi lại tín hiệu đến browser để bắt đầu một phiên kết nối có ssl. 
#### -->   Private Key SSL đóng vai trò là chìa khóa để server có thể giải mã được thông tin từ client để bắt đầu một phiên kết nối SSL
--- 

### PFX là gì ? 
- File PFX (persional Exchange Format) còn được gọi là PKCS #12 là một định dạng tệp chứa các chứng chỉ bảo mật và các khóa mã hóa liên quan. Đây là tệp nhị phân lưu trữ cả public certificate và private key và thường được bảo vệ bằng mật khẩu. Nó thường được dùng để cài đặt SSL/TLS trên các web server hoặc để xuất nhập các chứng chỉ giữa các hệ thống khác nhau.
### Cách chuyển từ crt file sang PFX file ?
1. Truy cập vào đường dẫn https://www.httpcs.com/en/ssl-converter để convert sang file PFX
2. Import file lên để convert. Trước khi import file phải có 2 file .crt và .key. Ta lần lượt import file .crt và file .key vào sau đó chọn định dạng **PEM (.pem, .crt, .cer, .key)** tại **Current certificate format** và **PKCS#12/PFX(.pfx, .p12)** tại **Final conversion format** sau đó click **Convert**
3. Sau khi convert file xong thì ta tiến hành tải file về.

---
