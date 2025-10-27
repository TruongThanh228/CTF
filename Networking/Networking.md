# Mô hình OSI :

1. **Lớp vật lý (Physical)**

Lớp vật lý, còn được gọi là lớp 1, xử lý kết nối vật lý giữa các thiết bị; bao gồm môi trường truyền dẫn, chẳng hạn như dây dẫn, và định nghĩa của các chữ số nhị phân 0 và 1. Việc truyền dữ liệu có thể được thực hiện thông qua tín hiệu điện, quang hoặc không dây. Do đó, chúng ta cần cáp dữ liệu hoặc ăng-ten, tùy thuộc vào môi trường truyền dẫn vật lý.



Ngoài cáp Ethernet, được hiển thị trong hình minh họa bên dưới, và cáp quang, các ví dụ về môi trường lớp vật lý bao gồm băng tần vô tuyến WiFi, băng tần 2,4 GHz, băng tần 5 GHz và băng tần 6 GHz.



Giao thức : Tín hiệu điện, quang và không dây



**2. Lớp liên kết dữ liệu (Data link)**

Tầng vật lý định nghĩa một phương tiện để truyền tín hiệu. Tầng liên kết dữ liệu, tức là tầng 2, đại diện cho giao thức cho phép truyền dữ liệu giữa các nút trên cùng một phân đoạn mạng. Nói một cách đơn giản hơn, tầng liên kết dữ liệu mô tả thỏa thuận giữa các hệ thống khác nhau trên cùng một phân đoạn mạng về cách thức giao tiếp. Phân đoạn mạng là một nhóm các thiết bị được kết nối mạng sử dụng một phương tiện hoặc kênh chung để truyền thông tin.



Ví dụ, hãy xem xét một văn phòng công ty có mười máy tính được kết nối với một bộ chuyển mạch mạng; đó là một phân đoạn mạng.

Giao thức : 	Ethernet (802.3), WiFi (802.11)



**3. Lớp mạng (Network)**

Lớp mạng, tức là lớp 3, chịu trách nhiệm gửi dữ liệu giữa các mạng khác nhau. Nói một cách kỹ thuật hơn, lớp mạng xử lý việc định địa chỉ và định tuyến logic, tức là tìm đường dẫn để truyền các gói tin mạng giữa các mạng khác nhau.



Trong lớp liên kết dữ liệu, chúng tôi đã đưa ra ví dụ về một văn phòng công ty có mười máy tính, trong đó lớp liên kết dữ liệu chịu trách nhiệm cung cấp kết nối giữa chúng. Giả sử công ty này có nhiều văn phòng phân bổ trên nhiều thành phố, quốc gia, hoặc thậm chí là các châu lục khác nhau. Lớp mạng chịu trách nhiệm kết nối các văn phòng khác nhau lại với nhau.



Giao thức  : IP, ICMP, IPSec



**4. Lớp vận chuyển (Transport)**

Lớp 4, lớp vận chuyển, cho phép giao tiếp đầu cuối giữa các ứng dụng đang chạy trên các máy chủ khác nhau. Trình duyệt web của bạn được kết nối với máy chủ web TryHackMe thông qua lớp vận chuyển, có thể hỗ trợ nhiều chức năng khác nhau như kiểm soát luồng, phân đoạn và sửa lỗi.



Ví dụ về lớp 4 là Giao thức điều khiển truyền dẫn ( TCP ) và Giao thức dữ liệu người dùng ( UDP ).



Giao thức : UDP , TCP



**5. Lớp phiên (Session)**

Lớp phiên chịu trách nhiệm thiết lập, duy trì và đồng bộ hóa giao tiếp giữa các ứng dụng chạy trên các máy chủ khác nhau. Thiết lập phiên nghĩa là khởi tạo giao tiếp giữa các ứng dụng và thương lượng các tham số cần thiết cho phiên. Đồng bộ hóa dữ liệu đảm bảo dữ liệu được truyền theo đúng thứ tự và cung cấp cơ chế phục hồi trong trường hợp lỗi truyền.



Ví dụ về lớp phiên là Hệ thống tệp mạng (NFS) và Gọi thủ tục từ xa (RPC).



Giao thức : 	NFS, RPC



**6. Lớp trình bày (Presentation)**

Lớp trình bày đảm bảo dữ liệu được truyền tải dưới dạng mà lớp ứng dụng có thể hiểu được. Lớp 6 xử lý việc mã hóa, nén và mã hóa dữ liệu. Một ví dụ về mã hóa là mã hóa ký tự, chẳng hạn như ASCII hoặc Unicode.



Nhiều tiêu chuẩn khác nhau được sử dụng ở lớp trình bày. Hãy xem xét trường hợp chúng ta muốn gửi một hình ảnh qua email. Đầu tiên, chúng ta sử dụng JPEG, GIF và PNG để lưu hình ảnh; hơn nữa, mặc dù bị trình duyệt email ẩn khỏi người dùng, chúng ta sử dụng MIME (Tiện ích mở rộng Thư Internet Đa năng) để đính kèm tệp vào email. MIME mã hóa tệp nhị phân bằng các ký tự ASCII 7 bit.



Giao thức : Unicode, MIME , JPEG, PNG, MPEG



**7. Lớp ứng dụng (Application)**

   Lớp ứng dụng cung cấp các dịch vụ mạng trực tiếp cho các ứng dụng của người dùng cuối. Trình duyệt web của bạn sẽ sử dụng giao thức HTTP để yêu cầu tệp, gửi biểu mẫu hoặc tải tệp lên.



   Lớp ứng dụng là lớp trên cùng, và bạn có thể đã gặp nhiều giao thức của lớp này khi sử dụng các ứng dụng khác nhau. Ví dụ về các giao thức Lớp 7 là HTTP , FTP , DNS , POP3 , SMTP và             IMAP . Đừng lo lắng nếu bạn chưa quen thuộc với tất cả chúng.



Giao thức : HTTP , FTP , DNS , POP3 , SMTP , IMAP



# Mô hình TCP/IP :

**Lớp ứng dụng :** Trong mô hình OSI, lớp ứng dụng, lớp trình bày và lớp phiên, tức là lớp 5, 6 và 7, được nhóm vào lớp ứng dụng trong mô hình TCP /IP.

**Lớp vận chuyển :** Đây là lớp 4.

**Lớp Internet :** Đây là lớp 3. Lớp mạng của mô hình OSI được gọi là lớp Internet trong mô hình TCP /IP.

**Lớp liên kết :** Đây là lớp 2.



# Địa chỉ IP và Mạng con :

Mỗi máy chủ trên mạng cần một mã định danh duy nhất để các máy chủ khác có thể giao tiếp với nó. Nếu không có mã định danh duy nhất, máy chủ sẽ không thể được tìm thấy mà không gây nhầm lẫn. Khi sử dụng bộ giao thức TCP /IP, chúng ta cần gán một địa chỉ IP cho mỗi thiết bị được kết nối vào mạng.



Một ví dụ tương tự của địa chỉ IP chính là địa chỉ bưu điện nhà bạn. Địa chỉ bưu điện cho phép bạn nhận thư từ và bưu kiện từ khắp nơi trên thế giới. Hơn nữa, nó có thể xác định chính xác nhà bạn; nếu không, bạn sẽ không thể mua sắm trực tuyến!



Như bạn có thể đã biết, chúng ta có IPv4 và IPv6 (IP phiên bản 6). IPv4 vẫn là giao thức phổ biến nhất, và bất cứ khi nào bạn gặp một văn bản đề cập đến IP mà không có phiên bản, chúng tôi cho rằng họ đang nói đến IPv4.



Vậy, địa chỉ IP được tạo nên như thế nào? Địa chỉ IP bao gồm bốn octet, tức là 32 bit. Với 8 bit, một octet cho phép chúng ta biểu diễn một số thập phân từ 0 đến 255.

Ví dụ :   192       .       168        .      1       .        1

     Octet#1(0-255)   Octet#2(0-255)   Octet#3(0-255)   Octet#4(0-255)



Để đơn giản hóa vấn đề, 0 và 255 được dành riêng cho địa chỉ mạng và địa chỉ phát sóng. Nói cách khác, 192.168.1.00 là địa chỉ mạng, còn 192.168.1.255255 là địa chỉ phát sóng. Việc gửi đến địa chỉ phát sóng sẽ nhắm đến tất cả các máy chủ trên mạng. Với phép tính đơn giản, bạn có thể kết luận rằng chúng ta không thể có hơn 4 tỷ địa chỉ IPv4 duy nhất.(2^32)



