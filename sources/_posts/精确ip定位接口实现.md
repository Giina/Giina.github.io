---
title: 精确ip定位接口实现
tags:
  - 定位
  - ip
  - 接口
category: 功能实现
lang: zh
date: 2017-02-27 10:01:07
---

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
