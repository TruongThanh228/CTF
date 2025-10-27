ssh bandit0@bandit.labs.overthewire.org -p 2220



0->1 : ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If ---> cat readme

1->2 : 263JGJPfgU6LtdEvgfWU1XP5yac29mFx ---> cat ./-

2->3 : MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx ---> cat ./"--spaces in this filename--"

3->4 : 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ ---> cd ~/inhere ---> find ---> cat ./...Hiding-From-You

4->5 : 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw ---> cd ~/inhere ---> find ---> cat ./-file07

5->6 : HWasnPhtq9AVKe0dmk45nxy20cvUa6EG ---> cd ~/inhere ---> find . -size 1033c ---> cat ./maybehere07/.file2
\*\*Note\*\* : Dấu "." tìm kiếm trong thư mục

6->7 : morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj ---> find / -user bandit7 -group bandit6 -size 33c 2>/dev/null ---> cat /var/lib/dpkg/info/bandit7.password
\*\*Note\*\* : - / : tìm từ gốc của hệ thống (toàn bộ máy).
    - -user bandit7 : chỉ lấy file mà chủ sở hữu là user bandit7.
    - -group bandit6 : chỉ lấy file thuộc group bandit6.
    - -size 33c : chỉ lấy file có đúng 33 byte (c = bytes).
    - 2>/dev/null : bỏ qua các lỗi “Permission denied” khi bạn không có quyền đọc một số thư mục.

7->8 : dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc ---> grep millionth data.txt

8->9 : 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM ---> sort data.txt | uniq -u
\*\*Note\*\* : - uniq -u → chỉ in dòng xuất hiện đúng 1 lần
     - uniq -d → chỉ in các dòng xuất hiện nhiều hơn 1 lần (≥2)
     - uniq    -c → in kèm số lần xuất hiện của mỗi dòng

9->10 : FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey ---> strings data.txt | grep '='
\*\*Note\*\* : - strings đọc file nhị phân ra chuỗi

10->11 : dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr ---> base64 -d data.txt

11->12 : 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4 ---> tr 'A-Za-z' 'N-ZA-Mn-za-m' ---> 7k16JArUVv5LxVuJfsSVdbbtaHGlw9D4
\*\*Note\*\* : Câu lệnh mã hóa rot13 : tr 'A-Za-z' 'N-ZA-Mn-za-m'

12->13 : FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn ---> gunzip -r data.txt ---> mktemp -d ---> cd /tmp/tmp ---> ls ---> cat data8\\

13->14 : MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS ---> chmod 600 sshkey.private ---> ssh -i sshkey.private -p 2220 bandit14@localhost ---> cat /etc/bandit\_pass/bandit14
**Note** :  ssh: lệnh đăng nhập vào máy từ xa.
-i sshkey.private: chỉ định file private key để xác thực thay cho password.
-p 2220: chỉ định port 2220, vì Bandit không chạy SSH ở cổng mặc định (22) mà ở cổng này.
bandit14@localhost: nghĩa là login với user bandit14, và host localhost (máy hiện tại bạn đang đứng trên).

14->15 : 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo ---> echo "MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS" | nc localhost 30000

15->16 : kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx ---> openssl s\_client -connect localhost:30001 ---> 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo

