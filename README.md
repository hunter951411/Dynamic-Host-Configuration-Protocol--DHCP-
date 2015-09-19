# Dynamic-Host-Configuration-Protocol--DHCP-
Hướng dẫn cấu hình DHCP Server trên CENTOS

- Dynamic Host Configuration Protocol (DHCP) là một giao thức mạng gán thông tin TCP/IP cho máy người dùng. Mỗi người dùng kết nối đến DHCP Server trung tâm, nơi trả về thông tin mạng cho người dùng gồm có địa chỉ IP, default gateway và DNS servers.

#1. Tại sao lại sử dụng DHCP

- DHCP tự động cấu hình interface  network cho người dùng. Khi cấu hình hệ thống người dùng, người quản trị chọn DHCP và thay vì nhập địa chỉ IP, netmask, gateway hay DNS server. Người dùng cuối sẽ lấy những thông tin này từ DHCP Server. DHCP chỉ sử dụng nếu người quản trị muốn gắn địa chỉ IP cho hệ thống người dùng lớn. Thay vì cấu hình lại tất cả hệ thống, Admin chỉ cần chỉnh sửa tập tin cấu hình DHCP trên máy chủ cho các thiết lập mới của địa chỉ IP. Nếu các máy chủ DNS cho một tổ chức thay đổi, những thay đổi được thực hiện trên máy chủ DHCP, không phải trên cái máy người dùng. Một khi mạng được khởi động lại (hoặc người dùng tự khỏi động lại), những thay đổi sẽ có hiệu lực.

- Hơn nữa, nếu một laptop hay một thiết bị di động của người dùng cấu hình dùng DHCP, nếu họ di chuyển từ địa điểm này đến địa điểm khác thì họ vẫn nhận được địa chỉ IP, netmask, getway, DNS server chính xác mà không cần phải cấu hình lại mỗi khi đến địa điểm mới.

#2. Cấu hình DHCP Server

- Để cấu hình một máy chủ DHCP, các tập tin cấu hình /etc/dhcpd.conf phải được tạo. Một tập tin mẫu có thể được tìm thấy tại /usr/share/doc/dhcp-<version>/dhcpd.conf.sample
- DHCP cũng sử dụng file /var/lb/dhcp/dhcpd.leases để lưu trữ cơ sở dữ liệu cấp phát cho người dùng. 

##2.1 Cấu hình file DHCP

- Bước đầu tiên trong việc cấu hình một máy chủ DHCP là để tạo ra các tập tin cấu hình lưu trữ thông tin về mạng cho khách hàng. Tùy chọn Global có thể được khai báo cho tất cả các client, trong khi tùy trọng khác con thể được khác báo cho hệ thống từng đối tượng client riêng biệt.

- Các tập tin cấu hình có thể chưa thêm các tab hoặc dòng trống để định dạng dễ dàng hơn, dòng bắt đầu với một dấu (#) được coi là ghi chú.

- Để sử dụng ad-hoc mode, thêm vào sau của tập tin cấu hình: 

| ddns-update-style ad-hoc; |
|---------------------------|

- Để sử dụng Recommended mode, thêm vào sau của tập tin cấu hình:

| ddns-update-style interim; |
|----------------------------|

#3. Cấu hình DHCP Client
