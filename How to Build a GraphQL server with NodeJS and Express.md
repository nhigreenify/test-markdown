# **How to Build a GraphQL server with NodeJS and Express**

***GraphQL** là một ngôn ngữ truy vấn cho các API và thực thi các truy vấn đó với dữ liệu hiện có.*

***GraphQL** cung cấp đầy đủ và dễ hiểu về dữ liệu trong API để yêu cầu chính xác những gì ta cần và không hơn, giúp dễ dàng mở rộng API theo thời gian và cung cấp các công cụ phát triển mạnh mẽ.*

***GraphQL** làm việc với Playground và GraphiQL, cũng có một số lựa chọn thay thế từ bên thứ ba như Altair và Insomnia.*

*1. Using GraphQL:*

- Sử dụng GraphQL với Express và NodeJS để tạo 1 server đơn giản trả về 1 image hoặc tập hợp image tuỳ thuộc vào truy vấn.
- Để build được thì phải cần có:

-**The GraphQL schema** (Lược đồ GraphQL - mô tả loại và hệ thống phân cấp của CSDL. Nó xác định các điểm cuối truy vấn mà khách hàng có thể gửi yêu cầu.)

-**The Resolver** (Trình giải quyết - để giúp đính kèm một hàm vào mỗi truy vấn từ lược đồ thực thi khi yêu cầu của khách hàng chứa truy vấn đó.)

-**The Data** (Dữ liệu - Đây sẽ là dữ liệu mà máy chủ trả về khi nhận được truy vấn. Đối với mục đích demo ở đây  sẽ tạo một mảng các đối tượng hình ảnh và trả về dữ liệu theo truy vấn.)

*2. DEMO Creating Server: build **GraphQL** server using **Express and NodeJS.***

- Tạo dự án node với lệnh terminal: ```npm init```
- Trong **package.json** cần thêm trường (“type”:”module” vì tại demo này sẽ tạo 1 module ES6):

![alt](https://i.imgur.com/mUf8WVo.png)
- Tiếp theo sẽ cài đặt **GraphQL và Express** với lệnh: ```npm i graphql express express-graphql -–save```
- Cuối cùng thêm đoạn mã dưới để thiết lập máy chủ: [Link Source Code](https://gist.github.com/RanjanSushant/772ee45d006c29d5d4c2ba7a668819a9#file-graphql_server_demo-js)

<u>*Lưu ý</u>: Demo trên sử dụng phương thức **buildSchema** do **graphql** cung cấp để xác định lược đồ. Phương thức gốc sau đó tới **hàm giải quyết**. Nó đính kèm các chức năng vào các truy vấn khác nhau có sẵn cho người dùng. Và hãy cần xác định các chức năng đó trong tệp của mình.*

*Sử dụng express, demo đã tạo ra một biến ứng dụng sử dụng **endpoint graphql** và **phần mềm trung gian graphqlHTTP**. Phần mềm trung gian này lấy hàm giải quyết và lược đồ làm tham số. Và hãy đặt tùy chọn **graphiql thành true**, cho phép công cụ trong trình duyệt **GraphiQL** được sử dụng để kiểm tra endpoint bằng cách cung cấp cho nó các truy vấn.*

*3. Sending queries using GraphiQL:*

- *Sử dụng terminal để có thể chạy lệnh sau để khởi động máy chủ của mình: node graphql_server_demo.js (chú ý tên tệp có bạn đặt có thể khác)*

- *Sau đó truy cập http://localhost:5000/graphql để truy cập GraphQL dễ dàng thao tác truy vấn:*

![alt](https://i.imgur.com/1ERv3rs.png)

*Giao diện sẽ trông như thế này*

- Trong demo này sẽ sử dụng 2 endpoint: 

1. ***image:*** get 1 image duy nhất theo id

2. ***images***:  gets images theo một danh mục cho endpoint image như sau:

![alt](https://i.imgur.com/gVhvx4C.png)

- Sử dụng biến **$imageId** tại mục **“Query Variables”**:

![alt](https://i.imgur.com/WpDkh92.png)

- Đây là kết quả truy vấn:

![alt](https://i.imgur.com/MNK64T3.png)

=> Tương tự có thể truy vấn với các endpoint khác như ví dụ trên.

Trên đây là cách thiết lập **GraphQl server sử dụng Express và NodeJS**. Và chỉ là 1 demo rất đơn trong thực tế nó sẽ phức tạp hơn rất nhiều. 