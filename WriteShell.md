# ping và hping3
## ping  
Ping được viết tắt của từ Packet Internet Groper, là một công cụ cho mạng máy tính sử dụng trên các mạng TCP/IP để kiểm tra xem có thể kết nối tới một máy chủ cụ thể nào đó hay không. Ngoài ra, Ping còn ước lượng khoảng thời gian trễ trọn vòng để gửi gói dữ liệu cũng như tỉ lệ các gói dữ liệu có thể bị mất giữa hai máy.
### Hoạt động của ping 
- Máy tính hoặc thiết bị A sẽ gửi đi 1 tín hiệu, 1 gói tin - packet đến địa chỉ IP của máy tính, thiết bị B.
- Thiết bị B Có nhận được tín hiệu, gói tin - packet từ phía A hay không?
- Phản hồi từ B trả về cho A và hiển thị thành kết quả của lệnh Ping.
- ![text](./ImagerPing/Screenshot%20from%202025-03-26%2016-25-20.png)
### Thực hiện ping tới vietnix.vn
![text](./ImagerPing/Screenshot%20from%202025-03-26%2016-16-40.png)
- Giải thích: 
  + ` ttl `: Time To Live (TTL) là thời gian một đối tượng được lưu trữ trong hệ thống bộ nhớ đệm trước khi nó bị xóa hoặc làm mới. Trong trường hợp của CDN, Time to live thường đề cập đến bộ nhớ đệm nội dung, là quá trình lưu trữ bản sao tài nguyên trang web của bạn (ví dụ: hình ảnh, giá cả, văn bản) trên proxy CDN để cải thiện tốc độ tải trang và giảm tiêu thụ băng thông của server gốc.
  + ` time `: time thể hiện thời gian khứ hồi (RTT - Round Trip Time) của gói tin, được đo bằng đơn vị milliseconds (ms). Đây là thời gian mà một gói tin ICMP (Internet Control Message Protocol) cần để: Từ máy của bạn (máy phát) gửi gói tin đến máy chủ đích. Máy chủ đích nhận gói tin và gửi lại gói tin phản hồi. Gói tin phản hồi quay trở lại máy của bạn.
## hping3 
Hping3 - Công cụ quét mạng và máy phân tích cho giao thức TCP/IP được phân phối bởi Salvatore Sanfilippo (còn được gọi là Antirez).
Nó là một loại của một thửu nghiệm cho an ninh mạng. Nó là một trong những defacto cong cụ để kiểm tra an nih và thử nghiệm tường lửa.
Công cụ quét mạng hping là một bộ phân tích, phân tích gói tin TCP/IP theo định hướng dòng lệnh. Giao diện được lấy cảm ứng từ lệnh ping(8) Unix, nhưng hping không chỉ có thể gửi các yêu cầu echo ICMP. Nó hỗ trợ giao thức TCP, UDP, ICMP và RAW-IP, có chế độ traceroute, khẳ năng gửi tập tin giữa một kênh được bảo vệ và nhiều tính năng khác.
Trong khi hping chủ yếu được sử dụng như một Công cụ quét mạng trong quá khứ, nó có thể được sử dụng theo nhiều cách bởi những người không quan tâm đến bảo mật để kiểm tra mạng và máy chủ.
#### Thực hiện scan từ port 1 - 1000 mục tiêu là vietnix.vn
    `hping3 --scan 1-1000 -S vietnix.vn`
![text](./ImagerPing/Screenshot%20from%202025-03-26%2016-51-05.png)
#### Thực hiện scan port 80 và 443 mục tiêu là vietnix.vn
    `sudo hping3 --scan 80,443 -S vietnix.vn`
![text](./ImagerPing/Screenshot%20from%202025-03-26%2016-52-32.png)

---
# SSH command 
SSH (viết tắt của Secure Shell) là một giao thức mạng cho phép kết nối an toàn qua mạng không an toàn. Giao thức được phát triển bởi Tatu Ylonen vào năm 1995 để thay thế Telnet – một giao thức dễ bị tấn công. Lệnh ssh trong Linux sử dụng giao thức SSH nhằm đăng nhập và thực thi các lệnh trên server từ xa an toàn với tất cả dữ liệu được mã hóa.
#### Cú pháp
    `ssh [OPTION]... username@ip_address`
