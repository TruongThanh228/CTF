# **DNS in Detail**

#### **What is DNS?(Domain Name System)**

DNS (Hệ thống Tên miền) cung cấp một cách đơn giản để chúng ta giao tiếp với các thiết bị trên Internet mà không cần phải nhớ những dãy số phức tạp. Giống như mỗi ngôi nhà đều có một địa chỉ duy nhất để gửi thư trực tiếp, mỗi máy tính trên Internet đều có một địa chỉ duy nhất để giao tiếp với nó, được gọi là địa chỉ IP. Địa chỉ IP trông như sau: 104.26.10.229, gồm 4 bộ chữ số từ 0 đến 255, được phân cách bằng dấu chấm. Khi bạn muốn truy cập một trang web, việc nhớ dãy số phức tạp này không thực sự tiện lợi, và đó chính là lúc DNS có thể giúp ích. Vì vậy, thay vì nhớ 104.26.10.229, bạn có thể nhớ tryhackme.com .



#### **Hệ thống phân cấp miền(Domain Hierarchy)**

**TLD (Tên miền cấp cao nhất)**

TLD là phần bên phải nhất của tên miền. Ví dụ, TLD của tryhackme.com là  .com . Có hai loại TLD: gTLD (Tên miền cấp cao nhất chung) và ccTLD (Tên miền cấp cao nhất theo mã quốc gia). Trước đây, gTLD nhằm mục đích cho người dùng biết mục đích của tên miền; ví dụ: .com dành cho mục đích thương mại, .org dành cho tổ chức, .edu dành cho giáo dục và .gov dành cho chính phủ. ccTLD cũng được sử dụng cho mục đích địa lý, ví dụ: .ca dành cho các trang web đặt tại Canada, .co.uk dành cho các trang web đặt tại Vương quốc Anh, v.v. Do nhu cầu như vậy, có rất nhiều gTLD mới xuất hiện, từ .online, .club, .website, .biz và nhiều hơn nữa. Để xem danh sách đầy đủ hơn 2000 TLD,  hãy nhấp vào đây .



**Tên miền cấp hai**

Lấy tryhackme.com làm ví dụ, phần .com là TLD, còn tryhackme là Tên miền Cấp hai. Khi đăng ký tên miền, tên miền cấp hai bị giới hạn ở 63 ký tự + TLD và chỉ có thể sử dụng các ký tự từ 0-9 và dấu gạch nối (không được bắt đầu hoặc kết thúc bằng dấu gạch nối hoặc có dấu gạch nối liền nhau).



**Tên miền phụ**

Tên miền phụ nằm ở phía bên trái của Tên miền cấp hai, sử dụng dấu chấm để phân tách; ví dụ: trong tên miền admin.tryhackme.com , phần quản trị là tên miền phụ. Tên miền phụ có cùng giới hạn tạo như Tên miền cấp hai, giới hạn ở 63 ký tự và chỉ được phép sử dụng các ký tự từ 0 đến 9 và dấu gạch nối (không được bắt đầu hoặc kết thúc bằng dấu gạch nối hoặc có dấu gạch nối liền nhau). Bạn có thể sử dụng nhiều tên miền phụ được phân tách bằng dấu chấm để tạo tên dài hơn, chẳng hạn như jupiter.servers.tryhackme.com . Tuy nhiên, độ dài phải được giữ ở mức 253 ký tự hoặc ít hơn. Không có giới hạn về số lượng tên miền phụ bạn có thể tạo cho tên miền của mình.



#### **Các loại bản ghi(DNS Record Types)**

**Các loại bản ghi DNS**

Tuy nhiên, DNS không chỉ dành cho trang web, và có rất nhiều loại bản ghi DNS khác nhau. Chúng tôi sẽ điểm qua một số loại phổ biến nhất mà bạn có thể gặp phải.



**Một Kỷ Lục**

Các bản ghi này phân giải thành địa chỉ IPv4, ví dụ 104.26.10.229



**Kỷ lục AAAA**

Các bản ghi này phân giải thành địa chỉ IPv6, ví dụ 2606:4700:20::681a:be5



**Bản ghi CNAME**

