# Benature/flomo: flomo.app 第三方 API
[![](https://raw.githubusercontent.com/Benature/flomo/main/flomo/media/logo-192x192.png)
](https://flomoapp.com/)

[![](https://camo.githubusercontent.com/3d4cb7f42468e8e9fa6160e038f78d43d3865c4dd6a71f15553100aaf15f2a57/68747470733a2f2f696d672e736869656c64732e696f2f707970692f762f666c6f6d6f)
](https://pypi.org/project/flomo/) [![](https://camo.githubusercontent.com/3572de9aa7a1419b00f4ad8c5df7e39a01fd6b03264e4f61bf1e242905a76881/68747470733a2f2f696d672e736869656c64732e696f2f707970692f707976657273696f6e732f666c6f6d6f)
](https://camo.githubusercontent.com/3572de9aa7a1419b00f4ad8c5df7e39a01fd6b03264e4f61bf1e242905a76881/68747470733a2f2f696d672e736869656c64732e696f2f707970692f707976657273696f6e732f666c6f6d6f) [![](https://camo.githubusercontent.com/2354c5dc55e2e858249ce87733b596497a5a1b11f610faabd46cd61dc02f5dc7/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f73746172732f42656e61747572652f666c6f6d6f)
](https://github.com/Benature/flomo)

一个非官方的 API python 玩具盒 （包括支持官方 API） 👀

> _prefer python3.7+_  
> 欢迎 Star 🌟、Fork 🍴、Issue 💬、PR. 一起让 flomo 用的更加得心应手

最新版在 dev 分支

## Usage 使用

```python
import flomo
client = flomo.Flomo(api='https://flomoapp.com/xxxxxAPIxxxx')
client.new('hello flomo')
```

相关 workflow 示例可参考 [flomo workflow](https://github.com/Benature/flomo-workflow)

```python
def get(self, tag=''):
    '''get all memo'''

def update(self, slug, content, file_ids=[], parent_memo_slug=None, source='web'):
    '''update a memo'''

def new(self, content, parent_memo_id=None, file_ids=[], source='web', method='api'):
    '''put a new memo
    @content: memo content
    @method: `api` or `cookies`, determine the method to send the new memo
    return response'''
```

## Relative Project 相关项目

-   workflow: [Benature/flomo workflow](https://github.com/Benature/flomo-workflow)
-   npm: [geekdada/flomo api helper](https://github.com/geekdada/flomo-api-helper) 
    [https://github.com/Benature/flomo](https://github.com/Benature/flomo)
