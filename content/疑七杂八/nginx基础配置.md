```json
{
  "date": "2024.07.03 18:28",
  "tags": ["nginx"],
  "description":"qweqwe___nginx基础基础最基础的用法"
}
```
# nginx基础配置

- 安装

  ```bash
  brew install nginx
  ```

- 配置server（配置一个目录浏览页面）

  nginx会从`/opt/homebrew/etc/nginx/servers/`这个路径下读取配置的`server`，所以只需要在这个目录下心间一个文件`default.conf`并且写配置即可。

  ```
  server {
      listen 9090 default_server;
      server_name  _;
  
      location /download {
          alias /Volumes/disk1/download/;
          # index index.html index.htm;
          autoindex on;  # 启用目录浏览
          autoindex_exact_size off;  # 可选，禁用精确文件大小显示
          autoindex_localtime on;  # 可选，使用本地时间显示文件修改时间
  
          charset utf-8;  # 指定字符编码为 UTF-8
      }
  
      location / {
          root   html;
          index  index.html index.htm;
      }
      error_page   500 502 503 504  /50x.html;
      location = /50x.html {
          root   html;
      }
  }
  ```

  - 监听`9090`端口
  - 默认路径`/`下会展示`index.html`
  - `/download`页面下会展示目录浏览页面，实现选择下载功能⏬