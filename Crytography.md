# Các loại mã hóa

**Mã hóa đối xứng :**

-Mã hóa đối xứng , còn được gọi là mật mã đối xứng , sử dụng cùng một khóa để mã hóa và giải mã dữ liệu, như minh họa trong hình bên dưới. Việc giữ bí mật khóa là điều bắt buộc; nó còn được gọi là mật mã khóa riêng . Hơn nữa, việc truyền đạt khóa cho các bên dự định có thể là một thách thức vì nó đòi hỏi một kênh truyền thông an toàn. Việc giữ bí mật khóa có thể là một thách thức đáng kể, đặc biệt nếu có nhiều người nhận. Vấn đề trở nên nghiêm trọng hơn khi có sự hiện diện của một đối thủ mạnh; ví dụ như mối đe dọa gián điệp công nghiệp.

-Ví dụ về mã hóa đối xứng là DES (Tiêu chuẩn mã hóa dữ liệu), 3DES (Triple DES ) và AES (Tiêu chuẩn mã hóa nâng cao):

* DES được áp dụng làm tiêu chuẩn vào năm 1977 và sử dụng khóa 56 bit. Với sự tiến bộ về sức mạnh tính toán, năm 1999, một khóa DES đã bị phá thành công trong vòng chưa đầy 24 giờ, thúc đẩy sự chuyển đổi sang 3DES.
* 3DES là thuật toán DES được áp dụng ba lần; do đó, kích thước khóa là 168 bit, mặc dù độ bảo mật hiệu quả là 112 bit. 3DES giống như một giải pháp tùy biến khi DES không còn được coi là an toàn. 3DES đã bị loại bỏ vào năm 2019 và nên được thay thế bằng AES ; tuy nhiên, nó vẫn có thể được tìm thấy trong một số hệ thống cũ.
* AES được áp dụng làm tiêu chuẩn vào năm 2001. Kích thước khóa của nó có thể là 128, 192 hoặc 256 bit.

**Mã hóa bất đối xứng :**

-Không giống như mã hóa đối xứng, sử dụng cùng một khóa để mã hóa và giải mã, mã hóa bất đối xứng sử dụng một cặp khóa, một để mã hóa và một để giải mã, như minh họa bên dưới. Để bảo vệ tính bảo mật, mã hóa bất đối xứng hay mật mã bất đối xứng mã hóa dữ liệu bằng khóa công khai; do đó, nó còn được gọi là mật mã khóa công khai .

-Ví dụ là mật mã RSA , Diffie-Hellman và mật mã đường cong Elliptic ( ECC ). Hai khóa liên quan đến quy trình này được gọi là khóa công khai và khóa riêng tư . Dữ liệu được mã hóa bằng khóa công khai có thể được giải mã bằng khóa riêng tư. Khóa riêng tư của bạn cần được giữ bí mật, do đó có tên như vậy.

# RSA

-RSA là một thuật toán mã hóa khóa công khai cho phép truyền dữ liệu an toàn qua các kênh không an toàn. Với một kênh không an toàn, chúng tôi dự đoán kẻ thù sẽ nghe lén nó.

-RSA dựa trên bài toán khó về mặt toán học là phân tích một số lớn thành thừa số. Nhân hai số nguyên tố lớn là một phép toán đơn giản; tuy nhiên, việc tìm ước số của một số lớn đòi hỏi sức mạnh tính toán lớn hơn nhiều.

-Thuật toán RSA hoạt động dựa trên nguyên tắc mã hóa bất đối xứng, hay còn gọi là mã hóa công khai. Hãy tưởng tượng bạn có một cặp chìa khóa: một chìa khóa công khai (public key) bạn có thể đưa cho bất kỳ ai, và một chìa khóa bí mật (private key) bạn phải giữ tuyệt đối an toàn.

* Ai cũng có thể dùng Public Key của bạn để "khóa" (mã hóa) một tin nhắn và gửi cho bạn.
* Nhưng chỉ bạn mới có Private Key tương ứng để "mở khóa" (giải mã) tin nhắn đó.

Ngay cả người đã mã hóa tin nhắn cũng không thể giải mã nếu không có private key của bạn.

**Quá trình này diễn ra qua 3 bước chính: Tạo khóa, Mã hóa, và Giải mã :**

Bước 1: Tạo khóa (Key Generation):

Đây là bước tạo ra cặp khóa Public và Private. Quá trình này dựa trên các phép toán với số nguyên tố.

* Chọn hai số nguyên tố lớn: Chọn hai số nguyên tố p và q (trong thực tế, chúng rất lớn, có hàng trăm chữ số để đảm bảo an toàn).
* Tính n: Nhân hai số này với nhau để tạo ra n, là một phần của cả hai khóa.
* Tính Phi hàm Euler ϕ(n): Giá trị này được tính bằng công thức ϕ(n)=(p−1)×(q−1). Nó rất quan trọng để tạo ra mối liên kết toán học giữa hai khóa.
* Chọn số mũ công khai e: Chọn một số e sao cho 1<e<ϕ(n) và e phải là số nguyên tố cùng nhau với ϕ(n) (Ước chung lớn nhất của chúng là 1). e thường được chọn là các số nhỏ như 3, 17, hoặc phổ biến nhất là 65537 để tăng tốc độ mã hóa.
* Tính số mũ bí mật d: Tìm một số d sao cho (d × e) mod ϕ(n) = 1. d chính là nghịch đảo modular của e theo modulo ϕ(n).

->Public Key (công khai cho mọi người) là cặp số (n, e)

->Private Key (phải giữ bí mật) là cặp số (n, d)

Bước 2: Mã hóa (Encryption)

Giả sử có người muốn gửi cho bạn một tin nhắn. Tin nhắn này đầu tiên sẽ được chuyển thành một con số (gọi là M).

Người gửi sẽ dùng Public Key của bạn (n, e) để mã hóa M thành bản mã C bằng công thức:  C = M^e mod n

Bước 3: Giải mã (Decryption)

Khi bạn nhận được bản mã C, bạn sẽ dùng Private Key của mình (n, d) để giải mã nó về lại tin nhắn gốc M bằng công thức: M = C^d mod n

# Trao đổi khóa Diffie-Hellman

Trao đổi khóa nhằm mục đích thiết lập một bí mật chung giữa hai bên. Đây là một phương pháp cho phép hai bên thiết lập một bí mật chung qua một kênh truyền thông không an toàn mà không cần một bí mật chung đã tồn tại từ trước và không cần người quan sát có thể lấy được khóa này. Do đó, khóa chung này có thể được sử dụng để mã hóa đối xứng trong các giao tiếp tiếp theo.



Hãy xem xét tình huống sau. Alice và Bob muốn trao đổi thông tin một cách an toàn. Họ muốn thiết lập một khóa chung cho mật mã đối xứng nhưng không muốn sử dụng mật mã bất đối xứng để trao đổi khóa. Đây chính là lúc Trao đổi Khóa Diffie-Hellman phát huy tác dụng.



Alice và Bob tạo ra bí mật một cách độc lập; chúng ta hãy gọi những bí mật này là A và B. Họ cũng có một số tài liệu chung công khai; chúng ta hãy gọi là C.



Chúng ta cần đưa ra một số giả định. Thứ nhất, bất cứ khi nào chúng ta kết hợp các bí mật, chúng gần như không thể tách rời. Thứ hai, thứ tự kết hợp của chúng không quan trọng. Alice và Bob sẽ kết hợp các bí mật của họ với vật liệu chung để tạo thành AC và BC. Sau đó, họ sẽ gửi chúng cho nhau và kết hợp phần nhận được với bí mật của họ để tạo ra hai khóa giống hệt nhau, cả hai đều là ABC. Giờ đây, họ có thể sử dụng khóa này để giao tiếp.



Những con số được chọn quá nhỏ để đảm bảo an toàn và trong các ứng dụng thực tế, chúng ta sẽ cân nhắc những con số lớn hơn nhiều.



