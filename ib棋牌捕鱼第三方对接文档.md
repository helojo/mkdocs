
# 游戏介绍

待整理...
# 接口对接
接口全部由游戏方sdk服务器提供,渠道方通过post的方式主动请求
## 1 账号注册(方法：POST)
    请求地址: http://xxx.xxx.xxx/sdk/register?gameid=xxx&platid=xxx&sign=xxxxxxxxx

#### 参数说明
<table>
      <tr>
        <th>名称</td>
        <th>类型</td>
        <th>是否必填</td>
        <th>说明</td>
    </tr>
    <tr>
        <td>account</td>
        <td>string</td>
        <td>是</td>
        <td>账号</td>
    </tr>
    <tr>
        <td>password</td>
        <td>string</td>
        <td>是</td>
        <td>密码</td>
    </tr>
    <tr>
        <td>ip</td>
        <td>string</td>
        <td>否</td>
        <td>用户的ip地址</td>
    </tr>
    <tr>
        <td>username</td>
        <td>string</td>
        <td>是</td>
        <td>渠道用户昵称</td>
    </tr>
    <tr>
        <td>headimg</td>
        <td>string</td>
        <td>否</td>
        <td>渠道用户头像</td>
    </tr>
    <tr>
        <td>sex</td>
        <td>int</td>
        <td>否</td>
        <td>渠道用户性别(1男，2女，0未知)</td>
    </tr>
</table>

#### 返回说明
<table>
      <tr>
        <th>名称</td>
        <th>类型</td>
        <th>是否必填</td>
        <th>说明</td>
    </tr>
    <tr>
        <td>uid</td>
        <td>string</td>
        <td>是</td>
        <td>渠道用户ID或者账号</td>
    </tr>
    <tr>
        <td>status</td>
        <td>int</td>
        <td>是</td>
        <td>注册状态(200登录成功,其他登录失败)</td>
    </tr>
    <tr>
        <td>desc</td>
        <td>string</td>
        <td>否</td>
        <td>成功或失败描述</td>
    </tr>
</table>

***

## 2 用户登录

### 2.1 用户登录账号(方法：POST)
    请求地址: http://xxx.xxx.xxx/sdk/login?gameid=xxx&platid=xxx&sign=xxxxxxxxxx

#### 参数说明
<table>
      <tr>
        <th>名称</td>
        <th>类型</td>
        <th>是否必填</td>
        <th>说明</td>
    </tr>
    <tr>
        <td>account</td>
        <td>string</td>
        <td>是</td>
        <td>用户账号</td>
    </tr>
    <tr>
        <td>password</td>
        <td>string</td>
        <td>是</td>
        <td>账号密码</td>
    </tr>
    <tr>
        <td>ip</td>
        <td>string</td>
        <td>否</td>
        <td>用户的ip地址</td>
    </tr>
</table>

#### 返回说明
<table>
      <tr>
        <th>名称</td>
        <th>类型</td>
        <th>是否必填</td>
        <th>说明</td>
    </tr>
    <tr>
        <td>uid</td>
        <td>string</td>
        <td>是</td>
        <td>用户ID</td>
    </tr>
    <tr>
        <td>token</td>
        <td>string</td>
        <td>是</td>
        <td>后续兑换需要的凭证,有使用期限，过期无效</td>
    </tr>
    <tr>
        <td>gameurl</td>
        <td>string</td>
        <td>是</td>
        <td>游戏入口地址,当前用户专用的，不可给其他人使用,该地址有使用期限，过期后登陆不了游戏</td>
    </tr>
    <tr>
        <td>status</td>
        <td>int</td>
        <td>是</td>
        <td>登录状态(200登录成功,其他登录失败)</td>
    </tr>
    <tr>
        <td>desc</td>
        <td>string</td>
        <td>否</td>
        <td>成功或失败描述</td>
    </tr>
</table>

***

## 3 充值
### 3.1 兑入游戏币（方法：POST）
    请求地址:http://xxx.xxx.xxx/sdk/callback_redeemin?gameid=xxx&platid=xxx&sign=xxxxxxxxx
#### 参数说明
<table>
    <tr>
        <th>名称</td>
        <th>类型</td>
        <th>是否必填</td>
        <th>说明</td>
    </tr>
    <tr>
        <td>uid</td>
        <td>string</td>
        <td>是</td>
        <td>渠道用户ID或者账号</td>
    </tr>
    <tr>
        <td>token</td>
        <td>string</td>
        <td>是</td>
        <td>后续兑换需要的凭证,有使用期限，过期无效</td>
    </tr>
    <tr>
        <td>platorder</td>
        <td>string</td>
        <td>是</td>
        <td>订单号(渠道方订单号、流水号，最长32位唯一字符串)</td>
    </tr>
    <tr>
        <td>money</td>
        <td>int</td>
        <td>是</td>
        <td>订单金额(分)</td>
    </tr>
    <tr>
        <td>ts</td>
        <td>int</td>
        <td>是</td>
        <td>时间戳:秒</td>
    </tr>