Tra cứu cấu hình mạng

Bạn có thể tra cứu địa chỉ IP của mình trên dòng lệnh MS Windows bằng lệnh ipconfig. Trên các hệ thống Linux và UNIX, bạn có thể dùng lệnh ifconfighoặc ip address show, có thể được nhập là ip a s



**1. Địa chỉ riêng tư**

RFC 1918 định nghĩa ba dải địa chỉ IP riêng sau đây:

10.0.0.0- 10.255.255.255( 10/8)

172.16.0.0- 172.31.255.255( 172.16/12)

192.168.0.0- 192.168.255.255( 192.168/16)



**2. Router**

Bộ định tuyến giống như bưu điện địa phương của bạn; bạn giao bưu kiện cho họ, và họ sẽ biết cách chuyển phát. Nếu tìm hiểu sâu hơn, bạn có thể gửi một thứ gì đó đến một địa chỉ ở một thành phố hoặc quốc gia khác. Bưu điện sẽ kiểm tra địa chỉ và quyết định nơi gửi tiếp theo. Ví dụ, nếu hàng hóa được gửi ra nước ngoài, chúng tôi mong đợi một bưu cục trung tâm sẽ xử lý tất cả các lô hàng ra nước ngoài.



Về mặt kỹ thuật, bộ định tuyến chuyển tiếp các gói dữ liệu đến mạng phù hợp. Thông thường, một gói dữ liệu sẽ đi qua nhiều bộ định tuyến trước khi đến đích cuối cùng. Bộ định tuyến hoạt động ở lớp 3, kiểm tra địa chỉ IP và chuyển tiếp gói đến mạng tốt nhất (bộ định tuyến) để gói đến gần đích hơn.



# UDP và TCP :

1. **UDP**

UDP (Giao thức gói dữ liệu người dùng) cho phép chúng ta tiếp cận một tiến trình cụ thể trên máy chủ đích này. UDP là một giao thức phi kết nối đơn giản hoạt động ở lớp vận chuyển, tức là lớp 4. Phi kết nối nghĩa là nó không cần thiết lập kết nối. UDP thậm chí không cung cấp cơ chế để biết gói tin đã được gửi hay chưa.



Địa chỉ IP xác định máy chủ; chúng ta cần một cơ chế để xác định quá trình gửi và nhận. Điều này có thể đạt được bằng cách sử dụng số cổng. Một số cổng sử dụng hai octet; do đó, nó nằm trong khoảng từ 1 đến 65535; cổng 0 được dành riêng. (Số 65535 được tính bằng biểu thức 2^16 - 1.)



Một ví dụ thực tế tương tự UDP là dịch vụ thư tiêu chuẩn, không có xác nhận giao hàng. Nói cách khác, không có gì đảm bảo rằng gói tin UDP đã được nhận thành công, tương tự như trường hợp gửi bưu kiện bằng thư tiêu chuẩn mà không có xác nhận giao hàng. Trong trường hợp thư tiêu chuẩn, chi phí rẻ hơn so với các tùy chọn giao hàng có xác nhận. Trong trường hợp UDP , tốc độ nhanh hơn so với giao thức truyền tải cung cấp "xác nhận".



**2. TCP**

TCP (Giao thức Điều khiển Truyền) là một giao thức truyền tải hướng kết nối. Nó sử dụng nhiều cơ chế khác nhau để đảm bảo việc truyền dữ liệu đáng tin cậy được gửi bởi các tiến trình khác nhau trên các máy chủ mạng. Giống như UDP , đây là giao thức lớp 4. Vì hướng kết nối, TCP yêu cầu thiết lập kết nối TCP trước khi bất kỳ dữ liệu nào có thể được gửi.



Trong TCP , mỗi octet dữ liệu có một số thứ tự; điều này giúp bên nhận dễ dàng xác định các gói tin bị mất hoặc trùng lặp. Mặt khác, bên nhận xác nhận việc nhận dữ liệu bằng một số xác nhận, chỉ rõ octet cuối cùng đã nhận.



Kết nối TCP được thiết lập bằng cái gọi là bắt tay ba bước. Hai cờ được sử dụng: SYN (Đồng bộ hóa) và ACK (Xác nhận). Các gói tin được gửi như sau:

Gói SYN: Máy khách khởi tạo kết nối bằng cách gửi một gói SYN đến máy chủ. Gói này chứa số thứ tự ban đầu được máy khách chọn ngẫu nhiên.

Gói SYN-ACK: Máy chủ phản hồi gói SYN bằng gói SYN-ACK, gói này sẽ thêm số thứ tự ban đầu do máy chủ chọn ngẫu nhiên.

Gói ACK: Quá trình bắt tay ba chiều được hoàn tất khi máy khách gửi gói ACK để xác nhận đã nhận được gói SYN-ACK.



Tương tự như UDP , TCP xác định quá trình khởi tạo hoặc chờ (lắng nghe) kết nối bằng số cổng. Như đã nêu, số cổng hợp lệ nằm trong khoảng từ 1 đến 65535 vì nó sử dụng hai octet và cổng 0 được dành riêng.



# Đóng gói :

Trước khi kết thúc, điều quan trọng là phải giải thích một khái niệm quan trọng khác: đóng gói . Trong bối cảnh này, đóng gói đề cập đến quá trình mỗi lớp thêm một tiêu đề (và đôi khi là một phần đuôi) vào đơn vị dữ liệu đã nhận và gửi đơn vị "được đóng gói" xuống lớp bên dưới.



Đóng gói là một khái niệm thiết yếu vì nó cho phép mỗi lớp tập trung vào chức năng dự định của nó. Trong hình ảnh bên dưới, chúng ta có bốn bước sau:

Dữ liệu ứng dụng : Mọi thứ bắt đầu khi người dùng nhập dữ liệu họ muốn gửi vào ứng dụng. Ví dụ: bạn soạn email hoặc tin nhắn tức thời và nhấn nút gửi. Ứng dụng sẽ định dạng dữ liệu này và bắt đầu gửi theo giao thức ứng dụng được sử dụng, sử dụng lớp bên dưới nó, lớp vận chuyển.

Phân đoạn giao thức vận chuyển hoặc datagram : Lớp vận chuyển, chẳng hạn như TCP hoặc UDP , thêm thông tin tiêu đề thích hợp và tạo phân đoạn TCP (hoặc datagram UDP ). Phân đoạn này được gửi đến lớp bên dưới nó, lớp mạng.

Gói tin mạng : Tầng mạng, tức là tầng Internet, thêm tiêu đề IP vào phân đoạn TCP hoặc gói tin UDP đã nhận . Sau đó, gói tin IP này được gửi đến tầng bên dưới nó, tầng liên kết dữ liệu.

Khung liên kết dữ liệu : Ethernet hoặc WiFi nhận gói tin IP và thêm phần đầu và phần cuối thích hợp, tạo thành một khung .



Chúng ta bắt đầu với dữ liệu ứng dụng. Ở tầng vận chuyển, chúng ta thêm tiêu đề TCP hoặc UDP để tạo phân đoạn TCP hoặc gói tin UDP . Ở tầng mạng, chúng ta thêm tiêu đề IP phù hợp để tạo gói tin IP có thể được định tuyến qua Internet. Cuối cùng, chúng ta thêm tiêu đề và đuôi phù hợp để tạo khung WiFi hoặc Ethernet ở tầng liên kết.



Quá trình này phải được đảo ngược ở phía nhận cho đến khi dữ liệu ứng dụng được trích xuất.



# Telnet :

Giao thức TELNET (Mạng Teletype) là một giao thức mạng cho kết nối thiết bị đầu cuối từ xa. Nói một cách đơn giản hơn, telnet TELNET Client cho phép bạn kết nối và giao tiếp với một hệ thống từ xa và đưa ra các lệnh văn bản. Mặc dù ban đầu nó được sử dụng cho quản trị từ xa, nhưng chúng ta có thể sử dụng nó telnet để kết nối với bất kỳ máy chủ nào đang lắng nghe trên một số cổng TCP .



