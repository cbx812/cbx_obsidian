> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [mp.weixin.qq.com](https://mp.weixin.qq.com/s/WFcSgVX9YuDUv1YHtzIymw)

![](https://mmbiz.qpic.cn/mmbiz_png/oiabfUBO7nd75lXUyycm0kuN1kIQWjmMAMTmPqDibonicHsU0nkBxvLZbf3WN8ntEzNyMQy5tdGocIghuL3ia2qhZA/640?wx_fmt=png)

▍省流助手
---------

1.  简悦是一个稍后读软件，你可以用它收藏网页文章，等有时间再看，本文会告诉你它有什么用，以及应该怎么用，我只能说，这是个不折不扣的阅读神器。  
    
2.  Logseq 是一个双向链接笔记软件，和简悦搭配使用能搭建全自动的、本地离线的个人知识库
    
3.  本文同样适用于 Obsidian 用户，99% 的设置过程都是一样的，你只需要修改少数几个模板代码即可
    
4.  建议在浏览器上阅读本文，在手机上看这种教程无异于自虐
    

![](https://mmbiz.qpic.cn/mmbiz_png/oiabfUBO7nd5plJkF7WjMjUniaicCs2icdxiapaU9JymkkA15t1HB8hKdRFFUv7pd2sLZ8ooDy3I3ARFVAmlr3bLhzQ/640?wx_fmt=png)

▍前言
-------

对我来说，简悦并没有降低我面对稍后读的压力，但它大大提高了我清空稍后读的动力，特别是当它和双链笔记软件进行无缝联动时，那种读完一篇再来一篇的激情就像小龙虾配啤酒一样让人欲罢不能。它的机制决定了，我必须用自己的思想来充实笔记库，而非僵硬机械地复制剪藏一堆二手文本。阅读本篇文章可能还需要你对 Logseq 这个软件，或者至少对双向链接这个概念有所了解，你可以在本文末尾找到一些参考资料。

▍传统稍后读软件的局限性
----------------

稍后再读是不得已而为之，收藏只是为了能稍后阅读的手段，而阅读的最终目的则是为了能更好的思考和创作。

但 Pocket 或是 Instapaper 这类传统的稍后读应用，只满足了收藏和阅读这两项最基础的需求，它们强调自己能用多种方式收藏多平台、多类型的网页、文章、或推文，更在意如何能让收藏这个动作更快捷。至于后续阅读文章时，能划划高亮、写写批注就已是极限。在知识管理这条路上，它们所提供的想象力仅能到此为止。

所以我总在想一个问题，这些软件跟印象笔记的本质区别是什么？很多时候好像只是 UI 更好看而已。

![](https://mmbiz.qpic.cn/mmbiz_jpg/oiabfUBO7nd4QvD5TuyvH5YSFNDPOBkeogRfAZqugkFueHmT7XklOluEbKhxuJGplXglZMIFHTRuCts870g2NOQ/640?wx_fmt=jpeg)

我想说的是，当我们终于痛定思痛放弃印象笔记，就不要再把自己埋进下一个剪藏的深渊。不要再相信自己能有足够的自制力，一旦收藏这个动作几乎零成本，READ IT LATER 就会变成 READ IT NEVER。

当你终于攒够足够的行动力开始阅读和记录，你又会发现在稍后读里做笔记是非常痛苦的一件事。无数剪藏的文章会污染你的笔记库，让检索笔记变成灾难，这也是我极力反对再在 Logseq 或 Obsidian 中使用任何一款一键剪藏工具的原因。你也很难在其中输出深度的、长篇的内容，就好像你不会轻易在出租房里置办大型家具一样，这是我不看好用 Cubox 记笔记（或速记）的原因。

![](https://mmbiz.qpic.cn/mmbiz_jpg/oiabfUBO7nd75lXUyycm0kuN1kIQWjmMA6mUHDsa3R73wx8IyftSXL8ZNXu8mqkGZelLxV4qibbSEHBFckvFx2Uw/640?wx_fmt=jpeg)

于是大家又开始寻找下一款工具，希望稍后读软件能将其中批注的段落或笔记导入到自己的另一款笔记软件之中，毕竟只有在纯粹的笔记软件内才能真正输出想法和内容。于是问题又出现了：

*   稍后读软件原生支持导出的格式稀少
    
*   每当批注有所更新，就必须再手动操作导出一次
    
*   99% 的网页快照都是付费功能
    
*   无法拥有真正的永久快照，一旦云端服务过期或者停止运营就无法再次访问
    
*   无法避免的审核制度与隐私泄漏问题
    

今天这篇文章将尝试利用简悦 +Logseq 来解决上述的所有问题。

▍简悦的基石与创新：让阅读灵感自由流转
-----------------------

本篇只打算用最低限度的篇幅介绍简悦最基础的功能——也就是稍后读，完整的功能介绍你可以阅读少数派软件商城对简悦的这篇介绍：https://sspai.com/item/186

![](https://mmbiz.qpic.cn/mmbiz_png/oiabfUBO7nd75lXUyycm0kuN1kIQWjmMAQ2IicgsNFHQIowicZN0p6Pl1Axmh8FU4cfZk6ia88hLjNLiaVVrNGopq0Q/640?wx_fmt=png)

### 简悦的基石：开箱即用的稍后读

简悦目前支持以插件形式在 Chrome 以及 Edge 等浏览器上安装使用，你无需任何额外设置就能使用以下两个最简单的功能：

1.  立即阅读：使用快捷键 `AA` 进入 `阅读模式`，在这个模式下它会自动提取标题和正文，并清除页面的多余元素，让你能用自定义的 `字体`、`间距` 和 `背景颜色` 等参数阅读文章。
    
2.  稍后阅读：使用快捷键 `DD` 将该网页加入 `稍后读清单`，等你有时间阅读的时候，你可以右键简悦插件，进入稍后读后台阅读那些你待读的文章，如下图所示：
    

![](https://mmbiz.qpic.cn/mmbiz_png/oiabfUBO7nd75lXUyycm0kuN1kIQWjmMAk1GgABnsoniaJ3uKXHNsGbFfRnibyib9BE2Q4DMvHvYGqGzUIddaT5nNA/640?wx_fmt=png)

简悦的稍后读后台

在这个用法上，简悦与其他任何一款稍后读软件几乎没有本质区别，但是：

*   市面几乎所有稍后读服务都是订阅制形式，年费至少在百元或以上，所有资料储存在云端，优点是开箱即用
    
*   简悦当前永久买断价格 18 元（据说很快要涨价了）；所有资料存储在本地；缺点是需要繁琐设置
    
*   基于简悦自由且开放的特性，它能以任意形式与几乎所有你能想到的本地的、或在线的效率软件进行联动
    

### 简悦的创新：牺牲便捷，突破边界

简约的创新和高自由度是用同样高得离谱的代价换来的，从本文超长的篇幅你应该不难看出，要想达到最终目的需要多么繁复的操作。但请相信我，如果你是一个双链笔记软件的使用者，一切都将是值得的。

#### ▍亮点其一：自由开放的多方联动

你可以在下图中寻找是否有你熟悉的 App Logo，以大家可能最熟悉的 Notion 为例，你可以一键（或者自动）将你通过简悦阅读过的、或者收藏了的文章全文同步到 Notion 上。原则上，简悦能拥抱一切愿意开放 API 接口的软件。

![](https://mmbiz.qpic.cn/mmbiz_png/oiabfUBO7nd75lXUyycm0kuN1kIQWjmMAliciaOicyrZ0cTe7QWnEwylwkSGUPE9Z51xrhH49yg2q8z1MrXta2cH8Q/640?wx_fmt=png)

其实还有好几个软件，但是找不到高清图标就没放进去

#### ▍亮点其二：一键 & 自动导出通用格式

![](https://mmbiz.qpic.cn/mmbiz_png/oiabfUBO7nd75lXUyycm0kuN1kIQWjmMAibHusiaknN5bQMpMAPg60mIe3VX12ibVspuhnpw8MtOenyYSfDxFTXRjA/640?wx_fmt=png)  

简悦并不希望用自有格式将用户困在它的库中，开发者的这篇文章《人人都应该建立自己的数据库》（https://www.yuque.com/kenshin/simpread/lpad5n）清晰地传达了他的这种理念。而能让简悦能与 Logseq （或 Obsidian）产生联动的，正是它自动导出的 MD 格式文本。

这个 MD 格式文本可以导出网页全文：

![](https://mmbiz.qpic.cn/mmbiz_png/oiabfUBO7nd75lXUyycm0kuN1kIQWjmMAxn9A3DJzV9AScJMUZbNspaQBTh1F83giaG9w42OcQiax0SEiaomr6vBMQ/640?wx_fmt=png)

也可以仅导出你划线和标注的几段话：

![](https://mmbiz.qpic.cn/mmbiz_png/oiabfUBO7nd75lXUyycm0kuN1kIQWjmMASkic2vDzByC33kybEzTw55ia0Zd0ibdb8iaDdvTfX5dbJnNOPaU2Z1jAug/640?wx_fmt=png)

#### ▍基于亮点二与 Logseq 的联动效果

如果你对 Logseq 已经具备一定的使用基础，应该会知道，Logseq 的基础是一个个 Markdown 文件，所以如果我们能够将这个 MD 格式的标注文件自动导入到 Logseq 的文件夹，那么 Logseq 就能即时读取到这个文件。

如下图所示，你在网页中批注的每一篇文章，都会自动转换成 Logseq（或 Obsidian）中的一个 Page，这个 Page 可以用丰富的参数自定义导出模板，但要想实现下图这样的自定义效果，你还需要对简悦进行一些配置，具体教程我后面会介绍。

![](https://mmbiz.qpic.cn/mmbiz_png/oiabfUBO7nd75lXUyycm0kuN1kIQWjmMAed8KDSQ3w8ordA26xmkn4H0Hdrqwiaez67g6ticjb2d2ic0L83SJG2Qzw/640?wx_fmt=png)

上图中的四个序号所对应的内容分别是：

*   ①：原文标题带超链接，点击可跳转到原网页
    
*   ②：自动打上的简悦标签，后期方便整理或集中查阅，这个标签可自定义修改
    
*   ③：自动生成批注时的日期，可被 Logseq 识别，这样就能显示在当天的 Daily Note 的 Linked References 下方，方便你在日记时间线下查看当天都读过哪些文章，如下图所示。
    
*   ④：所有你在网页中标注或批注的内容，都会出现在这里
    

![](https://mmbiz.qpic.cn/mmbiz_png/oiabfUBO7nd75lXUyycm0kuN1kIQWjmMAyO2iamaomtDkyrpeSeR7kVb2rOAN0vnk4UXg0CPU8AvFCzq9qYTZzFg/640?wx_fmt=png)

每一篇批注的文章都会出现在 Linked References 区域

#### ▍亮点其三：真正永久离线的网页快照

当你在 Logseq 中点击批注的句子时，它还能自动跳转到你所阅读的那篇文章的原文段落，表面上看这其实就是一个超链接跳转能解决的事，但简悦的不同之处在于，当你将网页加入稍后读，或者当你为网页留下任何划线或批注，它能自动离线保存原始网页的 HTML 文件，以及标注段落的 MD 文件，并导出到你的本地文件夹中，这样一来你永远不用担心超链接那头的网页会失效。

![](https://mmbiz.qpic.cn/mmbiz_gif/oiabfUBO7nd75lXUyycm0kuN1kIQWjmMAJDrzvOgUKfDujgbXDtDFG0FzfQDwZMpYFmtQALZeibgo4Euw7rJ19zQ/640?wx_fmt=gif)

本地笔记就该搭配本地离线的网页

目前市面上所有的稍后读软件，光是网页快照功能的月费就能买一个永久简悦了，并且由于快照是存储在它们的服务器上，所以理论上还是会有失效的风险。具体的永久快照效果你可以先参考简悦 Github 上的这个视频：点我跳转。

![](https://mmbiz.qpic.cn/mmbiz_png/oiabfUBO7nd75lXUyycm0kuN1kIQWjmMAXKHnnoeAnSmjWB6e1eeib5EwU99gvNMgSib85294nk6PJxP8Cb9so06A/640?wx_fmt=png)

在`阅读模式`下，你也可以选择标注并复制单独的一句话，然后直接粘贴到 Logseq（或任何支持超链接的地方）之中，点击这句话同样能自动跳转到自动保存的 HTML 网页对应段落上，这个功能对于保存可遇不可求的『金句』应该很有帮助。

![](https://mmbiz.qpic.cn/mmbiz_gif/oiabfUBO7nd75lXUyycm0kuN1kIQWjmMAf67JkSIXdjEeiajvX5p4oqHrhEugDtuU7eBKVcyzu5Z4Be0LPNRWYVg/640?wx_fmt=gif)

没有说图中这句是金句的意思

#### ▍亮点其四：足够灵敏的自动化

第四个亮点是前面三个的基础，简悦能用两个最基础的自动化命令，让信息在多平台之间的流转做到真正的自动化，如下图所示：

![](https://mmbiz.qpic.cn/mmbiz_png/oiabfUBO7nd75lXUyycm0kuN1kIQWjmMA8mUxD1aOO9LHib9o8fUkYLHqDh96L6CU0tLzuibBHNGsJAXNEghl2jeQ/640?wx_fmt=png)

▍简悦 + Logseq 设置全流程
----------------------

### 劝退警告：高耸入云的使用门槛

在你购买了高级账号后，仅激活并管理好你的高级账号权限这一项，已经能劝退起码 70% 的新手，如果你曾经因为这个原因放弃过简悦，那我真诚奉劝你不要再往下看，因为后面的设置之繁琐真是我生平仅见。

简悦给我带来了比当初研究 Omnifocus、Obsidian 或是 Logseq 所收获的挫败感总和乘以十还要多，被简悦搞崩溃只是入门的第一小步，一不小心还会迷失在开发者散落在 GitHub、Logseq、语雀或者是官方知识库里的成千上万字的教程当中，然后痛心疾首地感叹，要是这个软件能再易用一点，设置再简单一点，稍微缩减一下它的自由度，哪怕能做到 Cubox 三分之一的易用性，它将绝杀古今中外所有的稍后读软件，可惜换不得。

![](https://mmbiz.qpic.cn/mmbiz_png/oiabfUBO7nd75lXUyycm0kuN1kIQWjmMAqAjAxVibLoRUoGGiaM1cVnymia8doHNO6Ks7LT7MxaDz0nWwOX4Tu2PSw/640?wx_fmt=png)

开发者整理的，简悦功能大全

但我必须说，当你把所有自动化产线都架好后，你就会由衷地感叹这一切都是值得的，就好像忙活了一整年，终于能穿上新内裤去迎接新年的早晨一样。它给人带来的想象力是无边无际的，远不止是一个稍后读软件那么简单。

好的软件值得拥有更大的关注和市场，遗憾的是目前网上能够系统介绍简悦与 Logseq 联动的教程太少了， 所以我决定自己来写一篇。我想，如果当初在我折腾的时候能有人写一篇像我现在在写的文章，我真的会在感激涕零中给他打赏起码一年份的咖啡。

下面就让我们开始简悦与 Logseq 的联动设置教程，请备好足够的耐心和时间。

### 重置简悦插件到初始状态

请务必和我保持一致的设置参数和设置的先后顺序，以避免遗漏。因为简悦有太多本该放在一起的选项，反而是分散在设置界面的各个角落。只有（只要）按我的顺序操作，我才（我就）能保证你能获得和我一样的效果，如果流程上出了偏差或遗漏，不仅我救不了你，我也救不了我自己。所有的经验和教训，都是我经历了无数个夜晚的无能狂怒后，通过穷举测试每一个细节设置的具体作用得来的。

![](https://mmbiz.qpic.cn/mmbiz_png/oiabfUBO7nd75lXUyycm0kuN1kIQWjmMAsrTsN3ic78dWYRkgRyXGZCt6uFOOGfuBGVYEhgcwne6RuzP0fuX0YfQ/640?wx_fmt=png)

仅一项自动化功能，就测试了我两个多小时

请按下面的顺序操作，来将你的简悦恢复到初始状态：

1.  【设置 - 共通 - 导出配置文件到本地】，请保存好这个导出的文件，万一设置出错，你至少还能回到最初的地方。
    
2.  【设置 - 共通 - 配置文件】中，选择【重置当前配置文件】
    
3.  【设置 - 账户 - 已购买高级账号】选择【已购买高级账户 - 恢复高级账户】（请确认自己有高级账户权限）
    

![](https://mmbiz.qpic.cn/mmbiz_png/oiabfUBO7nd75lXUyycm0kuN1kIQWjmMAjHyC0oeJnto1L80v0twuiaax5Xaxicr9a60IicFBLD0okicOughwoqoeGg/640?wx_fmt=png)

### 安装同步与导出工具

#### ▍安装坚果云

就我并不太准确的观察而言，在简悦开发者的个人工作流中，坚果云占据了相当大的一部分比重，所以简悦的部分高级功能只在坚果云下能完整使用，为了避免更多的折腾，建议一步到位使用坚果云。

*   下载安装并注册坚果云
    
*   安装完坚果云后，请在坚果云的根目录新建一个名为 `SimpRead` 的文件夹
    
*   然后再在 `坚果云/SimpRead` 文件夹中，新建一个名为 `output` 的文件夹
    
*   这里目录和名称不可更改
    
*   再次提醒这里的位置是坚果云根目录，不要将文件夹新建在 `我的坚果云` 这个初始自带的文件夹里面
    

![](https://mmbiz.qpic.cn/mmbiz_png/oiabfUBO7nd75lXUyycm0kuN1kIQWjmMAh80Ww8uGowqOzVic9WyL4cfp1BoL7ViaMOamNUWsTIjn2bv6bmsMMRSA/640?wx_fmt=png)

#### ▍安装简悦 · 同步助手

*   下载地址：http://ksria.com/simpread/docs/#/Sync?id=%e4%b8%8b%e8%bd%bd
    
*   安装完毕后，请按照下面内容设置好各个选项卡的参数
    
*   【同步】：将 `同步文件夹路径` 指向 文件夹 `坚果云\SimpRead`
    
*   【导出】：
    

*   路径：`坚果云\SimpRead\output`
    
*   导出服务详细设定：开启所有选项
    

![](https://mmbiz.qpic.cn/mmbiz_png/oiabfUBO7nd75lXUyycm0kuN1kIQWjmMAlTaic5J6yX5yGjHm8a8XmGdaFGRnibdz6L8WqjHCFmacVDzUqpaJlDng/640?wx_fmt=png)

### 简悦插件设置

#### ▍共通

![](https://mmbiz.qpic.cn/mmbiz_png/oiabfUBO7nd75lXUyycm0kuN1kIQWjmMASHUYe66aOLvic7P4168x8N1JguRVQmBx8r6M1OvxztQ9BLJicCcTEGFQ/640?wx_fmt=png)

*   【验证】：点击 `授权验证简悦·同步助手客户端`
    
*   【自动同步】：选择 `启用同步助手的同步方案`
    

*   此时右上角会弹出数条提示信息，请先点击叉叉，把它们关掉
    
*   继续点击 `通过简悦 · 同步助手覆盖本地配置文件`（左边那项）
    
*   右上角会弹出一条提示，请点击 `保存`
    
*   这时在你刚刚新建的 `坚果云\SimpRead` 文件夹内，应该就会出现一个名叫 `simpread_config` 的 JSON 文件。这个 JSON 文件存储了简悦的所有个性化配置、以及你未来收藏的所有文章浏览和标注信息，请务必妥善保存。
    

![](https://mmbiz.qpic.cn/mmbiz_png/oiabfUBO7nd75lXUyycm0kuN1kIQWjmMA1MREmUZdYUQw1g8NVcCxG1krxiaMgaE0KY4VgM5xhQWibmowfqsfke2A/640?wx_fmt=png)

#### ▍高级设定

![](https://mmbiz.qpic.cn/mmbiz_png/oiabfUBO7nd75lXUyycm0kuN1kIQWjmMA9PJZLwIQoRS7K5JxmRvAt3pia47QLicEBicXyMyKpPllb1xjnCBQMDhWg/640?wx_fmt=png)

【暗色模式】

此处请取消打钩，否则【基础设定】中的各个主题选项很可能无法正常生效，这个问题起码让我卸载了简悦 5 次

【标注】

*   在进入阅读模式后不开启标注？————`否`
    
*   是否开启连续标注模式？——————————`是`
    
*   在标注时，浮动标注栏的显示方式？—————`鼠标移上时显示`
    
*   浮动标注栏可以选择一个默认的导出服务———`复制 Markdown 到剪贴板`
    
*   导出时可选————————————————`全文（含标注）+标注`
    

![](https://mmbiz.qpic.cn/mmbiz_png/oiabfUBO7nd75lXUyycm0kuN1kIQWjmMAxh0GHiceyubHhL08icJE6ibISF9ZYPn6jm7m8yrTGbHTI7t4sPD0SIz7w/640?wx_fmt=png)

设置完后，请刷新一次页面

#### ▍服务

![](https://mmbiz.qpic.cn/mmbiz_png/oiabfUBO7nd75lXUyycm0kuN1kIQWjmMAZicC2HrnQ4OjNn55mp1rjcTRcWFFrxv0h1xqM2joH5XecOQ9QmxBneA/640?wx_fmt=png)

【授权码】

*   同步时是否包含授权服务中的授权码？————是
    

【授权管理】

*   是否授权坚果云——————是
    

*   坚果云的 WebDAV 账号：就是你的坚果云账号
    
*   坚果云的 WebDAV 密码：请参考此教程获取（https://help.jianguoyun.com/?p=2064）
    
*   注：坚果云的免费账号足够实现本教程的所有功能，不用付费订阅坚果云
    

【定制导出】

*   当导出到本地时，是否开启自定义标题功能？————是
    
*   然后请在弹出的框中复制粘贴这段代码：`{{id}}{{un_title}}{{mode}}`
    

![](https://mmbiz.qpic.cn/mmbiz_png/oiabfUBO7nd75lXUyycm0kuN1kIQWjmMAQulXXoZAP419hcILoRR5pVYJGpCI5yRKFDY0VnWcCib6t58quAib95rQ/640?wx_fmt=png)

*   是否开启自定义 Markdown 模板功能？——————是
    
*   然后请在弹出的框中复制粘贴下列代码
    

```
#[[excerpt]] [{{title}}]({{url}}) 
- tags: #[[SimpRead]] {{tags}}
- read date: [[{{date_format|now|yyyy_MM_dd}} ]]
- desc: {{desc}}
{{#each}}
- [📌](<{{an_int_uri}}>)  {{an_html}}
{{>|an_note}}{{an_tags}}
{{/each}}

```

![](https://mmbiz.qpic.cn/mmbiz_png/oiabfUBO7nd75lXUyycm0kuN1kIQWjmMAaptaUS4Bwka5uqeCVTvSlxJyE2QKZ9YTPHC0FlSJdSFp5jT2NQibibXQ/640?wx_fmt=png)

如果你觉得上述模板不够个性化，或者如果你是 Obsidian 用户，有能力的话可参考下列两个链接修改。但在你完全掌握简悦的用法前，我的建议是不要轻举妄动。

1.  官方模板参数
    
2.  第三方用户个性化模板
    

*   当导出单条标注时，是否使用单条的定制模板？————是
    
*   然后请在弹出的框中复制粘贴这段代码
    

```
{{#each}}
[{{an_text}}](<{{an_ext_uri}}>)
{{/each}}

```

![](https://mmbiz.qpic.cn/mmbiz_png/oiabfUBO7nd75lXUyycm0kuN1kIQWjmMAPBonMSdltk2sGq0ZzkkGaJr2a9NevQR8LN0VHRl3O0zArTlkDv1HYw/640?wx_fmt=png)

【增强导出】

*   开启所有选项
    

![](https://mmbiz.qpic.cn/mmbiz_png/oiabfUBO7nd75lXUyycm0kuN1kIQWjmMAicKKNWUByczU8oDO6lKnuxwRox3Q4NCvBWtaHvfEFxgJLngDOZnFzfw/640?wx_fmt=png)

【自动化】

*   请按照下图分别添加两项自动化流程
    

![](https://mmbiz.qpic.cn/mmbiz_png/oiabfUBO7nd75lXUyycm0kuN1kIQWjmMArHSDcRc74F2u0VJx8qVG5ZN8atoiaZnPtezogUic2QTwXRxdavkwrFsg/640?wx_fmt=png)

【开放平台】

*   点击右侧箭头，跳转到简悦的开放平台
    

![](https://mmbiz.qpic.cn/mmbiz_png/oiabfUBO7nd75lXUyycm0kuN1kIQWjmMAQ34RxEibLLu8jpfDdAuicMagq7WdJyM3wlbcGrhSeicdHxbnT4YqArGqQ/640?wx_fmt=png)

*   使用你的坚果云 WebDAV 账号登录，登录后请按照下图继续操作，请记住下图中的 ID
    

![](https://mmbiz.qpic.cn/mmbiz_png/oiabfUBO7nd75lXUyycm0kuN1kIQWjmMADdMNdX6f6T3uznEN1gWqRQTBv6ibF8F0ibflvonGwYxy9beEFLXp7Ipg/640?wx_fmt=png)

【定制导出】

*   接下来我们回到前面的【定制导出】选项，然后找到【内部链接】和【外部链接】这两个选项，字很小，仔细找找
    
*   在【内部链接】这一栏，复制粘贴这串网址 `http://localhost:7026/reading/` 注意，这一串网址最后的 `/` 不能漏（下同）
    
*   在【外部链接】这一栏，复制粘贴这串网址 `https://simpread.pro/@id/reading/`，注意请将这串网址里的 `id` 该成你刚才在开放平台注册的个人 ID
    

![](https://mmbiz.qpic.cn/mmbiz_png/oiabfUBO7nd75lXUyycm0kuN1kIQWjmMADibLP0nJKiaKGSeDw5lGgVGJicSKCzq2lovCuT5yTicnibEFicLy7Q9wWxeQ/640?wx_fmt=png)

▍重要提醒

*   做完上述所有操作后，请务必刷新一下设置页面，然后从头检查一遍你的所有设置是否成功，简悦很容易出现一刷新页面，刚才的设置却不见了的情况
    
*   如果设置都在，但还是出问题，请再检查一遍刚才复制的模板代码是否正确粘贴成功，简悦的设置很容易出现复制粘贴「ABCD」，一刷新只剩下「A」的情况，特别是上面的【外部链接】这一项，如果你发现你的 ID 总是输入不完整，请尝试一次只输入一个字母，每输入一个字母就刷新一次网页这个方式。
    

#### 稍后读后台设置

进入简悦稍后读后台有以下三种方式：

1.  为 `进入稍后读后台` 这个动作创建一个快捷键
    
2.  右键简悦插件，进入稍后读
    
3.  右键网页空白处，点击简悦 - 进入稍后读
    

*   进入稍后读后台，鼠标悬停在右下角的红色叉叉上，然后点击浮出的小齿轮
    
*   然后按照下图所示的设置，逐步操作，保存后请刷新网页（或重启浏览器）
    

![](https://mmbiz.qpic.cn/mmbiz_png/oiabfUBO7nd75lXUyycm0kuN1kIQWjmMAQxtsV1r6KJb3wqF5nDiafiaRVCEbcWGJxqGYw7Qs8icibUxC81vf181JTA/640?wx_fmt=png)

### 自动化功能测试

现在，在我们基本上完成了简悦端的设置，在正式开始与 Logseq 的联动之前，请先测试一下下面的几个自动化功能是否正常

#### ▍自动化测试 - 稍后读存档

*   使用快捷键 `AA` ，进入`阅读模式`
    
*   使用快捷键 `DD`，将本篇文章加入稍后读。注意，只有在阅读模式下才能触发所有的自动化流程，原因说明见 Github #2362（https://github.com/Kenshin/simpread/discussions/2362）
    
*   进入简悦稍后读后台，查看本篇文章是否成功加入稍后读。你可以右键简悦浏览器插件，点击 `快捷键设置`，为这个动作赋予一个快捷键
    
*   进入本地文件夹 `坚果云/SimpRead/output`，查看是否自动保存了本篇文章的 HTML 文件
    

如果上述操作成功，你就能在加入稍后读的同时，将这篇文章的 HTML 存档下来。但因为这个 HTML 文件读取的是位于缓存中的图片，所以如果你希望能自动化离线存档网页文章（含图片），请在【服务 - 自动化】 中添加一项保存【离线 HTML】的设置。但这里更建议是保存为 Textbundle 格式，因为离线 HTML 需要将图片转译为 Base64 的代码，碰到多图杀猫的文章很容易卡顿或失败。

但如果你只是想实现稍后读这一项最基础的需求，不需要任何存档相关的操作，则不用先进入阅读模式，只需要在任意网页下用快捷键 DD，就能将任意一篇文章加入稍后读。

#### ▍自动化测试 - 标注内容存档

*   进入阅读模式（任意使用快捷键 AA，或者进入简悦稍后读后台）
    
*   鼠标选中任意一段文本，如果自动化成功，右上角就会弹出四条「已保存」的提示
    

![](https://mmbiz.qpic.cn/mmbiz_png/oiabfUBO7nd75lXUyycm0kuN1kIQWjmMAVVu1JqQWmoL2H4vrxB1ranXsm8OntpiaVOGNvLmlfcafP9oxnamVKrA/640?wx_fmt=png)

*   进入 `坚果云/SimpRead/output`，查看是否自动保存了 4 个文件
    

![](https://mmbiz.qpic.cn/mmbiz_png/oiabfUBO7nd75lXUyycm0kuN1kIQWjmMAOLXEoTJj5wicNYicpcy3V91PiaLa97lZNo73gHxXOl72Te1ibJibYQb46Xg/640?wx_fmt=png)

注意，这里如果只生成了 HTML 文件，而没有生成 Markdown 文件，你可以再多标注几条试试，如果只标注一条，简悦很容易无法成功生成 MD 文件。

另外对上图中的 4 个文件做一下说明

*   文件 ①：以 Markdown 格式保存的，你划线的句子，和所作的备注，特征是结尾有 `@annote` 这串字符，这个文件我们之后需要导入到 Logseq 的文件夹中
    
*   文件 ②：以 Markdown 格式保存的。网页原文（全文）
    
*   文件 ③：以 HTML 格式保存的，你划线的句子，和所留的备注；这个文件请保留在 `output` 文件夹中，不要移动
    
*   文件 ④：以 HTML 格式保存的，网页原文（全文）；这个文件请保留在 `output` 文件夹中，不要移动
    

注意，请点进文件 ① ，执行下列操作：

*   请检查是否正确应用了自定义的 Markdown 模板，如果模板应用成功了，那么这个 Markdown 文件的固定开头应该是 `#[[excerpt]]`
    

![](https://mmbiz.qpic.cn/mmbiz_png/oiabfUBO7nd75lXUyycm0kuN1kIQWjmMA143HBtDhwyQVpIJjWial7US9Qe6XicdianlaUsb9H2axq8PREXyibBWwQw/640?wx_fmt=png)

*   请参照下图中标蓝这串代码，找到它，并复制粘贴到浏览器中，如果能正常访问（即正确跳转到 HTML 文件对应的段落上）则说明上述所有操作都成功了
    

![](https://mmbiz.qpic.cn/mmbiz_png/oiabfUBO7nd75lXUyycm0kuN1kIQWjmMA9Q0eCHVicNeY29MPGiaNEo647UTwTzvJwsHMUYhrEOmf6un9Ns4OckPw/640?wx_fmt=png)

另外，这个 MD 文件的格式（模板）依然是可以自定义的。最后，如果上述两个自动化都成功了，那么就可以进行最后一步设置了。

### 将 MD 批注文件自动导入 Logseq

为了将上面这个 MD 格式的批注文件导入 Logseq，我们需要借助第三方的自动化工具，移动路径为：`坚果云/SimpRead/output` → `Logseq文件夹`，文件特征为带有`@annote`结尾的 MD 文件。

![](https://mmbiz.qpic.cn/mmbiz_png/oiabfUBO7nd75lXUyycm0kuN1kIQWjmMAoI6EyAViaiaszYhG9xIyKibhLnRSqmBxFzTNEdVbddquFH8sC2YSjicibvw/640?wx_fmt=png)

#### 注意事项

1.  由于 Logseq 会自动读取文件夹内的所有 MD 文档，所以我们不应该将简悦导出的所有 MD 文件（比如网页全文的 MD 文件）都放进 Logseq 的文件夹，这样一来不仅你的 Logseq 文件夹会变得越来越臃肿，也会污染你的个人笔记库，也不便后期搜索查阅。
    
2.  建议你在 Logseq 文件夹中单独新建一个文件夹，而不是直接导入到原来的 pages 文件夹中，方便你后期管理
    

#### ▍Windows 平台自动化工具：DropIt

这个工具能够允许你按照一定的自定义逻辑，自动监视文件夹，并对其中的文件进行复制、移动、解压等操作，更详细的指南可阅读少数派的这篇文章：《用 DropIt 打造全自动的 Windows 文件管理体系》（https://sspai.com/post/45532）

官方地址：http://www.dropitproject.com/

设置流程：

*   安装 Dropit ，启动后右键桌面上的这个图标，选择 `协议`
    
*   然后在弹出的方框中，点击左下角的绿色加号，按照下图添加自动化规则
    
*   将带有 `@annote` 后缀的 MD 文件夹到 Logseq 的文件夹中
    

![](https://mmbiz.qpic.cn/mmbiz_png/oiabfUBO7nd75lXUyycm0kuN1kIQWjmMAMzfJCJ79E1Mha8L331sOTGkYHoWlfmESibswD12x5Nz701htdh1NVKA/640?wx_fmt=png)

*   设置 Dropit 开机自动启动，以及自动监视 `output 文件夹`，一旦简悦在其中生成了带有 `@annote` 关键词的 Markdown 文件，则自动将这个文件移动到 Logseq 文件夹中
    

![](https://mmbiz.qpic.cn/mmbiz_png/oiabfUBO7nd75lXUyycm0kuN1kIQWjmMAyibws7F9SnWM26I05icjHfSzYBdyfp7JuV4n68zOibsIkFbsOmsUs92Og/640?wx_fmt=png)

到这一步，设置完 Dropit 后，当你在网页中使用快捷键 AA 进入阅读模式，然后标注任意文字段落后，就能在 Logseq 中看到你所标注的内容了。

#### ▍MacOS 平台自动化工具：Hazel

这个工具的比 Windows 端的 Dropit 还要强大，更详细的介绍你可以阅读少数派的这篇文章：《Hazel 5：变身独立应用，更有强大的列表及表格匹配功能》（https://sspai.com/post/63693）

官方地址：https://www.noodlesoft.com/

具体设置流程如图所示

![](https://mmbiz.qpic.cn/mmbiz_png/oiabfUBO7nd75lXUyycm0kuN1kIQWjmMAR8kyeLYnDxDuIJwVPEnvPIWeTfRJaF5FI7sXHxVO1KU5bgVibPsic4rQ/640?wx_fmt=png)

![](https://mmbiz.qpic.cn/mmbiz_png/oiabfUBO7nd75lXUyycm0kuN1kIQWjmMAXdZac943KiaaibgDQsH6fXo5qn6afY4dzPyApZajGoBC8B8ogpuRdIWw/640?wx_fmt=png)

至此我们完成了所有的自动化设置

### 让简悦在 Windows 与 MacOS 之间的同步

如果你是多平台用户，只需要在其中一个平台设置一遍简悦即可。假设我们现在已经在 Windows 上实现了简悦与 Logseq 的联动，现在想要在 MacOS 平台也复刻这样的效果，你可以参考下列教程。

*   在 macOS 上同样安装坚果云，以及简悦同步助手
    
*   macOS 的同步助手设置需要和 Windows 端的一样
    
*   打开 Windows 平台的浏览器，进入简悦插件的设置后台
    

*   在【设置 - 共通】这一栏中，拉到最下面，找到【自动同步】这一项，然后点击 `通过简悦·同步助手覆盖本地配置文件`（就是左边那一项，不要点错了）
    
*   这一操作的意义是，将 Windows 端的简悦配置文件的最新版本保存到坚果云上
    

*   打开 macOS 平台的浏览器，进入简悦插件的设置后台
    

*   在【设置 - 共通】这一栏中，拉到最下面，找到【自动同步】这一项，然后点击 `通过简悦·同步助手覆盖浏览器配置文件`（就是右边那一项，不要点错了）
    
*   当然，如果你真的点错了，你也能通过坚果云的文件历史版本记录，恢复回来
    
*   这一项操作的意义是，将 Windows 端最新的简悦配置文件，覆盖在 macOS 端的简悦上
    

到这里所有的设置真的结束了，完结撒花！

▍问题和吐槽
----------

1.  简悦最大的优点可能也是它最大的缺点，那就是它为了尽可能满足各种想得到的、以及想不到的需求，插件选项的自由度实在高到离谱，虽然确实如开发者所说，一次配置就可永久使用，但新手要想成功配置一次是何其困难，而且还有太多反直觉的选项，反而被当成了默认设置。
    
2.  简悦有很多本应该放在同一个地方的参数选项，被开发者分散地放在了不同的角落，还有很多因为版本更新而过期了的功能选项并没有被删除，反而是在你点击的时候给你一句提示「这个新功能被放在了 XXX 地方」，实在有点难以理解。
    
3.  简悦大概是一个典型的程序员导向的产品，它的功能强大无比，但它在产品功能的组织和编排（大概是这么形容吧）以及对功能名词的解释还有所欠缺，很难让人一眼就明白这项功能到底是干嘛用的，每次看半天描述却看不懂的时候是真的会生气
    

▍若干建议及玄学经验
--------------

1.  当你折腾到头了，觉得累了，想说算了，就这样吧，的时候，请一定单独导出一份配置文件留作恢复原件，不然日后当你再次心血来潮想要尝试某个新功能时，有极大可能把原先可用的功能搞崩
    
2.  不要同时打开两个插件设置页面, 这会造成配置互相覆盖
    
3.  最好每修改一个选项，每输入一段代码，就刷新一次网页做二次确认
    
4.  当你想尝试一个新功能时，最好记下你都修改了哪些地方，不然一定会忘
    
5.  当你出现问题时，不要同时修改很多个选项，最好控制变量逐个尝试
    
6.  请相信你所遇到的一切问题都不是 BUG，那其实是某种特性，开发者也早已为你写好一切所需要的文档，你需要的就是认真、细心地去找到这份文档，或者在 GitHub、在 telegram、在任何你能找到开发者的地方向他提问，他真的每一条都会回复
    
7.  找到文档后，请逐字逐句的查看，如果涉及到代码，请不要漏掉复制任 · 何 · 一 · 个 · 标 · 点 · 符 · 号！
    
8.  要有耐心，坐和放宽，这是一切的基础
    

▍帮助文档
---------

如果你遇到了问题，建议在下列几个渠道中搜索答案

*   简悦 GitHub 的 Discussions 和 Issues
    

*   https://github.com/Kenshin/simpread/discussions
    
*   https://github.com/Kenshin/simpread/issues
    

*   简悦用 Logseq 做的教程中心
    

*   https://kb.simpread.pro/#/page/Contents
    

*   在简悦的 语雀文档 中了解开发者的产品理念
    

*   https://www.yuque.com/kenshin/simpread
    

▍双链笔记参考资料
-------------

*   《双链笔记软件推荐：Logseq 和它的五种用法》
    

*   https://sspai.com/post/69503
    

*   《我们需要什么样的双向链接，它适合你吗？》
    

*   https://sspai.com/post/67996
    

*   我的 B 站视频
    

*   https://space.bilibili.com/319417