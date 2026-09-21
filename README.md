我先看一下你的 issues 页面内容。
再抽样看一下早期的 issues 主题分布，同时查一下全球前沿的变更记录/文档管理实践作参考。
信息够了。现在给你把方案落成可直接使用的文件：目录模板、自动导出脚本、GitHub Actions 工作流。
看完了你 issues 的最新 10 条（#1730–#1739）、最早的 10 条（#1–#10）和中段抽样（#393–#402）。先说结论，再给方案。

## 一、诊断：issues 当知识库的三大问题

从你的记录里能直接看到：

1. **没有分类**——1700+ 条里 AI 对话存档、软件吐槽、科幻设定分析、专业研究、社会议题全部混在一起，你自己在 #1739 里都在抱怨这个问题；
2. **格式丢失**——#1730 你说的"表格存进知识管理软件就丢、混成一坨"，在 GitHub issues 里同样存在（标题渲染空白），而仓库里的 Markdown 文件是原生渲染表格的；
3. **真正的痛点不是"记在哪"，而是提交摩擦**——#1739 你自己写了："每回提交前都要填一下更改记录，还不如记录在问题里直接点击提交"。

第 3 点正是全球前沿工程实践专门解决的问题，下面方案就是围绕它设计的。

## 二、目录用什么：6 大类 docs 结构

按你 issues 的实际内容分布（抽样显示的主题），建议固定 6 类、编号排序、不膨胀：

```
├── README.md        ← 门面+导航
├── INDEX.md         ← 全库分类索引（脚本自动生成）
├── CHANGELOG.md     ← 更新记录（Keep a Changelog 规范）
├── docs/
│   ├── 01-专业研究/   ← 机械/机电/具身智能/论文选题（你的主线，#1737 这类）
│   ├── 02-AI大模型/   ← 各家模型使用记录、对比（#1731、#1732 这类）
│   ├── 03-科幻设定/   ← 阿基拉/生化危机设定分析（#1734、#1738）
│   ├── 04-社会观察/   ← 养老金/AI泡沫（#1731、#1736）
│   ├── 05-工具与Bug/  ← 软件吐槽、踩坑（#1739、#395-#399）
│   ├── 06-资源收藏/   ← 链接收藏（#2-#10 早期主力）
│   └── journal/       ← 日记流，2026-09.md 一个月一个文件
└── .github/workflows/ ← 自动同步
```

依据是全球通用的四条实践：**Keep a Changelog**（更新记录按 Added/Changed/Fixed 分类倒序）；**Conventional Commits**（提交信息带 `docs:`/`feat:` 前缀，机器可解析）；**docs as code**（知识就是 md，可搜索可 diff 可回滚）；编号目录借自 Johnny Decimal 思想，保证排序稳定、肌肉记忆可循。Keep a Changelog 的核心结构是 `[Unreleased]` 段加 `Added/Changed/Deprecated/Removed/Fixed/Security` 六类，各自动化工具产出的章节互相兼容。

## 三、消灭"多点好几次"：三级方案，任选

**方案 A（最省事，推荐）：连提交都自动化。** 用 GitHub Actions 每周日自动把所有 issues 导出成分类 md、重新生成 INDEX.md、自动 commit 推送。之后你继续像现在一样在 issues 里随手记（保持零摩擦），代码部分永远自动保持最新。这和语雀等平台的"定时自动导出 + Git 管理"是同一套模式。

**方案 B（想养成在 md 里记的习惯）：网页直接编辑。** 打开 `docs/journal/2026-09.md` → 点铅笔 → 粘贴 → 点"Commit changes"，两次点击，和发 issue 几乎同摩擦。随手记进 journal，月底把有价值的条目搬进 01–06 分类。