- Trong đó:
  + `[OPTIONS]`: Cho phép bạn thêm một hoặc nhiều tùy chọn cho lệnh ssh
  + `username`: Tên đăng nhập của bạn trên máy chủ mà bạn muốn kết nối.
  + `ip_address`: Địa chỉ IP của máy chủ.

#### Kết nối SSH sử dụng mật khẩu:
    `ssh username@hostname -p port_number`
- Trong đó: 
  + `username`: Tên người dùng trên máy chủ.
  + `hostname`: Địa chỉ hoặc tên miền của máy chủ.
  + `port_number`:  Sử dụng cổng SSH tùy chỉnh (nếu cần). Đây là tùy chọn.
- Sau khi nhập lệnh trên, bạn sẽ được yêu cầu nhập mật khẩu để kết nối đến máy chủ.
#### Kết nối SSH sử dụng khóa SSH (key):
    `ssh -i path/to/private_key username@hostname -p port_number`  
- Trong đó:
  + `-i path/to/private_key`: Đường dẫn đến khóa riêng tư SSH.
  + `username`: Tên người dùng trên máy chủ.
  + `hostname`: Địa chỉ hoặc tên miền của máy chủ.
  + `-p port_number`: Sử dụng cổng SSH tùy chỉnh (nếu cần). Đây là tùy chọn.
- Lệnh trên sẽ sử dụng khóa SSH thay vì mật khẩu để xác thực.
---
# SCP command 
#### scp 1 file hoặc 1 folder
    `scp [OPTION] [user_src@]src_host:]src_file [user@]desk_host:]des_file`
- Trong đó: 
  + `[user_src@]src_host:]src_file`:  là file, thư mục nguồn, ví dụ abcuser@192.168.1.55:/home/file1.txt là file /home/file1.txt tại máy abcuser@192.168.1.55, như dấu :, nếu là tại máy local thì không cần chỉ ra user, host tức bỏ đoạn abcuser@192.168.1.55:
  + `[user@]desk_host:]des_file` đường dẫn file, thư mục đích muốn copy - ý nghĩa tương tự như trên
  + `[OPTIONS]` các thiết lập cho thêm vào nếu muốn, như cho thêm tham số -r để đệ quy copy cả thư mục, các file, thư mục con theo đường dẫn.
---
# rsync command
#### Sao chép file từ máy cục bộ tới máy chủ từ xa:
    `rsync /path/to/local/file username@hostname:/path/to/remote/directory`
#### Sao chép file từ máy chủ từ xa về máy cục bộ:
    `rsync username@hostname:/path/to/remote/file /path/to/local/directory`
#### Đồng bộ hóa thư mục giữa hai máy chủ:
    `rsync -avz /path/to/source/directory username@hostname:/path/to/destination/directory`
#### Sử dụng SSH để kết nối và sao chép dữ liệu một cách an toàn:
    `rsync -e 'ssh -p port_number' /path/to/local/file username@hostname:/path/to/remote/directory`
---
# cat command 
#### cat nội dung 1 file 
    `cat filename`
#### cat dòng thứ <n> trong file 
    `sed -n 'n{p;q}' filename`
####
    `awk 'NR == n {print; exit}' n={desired_line_number} filename`
####
    `head -n filename | tail -1`
#### cat nhiều dòng vào 1 file bằng EOF (End Of File)
    ` cat << EOF >> output_file
        Dòng 1
        Dòng 2
        Dòng 3
        EOF `
---
# echo command 
#### Dùng echo để chèn thêm 1 dòng vào cuối file
    ` echo "Dòng cần chèn" >> ten_file `
#### Dùng echo để overwirte nội dung của file
    `echo "Nội dung mới" > ten_file`
---
# tail/head command
### tail command 
#### Sử dụng cơ bản:
    ` tail filename `
#### Hiển thị a dòng cuối file:
    ` tail -n a filename `
#### Hiển thị a dòng cuối file theo thời gian thực 
    ` tail -f a filename `
### head command 
#### Sử dụng cơ bản:
    ` head filename `
#### Hiển thị a dòng đầu tiên của file 
    ` head -n a filename `
---
# sed command
#### Dùng sed để find and replace một string trong file
    ` sed -i 's/Chuỗi_cần_tìm_kiếm_và_thay_thế/Chuỗi_thay_thế/g' filename `
- Ví dụ : `sed -i 's/hello/world/g' example.txt`
---
# traceroute/tracert command
#### Sau khi traceroute xong giải thích chi tiết kết quả trả về
    ` traceroute địa_chỉ_ip_hoặc_tên_miền `