</table>
#### 返回说明
<table>
    <tr>
        <th>名称</td>
        <th>类型</td>
        <th>是否必填</td>
        <th>说明</td>
    </tr>
    <tr>
        <td>status</td>
        <td>int</td>
        <td>是</td>
        <td>状态：200成功，其他失败</td>
    </tr>
    <tr>
        <td>desc</td>
        <td>string</td>
        <td>否</td>
        <td>成功或失败描述</td>
    </tr>
</table>

### 3.2 兑出游戏币(方法：POST)
    请求地址:http://xxx.xxx.xxx/sdk/callback_redeemout?gameid=xxx&platid=xxx&sign=xxxxxxxxx
#### 参数说明
<table>
      <tr>
        <th>名称</td>
        <th>类型</td>
        <th>是否必填</td>
        <th>说明</td>
    </tr>
    <tr>
        <td>uid</td>
        <td>string</td>
        <td>是</td>
        <td>渠道用户ID或者账号</td>
    </tr>
    <tr>
        <td>platorder</td>
        <td>string</td>
        <td>是</td>
        <td>订单号(渠道方订单号、流水号，最长32位唯一字符串)</td>
    </tr>
    <tr>
        <td>money</td>
        <td>int</td>
        <td>是</td>
        <td>订单金额(人民币分)</td>
    </tr>
    <tr>
        <td>token</td>
        <td>string</td>
        <td>是</td>
        <td>后续兑换需要的凭证,有使用期限，过期无效</td>
    </tr>
    <tr>
        <td>ts</td>
        <td>int</td>
        <td>是</td>
        <td>时间戳:秒</td>
    </tr>
</table>
#### 返回说明
<table>
    <tr>
        <th>名称</td>
        <th>类型</td>
        <th>是否必填</td>
        <th>说明</td>
    </tr>
    <tr>
        <td>status</td>
        <td>int</td>
        <td>是</td>
        <td>状态：200成功，其他失败</td>
    </tr>
    <tr>
        <td>desc</td>
        <td>string</td>
        <td>否</td>
        <td>成功或失败描述</td>
    </tr>
</table>

### 3.3 查询玩家当前能够兑换的余额(方法：POST)
    请求地址:http://xxx.xxx.xxx/sdk/callback_balance?gameid=xxx&platid=xxx&sign=xxxxxxxxxxxx
由渠道方提供,游戏收到兑出请求时调用该接口
#### 参数说明
<table>
    <tr>
        <th>名称</td>
        <th>类型</td>
        <th>是否必填</td>
        <th>说明</td>
    </tr>
    <tr>
        <td>uid</td>
        <td>string</td>
        <td>是</td>
        <td>渠道用户ID或者账号</td>
    </tr>
    <tr>
        <td>token</td>
        <td>string</td>
        <td>是</td>
        <td>后续兑换需要的凭证,有使用期限，过期无效</td>
    </tr>
    <tr>
        <td>ts</td>
        <td>int</td>
        <td>是</td>
        <td>时间戳:秒</td>
    </tr>
</table>

#### 返回说明
<table>
    <tr>
        <th>名称</td>
        <th>类型</td>
        <th>是否必填</td>
        <th>说明</td>
    </tr>
    <tr>
        <td>status</td>
        <td>int</td>
        <td>是</td>
        <td>充值确认返回状态码(200成功)</td>
    </tr>
    <tr>
        <td>desc</td>
        <td>string</td>
        <td>否</td>
        <td>描述</td>
    </tr>
    <tr>
        <td>uid</td>
        <td>string</td>
        <td>是</td>
        <td>渠道用户ID或者账号</td>
    </tr>
    <tr>
        <td>money</td>
        <td>int</td>
        <td>是</td>
        <td>订单金额(单位：分)</td>
    </tr>
</table>

***

## 4 查询接口
该接口提供游戏记录给渠道和子渠道方进行查询
### 4.1 查询地址(方法：POST)
    请求地址: http://xxx.xxx.xxx/sdk/callback_record?gameid=xxx&platid=xxx&sign=xxxxxxxxxx

#### 参数说明
<table>
    <tr>
        <th>名称</td>
        <th>类型</td>
        <th>是否必填</td>
        <th>说明</td>
    </tr>
    <tr>
        <td>account</td>
        <td>string</td>
        <td>是</td>
        <td>玩家登陆的账号(查询指定玩家才需要该参数)</td>
    </tr>
    <tr>
        <td>subplatid</td>
        <td>int</td>
        <td>是</td>
        <td>子渠道ID(没有子渠道ID的可以不填该参数)</td>
    </tr>
    <tr>
        <td>ts</td>
        <td>int</td>
        <td>是</td>
        <td>时间戳:秒</td>
    </tr>
