---
title: 精确ip定位调研
tags: ['ip定位','精确定位','调研','技术']
category: 技术
---
调研目标：高精度ip定位（精确到直辖市的各个区）
调研流程：搜索现有服务商 -> 试用服务 -> 生成报告
调研标准：服务质量（速度，稳定，客服反馈），服务价格，口碑

### 1. [百度高精度ip定位](http://bbs.lbsyun.baidu.com/forum.php?mod=viewthread&tid=123916&highlight=%E9%AB%98%E7%B2%BE%E5%BA%A6IP)

百度咨询回复内容：
> 因为这个接口能够在用户不知情的情况下获取用户的定位。会涉及到隐私，这块在国家政策上有些敏感。何时启用目前并没有排期，不好意思。

> 关于高精度IP定位服务，之前我们内部做了一些调整，目前已经不公开对外发布了。
但是会根据重点合作伙伴的需求情况，在签订合作协议，保证数据安全的基础之上，对外提供服务使用。
你们需要高精度IP定位服务，请问你们的具体使用场景是什么？每天的使用量级会是多少？

百度回复速度过慢，是否需要发送合作需求至相关邮箱？

### 2. [RTBAisa·IP地址区县级归属地](http://www.rtbasia.com/)

[测试API](http://wx.jcloud.com/market/api/10366)

18元/20000次，188元/30万次，5888元/5千万次


### 3. [IPIP.NET](https://www.ipip.net/price.html)

IP数据库区县级精度版价格为3.6万/年，[查看更多](https://www.ipip.net/price.html#ip_district)
且说明中建议配合地级市IP数据库联合使用。
客户服务较广。

### 4. [互联网IP地理信息标准库](http://iac-i.org/)

 * A类： 基础IP库15,000元/年；
 * B类：
    * 移动IP库：10,000元/年
    * 区县IP库：10,000元/年
    * 高校IP库：5,000元/年
    
根据需求，年费为2.5万元/年不限次数使用


### 总结

根据网站首页省市定位的需求，建议使用2号服务。


### 精确IP定位的实现
从一个前端的角度想要实现精准IP定位，调用接口的时候势必会暴露自己的APPKey。等我发现这一点的时候我的APPKey其实已经暴露了好几个月，有点庆幸没有人抱着恶意访问网站。因此，精准IP定位的接口工作交给了后端的同事，API说明文档如下：

> ip_location:
>
> 直辖市请求接口： https://way.jd.com/RTBAsia/ip_district?ip=查询的IP地址&appkey=RTBAisa购买所得APPKey
接口说明文档地址：https://wx.jcloud.com/market/api/10366
注意：该地区返回行政区号需要查询行政区号字典，在浏览器中访问https://way.jd.com/RTBAsia/dictionary_district?appkey=c25bfe7445f025e295f73668687051cc 改地址能够得到字典内容，该接口说明文档为https://wx.jcloud.com/market/datas/18/10367

> 一般地址请求接口： http://restapi.amap.com/v3/ip?key=高德地图创建的接口APPKey&ip=查询的IP地址
接口说明文档地址：http://lbs.amap.com/api/webservice/guide/api/ipconfig/#ip

> 接口返回结果参数说明：

| 名称	| 类型	| 示例值	| 描述 |
| -----|----|----|----|
| province	| string	| ‘浙江省’/‘上海市’	| 省份/直辖市名称 |
| city	| string	| ‘杭州市’/‘杨浦区’	| 城市/区域名称 |
| isMunicipality	| boolean	| True / False	| 是否是直辖市 |
| status	| int	| 返回结果状态值	| 值为0或1,0表示失败；1表示成功 |
| info	| string	| 返回状态说明	| 返回状态说明，status为0时，info返回错误原因，否则返回“OK”。 |