![text](./ImagersCommand/Screenshot%20from%202025-03-27%2008-52-48.png)
##### Giải thích kết quả 
- `traceroute to 8.8.8.8 (8.8.8.8), 30 hops max, 60 byte packets`: Đây là thông điệp khởi đầu cho quá trình traceroute. Nó cho biết địa chỉ IP mà đang được traceroute (8.8.8.8), số lượng bước tối đa (30 hops), và kích thước gói tin (60 byte).
- `1 192.168.0.1 (192.168.0.1) 2.236 ms 2.300 ms 3.082 ms`: Đây là bước đầu tiên trong quá trình traceroute. Gói dữ liệu được gửi tới địa chỉ IP 192.168.0.1 (có thể là cổng router của bạn). Thời gian trễ trung bình để gói dữ liệu đi tới và trả về từ địa chỉ này lần lượt là 2.236 ms, 2.300 ms, và 3.082 ms.
- `2 localhost (27.71.251.149) 7.872 ms 7.772 ms 7.700 ms`: Bước tiếp theo là gửi gói dữ liệu tới địa chỉ IP 27.71.251.149 và thời gian trễ trung bình là 7.872 ms, 7.772 ms, và 7.700 ms.
- Các bước tiếp theo tương tự, với thời gian trễ và địa chỉ IP của các bước trung gian trên đường đi.
- `9 dns.google (8.8.8.8) 36.509 ms 45.709 ms 46.033 ms`:Cuối cùng, gói dữ liệu đến địa chỉ IP cuối cùng 8.8.8.8 (dns.google - máy chủ DNS của Google) với thời gian trễ trung bình là 36.509 ms, 45.709 ms, và 46.033 ms.
---
# netstat command
#### Hiển thị các socket đang listen:
    `netstat -l`
#### don't resolve hostname và don't resolve portname
    `netstart -n`
#### Hiển thị tên tiến trình/PID
    `netstat -p`
#### Chỉ hiển thị socket TCP:
    `netstat -t`
#### Chỉ hiển thị socket UDP:
    `netstat -u`
---
# sort command
#### Sắp xếp theo thứ tự tăng dần:
    `sort ten_file`
#### Sắp xếp theo thứ tự giảm dần:
    `sort -r ten_file`
#### Sắp xếp theo một cột x cụ thể:
    `sort -kx ten_file`
- Ví dụ: Để sắp xếp file data.txt theo cột thứ hai: `sort -k2 data.txt` 
---
# uniq command
#### Lọc ra các dòng lặp lại trong một file
    `uniq ten_file`
#### Lọc ra các dòng lặp lại và đếm số lượng các dòng lặp lại:
    `sort ten_file | uniq -c`
---
# wc command
#### Đếm số dòng trong file:
    `wc -l ten_file`
#### Đếm số kí tự trong file:
    `wc -c ten_file`
---
# chmod, chown, chattr command
#### Cấp quyền thực thi, đọc và ghi cho user, group và others:
    `chmod permissions ten_file`
- Ví dụ: Để cấp quyền thực thi cho user, đọc và ghi cho group, đọc cho others trên file script.sh: `chmod u+x,g+rw,o+r script.sh`
#### Đổi chủ sở hữu và nhóm sở hữu của file hoặc thư mục:
    `chown new_owner:new_group ten_file`
- Ví dụ: Để đổi chủ sở hữu của file data.txt thành newuser và nhóm sở hữu thành newgroup: `chown newuser:newgroup data.txt`
#### Gán thuộc tính Immutable cho file (không thể xóa hoặc thay đổi):
    `chattr +i ten_file`
- Ví dụ: Để gán thuộc tính Immutable cho file important_file.txt: `chattr +i important_file.txt`
#### Phân quyền bằng số : Các số 4 - 2 - 1 tương ứng đọc - ghi - thực thi 
- Ví dụ:  `chmod 755 solid.txt` thì user có quyền đọc ghi và thực thi, group có quyền đọc và thực thi, other có quyền đọc và thực thi 
---
# find command
#### Tìm các file có đuôi .log:
    `find /duong/dan -type f -name "*.log"`
- Ví dụ: Để tìm các file có đuôi .log trong thư mục hiện tại và tất cả các thư mục con: `find . -type f -name "*.log"`
#### Tìm các thư mục có tên abc:
    `find /duong/dan -type d -name "abc"`