Các bản ghi này sẽ phân giải thành một tên miền khác, ví dụ: cửa hàng trực tuyến của TryHackMe có tên miền phụ store.tryhackme.com , trả về bản ghi CNAME shops.shopify.com . Sau đó, một yêu cầu DNS khác sẽ được gửi đến shops.shopify.com để xác định địa chỉ IP.



**Bản ghi MX**

Các bản ghi này sẽ phân giải đến địa chỉ của các máy chủ xử lý email cho tên miền bạn đang truy vấn, ví dụ: phản hồi bản ghi MX cho tryhackme.com sẽ trông giống như  alt1.aspmx.l.google.com . Các bản ghi này cũng đi kèm với một cờ ưu tiên. Cờ này cho máy khách biết thứ tự thử các máy chủ, rất lý tưởng trong trường hợp máy chủ chính bị sập và email cần được gửi đến máy chủ dự phòng.



**Bản ghi TXT**

Bản ghi TXT là các trường văn bản tự do, nơi bất kỳ dữ liệu dạng văn bản nào cũng có thể được lưu trữ. Bản ghi TXT có nhiều công dụng, nhưng một số công dụng phổ biến có thể kể đến là liệt kê các máy chủ có thẩm quyền gửi email thay mặt cho tên miền (điều này có thể giúp chống lại thư rác và email giả mạo). Chúng cũng có thể được sử dụng để xác minh quyền sở hữu tên miền khi đăng ký dịch vụ của bên thứ ba.



#### **Đưa ra yêu cầu(Making A Request)**

**Điều gì xảy ra khi bạn thực hiện yêu cầu DNS**

1. Khi bạn yêu cầu tên miền, máy tính của bạn sẽ kiểm tra bộ nhớ đệm cục bộ để xem bạn đã tra cứu địa chỉ này gần đây chưa; nếu chưa, yêu cầu sẽ được gửi đến Máy chủ DNS đệ quy của bạn.
2. 
3. Máy chủ DNS Đệ quy thường được cung cấp bởi ISP của bạn, nhưng bạn cũng có thể tự chọn. Máy chủ này cũng có bộ nhớ đệm cục bộ chứa các tên miền đã tra cứu gần đây. Nếu kết quả được tìm thấy cục bộ, kết quả sẽ được gửi trở lại máy tính của bạn và yêu cầu của bạn sẽ kết thúc tại đây (điều này thường gặp ở các dịch vụ phổ biến và được yêu cầu nhiều như Google, Facebook, Twitter). Nếu yêu cầu không được tìm thấy cục bộ, hành trình tìm kiếm câu trả lời chính xác sẽ bắt đầu, bắt đầu từ các máy chủ DNS gốc của Internet .
4. 
5. Máy chủ gốc hoạt động như xương sống DNS của Internet; nhiệm vụ của chúng là chuyển hướng bạn đến Máy chủ Tên miền Cấp cao nhất (Top Level Domain Server) chính xác, tùy thuộc vào yêu cầu của bạn. Ví dụ: nếu bạn yêu cầu www.tryhackme.com , máy chủ gốc sẽ nhận dạng Tên miền Cấp cao nhất (Top Level Domain) là .com và chuyển hướng bạn đến máy chủ TLD chính xác xử lý địa chỉ .com.
6. 
7. Máy chủ TLD lưu trữ các bản ghi về vị trí tìm máy chủ có thẩm quyền để trả lời yêu cầu DNS . Máy chủ có thẩm quyền thường được gọi là máy chủ tên miền. Ví dụ: máy chủ tên miền cho tryhackme.com là kip.ns.cloudflare.com và uma.ns.cloudflare.com . Bạn thường sẽ tìm thấy nhiều máy chủ tên miền cho một tên miền để làm phương án dự phòng trong trường hợp một máy chủ bị sập.
8. 
9. Máy chủ DNS có thẩm quyền là máy chủ chịu trách nhiệm lưu trữ các bản ghi DNS cho một tên miền cụ thể và nơi thực hiện bất kỳ cập nhật nào cho các bản ghi DNS tên miền của bạn. Tùy thuộc vào loại bản ghi, bản ghi DNS sau đó được gửi trở lại Máy chủ DNS Đệ quy , tại đó một bản sao cục bộ sẽ được lưu vào bộ nhớ đệm cho các yêu cầu trong tương lai và sau đó được chuyển tiếp trở lại máy khách ban đầu đã thực hiện yêu cầu. Tất cả các bản ghi DNS đều đi kèm với giá trị TTL (Thời gian tồn tại). Giá trị này là một số được biểu thị bằng giây mà phản hồi sẽ được lưu cục bộ cho đến khi bạn phải tra cứu lại. Việc lưu vào bộ nhớ đệm giúp bạn không phải tạo yêu cầu DNS mỗi khi giao tiếp với máy chủ.