# DHCP: Cung cấp cho tôi cài đặt mạng của tôi

Bất cứ khi nào chúng ta muốn truy cập vào mạng, ít nhất chúng ta cần cấu hình những điều sau:

Địa chỉ IP cùng với mặt nạ mạng con

Bộ định tuyến (hoặc cổng)

Máy chủ DNS



Bất cứ khi nào chúng ta kết nối thiết bị với một mạng mới, các cấu hình trên phải được thiết lập theo mạng mới. Việc cấu hình thủ công các thiết lập này là một lựa chọn tốt, đặc biệt là đối với máy chủ. Máy chủ không cần phải chuyển đổi mạng; bạn không cần phải mang theo bộ điều khiển miền và kết nối nó với WiFi của quán cà phê. Hơn nữa, các thiết bị khác cần kết nối với máy chủ và mong đợi tìm thấy chúng ở các địa chỉ IP cụ thể.



Việc tự động cấu hình các thiết bị được kết nối mang lại nhiều lợi ích. Thứ nhất, nó giúp chúng ta không phải cấu hình mạng thủ công; điều này cực kỳ quan trọng, đặc biệt là đối với các thiết bị di động. Thứ hai, nó giúp chúng ta tránh khỏi xung đột địa chỉ, tức là khi hai thiết bị được cấu hình với cùng một địa chỉ IP. Xung đột địa chỉ IP sẽ ngăn các máy chủ liên quan sử dụng tài nguyên mạng; điều này áp dụng cho cả tài nguyên cục bộ và Internet. Giải pháp nằm ở việc sử dụng Giao thức Cấu hình Máy chủ Động ( DHCP ). DHCP là một giao thức cấp ứng dụng dựa trên UDP ; máy chủ lắng nghe trên cổng UDP 67, và máy khách gửi dữ liệu qua cổng UDP 68. Điện thoại thông minh và máy tính xách tay của bạn được cấu hình để sử dụng DHCP theo mặc định.



DHCP thực hiện theo bốn bước: Khám phá, Đề xuất, Yêu cầu và Xác nhận (DORA):

DHCP Discover : Máy khách phát đi thông báo DHCPDISCOVER để tìm kiếm máy chủ DHCP cục bộ nếu có.

DHCP Offer : Máy chủ phản hồi bằng tin nhắn DHCPOFFER với địa chỉ IP có sẵn để máy khách chấp nhận.

Yêu cầu DHCP : Máy khách phản hồi bằng tin nhắn DHCPREQUEST để cho biết rằng máy khách đã chấp nhận IP được cung cấp.

DHCP Acknowledge : Máy chủ phản hồi bằng tin nhắn DHCPACK để xác nhận rằng địa chỉ IP được cung cấp hiện đã được gán cho máy khách này.



Khi kết thúc quá trình DHCP , thiết bị của chúng ta sẽ nhận được tất cả cấu hình cần thiết để truy cập mạng hoặc thậm chí là Internet. Cụ thể, chúng tôi kỳ vọng máy chủ DHCP đã cung cấp cho chúng ta những thông tin sau:

Địa chỉ IP được thuê để truy cập tài nguyên mạng

Cổng định tuyến các gói tin của chúng tôi ra bên ngoài mạng cục bộ

Máy chủ DNS để phân giải tên miền (sẽ nói thêm về điều này sau)



# ARP: Kết nối địa chỉ lớp 3 với địa chỉ lớp 2

Giao thức Phân giải Địa chỉ (ARP) cho phép tìm địa chỉ MAC của một thiết bị khác trên Ethernet. Trong ví dụ dưới đây, một máy chủ có địa chỉ IP 192.168.66.89 muốn giao tiếp với một hệ thống khác có cùng địa chỉ IP 192.168.66.1. Nó gửi một Yêu cầu ARP yêu cầu máy chủ có địa chỉ IP 192.168.66.1phản hồi. Yêu cầu ARP được gửi từ địa chỉ MAC của máy yêu cầu đến địa chỉ MAC quảng bá, ff:ff:ff:ff:ff:ff như được hiển thị trong gói tin đầu tiên. ARP Reply đến ngay sau đó, và máy chủ có địa chỉ IP 192.168.66.1phản hồi với địa chỉ MAC của nó. Từ thời điểm này, hai máy chủ có thể trao đổi các khung dữ liệu lớp liên kết.



# ICMP: Xử lý sự cố mạng

Giao thức Tin nhắn Điều khiển Internet (ICMP) chủ yếu được sử dụng để chẩn đoán và báo cáo lỗi mạng. Hai lệnh phổ biến dựa trên ICMP đóng vai trò quan trọng trong việc khắc phục sự cố mạng và bảo mật mạng. Các lệnh đó là:

ping: Lệnh này sử dụng ICMP để kiểm tra kết nối với hệ thống đích và đo thời gian khứ hồi (RTT). Nói cách khác, nó có thể được sử dụng để xác định xem mục tiêu có hoạt động hay không và phản hồi của nó có thể đến được hệ thống của chúng tôi hay không.

traceroute: Lệnh này được gọi traceroute trên các hệ thống Linux và UNIX cũng như tracert trên các hệ thống MS Windows. Lệnh này sử dụng ICMP để khám phá tuyến đường từ máy chủ của bạn đến đích.



**Ping :**

Có thể bạn chưa từng chơi bóng bàn trước đây; tuy nhiên, nhờ ICMP, giờ đây bạn có thể chơi bóng bàn trên máy tính! ping Lệnh này sẽ gửi một Yêu cầu Phản hồi ICMP (Loại ICMP 8).



**Theo dõi tuyến đường(Traceroute) :**

Giao thức Internet có một trường gọi là Thời gian sống ( TTL ), cho biết số lượng bộ định tuyến tối đa mà một gói tin có thể đi qua trước khi bị loại bỏ. Bộ định tuyến sẽ giảm giá trị TTL của gói tin đi một trước khi gửi nó đi. Khi TTL về 0, bộ định tuyến sẽ loại bỏ gói tin và gửi thông báo ICMP Time Exceeded (Loại ICMP 11). (Trong ngữ cảnh này, "thời gian" được đo bằng số lượng bộ định tuyến, không phải giây.)

# 

# Lộ trình(Routing) :

Các thuật toán định tuyến nằm ngoài phạm vi của phòng này; tuy nhiên, chúng tôi sẽ mô tả ngắn gọn một số giao thức định tuyến để bạn làm quen với tên của chúng:

* OSPF (Open Shortest Path First) : OSPF là một giao thức định tuyến cho phép các bộ định tuyến chia sẻ thông tin về cấu trúc mạng và tính toán các đường dẫn hiệu quả nhất để truyền dữ liệu. Giao thức này thực hiện điều này bằng cách cho các bộ định tuyến trao đổi thông tin cập nhật về trạng thái của các liên kết và mạng được kết nối. Nhờ đó, mỗi bộ định tuyến có một bản đồ mạng hoàn chỉnh và có thể xác định các tuyến đường tốt nhất để đến đích.
* EIGRP (Giao thức Định tuyến Cổng Nội bộ Nâng cao) : EIGRP là giao thức định tuyến độc quyền của Cisco, kết hợp các khía cạnh của nhiều thuật toán định tuyến khác nhau. Nó cho phép các bộ định tuyến chia sẻ thông tin về các mạng mà chúng có thể tiếp cận và chi phí (như băng thông hoặc độ trễ) liên quan đến các tuyến đường đó. Sau đó, các bộ định tuyến sử dụng thông tin này để chọn đường dẫn hiệu quả nhất cho việc truyền dữ liệu.
* BGP (Giao thức Cổng Biên giới) : BGP là giao thức định tuyến chính được sử dụng trên Internet. Nó cho phép các mạng khác nhau (như mạng của Nhà cung cấp Dịch vụ Internet) trao đổi thông tin định tuyến và thiết lập đường dẫn cho dữ liệu di chuyển giữa các mạng này. BGP giúp đảm bảo dữ liệu có thể được định tuyến hiệu quả trên Internet, ngay cả khi truyền qua nhiều mạng.
* RIP (Giao thức Thông tin Định tuyến) : RIP là một giao thức định tuyến đơn giản thường được sử dụng trong các mạng nhỏ. Các bộ định tuyến chạy RIP chia sẻ thông tin về các mạng mà chúng có thể tiếp cận và số lượng hop (bộ định tuyến) cần thiết để đến đó. Kết quả là, mỗi bộ định tuyến xây dựng một bảng định tuyến dựa trên thông tin này, chọn các tuyến đường có ít hop nhất để đến mỗi đích.



