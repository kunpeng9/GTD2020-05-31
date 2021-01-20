# sync-settings
#### [sync-settings 同步设置](/packages/sync-settings)

Synchronize package settings, keymap and installed packages 同步包设置、 keymap 和已安装的包

-   [#settings # 设置](/packages/search?utf8=✓&q=keyword:settings "Keyword: #settings")
-   [#productivity # 生产力](/packages/search?utf8=✓&q=keyword:productivity "Keyword: #productivity")
-   [#manager # 管理者](/packages/search?utf8=✓&q=keyword:manager "Keyword: #manager")
-   [#sync # sync](/packages/search?utf8=✓&q=keyword:sync "Keyword: #sync")
-   [#backup # 备份](/packages/search?utf8=✓&q=keyword:backup "Keyword: #backup")

    [![](https://github.com/atom-community.png)](/users/atom-community) [ atom-community  原子群落](/users/atom-community)

650,480

[](/packages/sync-settings/star)[1415](/packages/sync-settings/stargazers)

[Install 安装](atom://settings-view/show-package?package=sync-settings)

#### Launching Atom...

#### 发射原子弹..

If nothing happens, [download Atom](/) and try again.

如果什么都没有发生，请下载 Atom 并重试。

-   [Repo 回购](https://github.com/atom-community/sync-settings)
-   [Bugs 虫子](https://github.com/atom-community/sync-settings/issues)
-   [Versions 版本](https://github.com/atom-community/sync-settings/releases)
-   [License 许可证](https://github.com/atom-community/sync-settings/blob/ee64991ac258c9465c0c1dbd15dd84f0cacc63e4/LICENSE.md)

[Flag as spam or malicious 标记为垃圾邮件或恶意邮件](#flag-modal)

# [](#sync-settings-for-atom)Sync Settings for Atom Atom 的同步设置

![](https://i.github-camo.com/983b2dde4539744f8c1da305743f28e8e9c476cb/68747470733a2f2f6769746875622e636f6d2f61746f6d2d636f6d6d756e6974792f73796e632d73657474696e67732f776f726b666c6f77732f43492f62616467652e737667)

Synchronize settings, keymaps, user styles, init script, snippets and installed packages across [Atom](https://atom.io) instances.

跨 Atom 实例同步设置、键图、用户样式、 init 脚本、代码段和安装的包。

## [](#features)Features 功能

-   Sync Atom's and package settings 同步 Atom 和包的设置
-   Sync installed packages 同步安装的软件包
-   Sync user keymaps 同步用户键盘地图
-   Sync user styles 同步用户样式
-   Sync user init script 同步用户 init 脚本
-   Sync snippets 同步片段
-   Sync user defined text files 同步用户定义的文本文件

## [](#installation)Installation 安装

`$ apm install sync-settings` or using the Install button from [Atom.io](https://atom.io/packages/sync-settings).

$apm 安装同步设置或使用 Atom.io 中的安装按钮。

## [](#backup-locations)Backup locations 备份位置

By default your backup will be stored in a [gist](https://gist.github.com), but you may also install [other location packages](https://atom.io/packages/search?q=sync-settings+location).

默认情况下，你的备份将被保存在一个大意中，但是你也可以安装其他位置软件包。

Some other locations:

其他地点:

-   Local Folder: 本地文件夹:[sync-settings-folder-location 同步 - 设置 - 文件夹 - 位置](https://atom.io/packages/sync-settings-folder-location)
-   Git Repo: [sync-settings-git-location 同步 - 设置 - git-location](https://atom.io/packages/sync-settings-git-location)

### [](#gist-setup)Gist Setup

1.  Open 打开**Sync Settings 同步设置** configuration in 配置 Atom Settings 原子设置.
2.  Create a 创建一个[new personal access token 新的个人访问令牌](https://github.com/settings/tokens/new?scopes=gist) which has the 这里有`gist` scope and be sure to 一定要瞄准**activate permissions 激活许可**: Gist -> create gists. : 摘要 -> 创建要点
3.  Copy the access token to 将访问令牌复制到**Sync Settings 同步设置** configuration or set it as an environmental variable 配置或设置它作为环境变量**GITHUB_TOKEN 令牌**.
4.  Create a 创建一个[new gist 新的要点](https://gist.github.com/):

-   The description can be left empty. It will be set when invoking the 描述可以保持为空。调用`backup` command the first time. 第一次命令
-   Use 使用`packages.json` as the filename. 作为文件名
-   Put some arbitrary non-empty content into the file. It will be overwritten by the first invocation of the 将一些任意的非空内容放入文件中`backup` command 命令
-   Save the gist. 保存要点

5.  Copy the gist id (last part of url after the username) to 将 gist id (url 后面的最后一部分) 复制到**Sync Settings 同步设置** configuration or set it as an environmental variable 配置或设置它作为环境变量**GIST_ID 2010 年 10 月 11 日**.

Disclaimer: GitHub Gists are by default **public**. If you don't want other people to easily find your gist (i.e. if you use certain packages, storing auth-tokens, a malicious party could abuse them), you should make sure to **create a secret gist**.

免责声明: GitHub Gists 默认是公共的。如果你不想让其他人轻易找到你的要点 (例如，如果你使用某些软件包，存储授权令牌，恶意方可能会滥用它们) ，你应该确保创建一个秘密要点。

#### [](#alternative-sync-settings-configuration-using-atoms-configcson)Alternative 替代品**Sync Settings 同步设置** configuration using Atom's config.cson

1.  Click on Menu "Open Your Config" to edit Atom's config.cson
2.  Use these keys: 使用这些按键:


```


"sync-settings":

    gistId:"b3025...88c41c"

    personalAccessToken:"6a10cc207b....7a67e871"


```

#### [](#cloning-a-backup-to-a-fresh-atom-install)Cloning a backup to a fresh Atom install 克隆新安装 Atom 的备份

1.  Install the package from the command line: 从命令行安装软件包:`apm install sync-settings`
2.  Launch Atom passing in 发射原子进入**GITHUB_TOKEN 2.1.1.1.1.2.1.2.2.2.2.2.2.3.2.3.3.2.3.3.3.3.3.3.3.3.3.1** and 及**GIST_ID 2010 年 10 月 11 日**. For example: 。例如:


```
GITHUB_TOKEN=6a10cc207b....7a67e871 GIST_ID=b3025...88c41c atom

```

1.  You will still need to make sure you add your gist id and github token to the 您仍然需要确保将您的 gist id 和 github 标记添加到**Sync Settings 同步设置** configuration in 配置 Atom Settings 原子设置 OR set them as environment variables in your shell configuration. 或者将它们设置为 shell 配置中的环境变量

## [](#usage)Usage 用法

Open the Atom [Command Palette](https://github.com/atom/command-palette) where you can search for the following list of commands.

打开 Atom Command Palette，在其中可以搜索以下命令列表。

Backup or restore all settings from the Packages menu or use one of the following **commands**:

从软件包菜单中备份或恢复所有设置，或使用以下命令之一:

-   `sync-settings:backup`
-   `sync-settings:restore`

View your online backup using the following command:

使用以下命令查看联机备份:

-   `sync-settings:view-backup`

Check the latest backup is applied:

检查是否应用了最新备份:

-   `sync-settings:check-backup`

You can also fork existing settings from a different GitHub user using the following command:

你也可以使用以下命令从不同的 GitHub 用户那里获取现有的设置:

-   `sync-settings:fork`
-   In the following input field enter the Gist ID to fork 在下面的输入字段中输入 Gist ID to fork

Create a new backup:

创建一个新的备份:

-   `sync-settings:create-backup`

Delete the current backup:

删除当前备份:

-   `sync-settings:delete-backup`

## [](#running-the-tests)Running the tests 运行测试

1.  Create a new 创建一个新的[personal access token 个人存取令牌](https://github.com/settings/tokens/new) which has the 这里有`gist` scope and will be used for testing purposes. 并将用于测试目的
2.  Export it with 输出`export GITHUB_TOKEN=YOUR_TOKEN`
3.  Run 快跑`apm test`

## [](#contributing)Contributing 贡献

If you're going to submit a pull request, please try to follow [the official contribution guidelines of Atom](https://flight-manual.atom.io/hacking-atom/sections/contributing-to-official-atom-packages/).

如果你要提交一个请求，请尝试遵循 Atom 的官方贡献准则。

1.  [Fork it 用叉子叉](https://github.com/atom-community/sync-settings/).
2.  Create your feature branch ( 创建您的功能分支 (`git checkout -b my-new-feature`).
3.  Ensure tests are passing. See 确保测试通过。参见[running-the-tests 运行测试](https://github.com/atom-community/sync-settings#running-the-tests).
4.  Commit your changes ( 提交您的变更 (`git commit -am 'Add some feature'`).
5.  Push to the branch ( 推到树枝上 (`git push origin my-new-feature`).
6.  Create new Pull Request. 创建新的拉请求

[See all contributors](https://github.com/atom-community/sync-settings/graphs/contributors).

查看所有贡献者。

## [](#location-service)Location Service 位置服务

Packages can provide a location service using Atom's [Service's API](https://flight-manual.atom.io/behind-atom/sections/interacting-with-other-packages-via-services/)

包可以使用 Atom 的 Service 的 API 提供位置服务

### [](#example)Example: 例子:

Add the keywords `sync-settings` and `location` and add the `providedServices` property to your `package.json` file.

添加关键字 sync-settings 和 location，并将 providedServices 属性添加到 package.json 文件中。

```


// package.json

  ...

"main": "./main.js",

  ...

"keywords": \[

...

"sync-settings",

"location"

\],

  ...

"providedServices": {

"sync-settings-location":{

"versions":{

"1.0.0":"provideLocationService"

}

}

},

  ...


```

Then add the `provideLocationService` function to your `main.js` file (where your `activate` function is for Atom to activate your package)

然后将 provideLocationService 函数添加到 main.js 文件中 (其中的 activate 函数用于 Atom 激活包)

```


// main.js

...

activate(){

...

},

provideLocationService(){

returnrequire('./locationService.js')

},

...


```

Return an object that provides the functions for your service.

返回一个为您的服务提供函数的对象。

```


// locationService.js

module.exports\={

/\*\*

   \* Get URL for the backup

   \* @return{string}Backup URL. Return null if no URL exists

\*/

asyncgetUrl(){

...

},

/\*\*

   \* Create new backup location

   \* @return{Object}Returns empty object on success. Falsey value on silent error

\*/

asynccreate(){

...

},

/\*\*

   \* Get backup files and time

   \* @return{Object}Returns object with \`files\` and \`time\` on success. Falsey value on silent error

\*/

asyncget(){

...

return{

      files:{

'filename.txt':{

          content:'...'

}

},

      time:newDate().toISOString(),// ISO string, (e.g. 2020-01-01T00:00:00.000Z)

}

},

/\*\*

   \* Delete backup

   \* @return{Object}Returns empty object on success. Falsey value on silent error

\*/

asyncdelete(){

...

},

/\*\*

   \* Update backup and get time

   \* @param{Object}filesFiles to update

   \* @return{Object}Returns object with \`time\` on success. Falsey value on silent error

\*/

asyncupdate(files){

...

return{

      time:newDate().toISOString(),

}

},

/\*\*

   \* Fork backup

   \* @return{Object}Returns empty object on success. Falsey value on silent error

\*/

asyncfork(){

...

},

}


```

 [https://atom.io/packages/sync-settings](https://atom.io/packages/sync-settings)