# **HTTP in Detail**

#### **What is HTTP(S)?**

**HTTP là gì ? (Giao thức truyền siêu văn bản - HyperText Transfer Protocol)**

HTTP là giao thức được sử dụng mỗi khi bạn xem một trang web, được phát triển bởi Tim Berners-Lee và nhóm của ông từ năm 1989 đến năm 1991. HTTP là tập hợp các quy tắc được sử dụng để giao tiếp với máy chủ web nhằm truyền dữ liệu trang web, có thể là HTML, Hình ảnh, Video, v.v.



**HTTPS là gì? (Giao thức truyền siêu văn bản bảo mật - HyperText Transfer Protocol Secure)**

HTTPS là phiên bản bảo mật của HTTP . Dữ liệu HTTPS được mã hóa nên không chỉ ngăn người khác nhìn thấy dữ liệu bạn nhận và gửi mà còn đảm bảo rằng bạn đang giao tiếp với đúng máy chủ web chứ không phải thứ gì đó mạo danh máy chủ đó.



#### **Yêu cầu và phản hồi(Requests And Responses)**

Khi chúng ta truy cập một trang web, trình duyệt của bạn sẽ cần gửi yêu cầu đến máy chủ web để lấy các tài nguyên như HTML, Hình ảnh và tải xuống phản hồi. Trước đó, bạn cần cho trình duyệt biết cụ thể cách thức và vị trí truy cập các tài nguyên này, và URL sẽ giúp ích trong trường hợp này.



**URL là gì? (Uniform Resource Locator)**

Nếu bạn đã từng sử dụng Internet, hẳn bạn đã từng sử dụng URL. URL chủ yếu là hướng dẫn về cách truy cập một tài nguyên trên Internet. Hình ảnh bên dưới cho thấy URL trông như thế nào với tất cả các tính năng của nó (nó không sử dụng tất cả các tính năng trong mọi yêu cầu).



Ví dụ yêu cầu:

**GET / HTTP/1.1**

**Host: tryhackme.com**

**User-Agent: Mozilla/5.0 Firefox/87.0**

**Referer: https://tryhackme.com/**



Để phân tích từng dòng của yêu cầu này:

Dòng 1: Yêu cầu này đang gửi phương thức GET (thông tin chi tiết hơn trong tác vụ Phương thức HTTP ), yêu cầu trang chủ bằng / và thông báo cho máy chủ web rằng chúng tôi đang sử dụng giao thức HTTP phiên bản 1.1.

Dòng 2: Chúng tôi nói với máy chủ web rằng chúng tôi muốn trang web tryhackme.com

Dòng 3: Chúng tôi thông báo cho máy chủ web rằng chúng tôi đang sử dụng Trình duyệt Firefox phiên bản 87

Dòng 4: Chúng tôi đang thông báo cho máy chủ web rằng trang web giới thiệu chúng tôi đến trang này là https://tryhackme.com

Dòng 5: Yêu cầu HTTP luôn kết thúc bằng một dòng trống để thông báo cho máy chủ web rằng yêu cầu đã hoàn tất.



Ví dụ phản hồi:

**HTTP/1.1 200 OK**

**Server: nginx/1.15.8**

**Date: Fri, 09 Apr 2021 13:34:03 GMT**

**Content-Type: text/html**

**Content-Length: 98**

**<html>**

**<head>**

&nbsp;   \*\*<title>TryHackMe</title>\*\*


**</head>**

**<body>**

&nbsp;   \*\*Welcome To TryHackMe.com\*\*


**</body>**

**</html>**



Để phân tích từng dòng của phản hồi:

