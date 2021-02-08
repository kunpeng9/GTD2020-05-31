# Mayandev/flomo-cli: 为 flomo 灵感笔记提供的命令行工具
[![](https://camo.githubusercontent.com/aa964d1e352156160b52f2aff5c08fc5378d80628a5a589531751109333cf3cb/68747470733a2f2f6d6179616e6465762e6f73732d636e2d68616e677a686f752e616c6979756e63732e636f6d2f755069632f666c6f6d6f2d636c692e706e67)
](https://camo.githubusercontent.com/aa964d1e352156160b52f2aff5c08fc5378d80628a5a589531751109333cf3cb/68747470733a2f2f6d6179616e6465762e6f73732d636e2d68616e677a686f752e616c6979756e63732e636f6d2f755069632f666c6f6d6f2d636c692e706e67)

# [](#flomo-cli)flomo-cli

为 [flomo 灵感笔记](https://flomoapp.com/)提供的命令行工具

## [](#install)Install

```shell
$ npm install flomo-cli -g
# or yarn
$ yarn global add flomo-cli
```

![](https://raw.githubusercontent.com/kunpeng9/PicgoPicture2020-10-18/master/20210208214810.png)

Command 'yarn' not found, but can be installed with：
sudo apt install cmdtest
 提示我没有安装yarn 
 
## [](#usage)Usage

[![](https://camo.githubusercontent.com/9e22dde56dc7bede87590de7376db250b9f2705197f6ae25e7ae976d88cd1f0d/68747470733a2f2f6d6179616e6465762e6f73732d636e2d68616e677a686f752e616c6979756e63732e636f6d2f755069632f666c6f6d6f2e706e67)
](https://camo.githubusercontent.com/9e22dde56dc7bede87590de7376db250b9f2705197f6ae25e7ae976d88cd1f0d/68747470733a2f2f6d6179616e6465762e6f73732d636e2d68616e677a686f752e616c6979756e63732e636f6d2f755069632f666c6f6d6f2e706e67)

### [](#normal)Normal

```shell
$ flomo '#tag This is a flow momery from flomo-cli with hash tag.'
```

普通模式下，默认将命令后的字符串内容上传到 flomo 到服务器。

### [](#editor)Editor

```shell
$ flomo edit
```

工具提供编辑器模式，输入 `flomo edit` 启动。

[![](https://camo.githubusercontent.com/139170d9be18b04ac6d95dd6a3e1df3043089cb7d16f98f06abaee6d9ad47618/68747470733a2f2f6d6179616e6465762e6f73732d636e2d68616e677a686f752e616c6979756e63732e636f6d2f755069632f6769746875622d666c6f6d6f2d636c692d6769662e676966)
](https://camo.githubusercontent.com/139170d9be18b04ac6d95dd6a3e1df3043089cb7d16f98f06abaee6d9ad47618/68747470733a2f2f6d6179616e6465762e6f73732d636e2d68616e677a686f752e616c6979756e63732e636f6d2f755069632f6769746875622d666c6f6d6f2d636c692d6769662e676966)

[![](https://camo.githubusercontent.com/5346e12513429255ac1bacd58992d0429ea4cce94e18c7698fafb6dcf6253386/68747470733a2f2f6d6179616e6465762e6f73732d636e2d68616e677a686f752e616c6979756e63732e636f6d2f755069632f696d6167652d32303231303131383130353135393834362e706e67)
](https://camo.githubusercontent.com/5346e12513429255ac1bacd58992d0429ea4cce94e18c7698fafb6dcf6253386/68747470733a2f2f6d6179616e6465762e6f73732d636e2d68616e677a686f752e616c6979756e63732e636f6d2f755069632f696d6167652d32303231303131383130353135393834362e706e67)

### [](#config)Config

如果你在 flomo 的设置里更换了 api，可以使用 `flomo config` 命令，重新设置 api 链接。

```shell
$ flomo config
```

## [](#reference)Reference

本工具由 [cli-template](https://github.com/Mayandev/cli-template) 提供支持。 
 [https://github.com/Mayandev/flomo-cli](https://github.com/Mayandev/flomo-cli)
