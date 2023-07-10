**1. Cài docker**

[Link tải:](https://www.docker.com/products/docker-desktop/)

**2. Setup môi trường WSL 2:**
- Vào Windows PowerShell => run as administrator
- Nhập lệnh sau:\
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
=> chờ khi run xong => restart lại máy
- Vào cmd bằng quyền admin => nhập lệnh sau:\
** wsl --set-default-version 2 **
- Tải linux: [Link tải:](https://aka.ms/wslstorepage)

**3. Cài directus**
- Clone dự án từ link git https://github.com/tientham/directus   
- Git checkout dev-tien-9.21.2
- Tải và giải nén folder dc và cho vào folder directus (ngang cấp với main)\
link tải: https://drive.google.com/file/d/1ZGu5tOKjZyqSGuIX0QVwsl_dohpTtwq8/view?usp=sharing
- Double click docker desktop để run docker
- Replace file index.js trong  \directus\dc\extensions\modules\global-search và \directus\dc\extensions\modules\tien bằng file index.js mới

<u>*Cách 1*</u>: Mở terminal trỏ đến fiie docker (macOS):

![alt](https://i.imgur.com/xjS0EYQ.png)

- Sau đó chạy lệnh “make test-image”

![alt](https://i.imgur.com/E6PnGBv.png)

- Chạy tiếp “make test-image” là hoàn thành 

![alt](https://i.imgur.com/DCJ4jXI.png)

<u>*Cách 2*</u>: Mở terminal trỏ đến dc nhập 2 lệnh sau:

![alt](https://i.imgur.com/TjODMxi.png)

```
docker compose build

docker compose up
```

- Sau khi chạy xong vào http://localhost:8055/	

![alt](https://i.imgur.com/HupvCkY.png)

![alt](https://i.imgur.com/C7ZPSY8.png)

user: admin@example.com

pass: d1r3ctu5
