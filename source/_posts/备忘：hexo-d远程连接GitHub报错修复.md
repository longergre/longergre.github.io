---
title: 备忘：hexo d远程连接GitHub报错修复
date: 2024-01-28 21:39:43
tags:
    - 备忘
    - Hexo
categories: 备忘
---

# 输入密码报错，应使用Personal access tokens

## 一、生成token

1. 登录GitHub，点击网页右上角的头像，再点击Settings

   ![](https://cdn.jsdelivr.net/gh/longergre/picgo/img/屏幕快照 2024-01-28 下午9.51.07.png#pic_left =500x)

   <!--more-->

2. 点击网页左侧底部的Developer settings

   ![](https://cdn.jsdelivr.net/gh/longergre/picgo/img/屏幕快照 2024-01-28 下午9.54.30.png#pic_left =500x)

3. 点击Personal access tokens

   ![](https://cdn.jsdelivr.net/gh/longergre/picgo/img/屏幕快照 2024-01-28 下午9.55.47.png#pic_left =500x)

4. 点击Tokens（classic）

   ![](https://cdn.jsdelivr.net/gh/longergre/picgo/img/屏幕快照 2024-01-28 下午9.56.41.png#pic_left =500x)

5. 点击Generate new token

   ![](https://cdn.jsdelivr.net/gh/longergre/picgo/img/b0b9f559b7844d98912a7d7204160ca2.png)

6. 按下图提示设置，点击底部生成按钮

   ![](https://cdn.jsdelivr.net/gh/longergre/picgo/img/0410458e9e7146efbbd33f9199c687f8.png)

   注意保存生成的token，否则关闭页面不可找回

   ![](https://cdn.jsdelivr.net/gh/longergre/picgo/img/29b42c36da81436e947a73ab8377eea1.png)

   ## 二、修改博客根目录下的<mark>_config.yml</mark>文件

   将原本的

   ```
   repo: https://github.com/【用户名】/【用户名】.github.io.git
   ```

   改成

   ```
   repo: https://【这里填写刚刚拿到的token】@github.com/【用户名】/【用户名】.github.io.git
   ```

   即可。

   再执行 hexo d 时就不再需要输入GitHub用户名和密码了。

   # 出现错误<mark>error：spawn failed</mark>

   ## 一、删除博客根目录下的<mark>.deploy_git</mark>隐藏文件夹

   ## 二、执行命令

   ```
   git config --global core.autocrlf false
   ```
