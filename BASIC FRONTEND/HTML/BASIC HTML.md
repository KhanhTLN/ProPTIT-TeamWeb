# Buổi 1: Cơ bản về WEB - HTML

## Cơ bản về web:
1. **Cách thức hoạt động của 1 trang web:**
- **Quy trình đơn giản khi truy cập một trang web:**
    + Nhập địa chỉ website(URL) vào trình duyệt, ví dụ "http://www.example.com"
    + Trình duyệt gửi yêu cầu(request) đến hệ thống tên miền DNS(Domain Name System) để tìm địa chỉ IP của tên miền đó
    + Sau khi có IP, trình duyệt gửi yêu cầu đến máy chủ(server) chứa trang web
    + Máy chủ xử lý yêu cầu, lấy dữ liệu(HTML,CSS,..) và gửi phản hồi(response) lại cho trình duyệt
    + Trình duyệt nhận nội dung và hiện thị ra giao diện
- **Các thuật ngữ cơ bản:**
    +** Internet connection**: cho phép ta có thể **gửi và nhận dữ liệu qua lại trên web**. Vê cơ bản nó như đường ống nối từ client tới server để vận chuyển "hàng hóa" qua lại.
    + **TCP/IP (Transmission Control Protocol và Internet Protocol)**: **Giao thức điều khiển truyền dẫn và giao thức kết nối internet**. Chúng là những giao thức có thể quyết định được cách mà data của bạn được truyền tải dọc đường truyền internet. Điều này giống như cơ chế vận chuyển cho phép ta đặt hàng, đến cửa hàng và mua hàng. 
    + **DNS (Domain Name System)**: **Hệ thống tên miền**, nó giống như một cuốn sổ địa chỉ các websites. Khi gõ một địa chỉ website lên thanh trình duyệt, trình duyệt sẽ tìm trong DNS để tìm được địa chỉ IP của website trước, sau kh tìm được sẽ bắt đầu truy suất trang web đó. Trình duyệt sẽ cần phải tìm ra địa chỉ của máy server đang chứa trang web đó để nó có thể gửi HTTP message tới đúng nơi. Cơ bản giống như việc ta phải tìm được đúng địa chỉ cửa hàng mà ta muốn mua sắm.
    + **HTTP (Hypertext Transfer Protocol)**: **Giao thức truyền siêu văn bản**, nó là một giao thức ứng dụng nhằm quy định ra một ngôn ngữ chung giữa client và server để chúng có thể dùng và giao tiếp với nhau. Tường tượng nó giống như một ngôn ngữ ta dùng để có thể đặt được những món hàng mong muốn ở cửa hàng
    + **Component files: Một website được tạo thành từ rất nhiều file khác nhau**, những file này được chia thành 2 loại chính:
        * **Code files**: Các trang web chủ yếu được xây dựng từ HTML, CSS và JavaScript, sau này có thể còn có nhiều công nghệ khác
        * **Assets**: Đây là tên chung cho tất cả nội dung tạo nên trang web, chẳng hạn như hình ảnh, âm nhạc, video, tài liệu,...


## HTML:

1. Giới thiệu, cấu trúc HTML:
- Khái niệm: HTML(HyperText Markup Language) là ngôn ngữ đánh dấu dùng để tạo ra cấu trúc nội dung trên trang web
- HTML không phải là ngôn ngữ lập trình mà là ngôn ngữ mô tả(markup)
- XHTML (Extensible HyperText Markup Language):
    + gần giống với HTML
    + có quy định nghiêm khắc hơn HTML
    + được định nghĩa như một ứng dụng XML
    + được hỗ trợ bởi hầu hết các trình duyệt phổ biến
=> Tại sao lại dùng XHTML: nhiều trang trên internet chứa HTML rất tệ, dù không tuân theo quy định của HTML nhưng vẫn chạy được trên nhiều trình duyệt. 

2. Cấu trúc tài liệu HTML:
```HTML
<!DOCTYPE html>
<html lang="vi">
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tiêu đề trang</title>
    <link rel="icon" href="favicon.ico">
  </head>
  <body>
    <h1>Chào mừng đến với trang web!</h1>
    <p>Đây là nội dung chính của trang.</p>
  </body>
</html>
```

