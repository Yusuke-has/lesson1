##記事のタイトルと更新日を取得する

import requests
from bs4 import BeautifulSoup
import pandas as pd


#空のリストを作る
d_list=[]

url="https://www.python.org/"

r=requests.get(url)

r.raise_for_status()

#BSで解析
soup=BeautifulSoup(r.content,"lxml")

#クラス名blog-widgetをもつdivタグを指定
articles=soup.select(".blog-widget li")

print(len(articles))


for article in articles:
    articles_date=article.select_one("time").text
    articles_title=article.select_one("a").text
    d_list.append({"articles_date":articles_date,
                 "articles_title": articles_title
                 })


print(d_list)

df=pd.DataFrame(d_list)
df.to_csv("putit_article_list.csv",index=None,encoding="utf-8-sig")
