# Linux中systemctl的使用

- 编写`.service`服务文件

  - 在`/etc/systed/system`文件夹下创建一个新的文件`cvi.service`

    ```bash
    [Unit]
    #服务名称
    Description=CivilDefenseDetection Backend Service
    #确保java存在
    ConditionFileIsExecutable=/usr/local/jdk-21.0.3/bin/java
    After=network.target
    
    [Service]
    StartLimitInterval=5
    StartLimitBurst=10
    #执行指令
    ExecStart=/usr/local/jdk-21.0.3/bin/java -jar /usr/local/app/CivilDefenseDetection-0.0.1-SNAPSHOT.jar
    KillMode=process
    
    Restart=always
    RestartSec=120
    
    #配置标准输出文件位置
    StandardOutput=file:/usr/local/app/CivilDefenseDetection_sys.log
    
    #可以配置环境变量文件的位置，这里没有配置
    #
    
    [Install]
    WantedBy=multi-user.target
    ```

    *主要是写`服务名称`，`执行指令`，`输出文件位置`这几个部分，其余部分都不用改*

- 重载系统服务

  在修改了`.service`之后需要重载`systemctl`

  ```bash
  systemctl daemon-reload
  ```

  

- 常用的`systemctl`指令

  ```bash
  #启动服务
  systemctl start cvi.service
  
  #停止服务
  systemctl stop cvi.service
  
  #重启服务
  systemctl restart cvi.service
  
  #查看服务状态
  systemctl status cvi.service
  ```



- 查看日志输出

  - 使用`tail -f CivilDefenseDetection_sys.log `查看日志文件的最后几行

  - `-f`表示跟踪文件实时更新，当有新内容追加时，`tail`会显示这些内容

