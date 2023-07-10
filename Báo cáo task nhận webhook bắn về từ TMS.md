
# **Báo cáo task nhận webhook bắn về từ TMS** 

**Các bước nhận webhook bắn về từ TMS:**

1.Tạo project

- Nhập thông tin detail của project

Các trường bắt buộc:

-Name: Tên project

-Source language: Ngôn ngữ cần translate

-Target languages: Các ngôn ngữ đích

![alt](https://i.imgur.com/JJHsJ1S.png)

- Chọn continuous job -> Create project

![alt](https://i.imgur.com/wjwy1fI.png)

**Các bước sau sẽ được thực hiện trên postman:**

2. Tiền điều kiện và xử lý lỗi authentication

- Login bằng api Auth: https://cloud.memsource.com/web/api2/v1/auth/login
- Xử lý lỗi authentication

**Error code:** 401

**Nguyên nhân:** Token hết hạn

**Khắc phục:** Chạy lại api Login

3. Tạo webhook
- Lấy url receive webhook từ web Pipedream
-Đăng nhập vào trang web -> Create new workflows -> New HTTP/ Webhook Request

![alt](https://i.imgur.com/gOSVPMh.png)

-Click Save and continue

![alt](https://i.imgur.com/h4e66RW.png)

-Copy url nhận webhook bắn về

![alt](https://i.imgur.com/i8xpTPz.png)

- Tạo webhook mới sử dụng api: 

https://cloud.memsource.com/web/api2/v2/webhooks

**Request Body Schema**

| Param | Required | Type             | Description           |
|-------|----------|------------------|-----------------------|
| event | Yes      | Array of strings | Các sự kiện lắng nghe |
| url   | Yes      | String           | Url receive webhook   |

-Sự kiện lắng nghe: "JOB_STATUS_CHANGED"

-Web nhận webhook bắn về: https://pipedream.com/requestbin

-Url receive webhook: url đã copy ở phía trên.

-Response trả về khi sự kiện xảy ra:

![alt](https://i.imgur.com/v5ilcll.png)

4. Tạo job bằng api

- Get list projects sử dụng api:

https://cloud.memsource.com/web/api2/v1/projects

Để nhận uid của project dùng để tạo job

![alt](https://i.imgur.com/CCjxld0.png)

- Create job sử dụng api Create job:

https://cloud.memsource.com/web/api2/v1/projects/{projectUid}/jobs

**Path Parameters**

| Param      | Required | Type   | Description     |
|------------|----------|--------|-----------------|
| projectUid | Yes      | String | Uid của project |

**Request Headers**

| Param                | Required | Type   | Description                                                                            |
|----------------------|----------|--------|----------------------------------------------------------------------------------------|
| Content- Disposition | Yes      | String | Định dạng: filename*=UTF-8"{file_name} Truyền tên file( file_name được import từ body) |
| Memsource            | Yes      | String | Truyền targetLangs phải nằm trong các ngôn ngữ đích của project)                       |
| Content- Type        | Yes      | String | Định dạng dữ liệu được gửi                                                             |

![alt](https://i.imgur.com/AQssgAz.png)

**Body (binaty):** import file .json

![alt](https://i.imgur.com/uG9v9J8.png)

5. Accept job
- Sử dụng api Target File để check translate trả về:


https://cloud.memsource.com/web/api2/v1/projects/{projectUid}/jobs/{jobUid}/targetFile

**Path Parameters**

| Param      | Required | Type   | Description     |
|------------|----------|--------|-----------------|
| projectUid | Yes      | String | Uid của project |
| jobUid     | Yes      | string | Uid của job     |

![alt](https://i.imgur.com/dtkadWo.png)

**Note:** Lỗi khi chạy api Target File không hiển thị kết quả được translate

**Nguyên nhân:** Chưa chọn file trong Create job

**Khắc phục:** Create lại job và chọn lại file .json cần translate

- Sử dụng api Accept job để chuyển trạng thái của job sang “ACCEPTED”

https://cloud.memsource.com/web/api2/v1/projects/{projectUid}/jobs/{jobUid}/setStatus


**Path Parameters**

| Param      | Required | Type   | Description     |
|------------|----------|--------|-----------------|
| projectUid | Yes      | String | Uid của project |
| jobUid     | Yes      | string | Uid của job     |

**Request Body Schema**

| Param           | Required | Type   | Description                 |
|-----------------|----------|--------|-----------------------------|
| requestedStatus | Yes      | String | Trạng thái cập nhật của job |

6. Nhận webhook bắn về từ TMS

Mở trang web Pipedream để xem thông tin webhook bắn về, Chọn SELECT EVENT để xem thông tin

- Khi nhận webhook bắn về lần đầu

![alt](https://i.imgur.com/F309ejz.png)

- Khi nhận webhook bắn về lần thứ hai trở đi

![alt](https://i.imgur.com/1H0UUc3.png)
