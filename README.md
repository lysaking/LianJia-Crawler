## 链家爬虫
基于[Fast LianJia Crawler](https://github.com/CaoZ/Fast-LianJia-Crawler)改造。主要修改为使用MySQL，并增加小区地址的爬取。

### 准备工作：

1. 安装`Python`（3.6 或更高版本），安装`MySQL`

2. [建立虚拟运行环境](https://www.baidu.com/s?wd=virtualenv)（可选）

3. 下载代码

4. 安装依赖：`pip install -r requirements.txt`

5. 根据自己的数据库创建配置文件或修改默认配置文件（可选）

6. 创建数据库

7. 准备完成，现在可以愉快的去抓取数据啦~


### 使用方法：

```
app
├── main.py             用于抓取城市、行政区、商圈及小区基本信息。
├── page_crawler.py     用于抓取小区详情页面。
└── page_parser.py      用于解析小区详情信息。
```

```
usage: main.py [-h] [-c CONFIG] [city_id]

positional arguments:
  city_id               city id

optional arguments:
  -h, --help            show this help message and exit
  -c CONFIG, --config CONFIG
                        config file name
```

例如，抓取北京市的数据：

`python app/main.py 110000` （110000 即为北京市的 id）

这步可以获得小区基本信息，由于是通过链家网 API 获得的数据，速度极快。小区详细信息似乎并不能通过 API 获得，只能通过抓取页面的方式获得（链家 App 同样是通过页面来展示小区详情的）。

抓取小区详情页面：`python app/page_crawler.py 110000`

解析小区详情信息：`python app/page_parser.py 110000`

<br>


