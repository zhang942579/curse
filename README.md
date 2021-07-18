# curse
芜湖
import requests
from lxml import etree

headers = {
    'user-agent':
        'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/91.0.4472.124 Safari/537.36'
}
url = 'https://fz.58.com/searchjob.shtml?spm=154867245223.zhaopin_baidu&utm_source=12345'

page_text = requests.get(url=url, headers=headers).text
tree = etree.HTML(page_text)
ocuumat = tree.xpath('//div[@class="types"]/ul/li/p/a')
first_list = []
for a in ocuumat:
    az = a.xpath('./text()')[0]
    first_list.append(az)
     
print(first_list, len(first_list))