# NAT :

Như đã thảo luận trong phòng Khái niệm Mạng , chúng tôi đã tính toán rằng IPv4 có thể hỗ trợ tối đa bốn tỷ thiết bị. Với sự gia tăng số lượng thiết bị kết nối Internet, từ máy tính và điện thoại thông minh đến camera an ninh và máy giặt, rõ ràng là không gian địa chỉ IPv4 sẽ nhanh chóng cạn kiệt. Một giải pháp để giải quyết vấn đề cạn kiệt này là Chuyển đổi Địa chỉ Mạng (NAT).



Ý tưởng đằng sau NAT nằm ở việc sử dụng một địa chỉ IP công cộng để cung cấp quyền truy cập Internet cho nhiều địa chỉ IP riêng . Nói cách khác, nếu bạn đang kết nối một công ty với hai mươi máy tính, bạn có thể cung cấp quyền truy cập Internet cho tất cả hai mươi máy tính bằng cách sử dụng một địa chỉ IP công cộng duy nhất thay vì hai mươi địa chỉ IP công cộng. (Lưu ý: Về mặt kỹ thuật, số lượng địa chỉ IP luôn được biểu thị bằng lũy ​​thừa của hai. Chính xác hơn về mặt kỹ thuật, với NAT, bạn dành riêng hai địa chỉ IP công cộng thay vì ba mươi hai. Do đó, bạn sẽ tiết kiệm được ba mươi địa chỉ IP công cộng. )



Không giống như định tuyến, vốn là cách tự nhiên để định tuyến các gói tin đến máy chủ đích, các bộ định tuyến hỗ trợ NAT phải tìm cách theo dõi các kết nối đang diễn ra. Do đó, các bộ định tuyến hỗ trợ NAT duy trì một bảng chuyển đổi địa chỉ mạng giữa mạng nội bộ và mạng bên ngoài. Thông thường, mạng nội bộ sẽ sử dụng dải địa chỉ IP riêng, trong khi mạng bên ngoài sẽ sử dụng địa chỉ IP công cộng.



# DNS: Ghi nhớ địa ch

Bạn có nhớ địa chỉ IP của các trang web yêu thích của mình không? Trừ khi đó là địa chỉ IP riêng của một thiết bị cục bộ, không ai cần phải lo lắng về việc ghi nhớ địa chỉ IP. Điều này một phần là nhờ Hệ thống Tên miền ( DNS ), chịu trách nhiệm ánh xạ chính xác tên miền với địa chỉ IP.



DNS hoạt động ở Lớp Ứng dụng, tức là Lớp 7 của mô hình OSI ISO. Lưu lượng DNS sử dụng cổng UDP 53 theo mặc định và cổng TCP 53 làm cổng dự phòng mặc định. Có nhiều loại bản ghi DNS ; tuy nhiên, trong bài tập này, chúng ta sẽ tập trung vào bốn loại sau:

* Bản ghi A : Bản ghi A (Địa chỉ) ánh xạ tên máy chủ thành một hoặc nhiều địa chỉ IPv4. Ví dụ: bạn có thể thiết lập example.com để phân giải thành 172.17.2.172.
* Bản ghi AAAA : Bản ghi AAAA tương tự như Bản ghi A, nhưng dành cho IPv6. Lưu ý rằng nó là AAAA (quad-A), vì AA và AAA dùng để chỉ dung lượng pin; hơn nữa, AAA dùng để chỉ Xác thực, Ủy quyền và Kế toán ; cả hai đều không thuộc DNS .
* Bản ghi CNAME : Bản ghi CNAME (Tên chuẩn) ánh xạ một tên miền sang một tên miền khác. Ví dụ: www.example.com có thể được ánh xạ đến example.com hoặc thậm chí đến example.org.
* Bản ghi MX : Bản ghi MX (Trao đổi thư) chỉ định máy chủ thư chịu trách nhiệm xử lý email cho một tên miền.



Nói cách khác, khi bạn nhập example.comvào trình duyệt, trình duyệt sẽ cố gắng phân giải tên miền này bằng cách truy vấn máy chủ DNS để tìm bản ghi A. Tuy nhiên, khi bạn cố gắng gửi email đến test@example.com, máy chủ thư sẽ truy vấn máy chủ DNS để tìm bản ghi MX.



Nếu bạn muốn tra cứu địa chỉ IP của một tên miền từ dòng lệnh, bạn có thể sử dụng một công cụ như nslookup.



# WHOIS :

Bạn có thể tra cứu hồ sơ WHOIS của bất kỳ tên miền đã đăng ký nào bằng một trong các dịch vụ trực tuyến hoặc thông qua công cụ dòng lệnh whois, có sẵn trên hệ thống Linux , cùng nhiều công cụ khác. Đúng như dự kiến, hồ sơ WHOIS cung cấp thông tin về chủ thể đã đăng ký tên miền, bao gồm tên, số điện thoại, email và địa chỉ. Trong ảnh chụp màn hình bên dưới, bạn có thể thấy thời điểm hồ sơ được tạo lần đầu và thời điểm cập nhật lần cuối. Ngoài ra, bạn có thể tìm thấy tên, địa chỉ, số điện thoại và email của người đăng ký.



# HTTP(S) : Truy cập Web

Khi khởi động trình duyệt, bạn chủ yếu sử dụng giao thức HTTP và HTTPS. HTTP là viết tắt của Hypertext Transfer Protocol (Giao thức truyền siêu văn bản); chữ S trong HTTPS là viết tắt của Secure (Bảo mật). Giao thức này dựa trên TCP và xác định cách trình duyệt web của bạn giao tiếp với máy chủ web.



Một số lệnh hoặc phương thức mà trình duyệt web của bạn thường gửi tới máy chủ web là:

* GET lấy dữ liệu từ máy chủ, chẳng hạn như tệp HTML hoặc hình ảnh.
* POST cho phép chúng ta gửi dữ liệu mới tới máy chủ, chẳng hạn như gửi biểu mẫu hoặc tải tệp lên.
* PUT được sử dụng để tạo tài nguyên mới trên máy chủ và cập nhật và ghi đè thông tin hiện có.
* DELETE, như tên gọi của nó, được sử dụng để xóa một tệp hoặc tài nguyên được chỉ định trên máy chủ.



HTTP và HTTPS thường sử dụng cổng TCP 80 và 443, ít phổ biến hơn là các cổng khác như 8080 và 8443.



# FTP : Truyền tệp

Không giống như HTTP , được thiết kế để truy xuất các trang web, Giao thức Truyền Tệp ( FTP ) được thiết kế để truyền tệp. Do đó, FTP rất hiệu quả trong việc truyền tệp và khi tất cả các điều kiện đều như nhau, nó có thể đạt tốc độ cao hơn HTTP .



Các lệnh ví dụ được định nghĩa bởi giao thức FTP là:

* USER được sử dụng để nhập tên người dùng
* PASS được sử dụng để nhập mật khẩu
* RETR(lấy) được sử dụng để tải xuống tệp từ máy chủ FTP tới máy khách.
* STOR(store) được sử dụng để tải tệp từ máy khách lên máy chủ FTP .



Máy chủ FTP lắng nghe trên cổng TCP 21 theo mặc định; việc truyền dữ liệu được thực hiện thông qua một kết nối khác từ máy khách đến máy chủ.



# SMTP : Gửi email

Giống như việc duyệt web và tải xuống tệp, việc gửi email cũng cần có giao thức riêng. Giao thức Truyền Thư Đơn giản ( SMTP ) xác định cách máy khách thư giao tiếp với máy chủ thư và cách máy chủ thư giao tiếp với máy chủ thư khác.



Giao thức SMTP tương tự như khi bạn đến bưu điện địa phương để gửi một gói hàng. Bạn chào nhân viên, cho họ biết địa điểm bạn muốn gửi gói hàng và cung cấp thông tin người gửi trước khi giao gói hàng. Tùy thuộc vào quốc gia bạn đang ở, bạn có thể được yêu cầu xuất trình chứng minh thư. Quy trình này không khác mấy so với một phiên SMTP .



