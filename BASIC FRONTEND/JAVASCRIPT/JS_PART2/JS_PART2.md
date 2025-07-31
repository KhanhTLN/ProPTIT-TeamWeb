# Buổi 5: JS - 2

- [Buổi 5: JS - 2](#buổi-5-js---2)
  - [Phần 4: JS Async, API](#phần-4-js-async-api)
    - [1. JS Async:](#1-js-async)
      - [1.1. JSON (JavaScript Object Notation):](#11-json-javascript-object-notation)
      - [1.2. JS Async:](#12-js-async)
        - [1.2.1. Asynchronous trong JS (bất đồng bộ):](#121-asynchronous-trong-js-bất-đồng-bộ)
        - [1.2.2. Callback:](#122-callback)
        - [1.2.3. Callback Hell:](#123-callback-hell)
        - [1.2.4. Promise](#124-promise)
        - [1.2.5. Async/Await](#125-asyncawait)
        - [1.2.6. So sánh](#126-so-sánh)
    - [2. Fetch API](#2-fetch-api)
    - [3. REST API](#3-rest-api)
    - [4. Postman](#4-postman)
  - [Phần 5: Storage](#phần-5-storage)
    - [1. Storing data:](#1-storing-data)
      - [1.1. Cookie](#11-cookie)
      - [1.2. localStorage](#12-localstorage)
      - [1.3. sessionStorage](#13-sessionstorage)
    - [2. Token (Access Token, Refresh Token)](#2-token-access-token-refresh-token)
      - [2.1. Token là gì?](#21-token-là-gì)
      - [2.2. Access token:](#22-access-token)
      - [2.3. Refresh token](#23-refresh-token)


## Phần 4: JS Async, API

### 1. JS Async:
#### 1.1. JSON (JavaScript Object Notation):
- **JSON** là định dạng dữ liệu phor biến để trao đổi giữa client và server
- **Cấu trúc:**
    + là một **object/array**
    + **Key:** luôn là chuỗi (trong `""`)
    + **Value:** string, number, array, boolean, null
- Ví dụ:

```json
{
    "name" : "Khanh", 
    "age": 20,
    "skill": ["HTML", "CSS", "JS"]
}
```

- Tạo JSON trong JS:

```js
const jsonStr = `{"name": "Khanh", "age": 20}`;
// Chuyển từ JSON -> Object
const obj = JSON.parse(jsonStr);

// Chuyển từ Object -> JSON
const newStr = JSON.stringify(obj);
```

#### 1.2. JS Async:

##### 1.2.1. Asynchronous trong JS (bất đồng bộ):

- Trong khi làm việc với web, nếu chúng ta muốn lấy dữ liệu để có thể hiển thị cho người dùng thì chúng ta sẽ phải việc với API. Các API luôn luôn có một độ trễ trong thời gian xử lý yêu cầu, sau đó nó sẽ trả về kết quả chúng ta cần hoặc trong trường hợp xấu có thể nó sẽ không trả về kết quả gì. Trong những trường hợp cần chờ hệ thống xử lý như thế này, nếu chúng ta cố gắng đợi cho việc xử lý hoàn thành nó có thể khiến trang web không phản hồi lại cho người dùng. Đây sẽ là trải nghiệm không tốt đối với người dùng.

- Đây là lúc các khái niệm **"Asynchronous"** được đề cập đến, nó cho phép các tác vụ được thực hiện mà không cần phải chờ đợi các tác vụ trước đó hoàn thành. Việc các tác vụ được xử lý mà không cần phải chờ các tác vụ khác cho phép ứng dụng cs thể tiếp tục hoạt động mà không cần chờ đợi các tác vụ xử lý xong. Điều này sẽ càng được thể hiện rõ ràng hơn trong các tác vụ mất nhiều thời gian xử lý hay giao tiếp với cơ sở dữ liệu.


##### 1.2.2. Callback:

- là một hàm được truyền vào hàm khác như một đối số, và được gọi sau khi nhiệm vụ hoàn tất.
- Dễ hiểu như: "Làm xong bước A thì chạy tiếp bước B" -> B chính là `callback`
- Ví dụ:

```js
function greeting(name, callback){
    console.log("Xin chao " + name);
    callback();
}

function done(){
    console.log("Ket thuc loi chao.");
}

greeting("Khanh", done);
```

- Dùng khi:
    + Xử lý sự kiện (event handler)
    + Tác vụ bất đồng bộ như đọc file, gọi API, timeout,...

##### 1.2.3. Callback Hell:

- Là hiện tượng khi dùng nhiều `callback` lồng nhau, dẫn đến mã nguồn rối rắm, khó đọc, khó bảo trì.
- Ví dụ:
```js
getUser(userId, (user) => {
  getPosts(user.id, (posts) => {
    getComments(posts[0].id, (comments) => {
      console.log(comments);
    });
  });
});
```
- Vấn đề:
    + Khó quản lý
    + Khó đọc hiểu logic
    + Gây "tháp callback" lồng nhau

##### 1.2.4. Promise
- Là một **object** đại diện cho một kết quả chưa có ngay lập tức, nhưng sẽ có sau này.
- Ưu điểm:
    + Viết code dễ đọc hơn
    + Có `.then()` và `.catch()` để xử lý kết quả và lỗi
- Ví dụ:
```js
const fetchData = () => {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve("Dữ liệu đã tải xong");
        }, 2000);
    });
};

fetchData()
    .then(data => console.log(data)) //Xử lý kết quả
    .catch(err => console.log(err));  //Xử lý lỗi
```

- Trạng thái Promise:

|Trạng thái|Ý nghĩa|
|---|---|
|`pending`|Đang xử lý|
|`fullfilled`|Thành công|
|`rejected`|Thất bại|

##### 1.2.5. Async/Await
- Khái niệm: là cú pháp giúp viết code bất đồng bộ như đồng bộ, dễ hiểu hơn Promise `.then()`
    + `async:` biến hàm thường thành bất đồng bộ -> trả về **promise**
    + `await:` đợi **promise** hoàn tất trước khi chạy tiếp
- Ví dụ:
```js
const fetchData = () => {
    return new Promise((resolve) => {
        setTimeout(() => {
            resolve("Dữ liệu OK!");
        }, 2000);
    });
};

async function getData() {
    try{
        const data = await fetchData();
        console.log(data);
    } catch (error) {
        console.error("Có lỗi", error);
    }
}

getData();
```

- Ưu điểm:
    + Gọn gàng, dễ đọc
    + Viết giống như code đồng bộ
    + Xử lý lỗi dễ bằng `try...catch`


##### 1.2.6. So sánh
- 1 Ví dụ thực tế: Khánh phải làm 3 công việc tuần tự và mỗi việc mất 1 giây:
    + Đánh răng
    + Ăn sáng
    + Đi học
-> Mô phỏng các bước này bằng `setTimeout` để tạo độ trễ 1s.

1. **Callback đơn giản**

```js
function brushTeeth(callback) {
    setTimeout(() => {
        console.log("1.Finished brushing teeth");
        callback();
    }, 1000);
}

function eatBreakfast(callback) {
    setTimeout(() => {
        console.log("2.Finished eating breakfast");
        callback();
    }, 1000);
}

function goToSchool(callback) {
    setTimeout(() => {
        console.log("3.Finished going to school");
        callback();
    }, 1000);
}

brushTeet(() => {
    eatBreakfast(() => {
        goToSchool(() => {
            console.log("Finishing everything");
        });
    });
});
```
-> Callback hell vì có nhiều hàm lồng nhau

2. **Promise**

```js
function brushTeeth(){
    return new Promise(resolve => {
        setTimeout(() => {
            console.log("1. Finished brushing teeth");
            resolve();
        }, 1000);
    });
}

function eatBreakfast(){
    return new Promise(resolve => {
        setTimeout(() => {
            console.log("2. Finished eating breakfast");
            resolve();
        }, 1000);
    });
}

function goToSchool(){
    return new Promise(resolve => {
        setTimeout(() => {
            console.log("3. Finished going to school");
            resolve();
        }, 1000);
    });
}

// Gọi lần lượt bằng Promise
brushTeeth()
    .then(() => eatBreakfast())
    .then(() => goToSchool())
    .then(() => console.log("Finished everything"));
```

3. **Async**

```js
function brushTeeth(){
    return new Promise(resolve => {
        setTimeout(() => {
            console.log("1. Finished brushing teeth");
            resolve();
        }, 1000);
    });
}

function eatBreakfast(){
    return new Promise(resolve => {
        setTimeout(() => {
            console.log("2. Finished eating breakfast");
            resolve();
        }, 1000);
    });
}

function goToSchool(){
    return new Promise(resolve => {
        setTimeout(() => {
            console.log("3. Finished going to school");
            resolve();
        }, 1000);
    });
}

async function startDay(){
    await brushTeeth();
    await eatBreakfast();
    await goToSchool();
    console.log("Finished everything");
}

startDay();
```

### 2. Fetch API

- Để hiểu về fetch cần biết những thứ sau: API, JSON, Promise
- API là viết tắt của Application Programming Interface. Là bộ phận quan trọng giúp chúng ta kết nối 2 hệ thống khác nhau lại với nhau. Để đơn gian hóa, ta có ví dụ: Mình có 1 người bạn là John đến từ Anh và mình muốn giao tiếp với John mình sẽ sử dụng ngôn ngữ chính là tiếng ANh, thì lúc này tiếng Anh là phương thức giúp mình và John có thể trò chuyện. Thì API cũng thế, nó giúp phía Front-End hay người dùng có thể giao tiếp với Database và những thứ từ phía Back-End. Thông thường API sẽ có dạng là 1 URL trỏ về phía Back-End. Nên có thể hiểu đơn giản API là 1 url
- JSON là 1 định dạng dữ liệu chuỗi giúp thể hiện number, boolean, NULL, object. Có thể biến những dữ liệu đó thành JSON và ngược lại
- **fetch()** là 1 web API có nhiệm vụ gọi 1 API từ phía BE cung cấp giúp chúng ta lấy ra những thông tin cần thiết để hiển thị ra giao diện
- Quy trình làm việc của **fetch()**:
    + BE cung cấp API đẻ kết nối FE với DB
    + FE sử dụng **fetch** để lấy dữ liệu ở dạng XML hoặc JSON
    + FE sử dụng dữ liệu dạng XML hoặc JSON để biến đổi thành cách kiểu dữ liệu trong JS
    + Sử dụng kiểu dữ liệu được biến đổi và làm việc với chúng
- Cú pháp của **fetch()**:

```js
fetch(url, int);
```

    + **url**: là API mà BE cung cấp
    + **int**: là tham số không bắt buộc
- **fetch()** được thiết lập bằng **Promise** nên nó cũng sẽ trả về resolve() và reject(), nên muốn bắt được chúng thì ta chỉ cần .then() và .catch() ở phía sau là được

```js
fetch(API)
    .then()
    .catch()
```

- **Query**: là phần nằm sau dấu `?` trong URL, dùng để lọc/tìm kiếm/ phân trang...

```
https://example.com/api/products?category=shoes&page=2
```
    + `category=shoes` -> lọc theo danh mục giày
    + `page=2` -> trang thứ 2
-> Query luôn được viết trong URL với phương thức `GET`

- **Params (URL parameters)**: là phần biến đổi trong đường dẫn URL - thường dùng để xác định tài nguyên cụ thế

```html
GET https://example.com/api/users/123

```

    + "123" là userId
    + Nghĩa là lấy thông tin người dùng có ID="123"

- **Body (Request Body)**: Body là phần dữ liệu gửi kèm khi gọi API kiểu `POST`, `PUT`, `PATCH`,...
-> Dùng khi cần gửi dữ liệu từ client lên server(ví dụ: đăng ký, đăng nhập, gửi form,...)

```js
POST /api/login
Body:
{
    "username": "khanh",
    "password": "123456"
}
```
-> **Body** thường lấy ở dạng JSON, chỉ các phương thức `POST`, `PUT`, `PATCH` mới có body (GET không có)

### 3. REST API
- **REST API** là một kiểu thiết kế API (chứ không phải công nghệ), dùng để giao tiếp giữa client và server theo nguyên tắc chuẩn **REST Representational State Transfer**
- Tưởng tượng:
    + Mình là người dùng(client)
    + Mình gửi request tới nhà hàng(server)
    + Nhân viên mang món ăn(response) cho mình
-> **REST API** chính là menu đặt món - ta chọn món(endpoint)

- **Các đặc điểm chính của REST API:**
    + **Stateless**: mỗi request là độc lập, server không nhớ ta làm gì trước đó
    + **Sử dụng HTTP method**: dùng `GET`, `POST`, `PUT`, `DELETE` để thực hiện hành động
    + **Dữ liệu dạng JSON**:  gửi và nhận dữ liệu dưới dạng JSON
    + **Resource-based**: mỗi URL đại diện cho một tài nguyên như người dùng, bài viết, sản phẩm
- Ví dụ: Tài nguyên: `users`

|Mục đích|Method|URL|Ý nghĩa|
|---|---|---|---|
|Lấy danh sách user|GET|/api/users|lấy tất cả người dùng|
|Lấy 1 user cụ thể|GET|/api/users/1|Lấy user có ID = 1|
|Tạo user mới|POST|/api/users|gửi dữ liệu user mới trong Body|
|Cập nhật user|PUT|/api/users/1|Cập nhật userID = 1|
|Xóa user|DELETE|/api/users/1|Xóa users ID = 1|


### 4. Postman

- Postman hiện là một trong những công cụ phổ biến nhất được sử dụng trong kiểm thử API. Nó bắt đầu vào năm 2012 như một dự án phụ của Abhinav Asthana để đơn giản hóa quy trình làm việc API trong kiểm thử và phát triển. API là viết tắt của giao diện lập trình ứng dụng cho phép các ứng dụng phần mềm giao tiếp với nhau thông qua các lệnh gọi API.
- Postman là một phần mềm dùng để:
    + Gửi request tới REST API
    + Kiểm tra phản hồi (response)
    + Giả lập các hành động như GET, POST, PUT, DELETE,..
    + Test API mà không cần viết code

-> Tưởng tượng như sau: có 1 địa chỉ API :
```http
https://example.com/api/users/1
```
- Thay vì viết code JS để gửi request, thì ta chỉ cần:
    + Mở Postman
    + Dán url
    + Chọn phương thức (GET, POST,...)
    + Gửi request -> xem kết quả JSON trả về

- Các thao tác cơ bản trong Postman:
    + Gửi một request GET
        * Mở postman
        * Chọn GET
        * Nhập URL
        * Bấm nút Send
        * Kết quả hiện ra ở tab Body (JSON)

## Phần 5: Storage

### 1. Storing data:

#### 1.1. Cookie
- là các **cặp key-value** nhỏ được trình duyệt lưu trữ và gửi kèm theo mỗi request HTTP đến server
- Thường dùng để:
    + Xác thực đăng nhập
    + Ghi nhớ cài đặt người dùng
- Cách dùng
```js
document.cookie = "username=khanh; expires=Fri, 31 Dec 2025 23:59:59 GMT";
```
- Dung lượng: Tối đa 4KB mỗi cookie
- Thời gian sống: Do bạn quy định qua `expires` hoặc `max-age`
- Gửi đến server: Tự động gửi kèm trong mỗi HTTP request
- Nhược điểm:
    + Dung lượng rất nhỏ
    + Gửi đi mỗi lần => tốn băng thông
    + Dễ bị đánh cắp nếu không bảo mật tốt

#### 1.2. localStorage
- Dùng để lưu trữ dữ liệu lâu dài trên trình duyệt
- Dữ liệu chỉ lưu ở phía client, không tự động gửi đến server
- Cách dùng:

```js
localStorage.setItem("username", "khanh");
let name = localStorage.getItem("username");
localStorage.removeItem("username");
localStorage.clear();
```
- Dung lượng: Khoảng 5MB-10MB, tùy trình duyệt
- Thời gian sống: Không bị xóa khi đóng tab/ trình duyệt
- Ưu điểm:
    + Lưu được dữ liệu lớn hơn
    + Không gửi kèm trong request
- Nhược điểm:
    + Không bảo mật: Dữ liệu hiển thị rõ nếu inspect
    + Dễ bị truy cập bởi JS độc


#### 1.3. sessionStorage
- gần giống `localStorage`, nhưng chỉ lưu trong phiên làm việc (session)
- Cách dùng

```js
sessionStorage.setItem("username", "khanh");
let name = sessionStorage.getItem("username");
```
- Thời gian sống: Tồn tại đến khi đóng tab hoặc trình duyệt
- Dung lượng: khoảng 5MB, như `localStorage`
- Không gửi đến server

### 2. Token (Access Token, Refresh Token)

#### 2.1. Token là gì?
- Token là một đoạn mã (chuỗi ký tự) mà server tạo ra và gửi cho client sau khi đăng nhập thành công.
Client sẽ dùng token đó để chứng minh mình đã xác thực trong các lần request tiếp theo.


#### 2.2. Access token:
- Là loại token được cấp khi đăng nhập thành công
- Mang theo thông tin người dùng (ví dụ: userId, role,...)
- Dùng để gửi kèm theo mỗi request đến server nhằm xác minh danh tính.
- Thời gian sống: Ngắn hạn, ví dụ: 15 phút, 1 giờ… để giảm rủi ro bị đánh cắp.
- Gửi như thế nào: Gửi trong HTTP header (thường dùng Authorization):

#### 2.3. Refresh token
- Là token dài hạn, dùng để xin Access Token mới khi access token hết hạn.
- Không dùng để truy cập API trực tiếp.
- Giúp user không phải đăng nhập lại sau khi access token hết hạn.