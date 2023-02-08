# MCQTSS Subscribe ToolBox Project Api接口文档

## 当前服务器域名:toolboxproject.api.nmsl.life
### 本文档中Python演示代码使用了`requests`作为HTTP请求模块,请先执行下面命令安装

``` python -m pip install requests ```
### 易语言演示代码使用了`精易模块`内的部分功能,请先导入`精易模块`([点我前往官网下载](https://ec.125.la/))
## ApiKey验证
### 此Api用于查看ApiKey状态
### 如是否存在,所属ToolBoxID,所属用户等
### 接口:`/api/open/apikey_verify`
### Python代码:
``` import requests

api_url = 'toolboxproject.api.nmsl.life'
ApiKey = '你的ApiKey'
# 推荐请求写法(POST)
resp = requests.post(url='http://{}/api/open/apikey_verify'.format(api_url),
                     data={'apikey': ApiKey})
# 请求方法2(GET)
# resp = requests.get(url='http://{}/api/open/apikey_verify?apikey={}'.format(api_url, ApiKey))
if resp.json()['code'] not in [0, 1]:
    print('访问接口时发送错误\n错误码:{}\n错误信息:{}'.format(resp.json()['code'], resp.json()['message']))
    exit()
if resp.json()['code'] == 0:
    print('ApiKey信息获取成功:\n所属用户名:{}\nToolBoxID:{}'.format(resp.json()['username'], resp.json()['toolbox_id']))
else:
    print('ApiKey不存在')
 ```
