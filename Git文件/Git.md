###### 设置用户名

```
git config user.name "用户名"
```

###### 设置邮箱

```
git config user.email "你的邮箱"
```

###### 检查信息

```
git config -l
```

###### 检查状态

```
git status
```

###### 加载当前目录

```
git add .
```

###### 提交本地仓库

```
git conmmit -m "2023年03月29日21时28分"
```

第三方SSH

###### 生成sshkey

```
ssh-keygen -t rsa -C "邮箱"
```

###### 查看公钥

```
cat ~/.ssh/id_rsa.pub
```

###### 粘贴ssh

###### 终端

```
ssh -T git@github.com
```