**方案 C（更新记录自动生成）：** 提交信息写成 `docs(ai): 记录豆包工作模式速度测试` 这种 Conventional Commits 格式，然后用 git-cliff 一条命令从 git 历史生成 CHANGELOG——`git cliff -o CHANGELOG.md`。git-cliff 支持正则自定义解析器，模板可用配置文件定制，适合大仓库。这样"填更改记录"这个动作就从你的流程里彻底消失——这是业界自动化的标准路径：先统一提交规范，再引入 changelog 生成，最后接入 CI。

## 四、已生成的交付文件

我把上面所有东西做成了可直接使用的文件：

| 文件 | 用途 |
| --- | --- |
| `目录结构方案.md` | 完整结构说明 + INDEX/CHANGELOG 模板 + 痛点对照表 |
| `export_issues.py` | 一键导出全部 1739 条 issues → 按 6 主题 × 月份分类的 md + 自动生成 INDEX.md（公开仓库免 token 直接跑） |
| `.github/workflows/sync-docs.yml` | 每周自动同步的 Actions 工作流（也可手动点运行） |
| `cliff.toml` | git-cliff 配置（选了方案 C 才需要） |

使用步骤：
1. 把四个文件放进仓库（workflow 放到 `.github/workflows/`）；
2. 本地跑一次 `python export_issues.py`，全部历史 issues 就归档成带目录的 md；
3. 提交推送，以后每周自动同步，或随时在 Actions 页手动触发。

两点提醒：脚本按关键词规则自动分类，会有边界误判（比如 #1731 标题是讯飞星火但正文是养老金分析，会被归到 02-AI），跑完后建议抽查一下 `04-社会观察` 和 `02-AI大模型` 的交叉条目；另外 GitHub API 对未登录请求有限流（每小时 60 次），1700+ 条约需 18 次请求没问题，但如果你在 Actions 里跑会自动带上 token，更稳。

运行时间长了之后，任务管理框架就失效了，因为很多没有打标签或者进行分类。

# GitHub_GTD管理系统README.md 

01=收集箱=0=2020/10/15
赞助和捐赠相关，国外基金会各种较多工业革命相关视频的时候，也发现了开头有很多基金会的符号
怎么上传支付宝和微信截图？手机浏览器好麻烦，电脑上复制粘贴就行了，网页浏览器怎么上传文件
之前有看到有的开发者使用链接点击跳转显示图片

之前好些次使用国外论坛平台网站或者什么其他，突然掉线，翻墙突然失效或者掉速，搞得我写一大堆字，实际上根本没有提交保存好或一直转圈状态连不上，可能也和没有草稿箱功能有关系，搞得我丢了很多数据，我写了老半天，累死了，才写那么多字白给了。

02=下一步行动=0=2020/10/15
全球研发投入2500强+1500家独角兽🦄合计4000家具体应该怎么安排
还有很多不在榜单的怎么搞

官方的智能用的openai还是哪个根本不准的？
https://platform.deepseek.com/usage【深度求索开放平台官网可以看到统计使用次数的，什么时候能够实现类似的。】
https://liner.com/developers/docs/search-agent-api
这个韩国的学术智能大模型准非常多，
邀请链接，
https://app.liner.com/login?referralKey=nId2Hoz9-Fm9Cd3_&utm_campaign=rac-13-referral-invite&utm_medium=referral&utm_source=product

