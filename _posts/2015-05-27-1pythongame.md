---
layout: post
title: python过关游戏（0-5）
category : 技术分享
tagline: "Supporting tagline"
tags : [Jekyll, blog, 技术]
---
{% include JB/setup %}
# python过关游戏（0-5）


<br><br>
python过关游戏（0-5）持续更新。
pyhon游戏过关。
[http://www.pythonchallenge.com/pc/def/0.html](http://www.pythonchallenge.com/pc/def/0.html)<br>
**0        》》》》》**<br>
        第一关的图可以看出2^38
python计算得出答案274877906944。
得到通关URL：[www.pythonchallenge.com/pc/def/274877906944.html](www.pythonchallenge.com/pc/def/274877906944.html)
<!--break-->
**1        》》》》》**<br>
        第二题根据提示，和图片，可以看出来是对字符右移2位。其实就是字符替换的一种加密方式，传说中的恺撒密码。我们用String中的maketrans()和translate()方法，先构建一个map，然后在调用这个方法。

{% highlight python %}
>>> import string
>>> a="g fmnc wms bgblr rpylqjyrc gr zw fylb. rfyrq ufyr amknsrcpq ypc dmp. bmgle gr gl zw fylb gq glcddgagclr ylb rfyr'q ufw rfgq rcvr gq qm jmle. sqgle qrpgle.kyicrpylq() gq pcamkkclbcb. lmu ynnjw ml rfc spj. "
>>> map=string.maketrans(string.ascii_lowercase,string.ascii_lowercase[2:]+string.ascii_lowercase[0:2])
>>> a.translate(map)
"i hope you didnt translate it by hand. thats what computers are for. doing it in by hand is inefficient and that's why this text is so long. using string.maketrans() is recommended. now apply on the url. "
{% endhighlight %}

 然后根据他的意思，再一次解密URL得到下关的URL
[http://www.pythonchallenge.com/pc/def/ocr.html](http://www.pythonchallenge.com/pc/def/ocr.html)

**2      》》》》》**<br>
        第三题中，根据提示，在源代码中可以找出一个字符串。然后根据提示，是找出其中的字母。我们将其保存成文件，再用isalpha()来找出字母。

{% highlight python %}
>>> file=open("f:\Users\Administrator\Desktop\\1.txt",'r')
>>> s=file.read()
>>> for x in s:
	if x.isalpha():
		print x		
e
q
u
a
l
i
t
y
{% endhighlight %}

也可以用正则表达式：

{% highlight python %}
>>> file=open("f:\Users\Administrator\Desktop\\1.txt",'r')
>>> s=file.read()
>>> l=re.findall("([a-z])",s)
>>> l
['e', 'q', 'u', 'a', 'l', 'i', 't', 'y']
{% endhighlight %}

看出字母为equality。得到下一关URL：
[http://www.pythonchallenge.com/pc/def/equality.html](http://www.pythonchallenge.com/pc/def/equality.html)

**3       》》》》》**<br>
        第四题和第三题比较类似，在源码得到字符串后。根据提示，找出前后恰恰有3个大写字母的小写字母。可以使用re的findall进行正者表达式的匹配。

{% highlight python %}
>>> import re
>>> file=open("f:\Users\Administrator\Desktop\\1.txt",'r')
>>> s=file.read()
>>> l = re.findall("[a-z][A-Z]{3}([a-z])[A-Z]{3}[a-z]", s)
>>> ''.join(l)
'linkedlist'
{% endhighlight %}

可以得到下一题的URL：
[http://www.pythonchallenge.com/pc/def/linkedlist.html](http://www.pythonchallenge.com/pc/def/linkedlist.html
)

**4       》》》》》**<br>
        进入URL后，得到一个新的地址：http://www.pythonchallenge.com/pc/def/linkedlist.php
首先这个题很有意思。进入网页后，看到提示，发现图片是可以点击的。网页源码提示urllib may help. DON'T TRY ALL NOTHINGS, since it will never end. 400 times is more than enough.点击图片进去后得到and the next nothing is 44827然后和网页的URL对比http://www.pythonchallenge.com/pc/def/linkedlist.php?nothing=12345
于是对URL地址网页进行400次循环就可以的到答案了吧？：代码如下：

{% highlight python %}
#coding=utf-8
__author__ = 'Windyer'
import urllib2
import re
url="http://www.pythonchallenge.com/pc/def/linkedlist.php?nothing="
nothing="12345"
i=400
while(i):
    i=i-1
    s=urllib2.urlopen(url+nothing).read() #获取网页内容
    l=re.findall("([0-9])",s)
    if len(l)!=0:
        nothing=''.join(l)
        print str(i)+":"+s
    else:
        print s
{% endhighlight %} 
      
但却并不是我们想象的那么简单：在输出的内容中可以看到一个提示：Yes. Divide by two and keep going.这里需要对nothing除以2然后继续。得到此时的noting为16044。所以做出修改：nothing=8022然后继续。中间有给出提示让修改nothing为63579。（不知道是不是我的出问题了），按照修改，得出答案peak.html。
得到下一题URL:[http://www.pythonchallenge.com/pc/def/peak.html](http://www.pythonchallenge.com/pc/def/peak.html)

**5        》》》》》**<br>
        这个题其实我完全不会做。
在一个机缘巧合下载源码里得到了一个url。打开后得到一串字符。然后有提示让你读“peak hell”这个。为什么要读他？肯定和发音有关，python的一个peakle库。（无语了,但是学到一个新东西）。首先peakle有2个基本功能，通过pickle模块的序列化操作我们能够将程序中运行的对象信息保存到文件中去，永久存储；通过pickle模块的反序列化操作，我们能够从文件中创建上一次程序保存的对象。这里使用第二种：

{% highlight python %}
__author__ = 'Windyer'
#coding=utf-8
import pickle
file=open("f:\Users\Administrator\Desktop\\1.txt",'r')
data=pickle.load(file)
for line in data:
    print(''.join(t[0] * t[1] for t in line))
file.close()
{% endhighlight %}

然后说的到#组成的channel单词。
这里说一下

{% highlight python %}
print(''.join(t[0] * t[1] for t in line))
{% endhighlight %}

和

{% highlight python %}
for i in line:
       print ''.join(i[0]*i[1])
{% endhighlight %}

的区别。前者将是一行，后者输出将是多行。

得到下关url:​​[http://www.pythonchallenge.com/pc/def/channel.html](http://www.pythonchallenge.com/pc/def/channel.html)

























