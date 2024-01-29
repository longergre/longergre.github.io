---
title: 备忘：有用的git命令
date: 2024-01-29 18:10:02
tags:
    - 备忘
    - git
categories: 备忘
---

# git基本操作

```
git clone 【仓库地址】
```

这需要cd到想要保存仓库文件夹的路径再执行，否则需要指定路径。执行之后会在相应路径下建立文件夹，其名称与仓库名称相同，其内容与仓库默认分支相同。

```
git add .
```

添加当前目录下的所有文件到暂存区。

```
git commit -m "【这里写备注信息，可以留空】"
```

提交暂存区到本地仓库中。

```
git push origin 【分支名】
```

推送文件到origin主机的【分支名】分支。其中“origin”是远程主机名，远程主机一般都叫这个名，很少有人去改。

```
git pull origin 【分支名】
```

从远程获取代码并合并本地的版本。

<!--more-->

# 检查远程仓库和分支的连接状态

```
git remote -v
```

测试远程仓库是否连接。

```
git branch -a
```

测试远程仓库的分支。

这样就是没连接上。

![](https://cdn.jsdelivr.net/gh/longergre/picgo/img/d38ebfe4c9a5499786269fee65fed49b.png)

这样就是连接上了。

![](https://cdn.jsdelivr.net/gh/longergre/picgo/img/8e2ee8c81bf1479380e622df5d37d1e1.png)

# git pull 显示已是最新，并未拉取文件

![](https://cdn.jsdelivr.net/gh/longergre/picgo/img/b5e7069f04de43a1b1f81ec0ca2fe1bd.png)

在适当路径下依次执行如下命令：

```
git fetch --all
```

```
git reset --hard origin/【分支名】
```

```
git pull origin 【分支名】
```

# git push显示没有权限

## 确认用户信息配置

在本地系统用户文件夹中查看.gitconfig文件中的内容。如果已经配置成功，该文件内容应包括远程仓库的用户名、邮箱和登录密码。

![](https://cdn.jsdelivr.net/gh/longergre/picgo/img/b4f47e87268d4186abf71fbd6cb22f70.png)

![](https://cdn.jsdelivr.net/gh/longergre/picgo/img/c40e12b08b73471ba02ff21aaed03718.png)

## 若尚未配置成功，则需在命令行中执行以下命令

```
git config --global user.name "【用户名】"
```

```
git config --global user.email "【邮箱】"
```

```
git config --global user.password "【登录密码】"
```

## 生成SSH公钥和私钥

```
ssh-keygen
```

在冒号停顿处按回车键。如果以前生成过SSH公钥和私钥，会询问是否覆盖。其后冒号停顿的地方会有三个，一个设定文件名，另两个设定密码。所以一共要按三次回车键，使用默认文件名，不设密码。

## 查询公钥文件内容

![](https://cdn.jsdelivr.net/gh/longergre/picgo/img/776e37ba36ca4861a9e71b5eeea392cd.png)

生成公钥时系统会显示公钥文件的路径，但有时候这个路径无法直接访问，这时可执行

```
cat 【路径/id_rsa.pub】
```

如果执行ssh-keygen的过程中没有设置文件名的话，公钥的路径就是以/id_rsa.pub结尾的。执行上述cat命令之后，公钥的内容就会显示出来。

![](https://cdn.jsdelivr.net/gh/longergre/picgo/img/f434974c56c347b2b456e9919fdbff24.png)

## 复制公钥的内容，登录远程仓库，添加SSH key

![](https://cdn.jsdelivr.net/gh/longergre/picgo/img/9e783d16c3a2485e8e43c6c48e96f5f9.png)