Trao đổi Khóa Diffie-Hellman thường được sử dụng cùng với mật mã khóa công khai RSA . Diffie-Hellman được sử dụng cho thỏa thuận khóa, trong khi RSA được sử dụng cho chữ ký số, vận chuyển khóa và xác thực, cùng nhiều ứng dụng khác. Ví dụ: RSA giúp chứng minh danh tính của người bạn đang nói chuyện thông qua chữ ký số, vì bạn có thể xác nhận dựa trên khóa công khai của họ. Điều này sẽ ngăn chặn kẻ tấn công tấn công trung gian vào Alice bằng cách giả danh Bob. Tóm lại, Diffie-Hellman và RSA được tích hợp vào nhiều giao thức và tiêu chuẩn bảo mật để cung cấp một giải pháp bảo mật toàn diện.

# SSH

**Xác thực máy chủ**

Nếu bạn đã từng sử dụng máy khách SSH trước đây, bạn sẽ biết lời nhắc xác nhận trong đầu ra của thiết bị đầu cuối bên dưới.



root@TryHackMe# ssh 10.10.244.173

The authenticity of host '10.10.244.173 (10.10.244.173)' can't be established.

ED25519 key fingerprint is SHA256:lLzhZc7YzRBDchm02qTX0qsLqeeiTCJg5ipOT0E/YM8.

This key is not known by any other name.

Are you sure you want to continue connecting (yes/no/\[fingerprint])? yes

Warning: Permanently added '10.10.244.173' (ED25519) to the list of known hosts.



Trong tương tác trên, máy khách SSH xác nhận xem chúng ta có nhận dạng được dấu vân tay khóa công khai của máy chủ hay không. ED25519 là thuật toán khóa công khai được sử dụng để tạo và xác minh chữ ký số trong ví dụ này. Máy khách SSH của chúng ta không nhận dạng được khóa này và yêu cầu chúng ta xác nhận xem có muốn tiếp tục kết nối hay không. Cảnh báo này là do có khả năng xảy ra tấn công trung gian; một máy chủ độc hại có thể đã chặn kết nối và phản hồi, giả mạo là máy chủ mục tiêu.

Trong trường hợp này, người dùng phải xác thực máy chủ, tức là xác nhận danh tính của máy chủ bằng cách kiểm tra chữ ký khóa công khai. Khi bạn trả lời "có", máy khách SSH sẽ ghi lại chữ ký khóa công khai này cho máy chủ này. Trong tương lai, nó sẽ tự động kết nối với bạn trừ khi máy chủ này trả lời bằng một khóa công khai khác.



**Xác thực máy khách**

Bây giờ chúng ta đã xác nhận đang giao tiếp với đúng máy chủ, chúng ta cần xác minh danh tính và được xác thực. Trong nhiều trường hợp, người dùng SSH được xác thực bằng tên người dùng và mật khẩu giống như bạn đăng nhập vào máy tính vật lý. Tuy nhiên, xét đến những vấn đề cố hữu của mật khẩu, điều này không nằm trong các biện pháp bảo mật tốt nhất.



Đến một lúc nào đó, chắc chắn bạn sẽ truy cập vào một máy tính được cấu hình SSH với xác thực khóa. Xác thực này sử dụng khóa công khai và khóa riêng để chứng minh máy khách là người dùng hợp lệ và được ủy quyền trên máy chủ. Theo mặc định, khóa SSH là khóa RSA . Bạn có thể chọn thuật toán để tạo và thêm cụm mật khẩu để mã hóa khóa SSH .



**ssh-keygen** là chương trình thường được sử dụng để tạo cặp khóa.



Chia sẻ khóa riêng sẽ là hành động thiếu an toàn nhất mà bất kỳ ai cũng có thể thực hiện đối với sự an toàn của mình. Một lưu ý khác, nếu chúng ta sử dụng **-t rsa**, thì các khóa thu được sẽ dài hơn nhiều.

 

**Khóa riêng SSH**

Như đã đề cập, bạn nên coi khóa SSH riêng tư của mình như mật khẩu. Tuyệt đối không chia sẻ chúng trong bất kỳ trường hợp nào; chúng được gọi là khóa riêng tư là có lý do. Người có khóa riêng tư của bạn có thể đăng nhập vào các máy chủ chấp nhận nó, tức là bao gồm nó trong số các khóa được ủy quyền, trừ khi khóa được mã hóa bằng cụm mật khẩu.



Điều rất quan trọng cần lưu ý là mật khẩu được sử dụng để giải mã khóa riêng không hề giúp máy chủ nhận dạng bạn; nó chỉ giải mã khóa riêng SSH . Mật khẩu không bao giờ được truyền đi và không bao giờ rời khỏi hệ thống của bạn.



Khi sử dụng các công cụ như John the Ripper , bạn có thể tấn công khóa SSH được mã hóa để cố gắng tìm ra cụm mật khẩu, nhấn mạnh tầm quan trọng của việc sử dụng cụm mật khẩu phức tạp và giữ bí mật khóa riêng của bạn.



Khi tạo khóa SSH để đăng nhập vào máy từ xa, bạn nên tạo khóa trên máy của mình rồi sao chép khóa công khai sang, vì điều này có nghĩa là khóa riêng tư sẽ không bao giờ tồn tại trên máy đích bằng cách sử dụng **ssh-copy-id**. Tuy nhiên, điều này không quan trọng lắm đối với các khóa tạm thời được tạo để truy cập hộp CTF.



Quyền phải được thiết lập chính xác để sử dụng khóa SSH riêng ; nếu không, máy khách SSH của bạn sẽ bỏ qua tệp kèm theo cảnh báo. Chỉ chủ sở hữu mới có thể đọc hoặc ghi vào khóa riêng (600 hoặc nghiêm ngặt hơn). **ssh -i privateKeyFileName user@host** Đây là cách bạn chỉ định khóa cho máy khách Linux OpenSSH tiêu chuẩn.



Khóa được máy chủ từ xa tin cậy

Thư mục này **~/.ssh** là nơi mặc định để lưu trữ các khóa này cho OpenSSH. **authorized\_keys** Tệp (lưu ý chính tả tiếng Anh Mỹ) trong thư mục này chứa các khóa công khai được phép truy cập vào máy chủ nếu xác thực khóa được bật. Theo mặc định trên nhiều bản phân phối Linux , xác thực khóa được bật vì nó an toàn hơn so với việc sử dụng mật khẩu để xác thực. Chỉ nên chấp nhận xác thực khóa nếu bạn muốn cho phép người dùng root truy cập SSH .



**Sử dụng Khóa SSH để có “Shell tốt hơn”**

Trong các cuộc thử nghiệm CTF, kiểm tra xâm nhập và các bài tập nhóm đỏ, khóa SSH là một cách tuyệt vời để "nâng cấp" shell ngược, giả sử người dùng đã bật tính năng đăng nhập. Lưu ý rằng www-data thường không cho phép điều này, nhưng người dùng thông thường và root vẫn có thể sử dụng. Việc để lại khóa **SSHauthorized\_keys** trong tệp trên máy có thể là một cửa hậu hữu ích, và bạn không cần phải xử lý bất kỳ vấn đề nào liên quan đến shell ngược không ổn định như Control-C hoặc thiếu hoàn thành tab.



# Chữ ký số và chứng chỉ số

**Chữ ký số là gì?**

Chữ ký số cung cấp một phương thức xác minh tính xác thực và toàn vẹn của một thông điệp hoặc tài liệu kỹ thuật số. Việc chứng minh tính xác thực của tệp tin đồng nghĩa với việc chúng ta biết ai đã tạo hoặc chỉnh sửa chúng. Sử dụng mật mã bất đối xứng, bạn tạo chữ ký bằng khóa riêng, có thể được xác minh bằng khóa công khai. Chỉ bạn mới có quyền truy cập vào khóa riêng, chứng minh bạn đã ký tệp tin. Ở nhiều quốc gia hiện đại, chữ ký số và chữ ký vật lý có giá trị pháp lý như nhau.