Dòng 1: HTTP 1.1 là phiên bản giao thức HTTP mà máy chủ đang sử dụng và theo sau là Mã trạng thái HTTP trong trường hợp này là "200 OK" cho chúng ta biết yêu cầu đã hoàn tất thành công.

Dòng 2: Dòng này cho chúng ta biết phần mềm máy chủ web và số phiên bản.

Dòng 3: Ngày, giờ và múi giờ hiện tại của máy chủ web.

Dòng 4: Tiêu đề Content-Type cho máy khách biết loại thông tin nào sẽ được gửi, chẳng hạn như HTML, hình ảnh, video, pdf, XML .

Dòng 5: Content-Length cho máy khách biết độ dài của phản hồi, theo cách này chúng ta có thể xác nhận không có dữ liệu nào bị thiếu.

Dòng 6: Phản hồi HTTP chứa một dòng trống để xác nhận kết thúc phản hồi HTTP .

Dòng 7-14: Thông tin được yêu cầu, trong trường hợp này là trang chủ.

#### 

#### **Phương pháp HTTP(HTTP Methods)**

Phương thức HTTP là cách để máy khách thể hiện hành động dự định khi thực hiện một yêu cầu HTTP . Có rất nhiều phương thức HTTP , nhưng chúng tôi sẽ đề cập đến những phương thức phổ biến nhất, mặc dù chủ yếu bạn sẽ xử lý phương thức GET và POST.



* Yêu cầu GET

Được sử dụng để lấy thông tin từ máy chủ web.

* Yêu cầu POST

Điều này được sử dụng để gửi dữ liệu đến máy chủ web và có khả năng tạo các bản ghi mới

* Yêu cầu PUT

Điều này được sử dụng để gửi dữ liệu đến máy chủ web để cập nhật thông tin

* Yêu cầu XÓA

Được sử dụng để xóa thông tin/bản ghi khỏi máy chủ web.



#### **Mã trạng thái HTTP(HTTP Status Codes)**

###### **Mã trạng thái HTTP :**

Trong bài tập trước, bạn đã học rằng khi máy chủ HTTP phản hồi, dòng đầu tiên luôn chứa mã trạng thái thông báo cho máy khách về kết quả yêu cầu của họ và cũng có thể là cách xử lý yêu cầu đó. Các mã trạng thái này có thể được chia thành 5 phạm vi khác nhau:



100-199 - Phản hồi thông tin	Những mã này được gửi để thông báo cho khách hàng rằng phần đầu tiên của yêu cầu đã được chấp nhận và họ nên tiếp tục gửi phần còn lại của yêu cầu. Những mã này hiện không còn phổ biến nữa.

200-299 - Thành công	Dãy mã trạng thái này được sử dụng để thông báo cho khách hàng rằng yêu cầu của họ đã thành công.

300-399 - Chuyển hướng	Chúng được sử dụng để chuyển hướng yêu cầu của khách hàng đến một tài nguyên khác. Có thể là một trang web khác hoặc một trang web hoàn toàn khác.

400-499 - Lỗi của khách hàng	Được sử dụng để thông báo cho khách hàng rằng có lỗi trong yêu cầu của họ.

500-599 - Lỗi máy chủ	Điều này dành riêng cho các lỗi xảy ra ở phía máy chủ và thường chỉ ra một vấn đề khá lớn với máy chủ khi xử lý yêu cầu.



###### **Mã trạng thái HTTP phổ biến :**

Có rất nhiều mã trạng thái HTTP khác nhau và chưa kể đến việc các ứng dụng thậm chí có thể tự xác định mã trạng thái của riêng mình, chúng tôi sẽ xem xét các phản hồi HTTP phổ biến nhất mà bạn có thể gặp phải:



**200 - Được(200 - OK) :**	Yêu cầu đã được hoàn thành thành công.

**201 - Đã tạo(201 - Created) :**	Một tài nguyên đã được tạo (ví dụ: người dùng mới hoặc bài đăng blog mới).

**301 - Đã di chuyển vĩnh viễn(301 - Moved Permanently) :**	Thao tác này sẽ chuyển hướng trình duyệt của khách hàng đến một trang web mới hoặc thông báo cho các công cụ tìm kiếm rằng trang đã được di chuyển đến nơi khác và yêu cầu họ tìm kiếm ở đó.

