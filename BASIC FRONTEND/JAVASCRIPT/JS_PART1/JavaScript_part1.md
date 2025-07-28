# JavaScript: Buổi 1

- [JavaScript: Buổi 1](#javascript-buổi-1)
  - [Phần 1: Syntax cơ bản JS](#phần-1-syntax-cơ-bản-js)
    - [1. Khai báo dữ liệu: Biến, toán tử](#1-khai-báo-dữ-liệu-biến-toán-tử)
      - [1.1. Biến](#11-biến)
      - [1.2. Toán tử](#12-toán-tử)
        - [1.2.1. Toán tử gán](#121-toán-tử-gán)
        - [1.2.2. Các toán tử số học](#122-các-toán-tử-số-học)
        - [1.2.3. Toán tử so sánh](#123-toán-tử-so-sánh)
        - [1.2.4. Toán tử logic](#124-toán-tử-logic)
        - [1.2.5. Toán tử ba ngôi](#125-toán-tử-ba-ngôi)
    - [2. Đối tượng: Array, Object, String](#2-đối-tượng-array-object-string)
      - [2.1. Array](#21-array)
      - [2.2. Object](#22-object)
      - [2.3. String](#23-string)
    - [3. Vòng lặp](#3-vòng-lặp)
      - [3.1. for](#31-for)
      - [3.2. while và do...while](#32-while-và-dowhile)
      - [3.3. for..of (chỉ dành cho iterable)](#33-forof-chỉ-dành-cho-iterable)
      - [3.4. for...in (lặp qua key)](#34-forin-lặp-qua-key)
      - [3.5. forEach() - (cho mảng)](#35-foreach---cho-mảng)
    - [4. Function(hàm)](#4-functionhàm)
    - [5. Array method: Map, Reduce, Filter, Includes, Group, Some, Every](#5-array-method-map-reduce-filter-includes-group-some-every)
      - [5.1. map(): chuyển đổi từng phần tử trong mảng](#51-map-chuyển-đổi-từng-phần-tử-trong-mảng)
      - [5.2. filter(): lọc phần tử theo điều kiện](#52-filter-lọc-phần-tử-theo-điều-kiện)
      - [5.3. reduce(): tính gộp lại 1 giá trị duy nhất](#53-reduce-tính-gộp-lại-1-giá-trị-duy-nhất)
      - [5.4. includes(): kiểm tra có tồn tại không](#54-includes-kiểm-tra-có-tồn-tại-không)
      - [5.5. some(): ít nhất 1 phẩn tử thỏa mãn điều kiện](#55-some-ít-nhất-1-phẩn-tử-thỏa-mãn-điều-kiện)
      - [5.6. every(): tất cả phần tử đều đúng](#56-every-tất-cả-phần-tử-đều-đúng)
      - [5.7. group(): gom nhóm object theo key (JS6 chưa hỗ trợ dùng phương thức group)](#57-group-gom-nhóm-object-theo-key-js6-chưa-hỗ-trợ-dùng-phương-thức-group)
    - [6. callback](#6-callback)
  - [Phần 2: JS6](#phần-2-js6)
    - [1. `let` và `const` (thay thế var)](#1-let-và-const-thay-thế-var)
    - [2.Arrow Function:](#2arrow-function)
    - [3. Template Literals (Chuỗi nội suy)](#3-template-literals-chuỗi-nội-suy)
    - [4. Destructing (Phân rã):](#4-destructing-phân-rã)
    - [5. Spread(...) (Toán tử trải rộng)](#5-spread-toán-tử-trải-rộng)
    - [6. Module (Import/Export):](#6-module-importexport)
  - [Phần 3: DOM và Event](#phần-3-dom-và-event)
    - [1. DOM là gì?](#1-dom-là-gì)
    - [2. DOM Events:](#2-dom-events)


## Phần 1: Syntax cơ bản JS

### 1. Khai báo dữ liệu: Biến, toán tử

#### 1.1. Biến
- Giống như nhiều ngôn ngữ khác, JavaScript có các biến. Các biến JS được lưu trữ trong bộ nhớ của browser process( tiến trình trình duyệt) hiểu nôm na 1 cách đơn giản là biến được lưu trong phần Ram mà trình duyệt đang sử dụng.
- **Khai báo biến**: để khai báo biến ta sử dụng từ khóa `const, let, var`.
    + `const`: được sử dụng để khai báo 1 **hằng số** và giá trị của nó không thay đổi trong suốt chương trình
    + `let`: khai báo biến có thể truy cập được trong **block** bao quanh nó được xác định bằng cặp '{}'.
    + `var`: khao báo biên có thể truy cập ở phạm vi **hàm số hoặc bên ngoài hàm số, toàn cục**.
- **Quy tắc đặt tên biến:**
    + Tên biến phải là các chữ không dấu viết hoa hoặc viết thường, các chữ số từ 0-9 và dấu gạch dưới () và kí hiệu $.
    + Tên biến bắt đầu phải là chữ hoặc dấu gạch dưới (_), nếu bắt đầu bằng số là sai.
    + Không thể sử dụng các từ dành riêng (như từ khóa JavaScript) làm tên.
    + Các tên có phân biệt chữ hoa chữ thường

- **Kiểu dữ liệu của biến:** Khi khai báo biến ta không cần phải khai báo kiểu của biến đó trước khi dùng. Kiểu sẽ được tự động xác định trong lúc chương trình được thực thi. Điều đó cũng có nghĩa là một biến có thể chứa giá trị của các kiểu dữ liệu khác nhau

```js
var test = 123 ; // test là một số

var test = "variable of js "; //test là một chuỗi

var test = true;  // test là một boolean
```
- Theo chuẩn ECMAScript xác định 7 kiểu dữ liệu như sau:
    + boolean
    + null
    + undefined
    + số
    + chuỗi
    + symbol
    + đối tượng

#### 1.2. Toán tử
##### 1.2.1. Toán tử gán

|Toán tử|Ví dụ|Ý nghĩa|
|---|---|---|
|=|x=y|gán giá trị y vào x|
|+=|x+=y|x = x + y; cộng thêm giá trị y vào x|
|-=|x-=y|x = x - y|
|*=|x*=y|x = x * y|
|/=|x/=y|x = x / y|
|%=|x%=y|x = x % y|
|??=|x??=y|Toán tử `??=` trong js là phép gán khi null. Nếu x bằng null thì giá trị y gán cho x, nếu x đã khác null thì không thay đổi gì 
```js
let name = "Khanh";
let address = null;
const name_default = "No name";
const add_default = "No address";

name ??= name_default;
console.log(name); //Khanh
addresss ??= add_default;
console.log(address); // "No address"
``` 
|

##### 1.2.2. Các toán tử số học
- `+`,`-`,`*`,`/`,`%`, `++`, `--`

```js
var x = 10 + 5;
document.write(x);
```

##### 1.2.3. Toán tử so sánh
- `==`: so sánh bằng(và giá trị, không so sánh về kiểu dữ liệu)
```js
var v1 = (5 == 10); // false
var v2 = 5;         // số
var v3 = "5";      // chuỗi
var v4 = (v2 == v3);// true
```

- `===`: so sánh giống nhau(cả về giá trị và kiểu dữ liệu)
```js
var v1 = (5 === 10);  // false
var v2 = 5;           // kiểu số number
var v3 = "5 ";        // chuỗi string
var v4 = (v2 === v3); // false, giống giá trị nhưng khác kiểu dữ liệu
```

- `!=`: so sánh khác
```js
var v1 = (5 != 10); //true
var v2 = (5 != "5"); //false
```

- `!==`: khác giá trị và khác kiểu
```js
var v1 = (5 !== 10); //false
var v2 = (5 !== "10"); // true
```

##### 1.2.4. Toán tử logic
- `&&`: phép và
- `||`: phép hoặc
- `!`: phủ định
```js
var a = (4>2) && (10>15);
// a = false vì vế trái đúng, vế phải sai
// a = true && false
```

##### 1.2.5. Toán tử ba ngôi
`variable = (condition) ? value1: value2;`
```js
var isAdult = (age < 18) ? "Too young" : "Old enough";
```

### 2. Đối tượng: Array, Object, String
#### 2.1. Array
- là danh sách các giá trị theo thứ tự
```js
let fruits = ['apple', 'banana', 'cherry'];
```
- Truy cập phần tử trong mảng
```js
console.log(fruit[0]); // apple
console.log(friut.length); // 3
```
- Một số phương thức phổ biến:

|Phương thức|Ý nghĩa|Ví dụ|
|---|---|---|
|`push()`|Thêm phần tử vào cuối mảng|`arr.push("grape")`|
|`pop()`|Xóa phần tử cuối mảng|`arr.pop()`|
|`shift()`|Xóa phần tử đầu|`arr.shift()`|
|`unshift()`|Thêm vào đầu|`arr.unshift("mango")`|
|`slice(start, end)`|Cắt mảng con|`arr.slice(0, 2)`|
|`indexOf()`|Tìm vị trí phần tử|`arr.indexOf("banana")`|
|`includes()`|Kiểm tra có tồn tại hay không	|`arr.includes("apple")`|
|`join()`|Nối mảng thành chuỗi|`arr.join(", ")`|
|`reverse()`|Đảo ngược|`arr.reverse()`|

- Ví dụ:
```js
let nums = [10, 20, 30];
nums.push(40);           // [10, 20, 30, 40]
nums.splice(1, 1);       // [10, 30, 40]
console.log(nums.join(" - ")); // "10 - 30 - 40"
```

#### 2.2. Object
- Dùng để lưu thông tin theo cặp `key:value`
```js
let person = {
  name: "Alice",
  age: 25,
  isStudent: true
};
```
- Truy cập và cập nhật:
```js
console.log(person.name);     // Alice
console.log(person["age"]);   // 25

person.age = 26;
person.email = "alice@gmail.com";
```
- Một số thao tác phổ biến:

|Tác vụ|Ví dụ|
|---|---|
|Truy cập thuộc tính|`obj.key` hoặc `obj["key"]`|
|Thêm thuộc tính|`obj.newKey = value`|
|Xóa thuộc tính|`delete obj.key`|
|Lặp qua keys|`for (let key in obj)`|
|Lấy danh sách keys|`Object.keys(obj)`|
|Lấy danh sách values|`Object.values(obj)`|
|Lấy danh sách key-value|`Object.entries(obj)`|

- Ví dụ:
```js
let person = {
  name: "Tí",
  age: 18,
  email: "ti@gmail.com"
};

let entries = Object.entries(person);
console.log(entries);

/*
[
  ["name", "Tí"],
  ["age", 18],
  ["email", "ti@gmail.com"]
]
*/
```

#### 2.3. String
- Là một chuỗi các ký tự
```js
let str = "Hello, world!";
```

- Truy cập ký tự:
```js
console.log(str[0]); //H
console.log(str.length); // 13
```

- Một số phương thức phổ biến:

| Phương thức | Ý nghĩa    | Ví dụ|
|---|-----|---|
|`toUpperCase()`| Viết hoa toàn bộ| `str.toUpperCase()`|
| `toLowerCase()`| Viết thường toàn bộ| `str.toLowerCase()`|
| `includes()`| Kiểm tra có chứa chuỗi con không | `str.includes("world")`|
| `indexOf()`| Tìm vị trí chuỗi con đầu tiên| `str.indexOf("o")`|
| `slice(start, end)` | Cắt chuỗi con | `str.slice(0, 5)`|
| `replace(a, b)` | Thay thế đoạn chuỗi | `str.replace("world", "everyone")` |
| `split()` | Tách chuỗi thành mảng | `str.split(", ")` |
| `trim()` | Xóa khoảng trắng đầu và cuối | `"  hello  ".trim()`|

- Ví dụ:
```js
let name = "  Alice  ";
console.log(name.trim());// "Alice"
console.log(name.toUpperCase());// "  ALICE  "
console.log(name.includes("lic"));// true
```

### 3. Vòng lặp

| Tên vòng lặp| Dùng cho loại dữ liệu | Mục đích chính|
|---| ---| ---|
| `for`| Mảng, số | Lặp với chỉ số (index) rõ ràng |
| `while`, `do...while` | Mọi thứ| Lặp khi điều kiện còn đúng |
| `for...of` | Mảng, chuỗi, Set| Duyệt **giá trị** từng phần tử |
| `for...in` | Object, Array | Duyệt **key** của object (hoặc index mảng)  |
| `forEach` | Mảng | Duyệt mảng dễ đọc, nhưng không break/return |

#### 3.1. for

```js
for(let i = 0; i < 5; i++){
    console.log("i = ", i);
}
```

#### 3.2. while và do...while

```js
let i = 0;
while(i < 3){
    console.log(i);
    ++i;
}
let j = 0;
do{
    console.log(j);
    ++j
} while(j < 3);
```

#### 3.3. for..of (chỉ dành cho iterable)
```js
let fruits = ['apple', 'banana', 'cherry'];
for (let fruit of fruits){
    console.log(fruit);
}
```

#### 3.4. for...in (lặp qua key)
```js
let person = {name: 'Khanh',  age: 20};
for(let key in person){
    console.log(key, person[key]);
}
```

#### 3.5. forEach() - (cho mảng)

```js
let numbers = [1,2,3];
numbers.forEach(function(value, index){
    console.log(index, value);
});
```

### 4. Function(hàm)
- là khối mã được đặt tên, có thể gọi lại nhiều lần, giúp tái sử dụng code, tách logic rõ ràng
- **Function Declaration** (Khai báo hàm):
```js
function sayHello(name){
    return "Hello " + name;
}
console.log(sayHello("Khanh"));
```

-> **Cú pháp ngắn gọn (Arrow Function)**:
```js
const greet = (name)=> "Hello " + name;
console.log(greet("Khanh"))
```

- **Function có đối số và trả về:**
```js
function multiply(a,b){
    return a * b;
}
let res = multiply(3,4); // 12
```

- **Tham số mặc định:**
```js
function greet(name = "bạn"){
    return "Xin chào" + name;
}
console.log(greet()); // Xin chào bạn
console.log(greet("Khánh")); // Xin chào Khánh
```


### 5. Array method: Map, Reduce, Filter, Includes, Group, Some, Every

#### 5.1. map(): chuyển đổi từng phần tử trong mảng
```js
let numbers = [1,2,3];
let doubled = numbers.map(x => x * 2);
console.log(doubled); // [2,4,6]
```
-> Trả về mảng mới, không làm thay đổi mảng gốc.

#### 5.2. filter(): lọc phần tử theo điều kiện

```js
let numbers = [1,2,3,4,5];
let even = numbers.filter(x => x%2 === 0);
console.log(even); //[2,4];
```
-> Trả về mảng mới chỉ chứa phần tử đúng điều kiện.

#### 5.3. reduce(): tính gộp lại 1 giá trị duy nhất
-  Cú pháp:
```js
array.reduce((accumulator, currentValue, index, array) => {...}, initialValue);
```

-> `accumulator`: biến tích lũy
   `currentValue`: phần tử hiện tại
   `initialValue`: giá trị khởi tạo


- Ví dụ:
```js
let nums = [1,2,3,4];
let sum = number.reduce((acc, val) => acc + val, 0);
console.log(sum); //10
```
->  Dùng để cộng dồn, nhân dồn, nhóm, gom object,...

#### 5.4. includes(): kiểm tra có tồn tại không

```js
let fruits = ['apple', 'banana', 'mango'];
console.log(fruits.includes('banana')); //true
console.log(fruits.includes('kiwi')); //false
```
-> trả về true/false

#### 5.5. some(): ít nhất 1 phẩn tử thỏa mãn điều kiện
```js
let ages = [10, 15, 20];
console.log(ages.some(age => age < 15)); //true (10)
```

#### 5.6. every(): tất cả phần tử đều đúng

```js
let ages = [10,15,20];
console.log(ages.every(age => age < 25)); //true
```

#### 5.7. group(): gom nhóm object theo key (JS6 chưa hỗ trợ dùng phương thức group)

- Ví dụ nhóm người theo độ tuổi:

```js
const people = [
    {name:"A", age:5},
    {name:"B", age:15},
    {name:"C", age:18}
];
const grouped = people.group(person =>person.age < 18 ? "Children":"Adult");
console.log(grouped);
```

### 6. callback
- là một **hàm** được truyền vào một hàm khác như một đối số, và được gọi bên trong hàm đó
-  Ví dụ:

```js
function sayHello(name){
    console.log("Hello " + name);
}
function greet(callback){
    const yourName = "Khanh";
    callback(yourName);
}
greet(sayHello);
```
->**Kết quả**: "Hello Khanh"

- Ví dụ về ứng dụng của calback trong `map`:
```js
const numbers = [1, 2, 3];
const doubled = numbers.map(num => num * 2);
console.log(doubled); // [2, 4, 6]
```
=> `num => num * 2` là một callback function được truyền vào `.map()`;

## Phần 2: JS6
### 1. `let` và `const` (thay thế var)
- `let`: khai báo biến có thể gán lại giá trị, nhưng có phạm vi khối
- `const`: khai báo hằng số

### 2.Arrow Function:
- Cú pháp viết hàm ngắn gọn hơn truyền thống
```js
const add = (a,b) => a + b;
console.log(add(2,3)); // 5
```

### 3. Template Literals (Chuỗi nội suy)
- Viết chuỗi dễ dàng với `${...}`

```js
const name = "Khanh";
const age = 20;
console.log("Tôi tên là ${name}, tôi ${age} tuổi");
// tôi tên là Khanh, tôi 20 tuổi
```
-> Không cần nối chuỗi bằng `+`, hỗ trợ xuống dòng dễ dàng

### 4. Destructing (Phân rã):
- Đối với object:

```js
const person = {name:"Khanh", age: 20};
const {name, age} = person;
console.log(name); // Khanh
console.log(age); // 20
```

- Đối với array:
```js
const arr = [1,2,3];
const [a,b,c] = arr;
console.log(b); //2
```

### 5. Spread(...) (Toán tử trải rộng)
- Copy hoặc nối mảng:
```js
const a = [1, 2];
const b = [...a, 3, 4];
console.log(b); // [1, 2, 3, 4]
```

- Copy object:
```js
const p1 = { name: "A", age: 18 };
const p2 = { ...p1, gender: "male" };
console.log(p2); // { name: "A", age: 18, gender: "male" }
```

### 6. Module (Import/Export):
- Tách file JS thành nhiều phần để tái sử dụng
- Ví dụ
    + file `math.js`:
    ```js
    export const add = (a,b) => a + b;
    export const multiply = (a,b) => a * b;  
    ```
    + file `main.js`:
    ```js
    import {add, multiply} from './math.js';
    console.log(add(2,3)); // 5
    console.log(multiply(2,3)); // 6
    ```

## Phần 3: DOM và Event
### 1. DOM là gì?
- **Dom (Document Object Model)** là một mô hình dạng cây đại diện cho cấu trúc của một trang web
    + Khi trình duyệt tải trang HTML, nó phân tích(parse) nội dung HTML và tạo ra mọt mô hình dạng cây DOM
    + Mỗi thẻ HTML trong tài liệu sẽ được chuyển thành một "đối tượng" (object) mà JavaScript có thể truy cập và thao tác
- **DOM** trông như thế nào?
- Ví dụ có đoạn HTML như sau:
```html
<!DOCTYPE html>
<html>
    <head>
        <title>Trang web của hoidanit</title>
    </head>
    <body>
        <h1>Chào bạn!</h1>
        <p>Đây là một đoạn văn bản.</p>
    </body>
</html>
```
-> DOM sẽ được biểu diễn như 1 cây phân cấp:
```
Document
 └── html
    ├── head
    │    └── title
    └── body
         ├── h1
         └── p
```

- **Dom cho phép làm gì?**: với Dom, ta có thể dùng JavaScript để:
    + Truy cập và đọc nội dung các phần tử HTML
    + Thay đổi nội dung hoặc thay đổi kiểu hiển thị(CSS)
    + Thêm, xóa phần tử HTML
    + Lắng nghe sự kiện người dùng: click chuột, nhập dữ liệu, rê chuột,...


- **HTML DOM**: là cách JS thấy một trang HTML như
    + Document: toàn bộ tài liệu
    + Element: các thẻ HTML
    + Attribute: thuộc tính của thẻ
    + Text: nội dung trong thẻ
    
-> Ví dụ:
```html
<p id="demo">Hello</p>
```
-> Có thể truy cập và thay đổi nội dung:
```js
document.getElementId("demo").innerText = "Hi";
```

- **DOM API (application Programming Interface)**: là tập hợp các hàm có sẵn để thao tác DOM
-> Một số API phổ biến

| API| Mô tả |
|---|---|
| `getElementById()`| Tìm element theo id|
| `getElementsByClassName()`| Trả về danh sách các phần tử có class|
| `querySelector()`| Truy cập phần tử đầu tiên khớp CSS selector |
| `createElement()`| Tạo phần tử mới|
| `appendChild()`| Thêm phần tử vào cha|
| `removeChild()`| Xóa phần tử con|
| `setAttribute()` / `getAttribute()` | Thao tác với thuộc tính |
| `addEventListener()`| Gắn sự kiện|

```js
const div = document.createElement("div");
div.innerText = "Chào bạn!";
document.body.appendChild(div);
```

- **DOM Document Object**: `document` là dối tượng của toàn bộ DOM, địa dienj cho toàn bộ trang HTML hiện tại.
-> Ví dụ:
```js
console.log(document.title); // in ra tiêu đề trang
console.log(document.body);  // in ra phần body
console.log(document.URL);   // in ra URL
```

- **DOM Attributes**: có thể thao tác với các thuộc tính HTML thông qua:
    + **Các truy cập**:
    ```js
    let img = document.querySelector("img");
    console.log(img.src);
    img.alt = "ảnh mô tả mới"; // đổi thuộc tính
    ```
    + **Dùng get/set**:
    ```js
    img.getAttribute("src");
    img.setAttribute("alt", "Mô tả mới");
    ```

- **DOM CSS**: có thể thay đổi style của phần tử HTML qua `.style`
    + Truy cập trực tiếp:
    ```js
    let box = document.getElementById("box");
    box.style.backgroundColor = "red";
    box.style.fontSize = "20px";
    ```
-> **Lưu ý**: dùng **camelCase** cho thuộc tính CSS (ví dụ: background-color → backgroundColor)

### 2. DOM Events:
- là cách để lắng nghe và xử lý hành động người dùng như click, di chuột, nhập dữ liệu,...
- Ví dụ:
```html
<button id="btn">Click me</button>
```
```js
document.getElementById("btn").addEventListener("click", function () {
    alert("Bạn vừa bấm nút!");
});
```

- **innerText, textContent, innerHTML:** Ba thuộc tính này dùng để lấy hoặc thay đổi nội dung của phần tử HTML.
```html
<div id="demo"><b>Hello</b> <span>world!</span></div>
```

| Thuộc tính    | Ý nghĩa | Kết quả |
| --- | ---| ---|
| `innerText`| Lấy nội dung hiển thị trên trình duyệt (ẩn phần bị ẩn) | `"Hello world!"`|
| `textContent` | Lấy toàn bộ text bên trong kể cả bị ẩn| `"Hello world!"`|
| `innerHTML`   | Lấy cả HTML (bao gồm tag)| `"<b>Hello</b> <span>world!</span>"` |

-> Thay đổi nội dung
```js
document.getElementById("demo").innerText = "Chào bạn!";
document.getElementById("demo").innerHTML = "<i>Xin chào</i>";
```

- **preventDefault() & stopPropagation():**
    + `preventDefault()`: Ngăn hành vi mặc định của trình duyệt.
    -> Ví dụ:
    ```html
    <a href="https://google.com" id="link">Google</a>
    ```
    ```js
    document.getElementById("link").addEventListener("click", function (e) {
    e.preventDefault(); // Ngăn không cho chuyển trang
    alert("Không đi đâu cả!");
    });
    ```

    + `stopPropagation()`: Ngăn sự kiện lan ra ngoài.
    -> Ví dụ:
    ```html
    <div id="outer">
        <button id="inner">Click me</button>
    </div>
    ```
    ```js
        document.getElementById("outer").addEventListener("click", () => {
        alert("Outer clicked");
        });

        document.getElementById("inner").addEventListener("click", (e) => {
        e.stopPropagation(); // Ngăn không cho outer bị click
        alert("Inner clicked");
        });
    ```

- **Get element methods (Lấy phần tử)**:
| Method | Mô tả |
|---|---|
| `getElementById("id")`| Tìm phần tử theo `id`|
| `getElementsByClassName("class")` | HTMLCollection (theo class)|
| `getElementsByTagName("tag")`| HTMLCollection|
| `querySelector("selector")` | Trả về phần tử đầu tiên khớp|
| `querySelectorAll("selector")`| Trả về NodeList tất cả phần tử khớp |
