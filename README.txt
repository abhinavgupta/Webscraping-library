>>> from webscraping import common
>>> common.remove_tags('hello <b>world</b>!')
'hello world!'

>>> common.extract_domain('http://www.google.com.au/tos.html')
'google.com.au'

>>> common.unescape('&lt;hello&nbsp;&amp;&nbsp;world&gt;')
'<hello & world>'

>>> common.extract_emails('hello richard AT sitescraper DOT net world')
['richard@sitescraper.net']

>>> cj = common.firefox_cookie()
>>> opener = urllib2.build_opener(urllib2.HTTPCookieProcessor(cj))
>>> html = opener.open(url).read() # use current firefox cookies to access url

Download

>>> from webscraping import download
>>> D = download.Download()

>>> # crawl given domain
>>> domain = ...
>>> for url in D.crawl(domain):
>>>    html = D.cache[url]

pdict

>>> from webscraping import pdict 
>>> cache = pdict.PersistentDict(CACHE_FILE)
>>> cache['a'] = range(5) # pickle stored in sqlite database
>>> 'a' in cache
True
>>> cache['a']
[0, 1, 2, 3, 4]

(see a further example here)
xpath

>>> from webscraping import xpath
>>> html = urllib2.urlopen(url).read()
>>> xpath.parse(html, '/html/body/ul[2]/li[@class="info"]/div[1]')
['div content']
>>> xpath.parse(html, '/html/body/ul[2]/li[@class="info"]/a/@href')
['url1', 'url2', 'url3']