**302 - Đã tìm thấy(302 - Found) :**	Tương tự như chuyển hướng vĩnh viễn ở trên, nhưng như tên gọi, đây chỉ là thay đổi tạm thời và có thể thay đổi lại trong tương lai gần.

**400 - Yêu cầu không hợp lệ(400 - Bad Request) :**	Điều này cho trình duyệt biết có điều gì đó sai hoặc thiếu sót trong yêu cầu của họ. Đôi khi, điều này có thể được sử dụng nếu tài nguyên máy chủ web đang được yêu cầu mong đợi một tham số nhất định mà máy khách không gửi.

**401 - Không được phép(401 - Not Authorised) :**	Hiện tại, bạn không được phép xem tài nguyên này cho đến khi bạn cấp quyền bằng ứng dụng web, thông thường là bằng tên người dùng và mật khẩu.

**403 - Cấm(403 - Forbidden) :**	Bạn không có quyền xem tài nguyên này cho dù bạn có đăng nhập hay không.

**405 - Phương pháp không được phép(405 - Method Not Allowed) :**	Tài nguyên không cho phép yêu cầu phương thức này, ví dụ, bạn gửi yêu cầu GET đến tài nguyên /create-account khi nó đang mong đợi yêu cầu POST.

**404 - Không tìm thấy trang(404 - Page Not Found) :**	Trang/tài nguyên bạn yêu cầu không tồn tại.

**500 - Lỗi dịch vụ nội bộ(500 - Internal Service Error) :**	Máy chủ đã gặp phải một số lỗi liên quan đến yêu cầu của bạn mà không biết cách xử lý đúng cách.

**503 - Dịch vụ không khả dụng(503 - Service Unavailable)**	: Máy chủ này không thể xử lý yêu cầu của bạn vì quá tải hoặc đang ngừng hoạt động để bảo trì.



###### **Tiêu đề(Headers)**

Tiêu đề là các bit dữ liệu bổ sung mà bạn có thể gửi đến máy chủ web khi thực hiện yêu cầu.



Mặc dù không bắt buộc phải có tiêu đề khi thực hiện yêu cầu HTTP , nhưng bạn sẽ thấy khó có thể xem trang web một cách chính xác.



**Tiêu đề yêu cầu chung**

﻿Đây là những tiêu đề được gửi từ máy khách (thường là trình duyệt của bạn) đến máy chủ.

* Máy chủ: Một số máy chủ web lưu trữ nhiều trang web, do đó bằng cách cung cấp tiêu đề máy chủ, bạn có thể cho máy chủ biết trang web nào bạn cần, nếu không, bạn sẽ chỉ nhận được trang web mặc định cho máy chủ.
* User-Agent: Đây là phần mềm trình duyệt và số phiên bản của bạn, cho máy chủ web biết rằng phần mềm trình duyệt của bạn giúp định dạng trang web phù hợp với trình duyệt của bạn và một số thành phần của HTML, JavaScript và CSS chỉ khả dụng trên một số trình duyệt nhất định.
* Độ dài nội dung(Content-Length): Khi gửi dữ liệu đến máy chủ web, chẳng hạn như trong biểu mẫu, độ dài nội dung sẽ cho máy chủ web biết lượng dữ liệu cần thiết trong yêu cầu web. Bằng cách này, máy chủ có thể đảm bảo không bỏ sót bất kỳ dữ liệu nào.
* Accept-Encoding: Cho máy chủ web biết trình duyệt hỗ trợ loại phương pháp nén nào để dữ liệu có thể được nén nhỏ hơn khi truyền qua Internet.
* Cookie: Dữ liệu được gửi đến máy chủ để giúp ghi nhớ thông tin của bạn (xem tác vụ cookie để biết thêm thông tin).

**Tiêu đề phản hồi chung**

Đây là các tiêu đề được máy chủ trả về cho máy khách sau khi có yêu cầu.

