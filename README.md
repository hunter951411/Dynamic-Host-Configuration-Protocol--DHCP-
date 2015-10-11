# Dich-vu-cung-cap-dia-chi-ip-dong-DHCP-Server
Dịch vụ cung cấp địa chỉ IP động (DHCP SERVER)


#1. Khái niệm

- Khi quản trị một hệ thống mạng, thường ta phải cung cấp một địa chỉ IP cho mỗi máy tính khác nhau để các máy này có thể liên lạc được với nhau. Với mô hình mạng nhỏ(khoảng 10 đến 20 máy), việc cung cấp IP cho mỗi máy tính cho mạng thì tương đối dễ dàng cho một quản trị viên, anh ta chỉ việc sử dụng vài thao tác quen thuộc trong việc gán các địa chỉ IP. Nhưng nếu đối với một mô hình mạng lớn (20 máy trở lên) thì việc cung cấp IP như thế là thật sự mệt mỏi và khó khăn rồi, thỉnh thoảng nếu có vấn đề di chuyển thường xuyên giữa những máy tính với nhau thì đây là một công việc khá phức tạp và phí sức.
- Chính vì những lý do như thế mà ngày nay, hầu hết trên tất cả các hệ điều hành cung cấp cho chúng ta một dịch vụ để giải quyết vấn đề cần thiết trên, đó là dịch vụ cung cấp địa chỉ IP động DHCP (Dynamic Host Configuration Protocol).
- Không những cung cấp được IP mà dịch vụ trên còn đưa cho chúng ta nhiều chức năng để cung cấp những yếu tố khác cho các máy client, ví dụ như cung cấp địa chỉ của máy tính dùng để giải quyết tên miền DNS, địa chỉ của một Gateway router, địa chỉ máy WINS....
- Thành phần của một DHCP server bao gồm 4 mục chính sau:

| Thành phần | Chức năng |
|------------|-----------|
| Options | Dùng để cung cấp địa chỉ IP, subnet mask, gateway. dns cho client |
| Scope | Một đoạn địa chỉ được quy định trước trên DHCP server mà chúng ta sẽ dùng để gán cho các máy client |
| Reservation | Là những đoạn địa chỉ dùng để "để dành" trong một scope mà chúng ta quy định ở trên |
| Lease | Thời gian "cho thuê" địa chỉ IP đối với mỗi client |

#2. Cài đặt

- Để sử dụng được dịch vụ DHCP này, bạn phải cài đặt vào hệ thống thông thường bằng gói dịch vụ có sẵn trên đĩa CD có phần đuôi mở rộng là .rpm, ngoài ra chúng ta có thể cài đặt package ở dạng source code và tải gói này về từ trang web của GNU. Quá trình cài đặt bao gồm những bước sau:
<ul>
<li>Ở dạng phần đuôi mở rộng là .rpm, ta chạy lệnh:</li>
    **rpm -ivh dhcp-*.rpm**
<li>Ở dạng source code, ta biên dịch như sau:</li>
tar -xzvf dhcp-*.rpm
cd dhcp-*
./configure
make
make install
</ul>

- Sau khi hoàn tất xong quá trình cài đặt, kế tiếp chúng ta sẽ cấu hình để dịch vụ này có thể chạy theo tùy chính rcuar chúng ta bằng cách tạo và sửa đổi file /etc/dhcpd.conf. Tập tin này sẽ có nội dung sau:


