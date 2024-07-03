# 从0开始配置一台mac

### homebrew

homebrew是mac上不可缺少的工具，可以实现方便的软件管理，服务管理等等。

- 先安装`xcode`
- 输入指令安装`brew`，并且换源

```bash
/bin/zsh -c "$(curl -fsSL https://gitee.com/cunkai/HomebrewCN/raw/master/Homebrew.sh)"
```

[参考资料](https://zhuanlan.zhihu.com/p/620975942)



### 安装一系列软件

```bash
#命令行文件树形展示
brew install tree

#ssh连接工具
brew install --cask termius

#代替原生终端，更现代化的终端界面
brew install warp

#clash代理工具
brew install clashx
```



### 安装docker

- Docker 官网下载[Docker.dmg](https://www.docker.com/products/docker-desktop/)
- 按照引导安装
- ==设置开机自启动==



