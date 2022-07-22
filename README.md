# 地址要素解析-NER任务

## 仓库内容

通过CCKS2021中NLP竞赛提供的数据集，构建**BiLSTM-CRF**模型，实现地址要素的解析

中文地址要素解析任务的目标即将一条地址分解为上述几个部分的详细标签，如：
```text
输入：浙江省杭州市余杭区五常街道文一西路969号淘宝城5号楼，放前台
输出：Province=浙江省 city=杭州市 district=余杭区 town=五常街道 road=文一西路road_number=969号 poi=淘宝城 house_number=5号楼 other=，放前台
```

## 题目背景
人类的活动离不开位置，从空间上可以表征为坐标，从文本上表征为通讯地址。通讯地址广泛存在于电商物流、政府登记、金融交通等领域。对通讯地址的分析、聚合服务已经是一项重要基础服务，支撑着诸多互联网场景，比如地图搜索、电商物流分析等。实际应用中，地址文本存在写法自由、缺省别名多、地域性强等特点，对地址的解析、归一和匹配等都造成困难。

地址要素任务解析，是CCKS2021和阿里举办的一个NLP比赛：[比赛地址](https://tianchi.aliyun.com/competition/entrance/531900/introduction)

地址是日常生活中一种重要的文本信息，诸多场景需要登记地址，如电商购物、外卖配送、人口普查、水电气开户等。常见的地址一般包含以下几类信息：

```text
行政区划信息，如省、市、县、乡镇信息;
路网信息，如路名，路号，道路设施等;
详细地址信息，如POI (兴趣点)、楼栋号、户室号等;
非地址信息，如补充说明，误输入等;
```
地址要素解析是将地址文本拆分成独立语义的要素，并对这些要素进行类型识别的过程。

目前中文地址领域缺少标准的评测和数据集，这个竞赛开放较大规模的标注语料.

**NOTICE: 比较好用，但是语料相对比较纯净，所以可能存在一定问题**

## 具体解析与实现过程

### TODO

## 执行顺序

将训练集命名为train.txt,验证集命名为test.txt,并将这两个文件置于./output/下

先执行data_pre_process.py文件，生成词缓存与标签缓存，实际上是保留唯一映射关系

然后根据标签缓存中的O的对应数字修改config文件中的LABEL_O_ID以及VOCAB_SIZE与TARGET_SIZE

接着执行train.py文件，模型会保存在./output/model/文件夹（如果没有就新建一下）下

执行validate.py文件即可通过验证集预估模型的泛化性能

最后通过predict.py文件可进行预测