16->17 : EReVavePLFHtFlFsjn3hyzMlvSuSAcRD ---> nmap -p 31000-32000 localhost ---> echo "<password\_bandit16>" | openssl s\_client -connect localhost:<port> -quiet ---> nano bandit17.key (# dán nguyên key vào đây, kể cả BEGIN/END) ---> chmod 600 bandit17.key   (# đổi quyền để ssh chấp nhận) ---> ssh -i bandit17.key bandit17@bandit.labs.overthewire.org -p 2220

17-> 18 : CgmS55GVlEKTgx8xpW8HuWnHlBKP924b

          x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO

18->19 : cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8 ---> ssh bandit18@bandit.labs.overthewire.org -p 2220 "cat readme"
ssh có thể chạy lệnh trực tiếp qua SSH, không mở shell, mà chạy lệnh rồi thoát.

19->20 : 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO ---> ./bandit20-do cat /etc/bandit\_pass/bandit20
Setuid bit chỉ đơn giản cho biết rằng khi chạy tệp thực thi, nó sẽ đặt quyền của mình cho người dùng đã tạo ra nó (chủ sở hữu), thay vì đặt cho người dùng đã khởi chạy nó.
Để xác định vị trí setuid hãy tìm 's' thay vì 'x' trong phần thực thi của quyền tệp.
vd : -rwsr-x--- 1 bandit20 bandit19 14884 Aug 15 13:16 bandit20-do
->Nếu là \*\*rwx\*\* → tức là file có quyền thực thi bình thường, khi bạn chạy nó thì nó chạy với quyền của user hiện tại (bandit19).
->Nếu là \*\*rws\*\* → tức là file có setuid bit. Khi chạy, nó sẽ chạy với quyền của owner(người sở hữu) (bandit20), chứ không phải của bạn.

20->21 : EeoULMCra2q0dSkYj561DX7s1CpBuOBt

21->22 : tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q

22->23 : 0Zf11ioIjMVN551jX3CmStKLYqjk54Ga
cd

23->24 : gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8

24->25 : iCi86ttT4KSNe1armKiwbQNmB3YJP3q4

25->26 : s0773xxkk0MXfdqOfPRVr9L3jJBUOgCZ

26->27 : upsNCc7vzaRDx6oZC6GiR6ERwe1MowGB

27->28 : Yz9IpL0sBcCeuG7m9uQFt8ZNpS4HZRcN

28->29 : 4pT1t5DENaYuqnqvadYs1oE4QLCdjmJ7

29->30 : qp30ex3VLz5MDG1n91YowTv4Q8l7CDZL

30->31 : fb5S2xb7bRyFmAvQYQGEqsbhVyJqhnDy

31->32 : 3O9RfhqyAlVBEZpVb6LYStshZoqoSx5K

32->33 : tQdtbs5D5i2vJwkO8mEyYEyTL8izoeJ0

LEVIATHAN :

0->1 : 3QJ3TgzHDq

1->2 : NsN1HwFoyN

2->3 : f0n8h2iWLP

3->4 : WG1egElCvO

4->5 : 0dyxT7F4QD

5->6 : szo7HDB88w

6->7 : qEs5Io5yM8

NATAS

0->1 : 0nzCigAq7t2iALyvU9xcHlYN4MlkIwlq

1->2 : TguMNxKo1DSa1tujBLuZJnDUlCcUAPlI

2->3 : 3gqisGdR0pjm6tpkDKdIWO2hSvchLeYH

3->4 : QryZXc2e0zahULdHrtHxzyYkj59kUxLQ

4->5 : 0n35PkggAPm2zbEpOU802c0x0Msn1ToK

5->6 : 0RoJwHdSKWFTYR5WuiAewauSuNaBXned

6->7 : bmg8SvU1LizuWjx3y7xkNERkHxGre0GS

7->8 : xcoXLmzMkoIP9D7hlgPlh9XD7OgLAe5Q

8->9 : ZE1ck82lmdGIoErlhQgWND6j2Wzz6b6t

9->10 : t7I5VHvpa14sJTUGV0cbEsbYfFP2dmOu

10->11 : UJdqkK1pTu6VLt9UHWAgRZz6sVUZ3lEk

11->12 :  yZdkjAYZRd3R7tq7T5kXMjMJlOIkzDeB

12->13 : trbs5pCjCrkuSknBBKHhaBxq6Wm1j3LC


KRYPTON 

0->1 : KRYPTONISGREAT

1->2 : ROTTEN

2->3 : CAESARISEASY
