# webcrawler
from itertools import count
import requests
from bs4 import BeautifulSoup
import time


#book = load_workbook('C:\\ProgramData\\Anaconda3\\Scripts\\Book1.xlsx')

import openpyxl

# 建立一個工作簿
workbook = openpyxl.Workbook()
# 建立一個表單
sheet = workbook.create_sheet('表單1')

# 儲存






years = 2022


def web_crawl(weblink):
  headers = {
      	'user-agent': '你的user agent'
      }
  res = requests.get(weblink)
  res.encoding = 'UTF-8'
  soup = BeautifulSoup(res.text, 'html.parser')
  return soup



start =time.time()

count = 1
for year in range(2000,years):


    
    for count in range(1,13):
        
        #print(str(year) + '/' + str(count) )
        soup_2 = web_crawl('https://nvd.nist.gov/vuln/full-listing/' + str(year) + '/' + str(count))
        link = soup_2.find_all('span', 'col-md-2')
        cve_length = len(link)
        cve_length += cve_length
        
        print(cve_length)
        abc = 0
        
        
        for i in link:
            links = i.find('a')['href']
            cve = i.find('a')
             
            
            
            print(cve.text)
            print(count)
            sheet.cell(row=count, column=1, value=cve.text)
            workbook.save('C:\\ProgramData\\Anaconda3\\Scripts\\Book1.xlsx')
            count += 1
            





end = time.time()

print("執行時間:%f 秒" % (end - start))


# 寫入一個資料

