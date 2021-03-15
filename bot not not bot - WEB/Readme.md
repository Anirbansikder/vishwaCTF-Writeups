# Solution

After Opening The Link We see there are 500 links provided some of which are useless and some are useful.

So upon opening few of them it is understood that useful links contain one character of the flag and it's position.

Here what python comes into play ->

```python
import requests
import re

URL = "https://bot-not-not-bot.vishwactf.com/page"

flag = []

for i in range(1,501):
    response = requests.get(URL + str(i) + ".html")
    if "Useless Page" not in response.text:
        text = re.findall("<h1>(.*)</h1><p>",response.text)[0]
        pos = re.findall("<br>(.*)</p></body>",response.text)[0]
        flag.append({"pos" : int(pos) , "text" : text})

flag_str = ""
for i in sorted(flag,key = lambda i:i["pos"]):
    flag_str += i["text"]
print(flag_str)
```

So this travels through all the links and finds the useful pages and gives the out the characters of the flag !

```Flag : vishwaCTF{r0bot_15_t00_0P} ```