Chúng ta hãy cùng tìm hiểu một số lệnh mà máy khách thư của bạn sử dụng khi chuyển email đến máy chủ SMTP :

* HELO hoặc EHLO khởi tạo phiên SMTP
* MAIL FROM chỉ định địa chỉ email của người gửi
* RCPT TO chỉ định địa chỉ email của người nhận
* DATA chỉ ra rằng máy khách sẽ bắt đầu gửi nội dung của tin nhắn email
* .được gửi trên một dòng riêng để chỉ ra sự kết thúc của tin nhắn email



# POP3 : Nhận email

Bạn đã nhận được một email và muốn tải xuống máy khách thư cục bộ của mình. Giao thức Bưu điện phiên bản 3 ( POP3 ) được thiết kế để cho phép máy khách giao tiếp với máy chủ thư và nhận email.



Không đi sâu vào chi tiết kỹ thuật, một ứng dụng email sẽ gửi thư dựa trên SMTP và nhận chúng bằng POP3 . SMTP tương tự như việc bạn đưa phong bì hoặc bưu kiện đến bưu điện, còn POP3 tương tự như việc kiểm tra hộp thư địa phương của bạn để tìm thư hoặc bưu kiện mới.



Một số lệnh POP3 phổ biến là:

* USER <username>xác định người dùng
* PASS <password>cung cấp mật khẩu của người dùng
* STAT yêu cầu số lượng tin nhắn và tổng kích thước
* LIST liệt kê tất cả các tin nhắn và kích thước của chúng
* RETR <message\_number> lấy lại tin nhắn đã chỉ định
* DELE <message\_number> đánh dấu một tin nhắn để xóa
* QUIT kết thúc phiên POP3 bằng cách áp dụng các thay đổi, chẳng hạn như xóa



# IMAP : Đồng bộ hóa email

POP3 là đủ khi làm việc trên một thiết bị, ví dụ như ứng dụng email yêu thích của bạn trên máy tính để bàn. Tuy nhiên, nếu bạn muốn kiểm tra email từ máy tính để bàn ở cơ quan và từ máy tính xách tay hoặc điện thoại thông minh thì sao? Trong trường hợp này, bạn cần một giao thức cho phép đồng bộ hóa thư thay vì xóa thư sau khi nhận. Một giải pháp để duy trì hộp thư được đồng bộ hóa trên nhiều thiết bị là Giao thức Truy cập Thư Internet ( IMAP ).



IMAP cho phép đồng bộ hóa các thư đã đọc, đã di chuyển và đã xóa. IMAP khá tiện lợi khi bạn kiểm tra email qua nhiều máy khách. Không giống như POP3 , vốn có xu hướng giảm thiểu dung lượng lưu trữ máy chủ khi email được tải xuống và xóa khỏi máy chủ từ xa, IMAP có xu hướng sử dụng nhiều dung lượng lưu trữ hơn vì email được lưu trữ trên máy chủ và được đồng bộ hóa trên các máy khách email.



Các lệnh giao thức IMAP phức tạp hơn các lệnh giao thức POP3 . Chúng tôi liệt kê một vài ví dụ dưới đây:

* LOGIN <username> <password> xác thực người dùng
* SELECT <mailbox> chọn thư mục hộp thư để làm việc
* FETCH <mail\_number> <data\_item\_name> Ví dụ fetch 3 body\[] để lấy tin nhắn số 3, tiêu đề và nội dung.
* MOVE <sequence\_set> <mailbox> di chuyển các tin nhắn đã chỉ định đến hộp thư khác
* COPY <sequence\_set> <data\_item\_name> sao chép các tin nhắn đã chỉ định vào hộp thư khác
* LOGOUT đăng xuất

# 

# TLS

TLS là một giao thức mật mã hoạt động ở tầng vận chuyển của mô hình OSI. Nó cho phép giao tiếp an toàn giữa máy khách và máy chủ qua một mạng không an toàn. "An toàn" ở đây có nghĩa là bảo mật và toàn vẹn; TLS đảm bảo rằng không ai có thể đọc hoặc sửa đổi dữ liệu được trao đổi. Hãy dành một phút để suy nghĩ về việc mua sắm trực tuyến, giao dịch ngân hàng trực tuyến, hoặc thậm chí nhắn tin và email trực tuyến sẽ như thế nào nếu không thể đảm bảo tính bảo mật và toàn vẹn của các gói tin mạng. Nếu không có TLS, chúng ta sẽ không thể sử dụng Internet cho nhiều ứng dụng hiện đang là một phần trong thói quen hàng ngày của chúng ta.



Ngày nay, hàng chục giao thức đã được nâng cấp bảo mật chỉ với việc bổ sung TLS. Ví dụ bao gồm HTTP , DNS , MQTT và SIP, nay đã trở thành HTTPS, DoT ( DNS qua TLS), MQTTS và SIPS, trong đó chữ "S" được thêm vào là viết tắt của Secure (Bảo mật) do sử dụng SSL/TLS. Trong các bài tập sau, chúng ta sẽ tìm hiểu về HTTPS, SMTPS, POP3S và IMAPS.



# HTTPS

**HTTP**

HTTP dựa trên TCP và mặc định sử dụng cổng 80. Chúng ta cũng đã thấy cách tất cả lưu lượng HTTP được gửi dưới dạng văn bản thuần túy để bất kỳ ai cũng có thể chặn và giám sát. Ảnh chụp màn hình bên dưới được chụp từ phòng trước, cho thấy rõ cách kẻ tấn công có thể dễ dàng đọc được tất cả lưu lượng được trao đổi giữa máy khách và máy chủ.



Các bước phổ biến nhất trước khi trình duyệt web có thể yêu cầu một trang qua HTTP . Sau khi phân giải tên miền thành địa chỉ IP, máy khách sẽ thực hiện hai bước sau:

Thiết lập bắt tay ba chiều TCP với máy chủ mục tiêu

Giao tiếp bằng giao thức HTTP ; ví dụ, đưa ra các yêu cầu HTTP , chẳng hạn nhưGET / HTTP/1.1



**HTTP qua TLS**

HTTPS là viết tắt của Hypertext Transfer Protocol Secure (Giao thức Truyền Siêu văn bản An toàn). Về cơ bản, nó là HTTP qua TLS. Do đó, việc yêu cầu một trang qua HTTPS sẽ yêu cầu ba bước sau (sau khi phân giải tên miền):



Thiết lập bắt tay ba chiều TCP với máy chủ mục tiêu

Thiết lập phiên TLS

Giao tiếp bằng giao thức HTTP ; ví dụ, đưa ra các yêu cầu HTTP , chẳng hạn nhưGET / HTTP/1.1

Ảnh chụp màn hình bên dưới cho thấy một phiên TCP được thiết lập trong ba gói tin đầu tiên, được đánh dấu bằng 1. Sau đó, một số gói tin



**Nhận khóa mã hóa**

Việc thêm TLS vào HTTP dẫn đến việc tất cả các gói tin đều được mã hóa. Chúng ta không thể xem nội dung của các gói tin được trao đổi trừ khi có quyền truy cập vào khóa riêng. Mặc dù khả năng chúng ta có quyền truy cập vào các khóa được sử dụng để mã hóa trong phiên TLS là rất thấp, chúng tôi đã lặp lại các ảnh chụp màn hình ở trên sau khi cung cấp khóa giải mã cho Wireshark. Quá trình bắt tay TCP và TLS không thay đổi; sự khác biệt chính bắt đầu từ giao thức HTTP được đánh dấu 3. Ví dụ: chúng ta có thể thấy khi máy khách phát hành lệnh GET.



Điểm mấu chốt là TLS cung cấp bảo mật cho HTTP mà không yêu cầu bất kỳ thay đổi nào trong các giao thức tầng thấp hơn hoặc tầng cao hơn. Nói cách khác, TCP và IP không bị thay đổi, trong khi HTTP được gửi qua TLS theo cách nó được gửi qua TCP .



# SMTPS, POP3S và IMAPS

Việc thêm TLS vào SMTP , POP3 và IMAP cũng không khác gì việc thêm TLS vào HTTP . Tương tự như cách HTTP được thêm chữ S (viết tắt của Secure ) và trở thành HTTPS, SMTP , POP3 và IMAP lần lượt trở thành SMTPS, POP3S và IMAPS. Việc sử dụng các giao thức này qua TLS cũng không khác gì việc sử dụng HTTP qua TLS; do đó, hầu hết các điểm trong phần thảo luận về HTTPS đều áp dụng cho các giao thức này.