Hình thức chữ ký số đơn giản nhất là mã hóa tài liệu bằng khóa riêng của bạn. Nếu ai đó muốn xác minh chữ ký này, họ sẽ giải mã nó bằng khóa công khai của bạn và kiểm tra xem các tệp có khớp nhau không.



**Giấy chứng nhận: Chứng minh bạn là ai!**

Chứng chỉ là một ứng dụng thiết yếu của mật mã khóa công khai, và chúng cũng được liên kết với chữ ký số. Một ứng dụng phổ biến của chúng là HTTPS. Làm thế nào trình duyệt web của bạn biết được máy chủ bạn đang nói chuyện là tryhackme.com thực sự?



Câu trả lời nằm ở chứng chỉ. Máy chủ web có một chứng chỉ cho biết đó là tryhackme.com thực sự. Các chứng chỉ có một chuỗi tin cậy, bắt đầu với một CA gốc (Cơ quan cấp chứng chỉ). Từ thời điểm cài đặt, thiết bị, hệ điều hành và trình duyệt web của bạn sẽ tự động tin cậy các CA gốc khác nhau. Chứng chỉ chỉ được tin cậy khi các CA gốc nói rằng chúng tin cậy tổ chức đã ký chúng. Theo một cách nào đó, đây là một chuỗi; ví dụ: chứng chỉ được ký bởi một tổ chức, tổ chức được CA tin cậy và CA được trình duyệt của bạn tin cậy. Do đó, trình duyệt của bạn tin cậy chứng chỉ. Nhìn chung, có những chuỗi tin cậy dài. Bạn có thể xem các cơ quan cấp chứng chỉ được Mozilla Firefox tin cậy tại **https://wiki.mozilla.org/CA/Included\_Certificates** và Google Chrome tại **https://chromium.googlesource.com/chromium/src/+/main/net/data/ssl/chrome\_root\_store/root\_store.md** .



Giả sử bạn có một trang web và muốn sử dụng HTTPS. Bước này yêu cầu bạn phải có chứng chỉ TLS. Bạn có thể đăng ký chứng chỉ này từ nhiều cơ quan cấp chứng chỉ khác nhau với một khoản phí hàng năm. Hơn nữa, bạn có thể tự tạo chứng chỉ TLS cho các tên miền của mình bằng **Let's Encrypt** miễn phí. Nếu bạn đang vận hành một trang web, việc thiết lập và chuyển sang HTTPS là rất đáng giá, như bất kỳ trang web hiện đại nào khác.



# PGP và GPG

PGP là viết tắt của Pretty Good Privacy (Bảo mật khá tốt). Đây là phần mềm thực hiện mã hóa để mã hóa tệp, thực hiện ký số, v.v. GnuPG hay GPG là một triển khai mã nguồn mở của tiêu chuẩn OpenPGP.



GPG thường được sử dụng trong email để bảo vệ tính bảo mật của email. Hơn nữa, nó có thể được sử dụng để ký email và xác nhận tính toàn vẹn của email.



Bạn có thể cần sử dụng GPG để giải mã các tệp trong CTF. Với PGP/ GPG , khóa riêng có thể được bảo vệ bằng cụm mật khẩu tương tự như cách chúng ta bảo vệ khóa riêng SSH . Nếu khóa được bảo vệ bằng cụm mật khẩu, bạn có thể thử bẻ khóa bằng John the Ripper và . Khóa được cung cấp trong tác vụ này không được bảo vệ bằng cụm mật khẩu. Bạn có thể tìm thấy gpg2john trang hướng dẫn sử dụng GPG trực tuyến tại **https://www.gnupg.org/gph/de/manual/r1023.html** .



**Tóm Tắt Quy Trình Giải Mã :**

1.Kiểm tra khóa hiện có:         gpg --list-secret-keys

2.Nhập khóa riêng mới nếu cần:   gpg --import private.key

3.Giải mã tệp tin:               gpg --decrypt file.gpg > decrypted\_file.txt



# Hàm băm

**Hàm băm là gì?**

Hàm băm khác với mã hóa. Không có khóa, và việc chuyển từ đầu ra trở lại đầu vào được cho là bất khả thi (hoặc không thực tế về mặt tính toán).



Hàm băm lấy một số dữ liệu đầu vào có kích thước bất kỳ và tạo ra một bản tóm tắt hoặc bản tóm tắt của dữ liệu đó. Đầu ra có kích thước cố định. Việc dự đoán đầu ra cho bất kỳ đầu vào nào là rất khó khăn và ngược lại. Các thuật toán băm tốt sẽ tính toán tương đối nhanh và đảo ngược cực kỳ chậm, tức là, bắt đầu từ đầu ra và xác định đầu vào. Bất kỳ thay đổi nhỏ nào trong dữ liệu đầu vào, dù chỉ là một bit, cũng sẽ gây ra thay đổi đáng kể ở đầu ra.



Đầu ra của hàm băm thường là các byte thô, sau đó được mã hóa. Các mã hóa phổ biến là base64 hoặc thập lục phân. md5sum, sha1sum, sha256sum, và sha512sum tạo ra kết quả đầu ra ở định dạng thập lục phân. Lưu ý rằng định dạng thập lục phân in mỗi byte thô thành hai chữ số thập lục phân.



**Tại sao băm lại quan trọng?**

Băm đóng vai trò quan trọng trong việc sử dụng Internet hàng ngày của chúng ta. Giống như các hàm mật mã khác, băm được ẩn khỏi người dùng. Băm giúp bảo vệ tính toàn vẹn của dữ liệu và đảm bảo tính bảo mật của mật khẩu.



Hãy xem xét ví dụ này về việc sử dụng hàm băm để bảo vệ an ninh mạng của bạn. Khi bạn đăng nhập vào TryHackMe, máy chủ sẽ sử dụng hàm băm để xác minh mật khẩu của bạn. Trên thực tế, theo các thông lệ bảo mật tốt, máy chủ không ghi lại mật khẩu của bạn; nó ghi lại giá trị băm của mật khẩu. Bất cứ khi nào bạn muốn đăng nhập, máy chủ sẽ tính toán giá trị băm của mật khẩu bạn đã gửi cùng với giá trị băm đã ghi lại. Tương tự, khi bạn đăng nhập vào máy tính, hàm băm đóng vai trò xác minh mật khẩu của bạn. Bạn tương tác gián tiếp với hàm băm nhiều hơn bạn nghĩ, và hầu như hàng ngày trong bối cảnh mật khẩu.



**Hash Collision là gì?**

Va chạm băm xảy ra khi hai đầu vào khác nhau cho cùng một đầu ra. Các hàm băm được thiết kế để tránh va chạm tối đa có thể. Hơn nữa, các hàm băm được thiết kế để ngăn chặn kẻ tấn công cố ý tạo ra va chạm. Tuy nhiên, vì số lượng đầu vào gần như không giới hạn và số lượng đầu ra khả dĩ bị giới hạn, điều này dẫn đến hiệu ứng chuồng bồ câu.



Hiệu ứng chuồng bồ câu (Pigeon Hole) phát biểu rằng số lượng vật phẩm ( bồ câu ) nhiều hơn số lượng hộp đựng ( lồng chim bồ câu ); một số hộp đựng phải chứa nhiều hơn một vật phẩm. Nói cách khác, trong bối cảnh này, hàm băm có một số lượng cố định các giá trị đầu ra khác nhau, nhưng bạn có thể cung cấp cho nó bất kỳ kích thước đầu vào nào. Vì số lượng đầu vào nhiều hơn đầu ra, một số đầu vào chắc chắn sẽ cho cùng một kết quả đầu ra. Nếu bạn có 21 con bồ câu và 16 chuồng bồ câu, một số con bồ câu sẽ chia sẻ chuồng bồ câu. Do đó, va chạm là không thể tránh khỏi. Tuy nhiên, một hàm băm tốt đảm bảo rằng xác suất va chạm là không đáng kể.



