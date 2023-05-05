---
cssclass: fullwidth, centerAlign, academia, wideTable, whiteRed, whiteRed-rounded
obsidianUIMode: preview
---



> [!abstract]-  <center>文献阅读情况<center/>
>
>当前文献库中有 <font color=#FF0211>`$= dv.pages('"100-文献笔记"').file.length`</font> 篇文献！
>
>🪔  你已经完成 <font color=#FF0211>`$= dv.pages('"100-文献笔记" and #Done').file.length`</font>  篇文献的阅读。
>
>🗂️  接下来还有  <font color=#FF0211>`$= dv.pages('"100-文献笔记" and #unread').file.length`</font>  篇文献需要阅读，其中与你的研究方向<font color=red>高度相关</font>的文献还有 <font color=#FF0211> `$= dv.pages('"100-文献笔记" and #unread and #High-Related').file.length`</font>   篇，继续加油哦😇

 >[!note]- <center>文献标签汇总<center/>
 >
>```dataviewjs
> dv.paragraph(
   dv.pages('"100-文献笔记"').file.tags.distinct().map(t => {return `[${t}](${t})`}).array().join(" | ")
)
> ```

> [!done]-  <center>  已读文献目录 <center/>
> 
> ```dataview
> TABLE shortTitle as 中文标题, date as 日期, creators as 作者, rights as rating , publicationTitle as 期刊, tags , callNumber as IF, libraryCatalog As 分区, archiveLocation As 被引次数
> from "100-文献笔记" and #Done 
> sort date desc
> ```

>[!unread]+ <center>  未读文献：研究方向高相关 <center/>
>
> ```dataview
> TABLE shortTitle as 中文标题, date as 日期, creators as 作者, rights as rating , publicationTitle as 期刊, tags , callNumber as IF, libraryCatalog As 分区, archiveLocation As 被引次数
> from "100-文献笔记" and #unread and #High-Related   
> sort date desc
> ```

>[!unread]+ <center>  未读文献 <center/>
>
> ```dataview
> TABLE shortTitle as 中文标题, date as 日期, creators as 作者, rights as rating , publicationTitle as 期刊, tags , callNumber as IF, libraryCatalog As 分区, archiveLocation As 被引次数
> from "100-文献笔记" and #unread 
> sort date desc
> ```

>[!note]- <center> 文献总目录 <center/>
>
> ```dataview
> TABLE shortTitle as 中文标题, date as 日期, creators as 作者, rights as rating , publicationTitle as 期刊, tags , callNumber as IF, libraryCatalog As 分区, archiveLocation As 被引次数
> from "100-文献笔记" 
> sort date desc
> ```