- Các thành phần:
    + `<!DOCTYPE html>` : khai báo đây là tài liệu HTML5  
    + `<html lang="vi">` : phần gốc bao toàn bộ tài liệu  
    + `<head>` : chứa thông tin cấu hình trang, không hiển thị trực tiếp  
    + `<meta charset="UTF-8">` : mã hóa ký tự, dùng để hiển thị tiếng Việt chính xác  
    + `<meta name="viewport">` : thiết lập responsive cho thiết bị di động  
    + `<title>` : Tiêu đề trang  
    + `<link rel="icon">` : gắn favicon (biểu tượng nhỏ trên tab)  
    + `<body>` : chứa toàn bộ nội dung hiển thị ra trang web

=> Tóm tắt cấu trúc tài liệu HTML:
```html
<!DOCTYPE html>      --> Khai báo HTML5
<html>               --> Bao toàn bộ tài liệu
  <head>             --> Cấu hình, meta, title, link
  </head>
  <body>             --> Nội dung hiển thị (giao diện)
  </body>
</html>
```

3. Khái niệm: Element, Attribute, Comment:
- **Element**: là đơn vị cơ bản trong HTML, gồm thẻ mở, nội dung và thẻ đóng
```html
<p> Đây là một đoạn văn </p>
```
-> Một số thẻ **tự đóng**, không có thẻ đóng đi kèm:
```html
<br>  <!-- Xuống dòng -->
<hr>  <!-- Gạch ngang -->
<img src="..." alt="..."> <!-- Hình ảnh -->
```

- **Attribute** : nằm trong thẻ mở, cung cấp thông tin bổ sung cho Element
```html
<img src="avatar.png" alt="Ảnh đại diện" width="200">
<a href="https://example.com" target="_blank">Trang web</a>

```
-> Ví dụ các thuộc tính thường gặp: src, alt, href, class, id, type, required, ...

- **Comment** : dùng để ghi chú, không hiển thị trên trình duyệt
```html
<!-- Đây là một chú thích trong html -->
```

4. Các thẻ HTML cơ bản:
- Các thẻ văn bản:
<table border="1">
    <thead>
        <tr>
            <th>Thẻ</th>
            <th>Chức năng</th>
            <th>Ví dụ</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>&lt;h1&gt; đến &lt;h6&gt;</td>
            <td>Tiêu đề, từ lớn nhất (h1) đến nhỏ nhất (h6)</td>
            <td>&lt;h1&gt; Trang chính &lt;/h1&gt;</td>
        </tr>
        <tr>
            <td>&lt;p&gt;</td>
            <td>Đoạn văn bản</td>
            <td>&lt;p&gt;Đây là một đoạn văn&lt;/p&gt;</td>
        </tr>
        <tr>
            <td>&lt;br&gt;</td>
            <td>Xuống dòng</td>
            <td>Dòng 1&lt;br&gt;Dòng 2</td>
        </tr>
        <tr>
            <td> &lt;gt&gt;</td>
            <td>Kẻ ngang phân cách nội dung</td>
            <td>&lt;hr&gt;</td>
        </tr>
        <tr>
            <td> &lt;strong&gt;</td>
            <td>In đậm, có ý nghĩa nhấn mạnh</td>
            <td>&lt;strong&gt;Quan trọng!&lt;/strong&gt;</td>
        </tr>
        <tr>
            <td> &lt;em&gt;</td>
            <td>In nghiêng</td>
            <td>&lt;em&gt;Ghi chú&lt;/em&gt;</td>
        </tr>
    </tbody>
</table>

- **Thẻ liên kết và media:**
    + `<a>`: Thẻ liên kết
    ```html
    <a href="https://www.facebook.com/clubproptit?locale=vi_VN" target="_blank">Trang ví dụ</a>
    ```
    -> **href**: đường dẫn đến nơi cần liên kết
    -> **target="_blank"**: mở trong tab mới

    + `<img>`: Hình ảnh
    ```html
    <img src="khanh.png" alt="Ảnh đại diện" width="200">
    ```
    -> **src** : đường dẫn ảnh
    -> **alt** : mô tả ảnh(hiện khi ảnh lỗi)

    + `<video>` : Video
    ```html
    <video src = "video.mp4" controls width="400"></video>
    ```
    -> **controls** : hiển thị thanh điều khiển
    -> có thể thêm autoplay, loop, muted,...

    + `<audio>` : âm thanh
    ```html
    <audio src="audio.mp3"></audio>
    ```

    + `<iframe>` : Nhúng nội dung bên ngoài(web, video, bản đồ,...)
    ```html
    <iframe src="https://www.youtube.com/embed/abcxyz" width="560" height="315"></iframe>
    ```

