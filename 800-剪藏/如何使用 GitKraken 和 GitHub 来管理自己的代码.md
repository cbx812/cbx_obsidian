在[如何使用 Git 和 GitHub 来管理自己的代码](http://mp.weixin.qq.com/s?__biz=MzIxNDU3Njk5NQ==&mid=2247486244&idx=1&sn=f695bc8f3ff9a046f41c2d77f76d5ed6&chksm=97a43128a0d3b83eddc6195ac4ef36658534c1ffc0d42f2d03f2dedb1eae09f627a05f2590fe&scene=21#wechat_redirect)中我们已经介绍了通过git命令行，来管理github的项目，但是其中git命令的使用可能不太符合某些同学的使用习惯，从而提高了使用门槛，本章节讲介绍通过git GUI来实现github项目管理。

    通过GitKraken实现github管理自己的代码，同把大象放进冰箱一样，也是需要三步：  

*   下载并破解GitKraken  
    
*   新建Github仓库
    
*   克隆github仓库，并进行pull和push
    

**1.下载并破解GitKraken**

1）我们选择安装GitKraken6.5.1版本，因为GitKraken6.5.1版本时唯一一个免费的版本

     下载链接：https://pan.baidu.com/s/1pqJ3-eaC2B81oG\_12PwpFw

      提取码：zu2z

  下载完成后，即可得到这个setup安装包，先不要急着双击安装它。

![](https://mmbiz.qpic.cn/mmbiz_png/xnMLeA8ESjuJeDmVasMFkmKiaH0AkJB70icOkQTzOjbt88eQAhica0kMXPSOicia8aTZqgffcE0Ka2AeJ214icUcCaSg/640?wx_fmt=png)

原因：直接安装打开后，会出现7天试用期，需要在7天后进行收费。

2）打开C:\\Windows\\System32下的hosts，hosts文件是用来通过DNS网关登录某ip的，其作用就是将一些常用的网址域名与其对应的IP地址建立一个关联“数据库”，当用户在浏览器中输入一个需要登录的网址时，系统会首先自动从Hosts：

```css
127.0.0.1 release.gitkraken.com api.gitkraken
```

   **用来屏蔽Gitkraken的收费网站。** 

3）回到GitKraken的安装包位置，这个安装包很神奇，不需要自己配置安装过程，安装一次会默认在Local本地文件夹中安装，安装后关闭软件，进行下一步：屏蔽自动更新。

4）查看GitKraken快捷方式的路径：

![](https://mmbiz.qpic.cn/mmbiz_png/xnMLeA8ESjuJeDmVasMFkmKiaH0AkJB70RlBXUN9s4E1mdSlrmeFB4qTHibF2uUibGlHW3Wws4HMRSAa75ricDu4cQ/640?wx_fmt=png)

    发现目标里面是执行了update.exe，说明每次打开都会默认执行自动更新，然而我们不应该让它更新，新版本是收费的。所以我们对其更新进行屏蔽，也就是对update.exe进行屏蔽联网。

    在windows搜索中直接搜索"防火墙"，打开Windwos Defender 防火墙，点击"高级设置",点击"出站规则",点击右侧"新建规则"，选择"程序"：在路径上将update.exe的路径复制上去：

![](https://mmbiz.qpic.cn/mmbiz_png/xnMLeA8ESjuJeDmVasMFkmKiaH0AkJB70q8ZvPLOWkibUNkWVd9nICAkncUoalgvdA5eh7CZJxt6UpztU9iaEib4gw/640?wx_fmt=png)

    点击 “下一步”，选择"阻止连接"：

![](https://mmbiz.qpic.cn/mmbiz_png/xnMLeA8ESjuJeDmVasMFkmKiaH0AkJB70icLe2MsgWfPxrnkCGXe2jXQRiclJ9aIZ0ZuRvcIKK9ThUkl8KricnMiamg/640?wx_fmt=png)

    点击"下一步"，三个全都选中：

![](https://mmbiz.qpic.cn/mmbiz_png/xnMLeA8ESjuJeDmVasMFkmKiaH0AkJB70NoUfOUG0OicSaYBPudUtajibIA3sBF24MH2wUxA1C2MyqfNia10d3LoOQ/640?wx_fmt=png)

    点击"下一步"，设置规则名称及描述：

![](https://mmbiz.qpic.cn/mmbiz_png/xnMLeA8ESjuJeDmVasMFkmKiaH0AkJB706DiaibOWee0xLHoXNrTfbrZTv7kvUFPUXcNxMKzibuLNjQhn2YxcaRz7A/640?wx_fmt=png)

    完成即可，在"出站规则"中显示出新建的规则：

![](https://mmbiz.qpic.cn/mmbiz_png/xnMLeA8ESjuJeDmVasMFkmKiaH0AkJB70D5VVqPsUryibRyHdfPNm1asibbBU4FT9UPUCDXtmaic9jDWUwibhmAGVTw/640?wx_fmt=png)

    到这里，即完成了对GitKraken的安装和破解。

5）打开开始菜单的GitKraken快捷方式，先是一个可爱的章鱼，就进入了GitKraken：

![](https://mmbiz.qpic.cn/mmbiz_png/xnMLeA8ESjuJeDmVasMFkmKiaH0AkJB70KriaZ3K2xpCwIdhicgJkzIYia0yvAnoOmxzF6v83jYw7nJBK28H49gMag/640?wx_fmt=png)

![](https://mmbiz.qpic.cn/mmbiz_png/xnMLeA8ESjuJeDmVasMFkmKiaH0AkJB70lfEyX6piaJQBIedvqlvRXziaCV7mnL3NG83bcMOcXLUaVHuQ57N84TTA/640?wx_fmt=png)

    第一次打开的时候，选择用github账号登录。  

**2.新建github仓库**

![](https://mmbiz.qpic.cn/mmbiz_png/xnMLeA8ESjuJeDmVasMFkmKiaH0AkJB70s9rHKZTQ8XPXLwVHSbL6PN1YFkicNjbFibWU66HktG34ibUicvicb6zJNbA/640?wx_fmt=png)

![](https://mmbiz.qpic.cn/mmbiz_png/xnMLeA8ESjuJeDmVasMFkmKiaH0AkJB70ZZHQ6RcX0lic6dPsHBOy66Txz3YnC3FF6RWfjddcXmyMjoSBheGXZzA/640?wx_fmt=png)

**3.GitKraken和Github交互**

1）克隆github仓库  

![](https://mmbiz.qpic.cn/mmbiz_png/xnMLeA8ESjuJeDmVasMFkmKiaH0AkJB70UWWzZl2aicTleiahLYvYBjh4jIjS9Hq7q7LwVYGohLcB3P9iapicWUNfYQ/640?wx_fmt=png)

![](https://mmbiz.qpic.cn/mmbiz_png/xnMLeA8ESjuJeDmVasMFkmKiaH0AkJB70MjLUd7CS5zx0sxaqEKjUPyuewibf24BUkSnMBgfiaxWGgGiamUic3AO8hA/640?wx_fmt=png)

![](https://mmbiz.qpic.cn/mmbiz_png/xnMLeA8ESjuJeDmVasMFkmKiaH0AkJB70Jv67JOVv2g0RptBcJzB60SDESJxzO8lYCOPwoHFcicibuM36oPppQOGA/640?wx_fmt=png)

![](https://mmbiz.qpic.cn/mmbiz_png/xnMLeA8ESjuJeDmVasMFkmKiaH0AkJB70icEK7Hw98YdSGM45ic6ZSEnyg1IUVR6IZBRNfwIuic9Eict3iawvwF0SGhQ/640?wx_fmt=png)

    至此，我们已经将github上面的项目克隆到本地路径。  

2）Push本地更改

    打开本地路径

![](https://mmbiz.qpic.cn/mmbiz_png/xnMLeA8ESjuJeDmVasMFkmKiaH0AkJB70FnsQV66mYxUVUW5ksl9axnnvQibHv0ehtq03DMlT9ibicORNicDLoicDibibw/640?wx_fmt=png)

新建一个测试文档

![](https://mmbiz.qpic.cn/mmbiz_png/xnMLeA8ESjuJeDmVasMFkmKiaH0AkJB70dqW1LlOjvTia9Z6aOBaGgtrib8MmHtshITGZfeDJGlkLgXrNaU07RrEw/640?wx_fmt=png)

    提示有文档编辑过  

![](https://mmbiz.qpic.cn/mmbiz_png/xnMLeA8ESjuJeDmVasMFkmKiaH0AkJB70QonBYhUB6ibx0MZ6aJXoCCicSPMLGqpWadpDW7Hf5Vkjvfj3fvf5fQSA/640?wx_fmt=png)

    显示缓冲区文件，通过stage all changes将缓冲区文件导出，提交的时候注意要附上注释，记录更改内容  

![](https://mmbiz.qpic.cn/mmbiz_png/xnMLeA8ESjuJeDmVasMFkmKiaH0AkJB70RHqfoEvJdTHagWianAH2az30cu0IA4w2BSdtmR3ucLAytzH7dw18aQg/640?wx_fmt=png)

![](https://mmbiz.qpic.cn/mmbiz_png/xnMLeA8ESjuJeDmVasMFkmKiaH0AkJB70ibQXGVNb8V26NmlTxKZ2ecSlx7GJsEx7anYZrwtgy2BjmSiax2S95tRA/640?wx_fmt=png)

    刷新github，可以看的此时生成了一个新的文件  

![](https://mmbiz.qpic.cn/mmbiz_png/xnMLeA8ESjuJeDmVasMFkmKiaH0AkJB70uEFIlZywJhexOxWVpC0BdrfSZg9bnPWKByEUOWLoNLpt4P2W1BzttA/640?wx_fmt=png)

3）Pull远程代码

    在github中add file  

![](https://mmbiz.qpic.cn/mmbiz_png/xnMLeA8ESjuJeDmVasMFkmKiaH0AkJB70LRMc8JYpV34ZpnY2elYc0ibm85PdMcMIVSlPtkqITQts8unNIE6L00g/640?wx_fmt=png)

![](https://mmbiz.qpic.cn/mmbiz_png/xnMLeA8ESjuJeDmVasMFkmKiaH0AkJB709n61sLqAaxbXv9SZXEVuQAicymeLn3icic0NpFz35XMUBx25VEbFEwolQ/640?wx_fmt=png)

PS：参考

https://blog.csdn.net/weixin\_43335226/article/details/107091568

https://www.bilibili.com/video/BV1KD4y1S7FL?spm\_id\_from=333.880.my\_history.page.click