Protocol         Port

HTTP             80

HTTPS            443

SMTP             25

SMTPS            465 và 587

POP3             110

POP3S            995

IMAP             143

IMAPS            993



# SSH

OpenSSH mang lại nhiều lợi ích. Chúng tôi sẽ liệt kê một vài điểm chính:

Xác thực an toàn : Bên cạnh xác thực dựa trên mật khẩu, SSH hỗ trợ khóa công khai và xác thực hai yếu tố.

Bảo mật : OpenSSH cung cấp mã hóa đầu cuối, bảo vệ chống nghe lén. Hơn nữa, nó còn thông báo cho bạn về các khóa máy chủ mới để bảo vệ chống lại các cuộc tấn công trung gian.

Tính toàn vẹn : Ngoài việc bảo vệ tính bảo mật của dữ liệu trao đổi, mật mã còn bảo vệ tính toàn vẹn của lưu lượng.

Đường hầm : SSH có thể tạo một "đường hầm" an toàn để định tuyến các giao thức khác qua SSH . Thiết lập này dẫn đến một kết nối giống như VPN .

Chuyển tiếp X11 : Nếu bạn kết nối với hệ thống giống Unix có giao diện người dùng đồ họa, SSH cho phép bạn sử dụng ứng dụng đồ họa qua mạng.



Bạn sẽ ra lệnh ssh username@hostnamekết nối đến máy chủ SSH . Nếu tên người dùng trùng với tên người dùng đã đăng nhập, bạn chỉ cần ssh hostname. Sau đó, bạn sẽ được yêu cầu nhập mật khẩu; tuy nhiên, nếu sử dụng xác thực khóa công khai, bạn sẽ được đăng nhập ngay lập tức.



# SFTP và FTPS

SFTP là viết tắt của Giao thức Truyền Tệp SSH (SSH File Transfer Protocol) và cho phép truyền tệp an toàn. SFTP là một phần của bộ giao thức SSH và dùng chung cổng 22. Nếu được bật trong cấu hình máy chủ OpenSSH, bạn có thể kết nối bằng lệnh như sftp username@hostname. Sau khi đăng nhập, bạn có thể dùng lệnh như get filename và put filename để tải xuống và tải lên tệp tương ứng. Nhìn chung, các lệnh SFTP tương tự Unix và có thể khác với lệnh FTP .



Không nên nhầm lẫn SFTP với FTPS. Bạn hoàn toàn đúng khi cho rằng FTPS là viết tắt của Giao thức Truyền Tệp Bảo mật (File Transfer Protocol Secure). FTPS được bảo mật như thế nào? Đúng vậy, bạn hoàn toàn đúng khi cho rằng nó được bảo mật bằng TLS, giống như HTTPS. Trong khi FTP sử dụng cổng 21, FTPS thường sử dụng cổng 990. Nó yêu cầu thiết lập chứng chỉ, và việc cho phép truy cập qua tường lửa nghiêm ngặt có thể gặp khó khăn vì nó sử dụng các kết nối riêng biệt để kiểm soát và truyền dữ liệu.



Việc thiết lập máy chủ SFTP cũng dễ dàng như việc bật tùy chọn trong máy chủ OpenSSH. Giống như HTTPS, SMTPS, POP3S, IMAPS và các giao thức khác dựa trên TLS để bảo mật, FTPS yêu cầu chứng chỉ TLS phù hợp để chạy an toàn.



# Mạng riêng ảo (VPN)

Hãy xem xét một công ty có văn phòng ở nhiều vị trí địa lý khác nhau. Liệu công ty này có thể kết nối tất cả văn phòng và địa điểm của mình với chi nhánh chính để mọi thiết bị đều có thể truy cập tài nguyên dùng chung như thể đang ở chi nhánh chính không? Câu trả lời là có; hơn nữa, giải pháp tiết kiệm nhất sẽ là thiết lập mạng riêng ảo ( VPN ) sử dụng cơ sở hạ tầng Internet. Trọng tâm ở đây là chữ V (Virtual) trong VPN .



Khi Internet được thiết kế, bộ giao thức TCP /IP tập trung vào việc phân phối các gói tin. Ví dụ, nếu một bộ định tuyến ngừng hoạt động, các giao thức định tuyến có thể điều chỉnh và chọn một tuyến đường khác để gửi các gói tin của chúng. Nếu một gói tin không được xác nhận, TCP có các cơ chế tích hợp để phát hiện tình huống này và gửi lại. Tuy nhiên, không có cơ chế nào được thiết lập để đảm bảo rằng tất cả dữ liệu ra vào máy tính được bảo vệ khỏi bị tiết lộ và thay đổi. Một giải pháp phổ biến là thiết lập kết nối VPN . Trọng tâm ở đây là chữ P (Private) trong VPN .



Hầu hết các công ty đều yêu cầu trao đổi thông tin "riêng tư" trong mạng ảo của họ. Vì vậy, VPN cung cấp một giải pháp rất tiện lợi và tương đối tiết kiệm chi phí. Yêu cầu chính là kết nối Internet và máy chủ VPN cùng máy khách.



Sau khi đường hầm VPN được thiết lập, tất cả lưu lượng truy cập Internet của chúng ta thường sẽ được định tuyến qua kết nối VPN , tức là thông qua đường hầm VPN . Do đó, khi chúng ta cố gắng truy cập một dịch vụ Internet hoặc ứng dụng web, họ sẽ không thấy địa chỉ IP công khai của chúng ta mà là địa chỉ IP của máy chủ VPN . Đây là lý do tại sao một số người dùng Internet kết nối qua VPN để vượt qua các hạn chế về địa lý. Hơn nữa, ISP địa phương sẽ chỉ thấy lưu lượng được mã hóa, điều này hạn chế khả năng kiểm duyệt truy cập Internet của họ.



Nói cách khác, nếu người dùng kết nối với máy chủ VPN tại Nhật Bản, họ sẽ được hiển thị trên máy chủ họ truy cập như thể đang ở Nhật Bản. Các máy chủ này sẽ tùy chỉnh trải nghiệm của họ cho phù hợp, chẳng hạn như chuyển hướng họ đến phiên bản tiếng Nhật của dịch vụ. Ảnh chụp màn hình bên dưới hiển thị trang Google Tìm kiếm sau khi kết nối với máy chủ VPN tại Nhật Bản.



Cuối cùng, mặc dù trong nhiều trường hợp, người ta sẽ thiết lập kết nối VPN để định tuyến toàn bộ lưu lượng qua đường hầm VPN , nhưng một số kết nối VPN lại không làm như vậy. Máy chủ VPN có thể được cấu hình để cho phép bạn truy cập vào mạng riêng nhưng không phải để định tuyến lưu lượng của bạn. Hơn nữa, một số máy chủ VPN làm rò rỉ địa chỉ IP thực của bạn, mặc dù chúng được kỳ vọng sẽ định tuyến toàn bộ lưu lượng của bạn qua VPN . Tùy thuộc vào lý do bạn sử dụng kết nối VPN , bạn có thể cần chạy thêm một vài bài kiểm tra, chẳng hạn như kiểm tra rò rỉ DNS .



Cuối cùng, một số quốc gia coi việc sử dụng VPN là bất hợp pháp và thậm chí có thể bị phạt. Vui lòng kiểm tra luật pháp và quy định địa phương trước khi sử dụng VPN, đặc biệt là khi đi du lịch.



# Tcpdump

**Chụp gói tin cơ bản**

* tcpdump -i INTERFACE : 	Bắt các gói tin trên một giao diện mạng cụ thể
* tcpdump -w FILE : Ghi các gói tin đã chụp vào một tệp
* tcpdump -r FILE : Đọc các gói tin đã chụp từ một tệp
* tcpdump -c COUNT : Chụp một số lượng gói tin cụ thể
* tcpdump -n : Không giải quyết địa chỉ IP
* tcpdump -nn : Không giải quyết địa chỉ IP và không giải quyết số giao thức
* tcpdump -v : Hiển thị chi tiết; mức độ chi tiết có thể được tăng lên với -vv và -vvv



