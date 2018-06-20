 # 订阅-K线行情
 ws://stagingqa.365os.com/kline-api/ws 
### 请求
#
```
{
   "event":"sub",
   "params":
      {
        "channel":"market_$base$quote_kline_[1min/5min/15min/30min/60min/1day/1week/1mo nth]",
        "cb_id":"自定义"
      }
}

```

#
### 返回订阅状态1次
```
{
    "event_rep":"subed",
    "channel":"market_$base$quote_kline_[1min/5min/15min/30min/60min/1day/1week/1month] ",
    "cb_id":"原路返回",
    "ts":1506584998239,
    "status":"ok"
}

```
#
### 持续返回订阅消息
```
{ 
    "channel":"market_$base$quote_kline_[1min/5min/15min/30min/60min/1day/1week/1month]",//订阅的交易对行情 $base$quote表示btckrw等 
    "ts":1506584998239,//请求时间 
    "tick":{  
              "id":1506602880,//时间刻度起始值  
              "amount":123.1221,//交易额  
              "vol":1212.12211,//交易量  
              "open":2233.22,//开盘价  
              "close":1221.11,//收盘价  
              "high":22322.22,//最高价  
              "low":2321.22//最低价 
            } 
  }

```

# 订阅-前24小时行情
ws://stagingqa.365os.com/kline-api/ws

### 请求
```
{
    "event":"sub",
    "params":{
                "channel":"market_$base$quote_ticker",
                "cb_id":"自定义"
            }
}

```

### 返回订阅状态1次
```
{
    "event_rep":"subed",
    "channel":"market_$base$quote_ticker",
    "cb_id":"原路返回",
    "ts":1506584998239,
    "status ":"ok"
}

```

### 持续返回订阅消息
```
{ 
    "channel":"market_$base$quote_ticker",//订阅的交易对行情$base$quote表示btckrw等 
    "ts":1506584998239,//请求时间 
    "tick":{  
               "id":1506584998,//冗余，无实际意义，时间戳  
               "amount":123.1221,//交易额  
               "vol":1212.12211,//交易量  
               "open":2233.22,//开盘价  
               "close":1221.11,//收盘价  
               "high":22322.22,//最高价  
               "low":2321.22,//最低价  
               "rose":-0.2922,//涨幅  
               "ts":1506584998239//数据产生时间 
             } 
 }
```


# 订阅-实时成交信息
ws://stagingqa.365os.com/kline-api/ws
### 请求
```
{
    "event":"sub",
    "params":{
                "channel":"market_$base$quote_trade_ticker",
                "cb_id":"自定义"
              }
}

```

#### 返回订阅状态1次
```
{
    "event_rep":"subed",
    "channel":"market_$base$quote_trade_ticker",
    "cb_id":"原路返回",
    "ts":1506584998239,
    " status":"ok"
}
```

#### 持续返回订阅消息
```
{ 
      "channel":"market_$base$quote_trade_ticker",//订阅的交易对行情$base$quote表示btckrw等 
      "ts":1506584998239,//请求时间 
      "tick":{  
          "id":12121,//data中最大交易ID  
          "ts":1506584998239,//data中最大时间  
          "data":[   
                    {    
                        "id":12121,//交易ID    
                        "side":"buy",//买卖方向buy,sell    
                        "price":32.233,//单价    
                        "vol":232,//数量    
                        "amount":323,//总额    
                        "ts":1506584998239,//数据产生时间    
                        "ds":'2017-09-10 23:12:21'   
                    },   
                    {    
                        "id":12120,//交易ID    
                        "side":"buy",//买卖方向buy,sell    
                        "price":32.233,//单价    
                        "vol":232,//数量    
                        "amount":323,//总额    
                        "ts":1506584998239,//数据产生时间    
                        "ds":'2017-09-10 23:12:21'   
                    }  
                ] 
          } 
}

```

# 订阅-深度盘口
ws://stagingqa.365os.com/kline-api/ws
### 请求
````
{
    "event":"sub",
    "params":{
                "channel":"market_$base$quote_depth_step[0-2]",
                "cb_id":"自定义",
                "asks":150,
                "bids":150
              }
}

````

###  返回订阅状态1次
```
{
   "event_rep":"subed",
   "channel":"market_$base$quote_depth_step[0-2]",
   "cb_id":"原路返回","asks":150,
   "bids" :150,
   "ts":1506584998239,
   "status":"ok"
}

```

### 持续返回订阅消息
```
{ 
   "channel":"market_$base$quote_depth_step[0-2]",//$base$quote表示btckrw等,深度有3个维度，0、1、2 
   "ts":1506584998239,//请求时间 
   "tick":{  
             "asks":[//卖盘   
                       {22112.22,0.9332},   
                       {22112.21,0.2},  
                    ],  
              "bids":[//买盘   
                        {22111.22,0.9332},   
                        {22111.21,0.2},  
                     ] 
           } 
 }

```

# 请求-K线历史数据
ws://stagingqa.365os.com/kline-api/ws
### 请求
```
{
    "event":"req",
    "params":{"channel":"market_$base$quote_kline_[1min/5min/15min/30min/60min/1day/1week/1mo nth]",
    "cb_id":"自定义",
    "since":"1506602880"}
}//since缺省时返回最新300条，有值时返回大于since的最多1小时 数据，since有强校验，不能早于当前1小时  since取到59

```

### 返回一次历史数据
```
{ 
    "event_rep":"rep",
    "channel":"market_$base$quote_kline_[1min/5min/15min/30min/60min/1day/1week/1month]", 
    "cb_id":"原路返回", 
    "since":"1506602880",//since缺省时返回最新300条，有值时返回大于since的最多1小时数据，since有强校验，不 能早于当前1小时                         "ts":1506584998239,//请求时间 
    "data":[//300条  
              {
                  "id":1506602880,//时间刻度起始值   
                  "amount":123.1221,//交易额   
                  "vol":1212.12211,//交易量   
                  "open":2233.22,//开盘价   
                  "close":1221.11,//收盘价   
                  "high":22322.22,//最高价   
                  "low":2321.22//最低价  
              },  
              {   
                   "id":1506602880,//时间刻度起始值   
                   "amount":123.1221,//交易额   
                   "vol":1212.12211,//交易量   
                   "open":2233.22,//开盘价   
                   "close":1221.11,//收盘价   
                   "high":22322.22,//最高价   
                   "low":2321.22//最低价  
                } 
            ] 
}

```

# 请求-成交历史数据
ws://stagingqa.365os.com/kline-api/ws
###  请求
```
{
   "event":"req",
   "params":{
               "channel":"market_$base$quote_trade_ticker",
               "cb_id":"自定义","top":200
            }
}

```

### 直接返回成交信息
```
{ 
   "event_rep":"rep",
   "channel":"market_$base$quote_trade_ticker",
   "cb_id":"原路返回",
   "ts":1506584998239,
   "st atus":"ok", 
   "top":200,//最大支持200 
   "data":[  
            {   
                "id":12121,//交易ID   
                "side":"buy",//买卖方向buy,sell   
                "price":32.233,//单价   
                "vol":232,//数量   
                "amount":323,//总额   
                "ts":1506584998239//数据产生时间  
            },  
            {   
                "id":12120,//交易ID   
                "side":"buy",//买卖方向buy,sell   
                "price":32.233,//单价   
                "vol":232,//数量   
                "amount":323,//总额   
                "ts":1506584998239,//数据产生时间   
                "ds":'2017-09-10 23:12:21'  
             } 
          ] 
 }

```