- Ví dụ: Để tìm các thư mục có tên abc trong thư mục hiện tại và tất cả các thư mục con: `find . -type d -name "abc"`
#### Tìm các file có tên abc:
    ` find /duong/dan -type f -name "abc" `
- Ví dụ: Để tìm các file có tên abc trong thư mục hiện tại và tất cả các thư mục con: `find . -type f -name "abc"`
#### Tìm các file có tên abc và thực hiện phần quyền read only cho file:
    `find /duong/dan -type f -name "abc" -exec chmod a-w {} \;`
- Ví dụ: Để tìm các file có tên abc và thực hiện phần quyền read only cho các file đó: `find . -type f -name "abc" -exec chmod a-w {} \;` trong đó `-exec chmod a-w {} \;` sẽ thực hiện lệnh chmod a-w cho mỗi file kết quả tìm được, gỡ bỏ quyền ghi từ tất cả các user (user, group, others).

---
# cp command 
#### Sao chép một file:
    `cp duong_dan_file nguon_dan_dich`
- Ví dụ: Để sao chép file file.txt từ thư mục hiện tại sang thư mục /home/user/documents:  `cp file.txt /home/user/documents`
#### Sao chép một thư mục (với tất cả các file và thư mục con):
    `cp -r duong_dan_thu_muc nguon_dan_dich`
- Ví dụ: Để sao chép thư mục myfolder từ thư mục hiện tại sang thư mục /home/user/documents cùng với tất cả các file và thư mục con: `cp -r myfolder /home/user/documents` sử dụng tùy chọn -r để sao chép tất cả các file và thư mục con bên trong thư mục đó.
---
# mv command
#### Di chuyển/Đổi tên một file:
    `mv duong_dan_file nguon_dan_dich`
- Ví dụ: Để di chuyển file file.txt từ thư mục hiện tại sang thư mục /home/user/documents: `mv file.txt /home/user/documents`
#### Di chuyển/Đổi tên một thư mục:
    `mv duong_dan_thu_muc nguon_dan_dich`
- Ví dụ: Để di chuyển thư mục myfolder từ thư mục hiện tại sang thư mục /home/user/documents: `mv myfolder /home/user/documents`
---
# cut command 
#### Cắt kí tự thứ <n> trong string:
    `echo "Chuỗi cần cắt" | cut -c<n>`
- Ví dụ: Để cắt kí tự thứ 5 trong chuỗi "Hello World": `echo "Hello World" | cut -c5`
#### Cắt từ kí tự thứ <n> trở về sau:
    `echo "Chuỗi cần cắt" | cut -c<n>-`
- Ví dụ: Để cắt từ kí tự thứ 7 trở về sau trong chuỗi "Hello World": `echo "Hello World" | cut -c7-`
#### Cắt từ kí tự thứ <n> trở về trước:
    `echo "Chuỗi cần cắt" | rev | cut -c<n>-`
- Ví dụ: Để cắt từ kí tự thứ 3 trở về trước trong chuỗi "Hello World": `echo "Hello World" | rev | cut -c4-`
---
# dig command
#### Kiểm tra bản ghi A (địa chỉ IP), MX (mail exchange), NS (name server) mặc định:
#### Bản ghi A (địa chỉ IP): 
    `dig A ten_mien`
#### Bản ghi MX (mail exchange):
    `dig MX ten_mien`
#### Bản ghi NS (name server):
    `dig NS ten_mien`
#### Kiểm tra bản ghi A, MX, NS với custom DNS:
#### Ví dụ kiểm tra bản ghi A với custom DNS 8.8.8.8:
    `dig A ten_mien @8.8.8.8`
#### Ví dụ kiểm tra bản ghi MX với custom DNS 1.1.1.1:
    `dig MX ten_mien @1.1.1.1`
#### Ví dụ kiểm tra bản ghi NS với custom DNS 9.9.9.9:
    `dig NS ten_mien @9.9.9.9`
---
# tar/zip/unzip command
#### Nén file hoặc thư mục vào file tar.gz:
    `tar -czvf ten_file.tar.gz duong_dan_file`
#### Giải nén file tar.gz:
    `tar -xzvf ten_file.tar.gz`
#### Nén file hoặc thư mục vào file .zip:
    `zip ten_file.zip duong_dan_file`
#### Giải nén file .zip:
    `unzip ten_file.zip`
