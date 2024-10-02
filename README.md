#!/bin/sh
# Install Open VPN 2.13.1 treen Centos 7
yum install wget
wget https://github.com/income88/Unlimited-OpenVPN-2.13.1/openvpn_2_13_1.sh && sudo sh openvpn_2_13_1.sh

# Sao lưu dữ liệu từ server cũ
Dùng FileZilla để tạo đường dẫn: /path/to/backup/ cho Server Open VPN cần chuyển tới sau đó:

# Bước 1: Sao lưu dữ liệu từ server cũ
sudo systemctl stop openvpnas
sudo tar czvf openvpn_as_backup.tar.gz /usr/local/openvpn_as/
scp openvpn_as_backup.tar.gz root@172.27.105.31:/path/to/backup/    ----Thay TK root và IP server cần chuyển

# Bước 2: Phục hồi dữ liệu trên server mới
Cài đặt OpenVPN Access Server trên server mới: Trên server mới, cài đặt phiên bản OpenVPN Access Server cùng phiên bản với server cũ (phiên bản 2.14.1). Bạn có thể làm theo các hướng dẫn cài đặt chính thức của OpenVPN Access Server.
sudo systemctl stop openvpnas
sudo tar xzvf /path/to/backup/openvpn_as_backup.tar.gz -C /
sudo chown -R openvpn:openvpn /usr/local/openvpn_as
sudo systemctl start openvpnas
# Bước 3: Kiểm tra và cấu hình lại
Kiểm tra tường lửa và các quy tắc bảo mật trên server mới để đảm bảo rằng các cổng cần thiết (ví dụ: 1194, 443) được mở.
Sau khi hoàn tất, server OpenVPN mới của bạn sẽ hoạt động giống như server cũ với tất cả các cấu hình và dữ liệu người dùng đã được chuyển.
