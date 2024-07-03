```json
{
  "date": "2024.07.03 22:13",
  "tags": ["git"],
  "description":"在git push的时候如果按照提示一步一步操作会发现push不上去，说是认证出问题，其实是需要用token添加远程仓库。"
}
```

# 解决github不能push的问题

## 解决思路

- 用户名-密码的登陆方式不可用了
- 改用`token`的方式添加远程仓库



## 操作

- 从github生成密钥

  settings -> Developer Settings -> personal access token -> Tokens(classic) -> generate new token (classic) -> ...

- 获取到`token`之后，用下面的命令添加远程仓库

  ```bash
  #添加仓库
  git remote add origin  https://<token>@github.com/chennann/blog_docs.git
  
  #或者修改
  git remote set-url origin  https://<token>@github.com/chennann/blog_docs.git
  ```

- 然后就可以正常push

  ```bash
  git push -u origin main
  ```

  