# mac安装homeassistant

## 通过docker安装

### 安装过程

#### 安装HA

以下步骤需要在安装完docker的前提下

- 终端输入

  ```bash
  docker pull homeassistant/home-assistant
  
  docker run -d --name="home-assistant" -v /Users/chennann_mm/hass:/config -p 8123:8123 homeassistant/home-assistant
  
  ```

  - `/Users/chennann_mm/hass`为容器创建的路径

- 浏览器进入`8123`端口，按照引导安装

#### 安装HACS

- 在HA的安装目录下，即`hass`目录下添加`www`和`custom_components`文件夹📁

- 在github上下载[hacs](https://github.com/hacs/integration/releases)

- 解压之后放入📁`custom_components`

- 重启`HA`，即重启docker容器

- 进入`HA`系统添加集成，搜索`hacs`

- 勾选所有之后按照引导安装（github验证）



### 存在的问题

由于macOS下docker的运行方式的问题，这种方式安装的HA不能连接到本地的局域网内，也就是说不能通过HA来实现米家设备接入homeKit的操作(因为不在一个网段，应该是🌚)。通过`UTM虚拟机`安装的HA就没有这种奇怪的限制。





## 🌟通过UTM虚拟机安装