# Sử dụng Hashing để lưu trữ mật khẩu an toàn

**Sử dụng Hashing để lưu trữ mật khẩu**

Đây chính là lúc băm phát huy tác dụng. Sẽ thế nào nếu thay vì lưu trữ mật khẩu, bạn chỉ lưu trữ giá trị băm của nó bằng một hàm băm an toàn? Quy trình này đồng nghĩa với việc bạn không bao giờ phải lưu trữ mật khẩu của người dùng, và nếu cơ sở dữ liệu của bạn bị rò rỉ, kẻ tấn công sẽ phải bẻ khóa từng mật khẩu để tìm ra mật khẩu đó.



Chỉ có một vấn đề với điều này. Điều gì sẽ xảy ra nếu hai người dùng có cùng mật khẩu? Vì hàm băm sẽ luôn biến cùng một đầu vào thành cùng một đầu ra, bạn sẽ lưu trữ cùng một hàm băm mật khẩu cho mỗi người dùng. Điều đó có nghĩa là nếu ai đó bẻ khóa hàm băm đó, họ sẽ có quyền truy cập vào nhiều tài khoản. Điều này cũng có nghĩa là ai đó có thể tạo Bảng Cầu Vồng để bẻ khóa các hàm băm.



Bảng Cầu Vồng là một bảng tra cứu các giá trị băm thành văn bản thuần túy, giúp bạn nhanh chóng tìm ra mật khẩu của người dùng chỉ từ giá trị băm. Bảng cầu vồng giúp đổi thời gian bẻ khóa băm lấy dung lượng ổ cứng, nhưng việc tạo ra nó cũng mất thời gian.