* Set-Cookie: Thông tin cần lưu trữ được gửi lại cho máy chủ web sau mỗi yêu cầu (xem tác vụ cookie để biết thêm thông tin).
* Cache-Control: Thời gian lưu trữ nội dung phản hồi trong bộ nhớ đệm của trình duyệt trước khi trình duyệt yêu cầu lại.
* Content-Type: Phần này cho máy khách biết loại dữ liệu nào đang được trả về, tức là HTML, CSS, JavaScript, Hình ảnh, PDF, Video, v.v. Khi sử dụng tiêu đề content-type, trình duyệt sẽ biết cách xử lý dữ liệu.
* Mã hóa nội dung - Content-Encoding: Phương pháp nào được sử dụng để nén dữ liệu nhằm làm cho dữ liệu nhỏ hơn khi gửi qua Internet.



#### **Cookies**

Có lẽ bạn đã từng nghe về cookie, chúng chỉ là một phần dữ liệu nhỏ được lưu trữ trên máy tính của bạn. Cookie được lưu khi bạn nhận được tiêu đề "Set-Cookie" từ máy chủ web. Sau đó, mỗi yêu cầu tiếp theo bạn thực hiện, bạn sẽ gửi dữ liệu cookie trở lại máy chủ web. Vì HTTP không có trạng thái (không lưu trữ các yêu cầu trước đó của bạn), cookie có thể được sử dụng để nhắc máy chủ web về danh tính của bạn, một số cài đặt cá nhân cho trang web hoặc liệu bạn đã từng truy cập trang web trước đó hay chưa.



Cookie có thể được sử dụng cho nhiều mục đích, nhưng phổ biến nhất là để xác thực trang web. Giá trị cookie thường không phải là một chuỗi ký tự rõ ràng, nơi bạn có thể thấy mật khẩu, mà là một mã thông báo (mã bí mật duy nhất mà con người không dễ dàng đoán được).



# **How Websites Work**

#### **How websites work**

Khi bạn truy cập một trang web, trình duyệt của bạn ( như Safari hoặc Google Chrome ) sẽ gửi yêu cầu đến máy chủ web để xin thông tin về trang bạn đang truy cập. Máy chủ sẽ phản hồi dữ liệu mà trình duyệt sử dụng để hiển thị trang web cho bạn; máy chủ web chỉ là một máy tính chuyên dụng ở một nơi nào đó trên thế giới xử lý các yêu cầu của bạn.

Có hai thành phần chính tạo nên một trang web:

1. Giao diện người dùng (Phía máy khách) - cách trình duyệt của bạn hiển thị trang web.
2. Back End (Phía máy chủ) - máy chủ xử lý yêu cầu của bạn và trả về phản hồi.



#### **JavaScript**

JavaScript (JS) là một trong những ngôn ngữ lập trình phổ biến nhất thế giới và cho phép các trang web trở nên tương tác. HTML được sử dụng để tạo cấu trúc và nội dung trang web, trong khi JavaScript được sử dụng để kiểm soát chức năng của trang web - nếu không có JavaScript, một trang web sẽ không có các thành phần tương tác và sẽ luôn ở trạng thái tĩnh. JS có thể cập nhật trang web theo thời gian thực, cung cấp chức năng thay đổi kiểu nút khi một sự kiện cụ thể trên trang xảy ra (chẳng hạn như khi người dùng nhấp vào nút) hoặc hiển thị các hiệu ứng động.



JavaScript được thêm vào trong mã nguồn của trang và có thể được tải trong thẻ hoặc có thể được đưa vào từ xa bằng thuộc tính **src:<script><script src="/location/of/javascript\\\_file.js"></script>**



Mã JavaScript sau đây tìm thấy một phần tử HTML trên trang có id là "demo" và thay đổi nội dung của phần tử thành "Hack the Planet": **document.getElementById("demo").innerHTML = "Hack the Planet";**



Các phần tử HTML cũng có thể có các sự kiện, chẳng hạn như "onclick" hoặc "onhover", để thực thi JavaScript khi sự kiện xảy ra. Đoạn mã sau sẽ thay đổi văn bản của phần tử có ID demo thành Button Clicked:  - Sự kiện onclick cũng có thể được định nghĩa bên trong thẻ script JavaScript, chứ không phải trực tiếp trên các phần tử. **<button onclick='document.getElementById("demo").innerHTML = "Button Clicked";'>Click Me!</button>**



#### **Các thành phần khác**

**Bộ cân bằng tải(Load Balancers)**

