# tonsky/datascript: Immutable database and Datalog query engine for Clojure, ClojureScript and JS
[![](https://github.com/tonsky/datascript/raw/master/extras/logo.svg)
](https://github.com/tonsky/datascript/blob/master/extras/logo.svg)

> What if creating a database would be as cheap as creating a Hashmap?
>
> 如果创建一个数据库和创建一个 Hashmap 一样简单呢？

An immutable in-memory database and Datalog query engine in Clojure and ClojureScript.

在 Clojure 和 ClojureScript 中的一个不可变的内存数据库和数据查询引擎。

DataScript is meant to run inside the browser. It is cheap to create, quick to query and ephemeral. You create a database on page load, put some data in it, track changes, do queries and forget about it when the user closes the page.

打算在浏览器内部运行。它创建成本低廉，查询速度快，而且转瞬即逝。您在页面加载时创建一个数据库，将一些数据放入其中，跟踪更改，执行查询，并在用户关闭页面时忘记它。

DataScript databases are immutable and based on persistent data structures. In fact, they’re more like data structures than databases (think Hashmap). Unlike querying a real SQL DB, when you query DataScript, it all comes down to a Hashmap lookup. Or series of lookups. Or array iteration. There’s no particular overhead to it. You put a little data in it, it’s fast. You put in a lot of data, well, at least it has indexes. That should do better than you filtering an array by hand anyway. The thing is really lightweight.

DataScript 数据库是不可变的，并且基于持久化数据结构。事实上，它们更像是数据结构而不是数据库 (想想 Hashmap)。与查询真正的 sqldb 不同，在查询 DataScript 时，这一切都归结为 Hashmap 查询。或者一系列的查找。或者数组迭代。没有什么特别的开销。你放一点数据进去，它很快。你放入了大量的数据，至少它有索引。无论如何，这应该比手工过滤数组要好。这东西真的很轻。

The intention with DataScript is to be a basic building block in client-side applications that needs to track a lot of state during their lifetime. There’s a lot of benefits:

DataScript 的目的是成为客户端应用程序中的基本构建块，在其生命周期中需要跟踪许多状态。这样做有很多好处:

-   Central, uniform approach to manage all application state. Clients working with state become decoupled and independent: rendering, server sync, undo/redo do not interfere with each other. 中央，统一的方法来管理所有的应用程序状态。处理状态的客户端变得分离和独立: 呈现、服务器同步、撤销 / 重做之间不会相互干扰
-   Immutability simplifies things even in a single-threaded browser environment. Keep track of app state evolution, rewind to any point in time, always render consistent state, sync in background without locking anybody. 即使在单线程浏览器环境中，不变性也能简化事情。跟踪应用程序状态的演变，倒回到任何时间点，始终呈现一致的状态，在后台同步而不锁定任何人
-   Datalog query engine to answer non-trivial questions about current app state. 用于回答关于当前应用程序状态的重要问题的数据记录查询引擎
-   Structured format to track data coming in and out of DB. Datalog queries can be run against it too. 用于跟踪数据进出 DB 的结构化格式，也可以针对它运行数据记录查询

Latest version 最新版本 \[![](https://camo.githubusercontent.com/b75c5a6ed61792e6dc6316ac726c12ac72a6aa32bcf2a64f1823aacd73e9d18b/68747470733a2f2f7472617669732d63692e6f72672f746f6e736b792f646174617363726970742e7376673f6272616e63683d6d6173746572)

## ]([https://travis-ci.org/tonsky/datascript](https://travis-ci.org/tonsky/datascript))

## Support us 支持我们

[![](https://github.com/tonsky/datascript/raw/master/extras/datascript_patreon.png)
](https://patreon.com/tonsky)

## Resources 资源

Support:

支持:

-   Join 加入[#datascript on Clojurians Slack # Clojurians Slack 的数据手稿](https://clojurians.slack.com/messages/C07V8N22C/) (grab invite (抓住邀请[here 这里](http://clojurians.net/))

Books:

书籍:

-   [Learning ClojureScript 学习 ClojureScript](https://www.packtpub.com/web-development/learning-clojurescript) has a chapter on DataScript 有一章是关于数据脚本的

Docs:

文件:

-   API Docs API 文档[![](https://camo.githubusercontent.com/39ef43c3576c8369329c90672b8e7510f83873b95724b4e53d4d3ba99f0cd0fe/68747470733a2f2f636c6a646f632e6f72672f62616467652f646174617363726970742f64617461736372697074)
    ](https://cljdoc.org/d/datascript/datascript/CURRENT)
-   [Getting started 开始吧](https://github.com/tonsky/datascript/wiki/Getting-started)
-   [Tutorials 教程](https://github.com/kristianmandrup/datascript-tutorial)
-   [DataScript 101 101](http://udayv.com/clojurescript/clojure/2016/04/28/datascript101/)
-   [Tips & tricks 技巧和窍门](https://github.com/tonsky/datascript/wiki/Tips-&-tricks)

Posts:

职位:

-   [How DataScript fits into the current webdev ecosystem 如何适应当前的 webdev 生态系统](http://tonsky.me/blog/decomposing-web-app-development/)
-   [DataScript internals explained 内部解释](http://tonsky.me/blog/datascript-internals/)
-   [Sketch of client/server reactive architecture 客户机 / 服务器反应式体系结构示意图](http://tonsky.me/blog/the-web-after-tomorrow/)

Talks:

讲座:

-   “Frontend with Joy” talk (FPConf, August 2015): 返回文章页面【一分钟科普】“快乐的前方”(FPConf，2015 年 8 月) :[video 视频](https://www.youtube.com/watch?v=cRWrrHPrk9g) in Russian 用俄语
-   “Programming Web UI with Database in a Browser” talk (PolyConf, July 2015): “在浏览器中使用数据库编写 Web UI” 演讲 (PolyConf，2015 年 7 月) :[slides 幻灯片](http://s.tonsky.me/conferences/2015.07%20polyconf.pdf), [video 视频](https://www.youtube.com/watch?v=1dr-CzMMDD8)
-   “DataScript for Web Development” talk (Clojure eXchange, Dec 2014): “用于 Web 开发的 DataScript” 演讲 (Clojure eXchange，2014 年 12 月) :[slides 幻灯片](http://s.tonsky.me/conferences/2014.12%20clojure%20eXchange.pdf), [video 视频](https://skillsmatter.com/skillscasts/6038-datascript-for-web-development)
-   “Building ToDo list with DataScript” webinar (ClojureScript NYC, Dec 2014): “用 DataScript 构建 ToDo 列表” 网络研讨会 (ClojureScript NYC，2014 年 12 月) :[video 视频](http://vimeo.com/114688970), [app 应用](https://github.com/tonsky/datascript-todo)
-   DataScript hangout (May 2014, in Russian): 返回文章页面 DataScript hangout:[video 视频](http://www.youtube.com/watch?v=jhBC81pczZY)

Projects using DataScript:

使用 DataScript 的项目:

-   [Roam Research 漫游研究](https://roamresearch.com/), a note-taking graph database 笔记图形数据库
-   [Athens 雅典](https://github.com/athensresearch/athens), a tool for networked thought 这是一个网络化思维的工具
-   [Precursor 前身](http://precursorapp.com/), collaborative prototyping tool 协作原型开发工具
-   [LightMesh](http://lightmesh.com/), datacenter management 、数据中心管理
-   [Cognician 认知学家](https://www.cognician.com/), coaching platform 、教练平台
-   [PartsBox](https://partsbox.io/), electronic parts management 、电子零部件管理
-   [I am Fy 我是 Fy](https://www.iamfy.co/), accessories e-shop ，配件电子商店
-   [Acha-acha 阿查 - 阿查](http://tonsky.me/blog/acha-acha/), GitHub achievements ，GitHub 成就
-   [Showkr](http://showkr.solovyov.net/), flickr gallery viewer ( 、 flickr gallery viewer ([sources 来源](https://github.com/piranha/showkr))
-   [Zetawar 女名女子名](http://www.zetawar.com/), turn-based tactical strategy game ，回合制战术策略游戏
-   [Lemmings 旅鼠](https://www.lemmings.io/), incubator focused on art & artificial intelligence ，孵化器专注于艺术和人工智能

Related projects:

相关项目:

-   [DataScript-Transit](https://github.com/tonsky/datascript-transit), transit serialization for database and datoms 、数据库和数据库的传输序列化
-   [Posh 时髦](https://github.com/mpdairy/posh), lib that lets you use a single DataScript db to store Reagent app state ，lib，它允许你使用一个单独的数据库来存储试剂应用程序状态
-   [re-posh 重新装修](https://github.com/denistakeda/re-posh), use re-frame with DataScript storage ，对数据脚本存储使用重新帧
-   [DataScript-mori](https://github.com/typeetfunc/datascript-mori), DataScript & Mori wrapper for use from JS ，DataScript & Mori 包装器，供 JS 使用
-   [DatSync](https://github.com/metasoarous/datsync), Datomic ↔︎ DataScript syncing/replication utilities ，Datomic something DataScript 同步 / 复制实用程序
-   [Intension 内涵](https://github.com/alandipert/intension), lib to convert associative structures to in-memory databases for querying them ，lib 将关联结构转换为内存中数据库，以便查询它们
-   [Datamaps](https://github.com/djjolicoeur/datamaps), lib designed to leverage datalog queries to query arbitrary maps. ，lib 被设计为利用数据记录查询来查询任意的映射

Demo applications:

演示应用程序:

-   [Localisation Demo with Om Next 使用 Om Next 进行本地化演示](http://simonb.com/blog/2016/01/24/om-next-datascript-localisation-demo/)
-   ToDo, task manager demo app (persistence via localStorage and transit, filtering, undo/redo): 任务管理器演示应用程序 (通过 localStorage 和 transit 进行持久化、过滤、撤销 / 恢复) :[sources 来源](https://github.com/tonsky/datascript-todo), [live 活着](http://tonsky.me/datascript-todo/)
-   CatChat, chat demo app: 聊天演示应用程序:[sources 来源](https://github.com/tonsky/datascript-chat), [code walkthrough 代码演练](http://tonsky.me/blog/datascript-chat/), [live 活着](http://tonsky.me/datascript-chat/)
-   clj-crud, demo CRUD app: Clj-CRUD 演示 CRUD 应用程序:[sources 来源](https://github.com/thegeez/clj-crud), [blog post 博客帖子](http://thegeez.net/2014/04/30/datascript_clojure_web_app.html)
-   [OmNext TodoMVC Ompnext TodoMVC](https://github.com/madvas/todomvc-omnext-datomic-datascript)

## Usage examples 使用例子

For more examples, see [our acceptance test suite](https://github.com/tonsky/datascript/blob/master/test/datascript/test).

有关更多示例，请参见我们的验收测试套件。

```clojure
(require '[datascript.core :as d])

;; Implicit join, multi-valued attribute

(let [schema {:aka {:db/cardinality :db.cardinality/many}}
      conn   (d/create-conn schema)]
  (d/transact! conn [ { :db/id -1
                        :name  "Maksim"
                        :age   45
                        :aka   ["Max Otto von Stierlitz", "Jack Ryan"] } ])
  (d/q '[ :find  ?n ?a
          :where [?e :aka "Max Otto von Stierlitz"]
                 [?e :name ?n]
                 [?e :age  ?a] ]
       @conn))

;; => #{ ["Maksim" 45] }


;; Destructuring, function call, predicate call, query over collection

(d/q '[ :find  ?k ?x
        :in    [[?k [?min ?max]] ...] ?range
        :where [(?range ?min ?max) [?x ...]]
               [(even? ?x)] ]
      { :a [1 7], :b [2 4] }
      range)

;; => #{ [:a 2] [:a 4] [:a 6] [:b 2] }


;; Recursive rule

(d/q '[ :find  ?u1 ?u2
        :in    $ %
        :where (follows ?u1 ?u2) ]
      [ [1 :follows 2]
        [2 :follows 3]
        [3 :follows 4] ]
     '[ [(follows ?e1 ?e2)
         [?e1 :follows ?e2]]
        [(follows ?e1 ?e2)
         [?e1 :follows ?t]
         (follows ?t ?e2)] ])

;; => #{ [1 2] [1 3] [1 4]
;;       [2 3] [2 4]
;;       [3 4] }


;; Aggregates

(d/q '[ :find ?color (max ?amount ?x) (min ?amount ?x)
        :in   [[?color ?x]] ?amount ]
     [[:red 10]  [:red 20] [:red 30] [:red 40] [:red 50]
      [:blue 7] [:blue 8]]
     3)

;; => [[:red  [30 40 50] [10 20 30]]
;;     [:blue [7 8] [7 8]]]
```

## Using from vanilla JS 使用 vanilla JS

DataScript can be used from any JS engine without additional dependencies:

可以在任何 JS 引擎中使用，不需要额外的依赖:

```html
<script src="https://github.com/tonsky/datascript/releases/download/1.0.3/datascript-1.0.3.min.js"></script>
```

or as a CommonJS module ([npm page](https://www.npmjs.org/package/datascript)):

或者作为 CommonJS 模块 (npm 页面) :

```
npm install datascript

```

```js
var ds = require('datascript');
```

or as a RequireJS module:

或者作为一个 RequireJS 模块:

```js
require(['datascript'], function(ds) { ... });
```

Queries:

查询:

-   Query and rules should be EDN passed as strings 查询和规则应以 EDN 作为字符串传递
-   Results of 调查结果`q` are returned as regular JS arrays 返回为常规 JS 数组

Entities:

实体:

-   Entities returned by 返还的实体`entity` call are lazy as in Clojure Call 和 Clojure 一样懒惰
-   Use 使用`e.get("prop")`, `e.get(":db/id")`, `e.db` to access entity properties 访问实体属性
-   Entities implement ECMAScript 6 Map interface (has/get/keys/...) 实体实现 ECMAScript 6 Map 接口 (has/get/keys/...)

Transactions:

交易:

-   Use strings such as 使用字符串，如`":db/id"`, `":db/add"`, etc. instead of db-namespaced keywords 代替 db 命名空间关键字
-   Use regular JS arrays and objects to pass data to 使用普通的 JS 数组和对象来传递数据`transact` and 及`db_with`

Transaction reports:

交易报告:

-   `report.tempids` has string keys ( 有字符串键 (`"-1"` for entity tempid 实体暴风雨`-1`), use )、使用`resolve_tempid` to set up a correspondence 建立一个通信

Check out [test/js/tests.js](https://github.com/tonsky/datascript/blob/master/test/js/tests.js) for usage examples.

查看 test/js/tests.js 中的使用示例。

## Project status 项目状况

Stable. Most of the features done, expecting non-breaking API additions and performance optimizations. No docs at the moment, use examples & [Datomic documentation](https://docs.datomic.com/on-prem/index.html#sec-3).

稳定。大多数特性都已经完成，期望不会出现破坏性的 API 添加和性能优化。目前没有文档，请使用示例和数据文档。

The following features are supported:

支持以下特性:

-   Database as a value: each DB is an immutable value. New DBs are created on top of old ones, but old ones stay perfectly valid too 数据库作为一个值: 每个 DB 都是一个不可变的值。新的数据库是在旧的数据库之上创建的，但是旧的数据库仍然是完全有效的
-   Triple store model 三重存储模式
-   EAVT, AEVT and AVET indexes Eevt、 AEVT 和 AVET 指数
-   Multi-valued attributes via 多值属性通过`:db/cardinality :db.cardinality/many`
-   Lazy entities and 懒惰的实体`:db/valueType :db.type/ref` auto-expansion 自动膨胀
-   Database “mutations” via 数据库 “突变” 通过`transact!`
-   Callback-based analogue to txReportQueue via 基于回调的 txReportQueue 模拟`listen!`
-   Direct index lookup and iteration via 通过直接索引查找和迭代`datoms` and 及`seek-datoms`
-   Filtered databases via 过滤的数据库`filter`
-   Lookup refs 查找文献
-   Unique constraints, upsert 独特的约束条件
-   Pull API (thx 拉出 API (thx[David Thomas Hume 大卫 · 托马斯 · 休谟](https://github.com/dthume))

Query engine features:

查询引擎功能:

-   Implicit joins 隐式连接
-   Query over DB or regular collections 对 DB 或常规集合的查询
-   Parameterized queries via 参数化查询通过`:in` clause 子句
-   Tuple, collection, relation binding forms in 中的元组、集合、关系绑定形式`:in` clause 子句
-   Query over multiple DB/collections 多个 DB / 集合的查询
-   Predicates and user functions in query 查询中的谓词和用户函数
-   Negation and disjunction 否定和分离
-   Rules, recursive rules 规则，递归规则
-   Aggregates 聚合体
-   Find specifications 查找规范

Interface differences:

界面差异:

-   Conn is just an atom storing last DB value, use Conn 只是存储最后一个 DB 值的原子`@conn` instead of 而不是`(d/db conn)`
-   Instead of 而不是`#db/id[:db.part/user -100]` just use 就用`-100` in place of 代替`:db/id` or entity id 或者实体 id
-   Transactor functions can be called as 事务处理器函数可以调用为`[:db.fn/call f args]` where 在哪里`f` is a function reference and will take db as first argument (thx 是一个函数引用，并将 db 作为第一个参数 (thx[@thegeez @ thegeez](https://github.com/thegeez))
-   In ClojureScript, custom query functions and aggregates should be passed as source instead of being referenced by symbol (due to lack of 在 ClojureScript 中，自定义查询函数和聚合应该作为源传递，而不是由符号引用 (由于缺少`resolve` in CLJS) 在 CLJS 中)
-   Custom aggregate functions are called via aggregate keyword: 通过聚合关键字调用自定义聚合函数:`:find (aggregate ?myfn ?e) :in $ ?myfn`
-   Additional 附加`:db.fn/retractAttribute` shortcut 捷径
-   Transactions are not annotated by default with 默认情况下，事务不使用`:db/txInstant`

Expected soon:

预计不久之后:

-   Better error reporting 更好的错误报告
-   Proper documentation 适当的文件

## Differences from Datomic 与数据集成电路的区别

-   DataScript is built totally from scratch and is not related by any means to the popular Clojure database Datomic 是完全从头开始构建的，与流行的 Clojure 数据库 Datomic 没有任何关系
-   Runs in a browser and/or in a JVM 在浏览器和 / 或 JVM 中运行
-   Simplified schema, not queryable 简化的模式，不可查询
-   Attributes do not have to be declared in advance. Put them to schema only when you need special behaviour from them 属性不必事先声明。只有当您需要它们的特殊行为时，才将它们放入模式
-   Any type can be used for values 任何类型都可以用于值
-   No 没有`:db/ident` attributes, keywords are 属性，关键字是_literally 字面上_ attribute values, no integer id behind them 属性值，后面没有整数 id
-   No schema migrations 没有模式迁移
-   No cache segments management, no laziness. Entire DB must reside in memory 没有缓存段管理，没有懒惰。整个 DB 必须驻留在内存中
-   No facilities to persist, transfer over the wire or sync DB with the server 没有任何工具可用于持久化、通过有线传输或与服务器同步 DB
-   No pluggable storage options, no full-text search, no partitions 没有可插入的存储选项，没有全文搜索，没有分区
-   No external dependencies 没有外部依赖
-   Free 免费

Aimed at interactive, long-living browser applications, DataScript DBs operate in constant space. If you do not add new entities, just update existing ones, or clean up database from time to time, memory consumption will be limited. This is unlike Datomic which keeps history of all changes, thus grows monotonically. DataScript does not track history by default, but you can do it via your own code if needed.

针对交互式、长寿命的浏览器应用程序，datascripdbs 在常数空间中运行。如果您不添加新的实体，只是更新现有的实体，或不时清理数据库，内存消耗将受到限制。这与数据集不同，数据集保存所有变化的历史，因此单调地增长。默认情况下，DataScript 不跟踪历史记录，但如果需要，可以通过自己的代码来跟踪。

Some of the features are omitted intentionally. Different apps have different needs in storing/transfering/keeping track of DB state. DataScript is a foundation to build exactly the right storage solution for your needs without selling too much “vision”.

有些特征是有意省略的。不同的应用程序在存储 / 传输 / 跟踪 DB 状态方面有不同的需求。DataScript 是一个基础，可以为您的需求构建正确的存储解决方案，而不需要出售太多的 “远景”。

## License 许可证

Copyright © 2014–2020 Nikita Prokopov

版权所有 2014-2020 Nikita Prokopov

Licensed under Eclipse Public License (see [LICENSE](https://github.com/tonsky/datascript/blob/master/LICENSE)).

根据 Eclipse 公共许可证许可证 (见许可证)。 
 [https://github.com/tonsky/datascript](https://github.com/tonsky/datascript)