- **List(Danh sách):**
    + **"ul" - unordered list** : Danh sách không thứ tự
    + **"ol" - ordered list** : Danh sách có thứ tự
    + **"li" - list item** : Mỗi mục

**Ví dụ:**
```html
<p>- Danh sách không thứ tự</p>
<ul>
  <li>Táo</li>
  <li>Cam</li>
</ul>

<p>- Danh sách có thứ tự</p>
<ol>
  <li>Bước 1</li>
  <li>Bước 2</li>
</ol>

```

**Kết quả:**
<p>- Danh sách không thứ tự</p>
<ul>
  <li>Táo</li>
  <li>Cam</li>
</ul>

<p>- Danh sách có thứ tự</p>
<ol>
  <li>Bước 1</li>
  <li>Bước 2</li>
</ol>

- **Table:**
<table>
    <thead>
        <tr>
            <th>Thẻ</th>
            <th>Mô tả</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>&lt;table&gt;</td>
            <td>Bắt đầu bảng</td>
        </tr>
        <tr>
            <td>&lt;tr&gt;</td>
            <td>Hàng</td>
        </tr>
        <tr>
            <td>&lt;td&gt;</td>
            <td>Ô dữ liệu</td>
        </tr>
        <tr>
            <td>&lt;th&gt;</td>
            <td>Ô tiêu đề</td>
        </tr>
        <tr>
            <td>&lt;thead&gt;, &lt;tbody&gt;</td>
            <td>Phân nhóm phần đầu và thân bảng</td>
        </tr>
    </tbody>
</table>

**Ví dụ:**
```html
<table border="1">
  <thead>
    <tr><th>Tên</th><th>Tuổi</th></tr>
  </thead>
  <tbody>
    <tr><td>Lan</td><td>20</td></tr>
    <tr><td>Hùng</td><td>22</td></tr>
  </tbody>
</table>
```
**Kết quả:**
<table>
    <thead>
        <tr>
            <th>Tên</th>
            <th>Tuổi</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Khánh</td>
            <td>20</td>
        </tr>
        <tr>
            <td>Kkk</td>
            <td>20</td>
        </tr>
    </tbody>
</table>


- **Form:**
    + Các thẻ form thường dùng:
    <table>
    <thead>
        <tr>
            <th>Thẻ</th>
            <th>Mục đích</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>&lt;input&gt;</td>
            <td>Nhập dữ liệu</td>
        </tr>
        <tr>
            <td>&lt;label&gt;</td>
            <td>Nhãn cho input</td>
        </tr>
        <tr>
            <td>&lt;textarea&gt;</td>
            <td>Ô nhập văn bản nhiều dòng</td>
        </tr>
        <tr>
            <td>&lt;select&gt;, &lt;option&gt;</td>
            <td>Danh sạch chọn</td>
        </tr>
        </tbody>
    </table>

**Ví dụ:**
```html
<form action="/submit" method="post">
  <label for="name">Họ tên:</label><br>
  <input type="text" id="name" name="name" required><br><br>

  <label>Giới tính:</label><br>
  
  <input type="radio" id="male" name="gender" value="Nam">
  <label for="male">Nam</label><br>

  <input type="radio" id="female" name="gender" value="Nữ">
  <label for="female">Nữ</label><br><br>

  <label for="email">Email:</label><br>
  <input type="email" id="email" name="email" required><br><br>

  <label for="message">Tin nhắn:</label><br>
  <textarea id="message" name="message" rows="4" cols="30"></textarea><br><br>

  <input type="submit" value="Gửi">
</form>
```
**Kết quả form mẫu:**
<form action="/submit" method="post">
  <label for="name">Họ tên:</label><br>
  <input type="text" id="name" name="name" required><br><br>

  <label>Giới tính:</label><br>
  
  <input type="radio" id="male" name="gender" value="Nam">
  <label for="male">Nam</label><br>

  <input type="radio" id="female" name="gender" value="Nữ">
  <label for="female">Nữ</label><br><br>

  <label for="email">Email:</label><br>
  <input type="email" id="email" name="email" required><br><br>

  <label for="message">Tin nhắn:</label><br>
  <textarea id="message" name="message" rows="4" cols="30"></textarea><br><br>

  <input type="submit" value="Gửi">
</form>


- **Thẻ `<script>` và HTML JS:**
```html
<script>
    alert("Chào mừng bạn đến với website!");
</script>
```
-> Dùng để nhúng mã JS, ví dụ tương tác như: Cảnh báo(Alert), thay đổi nội dung HTML, gửi dữ liệu, xử lý logic

