+++
title = "Chapter 3"
date = 2021-10-22T22:40:59+05:30
draft = false
+++

## [Challenge 1] Emdee five for life

![Example image](https://i.ibb.co/G0NSZp8/Emdee-five-for-life-activities.png)

Well, you see the name ***Kikimora47***, thats me. Looks cool right! Alright let me share the steps I did to get the flag.
# Steps[Emdee Five for Life BOX]:
- Open "TRAGET_IP:30891" in the browser
- we get MD5 string "7It4ykV6YGdvjIm2TE7e", we have to encrypt it fast    
and subit a POST request.   
- But if we manualy, it says we are slow so we have to write a 
python script
- I followed the blog: 
https://bigb0ss.medium.com/htb-web-challenge-emdee-five-for-life-56cb0ddfd63f
- I wrote a script named md5_scrypt.py where we encrypt the given 
string and send the encrypted string to the IP using POST request and 
it works
- It gave the FLAG "HTB{N1c3_ScrIpt1nG_B0i!}"

**md5_scrypt.py**
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


