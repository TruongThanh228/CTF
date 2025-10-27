# Tổng quan về ứng dụng web(Web Application Overview)

Hãy xem xét một ví dụ tương tự về ứng dụng web như một hành tinh. Các phi hành gia du hành đến hành tinh để khám phá bề mặt của nó, tương tự như cách ai đó sử dụng trình duyệt web để khám phá hoặc duyệt một ứng dụng web. Mặc dù chúng ta chỉ nhìn thấy bề mặt của một hành tinh, nhưng có rất nhiều thứ đang diễn ra bên dưới bề mặt đó. Bạn có thể tưởng tượng toàn bộ hành tinh như một máy chủ web với rất nhiều thứ đang diễn ra bên dưới bề mặt của máy chủ web, nhưng tất cả những gì chúng ta thường thấy chỉ là bề mặt của các trang web hoặc ứng dụng. Bây giờ chúng ta sẽ khám phá các thành phần khác nhau tạo nên một ứng dụng web.



#### **Phần đầu(Front End)**

Front End  có thể được coi tương tự như bề mặt hành tinh, những phần mà phi hành gia có thể nhìn thấy và tương tác dựa trên các quy luật tự nhiên. Một ứng dụng web sẽ cho phép người dùng tương tác với nó và sử dụng một số công nghệ như HTML, CSS và JavaScript để thực hiện việc này.



HTML (Ngôn ngữ Đánh dấu Siêu văn bản) là một khía cạnh nền tảng của các ứng dụng web. Nó là một tập hợp các hướng dẫn hoặc mã lệnh hướng dẫn trình duyệt web hiển thị nội dung gì và cách hiển thị. Nó có thể được so sánh với các sinh vật đơn giản sống trên hành tinh; những sinh vật này có DNA, là những hướng dẫn về cách các sinh vật đơn giản được kết hợp với nhau.



CSS  (Cascading Style Sheets) trong các ứng dụng web mô tả giao diện chuẩn, chẳng hạn như màu sắc, kiểu văn bản và bố cục nhất định. Tiếp tục so sánh với DNA, chúng có thể được so sánh với các phần DNA mô tả màu sắc, hình dạng, kích thước và kết cấu của một sinh vật đơn giản.



JS  (JavaScript) là một phần của giao diện ứng dụng web, cho phép thực hiện các hoạt động phức tạp hơn trên trình duyệt web. Trong khi HTML có thể được coi là một tập hợp các hướng dẫn đơn giản về nội dung hiển thị, JavaScript là một tập hợp các hướng dẫn nâng cao hơn, cho phép lựa chọn và quyết định nội dung hiển thị. Trong phép so sánh với hành tinh, JavaScript có thể được coi là bộ não của một sinh vật tiên tiến, cho phép đưa ra quyết định dựa trên nội dung và cách thức tương tác của một vật với nó.



#### **Phần cuối(Back End)**

Phần cuối của một ứng dụng web là những thứ bạn không nhìn thấy trong trình duyệt web nhưng lại rất quan trọng để ứng dụng web hoạt động. Trên một hành tinh, đây là những thứ phi thị giác: các cấu trúc giúp tòa nhà đứng vững, không khí và trọng lực giúp bàn chân đứng vững trên mặt đất.



Cơ sở dữ liệu là nơi thông tin có thể được lưu trữ, chỉnh sửa và truy xuất. Một ứng dụng web có thể muốn lưu trữ và truy xuất thông tin về sở thích của người dùng về việc hiển thị hay không hiển thị; thông tin này sẽ được lưu trữ trong cơ sở dữ liệu. Một hành tinh có thể có những cư dân tiên tiến hơn, lưu trữ thông tin về vị trí trên bản đồ, ghi chú vào nhật ký hoặc cất sách vào thư viện và hồ sơ vào tủ hồ sơ.



Có rất nhiều thành phần cơ sở hạ tầng khác hỗ trợ Ứng dụng Web, chẳng hạn như máy chủ web, máy chủ ứng dụng, lưu trữ, nhiều thiết bị mạng và phần mềm khác hỗ trợ ứng dụng web. Trên một hành tinh, đó là những con đường hiện hữu, những chiếc xe chạy trên những con đường đó, và nhiên liệu cung cấp năng lượng cho xe.



WAF  ( Tường lửa Ứng dụng Web ) là một thành phần tùy chọn cho các ứng dụng web. Nó giúp lọc các yêu cầu nguy hiểm khỏi Máy chủ Web và cung cấp một yếu tố bảo vệ. Điều này có thể được coi tương tự như cách bầu khí quyển của một hành tinh bảo vệ cư dân khỏi tia UV có hại.



# Bộ định vị tài nguyên thống nhất(Uniform Resource Locator)

#### Bộ định vị tài nguyên thống nhất

Định vị Tài nguyên Thống nhất (URL) là một địa chỉ web cho phép bạn truy cập mọi loại nội dung trực tuyến—cho dù đó là trang web, video, ảnh hay phương tiện truyền thông khác. URL hướng dẫn trình duyệt của bạn đến đúng nơi trên Internet.



#### Giải phẫu của một URL

                                http://user:password@tryhackme.com:80/view-room?id=1#task3

                               scheme|  user   |     host/domain | port | path | query string | fragment



Hãy hình dung một URL được tạo thành từ nhiều phần, mỗi phần đóng một vai trò khác nhau trong việc giúp bạn tìm đúng tài nguyên. Việc hiểu cách các phần này kết hợp với nhau rất quan trọng khi duyệt web, phát triển ứng dụng web và thậm chí là khắc phục sự cố.



Sau đây là bảng phân tích các thành phần chính:



Cơ chế(scheme)

Giao thức này là giao thức được sử dụng để truy cập trang web. Phổ biến nhất là HTTP (Giao thức Truyền Siêu văn bản) và HTTPS (Giao thức Truyền Siêu văn bản Bảo mật). HTTPS an toàn hơn vì nó mã hóa kết nối, đó là lý do tại sao các trình duyệt và chuyên gia an ninh mạng khuyên dùng. Các trang web thường áp dụng HTTPS để tăng cường bảo mật.



Người dùng(user)

Một số URL có thể bao gồm thông tin đăng nhập của người dùng (thường là tên người dùng) cho các trang web yêu cầu xác thực. Điều này chủ yếu xảy ra ở các URL yêu cầu thông tin xác thực để truy cập một số tài nguyên nhất định. Tuy nhiên, hiện nay tình trạng này rất hiếm gặp vì việc đưa thông tin đăng nhập vào URL không thực sự an toàn—nó có thể làm lộ thông tin nhạy cảm, gây ra rủi ro bảo mật.



Máy chủ/Tên miền(host/domain)

Máy chủ hoặc tên miền là phần quan trọng nhất của URL vì nó cho bạn biết bạn đang truy cập trang web nào. Mỗi tên miền phải là duy nhất và được đăng ký thông qua các nhà đăng ký tên miền. Về mặt bảo mật, hãy tìm những tên miền trông gần giống tên miền thật nhưng có một số khác biệt nhỏ (đây được gọi là đánh cắp tên miền ). Những tên miền giả mạo này thường được sử dụng trong các cuộc tấn công lừa đảo để lừa người dùng cung cấp thông tin nhạy cảm.



Cảng(port)

Số cổng giúp định hướng trình duyệt của bạn đến đúng dịch vụ trên máy chủ web. Nó giống như việc cho máy chủ biết nên sử dụng cổng nào để giao tiếp. Số cổng nằm trong khoảng từ 1 đến 65.535, nhưng phổ biến nhất là 80 cho HTTP và 443 cho HTTPS.



Con đường(path)

Đường dẫn này trỏ đến tệp hoặc trang cụ thể trên máy chủ mà bạn đang cố gắng truy cập. Nó giống như một lộ trình chỉ đường cho trình duyệt biết cần đi đến đâu. Các trang web cần bảo mật những đường dẫn này để đảm bảo chỉ những người dùng được ủy quyền mới có thể truy cập các tài nguyên nhạy cảm.



Chuỗi truy vấn(query string)

Chuỗi truy vấn là phần URL bắt đầu bằng dấu chấm hỏi (?). Nó thường được sử dụng cho các mục đích như tìm kiếm hoặc nhập dữ liệu biểu mẫu. Vì người dùng có thể sửa đổi các chuỗi truy vấn này, điều quan trọng là phải xử lý chúng một cách an toàn để ngăn chặn các cuộc tấn công như chèn mã độc , có thể dẫn đến việc chèn mã độc.



Mảnh vỡ(fragment)

