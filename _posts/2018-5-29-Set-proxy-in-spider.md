---
layout: post
title: Set proxy in sipder
category: python
keywords: Whatever
---
# urllib
When you use urllib, build a opener.

    import urllib.request
    proxy_temp = {'http':'http://119.28.194.66:8888'}
    handler=urllib.request.ProxyHandler(proxy_temp)  
    opener=urllib.request.build_opener(handler)  
    urllib.request.install_opener(opener)
    url='https://uxxunet.github.io/'
    r = urllib.request.urlopen(url)


# requets
When you use requets, use index "proxies".

    import requests
    proxy_temp = {'http':'http://119.28.194.66:8888'}
    url='https://uxxunet.github.io/'
    r=requests.get(url, proxies=proxy_temp)

# Reference

(Reference1)[http://gohom.win/2016/01/21/proxy-py/]