# 对联数据集
Chinese Couplets Dataset. Some couplets that contain vulgar words are removed from this dataset. This dataset contains around 740,000 couplets.

此数据集基于[couplet-dataset](https://github.com/wb14123/couplet-dataset)的70w条数据集，在此基础上利用敏感词词库对数据进行了过滤，删除了低俗或敏感的内容，删除后剩余约74w条对联数据。

原有的70多万条数据集中包含了较多的低俗或敏感内容，不太适合商用场景。

如辱骂、低俗等内容：
```
神 经 病 净 神 神 净 病 
你 是 神 经 病 
妓 女 出 门 访 情 人 ， 来 时 万 福 ， 去 时 万 福
一 步 卧 槽 成 绝 杀 
```

又如政治话题内容：
```
美 日 躬 迎 胡 锦 涛 
```

# 数据下载（Download）

1. Clone the repository

    The data is at [./couplets](./couplets/).

2. Download at [here](https://github.com/v-zich/couplet-clean-dataset/releases/download/1.0.0/couplets.zip).


# 过滤说明
该数据集通过敏感词词库，删除了包含敏感词的内容。

查看使用的敏感词词库：[badwords.txt](./badwords.txt)

## 敏感词词库
为1到3个中文汉字的敏感词。

在[sensitive_words](https://github.com/qloog/sensitive_words)的基础上，筛选保留1到3个汉字的敏感词，并删除部分容易“误杀”的敏感词后构成。

在过滤时，有时候会“误杀”部分对联。

如过滤“月经”一词，既会过滤以下对联：

```
美 女 留 神 来 月 经 
月 经 乱 套 紧 张 人 
```

也会过滤以下对联：
```
古 月 经 商 路 路 通
岁 月 经 过 白 发 衰 
```

因此，在构建敏感词词库前，先做了统计分析，统计对联数据库中包含各个敏感词的对联数量。将包含对联数量大于某一个阈值的敏感词从词库中排除，如：

```
keyword:奥运 contain:424
keyword:国庆 contain:164 
keyword:民意 contain:241 
```

该方法无法确保精确筛选所有敏感词，但能确保大多数包含敏感内容的对联被删除，也尽可能小地“误杀”对联。