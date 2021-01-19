[mountain/unterwegs: A personal knowledge exploration tool](https://github.com/mountain/unterwegs)

# mountain/unterwegs: A personal knowledge exploration tool

**Unterwegs**, means "on the way" in German language, reflects the nature of knowledge seeking.

Unterwegs 在德语中的意思是 “在路上”，反映了知识寻求的本质。

## the initial idea 最初的想法

What is an ideal personal knowledge tool?

什么是理想的个人知识工具？

-   there have been a bunch of note-taking tools, but without fulltext searching, easy reference and citation 已经有很多笔记工具，但是没有全文检索，很容易参考和引用
-   there have been several open-sourced searching engines, but are very complex to config and set-up 有几个开源的搜索引擎，但是配置和设置非常复杂
-   there have been many document management tools, but most of them can only manage files not pages or paragraphs 文档管理工具很多，但大多数只能管理文件而不能管理页面或段落

Why it can not integrate all of these handy features in one tool? Maybe it is too heavy for any desktop application.

为什么它不能在一个工具中集成所有这些方便的特性？也许它对于任何桌面应用程序来说都太重了。

Then it comes with **Unterwegs**, a personal knowledge tool, running on a Home-NAS or a family server, which may generally cost you $500 ~ $1000.

然后它附带了 Unterwegs，一个个人知识工具，运行在 Home-NAS 或家庭服务器上，这通常需要花费你 500 ~ 1000 美元。

## the core concept 核心概念

Note cards, desktop, library are the core metaphor, and it also features

笔记卡、桌面、图书馆是其核心隐喻，也是其特色

-   reading/authoring: 阅读 / 创作:
    -   text: markdown with math formula support 文本: markdown with math formula support
    -   datavis: support vega data visualization 支援织女星数据可视化
    -   references: it can be at article, page and paragraph levels 引用: 它可以在文章，页面和段落的水平
-   organizing 组织
    -   classified by category, tag and aspect 按类别，标签和方面分类
-   searching 搜索
    -   fulltext searching 全文搜索
    -   search result can be refined into a card with cluster graph and nlp analysis data 搜索结果可以精炼成一张带有聚类图和 nlp 分析数据的卡片

For example, the cluster graph of key word "Alan Turing" in my article repository is as below [![](https://github.com/mountain/unterwegs/raw/main/docs/images/alanturing.png?raw=true)
](https://github.com/mountain/unterwegs/blob/main/docs/images/alanturing.png?raw=true)

例如，我的文章存储库中关键词 “Alan Turing” 的聚类图如下

## just on the way 就在路上

It is not finished, and is just on the way.

它还没有完工，只是在路上。

Currently, the main page of the tool is like that: [![](https://github.com/mountain/unterwegs/raw/main/docs/images/computability.png?raw=true)
](https://github.com/mountain/unterwegs/blob/main/docs/images/computability.png?raw=true)

目前，该工具的主页是这样的:

## how to run 怎么跑

1.  use the docker-compose to setup the system

    使用 docker-compose 来建立系统
2.  upload pdf files

    上传 pdf 档案

```shell
curl -v -F upload=@example.pdf http://HOST:PORT/upload
```

3.  visting the pages by browser at 通过浏览器查看网页[http://HOST:PORT/](http://HOST:PORT/) 
    [https://github.com/mountain/unterwegs](https://github.com/mountain/unterwegs)