</table>

#### 返回说明
<table>
    <tr>
        <th>名称</td>
        <th>类型</td>
        <th>是否必填</td>
        <th>说明</td>
    </tr>
    <tr>
        <td>status</td>
        <td>int</td>
        <td>是</td>
        <td>查询状态(200登录成功,其他失败)</td>
    </tr>
    <tr>
        <td>desc</td>
        <td>string</td>
        <td>否</td>
        <td>成功或失败描述</td>
    </tr>
    <tr>
        <td>uid</td>
        <td>string</td>
        <td>是</td>
        <td>用户账号</td>
    </tr>
    <tr>
        <td>nickname</td>
        <td>string</td>
        <td>是</td>
        <td>昵称</td>
    </tr>
    <tr>
        <td>platid</td>
        <td>int</td>
        <td>是</td>
        <td>渠道Id(通常跟分配给渠道的ID一样，除非拥有子渠道)</td>
    </tr>
    <tr>
        <td>sceneid</td>
        <td>int</td>
        <td>是</td>
        <td>场次id(1初级场,2中级场,3高级场)</td>
    </tr>
    <tr>
        <td>roomid</td>
        <td>int</td>
        <td>是</td>
        <td>房号</td>
    </tr>
    <tr>
        <td>bet</td>
        <td>int</td>
        <td>是</td>
        <td>投注</td>
    </tr>
    <tr>
        <td>payout</td>
        <td>int</td>
        <td>是</td>
        <td>派彩(派彩减去投注就是输赢)</td>
    </tr>
    <tr>
        <td>from</td>
        <td>int</td>
        <td>是</td>
        <td>开始时间戳</td>
    </tr>
    <tr>
        <td>to</td>
        <td>int</td>
        <td>是</td>
        <td>结束时间戳</td>
    </tr>
    <tr>
        <td>ip</td>
        <td>string</td>
        <td>否</td>
        <td>用户的ip地址</td>
    </tr>
</table>

***

### 签名说明：
注意：当前的所有接口都是POST方法，body要求是参数的json格式，并经过base64编码, sign计算是根据参数的json字符串计算的Md5值;
如，gameid=1, platid=1, key=adsadsdfgrtg(gameid, platid, key接入时我方会分配),注册账号：buyu，密码：123456，头像：https://ss0.bdstatic.com/a8773912b31bb051b3333f73307adab44aede052.jpg，昵称：buyu,性别：男，子渠道ID为0

参数的json格式为：
>{"account":"buyu","password":"123456","headimg":"https://ss0.bdstatic.com/a8773912b31bb051b3333f73307adab44aede052.jpg","sex":1,"username":"buyu","subplatid":0}

签名字符串则是：
>{"account":"buyu","password":"123456","headimg":"https://ss0.bdstatic.com/a8773912b31bb051b3333f73307adab44aede052.jpg","sex":1,"username":"buyu","subplatid":0}

签名结果是：
>8312a39b7df0a2a3c339d8b76b4eebff

post请求的body:
>eyJhY2NvdW50IjoiYnV5dSIsInBhc3N3b3JkIjoiMTIzNDU2IiwiaGVhZGltZyI6Imh0dHBzOi8v\nc3MwLmJkc3RhdGljLmNvbS9hODc3MzkxMmIzMWJiMDUxYjMzMzNmNzMzMDdhZGFiNDRhZWRlMDUy\nLmpwZyIsInNleCI6MSwidXNlcm5hbWUiOiJidXl1Iiwic3VicGxhdGlkIjowfQ==

url地址:
>http://xxx.xxx.xxx/sdk/register?gameid=1&platid=1&sign=8312a39b7df0a2a3c339d8b76b4eebff

最终的请求应该类似以下curl命令
>curl -vvv 'http://xxx.xxx.xxx/sdk/register?gameid=1&platid=1&sign=8312a39b7df0a2a3c339d8b76b4eebff' -d 'eyJhY2NvdW50IjoiYnV5dSIsInBhc3N3b3JkIjoiMTIzNDU2IiwiaGVhZGltZyI6Imh0dHBzOi8v\nc3MwLmJkc3RhdGljLmNvbS9hODc3MzkxMmIzMWJiMDUxYjMzMzNmNzMzMDdhZGFiNDRhZWRlMDUy\nLmpwZyIsInNleCI6MSwidXNlcm5hbWUiOiJidXl1Iiwic3VicGxhdGlkIjowfQ=='
