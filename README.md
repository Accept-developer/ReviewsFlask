# ReviewsFlask
Graduation project.
基于Scrapy+Flask+ECharts+Jieba的亚马逊平台商品评价获取分析系统
数据库文件 reviews.sql
## 系统的整体功能分为三个模块：
1. 其中数据采集模块主要是基于Scrapy框架按照Xpath规则对指定URL地址爬取需求信息，
包括评价标题，用户名称，评价时间，评价内容，评分和下一页的URL地址，当其不为空时重复按照上述规则进行数据采集，
并结合MySQL存储实现数据持久化。
2. 数据分析模块主要是利用Jieba分词对评价详情内容进行词频分析，使用经过LSTM训练得到的模型进行情感分析。
3. 展示模块是对分析模块进行可视化的图表展示，包括使用词云展示词汇，词汇字体越大表示词频越高，使用户可以更直观的看到商品的特点和受众群体定位。
## 针对反爬虫系统的应对措施：
事先在Scrapy的Setting.py中维护一个包含各种浏览器的UserAgent的库，面对每一个Request请求，都随机从中选取一个填充到该请求的字段中，这样远程服务器就无法使用该反爬虫策略限制爬虫了。
