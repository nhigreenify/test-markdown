# **How to Build a GraphQL server with NodeJS and Express**

***<span style = "color: green">GraphQL</span>** là một ngôn ngữ truy vấn cho các API và thực thi các truy vấn đó với dữ liệu hiện có.*

***<span style = "color: green">GraphQL</span>** cung cấp đầy đủ và dễ hiểu về dữ liệu trong API để yêu cầu chính xác những gì ta cần và không hơn, giúp dễ dàng mở rộng API theo thời gian và cung cấp các công cụ phát triển mạnh mẽ.*

***<span style = "color: green">GraphQL</span>** làm việc với Playground và GraphiQL, cũng có một số lựa chọn thay thế từ bên thứ ba như Altair và <span style = "color: green">Insomnia</span>.*

### *1. Using GraphQL:*

- Sử dụng <span style = "color: green">GraphQL với Express và NodeJS</span> để tạo 1 server đơn giản trả về 1 image hoặc tập hợp image tuỳ thuộc vào truy vấn.
- Để build được thì phải cần có:

-**<span style = "color: green">The GraphQL schema</span>** (Lược đồ GraphQL - mô tả loại và hệ thống phân cấp của CSDL. Nó xác định các điểm cuối truy vấn mà khách hàng có thể gửi yêu cầu.)

-**<span style = "color: green">The Resolver</span>** (Trình giải quyết - để giúp đính kèm một hàm vào mỗi truy vấn từ lược đồ thực thi khi yêu cầu của khách hàng chứa truy vấn đó.)

-**<span style = "color: green">The Data</span>** (Dữ liệu - Đây sẽ là dữ liệu mà máy chủ trả về khi nhận được truy vấn. Đối với mục đích demo ở đây  sẽ tạo một mảng các đối tượng hình ảnh và trả về dữ liệu theo truy vấn.)

### *2. DEMO Creating Server: build **<span style = "color: green">GraphQL</span>** server using **<span style = "color: green">Express and NodeJS.</span>***

- Tạo dự án node với lệnh terminal: *<span style = "color: red">npm init</span>*
- Trong **<span style = "color: green">package.json</span>** cần thêm trường (“type”:”module” vì tại demo này sẽ tạo 1 module ES6):

![alt](https://i.imgur.com/mUf8WVo.png)
- Tiếp theo sẽ cài đặt **<span style = "color: green">GraphQL và Express</span>** với lệnh: ***npm i graphql express express-graphql -–save***
- Cuối cùng thêm đoạn mã dưới để thiết lập máy chủ: [Link Source Code](https://gist.github.com/RanjanSushant/772ee45d006c29d5d4c2ba7a668819a9#file-graphql_server_demo-js)

*Lưu ý: Demo trên sử dụng phương thức <span style = "color: green">**buildSchema**</span> do <span style = "color: green">**graphql**</span> cung cấp để xác định lược đồ. Phương thức gốc sau đó tới <span style = "color: green">**hàm giải quyết**</span>. Nó đính kèm các chức năng vào các truy vấn khác nhau có sẵn cho người dùng. Và hãy cần xác định các chức năng đó trong tệp của mình.*

*Sử dụng express, demo đã tạo ra một biến ứng dụng sử dụng <span style = "color: green">**endpoint graphql**</span> và <span style = "color: green">**phần mềm trung gian graphqlHTTP**</span>. Phần mềm trung gian này lấy hàm giải quyết và lược đồ làm tham số. Và hãy đặt tùy chọn <span style = "color: green">**graphiql thành true**</span>, cho phép công cụ trong trình duyệt <span style = "color: green">**GraphiQL**</span> được sử dụng để kiểm tra endpoint bằng cách cung cấp cho nó các truy vấn.*

### *3. Sending queries using GraphiQL:*

- *Sử dụng terminal để có thể chạy lệnh sau để khởi động máy chủ của mình: <span style = "color: green">**node graphql_server_demo.js</span>** (chú ý tên tệp có bạn đặt có thể khác)*

- *Sau đó truy cập http://localhost:5000/graphql để truy cập GraphQL dễ dàng thao tác truy vấn:*

![alt](https://i.imgur.com/1ERv3rs.png)

*Giao diện sẽ trông như thế này*

- Trong demo này sẽ sử dụng 2 endpoint: 

1. <span style = "color: green">***image:***</span> get 1 image duy nhất theo id

2. <span style = "color: green">***images***:</span> gets images theo một danh mục cho endpoint image như sau:

![alt](https://i.imgur.com/gVhvx4C.png)

- Sử dụng biến <span style = "color: green">**$imageId**</span> tại mục <span  style = "color: green; font-family: Arial; font-size:15px;">**“Query Variables”**:

![alt](https://i.imgur.com/WpDkh92.png)

- Đây là kết quả truy vấn:

![alt](https://i.imgur.com/MNK64T3.png)

=> Tương tự có thể truy vấn với các endpoint khác như ví dụ trên.

Trên đây là cách thiết lập <span style = "color: green">**GraphQl server sử dụng Express và NodeJS**.</span> Và chỉ là 1 demo rất đơn trong thực tế nó sẽ phức tạp hơn rất nhiều. 


