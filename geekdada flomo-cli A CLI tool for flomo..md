# geekdada/flomo-cli: A CLI tool for flomo.
# [](#flomo-cli)flomo-cli

[![](https://github.com/geekdada/flomo-cli/workflows/Go/badge.svg)
](https://github.com/geekdada/flomo-cli/workflows/Go/badge.svg) [![](https://camo.githubusercontent.com/61763771db04027910d54e5e01bb1785319149d215b74c24938aab0e78716a34/68747470733a2f2f636f6465636f762e696f2f67682f6765656b646164612f666c6f6d6f2d636c692f6272616e63682f6d61737465722f67726170682f62616467652e7376673f746f6b656e3d464a3359325a42385953)
](https://codecov.io/gh/geekdada/flomo-cli)

A CLI tool for [flomo](https://flomoapp.com/register2/?Mzk3).

## [](#-安装)📥 安装

```shell
# 支持在不同平台运行
curl -sf https://gobinaries.com/geekdada/flomo-cli | sh
```

**或者** 在 [Releases](https://github.com/geekdada/flomo-cli/releases) 页面下载对应的二进制文件。目前有：

-   `flomo-cli-darwin-amd64.gz`
-   `flomo-cli-freebsd-386.gz`
-   `flomo-cli-freebsd-amd64.gz`
-   `flomo-cli-linux-386.gz`
-   `flomo-cli-linux-amd64.gz`
-   `flomo-cli-linux-armv5.gz`
-   `flomo-cli-linux-armv6.gz`
-   `flomo-cli-linux-armv7.gz`
-   `flomo-cli-linux-armv8.gz`
-   `flomo-cli-windows-386.zip`
-   `flomo-cli-windows-amd64.zip`
-   `flomo-cli-windows-arm32v7.zip`

macOS 系统请使用 `flomo-cli-darwin-amd64.gz`。

## [](#-使用)👉 使用

### [](#添加一条新的墨)添加一条新的墨

```shell
$ flomo-cli new --api <YOUR_API> "一条新的墨"
```

### [](#添加一条带标签的墨)添加一条带标签的墨

```shell
$ flomo-cli new --api <YOUR_API> --tag "随手记" "一条新的墨"
```

**🔮 效果**

[![](https://camo.githubusercontent.com/eb776ae4cb2016229fc750d54a3d4bb205c4bab24b7423e8ec8a06a183f9f1c4/68747470733a2f2f692e6c6f6c692e6e65742f323032302f31322f32342f67337637633666774f4b79617552542e706e67)
](https://camo.githubusercontent.com/eb776ae4cb2016229fc750d54a3d4bb205c4bab24b7423e8ec8a06a183f9f1c4/68747470733a2f2f692e6c6f6c692e6e65742f323032302f31322f32342f67337637633666774f4b79617552542e706e67)

### [](#使用环境变量来指定-api)使用环境变量来指定 API

```shell
$ export FLOMO_API=<YOUR_API>
$ flomo-cli new --tag "随手记" "一条新的墨"
```

### [](#将文本文件添加到浮墨)将文本文件添加到浮墨

```shell
$ cat memo.txt | flomo-cli new --tag "Quote"
```

## [](#licence)LICENCE

[MIT](/geekdada/flomo-cli/blob/master/LICENSE) 
 [https://github.com/geekdada/flomo-cli](https://github.com/geekdada/flomo-cli)