Ví dụ sau:

* tcpdump -i eth0 -c 50 -v thu thập và hiển thị 50 gói tin bằng cách lắng nghe trên eth0giao diện là Ethernet có dây và hiển thị chúng một cách chi tiết.
* tcpdump -i wlo1 -w data.pcap bắt các gói tin bằng cách lắng nghe trên wlo1giao diện (giao diện WiFi) và ghi các gói tin vào data.pcap. Quá trình này sẽ tiếp tục cho đến khi người dùng ngắt quá trình bắt bằng cách nhấn CTRL-C.
* tcpdump -i any -nn thu thập các gói tin trên tất cả các giao diện và hiển thị chúng trên màn hình mà không cần phân giải tên miền hoặc giao thức.



**Lọc biểu thức**

* tcpdump host IP hoặc tcpdump host HOSTNAME : Lọc các gói tin theo địa chỉ IP hoặc tên máy chủ
* tcpdump src host IP : Lọc các gói tin theo máy chủ nguồn cụ thể
* tcpdump dst host IP : Lọc các gói tin theo máy chủ đích cụ thể
* tcpdump port PORT\_NUMBER : Lọc các gói tin theo số cổng
* tcpdump src port PORT\_NUMBER : Lọc các gói tin theo số cổng nguồn được chỉ định
* tcpdump dst port PORT\_NUMBER : Lọc các gói tin theo số cổng đích đã chỉ định
* tcpdump PROTOCOL : Lọc các gói tin theo giao thức; ví dụ bao gồm ip, ip6, và icmp



Các ví dụ sau:

* tcpdump -i any tcp port 22 lắng nghe trên tất cả các giao diện và bắt tcp các gói tin đến hoặc đi port 22, tức là lưu lượng SSH .
* tcpdump -i wlo1 udp port 123lắng nghe trên card mạng WiFi và lọc udp lưu lượng đến port 123Giao thức thời gian mạng ( NTP ).
* tcpdump -i eth0 host example.com and tcp port 443 -w https.pcap sẽ lắng nghe trên eth0, giao diện Ethernet có dây và lọc lưu lượng được trao đổi với example.com giao diện đó sử dụng tcp và port 443. Nói cách khác, lệnh này đang lọc lưu lượng HTTPS liên quan đến example.com.

**Lọc nâng cao**

Còn rất nhiều cách khác để lọc gói tin. Xét cho cùng, trong bất kỳ tình huống thực tế nào, chúng ta cũng cần lọc qua hàng nghìn, thậm chí hàng triệu gói tin. Việc có thể biểu diễn chính xác các gói tin cần hiển thị là điều không thể thiếu. Ví dụ, chúng ta có thể giới hạn các gói tin được hiển thị ở mức nhỏ hơn hoặc lớn hơn một độ dài nhất định:

greater LENGTH: Lọc các gói tin có độ dài lớn hơn hoặc bằng độ dài đã chỉ định

less LENGTH: Lọc các gói tin có độ dài nhỏ hơn hoặc bằng độ dài đã chỉ định

Byte tiêu đề

Mục đích của phần này là để lọc các gói tin dựa trên nội dung của một byte tiêu đề. Hãy xem xét các giao thức sau: ARP , Ethernet, ICMP, IP, TCP và UDP . Đây chỉ là một vài giao thức mạng mà chúng ta đã nghiên cứu. Làm thế nào để yêu cầu Tcpdump lọc các gói tin dựa trên nội dung của các byte tiêu đề giao thức? (Chúng ta sẽ không đi sâu vào chi tiết về tiêu đề của từng giao thức vì điều này nằm ngoài phạm vi của bài viết này; thay vào đó, chúng ta sẽ tập trung vào các cờ TCP .)



Khi sử dụng pcap -filter, Tcpdump cho phép bạn tham chiếu đến nội dung của bất kỳ byte nào trong tiêu đề bằng cú pháp sau proto\[expr:size], trong đó:

proto đề cập đến giao thức. Ví dụ: arp, ether, icmp, ip, ip6, tcp, và udp đề cập đến ARP , Ethernet, ICMP, IPv4, IPv6, TCP và UDP tương ứng.

expr biểu thị độ lệch byte, trong đó 0tham chiếu đến byte đầu tiên.

size cho biết số byte mà chúng ta quan tâm, có thể là một, hai hoặc bốn. Giá trị này là tùy chọn và mặc định là một.



Để hiểu rõ hơn về điều này, hãy xem xét hai ví dụ sau từ trang hướng dẫn pcap -filter (và đừng lo lắng nếu bạn thấy chúng khó):

* ether\[0] \& 1 != 0lấy byte đầu tiên trong tiêu đề Ethernet và số thập phân 1 (tức là 0000 0001ở dạng nhị phân) và áp dụng \&(phép toán nhị phân And). Bộ lọc sẽ trả về true nếu kết quả không bằng số 0 (tức là 0000 0000). Mục đích của bộ lọc này là hiển thị các gói tin được gửi đến một địa chỉ đa hướng. Địa chỉ Ethernet đa hướng là một địa chỉ cụ thể xác định một nhóm thiết bị dự định nhận cùng một dữ liệu.
* ip\[0] \& 0xf != 5lấy byte đầu tiên trong tiêu đề IP và so sánh nó với số thập lục phân F (tức là 0000 1111ở dạng nhị phân). Bộ lọc sẽ trả về true nếu kết quả không bằng số (thập phân) 5 (tức là 0000 0101ở dạng nhị phân). Mục đích của bộ lọc này là bắt tất cả các gói tin IP có tùy chọn.
* Đừng lo lắng nếu bạn thấy hai ví dụ trên phức tạp. Chúng tôi đã đưa chúng vào để bạn biết mình có thể đạt được những gì; tuy nhiên, việc hiểu đầy đủ các ví dụ trên không nhất thiết phải hoàn thành nhiệm vụ này. Thay vào đó, chúng ta sẽ tập trung vào việc lọc các gói tin TCP dựa trên các cờ TCP đã thiết lập .



Bạn có thể sử dụng tcp\[tcpflags] để tham chiếu đến trường cờ TCP . Các cờ TCP sau đây có sẵn để so sánh:

* tcp-syn TCP SYN (Đồng bộ hóa)
* tcp-ack TCP ACK (Xác nhận)
* tcp-fin TCP FIN (Kết thúc)
* tcp-rst TCP RST (Đặt lại)
* tcp-push Đẩy TCP



Dựa trên những điều trên, chúng ta có thể viết:

* tcpdump "tcp\[tcpflags] == tcp-syn" để bắt các gói tin TCP chỉ có cờ SYN (Đồng bộ hóa) được đặt, trong khi tất cả các cờ khác đều không được đặt.
* tcpdump "tcp\[tcpflags] \& tcp-syn != 0" để bắt các gói tin TCP có ít nhất cờ SYN (Đồng bộ hóa) được đặt.
* tcpdump "tcp\[tcpflags] \& (tcp-syn|tcp-ack) != 0" để nắm bắt các gói tin TCP có ít nhất cờ SYN (Đồng bộ hóa) hoặc ACK (Xác nhận) được đặt.



**Hiển thị các gói tin**

* Tcpdump là một chương trình phong phú với nhiều tùy chọn để tùy chỉnh cách in và hiển thị các gói tin. Chúng tôi đã chọn đề cập đến năm tùy chọn sau:
* tcpdump -q : Nhanh chóng và yên tĩnh: thông tin gói ngắn gọn
* tcpdump -e : Bao gồm địa chỉ MAC
* tcpdump -A : In các gói tin dưới dạng mã hóa ASCII
* tcpdump -xx : Hiển thị các gói tin theo định dạng thập lục phân
* tcpdump -X : Hiển thị các gói tin theo cả định dạng thập lục phân và ASCII



# NMAP : THE BASICS

1. **Khám phá máy chủ: Ai đang trực tuyến**

Nmap sử dụng nhiều cách để xác định mục tiêu của mình:

* Phạm vi IP sử dụng - : Nếu bạn muốn quét tất cả các địa chỉ IP từ 192.168.0.1 đến 192.168.0.10, bạn có thể viết 192.168.0.1-10
* Mạng con IP sử dụng /: Nếu bạn muốn quét một mạng con, bạn có thể biểu thị nó như 192.168.0.1/24, và điều này sẽ tương đương với 192.168.0.0-255
* Tên máy chủ: Bạn cũng có thể chỉ định mục tiêu của mình theo tên máy chủ, ví dụ : example.thm

