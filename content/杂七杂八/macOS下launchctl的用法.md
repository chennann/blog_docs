```json
{
  "date": "2024.07.06 17:33",
  "tags": ["macOS"],
  "description":"本站点建立在一个开源的golang项目上，显然一直开着一个终端运行是不合理的。本站点是搭建在一台mac mini上的，所以需要在macOS下配置一个系统服务。在Linux下可以通过systemctl配置系统服务，在macOS下需要launchctl"
}
```

# macOS下launchctl的用法

## 配置系统服务

- 👨🏻‍💻编译go程序

  ```bash
  go build -o forestBlog ForestBlog.go
  ```



- ⚙️创建plist

  每个用户的launchctl的服务配置文件都存放在`~/Library/LaunchAgents`文件夹下，而如果是`root`用户，则是存放在`/Library/LaunchDaemons`文件夹下，这里以用户为例子做演示。

  ```bash
  #首先cd到正确的目录
  cd ~/Library/LaunchAgents
  
  #创建服务配置文件，以.plist结尾
  vim chennann.forestBlog.plist
  ```

  

- ✍️编辑plist

  plist中的内容和Linux下.service文件中的内容大同小异，但是个人感觉.service要更加友好一点。在`chennann.forestBlog.plist`文件中添加如下内容：

  ```xml
  <?xml version="1.0" encoding="UTF-8"?>
  <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
  <plist version="1.0">
  <dict>
      <key>Label</key>
      <string>chennann.forestBlog</string>
      <key>ProgramArguments</key>
      <array>
          <string>/Users/chennann_mm/forest-blog/forestBlog</string>
      </array>
      <key>WorkingDirectory</key>
      <string>/Users/chennann_mm/forest-blog</string>
      <key>RunAtLoad</key>
      <true/>
      <key>KeepAlive</key>
      <true/>
      <key>StandardOutPath</key>
      <string>/Users/chennann_mm/forest-blog/forestBlog.out</string>
      <key>StandardErrorPath</key>
      <string>/Users/chennann_mm/forest-blog/forestBlog.err</string>
  </dict>
  </plist>
  ```

  - `Label`字段表示服务的标识
  - `ProgramArguments`字段表示服务要执行的操作，或者说指令。这里直接用刚才build出来的go程序即可
  - `WorkingDirectory`是我认为很关键的一个字段。因为plist文件是存放在统一的目录下的（`~/Library/LaunchAgents`），但是其中运行的程序可能会用到相对目录去找依赖或者其他资源文件，这就导致了服务不能正常启动运行。这里`WorkingDirectory`的作用就是指定工作目录，让这个服务中运行的指令好像是在工作目录中运行的一样，这样就解决了相对路径找不到的问题。
  - 其余字段见名知意，不想写了🫡



- ⏬加载服务

  ```bash
  launchctl load ~/Library/LaunchAgents/chennann.forestBlog.plist
  ```
  launchctl中的服务需要先被加载进来，类似于`systemctl daemon-reload`？加载完之后就可以用list命令看到配置的服务，但是这个时候还没有正式启动服务。
  
  ```bash
  launchctl list
  launchctl list | grep chennann
  ```



- 🚀启动服务（管理）

  ```bash
  #启动
  launchctl start chennann.forestBlog
  
  #停止
  launchctl stop chennann.forestBlog
  
  #卸载
  launchctl unload chennann.forestBlog
  ```

  但是实际操作发现启动的服务`stop`之后，又启动了（pid是不同了，应该是系统重新又自己开了），猜测是和配置文件中的`KeepAlive`字段的值有关系，有点迷🤨🤨。所以最后研究出来关停服务的操作是要把服务卸载了才可以💁🏻‍♂️。



## launchctl list

终端查看`launchctl list`返回如下的信息（删减，只保留关键信息）

```bash
PID     Status  Label
407     0       com.apple.trustd.agent
-       0       com.apple.SafariHistoryServiceAgent
-       -9      com.apple.progressd
89091   -9      com.apple.cloudphotod
-       78      homebrew.mxcl.squid
464     0       com.apple.Finder
6266    -15     chennann.forestBlog
456     0       application.abnerworks.Typora.167283.167562
-       0       com.apple.appleseed.seedusaged
```

- 可以看到用户所有load的服务，其中`Status`字段表示服务上一次退出的状态
  - 0    : 正常退出
  - -9   ：被 `SIGKILL` 信号终止
  - -15 ：被 `SIGTERM` 信号终止
  - 78  ：配置错误
- `Pid`字段表示服务当前的pid，如果有数字表示服务正在正常运行🙂，如果“-”则表示服务当前没有在运行🙃。