Đoạn mã bắt đầu bằng ký hiệu thăng (#) và giúp trỏ đến một phần cụ thể của trang web—giống như việc nhảy trực tiếp đến một tiêu đề hoặc bảng cụ thể. Người dùng cũng có thể sửa đổi đoạn mã này, vì vậy, giống như với chuỗi truy vấn, điều quan trọng là phải kiểm tra và dọn dẹp mọi dữ liệu ở đây để tránh các sự cố như tấn công chèn mã độc.



# Tin nhắn HTTP(HTTP Messages)

Thông điệp HTTP là các gói dữ liệu được trao đổi giữa người dùng (máy khách) và máy chủ web. Những thông điệp này rất quan trọng để hiểu cách thức hoạt động của các ứng dụng web vì chúng cho thấy cách thức các yêu cầu của người dùng và phản hồi của máy chủ được truyền đạt.



Hãy tưởng tượng một ví dụ về Yêu cầu HTTP và Phản hồi HTTP , trong đó bạn có thể thấy các thành phần chính như phương thức, URL, tiêu đề và mã trạng thái. Đây là những yếu tố tạo nên khả năng tương tác giữa máy khách và máy chủ.



Có hai loại tin nhắn HTTP :

* Yêu cầu HTTP(HTTP Request) : Được người dùng gửi để kích hoạt các hành động trên ứng dụng web.
* Phản hồi HTTP(HTTP Responses) : Được máy chủ gửi để phản hồi yêu cầu của người dùng.



Mỗi tin nhắn đều theo một định dạng cụ thể giúp cả người dùng và máy chủ giao tiếp dễ dàng.



Dòng bắt đầu(Start Line)

Dòng bắt đầu giống như phần giới thiệu của tin nhắn. Nó cho bạn biết loại tin nhắn nào đang được gửi đi—đó là yêu cầu từ người dùng hay phản hồi từ máy chủ. Dòng này cũng cung cấp các chi tiết quan trọng về cách xử lý tin nhắn.



Tiêu đề(Headers)

Tiêu đề được tạo thành từ các cặp khóa-giá trị cung cấp thông tin bổ sung về thông điệp HTTP . Chúng cung cấp hướng dẫn cho cả máy khách và máy chủ xử lý yêu cầu hoặc phản hồi. Các tiêu đề này bao gồm nhiều vấn đề, chẳng hạn như bảo mật, loại nội dung, v.v., đảm bảo mọi thứ diễn ra suôn sẻ trong quá trình giao tiếp.



Dòng trống(Empty Line)

Dòng trống là một dải phân cách nhỏ ngăn cách phần tiêu đề với phần nội dung. Điều này rất quan trọng vì nó cho thấy điểm kết thúc của phần tiêu đề và điểm bắt đầu của nội dung thực tế của thông điệp. Nếu không có dòng trống này, thông điệp có thể bị sai lệch, và máy khách hoặc máy chủ có thể hiểu sai, gây ra lỗi.



Thân hình(Body)

Phần thân là nơi lưu trữ dữ liệu thực tế. Trong một yêu cầu, phần thân có thể bao gồm dữ liệu người dùng muốn gửi đến máy chủ (như dữ liệu biểu mẫu). Trong một phản hồi, đây là nơi máy chủ đặt nội dung mà người dùng yêu cầu (như trang web hoặc dữ liệu API ).



Tại sao việc hiểu các thông điệp HTTP lại quan trọng

* Những thông điệp này là nền tảng cho cách các ứng dụng web giao tiếp. Nếu được cấu trúc đúng, mọi thứ sẽ hoạt động trơn tru.
* Biết cách chúng hoạt động sẽ giúp bạn chẩn đoán các sự cố trong giao tiếp web, nghĩa là cải thiện hiệu suất và độ tin cậy cho ứng dụng web của bạn.
* Điều này cũng rất quan trọng đối với bảo mật. Hiểu rõ các thông điệp HTTP giúp bạn triển khai các biện pháp bảo mật mạnh mẽ để bảo vệ dữ liệu trong quá trình truyền tải.



# Yêu cầu HTTP: Dòng yêu cầu và phương thức

Yêu cầu HTTP là những gì người dùng gửi đến máy chủ web để tương tác với ứng dụng web và thực hiện một thao tác nào đó. Vì những yêu cầu này thường là điểm tiếp xúc đầu tiên giữa người dùng và máy chủ web, nên việc hiểu rõ cách thức hoạt động của chúng là vô cùng quan trọng, đặc biệt nếu bạn đang tìm hiểu về an ninh mạng.



Hãy tưởng tượng một yêu cầu HTTP hiển thị các thành phần chính như phương thức (ví dụ: GET hoặc POST), đường dẫn (ví dụ: /login) và phiên bản (ví dụ: HTTP /1.1). Những thành phần này tạo nên nền tảng cơ bản về cách máy khách (người dùng) giao tiếp với máy chủ.



##                   **GET /user/login.html HTTP/1.1**

                                     \*\*HTTP Methods   |              Path                 |  HTTP Version\*\*











#### Dòng yêu cầu(Request Line)

Dòng yêu cầu (hay dòng bắt đầu) là phần đầu tiên của một yêu cầu HTTP và cho máy chủ biết loại yêu cầu nào đang được xử lý. Nó bao gồm ba phần chính: phương thức HTTP , đường dẫn URL và phiên bản HTTP .

Ví dụ: METHOD /path HTTP/version



#### Phương pháp HTTP(HTTP Methods)

Phương thức HTTP cho máy chủ biết hành động nào người dùng muốn thực hiện trên tài nguyên được xác định bởi đường dẫn URL. Dưới đây là một số phương thức phổ biến nhất và các vấn đề bảo mật có thể xảy ra của chúng:



**GET**

Dùng để lấy dữ liệu từ máy chủ mà không thực hiện bất kỳ thay đổi nào. Lưu ý! Đảm bảo bạn chỉ hiển thị dữ liệu mà người dùng được phép xem. Tránh đưa thông tin nhạy cảm như mã thông báo hoặc mật khẩu vào yêu cầu GET vì chúng có thể hiển thị dưới dạng văn bản thuần túy.



**POST**

Gửi dữ liệu đến máy chủ, thường là để tạo hoặc cập nhật dữ liệu. Lưu ý! Luôn xác thực và làm sạch dữ liệu đầu vào để tránh các cuộc tấn công như SQL injection hoặc XSS .



**PUT**

Thay thế hoặc cập nhật nội dung nào đó trên máy chủ. Lưu ý! Hãy đảm bảo người dùng được phép thực hiện thay đổi trước khi chấp nhận yêu cầu.



**DELETE**

Xóa một mục nào đó khỏi máy chủ. Lưu ý! Giống như PUT, hãy đảm bảo chỉ những người dùng được ủy quyền mới có thể xóa tài nguyên.



Bên cạnh những phương pháp phổ biến này, còn có một số phương pháp khác được sử dụng trong những trường hợp cụ thể:



**PATCH**

Cập nhật một phần tài nguyên. Lệnh này hữu ích khi thực hiện những thay đổi nhỏ mà không cần thay thế toàn bộ, nhưng luôn xác thực dữ liệu để tránh sự không nhất quán.



**HEAD**

hoạt động giống GET nhưng chỉ lấy tiêu đề, không lấy toàn bộ nội dung. Nó rất tiện lợi để kiểm tra siêu dữ liệu mà không cần tải xuống toàn bộ phản hồi.



**TÙY CHỌN(Opitions)**

Cho bạn biết những phương pháp nào có sẵn cho một tài nguyên cụ thể, giúp khách hàng hiểu những gì họ có thể làm với máy chủ.



**TRACE**

Tương tự như OPTIONS, nó hiển thị những phương thức nào được phép, thường dùng để gỡ lỗi. Nhiều máy chủ vô hiệu hóa nó vì lý do bảo mật.



**CONNECT**

Được sử dụng để tạo kết nối an toàn, chẳng hạn như HTTPS. Giao thức này không phổ biến nhưng rất quan trọng đối với giao tiếp được mã hóa.



Mỗi phương pháp này đều có bộ quy tắc bảo mật riêng. Ví dụ: yêu cầu PATCH cần được xác thực để tránh sự không nhất quán, và OPTIONS và TRACE nên được tắt nếu không cần thiết để tránh các rủi ro bảo mật có thể xảy ra.



#### Đường dẫn URL(URL Path)

Đường dẫn URL cho máy chủ biết nơi tìm tài nguyên mà người dùng đang yêu cầu. Ví dụ: trong URL https://tryhackme.com/api/users/123, đường dẫn /api/users/123 xác định một người dùng cụ thể.



Kẻ tấn công thường cố gắng thao túng đường dẫn URL để khai thác lỗ hổng, vì vậy điều quan trọng là phải:

* Xác thực đường dẫn URL để ngăn chặn truy cập trái phép
* Vệ sinh đường dẫn để tránh các cuộc tấn công tiêm nhiễm
* Bảo vệ dữ liệu nhạy cảm bằng cách tiến hành đánh giá quyền riêng tư và rủi ro

Thực hiện các biện pháp này sẽ giúp bảo vệ ứng dụng web của bạn khỏi các cuộc tấn công phổ biến.



#### Phiên bản HTTP(HTTP Version)

Phiên bản HTTP hiển thị phiên bản giao thức   được sử dụng để giao tiếp giữa máy khách và máy chủ. Dưới đây là tóm tắt nhanh về những giao thức phổ biến nhất:



HTTP /0.9 (1991)

Phiên bản đầu tiên chỉ hỗ trợ các yêu cầu GET.



HTTP /1.0 (1996)

Thêm tiêu đề và hỗ trợ tốt hơn cho các loại nội dung khác nhau, cải thiện bộ nhớ đệm.



HTTP /1.1 (1997)

mang lại kết nối liên tục, mã hóa truyền dữ liệu theo khối và bộ nhớ đệm tốt hơn. Nó vẫn được sử dụng rộng rãi cho đến ngày nay.



HTTP /2 (2015)

Giới thiệu các tính năng như ghép kênh, nén tiêu đề và ưu tiên để có hiệu suất nhanh hơn.



HTTP /3 (2022)

Được xây dựng trên HTTP /2, nhưng sử dụng giao thức mới (QUIC) để kết nối nhanh hơn và an toàn hơn.



Mặc dù HTTP /2 và HTTP /3 mang lại tốc độ và bảo mật tốt hơn, nhiều hệ thống vẫn sử dụng HTTP /1.1 vì nó được hỗ trợ tốt và tương thích với hầu hết các thiết lập hiện có. Tuy nhiên, việc nâng cấp lên HTTP /2 hoặc HTTP /3 có thể mang lại những cải tiến đáng kể về hiệu suất và bảo mật khi ngày càng nhiều hệ thống áp dụng chúng.



# Yêu cầu HTTP: Tiêu đề và Nội dung(HTTP Request : Headers and Body)

#### Tiêu đề yêu cầu(Request Headers)

Tiêu đề yêu cầu cho phép truyền tải thêm thông tin về yêu cầu đến máy chủ web. Một số tiêu đề phổ biến như sau:



#### Tiêu đề yêu cầu chung



Tiêu đề yêu cầu	                   Ví dụ	                                                                             Sự miêu tả

Chủ nhà	                   Host: tryhackme.com                                                              Chỉ định tên máy chủ web mà yêu cầu được gửi tới.

Tác nhân người dùng	   User-Agent: Mozilla/5.0                                                          Chia sẻ thông tin về trình duyệt web mà yêu cầu đến từ đó.

Người giới thiệu	   Referer: https://www.google.com/                                                 Chỉ ra URL mà yêu cầu đến từ đó.

Bánh quy	Cookie: user\_type=student; room=introtowebapplication; room\_status=in\_progress              Thông tin mà máy chủ web trước đó đã yêu cầu trình duyệt web lưu trữ sẽ được lưu        trong cookie.

Loại nội dung	Content-Type: application/json                                                              Mô tả loại hoặc định dạng dữ liệu có trong yêu cầu.





#### Yêu cầu cơ thể(Request Body)

Trong các yêu cầu HTTP như POST và PUT, dữ liệu được gửi đến máy chủ web thay vì được yêu cầu từ máy chủ web, dữ liệu được đặt bên trong Thân Yêu cầu HTTP . Định dạng dữ liệu có thể có nhiều dạng, nhưng một số dạng phổ biến là  URL Encoded, Form Data, JSON, hoặc XML.



* URL được mã hóa (application/x-www-form-urlencoded)

Định dạng mà dữ liệu được cấu trúc theo cặp khóa và giá trị, trong đó ( key=value). Nhiều cặp được phân tách bằng \&ký hiệu (), chẳng hạn như  key1=value1\&key2=value2. Các ký tự đặc biệt được mã hóa theo phần trăm.



Ví dụ

POST /profile HTTP/1.1

Host: tryhackme.com

User-Agent: Mozilla/5.0

Content-Type: application/x-www-form-urlencoded

Content-Length: 33

name=Aleksandra\&age=27\&country=US



* Dữ liệu Biểu mẫu (multipart/form-data)

Cho phép gửi nhiều khối dữ liệu, mỗi khối được phân tách bằng một chuỗi ranh giới. Chuỗi ranh giới này là tiêu đề được xác định của chính yêu cầu. Kiểu định dạng này có thể được sử dụng để gửi dữ liệu nhị phân, chẳng hạn như khi tải tệp hoặc hình ảnh lên máy chủ web.



Ví dụ

POST /upload HTTP/1.1

Host: tryhackme.com

User-Agent: Mozilla/5.0

Content-Type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW



----WebKitFormBoundary7MA4YWxkTrZu0gW

Content-Disposition: form-data; name="username"



aleksandra

----WebKitFormBoundary7MA4YWxkTrZu0gW

Content-Disposition: form-data; name="profile\_pic"; filename="aleksandra.jpg"

Content-Type: image/jpeg



\[Binary Data Here representing the image]

----WebKitFormBoundary7MA4YWxkTrZu0gW--



* JSON (application/ json )

Ở định dạng này, dữ liệu có thể được gửi bằng cấu trúc JSON (JavaScript Object Notation). Dữ liệu được định dạng theo cặp name : value. Nhiều cặp được phân tách bằng dấu phẩy, tất cả đều nằm trong dấu ngoặc nhọn { }.



Ví dụ

POST /api/user HTTP/1.1

Host: tryhackme.com

User-Agent: Mozilla/5.0

Content-Type: application/json

Content-Length: 62



{

    "name": "Aleksandra",

    "age": 27,

    "country": "US"

}



* XML (application/ xml )

Trong  định dạng XML  , dữ liệu được cấu trúc bên trong các nhãn gọi là thẻ, có phần mở đầu và phần đóng. Các nhãn này có thể được lồng vào nhau. Bạn có thể thấy trong ví dụ bên dưới phần mở đầu và đóng của các thẻ để gửi thông tin chi tiết về người dùng tên là Aleksandra.



Ví dụ

POST /api/user HTTP/1.1

Host: tryhackme.com

User-Agent: Mozilla/5.0

Content-Type: application/xml

Content-Length: 124



<user>

    <name>Aleksandra</name>

    <age>27</age>

    <country>US</country>

</user>



# Phản hồi HTTP: Dòng trạng thái và Mã trạng thái(HTTP Response: Status Line and Status Codes)

Khi bạn tương tác với một ứng dụng web, máy chủ sẽ gửi lại phản hồi HTTP để cho bạn biết yêu cầu của bạn đã thành công hay có sự cố. Các phản hồi này bao gồm mã trạng thái và một lời giải thích ngắn gọn (gọi là Cụm từ Lý do ) cung cấp thông tin chi tiết về cách máy chủ xử lý yêu cầu của bạn.



#### Dòng trạng thái(Status Line)

Dòng đầu tiên trong mỗi phản hồi HTTP được gọi là Dòng Trạng thái . Nó cung cấp cho bạn ba thông tin chính:

* Phiên bản HTTP : Thông tin này cho bạn biết phiên bản HTTP nào đang được sử dụng.
* Mã trạng thái : Số gồm ba chữ số hiển thị kết quả yêu cầu của bạn.
* Cụm từ lý do : Một thông báo ngắn giải thích mã trạng thái theo cách dễ hiểu đối với con người.



#### Mã trạng thái và cụm từ lý do(Status Codes and Reason Phrases)

Mã Trạng thái là số cho biết yêu cầu thành công hay thất bại, trong khi Cụm từ Lý do giải thích điều gì đã xảy ra. Các mã này được chia thành năm loại chính:



**Phản hồi thông tin (100-199)**

Các mã này có nghĩa là máy chủ đã nhận được một phần yêu cầu và đang chờ phần còn lại . Đây là tín hiệu "tiếp tục".



**Phản hồi thành công (200-299)**

Các mã này có nghĩa là mọi thứ hoạt động như mong đợi. Máy chủ đã xử lý yêu cầu và gửi lại dữ liệu được yêu cầu.



**Tin nhắn chuyển hướng (300-399)**

Các mã này cho bạn biết rằng tài nguyên bạn yêu cầu đã được chuyển đến một vị trí khác, thường cung cấp URL mới.



**Phản hồi lỗi từ máy khách (400-499)**

Các mã này cho biết yêu cầu có vấn đề. Có thể URL bị sai hoặc bạn thiếu một số thông tin bắt buộc, chẳng hạn như xác thực.



**Phản hồi lỗi máy chủ (500-599)**

Các mã này có nghĩa là máy chủ đã gặp lỗi khi cố gắng thực hiện yêu cầu. Đây thường là sự cố phía máy chủ chứ không phải lỗi của máy khách.



#### Mã trạng thái chung(Common Status Codes)

Sau đây là một số mã trạng thái thường thấy nhất:



**100 (Tiếp tục)**

Máy chủ đã nhận được phần đầu tiên của yêu cầu và sẵn sàng cho phần còn lại .



**200 (OK)**

Yêu cầu đã thành công và máy chủ đang gửi lại tài nguyên được yêu cầu.



**301 (Đã di chuyển vĩnh viễn)**

Tài nguyên bạn đang yêu cầu đã được di chuyển vĩnh viễn đến một URL mới. Hãy sử dụng URL mới từ bây giờ.



**404 (Không tìm thấy)**

Máy chủ không tìm thấy tài nguyên tại URL đã cho. Vui lòng kiểm tra lại xem bạn đã nhập đúng địa chỉ chưa.



**500 (Lỗi máy chủ nội bộ)**

Đã xảy ra lỗi ở phía máy chủ và không thể xử lý yêu cầu của bạn.



# Phản hồi HTTP: Tiêu đề và Nội dung

#### Tiêu đề phản hồi(Response Headers)

Khi máy chủ web phản hồi một yêu cầu HTTP , nó sẽ bao gồm các tiêu đề phản hồi HTTP , về cơ bản là các cặp khóa-giá trị. Các tiêu đề này cung cấp thông tin quan trọng về phản hồi và cho máy khách (thường là trình duyệt) biết cách xử lý.



Hãy hình dung ví dụ về phản hồi HTTP với các tiêu đề được tô sáng. Các tiêu đề chính như **Content-Type**, **Content-Length**, và **Date** cung cấp cho chúng ta thông tin chi tiết quan trọng về phản hồi mà máy chủ gửi lại.



**HTTP/1.1 200 OK**

**Content-Type: application/json**

**Content-Length: 34**

**Date: Wed, 29 Aug 2024 12:00:00 GMT**



**{**

    \*\*"message": "Login successful!",\*\*

    \\\*\\\*"status": "success"\\\*\\\*





**}**



#### Tiêu đề phản hồi bắt buộc

Một số tiêu đề phản hồi rất quan trọng để đảm bảo phản hồi HTTP hoạt động bình thường. Chúng cung cấp thông tin cần thiết mà cả máy khách và máy chủ cần để xử lý mọi thứ một cách chính xác. Dưới đây là một vài tiêu đề quan trọng:



* **Ngày :**

Ví dụ: **Date: Fri, 23 Aug 2024 10:43:21 GMT**

Tiêu đề này hiển thị ngày và giờ chính xác khi phản hồi được máy chủ tạo ra.



* **Content-Type :**

Ví dụ: **Content-Type: text/html; charset=utf-8**

Thuộc tính này cho biết loại nội dung mà máy khách đang nhận được, chẳng hạn như HTML, JSON hay nội dung nào khác. Thuộc tính này cũng bao gồm bộ ký tự (như UTF-8) để giúp trình duyệt hiển thị nội dung chính xác.



* **Máy chủ :**

Ví dụ: **Server: nginx**

Tiêu đề này hiển thị loại phần mềm máy chủ nào đang xử lý yêu cầu. Tiêu đề này hữu ích cho việc gỡ lỗi, nhưng cũng có thể tiết lộ thông tin máy chủ có thể hữu ích cho kẻ tấn công, vì vậy nhiều người thường xóa hoặc che giấu tiêu đề này.



#### Các tiêu đề phản hồi phổ biến khác

Bên cạnh những tiêu đề thiết yếu, còn có những tiêu đề phổ biến khác cung cấp hướng dẫn bổ sung cho máy khách hoặc trình duyệt và giúp kiểm soát cách xử lý phản hồi.



* **Set-Cookie :**

Ví dụ: **Set-Cookie: sessionId=38af1337es7a8**

Phương thức này gửi cookie từ máy chủ đến máy khách, sau đó máy khách sẽ lưu trữ cookie và gửi lại cho các yêu cầu trong tương lai. Để đảm bảo an toàn, hãy đảm bảo cookie được thiết lập với HttpOnlycờ (để JavaScript không thể truy cập) và Securecờ (để cookie chỉ được gửi qua HTTPS).



* **Cache-Control :**

Ví dụ: **Cache-Control: max-age=600**

Tiêu đề này cho máy khách biết thời gian có thể lưu trữ phản hồi trong bộ nhớ đệm trước khi kiểm tra lại với máy chủ. Nó cũng có thể ngăn chặn thông tin nhạy cảm được lưu trữ trong bộ nhớ đệm nếu cần (sử dụng no-cache).



* **Vị trí :(Location)**

Ví dụ: **Location: /index.html**

Trường này được sử dụng trong các phản hồi chuyển hướng (3xx). Nó cho máy khách biết phải đi đâu tiếp theo nếu tài nguyên đã được di chuyển. Nếu người dùng có thể sửa đổi tiêu đề này trong khi yêu cầu, hãy cẩn thận xác thực và khử trùng nó—nếu không, bạn có thể gặp phải các lỗ hổng chuyển hướng mở, nơi kẻ tấn công có thể chuyển hướng người dùng đến các trang web độc hại.



#### Cơ quan phản hồi

Nội dung phản hồi HTTP là nơi chứa dữ liệu thực tế—những thứ như HTML, JSON , hình ảnh, v.v., mà máy chủ gửi lại cho máy khách. Để ngăn chặn các cuộc tấn công chèn mã độc như Cross-Site Scripting ( XSS ), hãy luôn khử trùng và loại bỏ mọi dữ liệu (đặc biệt là nội dung do người dùng tạo) trước khi đưa vào phản hồi.



# Tiêu đề bảo mật(Security Headers)

#### Tiêu đề bảo mật

Tiêu đề bảo mật HTTP giúp cải thiện bảo mật tổng thể của ứng dụng web bằng cách cung cấp các biện pháp giảm thiểu các cuộc tấn công như Cross-Site Scripting ( XSS ), clickjacking, v.v. Bây giờ, chúng ta sẽ tìm hiểu sâu hơn về các tiêu đề bảo mật sau:

* Chính sách bảo mật nội dung ( CSP )
* Bảo mật vận chuyển nghiêm ngặt (HSTS)
* Tùy chọn loại nội dung X
* Chính sách giới thiệu

Bạn có thể sử dụng trang web như **https://securityheaders.io/** để phân tích các tiêu đề bảo mật của bất kỳ trang web nào. Sau khi thảo luận về bài tập này, hy vọng bạn sẽ hiểu rõ hơn về nội dung mà nó báo cáo.



#### Chính sách bảo mật nội dung ( CSP :  Cloud Service Provider)

Tiêu đề CSP là một lớp bảo mật bổ sung có thể giúp giảm thiểu các cuộc tấn công phổ biến như Cross-Site Scripting ( XSS ). Mã độc hại có thể được lưu trữ trên một trang web hoặc tên miền riêng biệt và được đưa vào trang web dễ bị tấn công. CSP cung cấp cho quản trị viên cách xác định tên miền hoặc nguồn nào được coi là an toàn và cung cấp một lớp giảm thiểu các cuộc tấn công như vậy.



Ngay trong tiêu đề, bạn có thể thấy các thuộc tính như **default-src** hoặc **script-src** defined và nhiều thuộc tính khác. Mỗi thuộc tính này cung cấp cho quản trị viên tùy chọn xác định ở nhiều mức độ chi tiết khác nhau những tên miền nào được phép cho loại nội dung nào. Việc sử dụng self là một từ khóa đặc biệt phản ánh cùng một tên miền mà trang web được lưu trữ.



Nhìn vào một ví dụ về tiêu đề CSP :

**Content-Security-Policy: default-src 'self'; script-src 'self' https://cdn.tryhackme.com; style-src 'self'**



Chúng ta thấy việc sử dụng:



* default-src

\- chỉ định chính sách mặc định của self, nghĩa là chỉ trang web hiện tại.



* script-src

\- chỉ định chính sách về nơi các tập lệnh có thể được tải từ đó, chính sách này cũng giống như các tập lệnh được lưu trữ trênhttps://cdn.tryhackme.com



* style-src

\- chỉ định chính sách về nơi có thể tải các bảng định kiểu CSS từ trang web hiện tại (self)



#### Bảo mật vận chuyển nghiêm ngặt (HSTS)

Tiêu đề HSTS đảm bảo rằng trình duyệt web sẽ luôn kết nối qua HTTPS. Hãy xem một ví dụ về HSTS:

**Strict-Transport-Security: max-age=63072000; includeSubDomains; preload**



Sau đây là phân tích chi tiết về tiêu đề HSTS theo chỉ thị:

* max-age

\- Đây là thời gian hết hạn tính bằng giây cho cài đặt này

* includeSubDomains

\- Thiết lập tùy chọn hướng dẫn trình duyệt áp dụng thiết lập này cho tất cả các miền phụ.

* Tải trước

\- Cài đặt tùy chọn này cho phép đưa trang web vào danh sách tải trước. Trình duyệt có thể sử dụng danh sách tải trước để áp dụng HSTS ngay cả trước khi truy cập trang web lần đầu.

#### Tùy chọn loại nội dung X

Tiêu đề X-Content-Type-Options có thể được sử dụng để hướng dẫn trình duyệt không đoán thời gian MIME của một tài nguyên mà chỉ sử dụng tiêu đề Content-Type. Sau đây là một ví dụ:

**X-Content-Type-Options: nosniff**



Sau đây là phân tích chi tiết về tiêu đề X-Content-Type-Options theo chỉ thị:

* nosniff

\- Chỉ thị này hướng dẫn trình duyệt không đánh hơi hoặc đoán loại MIME .



#### Chính sách giới thiệu

Tiêu đề này kiểm soát lượng thông tin được gửi đến máy chủ web đích khi người dùng được chuyển hướng từ máy chủ web nguồn, chẳng hạn như khi họ nhấp vào siêu liên kết. Tiêu đề này cho phép quản trị viên web kiểm soát thông tin được chia sẻ. Dưới đây là một số ví dụ về Chính sách Giới thiệu:

* **Referrer-Policy: no-referrer**
* **Referrer-Policy: same-origin**
* **Referrer-Policy: strict-origin**
* **Referrer-Policy: strict-origin-when-cross-origin**



Sau đây là phân tích chi tiết về tiêu đề Referrer-Policy theo chỉ thị:

* **không có người giới thiệu(no-referrer)**

\- Điều này hoàn toàn vô hiệu hóa bất kỳ thông tin nào được gửi về người giới thiệu

* **same-origin**

\- Chính sách này sẽ chỉ gửi thông tin người giới thiệu khi đích đến thuộc cùng một nguồn gốc. Điều này hữu ích khi bạn muốn thông tin người giới thiệu được truyền đi khi các siêu liên kết nằm trong cùng một trang web nhưng không nằm ngoài các trang web bên ngoài.

* **strict-origin**

\- Chính sách này chỉ gửi người giới thiệu làm nguồn gốc khi giao thức không thay đổi. Vì vậy, người giới thiệu sẽ được gửi khi một kết nối HTTPS chuyển sang một kết nối HTTPS khác.

* **strict-origin-when-cross-origin**

\- Tương tự như strict-origin ngoại trừ các yêu cầu cùng nguồn gốc, trong đó nó gửi đường dẫn URL đầy đủ trong tiêu đề nguồn gốc.



# Những điều cơ bản về JavaScript :

#### Biến số(Variables)

Biến là các vùng chứa cho phép bạn lưu trữ các giá trị dữ liệu trong chúng. Giống như bất kỳ ngôn ngữ nào khác, biến trong JS cũng tương tự như các vùng chứa để lưu trữ dữ liệu. Khi bạn lưu trữ một thứ gì đó trong một thùng chứa (bucket), bạn cũng cần phải gắn nhãn cho nó để có thể dễ dàng tham chiếu sau này. Tương tự, trong JS, mỗi biến đều có một tên; khi chúng ta lưu trữ một giá trị nhất định trong một biến, chúng ta gán một tên cho nó để tham chiếu sau này.  hình ảnh của các kiểu var, let và constCó ba cách để khai báo biến trong JS: var, let, và const. Trong khi , và , varđều nằm trong phạm vi hàm, thì let, và const, đều nằm trong phạm vi khối, giúp kiểm soát tốt hơn khả năng hiển thị của biến trong các khối mã cụ thể.



#### Kiểu dữ liệu(Data-Types)

Trong JS, kiểu dữ liệu xác định loại giá trị mà một biến có thể lưu trữ. Ví dụ bao gồm string(văn bản), number( Boolean đúng/sai), null, undefined và object (cho dữ liệu phức tạp hơn như mảng hoặc đối tượng).



#### Chức năng(Functions)

Hàm đại diện cho một khối mã được thiết kế để thực hiện một tác vụ cụ thể. Bên trong hàm, bạn nhóm các mã cần thực hiện một tác vụ tương tự. Ví dụ: bạn đang phát triển một ứng dụng web cần in kết quả của học sinh lên trang web. Trường hợp lý tưởng là tạo một hàm PrintResult(rollNum) chấp nhận số báo danh của người dùng làm đối số.



   **<script>**

        \*\*function PrintResult(rollNum) {\*\*

            \\\*\\\*alert("Username with roll number " + rollNum + " has passed the exam");\\\*\\\*

&nbsp;           \\\\\\\*\\\\\\\*// any other logic to display the result\\\\\\\*\\\\\\\*

        \\\\\\\*\\\\\\\*}\\\\\\\*\\\\\\\*



        \\\\\\\*\\\\\\\*for (let i = 0; i < 100; i++) {\\\\\\\*\\\\\\\*

            \\\\\\\*\\\\\\\*PrintResult(rollNumbers\\\\\\\\\\\\\\\[i]);\\\\\\\*\\\\\\\*

        \\\\\\\*\\\\\\\*}\\\\\\\*\\\\\\\*

    \\\\\\\*\\\\\\\*</script>\\\\\\\*\\\\\\\*










 

Vì vậy, thay vì viết cùng một mã in cho tất cả học sinh, chúng ta sẽ sử dụng một hàm đơn giản để in kết quả.



#### Vòng lặp(Loops)

Vòng lặp cho phép bạn chạy một khối mã nhiều lần miễn là điều kiện còn tồn tại true. Các vòng lặp phổ biến trong JS là for, while, và do...while, được sử dụng để lặp lại các tác vụ, chẳng hạn như duyệt qua danh sách các mục. Ví dụ: nếu chúng ta muốn in kết quả của 100 học sinh, chúng ta có thể gọi hàm PrintResult(rollNum) 100 lần bằng cách viết 100 lần, hoặc chúng ta có thể tạo một vòng lặp sẽ được lặp lại từ 1 đến 100 và sẽ gọi hàm PrintResult(rollNum) như minh họa bên dưới.



        **// Function to print student result**

        \*\*function PrintResult(rollNum) {\*\*

            \\\*\\\*alert("Username with roll number " + rollNum + " has passed the exam");\\\*\\\*

&nbsp;           \\\\\\\*\\\\\\\*// any other logic to the display result\\\\\\\*\\\\\\\*

        \\\\\\\*\\\\\\\*}\\\\\\\*\\\\\\\*



        \\\\\\\*\\\\\\\*for (let i = 0; i < 100; i++) {\\\\\\\*\\\\\\\*

            \\\\\\\*\\\\\\\*PrintResult(rollNumbers\\\\\\\\\\\\\\\[i]); // this will be called 100 times\\\\\\\*\\\\\\\* 

        \\\\\\\*\\\\\\\*}\\\\\\\*\\\\\\\*










 

#### Chu kỳ yêu cầu-phản hồi(Request-Response Cycle)

Trong phát triển web, chu trình yêu cầu-phản hồi là khi trình duyệt của người dùng (máy khách) gửi yêu cầu đến máy chủ web và máy chủ phản hồi thông tin được yêu cầu. Thông tin này có thể là trang web, dữ liệu hoặc các tài nguyên khác.



#### Tổng quan về JavaScript(JavaScript Overview)

Trong bài tập này, chúng ta sẽ sử dụng JS để tạo chương trình đầu tiên. JS là một ngôn ngữ thông dịch , nghĩa là mã được thực thi trực tiếp trong trình duyệt mà không cần biên dịch trước. Dưới đây là một đoạn mã JS mẫu minh họa các khái niệm chính, chẳng hạn như định nghĩa biến , hiểu các kiểu dữ liệu , sử dụng câu lệnh điều khiển luồng và viết các hàm đơn giản. Những khối xây dựng thiết yếu này giúp tạo ra các ứng dụng web động và tương tác hơn. Đừng lo lắng nếu bây giờ bạn thấy nó hơi mới - chúng ta sẽ thảo luận chi tiết về từng khái niệm này sau.



JS chủ yếu được thực thi ở phía máy khách, giúp dễ dàng kiểm tra và tương tác với HTML trực tiếp trong trình duyệt. Chúng ta sẽ sử dụng **Google Chrome Console** tính năng này để chạy chương trình JS đầu tiên, cho phép chúng ta viết và thực thi mã JS dễ dàng mà không cần thêm công cụ nào khác. Hãy làm theo các bước sau để bắt đầu:



* Mở Google Chrome bằng cách nhấp vào Google Chrome biểu tượng trên Màn hình của VM .
* Sau khi mở Chrome, hãy nhấn Ctrl + Shift + I để mở Console hoặc nhấp chuột phải vào bất kỳ đâu trên trang và chọn Inspect.
* Sau đó, nhấp vào Console tab. Bảng điều khiển này cho phép bạn chạy mã JS trực tiếp trên trình duyệt mà không cần cài đặt phần mềm bổ sung.



Hãy cùng tạo một chương trình JS đơn giản để cộng hai số và hiển thị kết quả. Dưới đây là mã:

let x = 5;

let y = 10;

let result = x + y;

console.log("The result is: " + result);



Trong đoạn mã trên, x và y là các biến lưu trữ các số. x + y là một biểu thức cộng hai số lại với nhau, trong khi console.log  là một hàm được sử dụng để in kết quả ra bảng điều khiển.

Sao chép mã trên và dán vào bảng điều khiển bằng cách nhấn phím Ctrl + V. Sau khi dán, nhấn Enter.



#### Tích hợp JavaScript vào HTML

###### **JavaScript nội bộ(Internal JavaScript)**

JS nội bộ đề cập đến việc nhúng mã JS trực tiếp vào tài liệu HTML. Phương pháp này được ưa chuộng hơn cho người mới bắt đầu vì nó cho phép họ thấy cách tập lệnh tương tác với HTML. Tập lệnh được chèn giữa **<script>** các thẻ. Các thẻ này có thể được đặt bên trong **<head>** phần (section), thường được sử dụng cho các tập lệnh cần được tải trước khi nội dung trang được hiển thị, hoặc bên trong **<body>** phần (section), nơi tập lệnh có thể được sử dụng để tương tác với các thành phần khi chúng được tải trên trang web.



Ví dụ

Để tạo tài liệu HTML với JS nội bộ, hãy nhấp chuột phải vào **Desktop** và chọn **Create Document > Empty File**. Đặt tên cho tệp **internal.html**. Tiếp theo, nhấp chuột phải vào **internal.html** tệp và choose **Open with Pluma** mở tệp trong trình soạn thảo văn bản.

Sau khi dán mã, hãy nhấp **File** và chọn **Save**, thao tác này sẽ lưu tệp vào **internal.html**. Nhấp đúp vào tệp để mở tệp trong trình duyệt Chrome, tại đó bạn sẽ thấy kết quả



Trong tài liệu HTML này, chúng tôi sử dụng JS nội bộ, nghĩa là mã được đặt trực tiếp bên trong tệp HTML trong thẻ **<script>** . JS tương tác với HTML bằng cách chọn một phần tử ( **<p>** với **id="result"** ) và cập nhật nội dung của nó bằng thẻ **document.getElementById("result").innerHTML**<script>. JS nội bộ này được thực thi khi trình duyệt tải tệp HTML.



###### **JavaScript bên ngoài(External JavaScript)**

JS bên ngoài bao gồm việc tạo và lưu trữ mã JS trong một tệp riêng biệt có đuôi mở rộng là **.js**  . Phương pháp này giúp các nhà phát triển giữ cho tài liệu HTML gọn gàng và ngăn nắp. Tệp JS bên ngoài có thể được lưu trữ hoặc lưu trữ trên cùng máy chủ web với tài liệu HTML hoặc trên máy chủ web bên ngoài như đám mây.



Điểm khác biệt của chúng tôi là sử dụng **src** thuộc tính trong thẻ <script> để tải JS từ một tệp bên ngoài. Khi trình duyệt tải trang, nó sẽ tìm kiếm **script.js** tệp đó và tải nội dung của nó vào tài liệu HTML. Cách tiếp cận này cho phép chúng tôi tách biệt mã JS với HTML, giúp mã được tổ chức tốt hơn và dễ bảo trì hơn, đặc biệt là khi làm việc trên các dự án lớn.



#### Lạm dụng chức năng đối thoại(Abusing Dialogue Functions)

Một trong những mục tiêu chính của JS là cung cấp các hộp thoại để tương tác với người dùng và cập nhật nội dung động trên các trang web. JS cung cấp các hàm tích hợp như **alert**, **prompt**, và **confirm** để tạo điều kiện thuận lợi cho tương tác này. Các hàm này cho phép nhà phát triển hiển thị thông báo, thu thập dữ liệu đầu vào và nhận xác nhận từ người dùng. Tuy nhiên, nếu không được triển khai an toàn, kẻ tấn công có thể lợi dụng các tính năng này để thực hiện các cuộc tấn công như Cross-Site Scripting (XSS), mà bạn sẽ tìm hiểu sau trong học phần này.



###### **Báo động(Alert)**

Hàm cảnh báo hiển thị thông báo trong hộp thoại với OKnút " ", thường được dùng để truyền đạt thông tin hoặc cảnh báo cho người dùng. Ví dụ: nếu muốn hiển thị "Hello THM" cho người dùng, chúng ta sẽ sử dụng  alert("HelloTHM");. Để dùng thử, hãy mở bảng điều khiển Chrome, nhập alert("Hello THM"), và nhấn Enter. Một hộp thoại với thông báo sẽ xuất hiện trên màn hình.



###### **Nhắc nhở(Prompt)**

Hàm prompt hiển thị hộp thoại yêu cầu người dùng nhập dữ liệu. Hàm này trả về giá trị đã nhập khi người dùng nhấp vào "OK", hoặc null nếu người dùng nhấp vào "Cancel". Ví dụ: để yêu cầu người dùng nhập tên, chúng ta sẽ sử dụng prompt("What is your name?");.



Để kiểm tra điều này, hãy mở bảng điều khiển Chrome và dán nội dung sau yêu cầu nhập tên người dùng và chào hỏi anh ta.



**name = prompt("What is your name?");**

    \*\*alert("Hello " + name);\*\*







Sau khi dán mã và nhấn Enter, một hộp thoại sẽ xuất hiện và giá trị do người dùng nhập sẽ được trả về bảng điều khiển.



###### **Xác nhận(Confirm)**

Hàm xác nhận sẽ hiển thị một hộp thoại với thông báo và hai nút: "**OK**" và "**Cancel**". Hàm trả về true nếu người dùng nhấp vào "**OK**" và false nếu người dùng nhấp vào "**Cancel**". Ví dụ: để yêu cầu người dùng xác nhận, chúng ta sẽ sử dụng **confirm("Are you sure?")**;. Để thử, hãy mở bảng điều khiển Chrome, nhập **confirm("Do you want to proceed?")**, và nhấn **Enter**.



Một hộp thoại sẽ xuất hiện và tùy thuộc vào việc người dùng nhấp vào "**OK**" hay "**Cancel**", giá trị đúng hoặc sai sẽ được trả về bảng điều khiển.



#### Khám phá các tệp được thu nhỏ

Cho đến bây giờ, chúng ta đã hiểu cách JS hoạt động và cách chúng ta có thể đọc nó, nhưng điều gì sẽ xảy ra nếu tệp không thể đọc được bằng con người và đã được thu nhỏ ?



Thu nhỏ trong JS là quá trình nén các tệp JS bằng cách loại bỏ tất cả các ký tự không cần thiết, chẳng hạn như khoảng trắng, ngắt dòng, chú thích và thậm chí rút gọn tên biến. Điều này giúp giảm kích thước tệp và cải thiện thời gian tải trang web, đặc biệt là trong môi trường production. Các tệp được thu nhỏ làm cho mã nguồn gọn gàng hơn và khó đọc hơn đối với người dùng, nhưng chúng vẫn hoạt động hoàn toàn giống nhau.



Tương tự như vậy, việc **làm tối nghĩa(obfuscation)** thường được sử dụng để làm cho JS khó hiểu hơn bằng cách thêm mã không mong muốn, đổi tên biến và hàm thành tên vô nghĩa và thậm chí chèn mã giả.



###### **Sự che giấu trong hành động(Obfuscation in Action)**

Bây giờ, chúng ta sẽ thử thu nhỏ và làm tối nghĩa mã JS bằng một công cụ trực tuyến. Truy cập trang web(**https://codebeautify.org/javascript-obfuscato**r) và sao chép nội dung của hello.js, rồi dán vào hộp thoại trên trang web. Công cụ sẽ thu nhỏ và làm tối nghĩa mã, biến nó thành một chuỗi ký tự vô nghĩa.



###### **Giải mã mã(Deobfuscating a Code)**

Chúng tôi cũng có thể giải mã mã đã bị mã hóa bằng một công cụ trực tuyến. Truy cập trang web(**https://obf-io.deobfuscate.io/**) sau đó dán mã đã được mã hóa vào hộp thoại được cung cấp. Trang web sẽ tạo mã JS tương đương, dễ đọc cho bạn, giúp bạn dễ hiểu và phân tích tập lệnh gốc hơn.



# **Cơ bản về SQL**

#### **Giới thiệu về cơ sở dữ liệu(Introducing Databases)**

Được rồi, vậy là bạn đã được nghe về tầm quan trọng của chúng. Giờ là lúc để hiểu chúng là gì ngay từ đầu. Như đã đề cập trong phần giới thiệu, cơ sở dữ liệu rất phổ biến đến mức bạn rất có thể sẽ tương tác với các hệ thống đang sử dụng chúng. Cơ sở dữ liệu là một tập hợp thông tin hoặc dữ liệu có cấu trúc được tổ chức, dễ dàng truy cập và có thể được thao tác hoặc phân tích. Dữ liệu đó có thể tồn tại dưới nhiều hình thức, chẳng hạn như dữ liệu xác thực người dùng (như tên người dùng và mật khẩu), được lưu trữ và kiểm tra khi xác thực vào một ứng dụng hoặc trang web (ví dụ như TryHackMe), dữ liệu do người dùng tạo trên mạng xã hội (như Instagram và Facebook) nơi dữ liệu như bài đăng, bình luận, lượt thích của người dùng, v.v. được thu thập và lưu trữ, cũng như thông tin như lịch sử xem được lưu trữ bởi các dịch vụ phát trực tuyến như Netflix và được sử dụng để tạo đề xuất.



Tôi chắc bạn đã hiểu ý tôi: cơ sở dữ liệu được sử dụng rộng rãi và có thể chứa nhiều nội dung khác nhau. Không chỉ các doanh nghiệp quy mô lớn mới sử dụng cơ sở dữ liệu. Các doanh nghiệp quy mô nhỏ hơn, khi thành lập, gần như chắc chắn sẽ phải cấu hình cơ sở dữ liệu để lưu trữ dữ liệu. Nói về các loại cơ sở dữ liệu, hãy cùng xem xét chúng là gì.

#### 

#### **Các loại cơ sở dữ liệu khác nhau(Different Types of Databases)**

Giờ thì việc một thứ được rất nhiều người sử dụng và sử dụng trong thời gian (tương đối) dài đến mức cần có nhiều loại triển khai khác nhau là điều dễ hiểu. Có khá nhiều loại cơ sở dữ liệu khác nhau có thể được xây dựng, nhưng trong phần giới thiệu này, chúng ta sẽ tập trung vào hai loại chính: cơ sở dữ liệu quan hệ (còn gọi là SQL ) và cơ sở dữ liệu phi quan hệ (còn gọi là NoSQL).



* **Cơ sở dữ liệu quan hệ(Relational databases)**:  Lưu trữ dữ liệu có cấu trúc, nghĩa là dữ liệu được chèn vào cơ sở dữ liệu này tuân theo một cấu trúc nhất định. Ví dụ: dữ liệu được thu thập về người dùng bao gồm first\_name, last\_name, email\_address, username và password. Khi một người dùng mới tham gia, một mục nhập sẽ được tạo trong cơ sở dữ liệu theo cấu trúc này. Dữ liệu có cấu trúc này được lưu trữ theo hàng và cột trong một bảng (tất cả sẽ được đề cập sau); sau đó, có thể thiết lập mối quan hệ giữa hai hoặc nhiều bảng (ví dụ: user và order\_history), do đó có thuật ngữ cơ sở dữ liệu quan hệ.



* **Cơ sở dữ liệu phi quan hệ(Non-relational databases)**: Thay vì lưu trữ dữ liệu theo cách trên, hãy lưu trữ dữ liệu ở định dạng phi bảng. Ví dụ: nếu tài liệu đang được quét, có thể chứa nhiều loại và số lượng dữ liệu khác nhau, và được lưu trữ trong cơ sở dữ liệu yêu cầu định dạng phi bảng. Dưới đây là ví dụ về cách lưu trữ dữ liệu ở định dạng phi bảng:



 {

    \_id: ObjectId("4556712cd2b2397ce1b47661"),

    name: { first: "Thomas", last: "Anderson" },

    date\_of\_birth: new Date('Sep 2, 1964'),

    occupation: \[ "The One"],

    steps\_taken : NumberLong(4738947387743977493)

 }



Về việc lựa chọn cơ sở dữ liệu nào, điều quan trọng luôn phụ thuộc vào bối cảnh sử dụng cơ sở dữ liệu đó. Cơ sở dữ liệu quan hệ thường được sử dụng khi dữ liệu được lưu trữ chắc chắn sẽ được nhận ở một định dạng nhất quán, trong đó độ chính xác là yếu tố quan trọng, chẳng hạn như khi xử lý các giao dịch thương mại điện tử.  Mặt khác, cơ sở dữ liệu phi quan hệ được sử dụng tốt hơn khi dữ liệu nhận được có thể rất khác nhau về định dạng nhưng cần được thu thập và sắp xếp tại cùng một nơi, chẳng hạn như các nền tảng mạng xã hội thu thập nội dung do người dùng tạo ra.



#### **Bảng, Hàng và Cột(Tables, Rows and Columns)**

Bây giờ chúng ta đã định nghĩa hai loại cơ sở dữ liệu chính, chúng ta sẽ tập trung vào cơ sở dữ liệu quan hệ. Chúng ta sẽ bắt đầu bằng cách giải thích về bảng , hàng và cột . Tất cả dữ liệu được lưu trữ trong cơ sở dữ liệu quan hệ sẽ được lưu trữ trong một bảng ; ví dụ, một bộ sưu tập sách đang có trong kho tại một hiệu sách có thể được lưu trữ trong một bảng có tên là "Sách".



Khi tạo bảng này, bạn cần xác định những thông tin cần thiết để định nghĩa một bản ghi sách, ví dụ: "ID", "Name" và "Published\_date". Sau đó, đây sẽ là các cột của bạn ; khi xác định các cột này, bạn cũng sẽ xác định kiểu dữ liệu mà cột này nên chứa; nếu có nỗ lực chèn một bản ghi vào cơ sở dữ liệu mà kiểu dữ liệu không khớp, nó sẽ bị từ chối. Các kiểu dữ liệu có thể được xác định có thể khác nhau tùy thuộc vào cơ sở dữ liệu bạn đang sử dụng, nhưng các kiểu dữ liệu cốt lõi được sử dụng bao gồm Chuỗi (một tập hợp các từ và ký tự), Số nguyên (số), Số thực/Số thập phân (số có dấu thập phân) và Thời gian/Ngày tháng.



Sau khi tạo bảng với các cột đã xác định, bản ghi đầu tiên sẽ được chèn vào cơ sở dữ liệu, ví dụ: một cuốn sách có tên "Android Security Internals" với id là "1" và ngày xuất bản là "2014-10-14". Sau khi được chèn, bản ghi này sẽ được biểu diễn dưới dạng một hàng .



#### **Khóa chính và khóa ngoại(Primary and Foreign Keys)**

Sau khi một bảng đã được định nghĩa và điền đầy đủ dữ liệu, có thể cần lưu trữ thêm dữ liệu. Ví dụ, chúng ta muốn tạo một bảng có tên "Tác giả" để lưu trữ danh sách tác giả của những cuốn sách được bán trong cửa hàng. Dưới đây là một ví dụ rất rõ ràng về mối quan hệ này. Một cuốn sách (được lưu trữ trong bảng Sách) được viết bởi một tác giả (được lưu trữ trong bảng Tác giả). Nếu chúng ta muốn truy vấn một cuốn sách trong câu chuyện của mình nhưng cũng muốn tác giả của cuốn sách đó được trả về, dữ liệu của chúng ta cần phải được liên kết bằng cách nào đó; chúng ta thực hiện việc này bằng các khóa. Có hai loại khóa :



**Khóa chính(Primary Keys)** : Khóa chính được sử dụng để đảm bảo dữ liệu được thu thập trong một cột nhất định là duy nhất. Nghĩa là, cần phải có một cách để xác định mỗi bản ghi được lưu trữ trong một bảng, một giá trị duy nhất cho bản ghi đó và không bị lặp lại bởi bất kỳ bản ghi nào khác trong bảng đó. Hãy nghĩ về số hiệu nhập học trong một trường đại học; đây là những số được gán cho một sinh viên để họ có thể được xác định duy nhất trong các bản ghi (vì đôi khi sinh viên có thể có cùng tên). Một cột phải được chọn trong mỗi bảng làm khóa chính; trong ví dụ của chúng tôi, "id" sẽ hợp lý nhất vì một id đã được tạo duy nhất cho mỗi cuốn sách, trong đó, các cuốn sách có thể có cùng ngày xuất bản hoặc (trong trường hợp hiếm hơn) tên sách. Lưu ý rằng chỉ có thể có một cột khóa chính trong một bảng.



**Khóa Ngoại(Foreign Keys)** : Khóa ngoại là một cột (hoặc nhiều cột) trong một bảng, đồng thời cũng tồn tại trong một bảng khác trong cơ sở dữ liệu, do đó tạo ra một liên kết giữa hai bảng. Trong ví dụ này, hãy tưởng tượng việc thêm trường "author\_id" vào bảng "Books"; trường này sẽ hoạt động như một khóa ngoại vì author\_id trong bảng "Books" tương ứng với cột "id" trong bảng "author". Khóa ngoại cho phép thiết lập mối quan hệ giữa các bảng khác nhau trong cơ sở dữ liệu quan hệ. Lưu ý rằng có thể có nhiều hơn một cột khóa ngoại trong một bảng.



#### **SQL**

###### **SQL là gì ?**

Về mặt lý thuyết, tất cả những điều này nghe có vẻ tuyệt vời, nhưng trên thực tế, cơ sở dữ liệu hoạt động như thế nào? Bạn sẽ tạo bảng đầu tiên và điền dữ liệu vào đó như thế nào? Bạn sẽ sử dụng cái gì? Cơ sở dữ liệu thường được điều khiển bằng Hệ thống Quản lý Cơ sở dữ liệu (DBMS). Đóng vai trò là giao diện giữa người dùng cuối và cơ sở dữ liệu, DBMS là một chương trình phần mềm cho phép người dùng truy xuất, cập nhật và quản lý dữ liệu đang được lưu trữ. Một số ví dụ về DBMS bao gồm MySQL, MongoDB, Oracle Database và Maria DB.



Tương tác giữa người dùng cuối và cơ sở dữ liệu có thể được thực hiện bằng SQL (Ngôn ngữ truy vấn có cấu trúc). SQL là ngôn ngữ lập trình có thể được sử dụng để truy vấn, định nghĩa và thao tác dữ liệu được lưu trữ trong cơ sở dữ liệu quan hệ.



###### **Lợi ích của SQL và cơ sở dữ liệu quan hệ**

SQL gần như phổ biến như chính cơ sở dữ liệu, và điều này hoàn toàn có lý do. Dưới đây là một số lợi ích khi học và sử dụng SQL :



* Nhanh :  Cơ sở dữ liệu quan hệ (hay còn gọi là cơ sở dữ liệu sử dụng SQL ) có thể trả về khối lượng dữ liệu khổng lồ gần như ngay lập tức do sử dụng rất ít không gian lưu trữ và tốc độ xử lý cao.



* Dễ học:  Không giống như nhiều ngôn ngữ lập trình khác, SQL được viết bằng tiếng Anh đơn giản, giúp việc học dễ dàng hơn nhiều. Tính dễ đọc của ngôn ngữ này giúp người dùng có thể tập trung vào việc học các hàm và cú pháp.



* Đáng tin cậy:  Như đã đề cập trước đó, cơ sở dữ liệu quan hệ có thể đảm bảo mức độ chính xác khi xử lý dữ liệu bằng cách xác định cấu trúc nghiêm ngặt mà các tập dữ liệu phải nằm trong đó để có thể chèn vào.



* Linh hoạt:  SQL cung cấp mọi khả năng khi truy vấn cơ sở dữ liệu; điều này cho phép người dùng thực hiện các tác vụ phân tích dữ liệu lớn một cách rất hiệu quả.



#### **Câu lệnh cơ sở dữ liệu và bảng**

###### **TẠO CƠ SỞ DỮ LIỆU**

Nếu cần một cơ sở dữ liệu mới, bước đầu tiên bạn cần thực hiện là tạo cơ sở dữ liệu đó. Việc này có thể được thực hiện trong SQL bằng câu lệnh sau **CREATE DATABASE** :

**mysql> CREATE DATABASE database\_name;**



###### **HIỂN THỊ CƠ SỞ DỮ LIỆU**

Bây giờ chúng ta đã tạo xong cơ sở dữ liệu, chúng ta có thể xem nó bằng câu lệnh **SHOW DATABASES**. Câu lệnh **SHOW DATABASES** sẽ trả về danh sách các cơ sở dữ liệu hiện có. Chạy câu lệnh như sau:

**mysql> SHOW DATABASES;**



Trong danh sách trả về, bạn sẽ thấy cơ sở dữ liệu vừa tạo và một số cơ sở dữ liệu được bao gồm theo mặc định (mysql, information\_scheme, performance\_scheme và sys), được sử dụng cho nhiều mục đích khác nhau để mysql hoạt động.



###### **SỬ DỤNG CƠ SỞ DỮ LIỆU**

Sau khi tạo cơ sở dữ liệu, bạn có thể muốn tương tác với nó. Trước khi có thể tương tác, chúng ta cần cho mysql biết chúng ta muốn tương tác với cơ sở dữ liệu nào (để mysql biết cần chạy các truy vấn tiếp theo với cơ sở dữ liệu nào). Để thiết lập cơ sở dữ liệu vừa tạo làm cơ sở dữ liệu đang hoạt động, chúng ta sẽ chạy **USE** câu lệnh như sau (hãy đảm bảo chạy câu lệnh này trên máy của bạn):

**mysql> USE thm\_bookmarket\_db;**



###### **XÓA CƠ SỞ DỮ LIỆU**

Khi một cơ sở dữ liệu không còn cần thiết nữa (có thể nó được tạo ra cho mục đích thử nghiệm, hoặc không còn cần thiết nữa), bạn có thể xóa nó bằng **DROP** câu lệnh. Để xóa cơ sở dữ liệu, chúng ta sẽ sử dụng cú pháp câu lệnh sau (mặc dù trong trường hợp này, chúng ta muốn giữ lại cơ sở dữ liệu, vì vậy không cần phải tự chạy câu lệnh này!):

**mysql> DROP database database\_name;**



###### **Câu lệnh bảng**

**-TẠO BẢNG :**

Theo logic của các câu lệnh cơ sở dữ liệu, việc tạo bảng cũng sử dụng một câu lệnh **CREATE**. Khi cơ sở dữ liệu đã hoạt động (bạn đã chạy USE câu lệnh trên đó), một bảng có thể được tạo bên trong cơ sở dữ liệu đó bằng cú pháp câu lệnh sau:

**mysql> CREATE TABLE example\_table\_name (**

&nbsp;   \*\*example\\\_column1 data\\\_type,\*\*

    \*\*example\\\_column2 data\\\_type,\*\*

    \*\*example\\\_column3 data\\\_type\*\*


**);**

**-BẢNG HIỂN THỊ :**

Cũng như chúng ta có thể liệt kê các cơ sở dữ liệu bằng câu lệnh **SHOW**, chúng ta cũng có thể liệt kê các bảng trong cơ sở dữ liệu hiện đang hoạt động (cơ sở dữ liệu mà chúng ta đã sử dụng câu lệnh **USE** lần cuối). Chạy lệnh sau, bạn sẽ thấy bảng vừa tạo:

**mysql> SHOW TABLES;**



###### **MÔ TẢ**

Nếu chúng ta muốn biết những cột nào có trong một bảng (và kiểu dữ liệu của chúng), chúng ta có thể mô tả chúng bằng lệnh **DESCRIBE** (cũng có thể viết tắt là DESC). Hãy mô tả bảng bạn vừa tạo bằng lệnh sau:

**mysql> DESCRIBE book\_inventory;**



###### **THAY ĐỔI**

Sau khi tạo bảng, có thể sẽ đến lúc nhu cầu về tập dữ liệu của bạn thay đổi và bạn cần chỉnh sửa bảng. Việc này có thể được thực hiện bằng cách sử dụng **ALTER** câu lệnh. Bây giờ, hãy tưởng tượng rằng chúng ta thực sự muốn có một cột trong kho sách chứa số trang của mỗi cuốn sách. Thêm cột này vào bảng bằng câu lệnh sau:

**mysql> ALTER TABLE book\_inventory**

**ADD page\_count INT;**

Câu lệnh này **ALTER** có thể được sử dụng để thực hiện các thay đổi trong bảng, chẳng hạn như đổi tên cột, thay đổi kiểu dữ liệu trong cột hoặc xóa cột.



###### **LÀM RƠI**

Tương tự như xóa cơ sở dữ liệu, bạn cũng có thể xóa bảng bằng câu lệnh **DROP**. Chúng ta không cần phải làm điều này, nhưng cú pháp bạn có thể sử dụng là:

**mysql> DROP TABLE table\_name;**



#### **Hoạt động CRUD**

###### **CRUD**

**CRUD** là viết tắt của Tạo , Đọc , Cập nhật và Xóa , được coi là các thao tác cơ bản trong bất kỳ hệ thống quản lý dữ liệu nào.



Hãy cùng khám phá tất cả các thao tác khác nhau này khi làm việc với **MySQL** .



###### **Tạo hoạt động (INSERT)**

Thao tác Create sẽ tạo các bản ghi mới trong một bảng. Trong MySQL, thao tác này có thể được thực hiện bằng cách sử dụng câu lệnh **INSERT INTO**, như minh họa bên dưới.

**mysql> INSERT INTO books (id, name, published\_date, description)**

&nbsp;   \*\*VALUES (1, "Android Security Internals", "2014-10-14", "An In-Depth Guide to Android's Security Architecture");\*\*






**Query OK, 1 row affected (0.01 sec)**

Như chúng ta có thể thấy, INSERT INTOcâu lệnh này chỉ định một bảng, trong trường hợp này là  books , nơi bạn có thể thêm một bản ghi mới; các cột id , name , published\_date và description là các bản ghi trong bảng. Trong ví dụ này, một bản ghi mới có id là  1 , tên là "Android Security Internals ", published\_date là " 2014-10-14 ", và mô tả ghi rõ " Android Security Internals cung cấp sự hiểu biết đầy đủ về nội dung bảo mật của thiết bị Android " đã được thêm vào.



###### **Đọc hoạt động (SELECT)**

Thao tác Đọc , đúng như tên gọi, được sử dụng để đọc hoặc lấy thông tin từ một bảng. Chúng ta có thể lấy một cột hoặc tất cả các cột từ một bảng bằng SELECTcâu lệnh, như được hiển thị trong ví dụ tiếp theo.

**mysql> SELECT \* FROM books;**

**+----+----------------------------+----------------+------------------------------------------------------+**

**| id | name                       | published\_date | description                                          |**

**+----+----------------------------+----------------+------------------------------------------------------+**

**|  1 | Android Security Internals | 2014-10-14     | An In-Depth Guide to Android's Security Architecture |**

**+----+----------------------------+----------------+------------------------------------------------------+**

**1 row in set (0.00 sec)**



Câu lệnh đầu ra ở trên **SELECT** được theo sau bởi một **\*** ký hiệu cho biết tất cả các cột sẽ được truy xuất, theo sau là **FROM** mệnh đề và tên bảng, trong trường hợp này  là books .

Nếu chúng ta muốn chọn một cột cụ thể như tên và mô tả , chúng ta nên chỉ định chúng thay vì \*ký hiệu, như được hiển thị bên dưới.

**mysql> SELECT name, description FROM books;**

**+----------------------------+------------------------------------------------------+**

**| name                       | description                                          |**

**+----------------------------+------------------------------------------------------+**

**| Android Security Internals | An In-Depth Guide to Android's Security Architecture |**

**+----------------------------+------------------------------------------------------+**

**1 row in set (0.00 sec)**



###### **Hoạt động cập nhật (UPDATE)**

Hoạt động Cập nhật **UPDATE** sẽ sửa đổi một bản ghi hiện có trong một bảng và có thể sử dụng cùng một câu lệnh , cho mục đích này.

**mysql> UPDATE books**

&nbsp;   \*\*SET description = "An In-Depth Guide to Android's Security Architecture."\*\*

    \*\*WHERE id = 1;\*\*






**Query OK, 1 row affected (0.00 sec)**

**Rows matched: 1  Changed: 1  Warnings: 0**



Câu UPDATE lệnh chỉ định bảng, trong trường hợp này là  books , sau đó chúng ta có thể sử dụng SETtheo sau là tên cột mà chúng ta sẽ cập nhật. WHEREMệnh đề chỉ định hàng nào sẽ cập nhật khi mệnh đề được đáp ứng, trong trường hợp này là hàng có id là 1 .



###### **Xóa thao tác (DELETE)**

Thao tác xóa sẽ xóa các bản ghi khỏi bảng. Chúng ta có thể thực hiện thao tác này bằng câu lệnh **DELETE**.

**mysql> DELETE FROM books WHERE id = 1;**



**Query OK, 1 row affected (0.00 sec)**



Ở trên, chúng ta có thể quan sát DELETEcâu lệnh theo sau là FROMmệnh đề cho phép chúng ta chỉ định bảng mà bản ghi sẽ bị xóa, trong trường hợp này là books , theo sau là WHEREmệnh đề cho biết rằng đó phải là bảng có id là 1 .



#### **Các điều khoản(Clauses)**

###### **Mệnh đề DISTINCT**

Mệnh đề này DISTINCTđược sử dụng để tránh các bản ghi trùng lặp khi thực hiện truy vấn, chỉ trả về các giá trị duy nhất.

**mysql> SELECT DISTINCT name FROM books;**



###### **Mệnh đề GROUP BY**

Mệnh đề này **GROUP BY** tổng hợp dữ liệu từ nhiều bản ghi và nhóm kết quả truy vấn thành các cột. Điều này có thể hữu ích cho việc tổng hợp các hàm.

m**ysql> SELECT name, COUNT(\*)**

&nbsp;   \*\*FROM books\*\*

    \*\*GROUP BY name;\*\*


**+----------------------------+----------+**

**| name                       | COUNT(\*) |**

**+----------------------------+----------+**

**| Android Security Internals |        1 |**

**| Bug Bounty Bootcamp        |        1 |**

**| Car Hacker's Handbook      |        1 |**

**| Designing Secure Software  |        1 |**

**| Ethical Hacking            |        2 |**

**+----------------------------+----------+**

**5 rows in set (0.00 sec)**



Trong ví dụ trên, các bản ghi trên bảng book được nhóm lại theo kết quả của  hàm **COUNT**. Chúng ta đã biết rằng Ethical hacking được liệt kê hai lần, do đó tổng số  là 2, được đặt ở cuối vì nó được  nhóm  theo số lượng.



###### **Mệnh đề ORDER BY**

Mệnh đề này **ORDER BY** có thể được sử dụng để sắp xếp các bản ghi được trả về bởi một truy vấn theo thứ tự tăng dần hoặc giảm dần. Việc sử dụng các hàm như **ASC** và **DESC** có thể giúp chúng ta thực hiện điều đó.



-THỨ TỰ TĂNG TỚI

**mysql> SELECT \***

&nbsp;   \*\*FROM books\*\*

    \*\*ORDER BY published\\\_date ASC;\*\*


**+----+----------------------------+----------------+--------------------------------------------------------+**

**| id | name                       | published\_date | description                                            |**

**+----+----------------------------+----------------+--------------------------------------------------------+**

**|  1 | Android Security Internals | 2014-10-14     | An In-Depth Guide to Android's Security Architecture   |**

**|  3 | Car Hacker's Handbook      | 2016-02-25     | A Guide for the Penetration Tester                     |**

**|  5 | Ethical Hacking            | 2021-11-02     | A Hands-on Introduction to Breaking In                 |**

**|  6 | Ethical Hacking            | 2021-11-02     |                                                        |**

**|  2 | Bug Bounty Bootcamp        | 2021-11-16     | The Guide to Finding and Reporting Web Vulnerabilities |**

**|  4 | Designing Secure Software  | 2021-12-21     | A Guide for Developers                                 |**

**+----+----------------------------+----------------+--------------------------------------------------------+**

**6 rows in set (0.00 sec)**



-THỨ TỰ GIẢM TỐT

**mysql> SELECT \***

&nbsp;   \*\*FROM books\*\*

    \*\*ORDER BY published\\\_date DESC;\*\*


**+----+----------------------------+----------------+--------------------------------------------------------+**

**| id | name                       | published\_date | description                                            |**

**+----+----------------------------+----------------+--------------------------------------------------------+**

**|  4 | Designing Secure Software  | 2021-12-21     | A Guide for Developers                                 |**

**|  2 | Bug Bounty Bootcamp        | 2021-11-16     | The Guide to Finding and Reporting Web Vulnerabilities |**

**|  5 | Ethical Hacking            | 2021-11-02     | A Hands-on Introduction to Breaking In                 |**

**|  6 | Ethical Hacking            | 2021-11-02     |                                                        |**

**|  3 | Car Hacker's Handbook      | 2016-02-25     | A Guide for the Penetration Tester                     |**

**|  1 | Android Security Internals | 2014-10-14     | An In-Depth Guide to Android's Security Architecture   |**

**+----+----------------------------+----------------+--------------------------------------------------------+**

**6 rows in set (0.00 sec)**



Chúng ta có thể quan sát sự khác biệt khi sắp xếp theo thứ tự tăng dần bằng cách sử dụng ASCvà theo thứ tự giảm dần bằng cách sử dụng DESC, cả hai đều sử dụng published\_date làm tham chiếu.



###### **Mệnh đề HAVING**

Mệnh đề này **HAVING** được sử dụng cùng với các mệnh đề khác để lọc nhóm hoặc kết quả của các bản ghi dựa trên một điều kiện. Trong trường hợp **GROUP BY**, nó đánh giá điều kiện thành **TRUE** hoặc **FALSE**, không giống như **WHERE** mệnh đề **HAVING** lọc kết quả sau khi quá trình tổng hợp được thực hiện.

**mysql> SELECT name, COUNT(\*)**

&nbsp;   \*\*FROM books\*\*

    \*\*GROUP BY name\*\*

    \*\*HAVING name LIKE '%Hack%';\*\*


**+-----------------------+----------+**

**| name                  | COUNT(\*) |**

**+-----------------------+----------+**

**| Car Hacker's Handbook |        1 |**

**| Ethical Hacking       |        2 |**

**+-----------------------+----------+**

**2 rows in set (0.00 sec)**



Trong ví dụ trên, chúng ta có thể thấy rằng truy vấn trả về các cuốn sách có tên chứa từ hack và số lượng thích hợp, như chúng ta đã tìm hiểu trước đó.



#### **Người vận hành(Operaters)**

###### **Toán tử logic**

Các toán tử này kiểm tra tính đúng đắn của một điều kiện và trả về giá trị boolean là TRUE hoặc FALSE. Tiếp theo, chúng ta hãy cùng khám phá một số toán tử này.



###### **Toán tử LIKE**

Toán tử này **LIKE** thường được sử dụng kết hợp với các mệnh đề như " WHERE to filter" để lọc các mẫu cụ thể trong một cột. Hãy tiếp tục sử dụng **DataBase** của chúng ta để truy vấn một ví dụ về cách sử dụng của nó.

**mysql> SELECT \***

&nbsp;   \*\*FROM books\*\*

    \*\*WHERE description LIKE "%guide%";\*\*


**+----+----------------------------+----------------+--------------------------------------------------------+--------------------+**

**| id | name                       | published\_date | description                                            | category           |**

**+----+----------------------------+----------------+--------------------------------------------------------+--------------------+**

**|  1 | Android Security Internals | 2014-10-14     | An In-Depth Guide to Android's Security Architecture   | Defensive Security |**

**|  2 | Bug Bounty Bootcamp        | 2021-11-16     | The Guide to Finding and Reporting Web Vulnerabilities | Offensive Security |**

**|  3 | Car Hacker's Handbook      | 2016-02-25     | A Guide for the Penetration Tester                     | Offensive Security |**

**|  4 | Designing Secure Software  | 2021-12-21     | A Guide for Developers                                 | Defensive Security |**

**+----+----------------------------+----------------+--------------------------------------------------------+--------------------+**

**4 rows in set (0.00 sec)**



Truy vấn trên trả về danh sách các bản ghi từ những cuốn sách đã lọc, nhưng những bản ghi sử dụng mệnh **WHERE** đề có chứa từ hướng dẫn bằng cách sử dụng **LIKE** toán tử.



#### **Chức năng(Functions)**

###### **Hàm CONCAT()**

Hàm này được sử dụng để cộng hai hoặc nhiều chuỗi lại với nhau. Hàm này hữu ích để kết hợp văn bản từ các cột khác nhau.



###### **Hàm GROUP\_CONCAT()**

Hàm này có thể giúp chúng ta nối dữ liệu từ nhiều hàng vào một trường. Hãy cùng khám phá một ví dụ về cách sử dụng hàm này.



###### **Hàm SUBSTRING()**

Hàm này sẽ lấy một chuỗi con từ một chuỗi trong truy vấn, bắt đầu từ một vị trí xác định. Độ dài của chuỗi con này cũng có thể được chỉ định.



###### **Hàm LENGTH()**

Hàm này trả về số ký tự trong một chuỗi. Số ký tự này bao gồm cả khoảng trắng và dấu câu. Chúng ta có thể xem ví dụ bên dưới.



###### **Hàm COUNT()**

Hàm này trả về số lượng bản ghi trong một biểu thức.



###### **Hàm SUM()**

Hàm này tính tổng tất cả các giá trị (không phải NULL) của một cột xác định.



###### **Hàm MAX()**

Hàm này tính giá trị lớn nhất trong một cột được cung cấp trong một biểu thức.



###### **Hàm MIN()**

Hàm này tính giá trị nhỏ nhất trong một cột được cung cấp trong một biểu thức.

