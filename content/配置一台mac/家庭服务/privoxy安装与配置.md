```json
{
  "date": "2024.07.03 17:55",
  "tags": ["家庭服务"],
  "description":"部署局域网内的代理服务器，但是好像失败了，还没玩明白"
}
```
# privoxy安装与配置

## 简介

配置privoxy



## 服务器端

- 通过`homebrew`安装

  ```bash
  brew install privoxy
  ```

- 修改配置文件

  - 通过homebrew安装的软件的配置文件一般都在`/opt/homebrew/etc`下面

  - 对于`privoxy`,需要修改`/opt/homebrew/etc/privoxy/config`这个文件

  - 在文件末尾加上如下内容（注释用`#`表示）

    ```bash
    #全部流量都从从代理发出
    #forward .
    
    #所有流量都从本机（服务器）的7890端口发出，7890端口有一个clashx的代理服务
    forward . 127.0.0.1:7890
    
    #所有.google.com的流量都从7890端口走
    #forward .google.com 127.0.0.1:7890
    
    
    #配置日志输出文件和日志等级（然而配置完感觉没有用，不知道为什么）
    logfile /Users/chennann_mm/log
    debug 1
    debug 4096
    ```










==前一天配置的好好的，第二天烂了，不知道为什么==