Khi lưu lượng truy cập của một trang web bắt đầu tăng lên đáng kể hoặc đang chạy một ứng dụng cần tính khả dụng cao, một máy chủ web có thể không còn đáp ứng được nhiệm vụ. Bộ cân bằng tải cung cấp hai tính năng chính: đảm bảo các trang web có lưu lượng truy cập cao có thể xử lý tải và cung cấp khả năng chuyển đổi dự phòng nếu một máy chủ không phản hồi.

Khi bạn yêu cầu một trang web bằng bộ cân bằng tải, bộ cân bằng tải sẽ nhận yêu cầu của bạn trước rồi chuyển tiếp đến một trong nhiều máy chủ phía sau. Bộ cân bằng tải sử dụng các thuật toán khác nhau để giúp quyết định máy chủ nào phù hợp nhất để xử lý yêu cầu. Một vài ví dụ về các thuật toán này là  round-robin (phân luồng vòng tròn) , theo đó yêu cầu được gửi đến từng máy chủ một cách tuần tự, hoặc  weighted (phân luồng có trọng số) , theo đó máy chủ hiện đang xử lý bao nhiêu yêu cầu và gửi đến máy chủ ít bận nhất.



Bộ cân bằng tải cũng thực hiện kiểm tra định kỳ với từng máy chủ để đảm bảo chúng hoạt động chính xác; đây được gọi là  kiểm tra tình trạng . Nếu máy chủ không phản hồi đúng hoặc không phản hồi, bộ cân bằng tải sẽ ngừng gửi lưu lượng cho đến khi phản hồi đúng trở lại.



**CDN (Mạng phân phối nội dung - Content Delivery Networks)**

CDN có thể là một giải pháp tuyệt vời để giảm lưu lượng truy cập đến một trang web bận rộn. Nó cho phép bạn lưu trữ các tệp tĩnh từ trang web của mình, chẳng hạn như JavaScript, CSS, Hình ảnh, Video, và lưu trữ chúng trên hàng ngàn máy chủ trên khắp thế giới. Khi người dùng yêu cầu một trong những tệp được lưu trữ, CDN sẽ xác định vị trí máy chủ gần nhất và gửi yêu cầu đến đó thay vì có khả năng là ở phía bên kia thế giới.



**Cơ sở dữ liệu(Databases)**

Thông thường, các trang web sẽ cần một phương thức lưu trữ thông tin cho người dùng. Máy chủ web có thể giao tiếp với cơ sở dữ liệu để lưu trữ và truy xuất dữ liệu từ đó. Cơ sở dữ liệu có thể đa dạng từ một tệp văn bản thuần túy đơn giản đến các cụm máy chủ phức tạp, cung cấp tốc độ và khả năng phục hồi cao. Bạn sẽ bắt gặp một số cơ sở dữ liệu phổ biến: MySQL, MSSQL, MongoDB, Postgres, v.v.; mỗi loại có những tính năng riêng.



**WAF (Tường lửa ứng dụng web - Web Application Firewall)**

WAF nằm giữa yêu cầu web của bạn và máy chủ web; mục đích chính của nó là bảo vệ máy chủ web khỏi các cuộc tấn công từ chối dịch vụ hoặc hack. Nó phân tích các yêu cầu web để tìm ra các kỹ thuật tấn công phổ biến, xem yêu cầu đó đến từ trình duyệt thực hay bot. Nó cũng kiểm tra xem có quá nhiều yêu cầu web được gửi đi hay không bằng cách sử dụng một thứ gọi là giới hạn tốc độ, chỉ cho phép một lượng yêu cầu nhất định từ một IP mỗi giây. Nếu một yêu cầu được coi là có khả năng bị tấn công, nó sẽ bị loại bỏ và không bao giờ được gửi đến máy chủ web.



**Máy chủ web hoạt động như thế nào.**

* Máy chủ web là gì?

Máy chủ web là phần mềm lắng nghe các kết nối đến và sau đó sử dụng giao thức HTTP để phân phối nội dung web đến máy khách. Các phần mềm máy chủ web phổ biến nhất mà bạn sẽ gặp là Apache , Nginx, IIS và NodeJS. Máy chủ web phân phối tệp từ thư mục gốc của nó, được định nghĩa trong cài đặt phần mềm. Ví dụ: Nginx và Apache chia sẻ cùng một vị trí mặc định là /var/www/html trong hệ điều hành Linux , và IIS sử dụng C:\\inetpub\\wwwroot cho hệ điều hành Windows. Vì vậy, ví dụ: nếu bạn yêu cầu tệp  http://www.example.com/picture.jpg , nó sẽ gửi tệp /var/www/html/picture.jpg từ ổ cứng cục bộ của nó.