- Lưu ý:

+ Khi sử dụng tar, tùy chọn -c để tạo file, -z để sử dụng gzip để nén, -x để giải nén, -v để hiển thị tiến trình.
+ Khi sử dụng zip, bạn chỉ cần gọi lệnh zip để nén và unzip để giải nén.
---
# mount/umount command 
### Add thêm một ổ cứng sdb ~ 5gb
### Kiểm tra được có bao nhiêu ổ cứng trên máy chủ
### Mount ổ cứng vào /mnt/test
### Umount /mnt/test
---
#### Add thêm một ổ cứng sdb khoảng 5GB:
1. Đầu tiên, kết nối ổ cứng vật lý vào máy chủ của bạn.
2. Sau khi kết nối, hãy sử dụng lệnh fdisk để tạo phân vùng mới trên ổ cứng sdb và định dạng nó.
#### Kiểm tra số lượng ổ cứng trên máy chủ:
    `lsblk`
- Lệnh này sẽ hiển thị danh sách các ổ đĩa trên máy chủ của bạn.
#### Mount ổ cứng vào /mnt/test:
1. Tạo thư mục /mnt/test nếu nó chưa tồn tại:
####
    `mkdir /mnt/test`
2. Mount ổ cứng sdb vào /mnt/test:
####
    `mount /dev/sdb1 /mnt/test`
- Trong đó, /dev/sdb1 là phân vùng trên ổ cứng sdb.
#### Umount /mnt/test:
    `umount /mnt/test`
- Lệnh này sẽ ngắt kết nối ổ cứng sdb từ thư mục /mnt/test.
- Lưu ý: 
  + Trước khi thực hiện các thao tác này, hãy đảm bảo bạn có quyền root hoặc quyền sudo để thực hiện các thay đổi hệ thống.
  + Khi thêm ổ cứng mới, hãy chắc chắn rằng bạn đang làm việc trên ổ cứng đúng và lưu ý không ghi đè lên dữ liệu quan trọng.
---
# Symbolic Links, Hard Links command
## Symbolic Links (liên kết tượng trưng):
- Symbolic link là một loại liên kết trỏ đến một tập tin hoặc thư mục khác bằng một đường dẫn tương đối hoặc tuyệt đối.
- Khi bạn tạo một symbolic link, nó sẽ tạo ra một tập tin mới chứa đường dẫn đến tập tin hoặc thư mục mà nó trỏ đến.
## Hard Links (liên kết cứng):
- Hard link là một liên kết trực tiếp đến một tập tin hoặc thư mục khác trong hệ thống tập tin mà không có tập tin "gốc".
- Khi bạn tạo một hard link, cả hai liên kết sẽ trỏ đến cùng một vị trí dữ liệu trên ổ đĩa, và các liên kết này không thể tồn tại trên các hệ thống tập tin khác nhau.
## Ví dụ về Symbolic Link và Hard Link:
#### Ví dụ về Symbolic Link:
- Tạo một symbolic link từ /home/user/file.txt đến /tmp/file.txt:
#### 
    `ln -s /home/user/file.txt /tmp/file.txt`
- Khi bạn truy cập vào /tmp/file.txt, nó sẽ thực sự trỏ đến /home/user/file.txt.
#### Ví dụ về Hard Link:
- Tạo một hard link từ /var/log/syslog đến /tmp/syslog_backup:
#### 
    `ln /var/log/syslog /tmp/syslog_backup`
- Cả hai tập tin syslog và syslog_backup sẽ trỏ đến cùng một dữ liệu trên ổ đĩa và thay đổi ở một tập tin sẽ ảnh hưởng đến tập tin kia.
- Lưu ý:

  + Symbolic links cho phép trỏ đến các vị trí linh hoạt, trong khi hard links chỉ hoạt động trên cùng một hệ thống tập tin và cùng một ổ đĩa.
