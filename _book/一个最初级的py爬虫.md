```
#!usr/bin/env python3
#-*- coding:UTF-8 -*-
import requests

if __name__ == "__main__":
    target = "http://www.biqukan.com/1_1094/5403177.html"
    res = requests.get(url = target)
    print(res.text)

# BeautifulSoup(markup,parser);
# markup:html 标签集(即一个html网页内容)
# parser:html/xml 标签解析器(html.parser,lxml)
```