* Máy chủ ảo

Máy chủ web có thể lưu trữ nhiều trang web với các tên miền khác nhau; để đạt được điều này, chúng sử dụng máy chủ ảo. Phần mềm máy chủ web sẽ kiểm tra tên máy chủ được yêu cầu từ tiêu đề HTTP và so khớp với máy chủ ảo (máy chủ ảo chỉ là các tệp cấu hình dạng văn bản). Nếu tìm thấy kết quả khớp, trang web chính xác sẽ được cung cấp. Nếu không tìm thấy, trang web mặc định sẽ được cung cấp.



Máy chủ ảo có thể ánh xạ thư mục gốc của chúng đến các vị trí khác nhau trên ổ cứng. Ví dụ: one.com được ánh xạ đến /var/www/website\_one, và two.com được ánh xạ đến /var/www/website\_two.



Không có giới hạn về số lượng trang web khác nhau mà bạn có thể lưu trữ trên một máy chủ web.



* Nội dung tĩnh so với nội dung động



Nội dung tĩnh, đúng như tên gọi, là nội dung không bao giờ thay đổi. Ví dụ phổ biến là hình ảnh, javascript, CSS, v.v., nhưng cũng có thể bao gồm HTML không bao giờ thay đổi. Hơn nữa, đây là những tệp được cung cấp trực tiếp từ máy chủ web mà không có bất kỳ thay đổi nào.



Mặt khác, nội dung động là nội dung có thể thay đổi theo các yêu cầu khác nhau. Lấy ví dụ, một blog. Trên trang chủ của blog, bạn sẽ thấy các bài viết mới nhất. Nếu một bài viết mới được tạo, trang chủ sẽ được cập nhật với bài viết mới nhất, hoặc một ví dụ khác có thể là trang tìm kiếm trên blog. Tùy thuộc vào từ khóa bạn tìm kiếm, các kết quả khác nhau sẽ được hiển thị.



Những thay đổi này đối với những gì bạn thấy được thực hiện ở phần  Backend  , sử dụng ngôn ngữ lập trình và kịch bản. Nó được gọi là Backend vì mọi thứ được thực hiện đều diễn ra ở chế độ nền. Bạn không thể xem mã nguồn HTML của trang web và xem những gì đang diễn ra ở Backend, trong khi HTML là kết quả của quá trình xử lý từ Backend. Mọi thứ bạn thấy trên trình duyệt được gọi là  Frontend.



* Ngôn ngữ kịch bản và ngôn ngữ phụ trợ



Không có nhiều giới hạn cho những gì một ngôn ngữ back-end có thể đạt được, và chính những điều này làm cho một trang web trở nên tương tác với người dùng. Một số ví dụ về các ngôn ngữ này (không theo thứ tự cụ thể :p) là PHP , Python, Ruby, NodeJS, Perl và nhiều ngôn ngữ khác nữa. Các ngôn ngữ này có thể tương tác với cơ sở dữ liệu, gọi các dịch vụ bên ngoài, xử lý dữ liệu từ người dùng, và còn nhiều hơn thế nữa. Một ví dụ PHP rất cơ bản về điều này sẽ là nếu bạn yêu cầu trang web  http://example.com/index.php ? name=adam



Nếu index.php được xây dựng như thế này:



**<html><body>Hello <?php echo $\\\_GET\\\["name"]; ?></body></html>**



Nó sẽ xuất ra thông tin sau cho máy khách:



**<html><body>Hello adam</body></html>**



Bạn sẽ nhận thấy rằng máy khách không thấy bất kỳ mã PHP nào vì nó nằm ở  Backend . Tính tương tác này làm nảy sinh nhiều vấn đề bảo mật hơn cho các ứng dụng web chưa được xây dựng an toàn, như bạn sẽ tìm hiểu trong các mô-đun tiếp theo.

