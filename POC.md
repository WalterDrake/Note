# BÁO CÁO POC: 

### Về kỹ thuật tấn công: OAuth 2.0 authentication vulnerabilities
**Tiến hành:** 
> 1. Tạo ra một event bằng tài khoản trên máy của user_1.
> 2. Thêm những người muốn chia sẻ là user_2 và user_3. Việc thêm vào là để có thể tạo ra request sharing.
> 3. Gửi request sharing và capture. Chuyển tới request có id về user_1,2,3. Gửi tới repeater và drop request.
>4. Sử dụng token đã lấy từ user_1 sửa lại thông tin của user_4.

``
Lý do:
Trước khi drop request thứ 3 thì có 2 request được gửi đi. 2 request trước đó tạo ra token nên khi drop nếu còn trong thời gian thì token cho user_1 vẫn còn hiệu lực. Việc chỉnh sửa được nội dung do token chỉ có duy trì tạo ra phiên kết nối giữa client và server không can thiệt vào bên trong request. Server dựa vào id được tạo ra để tạo event và gửi lời mời. Nếu id hợp lệ và token còn hiệu lực thì sẽ thay đổi được.
``