Nmap cung cấp **-sn** tùy chọn quét ping.

Chúng ta có thể kiểm soát tốt hơn cách Nmap phát hiện các máy chủ trực tiếp như -PS\[portlist], -PA\[portlist], -PU\[portlist]cho TCP SYN, TCP ACK và UDP discovery thông qua các cổng được chỉ định.

Cuối cùng, Nmap cung cấp tùy chọn quét danh sách **-sL**. Tùy chọn này chỉ liệt kê các mục tiêu cần quét mà không thực sự quét chúng. Ví dụ: nmap -sL 192.168.0.1/24 sẽ liệt kê 256 mục tiêu sẽ được quét. Tùy chọn này giúp xác nhận các mục tiêu trước khi thực hiện quét.

**2. Quét cổng: Ai đang nghe lén**

**Quét cổng TCP**

* Quét kết nối có thể được kích hoạt bằng cách sử dụng **-sT**. Nó sẽ cố gắng hoàn tất quá trình bắt tay ba chiều TCP với mọi cổng TCP đích. Nếu cổng TCP mở và Nmap kết nối thành công, Nmap sẽ hủy kết nối đã thiết lập.

**Quét SYN (Ẩn)**

* Không giống như quét kết nối, cố gắng kết nối đến cổng TCP đích , tức là hoàn tất bắt tay ba chiều, quét SYN chỉ thực hiện bước đầu tiên: nó gửi một gói tin TCP SYN. ​​Do đó, bắt tay ba chiều TCP không bao giờ được hoàn tất. Ưu điểm là điều này dự kiến ​​sẽ dẫn đến ít nhật ký hơn vì kết nối không bao giờ được thiết lập, và do đó, nó được coi là một quét tương đối bí mật. Bạn có thể chọn quét SYN bằng cách sử dụng **-sS** cờ.

**Quét cổng UDP**

* Mặc dù hầu hết các dịch vụ sử dụng TCP để giao tiếp, nhiều dịch vụ khác lại sử dụng UDP . Ví dụ bao gồm DNS , DHCP , NTP (Giao thức Thời gian Mạng), SNMP (Giao thức Quản lý Mạng Đơn giản) và VoIP (Thoại qua IP). UDP không yêu cầu thiết lập và ngắt kết nối sau đó. Hơn nữa, nó rất phù hợp cho giao tiếp thời gian thực, chẳng hạn như phát sóng trực tiếp. Tất cả những điều này là lý do để cân nhắc quét và khám phá các dịch vụ đang lắng nghe trên các cổng UDP .
* Nmap cung cấp tùy chọn -sUquét các dịch vụ UDP . Vì UDP đơn giản hơn TCP , chúng tôi dự đoán lưu lượng sẽ khác nhau.

**Giới hạn các cổng mục tiêu**

Theo mặc định, Nmap quét 1.000 cổng phổ biến nhất. Tuy nhiên, đây có thể không phải là điều bạn đang tìm kiếm. Do đó, Nmap cung cấp cho bạn một vài tùy chọn khác.

* -F dành cho chế độ Nhanh, quét 100 cổng phổ biến nhất (thay vì 1000 cổng mặc định).
* -p \[range]cho phép bạn chỉ định phạm vi cổng cần quét. Ví dụ: -p10-1024 quét từ cổng 10 đến cổng 1024, trong khi -p-25 quét tất cả các cổng từ 1 đến 25. Lưu ý rằng -p- quét tất cả các cổng và tương đương với -p1-65535và là lựa chọn tốt nhất nếu bạn muốn quét càng kỹ càng tốt.

**3. Phát hiện phiên bản: Trích xuất thêm thông tin**

**Phát hiện hệ điều hành**

Bạn có thể bật tính năng phát hiện hệ điều hành bằng cách thêm **-O** tùy chọn này. Đúng như tên gọi, tùy chọn phát hiện hệ điều hành sẽ kích hoạt Nmap dựa vào các chỉ số khác nhau để đưa ra dự đoán chính xác về hệ điều hành mục tiêu .

**Phát hiện dịch vụ và phiên bản**

Bạn đã phát hiện ra một số cổng mở và muốn biết những dịch vụ nào đang lắng nghe trên các cổng đó. -sVTính năng này cho phép phát hiện phiên bản. Điều này rất tiện lợi để thu thập thêm thông tin về mục tiêu của bạn mà chỉ cần ít lần nhấn phím hơn.

-> Nếu bạn có thể có cả -O, -sV và một số tùy chọn khác trong cùng một tùy chọn thì sao? Đó chính là -A. Tùy chọn này cho phép phát hiện hệ điều hành , quét phiên bản và theo dõi đường dẫn, cùng nhiều tính năng khác.

**Bắt buộc quét**

Khi chúng ta chạy quét cổng, chẳng hạn như sử dụng **-sS**, có khả năng máy chủ đích không phản hồi trong giai đoạn khám phá máy chủ (ví dụ: máy chủ không phản hồi yêu cầu ICMP). Do đó, Nmap sẽ đánh dấu máy chủ này là ngừng hoạt động và sẽ không khởi chạy quét cổng trên máy chủ đó. Chúng ta có thể yêu cầu Nmap coi tất cả máy chủ là trực tuyến và quét cổng trên mọi máy chủ, bao gồm cả những máy chủ không phản hồi trong giai đoạn khám phá máy chủ. Lựa chọn này có thể được kích hoạt bằng cách thêm **-Pn** tùy chọn.

**4. Thời gian: Nhanh thế nào là nhanh**

Nmap cung cấp nhiều tùy chọn khác nhau để kiểm soát tốc độ và thời gian quét :

* T0 (hoang tưởng)	9,8 giờ
* T1 (lén lút)	        27,53 phút
* T2 (lịch sự)	        40,56 giây
* T3 (bình thường)	0,15 giây
* T4 (hung hăng)	0,13 giây
* --min-parallelism <numprobes> Và --max-parallelism <numprobes>	Số lượng đầu dò song song tối thiểu và tối đa
* --min-rate <number>Và--max-rate <number>	                        Tốc độ tối thiểu và tối đa (gói/giây)
* --host-timeout	                                                Khoảng thời gian tối đa để chờ máy chủ đích

**5. Đầu ra: Kiểm soát những gì bạn nhìn thấy**

**Độ chi tiết và gỡ lỗi**

* Tùy chọn này rất có thể **-v** là quá đủ cho đầu ra chi tiết; tuy nhiên, nếu bạn vẫn chưa hài lòng, bạn có thể tăng mức độ chi tiết bằng cách thêm một ký tự "v" khác, chẳng hạn như -vvhoặc thậm chí **-vvvv**. Bạn cũng có thể chỉ định trực tiếp mức độ chi tiết, ví dụ, -v2 và -v4. Bạn thậm chí có thể tăng mức độ chi tiết bằng cách nhấn "v" sau khi quá trình quét đã bắt đầu.
* Nếu tất cả những điều rườm rà này không đáp ứng được nhu cầu của bạn, bạn phải cân nhắc **-d** đầu ra ở cấp độ gỡ lỗi. Tương tự, bạn có thể tăng cấp độ gỡ lỗi bằng cách thêm một hoặc nhiều ký tự "d" hoặc bằng cách chỉ định trực tiếp cấp độ gỡ lỗi. Cấp độ tối đa là **-d9**; trước khi chọn cấp độ này, hãy đảm bảo bạn đã sẵn sàng cho hàng ngàn thông tin và dòng gỡ lỗi.

**Lưu báo cáo quét**

Trong nhiều trường hợp, chúng ta cần lưu kết quả quét. Nmap cung cấp nhiều định dạng khác nhau. Ba định dạng hữu ích nhất là đầu ra bình thường (thân thiện với người dùng), đầu ra XML và đầu ra grepable, liên quan đến lệnh . grep Bạn có thể chọn định dạng báo cáo quét như sau:

* **-oN <filename>**- Đầu ra bình thường
* **-oX <filename>**- Đầu ra XML
* **-oG <filename>- grep**- đầu ra có thể (hữu ích cho grep và awk)
* **-oA <basename>**- Xuất ra tất cả các định dạng chính
