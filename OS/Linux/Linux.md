## [[Linux Folder]]
## Hyprland
- Wayland compositor
- [Hyprland Wiki](https://wiki.hyprland.org/)
- [https://github.com/JaKooLit/Debian-Hyprland](https://github.com/JaKooLit/Debian-Hyprland)
## Compositor
- Chịu trách nhiệm render và display window on the screen
- Xorg
- Wayland
## Display Manager
Hiển thị màn hình đăng nhập và quản lý phiên người dùng
- LightDM: Nhẹ
- GDM (GNOME Display Manager)
- KDE - KDE Display Manager
- SDDM - Simple Desktop Manager
## Desktop Environment
- Xfce
- GNOME
- KDE
## Base of Application
- Wayland - protocol
    - Sway
    - Hyprland
- X11- protocol
    - Firefox, xfce terminal
    - Xorg
- QT framework
- GTK toolkit
- Electron: Chronium
    - Visual Studio Code
    - Slack
# Linux Distribution
- **Thành phần:** Một bản distro điển hình bao gồm: một kernel Linux, các công cụ và thư viện GNU, các phần mềm thêm vào, phần document, một hệ thống window system (mà phần lớn là sử dụng XWindow System - hệ thống cửa sổ dùng để hiển thị đồ họa Bitmap), window manager và desktop environment.
- 3 nhánh distro chính
## Debian
- Hệ thống gói quản lý phần mềm sử dụng:
    - **`dpkg`** cài đặt các gói phần mềm `.deb`
    - **`apt`** cài đặt phần mềm từ các kho trên mạng. ((advanced package tool)
- Raspbian, Knoppix, Astra Linux, Kali Linux, ... và phổ biến nhất là nhánh **Ubuntu**
Display manager
- LightDM
- Sddm

## Fedora - Red Hat
- File `.rpm`
- Chu kì ra phiên bản mới của Fedora là 6 tháng. Phiên bản mới với các tính năng bảo mật mà các chuyên gia đánh giá khá tốt.
- Dùng **`yum`** để quản lý các gói phần mềm định dạng .rpm
- Fedora có thể dùng cho máy tính để bàn và máy trạm, thậm chí máy chủ; dành cho những người mới tiếp cận PMTDNM hay những người đã có nhiều kinh nghiệm.
- 2 distro phổ biến nhất được phát triển dựa trên Fedora là **Red Hat Enterprise Linux** - với đối tượng hướng tới là các doanh nghiệp và công ty lớn (tất nhiên là có tính phí) ; và **CentOS** - free và hướng tới đối tượng là người sử dụng cá nhân.
## Slackware