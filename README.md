# BiZu openApi

## 目录
- [/open/api/all_order-获取全部委托](https://github.com/bizukex/API-docs/blob/master/%E8%8E%B7%E5%8F%96%E5%85%A8%E9%83%A8%E5%A7%94%E6%89%98.md)

- [/open/api/all_trade-获取全部成交记录](https://github.com/bizukex/API-docs/blob/master/%E8%8E%B7%E5%8F%96%E5%85%A8%E9%83%A8%E6%88%90%E4%BA%A4%E8%AE%B0%E5%BD%95.md)

- [/open/api/cancel_order-取消委托单](https://github.com/bizukex/API-docs/blob/master/%E5%8F%96%E6%B6%88%E5%A7%94%E6%89%98%E5%8D%95.md)

- [/open/api/common/symbols 查询系统支持的所有交易对及精度](https://github.com/bizukex/API-docs/blob/master/%E6%9F%A5%E8%AF%A2%E7%B3%BB%E7%BB%9F%E6%94%AF%E6%8C%81%E7%9A%84%E6%89%80%E6%9C%89%E4%BA%A4%E6%98%93%E5%AF%B9%E5%8F%8A%E7%B2%BE%E5%BA%A6.md)

- [/open/api/create_order-创建订单](https://github.com/bizukex/API-docs/blob/master/%E5%88%9B%E5%BB%BA%E8%AE%A2%E5%8D%95.md)

- [/open/api/get_records 获取K线数据](https://github.com/bizukex/API-docs/blob/master/%E8%8E%B7%E5%8F%96K%E7%BA%BF%E6%95%B0%E6%8D%AE.md)

- [/open/api/get_ticker 获取当前行情](https://github.com/bizukex/API-docs/blob/master/%E8%8E%B7%E5%8F%96%E5%BD%93%E5%89%8D%E8%A1%8C%E6%83%85.md)

- [ /open/api/get_trades 获取行情成交记录](https://github.com/bizukex/API-docs/blob/master/%E8%8E%B7%E5%8F%96%E8%A1%8C%E6%83%85%E6%88%90%E4%BA%A4%E8%AE%B0%E5%BD%95.md)

- [/open/api/market_dept 查询买卖盘深度](https://github.com/bizukex/API-docs/blob/master/%E6%9F%A5%E8%AF%A2%E4%B9%B0%E5%8D%96%E7%9B%98%E6%B7%B1%E5%BA%A6.md)

- [/open/api/market-获取各个币对的最新成交价](https://github.com/bizukex/API-docs/blob/master/%E8%8E%B7%E5%8F%96%E5%90%84%E4%B8%AA%E5%B8%81%E5%AF%B9%E7%9A%84%E6%9C%80%E6%96%B0%E6%88%90%E4%BA%A4%E4%BB%B7.md)

- [/open/api/new_order-获取当前委托](https://github.com/bizukex/API-docs/blob/master/%E8%8E%B7%E5%8F%96%E5%BD%93%E5%89%8D%E5%A7%94%E6%89%98.md)

- [/open/api/order_info-获取订单详情](https://github.com/bizukex/API-docs/blob/master/%E8%8E%B7%E5%8F%96%E8%AE%A2%E5%8D%95%E8%AF%A6%E6%83%85.md)

- [/open/api/user/account-资产余额](https://github.com/bizukex/API-docs/blob/master/%E8%B5%84%E4%BA%A7%E4%BD%99%E9%A2%9D.md)

- hanxun api（暂定方案，有异议请及时沟通修改）The tentative plan, if there is any objection, please communicate in time

- sanweidu特殊接口（需要超管权限）

##  通用规则

1.  签名： <br>
请求参数按照字典排序，然后以keyvalue的形式拼接成字符串string，最后sign=MD5(string+secretKey)。注意：如果请求参数中value为NULL的 情况，则在拼接字符串时不计入签名字符串。<br>
例如： <br>
参数如下： <br>
```
{
      country = 86; 
      mobile = 15882133579;
      password = 654321zz;
      time = 1516007245;
}
```
拼接完成后：
```
string = country86mobile15882133579password654321zztime1516007278
sign=MD5(string+secretKey)
```

2 .  post请求参数采用表单格式提交数据
      content-type:application/x-www-form-urlencoded
<br/>
3. 错误码 
| 错误码 | 说明 | 备注 |
| ----- | :------: | -------: |
| 0 | 成功 |  |
| 5 | 下单失败 |  |
| 6 | 数量小于最小值 |  |
| 7 | 数量大于最大值 | |
| 8 | 订单取消失败 | |
| 9 | 交易被冻结 |  |
| 13 | 对不起，程序出现系统错误 ，请和网站管理员联系|  |
| 19 | 可用余额不足 |  |
| 22 | 订单不存在 |  |
| 23 | 缺少交易数量参数 |  |
| 24 | 缺少交易价格参数 |  |
| 100001 | 系统异常 |  |
| 100002 | 系统升级 |  |
| 100004 | 请求参数不合法 |  |
| 100005 | 参数签名错误 |  |
| 100007 | 非法IP |  |
| 110002 | 未知的货币代号 |  |
| 110003 | 资金密码错误 |  |
| 110004 | 提现被冻结 |  |
| 110005 | 可用余额不足 |  |
| 110020  | 用户名不存在 |  |
| 110023  | 手机号已注册 |  |
| 110024 | 邮箱已注册 |  |
| 110025 | 帐户被后台管理员锁定 |  |
| 110032 | 该用户无权限进行此操作 |  |
| 110033 | 充值失败 |  |
| 110034 | 提现失败 |  |

