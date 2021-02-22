---
title: "React Server Component"
date: 2021-02-06T12:46:52+07:00
author: "dnthanh"
tags: ["react", "server component", "frontend"]
keywords: ["react"]
description: "Giới thiệu tính năng mới nhất của react framework"
cover: "https://miro.medium.com/max/1240/1*tGA71mQYRla0DpyfrIG5ig.png"
---

# Vậy React Server Component là gì ?

Đội ngũ phát triển React gần đây vào 21/12/2020 đã giới thiệu về một tính năng mới của React mà mình nghĩ nó sẽ thay đổi cách xây dựng một ứng dụng web với react, như cách mà react hook đã làm. Ý tưởng của nghiên cứu này là giới thiệu thêm một loạt component mới (Server component).

React Server Component cho phép lập trình viên xây dựng ứng dụng có thể quyết định việc render một react component ở phía server hay client, qua đó có thể tận dụng được khả năng tương tác cao của client-side app cũng như tốc độ tải trang của server-side app.

## Lưu ý

Trước khi bắt đầu, bạn đọc nên chú ý React Server Component vẫn đang trong giải đoạn nghiên cứu.

> React core team quote:
>
> > We are sharing this work in the spirit of transparency and to get initial feedback from the React community. There will be plenty of
> > time for that, so don’t feel like you have to catch up right now!

## Bước 1: Xem Video giới thiệu

{{< rawhtml >}}
<iframe width="560" height="315" src="https://www.youtube.com/embed/TQQPAU21ZUw" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
{{< /rawhtml >}}

## Bước 2: Clone demo

Khi bạn đã xem video gới thiệu của nhóm phát triển react, bước tiếp theo là clone demo này về và vọc thôi. Demo này là một ứng dụng được xây dựng với React Server Component. Video ở trên đã đi qua các phần của demo code này và nhấn mạnh các điểm quan trọng trong cách hoạt động của Server Component và nhưng khả năng của chúng.

## Bước 3: Đọc React Server Component RFC

Bây giờ bạn đã xem video và vọc qua code demo. Nếu thấy hứng thú với tính năng mới này của React, bạn có thể tiếp tục với React.js RFCs repo để đọc về giới thiệu của React team một cách chi tiết hơn cũng như những thảo luận của lập trình viên trên toàn thế giới về chúng.

Sau đây là một vài ý trong RFC:

- Server component sẽ được chạy ở phía server và không có tác động đến dung lượng của ứng dụng. Code của server component sẽ không được gửi đến trình duyệt của người dùng qua đó cải thiện thời gian khởi động của ứng dụng.
- Server component có thể truy cập trực tiếp tài nguyên phía backend (database, file system, ...)
- Server component của thể tích hợp với client component. Ví dụL server component có thể tải dữ liệu ở phía server sau đó truyền cho client component qua props để CC (client component) có thể xử lý phần tương tác với người dùng.
- Server component có thể chọn client component nào được gửi đi, qua đó giảm lượng code xuống mức thấp nhất code thể.
- Server component có thể bảo toàn được trạng thái ở phía client.
- Lập trình viên có thể chia sẻ code của Server và Client, cho phép một component có thể render tĩnh ở phía server trong một số route và render ở phía client trong một số route khác.

#Zero-Bundle-Size Components
Khi phát triển ứng dụng, việc phải chọn một thư viện nào đó để hỗ trợ là rất thường xuyên. Ta sẽ cần một thư việc để render mardown hoặc một thư viện để xử lý ngày, những thư viện này khả năng cao sẽ làm tăng dung lượng của ứng dụng lên khá nhiều.

Ví dụ, thư biện để render mardown có dung lượng là 240kB khi nén lại cũng nặng đến 74KB.

```javascript
// NoteWithMarkdown.js
// NOTE: *before* Server Components.

import marked from 'marked'; // 35.9K (11.2K gzipped)
import sanitizeHtml from 'sanitize-html'; // 206K (63.3K gzipped)

function NoteWithMarkdown({text}) {
  const html = sanitizeHtml(marked(text));
  return (/* render */);
}
```

Tuy nhiên nhiều phần của ứng dụng không cần đến nhưng thư viện nặng nề này. Server component sẽ cho phép lập trình viên render nhưng nội dung tĩnh ở phía server, tận dụng được khả năng của các thư viện trong khi không làm tăng dung lượng của ứng dụng.

Nếu chúng ta viết lại đoạn code trên với server component, chúng ta có thể sử dụng đoạn code tương tự nhưng không cần chúng đến client, qua đó giảm được trên 240KB.

```javascript
/ NoteWithMarkdown.server.js - Server Component === zero bundle size.

import marked from 'marked'; // zero bundle size.
import sanitizeHtml from 'sanitize-html'; // zero bundle size.

function NoteWithMarkdown({text}) {
  // same as before
}
```

#Tiếp theo
Trên đây là toàn bộ sự hào hứng của tối với react server component. Tôi tin rằng tính năng mới này sẽ mang tới sự cải thiện về hiệu năng đáng kẻ ở React.JS website và chúng thực sự tuyệt vời cho mọi người phải không?!

bài viết được dịch lại từ [ahmadawais.com](https://ahmadawais.com/react-server-components/)