https://docs.github.com/cn/
[Search · anki](https://github.com/search?q=anki) 【也超级猛，7k储存库】




03=等待事项=0=2020/10/15
 备份地址在 https://gitee.com/kunpeng9/GTD2020-05-31 【担心将来万一美国发动制裁很可能用不了github，备份github上此项目到gitee。遗憾的是问题lssues无法备份】
 [希望增加对gitee的支持 · Issue #635 · webclipper/web-clipper](https://github.com/webclipper/web-clipper/issues/635)
 
 ![](https://raw.githubusercontent.com/kunpeng9/PicgoPicture2020-10-18/master/20201206183925.png)

没有标签的=https://github.com/kunpeng9/GTD2020-05-31/issues?q=is%3Aopen+is%3Aissue+no%3Alabel

出与统计+控制数量的需要，github上本项目还是不要打>2个标签了，打的多了，那就和没打标签差不多；要强化、增强执行力【2023年07月30日更新=不知道为什么在github输入光标老是乱跑、搞的老是打错字】


[tianruoyouxin (tianruo) / Repositories](https://github.com/tianruoyouxin?tab=repositories)   【好像很久没有在github写代码了】

为学生提供 dipakkr/a-to-z 资源 [dipakkr/A-to-Z-Resources-for-Students: ✅ Curated list of resources for college students](https://github.com/dipakkr/A-to-Z-Resources-for-Students)

04=执行项目工作台=0=2020/10/15
gitee老是莫名其妙突然被拦截，用不了，403代码。
125个科学问题和四大基本力，暗物质暗能量怎么管理分支，人工智能大模型，有一些查到的内容是错的，有些是对的，要校正的。
之前好些次用手机浏览器网页都没有这个界面版本之前都是特别大的那个，然后一直新建一直失败。
完整翻译 + 逐条命令作用详解
 
原文翻译
 
修改远程仓库分支名称不会自动更新你或者仓库其他成员电脑本地的代码分支，请执行下面命令更新你的本地仓库分支：
 
bash
  
git branch -m deploy <BRANCH> 
git fetch origin 
git branch -u origin/<BRANCH>
git remote set-head origin -a
 
 
 <BRANCH>  是占位符，需要替换成新分支名称，例如  online-release 
 
 
 
逐条命令解析
 
1.  git branch -m deploy <BRANCH> 
 
翻译：将本地名为  deploy  的分支重命名为新分支名  <BRANCH> 
 
-  -m  = move（重命名分支）
- 场景：远程已经把  deploy  分支改名，本地旧分支名字还叫 deploy，需要改名对齐
 
2.  git fetch origin 
 
翻译：拉取远端  origin  的所有最新分支信息（不合并代码）
 
- 获取远程仓库所有分支、标签变更，同步远程已经改名后的分支列表
- ⚠️ 和  git pull  区别：只更新分支索引，不会自动合并代码，更加安全
 
3.  git branch -u origin/<BRANCH> 
 
全称： git branch --set-upstream-to=origin/<BRANCH> 
翻译：把当前本地分支绑定上游追踪分支：远端的  <BRANCH> 
 
- 作用：建立本地分支 ↔ 远程新分支关联
- 执行后，后续直接  git push  /  git pull  不需要额外指定远端分支
 
如果不执行这条：push/pull 会报错「没有设置上游分支」
 
4.  git remote set-head origin -a 
 
翻译：自动同步远端  origin  的默认分支（HEAD指针）
 
-  -a  = auto 自动模式
- 作用：远程仓库如果修改了默认主分支（比如原来默认deploy，现在改成新分支），这条命令更新本地记录的远端默认分支
- 解决： git clone 、 git status  显示默认分支信息不一致问题
 
 
 
整套命令完整执行流程总结（使用示例）
 
假设远程把  deploy  改名为  prod-deploy 
替换  <BRANCH>  →  prod-deploy 
 
bash
  
#1 本地旧分支deploy重命名
git branch -m deploy prod-deploy
#2 同步远程所有分支信息
git fetch origin
#3 绑定本地分支追踪远程新分支
git branch -u origin/prod-deploy
#4 更新远端默认分支指针
git remote set-head origin -a
 
 
关键重要提醒
 
1. 仅修复本地分支名称 & 追踪关系，不会修改远程仓库
2. 仓库其他开发者每个人都需要手动执行这套命令，仅你操作没用
3. 如果其他人还继续使用旧名称  deploy  push代码，会新建一条独立远程分支，造成代码分裂
4. 操作前建议先  git status ，保证工作区干净，避免冲突
 
延伸补充（常见踩坑）
 
如果你不需要修改本地分支名，仅仅只是远程分支改名，旧分支被删除：
记得清理失效本地追踪：
 
bash
  
git fetch origin --prune
 
 
如果你需要，我可以整理一份【远程分支重命名完整操作清单（远程改名命令 + 全体成员本地同步步骤）】markdown版本。

[【直播回放】用TheBrain或Roam Research进行诗词关联+其他漫谈_哔哩哔哩 (゜-゜)つロ 干杯~-bilibili](https://www.bilibili.com/video/BV1uT4y1L7mf)【之前就知道吕了，反复看这个视频的时候顺便去搜了一下，还有去github看了一下】

【实践起来成本太高，本人机械电子工程的，非计算机专业；博客的内容实践起来有技术门槛，目前用不上，搞一个项目初步模仿一下】

[argenos/zotero-mdnotes: A Zotero plugin to export item metadata and notes as markdown files](https://github.com/argenos/zotero-mdnotes)

05=将来可能=1=2020/10/15
[pluwen/china-domain-allowlist: 常用中国网站白名单，纯列表，用于 SwitchyOmega，控制不走代理的网站。](https://github.com/pluwen/china-domain-allowlist)
[Search · 996](https://github.com/search?q=996) 

[996.ICU/README_CN.md at master · 996icu/996.ICU](https://github.com/996icu/996.ICU/blob/master/README_CN.md)

【这个是我自己的储存库，跳转不对！】[996icu2020-10-15/README_CN.md at master · kunpeng9/996icu2020-10-15](https://github.com/kunpeng9/996icu2020-10-15/blob/master/README_CN.md)

[Search · RoamResearch](https://github.com/search?q=RoamResearch)

[airingursb/bilibili-report: 🎈 B 站用户数据报告（Web App）](https://github.com/airingursb/bilibili-report)

[Awesome-Windows/Awesome: 🎉 An awesome & curated list of best applications and tools for Windows.](https://github.com/Awesome-Windows/Awesome)

06=归档资料=0=2020/10/15

07=历史=每日收集箱=0=2020/10/15
2023年03月25日20时02分=更新翻译书目录，之前不应该记录到知乎，没想到知乎居然这么麻烦！电脑发热太严重了、时不时就蓝屏
用quicker动作复制文件名，卡的等了好半天，结果被删好几次，点击提交文章之后整个消失，没有自动保存的草稿

 创建了就多用一段时间看，不急于改变策略，除非确定改变策略会更好【之前想过是不是应该用下其他的服务，插件或者网页啥的，或者其他的软件，但是还是放弃了，就只用github的简单的lssues功能+标签来管理】
 

灵感来自【2020/11/12】=
[JimmyLv/personal-reading-flow](https://github.com/JimmyLv/personal-reading-flow)

[Serverless 实战：打造个人阅读追踪系统 | 吕立青的博客](https://blog.jimmylv.info/2017-06-30-serverless-in-action-build-personal-reading-statistics-system/)

[JimmyLv/reading: My Reading List | 参考博客文章「Serverless 实战：打造个人阅读追踪系统」：](https://github.com/JimmyLv/reading)

【本项目(～￣(OO)￣)ブ是对吕立青博客内容的拙劣模仿；感谢他的启发【很早就有量化阅读还有系统化监控的想法，但是我一直不知道怎么实现它，也没有一个哪怕是大致上的,粗略的想法】


07=历史=资料=0=2020/10/15

【小心概念【notion】的所有的在1个【all in one】的理念;github就→github，不要加到滴答清单或者印象笔记或者我来，就在github上进行管理，打上不同的标签；】

【注意，项目下的read.me文件不能改成其他的名字，否则编辑完了之后，项目下面会出现提示叫你创建，自动提示】【GTD2020-05-31创建将github的项目链接等放入滴答清单进行管理或者印象笔记等，实践证明都不可行，不好用，完全被搁置了】

[listen1 (Listen 1)](https://github.com/listen1)【被封了* 集合的体验糟糕，没咋用了】

08=共享繁华=0=2020/10/15
