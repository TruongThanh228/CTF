Khi quét cổng bằng Nmap , có ba kiểu quét cơ bản. Đó là:

* Quét kết nối TCP (-sT) : quét TCP thực hiện bắt tay ba chiều đầy đủ với mục tiêu(Quét cổng: Tìm dịch vụ mở)
* Quét "Nửa mở" SYN (-sS) :  quét phạm vi cổng TCP của một hoặc nhiều mục tiêu
* Quét UDP (-sU) : Không giống như TCP , kết nối UDP không có trạng thái . Điều này có nghĩa là, thay vì khởi tạo kết nối bằng một "bắt tay" qua lại, kết nối UDP dựa vào việc gửi các gói tin đến một cổng đích và về cơ bản hy vọng chúng sẽ đến đích

Ngoài ra còn có một số loại quét cổng ít phổ biến hơn, một số trong đó chúng tôi cũng sẽ đề cập (mặc dù không chi tiết lắm). Đó là:

* Quét TCP Null (-sN)
* Quét TCP FIN (-sF)
* Quét TCP Xmas (-sX)
* Quét mạng ICMP (-sn) : chúng ta muốn xem địa chỉ IP nào chứa máy chủ đang hoạt động và địa chỉ nào thì không.

Có nhiều danh mục có sẵn. Một số danh mục hữu ích bao gồm:

* safe:- Sẽ không ảnh hưởng đến mục tiêu
* intrusive:- Không an toàn: có khả năng ảnh hưởng đến mục tiêu
* vuln:- Quét lỗ hổng bảo mật
* exploit:- Cố gắng khai thác lỗ hổng
* auth:- Cố gắng bỏ qua xác thực để chạy các dịch vụ (ví dụ: Đăng nhập vào máy chủ FTP ẩn danh)
* brute:- Cố gắng dùng vũ lực để lấy thông tin đăng nhập cho các dịch vụ đang chạy
* discovery:- Thử truy vấn các dịch vụ đang chạy để biết thêm thông tin về mạng (ví dụ: truy vấn máy chủ SNMP).

->Để chạy một tập lệnh cụ thể, chúng ta sẽ sử dụng --script=<script-name> , ví dụ --script=http-fileupload-exploiter

Giới hạn các cổng mục tiêu:

* -F dành cho chế độ Nhanh, quét 100 cổng phổ biến nhất (thay vì 1000 cổng mặc định).
* -p\[range]cho phép bạn chỉ định phạm vi cổng cần quét. Ví dụ: -p10-1024quét từ cổng 10 đến cổng 1024, trong khi -p-25quét tất cả các cổng từ 1 đến 25. Lưu ý rằng -p-quét tất cả các cổng và tương đương với -p1-65535và là lựa chọn tốt nhất nếu bạn muốn quét càng kỹ càng tốt.

Phát hiện phiên bản: Trích xuất thêm thông tin

* -O : Phát hiện hệ điều hành
* -sV : Phát hiện dịch vụ và phiên bản

Thời gian:

T0 (hoang tưởng, rất chậm) đến T5 (điên rồ, rất nhanh)

Lưu báo cáo quét:

* -oN <filename>- Đầu ra bình thường
* -oX <filename>- Đầu ra XML
* -oG <filename>- grep-đầu ra có thể (hữu ích cho grepvà awk)
* -oA <basename>- Xuất ra tất cả các định dạng chính
