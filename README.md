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





from itertools import count
import requests
from bs4 import BeautifulSoup
import time
#from lxml import etree

#book = load_workbook('C:\\ProgramData\\Anaconda3\\Scripts\\Book1.xlsx')

import openpyxl

# 建立一個工作簿
#workbook = openpyxl.Workbook()
# 建立一個表單
#sheet = workbook.create_sheet('表單1')

# 儲存

workbook = openpyxl.load_workbook('C:\\ProgramData\\Anaconda3\\Scripts\\Book1.xlsx')
s = workbook.active
print('max_row')
print(s.max_row)

max_row_len = s.max_row + 1


years = 2001


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
for year in range(2001,2010):


    
    for count in range(1,13):
        
        #print(str(year) + '/' + str(count) )
        soup_2 = web_crawl('https://nvd.nist.gov/vuln/full-listing/' + str(year) + '/' + str(count))
        link = soup_2.find_all('span', 'col-md-2')

        
   
        
        
        for i in link:
            links = i.find('a')['href']
            cve = i.find('a')
            
            resp = requests.get('https://nvd.nist.gov/vuln/detail/' + str(cve.text))
            soup = BeautifulSoup(resp.text, 'html.parser') 
            print(resp)
            print(cve.text)
            
            s.cell(row=max_row_len, column=1, value=cve.text)
            descri = soup.find(attrs={"data-testid":"vuln-description"})
            print(descri.text)
            s.cell(row=max_row_len, column=2, value=descri.text)
            max_row_len += 1









end = time.time()
workbook.save('C:\\ProgramData\\Anaconda3\\Scripts\\Book1.xlsx')
print("執行時間:%f 秒" % (end - start))


# 寫入一個資料


