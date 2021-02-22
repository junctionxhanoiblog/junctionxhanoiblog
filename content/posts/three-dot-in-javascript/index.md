---
title: "Toán tử ... (spread) trong Javascript"
date: 2021-01-26T09:38:16+07:00
author: "ngdmau"
tags: ["javascript", "spread", "three dots"]
keywords: ["javascript"]
description: "Cách dùng cơ bản của toán tử spread"
showFullContent: false
cover: "https://miro.medium.com/max/768/1*Js0Y20MwjcTnVAe7KjDXNg.png"
---

Toán tử spread là một tính năng mới được bổ sung vào Javascript ES6. Toán tử này nhận đầu vào là một iterable object rồi expands it into individual elements.

Nó được sử dụng chủ yếu để tạo bản sao của các đối tượng trong Javascript. Việc sử dụng spread thường giúp cho code trở nên ngắn gọn và dễ đọc hơn.

Cú pháp: Toán tử spread được ký hiệu bằng dấu ba chấm: ...
```javascript
let array = [...value]
```
Ta sẽ sử dụng các ví dụ liên quan đến mảng (array), do nó là iterable object được dùng nhiều nhất trong JS.
**Ví dụ 1. Copy một mảng**
Thông thường, nếu ta làm như sau:
```javascript
let array1 = [1, 3, 5, 7];
let array2 = array1;
array1.push(9);
console.log(array2);
```
Khi đó, mọi thay đổi ở mảng array1 sẽ ảnh hưởng đến array2. Kết quả nhận được (thường không phải mong muốn của dev lắm) sẽ là:
```bash
[1, 3, 5, 7, 9]
```
Sử dụng toán tử spread, ta chỉ cần:
```javascript
let array1 = [1, 3, 5, 7];
let array2 = [...array1];
array2.push(9)
console.log(array2)
```
Kết quả:
```bash
[1, 3, 5, 7]
```
**Ví dụ 2. Insert một số phần tử của một mảng vào một mảng khác:**
```javascript
// append mảng desserts vào phía sau của mảng desserts1
let desserts = ['cake', 'cookie', 'donut'];
let desserts1 = ['icecream', 'flan', 'frozen yoghurt', ...desserts];
console.log(desserts);

// append mảng desserts ngay sau phần tử 'flan'
let desserts2 = ['icecream', 'flan', ...deserts, 'frozen yoghurt'];
console.log(desserts2);
```
Kết quả là:
```bash
[ 'icecream', 'flan', 'frozen yoghurt', 'cake', 'cookie', 'donut' ]
[ 'icecream', 'flan', 'cake', 'cookie', 'donut', 'frozen yoghurt' ]
```

**Ví dụ 3. Chuyển mảng thành tham số:**
```javascript
function multiply(number1, number2, number3) {
    console.log(number1 * number2 * number3);
}
let numbers = [1, 2, 3];
multiply(...numbers);
```
Ở đây, thay vì truyền các tham số lần lượt là numbers[0], numbers[1] và numbers[2], toán tử spread cho phép chuyển 1 mảng thành một loạt các phần tử đơn lẻ tương ứng.


Trên đây là 3 ví dụ cơ bản về cách sử dụng toán tử spread trong Javascript, bài viết được dịch lại từ [codeburst](https://codeburst.io/what-are-three-dots-in-javascript-6f09476b03e1)