---
# ls command 
#### Liệt kê danh sách file/thư mục: `ls` 
#### Liệt kê danh sách file/thư mục và thuộc tính: `ls -l`
#### Hiển thị các file ẩn: `ls -a` 
---
# ps command 
#### Hiển thị danh sách các tiến trình: `ps`
#### Hiển thị danh sách các tiến trình chi tiết: `ps aux`
#### Kết thúc một tiến trình cụ thể (sử dụng kill):
1. Đầu tiên, bạn cần xác định ID của tiến trình mà bạn muốn kết thúc bằng cách sử dụng ps hoặc ps aux.
2. Sau đó, sử dụng lệnh kill PID với PID là ID của tiến trình để kết thúc tiến trình đó.
- Ví dụ kill tiến trình có PID: 12345 `kill 12345`
--- 
# top command 
#### Kiểm tra tài nguyên CPU đang sử dụng của các tiến trình:
1. Chạy lệnh `top` để mở giao diện hiển thị thông tin về các tiến trình và tài nguyên hệ thống.
2. Trong giao diện top, bạn có thể xem thông tin về CPU sử dụng của các tiến trình theo thời gian thực.
#### Giải thích về một số thông số quan trọng trong giao diện top:
- Load average: Load average là số liệu thống kê về tải hệ thống trong một khoảng thời gian nhất định. Nếu load average cao, có thể cho thấy hệ thống đang hoạt động quá tải.
- **us (user)**: Phần trăm CPU sử dụng bởi các tiến trình người dùng.
- **sy (system)**: Phần trăm CPU sử dụng bởi các tiến trình hệ thống.
- **ni (nice)**: Phần trăm CPU sử dụng bởi các tiến trình với độ ưu tiên cao.
- **id (idle)**: Phần trăm thời gian CPU không được sử dụng.
- **wa (wait)**: Phần trăm thời gian CPU đang chờ I/O hoàn thành.
- **hi (hardware interrupt)**: Phần trăm thời gian CPU sử dụng cho xử lý interrupt từ phần cứng.
- **si (software interrupt)**: Phần trăm thời gian CPU sử dụng cho xử lý interrupt từ phần mềm.
- **st (steal)**: Phần trăm thời gian CPU bị "đánh cắp" bởi máy ảo trong môi trường ảo hóa.
- **Zombie process**: Là một tiến trình đã kết thúc nhưng vẫn còn trong bảng tiến trình vì cha tiến trình chưa gọi wait().
- **Sleeping process**: Là các tiến trình đang chờ một sự kiện nào đó xảy ra để tiếp tục thực thi.
---
# free command 
- Trong Linux, lệnh free được sử dụng để hiển thị thông tin về bộ nhớ (RAM) đang được sử dụng trên hệ thống. Dưới đây là giải thích về các cột thông tin mà lệnh free cung cấp:
#### Giải thích về các cột thông tin trong kết quả của lệnh free:
- **total**: Tổng dung lượng bộ nhớ RAM trên hệ thống.
- **used**: Dung lượng RAM đang được sử dụng bởi các tiến trình và hệ thống.
- **free**: Dung lượng RAM hiện không được sử dụng và có sẵn cho các ứng dụng mới.
- **shared**: Dung lượng RAM được sử dụng chung bởi nhiều tiến trình.
- **buff/cache**: Dung lượng RAM được sử dụng cho việc đệm (buffer) và cache. Dữ liệu trong buffer thường là dữ liệu đang chờ được ghi vào đĩa, trong khi cache là dữ liệu đã được đọc từ đĩa và được lưu trữ trong RAM để truy cập nhanh hơn.
- **available**: Dung lượng RAM có sẵn cho các ứng dụng mới mà không cần phải swap ra đĩa.
---
# df command 
- Trong Linux, lệnh df được sử dụng để hiển thị thông tin về dung lượng đĩa (disk) trên hệ thống và việc sử dụng không gian đĩa. Dưới đây là cách sử dụng df để xem dung lượng đĩa và giải thích về phân vùng /:
#### Xem dung lượng đĩa sử dụng và còn trống trên hệ thống:
    `df -h`
- Lệnh này sẽ hiển thị thông tin về dung lượng đĩa sử dụng, dung lượng đĩa còn trống và tỷ lệ sử dụng trên hệ thống. Thêm -h để hiển thị dung lượng dưới dạng đơn vị dễ đọc (ví dụ: KB, MB, GB).
#### Giaỉ thích về phân vùng 
- Trong Linux, phân vùng / (gọi là "root partition") là phân vùng chứa hệ thống tập tin gốc của hệ điều hành. Tất cả các thư mục và tập tin trong hệ thống sẽ bắt đầu từ phân vùng này.
- Phân vùng / là phân vùng quan trọng nhất trên hệ thống vì nó chứa hệ thống tập tin và các thư mục quan trọng như /bin, /etc, /home, /usr, và các thư mục hệ thống khác.
---
