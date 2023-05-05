---
url: https://mp.weixin.qq.com/s/3L2MNJlKWfosL7LIjjKBtw
title: 使用本地图床优化 obsidian 的文件管理
date: 2023-05-03 14:44:10
tag: 本地图床
banner: "https://mmbiz.qpic.cn/mmbiz_jpg/IPZ262EcUIMBEldWaCG5TxkrTFRUzYAT600oybqJGlg1V00EVElxvzgQwJYuYDTuGheo63LX4F9aFaicl4icVbbg/0?wx_fmt=jpeg"
banner_icon: 🔖
---
# 摘要

使用 EasyWebSvr 软件来构建本地服务器，搭建本地图床，方便 obsidian 的图片引用，甚至是其他类型的文件引用。

# 引言

一般而言在 obsidian 或 markdown 领域，“图床” 是指将图片上传到互联网上的一个存储空间，供 markdown 引用，语法形式 一般为`![]()`。一般使用的服务提供商有腾讯云、阿里云、GitHub，gitee 等（对了，最近阿里云的对象存储费用好像降低了）。优点是避免 ob 库过大，一部分内容储存在网上有助于多端显示。缺点是：图床一般要用储存空间服务（上传和下载需要付费），另外可能有隐私泄露的疑虑。

但上述的图床可能只是图床中 “线上图床”，此外还有一种 “本地图床”。只要在本地电脑上建立服务器服务，让 ob 直接访问本地的地址，例如`127.0.0.1`，就可以访问相关图片。优点：免费，完全本地。

我之所考虑这方案，是为了管理艺术品的图片，一般该类照片的大小在 10m 以上，甚至有些在 50m，如果使用线上服务，网速传输和费用都存在问题。但如果都放在 ob 库中，因为我用坚果云同步，会直接占用大量空间也不是好的解决方法。

# 实际操作

事实上，所有能在本地构建服务端的软件都可以，例如 Apache、Nginx 等，但这些都有较高门槛。因此本文将使用 EasyWebSvr 软件（感谢蚕子的推荐）来构建本地服务器，改软件不大 100KB，使用简单。

![](https://mmbiz.qpic.cn/mmbiz_png/IPZ262EcUIPibh0Ys0uQCeqxzujxRic5Dz6xotKTpMVEaqxErTRjt2hpj1AqvB80dJhYiaJLl9bcX1XWqjBicXTYPg/640?wx_fmt=png)

点击下方栏目中的锤子按钮，点击 “设置”。

![](https://mmbiz.qpic.cn/mmbiz_png/IPZ262EcUIPibh0Ys0uQCeqxzujxRic5Dz6H1hGL4icJb7WzYOWAosnVd0j2wpQpydKeSH2TyTTuQh0kaM5e338nw/640?wx_fmt=png)

输入你本地图床的地址，记住相应端口。

![](https://mmbiz.qpic.cn/mmbiz_png/IPZ262EcUIPibh0Ys0uQCeqxzujxRic5DziasckDmmbic3Le6k8VZYB8icpeaD95rP83x2kW7jdxLU5DnEHeI4F0IFw/640?wx_fmt=png)

然后点击锤子旁边的按钮，启动服务器。

![](https://mmbiz.qpic.cn/mmbiz_png/IPZ262EcUIPibh0Ys0uQCeqxzujxRic5DzjqTiaBsVNDD0k0Xic0lGy9gC0uokzgBkVhP0bPLRNySHkWS7PgKsghtQ/640?wx_fmt=png)

我的图床目录内如下。

![](https://mmbiz.qpic.cn/mmbiz_png/IPZ262EcUIPibh0Ys0uQCeqxzujxRic5Dz56x7dNYE0QuP1eBQZqskW2OuiaK7B6YjqqZXCvSJiaBtjZkx8n9cgasg/640?wx_fmt=png)

因为我的端口为`1993`，因此，当我在 ob 中输入以下代码`![](http://127.0.0.1:1993/202304262109532.png)端口设置为80 ![](http://127.0.0.1:80/)`

就可以读取相关的图片，如下。因为这是本地图片，所以不能在多端同步，所以你们也将无法看到该图，而上方的图片是在线图床的图片，能让你们看到。