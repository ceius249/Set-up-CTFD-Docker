# 1. Môi trường
Tải ubuntu server 
# 2. Set up requirement
## Install Docker && Docker Compose

```bash
sudo apt-get update
```

```bash
sudo apt-get install ca-certificates curl
```

```bash
sudo install -m 0755 -d /etc/apt/keyrings
```

```bash
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
```

```bash
sudo chmod a+r /etc/apt/keyrings/docker.asc
```

```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

```bash
sudo apt-get update
```

```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

## Check Docker && Docker Compose
```bash
sudo docker -v
```

``` bash
sudo docker compose version
```

# 3. Install CTFD
- Clone ctfd, sau đó vào repo
```bash
git clone https://github.com/CTFd/CTFd.git
```
- Thêm file **.ctfd_secret_key** trong repo CTFd
```bash
head -c 64 /dev/urandom > .ctfd_secret_key
```
Hoặc
```bash
echo "<something>" > .ctfd_secret_key
```
- Chỉnh sửa file **docker-compose.yml** với WORKERS = 4
- Lưu ý: 
	- Nếu đã thêm file .ctfd_secret_key như trên rồi thì không cần phải tạo SECRET_KEY như trong docs nữa
	- Chạy command `sudo docker compose up`, không phải là `sudo docker-compose up`
- Chạy command `sudo docker compose up` (có thể thêm -d nếu muốn chạy ngầm)
- Truy cập vào đường dẫn http://<ip\>:\<port\>
