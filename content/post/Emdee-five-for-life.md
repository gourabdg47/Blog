+++
title = "Chapter 3"
date = 2021-10-22T22:40:59+05:30
draft = false
+++

## [Challenge 1] Emdee five for life

![Example image](https://i.ibb.co/G0NSZp8/Emdee-five-for-life-activities.png)

Well, you see the name ***Kikimora47***, thats me. Looks cool right! Alright let me share the steps I did to get the flag.

<!-- ```Python -->
```
import requests
import hashlib
import re

req = requests.session()
url = "http://134.209.27.142:31344/"

GET request
rget = req.get(url)
html = rget.content # Save the GET request

Strip HTML
def html_tags(html):
    clean = re.compile('<.*?>')
    return re.sub(clean, '', html.decode('UTF-8'))

Split Random String
out1 = html_tags(html)
out2 = out1.split('string')[1]
out3 = out2.rstrip()

print(out3)

MD5 Encrypt
mdHash = hashlib.md5(out3).hexdigest()
print(mdHash)

POST Request
data = dict(hash=mdHash)
rpost = req.post(url=url, data=data)

print(rpost.text)
```
<!-- {{< figure src="https://i.ibb.co/G0NSZp8/Emdee-five-for-life-activities.png" title="Steve Francia" >}} -->