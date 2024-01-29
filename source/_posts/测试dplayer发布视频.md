---
title: 备忘：dplayer发布视频测试及操作步骤
date: 2024-01-28 00:57:22
tags: 
     - 视频
     - 备忘
categories: 备忘
---

{% dplayer "url=1.mp4" "" "loop=yes" "theme=#FADFA3" "autoplay=true" "token=tokendemo" %}

# 一、博客中如果要插入本地视频，需要先安装hexo-tag-dplayer，在cmd/终端输入

```
npm install hexo-tag-dplayer --save
```

Mac端可能需要在命令前加“sodu”，以管理员身份运行，回车之后按提示输入登录密码，再回车。

成功安装后在 博客根目录/node_modules 中会出现dplayer 文件夹。

# 二、确保hexo的配置文件_config.yml里

```
post_asset_folder: true
```

这个设置可以在hexo new ''新的文章"时在 博客根目录/source/_posts 里面生成同名文件夹，用来存放本地视频文件以及视频封面图片。

# 三、把视频文件和作为视频封面的图片文件放到同名文件夹里，然后在文章插入以下语句

```
{% dplayer "url=1.mp4"  "pic=1.png" "loop=yes" "theme=#FADFA3" "autoplay=false" "token=tokendemo" %}
```

“url=本地视频文件名”空格“pic=封面图片文件名”，图片可以留空。注意单个文件大小不能超过100m，否则不能上传至GitHub。

# 插入本地音频操作类似，需要先安装hexo-tag-aplayer，执行命令

```
npm install --save hexo-tag-aplayer
```

把音频文件放到同名文件夹里，然后在文章插入以下语句

```
{% aplayer "No_Time_for_Caution" "Hans_Zimmer" "No_Time_for_Caution-Hans_Zimmer-24026258.mp3" "https://img4.kuwo.cn/star/albumcover/300/50/69/4184500136.jpg" %}
```
