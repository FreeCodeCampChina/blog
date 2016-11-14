## 我是如何使用*Google Forms* 在*Medium* 上实现一个邮件列表订阅表单的

![](https://cdn-images-1.medium.com/max/2000/1*IOZC9nmYpJCaendKkOWHVw.jpeg)

在Medium[备注：全球最火的博客网站，需科学上网]上有许多收集邮件地址的付费服务，并且它们提供了一大堆炫酷的特性。

但是你有没有想过万一你根本不需要这些特性呢？

如果你只是简单地想收集读者的邮件地址呢？ 

*Google Forms*可以满足你！它不仅简单、免费，而且可以直接将列表导出成CSV格式。

不同于付费的邮箱收集工具，Medium原生支持Google Forms集成。也就是说如果你的读者在浏览器中阅读你的文章的话，他们将能直接在文章中看到集成好的表单。

如果你的读者是在Medium的安卓或者iOS app上阅读的话，则不会看到表单。所以我建议你可以在文章中插入一份表单的链接以便读者可以方便地使用表单。


好了，说了一大堆，让我们一起开始吧，我们将会先构建邮箱订阅提交表单。然后将其集成到Medium文章中。

![image](https://cdn-images-1.medium.com/max/1600/1*PcMQNWqTGIUv2TFdqyRVTg.png)

最终的的结果看起来像这样。我会将这份表单集成到该篇教程的末尾。

### 如何使用Google Forms构建注册表单

第一步：创建表单

访问 [https://forms.google.com](https://forms.google.com) 并点击“＋”（译者注，需科学上网）

![image](https://cdn-images-1.medium.com/max/1600/1*6ZL4XkJt5QoRKU3F0I-5Lg.png)

第二步：创建输入区域
第一个问题默认会被设置成“单选题”。这里我们将其改为“简短回答”。

![image](https://cdn-images-1.medium.com/max/1600/1*ndjGUXZvZZMBIsqBn6L9Pw.png)

第三步：设置表单标题与问题描述

![image](https://cdn-images-1.medium.com/max/1600/1*u44PEr7Jqb5q_Kapp4F84A.png)

第四步：添加数据验证

首先，我们需要通过点击右下角的“...”，然后点击“数据验证”来开启数据验证功能。

![](https://cdn-images-1.medium.com/max/1600/1*Up1MrB8tT9N3-m1KCgtixg.png)

现在我们可以通过添加正则表达式来确保读者的输入确实是一个有效的邮箱地址。

![](https://cdn-images-1.medium.com/max/1600/1*mb0zOL0yqpTcePq8YB9sGw.png)

下面是我使用的正则。据[emailregex.com](emailregex.com)说这个正则的有效匹配度可以达到99.99%。你只需要复制并粘贴到“模式”输入栏即可。

```
(?:[a-z0-9!#$%&'*+/=?^_`{|}~-]+(?:\.[a-z0-9!#$%&'*+/=?^_`{|}~-]+)*|"(?:[\x01-\x08\x0b\x0c\x0e-\x1f\x21\x23-\x5b\x5d-\x7f]|\\[\x01-\x09\x0b\x0c\x0e-\x7f])*")@(?:(?:[a-z0-9](?:[a-z0-9-]*[a-z0-9])?\.)+[a-z0-9](?:[a-z0-9-]*[a-z0-9])?|\[(?:(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.){3}(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?|[a-z0-9-]*[a-z0-9]:(?:[\x01-\x08\x0b\x0c\x0e-\x1f\x21-\x5a\x53-\x7f]|\\[\x01-\x09\x0b\x0c\x0e-\x7f])+)\])
```
如果你对正则匹配是如何运作很感兴趣并且想要了解更多的话，可以查看[这篇互动的课程](https://www.freecodecamp.com/challenges/sift-through-text-with-regular-expressions).

这里我并不想将输入框设置为必填。因为如果设置为必填就会为输入框添加烦人的红色*\*必填*，会给读者造成一种你在向他们索取邮箱地址的感觉。事实上你可以通过正则轻松的过滤掉空输入。

第五步：确保它是公开的
通过右上角的菜单选择“设置”标签，确保“需要登录一栏”没有被限定为需要某一类用户。

![](https://cdn-images-1.medium.com/max/1600/1*cU2S2VW-sJ4xwm0jXR1H4A.png)

第六部：增加配色。为什么不呢？
点击右上角的调色板按钮。如果你想与众不同你也可以自己上传一张图片作为背景。

![](https://cdn-images-1.medium.com/max/1600/1*eXJeXb09Wyjav3WIERqVQw.png)

### 现在让我们将表单集成到Medium中去
点击Google Form页面右上角的“发送”按钮。

![](https://cdn-images-1.medium.com/max/1600/1*-OgJrreJbNZFuLUSlb5wxw.png)

点击像锁链一样的链接按钮，然后点击“短链接”。复制URL，然后回到Medium页面，粘贴，然后回车。

一会儿后，Medium就会展示出你的表单的一张快照。一旦你点击了发布按钮，你的表单就会被集成到文章中一起发布，并且是完全可操作的。

piu~, 我的最后就长这样：

![image](https://cdn-images-1.medium.com/max/1600/1*PcMQNWqTGIUv2TFdqyRVTg.png)

订阅我以每周获取我精心挑选的3篇文章。[点这里完成订阅](https://goo.gl/forms/dsvfK1dRz5zePih02)

### 额外章节： 我是如何发送我的订阅邮件的
下面的就是我每周用来给大约350,000人发邮件的脚本。

[https://github.com/FreeCodeCamp/massification](https://github.com/FreeCodeCamp/massification)

该脚本使用了*AmazonSES*来保障高送达率。AmazonSES的费用是每百封$0.01，也就是说我每周的订阅邮件分发一共只需要花费$35。

现在的脚本需要花费18个小时才能将350,000封邮件发送完成。脚本是开源的，所以说如果你能够提供一种更加高效的算法，欢迎到github上给我发PR。

如果你对我的邮件是什么样很好奇，下面就是邮件：

![](https://cdn-images-1.medium.com/max/2000/1*OTtgoPkQ7Z8zfhrD2WS3PQ.png)

下面是邮件的JSON模版：

```
{
 “subject”: “Someone’s learning how to take down the internet.”,
 “text”: “Here are this week’s three links that are worth your time:\n\n1. Someone is learning how to take down the internet (3 minute read): http://bit.ly/2cbR5um\n\n2. For 25 years this man has been fighting to make public information public. Now he’s being sued for it (25 minute read): http://bit.ly/2cZzkM4\n\n3. GitHub announced a ton of new collaboration features (6 minute read): http://bit.ly/2cfZrPZ\n\nBonus: I just added new Free Code Camp gear to our community’s shop, including t-shirts, hoodies, and recommended books: http://bit.ly/2cz8Wai\n\n\nHappy Coding,\n\n- Quincy Larson\n\nTeacher at https://www.FreeCodeCamp.com\n\n\n\n\n\nIf this email bothers you, you can manage your email settings here: https://www.freecodecamp.com/settings\n\nOr you can one-click unsubscribe: https://www.freecodecamp.com/unsubscribe/<%= email %>”
}
```

注意，JSON底部的有个[Free Code Camp的商店链接](https://www.freecodecamp.com/shop),这为读者支持我们的社区提供一个便捷的入口，也可以帮助我来平衡这笔邮件的支出。

我写了一个粗糙但可用的取消订阅的功能。它背后的所有逻辑都跑在Free Code Camp的服务器上，同时也是我维护邮件列表的地方。

对于取消订阅的功能，你得自己想法子了。

如果你的邮件列表不是很长，那么你可以简单得让读者回复“unsubscribe”来取消订阅，然后手动得将他们的邮箱从Google Docs表格中移除。

你也许还会注意到我发送的邮件为简单文本格式，而不是HTML。

有很多的设计者向我表达了愿意为我创建一份HTML模版的想法。但是他们其实没有意识到，[多数人对普通文本邮件的钟爱远胜他们对HTML邮件的喜爱](http://blog.hubspot.com/marketing/plain-text-vs-html-emails-data)。

**我的看法是，既然你的朋友给你发邮件的时候是使用的简单文本邮件，那么简单文本带给你的感觉会更佳友好，而HTML邮件会感觉是垃圾邮件。**

并且，HTML邮件会导致访问性和手机适配的问题，而你将不得不去处理这些问题。你是否尝试写过邮件模版吗？我告诉你，一点也不好玩。

所以我的建议是使用简单文本就够了。

如果你还是持怀疑态度的话，我自己已经使用A/B test测试过的这两种情况，并且结论是，简单文本邮件的易接受性确实比HTML邮件要更好。

所以我对那些愿意提供HTML模版设计帮助的设计者表示了感谢，转而询问他们是否愿意帮助为我们的社区设计[一些图标和贴纸](https://github.com/FreeCodeCamp/assets)。

最后，你会看到我使用了 bit.ly来为我进行数据追踪分析。虽然没能提供 邮件接收/邮件打开的数据分析，但却给了我点击邮件中链接的分析。

![我的 Bit.ly 主页（过去30天的分析）](https://cdn-images-1.medium.com/max/2000/1*GViH8Q_eXU5Af-Lst6mhAg.png)

如果有人知道如何使用简单文本追踪 接收／打开 数据的方法，请在评论区给我留言，谢谢。

###  当然啦，你得先登录

![image](https://cdn-images-1.medium.com/max/1600/1*PcMQNWqTGIUv2TFdqyRVTg.png)

订阅我以每周获取我精心挑选的3篇文章。[点这里完成订阅](https://goo.gl/forms/dsvfK1dRz5zePih02)

别忘了点击左下角的💚，这样就会有更多的读者会在Meduim上看到这篇文章。
