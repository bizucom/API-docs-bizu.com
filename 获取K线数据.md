# /open/api/get_records 获取K线数据
## 该接口不进行签名校验
<table>
    <tr><td colspan="3">/open/api/get_records(get)：获取K线数据</td></tr>
    <tr><td>参数</td><td>填写类型</td><td>说明</td></tr>
    <tr><td>symbol</td><td>必填</td><td>市场标记，bchbtc，详情看下面</td></tr>
    <tr><td>period</td><td>必填</td><td>单位为分钟，比喻1分钟则为1，一天则为1440</td></tr>
</table>

|虚拟币编号|xxx-cny|xxx-btc|xxx-usdt|
|----|:----:|:-----:|-----:|
|bch|bcccny|bchbtc|bchusdt|
|btc|btccny|-|btcusdt|
|etc |etccny |etcbtc|etcusdt|
|eth |ethcny |ethbtc|ethusdt|
|ltc|ltccny|ltcbtc |ltcusdt|

<table>
    <tr><td colspan="3">返回</td></tr>
    <tr><td>字段</td><td>实例</td><td>解释</td></tr>
    <tr><td>code</td><td>0</td><td></td></tr>
    <tr><td>msg</td><td>"suc"</td><td>code>0失败</td></tr>
    <tr><td>data</td><td>如下：</td></tr>
 </table>
  
```
[
   [
     1514445780, //时间戳
     1.12, //开盘价
     1.12, //最高
     1.12, //最低
     1.12, //收盘价
     0 //成交量
   ],
   [
     1514445840,
     1.12,
     1.12,
     1.12,
     1.12,
     0
   ],
   [
     1514445900,
     1.12,
     1.12,
     1.12,
     1.12,
     0
   ]
]
```
