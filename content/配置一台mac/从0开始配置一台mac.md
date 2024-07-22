```json
{
  "date": "2024.07.03 18:00",
  "tags": ["macOS"],
  "description":"拿到了一台全新的mac电脑怎么办🤯🤯🤯"
}
```
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



### 配置.zshrc

需要对新电脑的终端做一些个性化的配置才用的顺手，比如代理配置，自定义短语指令等等

在`用户根目录`下的`.zshrc`文件最后增加这几行内容：

```bash
#配置代理地址
export http_proxy='http://localhost:7890'
export https_proxy='http://localhost:7890'

#配置git-log优雅显示
alias git-log='git log --pretty=oneline --all --graph --abbrev-commit --decorate'

#配置ll，匹配linux习惯
alias ll='ls -al'
```