Các trang web như **CrackStation(https://crackstation.net/)** và **Hashes.com(https://hashes.com/en/decrypt/hash)** sử dụng bảng cầu vồng khổng lồ để bẻ khóa mật khẩu nhanh chóng cho các hàm băm không có muối . Việc tra cứu trong danh sách các hàm băm được sắp xếp sẽ nhanh hơn so với việc cố gắng bẻ khóa hàm băm.



**Bảo vệ chống lại bàn cầu vồng**

Để bảo vệ khỏi bảng cầu vồng, chúng tôi thêm một giá trị "muối" (salt) vào mật khẩu. Giá trị "muối" này là một giá trị được tạo ngẫu nhiên, được lưu trữ trong cơ sở dữ liệu và phải là duy nhất cho mỗi người dùng. Về lý thuyết, bạn có thể sử dụng cùng một giá trị "muối" cho tất cả người dùng, nhưng mật khẩu trùng lặp vẫn sẽ có cùng giá trị băm và bảng cầu vồng vẫn có thể được tạo cho mật khẩu với giá trị "muối" đó.



Muối được thêm vào đầu hoặc cuối mật khẩu trước khi băm, nghĩa là mỗi người dùng sẽ có một mã băm mật khẩu khác nhau ngay cả khi họ sử dụng cùng một mật khẩu. Các hàm băm như Bcrypt và Scrypt sẽ tự động xử lý việc này. Muối không cần phải được giữ bí mật.



**Sử dụng mã hóa để lưu trữ mật khẩu**

Xét đến vấn đề lưu trữ mật khẩu để xác thực, tại sao chúng ta không mã hóa mật khẩu thay vì thực hiện tất cả các bước rườm rà này? Lý do là ngay cả khi chúng ta chọn một thuật toán băm an toàn để mã hóa mật khẩu trước khi lưu trữ, chúng ta vẫn cần lưu trữ khóa đã sử dụng. Do đó, nếu ai đó có được khóa, họ có thể dễ dàng giải mã tất cả mật khẩu.



# Nhận dạng băm mật khẩu

**Mật khẩu Linux**

Trên Linux , các hàm băm mật khẩu được lưu trữ trong /etc/shadow, thông thường chỉ có root mới đọc được. Trước đây, chúng được lưu trữ trong /etc/passwd, mà ai cũng có thể đọc được.



Tệp này shadowchứa thông tin mật khẩu. Mỗi dòng chứa chín trường, được phân tách bằng dấu hai chấm ( :). Hai trường đầu tiên là tên đăng nhập và mật khẩu được mã hóa. Bạn có thể tìm hiểu thêm về các trường khác bằng cách chạy man 5 shadowtrên hệ thống Linux .



Trường mật khẩu được mã hóa chứa cụm mật khẩu đã băm với bốn thành phần: tiền tố (ID thuật toán), tùy chọn (tham số), muối và băm. Mật khẩu được lưu ở định dạng $prefix$options$salt$hash. Tiền tố giúp dễ dàng nhận dạng mật khẩu kiểu Unix và Linux ; nó chỉ định thuật toán băm được sử dụng để tạo băm.



Dưới đây là bảng tóm tắt một số tiền tố mật khẩu kiểu Unix phổ biến nhất mà bạn có thể gặp. Chúng được liệt kê theo thứ tự độ mạnh giảm dần. Bạn có thể tìm hiểu thêm về chúng bằng cách xem trang hướng dẫn sử dụng với **man 5 crypt**.

Tiền tố	                                              Thuật toán

$y$	                        yescrypt là một chương trình băm có thể mở rộng và là lựa chọn mặc định và được khuyến nghị trong các hệ thống mới

$gy$	                        gost-yescrypt sử dụng hàm băm GOST R 34.11-2012 và phương pháp băm yescrypt

$7$	                        scrypt là một hàm phái sinh khóa dựa trên mật khẩu

$2b$, $2y$, $2a$,$2x$	        bcrypt là một hàm băm dựa trên mã hóa khối Blowfish ban đầu được phát triển cho OpenBSD nhưng được hỗ trợ trên phiên bản gần đây của FreeBSD, NetBSD, Solaris 10 trở lên và một số bản phân phối Linux

$6$	                        sha512crypt là một hàm băm dựa trên SHA-2 với đầu ra 512-bit ban đầu được phát triển cho GNU libc và thường được sử dụng trên các hệ thống Linux (cũ hơn)

$md5	                        SunMD5 là một hàm băm dựa trên thuật toán MD5 ban đầu được phát triển cho Solaris

$1$	                        md5crypt là một hàm băm dựa trên thuật toán MD5 ban đầu được phát triển cho FreeBSD



**Mật khẩu MS Windows**

Mật khẩu MS Windows được băm bằng NTLM , một biến thể của MD4. Về mặt hình ảnh, chúng giống hệt với băm MD4 và MD5 , vì vậy việc sử dụng ngữ cảnh để xác định loại băm là rất quan trọng.



Trên MS Windows, các hàm băm mật khẩu được lưu trữ trong SAM (Trình quản lý Tài khoản Bảo mật). MS Windows cố gắng ngăn người dùng thông thường sao chép chúng, nhưng các công cụ như mimikatz tồn tại để vượt qua bảo mật của MS Windows. Đáng chú ý, các hàm băm được tìm thấy ở đó được chia thành hàm băm NT và hàm băm LM.



Một nơi tuyệt vời để tìm thêm định dạng băm và tiền tố mật khẩu là trang **Hashcat Example Hashes(https://hashcat.net/wiki/doku.php?id=example\_hashes)** . Đối với các loại băm khác, bạn thường cần kiểm tra độ dài hoặc mã hóa, hoặc thậm chí tìm hiểu về ứng dụng đã tạo ra chúng. Đừng bao giờ đánh giá thấp sức mạnh của việc nghiên cứu.



# Bẻ khóa mật khẩu

**Bẻ khóa mật khẩu bằng GPU**

GPU (Bộ xử lý đồ họa) hiện đại có hàng nghìn lõi. Chúng chuyên xử lý hình ảnh kỹ thuật số và tăng tốc đồ họa máy tính. Mặc dù không thể thực hiện cùng loại công việc như CPU , nhưng chúng rất giỏi trong một số phép tính toán học liên quan đến hàm băm. Bạn có thể sử dụng card đồ họa để bẻ khóa nhanh chóng nhiều loại hàm băm. Một số thuật toán băm, chẳng hạn như Bcrypt, được thiết kế sao cho việc băm trên GPU không cải thiện tốc độ so với việc sử dụng CPU ; điều này giúp chúng chống lại việc bẻ khóa.



**Cracking on VMs?**

Cần lưu ý rằng VM (Máy ảo) thường không có quyền truy cập vào card đồ họa của máy chủ. Tùy thuộc vào phần mềm ảo hóa bạn đang sử dụng, bạn có thể thiết lập tính năng này, nhưng khá phức tạp. Hơn nữa, hiệu suất sẽ giảm khi bạn sử dụng CPU từ hệ điều hành ảo hóa , và khi mục đích của bạn là bẻ khóa mã băm, bạn cần thêm mỗi chu kỳ CPU .



Nếu bạn muốn chạy Hashcat , tốt nhất nên chạy trên máy chủ để tận dụng tối đa GPU (nếu có). Nếu bạn thích MS Windows, bạn thật may mắn; các bản dựng MS Windows có sẵn trên trang web và bạn có thể chạy nó từ PowerShell . Bạn có thể chạy Hashcat với OpenCL trên máy ảo (VM) , nhưng tốc độ có thể sẽ chậm hơn so với việc chạy trên máy chủ.



John the Ripper sử dụng CPU theo mặc định và hoạt động trong VM ngay khi cài đặt, mặc dù bạn có thể có tốc độ tốt hơn khi chạy nó trên hệ điều hành máy chủ để tránh bất kỳ chi phí ảo hóa nào và tận dụng tối đa lõi và luồng CPU của bạn .



# HASHCAT

Hashcat sử dụng cú pháp cơ bản sau: **hashcat -m <hash\_type> -a <attack\_mode> hashfile wordlist**, trong đó:

* **-m <hash\_type>** Chỉ định kiểu băm ở định dạng số. Ví dụ: -m 1000dành cho NTLM
* **-a <attack\_mode>** Chỉ định chế độ tấn công. Ví dụ, -a 0là để tấn công trực tiếp, tức là thử từng mật khẩu trong danh sách từ.
* **hashfile** là tệp chứa mã băm mà bạn muốn bẻ khóa.
* **wordlist** là danh sách từ bảo mật mà bạn muốn sử dụng trong cuộc tấn công của mình.

Ví dụ, **hashcat -m 3200 -a 0 hash.txt /usr/share/wordlists/rockyou.txt** sẽ xử lý hàm băm như Bcrypt và thử các mật khẩu trong rockyou.txt tệp.



# Băm để kiểm tra tính toàn vẹn

**Kiểm tra tính toàn vẹn**

Có thể sử dụng hàm băm để kiểm tra xem các tệp có bị thay đổi hay không. Nếu bạn nhập cùng một dữ liệu, bạn sẽ luôn nhận được cùng một dữ liệu. Ngay cả khi một bit thay đổi, hàm băm cũng sẽ thay đổi đáng kể, như đã minh họa trong Bài tập 2. Điều này có nghĩa là bạn có thể sử dụng hàm băm để kiểm tra xem các tệp có bị thay đổi hay không hoặc để đảm bảo rằng tệp bạn đã tải xuống giống hệt với tệp trên máy chủ web. Tệp văn bản được liệt kê bên dưới hiển thị hàm băm SHA256 của hai tệp ISO Fedora Workstation. Nếu chạy sha256sumtrên tệp bạn đã tải xuống và trả về cùng một hàm băm được liệt kê trong tệp đã ký này, bạn có thể yên tâm rằng tệp của bạn giống hệt với tệp chính thức.



Bạn cũng có thể sử dụng hàm băm để tìm các tệp trùng lặp; nếu hai tài liệu có cùng hàm băm, chúng là cùng một tài liệu. Điều này rất tiện lợi cho việc tìm kiếm và xóa các tệp trùng lặp.



**HMAC**

HMAC (Mã xác thực tin nhắn có khóa băm) là một loại mã xác thực tin nhắn (MAC) sử dụng hàm băm mật mã kết hợp với khóa bí mật để xác minh tính xác thực và tính toàn vẹn của dữ liệu.



HMAC có thể được sử dụng để đảm bảo người tạo ra HMAC chính là người họ tự nhận, tức là tính xác thực được xác nhận; hơn nữa, nó chứng minh rằng thông điệp chưa bị sửa đổi hoặc làm sai lệch, tức là tính toàn vẹn được duy trì. Điều này đạt được thông qua việc sử dụng khóa bí mật để chứng minh tính xác thực và thuật toán băm để tạo ra hàm băm và chứng minh tính toàn vẹn.



Các bước sau đây sẽ giúp bạn hiểu rõ hơn về cách thức hoạt động của HMAC.

* Khóa bí mật được thêm vào kích thước khối của hàm băm.
* Khóa đệm được XOR với một hằng số (thường là một khối số không hoặc số một).
* Tin nhắn được băm bằng hàm băm với khóa XOR.
* Kết quả từ Bước 3 sau đó được băm lại bằng cùng một hàm băm nhưng sử dụng khóa được đệm XOR với một hằng số khác.
* Đầu ra cuối cùng là giá trị HMAC, thường là chuỗi có kích thước cố định.



# John the Ripper: The Basics

**Danh sách từ**

Như đã đề cập trước đó, để sử dụng tấn công từ điển vào các hàm băm, bạn cần một danh sách các từ để băm và so sánh; không có gì ngạc nhiên khi danh sách này được gọi là danh sách từ. Có rất nhiều danh sách từ khác nhau, và bạn có thể tìm thấy một bộ sưu tập tốt trong kho lưu trữ **SecLists(https://github.com/danielmiessler/SecLists)** . Có một vài nơi bạn có thể tìm thấy danh sách từ để tấn công hệ thống mong muốn; chúng tôi sẽ nhanh chóng hướng dẫn bạn tìm thấy chúng ở đâu.



Trên các bản phân phối AttackBox và Kali Linux , **/usr/share/wordlists** thư mục chứa một loạt danh sách từ tuyệt vời.



**Bẻ khóa băm cơ bản**

-Cú pháp cơ bản của các lệnh John the Ripper như sau. Chúng tôi sẽ đề cập đến các tùy chọn và bộ điều chỉnh cụ thể được sử dụng khi sử dụng chúng.

john \[options] \[file path]

* john: Gọi chương trình John the Ripper
* \[options]: Chỉ định các tùy chọn bạn muốn sử dụng
* \[file path]: Tệp chứa mã băm mà bạn đang cố gắng bẻ khóa; nếu tệp nằm trong cùng một thư mục, bạn không cần phải đặt tên đường dẫn, chỉ cần đặt tên tệp.



-John có các tính năng tích hợp để phát hiện loại băm đang được cung cấp và chọn các quy tắc và định dạng phù hợp để bẻ khóa nó cho bạn; đây không phải lúc nào cũng là ý tưởng tốt nhất vì nó có thể không đáng tin cậy, nhưng nếu bạn không thể xác định loại băm mình đang làm việc và muốn thử bẻ khóa, thì đây có thể là một lựa chọn tốt! Để làm điều này, chúng tôi sử dụng cú pháp sau:

john --wordlist=\[path to wordlist] \[path to file]

* --wordlist=: Chỉ định sử dụng chế độ danh sách từ, đọc từ tệp mà bạn cung cấp trong đường dẫn được cung cấp
* \[path to wordlist]: Đường dẫn đến danh sách từ bạn đang sử dụng, như đã mô tả trong nhiệm vụ trước



-Đôi khi, John sẽ không thích việc tự động nhận dạng và tải các hàm băm, nhưng không sao cả! Chúng ta có thể sử dụng các công cụ khác để nhận dạng hàm băm và sau đó đặt John về một định dạng cụ thể. Có nhiều cách để làm điều này, chẳng hạn như sử dụng một mã định danh hàm băm trực tuyến như trang web này(**https://hashes.com/en/tools/hash\_identifier**) . Tôi thích sử dụng một công cụ có tên là hash-identifier(**https://gitlab.com/kalilinux/packages/hash-identifier/-/tree/kali/master**) , một công cụ Python cực kỳ dễ sử dụng và sẽ cho bạn biết loại hàm băm mà bạn nhập có thể là gì, cung cấp cho bạn nhiều lựa chọn hơn nếu mã đầu tiên không thành công.



-Để sử dụng hash-identifier, bạn có thể sử dụng wget hoặc curl tải xuống tệp Python hash-id.py từ trang GitLab của nó(**https://gitlab.com/kalilinux/packages/hash-identifier/-/raw/kali/master/hash-id.py**) . Sau đó, khởi chạy nó python3 hash-id.py và nhập mã băm bạn muốn xác định. Nó sẽ cung cấp cho bạn danh sách các định dạng có khả năng xảy ra nhất.



-Sau khi xác định được mã băm mà bạn đang xử lý, bạn có thể yêu cầu John sử dụng mã băm đó trong khi bẻ khóa mã băm được cung cấp bằng cú pháp sau:

john --format=\[format] --wordlist=\[path to wordlist] \[path to file]

* --format=: Đây là cờ để báo cho John biết rằng bạn đang cung cấp cho nó một hàm băm có định dạng cụ thể và sử dụng định dạng sau để bẻ khóa nó
* \[format]: Định dạng của hàm băm

Ví dụ sử dụng:

john --format=raw-md5 --wordlist=/usr/share/wordlists/rockyou.txt hash\_to\_crack.txt



-Lưu ý về định dạng:

Khi bạn yêu cầu John sử dụng định dạng, nếu bạn đang xử lý một kiểu băm tiêu chuẩn, ví dụ  md5 như trong ví dụ trên, bạn phải thêm tiền tố vào raw-để cho John biết bạn chỉ đang xử lý một kiểu băm tiêu chuẩn, mặc dù điều này không phải lúc nào cũng đúng. Để kiểm tra xem bạn có cần thêm tiền tố hay không, bạn có thể liệt kê tất cả các định dạng của John bằng cách sử dụng john --list=formatsvà kiểm tra thủ công hoặc grep cho kiểu băm của bạn bằng cách sử dụng một lệnh như john --list=formats | grep -iF "md5".



**Bẻ khóa băm xác thực Windows**

-NTHash / NTLM

NThash là định dạng băm mà các máy tính chạy hệ điều hành Windows hiện đại sử dụng để lưu trữ mật khẩu người dùng và dịch vụ. Nó cũng thường được gọi là NTLM , ám chỉ phiên bản trước của định dạng băm mật khẩu Windows được gọi là LM, do đó là NT/LM.



Một chút lịch sử: ký hiệu NT cho các sản phẩm Windows ban đầu có nghĩa là Công nghệ Mới. Nó được sử dụng bắt đầu từ Windows NT để chỉ các sản phẩm không được xây dựng từ Hệ điều hành MS- DOS . Cuối cùng, dòng "NT" trở thành loại Hệ điều hành tiêu chuẩn được Microsoft phát hành, và tên gọi này đã bị loại bỏ, nhưng nó vẫn tồn tại trong tên của một số công nghệ của Microsoft.



Trong Windows, SAM (Trình quản lý Tài khoản Bảo mật) được sử dụng để lưu trữ thông tin tài khoản người dùng, bao gồm tên người dùng và mật khẩu đã băm. Bạn có thể lấy mã băm NTHash/ NTLM bằng cách sao chép cơ sở dữ liệu SAM vào máy tính Windows, sử dụng một công cụ như Mimikatz hoặc sử dụng cơ sở dữ liệu Active Directory: NTDS.dit. Bạn có thể không cần phải bẻ khóa mã băm để tiếp tục leo thang đặc quyền, vì bạn thường có thể thực hiện tấn công "truyền mã băm", nhưng đôi khi, bẻ khóa mã băm là một lựa chọn khả thi nếu có chính sách mật khẩu yếu.



**Bẻ khóa băm /etc/shadow**

\*\*-\*\*Tệp này /etc/shadowlà tệp trên máy Linux , nơi lưu trữ các mã băm mật khẩu. Nó cũng lưu trữ các thông tin khác, chẳng hạn như ngày thay đổi mật khẩu gần nhất và thông tin hết hạn mật khẩu. Tệp chứa một mục nhập trên mỗi dòng cho mỗi người dùng hoặc tài khoản người dùng của hệ thống. Tệp này thường chỉ có thể được truy cập bởi người dùng root, vì vậy bạn phải có đủ quyền để truy cập các mã băm. Tuy nhiên, nếu có, bạn vẫn có khả năng bẻ khóa được một số mã băm.

-John có thể rất khắt khe về định dạng dữ liệu cần thiết để có thể hoạt động; vì lý do này, để bẻ khóa /etc/shadowmật khẩu, bạn phải kết hợp dữ liệu đó với /etc/passwdtệp để John hiểu được dữ liệu được cung cấp. Để làm điều này, chúng tôi sử dụng một công cụ được tích hợp sẵn trong bộ công cụ John có tên là unshadow. Cú pháp cơ bản của unshadownhư sau:

unshadow \[path to passwd] \[path to shadow]

* unshadow: Gọi công cụ bỏ bóng
* \[path to passwd]: Tệp chứa bản sao của /etc/passwdtệp bạn đã lấy từ máy mục tiêu
* \[path to shadow]: Tệp chứa bản sao của /etc/shadowtệp bạn đã lấy từ máy mục tiêu

Ví dụ sử dụng:

unshadow local\_passwd local\_shadow > unshadowed.txt

-Lưu ý về các tập tin

Khi sử dụng unshadow, bạn có thể sử dụng toàn bộ các tệp /etc/passwd và /etc/shadow, giả sử bạn có sẵn chúng hoặc bạn có thể sử dụng dòng tương ứng từ mỗi tệp, ví dụ:

TỆP 1 - local\_passwd

Chứa /etc/passwd dòng dành cho người dùng root:

root:x:0:0::/root:/bin/bash



TỆP 2 - local\_shadow

Chứa /etc/shadow dòng dành cho người dùng root:root:$6$2nwjN454g.dv4HN/$m9Z/r2xVfweYVkrr.v5Ft8Ws3/YYksfNwq96UL1FX0OJjY1L6l.DS3KEVsZ9rOVLB/ldTeEL/OIhJZ4GMFMGA0:18576::::::



-Sau đó, chúng ta có thể đưa đầu ra từ unshadow, trong ví dụ sử dụng có tên unshadowed.txt, trực tiếp vào John. Chúng ta không cần chỉ định chế độ ở đây vì chúng ta đã tạo đầu vào dành riêng cho John; tuy nhiên, trong một số trường hợp, bạn sẽ cần chỉ định định dạng như chúng ta đã làm trước đó bằng cách sử dụng:--format=sha512crypt

john --wordlist=/usr/share/wordlists/rockyou.txt --format=sha512crypt unshadowed.txt



**Single Crack Mode**

Cho đến nay, chúng ta đã sử dụng chế độ danh sách từ của John để thử nghiệm các hàm băm đơn giản và không đơn giản. Nhưng John cũng có một chế độ khác, được gọi là chế độ Bẻ khóa Đơn . Trong chế độ này, John chỉ sử dụng thông tin được cung cấp trong tên người dùng để thử và tìm ra các mật khẩu khả thi theo phương pháp heuristic bằng cách thay đổi một chút các chữ cái và số có trong tên người dùng.

-Làm sai lệch từ ngữ

Cách tốt nhất để giải thích chế độ Single Crack và việc làm biến dạng từ ngữ là xem xét một ví dụ:

Hãy xem xét tên người dùng “Markus”.

Một số mật khẩu có thể là:

* Markus1, Markus2, Markus3 (v.v.)
* MARkus, MARkus, MARKus (v.v.)
* Markus!, Markus$, Markus\* (v.v.)

Kỹ thuật này được gọi là "xáo trộn từ". John xây dựng từ điển dựa trên thông tin được cung cấp và sử dụng một bộ quy tắc gọi là "xáo trộn", quy tắc này xác định cách thức nó có thể biến đổi từ gốc để tạo ra một danh sách từ dựa trên các yếu tố liên quan đến mục tiêu bạn đang cố gắng bẻ khóa. Kỹ thuật này khai thác cách mật khẩu yếu có thể được đặt dựa trên thông tin về tên người dùng hoặc dịch vụ mà họ đang đăng nhập.

-GECOS

Việc John triển khai việc xáo trộn từ ngữ cũng có tính năng tương thích với trường GECOS của hệ điều hành UNIX, cũng như các hệ điều hành tương tự UNIX khác như Linux . GECOS là viết tắt của Hệ điều hành Toàn diện General Electric. Trong bài tập trước, chúng ta đã xem xét các mục nhập cho cả hai /etc/shadowvà /etc/passwd. Nhìn kỹ, bạn sẽ thấy các trường được phân tách bằng dấu hai chấm :. Trường thứ năm trong bản ghi tài khoản người dùng là trường GECOS. Trường này lưu trữ thông tin chung về người dùng, chẳng hạn như họ tên đầy đủ, số điện thoại văn phòng và số điện thoại của người dùng, cùng nhiều thông tin khác. John có thể lấy thông tin được lưu trữ trong các bản ghi đó, chẳng hạn như họ tên đầy đủ và tên thư mục gốc, để thêm vào danh sách từ mà nó tạo ra khi bẻ /etc/shadowkhóa băm với chế độ bẻ khóa đơn.

-Using Single Crack Mode

Để sử dụng chế độ bẻ khóa đơn, chúng ta sử dụng cú pháp gần giống như chúng ta đã sử dụng cho đến nay; ví dụ, nếu chúng ta muốn bẻ khóa mật khẩu của người dùng có tên "Mike", bằng chế độ đơn, chúng ta sẽ sử dụng:

john --single --format=\[format] \[path to file]

* --single:Cờ này cho John biết bạn muốn sử dụng chế độ bẻ khóa băm đơn
* --format=\[format]:Như thường lệ, điều quan trọng là phải xác định đúng định dạng.

Ví dụ sử dụng:

john --single --format=raw-sha256 hashes.txt

-Lưu ý về định dạng tệp ở chế độ bẻ khóa đơn:

Nếu bạn đang bẻ khóa băm ở chế độ bẻ khóa đơn, bạn cần thay đổi định dạng tệp mà bạn đang cung cấp cho John để nó hiểu dữ liệu nào cần tạo danh sách từ. Bạn thực hiện việc này bằng cách thêm tên người dùng sở hữu băm vào đầu băm, vì vậy theo ví dụ trên, chúng ta sẽ thay đổi tệphashes.txt

Từ 1efee03cdcb96d90ad48ccc7b8666033



ĐẾN mike:1efee03cdcb96d90ad48ccc7b8666033



**Quy tắc tùy chỉnh**

-Quy tắc tùy chỉnh là gì?

Khi chúng ta khám phá những gì John có thể làm trong Chế độ Bẻ khóa Đơn, bạn có thể có một số ý tưởng về một số mẫu bẻ khóa hiệu quả hoặc những mẫu mà mật khẩu của bạn thường sử dụng có thể được sao chép bằng một mẫu bẻ khóa cụ thể. Tin tốt là bạn có thể tự định nghĩa các quy tắc của mình, mà John sẽ sử dụng để tạo mật khẩu động. Khả năng định nghĩa các quy tắc như vậy rất hữu ích khi bạn biết nhiều thông tin hơn về cấu trúc mật khẩu của bất kỳ mục tiêu nào.



-Quy tắc tùy chỉnh chung

Nhiều tổ chức sẽ yêu cầu mật khẩu ở một mức độ phức tạp nhất định để chống lại các cuộc tấn công từ điển. Nói cách khác, khi tạo tài khoản mới hoặc thay đổi mật khẩu, nếu bạn thử đặt mật khẩu như polopassword, thì rất có thể mật khẩu sẽ không hoạt động. Lý do có thể là do độ phức tạp của mật khẩu bắt buộc. Do đó, bạn có thể nhận được lời nhắc yêu cầu mật khẩu phải chứa ít nhất một ký tự từ mỗi trường hợp sau:

* Chữ thường
* Chữ in hoa
* Con số
* Biểu tượng



Độ phức tạp của mật khẩu là tốt! Tuy nhiên, chúng ta có thể tận dụng lợi thế là hầu hết người dùng sẽ dễ dàng đoán được vị trí của các ký tự này. Đối với các tiêu chí trên, nhiều người dùng sẽ sử dụng các ký tự sau:

Polopassword1!



Hãy xem xét mật khẩu với chữ cái viết hoa đầu tiên và một số theo sau là một ký hiệu ở cuối. Mẫu mật khẩu quen thuộc này, được thêm vào và đặt trước bởi các ký hiệu bổ nghĩa (chẳng hạn như chữ cái viết hoa hoặc ký hiệu), là một mẫu dễ nhớ mà mọi người sử dụng và tái sử dụng khi tạo mật khẩu. Mẫu này có thể cho phép chúng ta khai thác khả năng dự đoán độ phức tạp của mật khẩu.



Hiện tại, điều này đáp ứng các yêu cầu về độ phức tạp của mật khẩu; tuy nhiên, với tư cách là kẻ tấn công, chúng ta có thể lợi dụng thực tế là chúng ta biết vị trí có thể có của các phần tử được thêm vào này để tạo mật khẩu động từ danh sách từ của mình.



-Cách tạo Quy tắc tùy chỉnh

Các quy tắc tùy chỉnh được định nghĩa trong **john.conf** tệp. Tệp này có thể được tìm thấy trong **/opt/john/john.conf** TryHackMe Attackbox. Tệp này thường nằm trong **/etc/john/john.con**f nếu bạn đã cài đặt John bằng trình quản lý gói hoặc được xây dựng từ mã nguồn với make.



Hãy cùng xem qua cú pháp của các quy tắc tùy chỉnh này, sử dụng ví dụ trên làm mẫu mục tiêu. Lưu ý rằng bạn có thể định nghĩa mức độ kiểm soát chi tiết lớn trong các quy tắc này. Tôi khuyên bạn nên xem wiki tại đây(**https://www.openwall.com/john/doc/RULES.shtml**) để có cái nhìn tổng quan về các bộ điều chỉnh bạn có thể sử dụng và thêm ví dụ về cách triển khai quy tắc.



Dòng đầu tiên:

**\[List.Rules:THMRules]** được sử dụng để xác định tên quy tắc của bạn; đây là những gì bạn sẽ sử dụng để gọi quy tắc tùy chỉnh của mình là đối số John.

Sau đó, chúng tôi sử dụng mẫu khớp kiểu regex để xác định vị trí từ sẽ được sửa đổi; một lần nữa, chúng tôi sẽ chỉ đề cập đến các trình sửa đổi chính và phổ biến nhất ở đây:

* Az: Lấy từ và thêm vào đó các ký tự bạn định nghĩa
* A0: Lấy từ và thêm vào trước nó các ký tự bạn định nghĩa
* c: Viết hoa chữ cái theo vị trí

Bạn có thể sử dụng kết hợp những yếu tố này để xác định vị trí và nội dung trong từ mà bạn muốn sửa đổi.

Cuối cùng, chúng ta phải xác định những ký tự nào nên được thêm vào, thêm vào trước hoặc bao gồm theo cách khác. Chúng ta thực hiện việc này bằng cách thêm các bộ ký tự trong ngoặc vuông \[ ]tại vị trí cần sử dụng. Các bộ ký tự này tuân theo các mẫu sửa đổi bên trong dấu ngoặc kép " ". Dưới đây là một số ví dụ phổ biến:

* \[0-9]: Sẽ bao gồm các số từ 0-9
* \[0]: Chỉ bao gồm số 0
* \[A-z]: Sẽ bao gồm cả chữ hoa và chữ thường
* \[A-Z]: Chỉ bao gồm các chữ cái viết hoa
* \[a-z]: Chỉ bao gồm các chữ cái thường

Xin lưu ý rằng:

* \[a]: Sẽ chỉ bao gồma
* \[!£$%@]: Sẽ bao gồm các ký hiệu !, £, $, %, và @

Kết hợp tất cả những điều này lại với nhau, để tạo ra một danh sách từ các quy tắc phù hợp với mật khẩu mẫu Polopassword1!(giả sử từ đó polopassword có trong danh sách từ của chúng ta), chúng ta sẽ tạo một mục quy tắc trông như thế này:

**\[List.Rules:PoloPassword]**

**cAz"\[0-9] \[!£$%@]"**

Sử dụng những điều sau đây:

**c: Viết hoa chữ cái đầu tiên**

**Az: Thêm vào cuối từ**

**\[0-9]: Một số trong phạm vi 0-9**

**\[!£$%@]: Mật khẩu được theo sau bởi một trong những ký hiệu này**



-Sử dụng Quy tắc Tùy chỉnh

Sau đó chúng ta có thể gọi quy tắc tùy chỉnh này là đối số John bằng cách sử dụng  **--rule=PoloPassword** cờ.



Dưới dạng lệnh đầy đủ : **john --wordlist=\[path to wordlist] --rule=PoloPassword \[path to file]**



Lưu ý, tôi thấy việc nêu ra các mẫu sẽ hữu ích nếu bạn đang viết quy tắc; như đã trình bày ở trên, điều này cũng áp dụng cho việc viết các mẫu RegEx.



# Bẻ khóa các tệp Zip được bảo vệ bằng mật khẩu

**Zip2John**

Tương tự như **unshadow** công cụ chúng ta đã sử dụng trước đó, chúng ta sẽ sử dụng **zip2john** công cụ này để chuyển đổi tệp Zip sang định dạng băm mà John có thể hiểu và hy vọng bẻ khóa được. Cách sử dụng chính như sau:

**zip2john \[options] \[zip file] > \[output file]**

* **\[options]**: Cho phép bạn chuyển các tùy chọn tổng kiểm tra cụ thể tới zip2john; điều này thường không cần thiết
* **\[zip file]**: Đường dẫn đến tệp Zip mà bạn muốn lấy giá trị băm
* **>**: Điều này chuyển hướng đầu ra từ lệnh này sang một tệp khác
* **\[output file]**: Đây là tập tin sẽ lưu trữ đầu ra

Ví dụ sử dụng : zip2john zipfile.zip > zip\_hash.txt



**Cracking**

Sau đó, chúng ta có thể lấy tệp mà chúng ta xuất ra **zip2john** trong trường hợp sử dụng ví dụ của mình, **zip\_hash.txt**, và, như chúng ta đã làm với **unshadow**, đưa trực tiếp vào **John** vì chúng ta đã tạo đầu vào cụ thể cho tệp đó. : **john --wordlist=/usr/share/wordlists/rockyou.txt zip\_hash.txt**



# Bẻ khóa các tệp lưu trữ RAR được bảo vệ bằng mật khẩu

**Rar2John**

Gần giống với **zip2john** công cụ, chúng ta sẽ sử dụng **rar2john** công cụ này để chuyển đổi tệp RAR sang định dạng băm mà John có thể hiểu được. Cú pháp cơ bản như sau:

**rar2john \[rar file] > \[output file]**

* **\[rar file]**: Đường dẫn đến tệp RAR mà bạn muốn lấy giá trị băm
* **>**: Điều này chuyển hướng đầu ra của lệnh này sang một tệp khác
* **\[output file]**: Đây là tệp sẽ lưu trữ kết quả đầu ra từ lệnh

Ví dụ sử dụng : /opt/john/rar2john rarfile.rar > rar\_hash.txt



**Cracking**

Một lần nữa, chúng ta có thể lấy tệp đầu ra **rar2john** trong trường hợp sử dụng ví dụ của mình, **rar\_hash.txt**, và đưa trực tiếp vào **John** như chúng ta đã làm với **zip2john**.

**john --wordlist=/usr/share/wordlists/rockyou.txt rar\_hash.txt**



# Bẻ khóa SSH với John

Được rồi, được rồi, tôi hiểu ý bạn. Không còn tệp lưu trữ nào nữa! Tốt thôi! Hãy cùng khám phá thêm một cách sử dụng John thường xuyên xuất hiện trong các thử thách CTF—dùng John để bẻ khóa mật khẩu khóa riêng SSH id\_rsa của các tệp. Trừ khi được cấu hình khác, bạn sẽ xác thực thông tin đăng nhập SSH bằng mật khẩu. Tuy nhiên, bạn có thể cấu hình xác thực dựa trên khóa, cho phép bạn sử dụng khóa riêng, id\_rsa, làm khóa xác thực để đăng nhập vào máy tính từ xa qua SSH . Tuy nhiên, việc này thường yêu cầu mật khẩu để truy cập khóa riêng; ở đây, chúng ta sẽ dùng John để bẻ khóa mật khẩu này nhằm cho phép xác thực qua SSH bằng khóa.



**SSH2John**

Ai mà ngờ được, lại là một công cụ chuyển đổi khác chứ? Vâng, đó chính là mục đích của việc làm việc với John. Đúng như tên gọi, công cụ này ssh2john chuyển đổi id\_rsa khóa riêng tư, được sử dụng để đăng nhập vào phiên SSH, thành định dạng băm mà John có thể sử dụng. Đùa vậy thôi, đây là một ví dụ tuyệt vời khác về tính linh hoạt của John. Cú pháp khá giống với những gì bạn mong đợi. Lưu ý rằng nếu bạn chưa ssh2john cài đặt, bạn có thể sử dụng ssh2john.py, nằm trong /opt/john/ssh2john.py. Nếu bạn đang thực hiện việc này trên AttackBox, hãy thay thế ssh2john lệnh bằng python3 /opt/john/ssh2john.py hoặc trên Kali, python /usr/share/john/ssh2john.py.

**ssh2john \[id\_rsa private key file] > \[output file]**

* **\[id\_rsa private key file]**: Đường dẫn đến tệp id\_rsa mà bạn muốn lấy giá trị băm
* **>**: Đây là trình quản lý đầu ra. Chúng ta sử dụng nó để chuyển hướng đầu ra từ lệnh này sang một tệp khác.
* **\[output file]**: Đây là tập tin sẽ lưu trữ đầu ra từ

Ví dụ sử dụng : /opt/john/ssh2john.py id\_rsa > id\_rsa\_hash.txt



**Cracking**

Lần cuối cùng, chúng ta đưa tệp tin đầu ra từ ssh2john, trong trường hợp sử dụng ví dụ của chúng ta được gọi id\_rsa\_hash.txt và, như chúng ta đã làm với rar2john, chúng ta có thể sử dụng tệp này một cách liền mạch với John : **john --wordlist=/usr/share/wordlists/rockyou.txt id\_rsa\_hash.txt**

