# 我在FreeCodeCamp数据科学实验室的一年

>英文原文：[One year in the Free Code Camp Data Science Room](https://medium.freecodecamp.com/one-year-experience-in-the-free-code-camp-data-science-room-c97eb905af1f#.z0rybfdpg)
作者：[ecccs](https://medium.freecodecamp.com/@ecccs_FCC)
翻译：[dawnwenhui@fcc北京](https://github.com/dawnwenhui)
校对：[JackJin@fcc苏州](https://github.com/JackJin2014)

![Head](https://cdn-images-2.medium.com/max/2000/1*ef3sgKjwAFm2tAnfgL7_hg.jpeg)

一年半前，我作为一个对前端开发感兴趣的数据科学家，参加了freeCodeCamp社区。很快我就发现,他们不仅重视数据科学——并且已经计划将数据集作为开源的数据向公众发布。	
​经过一些讨论后，[Quincy Larson（昆西.拉尔森）](https://medium.com/u/17756313f41a)推荐我去 freeCodeCamp的核心团队，并为我创建 [数据科学实验室](https://gitter.im/FreeCodeCamp/DataScience) （这将作为专业的讨论数据科学、数据可视化及开源代码的讨论区/聊天室）开绿灯。  
​
​这一切发生在仅仅是一年前－－2015年七月的尾巴。
​
​自那时起，我在数据实验室的经验得到了极大的丰富和激励。截止到2016年8月，数据科学实验室已经拥有了超过700的中等活跃用户。实验室的日志包含非常丰富的且有用的资源，并且很多参与者编写了freeCodeCamp的开源代码。
​
​本文是对去年数据科学实验室的一些有趣的发展历程做了简单回顾。

## 开放数据视觉

我们数据科学实验室的第一条消息来自Quincy Larson（昆西.拉尔森），他总结了freeCodeCamp作为开源资源运动的自然延伸在开源数据中的优势：

```　　　
​“我们近期计划是开放我们全部的匿名数据集来做学术研究。”
		——Quincy Larson（昆西.拉尔森），２０１５年７月
```

​六个月后，在圣诞前夜，freeCodeCamp通过大量的开源的数据集进行了第一次公开的数据试验，这些数据集包含100,000选择参加训练营的营员的进度：

[freeCodeCamp特别的圣诞：送给开源数据的礼物]
(https://medium.freecodecamp.com/free-code-camp-christmas-special-giving-the-gift-of-data-6ecbf0313d62)

几个月后，数据科学实验室发布了通过对２０１６新的程序猿的研究的研究结果。这包括15000名受访者的数据,每个人回答了48问题：

[We asked 15,000 people who they are, and how they’re learning to code](https://medium.freecodecamp.com/we-asked-15-000-people-who-they-are-and-how-theyre-learning-to-code-4104e29b2781)

研究结果当下是 **[`Kaggle`](https://www.kaggle.com/forums/f/1318/2016-new-coder-survey)** 最流行的数据集之一，原始、结构化数据在 **[`GitHub`](https://github.com/FreeCodeCamp/2016-new-coder-survey)** 托管。

我们数据实验室的成员也加入了数据分析，并且集中他们的力量在生成freeCodeCamp社区的许多平台的数据集上。

## Gitter聊天室
git是一个freeCodeCamp自开办以来的核心社交中心，却也是一个短小“松弛的插曲”：
[So Yeah We Tried Slack… and We Deeply Regretted It](https://medium.freecodecamp.com/so-yeah-we-tried-slack-and-we-deeply-regretted-it-391bcc714c81)

git聊天室已经成为欢迎新营员、请求编程帮助和整合开源项目贡献的聚集地，与此同时，成为一个gitter也变得相当的流行。    
```
仅在2015年1月1日至2016年5月31日，在freeCodeCamp较集中的聊天室有将近2千万条消息发出。
```
在freeCodeCamp所有的聊天室中，最集中的聊天室 [(FreeCodeCamp/FreeCodeCamp)](https://www.gitter.im/freecodecamp/freecodecamp) 是最受欢迎的。至少每分钟会有一个消息，高峰时间甚至会蹦出６到９条消息每分钟蹦出来。
FCC Gitter Room Visualization

<iframe width="560" height="315" src="https://www.youtube.com/embed/KM-VY4z_PLY" frameborder="0" allowfullscreen></iframe>

Real Time data visualization of calling other users in the main chat room. This social network representation uses d3.js, node.js, and sockets, and was built by Koustuv Sinha and myself.


## 社区引导加强对新人的帮助
由于freeCodeCamp是一个志愿者主导的开源社区，这个社区大半的成功是依靠有意愿分享他们的时间和经验的营员来实现的。因此我们的社区致力于发展乐于助人的社区生态。
<p data-height="265" data-theme-id="0" data-slug-hash="mExpjg" data-default-tab="js,result" data-user="ecccs" data-embed-version="2" class="codepen">See the Pen <a href="http://codepen.io/ecccs/pen/mExpjg/">FreeCodeCamp Chat</a> by Evaristo (<a href="http://codepen.io/ecccs">@ecccs</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="//assets.codepen.io/assets/embed/ei.js"></script>
![](http://7xqg0a.com1.z0.glb.clouddn.com/fcc_Top10.jpeg)
Generational replacement of campers at work: a billboard of the users' top10, and other data about the Free Code Camp main chat room, built in python and d3.js by myself.

每月，都有成百的我们的营员找到他们第一份的程序猿工作，同样这也会使得他们在聊天室变得不再活跃。但是，会有新鲜血液补充进来，这就是社区如何可以维持生存的机制。

当一个营员帮助其他人时，就会获取freeCodeCamp平台的奖励分。想知道最新的最有价值营员是谁么？你可以查看非官方的 freeCodeCamp的 **[100强排行榜](https://fcctop100.herokuapp.com/)**（由 [Roel Verbunt](https://github.com/roelver)用react\MongoDB\nodejs创建的）。

## 线下的学习小组
![](https://cdn-images-2.medium.com/max/1200/1*p6poZi8CySNa-m8wFT75sA.jpeg)
Free Code Camp Mexico City.

我们的营员也会通过freeCodeCamp
**1500+的 [全球本地学习小组](https://medium.freecodecamp.com/free-code-camps-1-000-study-groups-are-now-fully-autonomous-d40a3660e292#.vidk0bnns)** 面对面的交流。

<p data-height="265" data-theme-id="0" data-slug-hash="WxRJGV" data-default-tab="js,result" data-user="BecauseAlice" data-embed-version="2" class="codepen">See the Pen <a href="http://codepen.io/BecauseAlice/pen/WxRJGV/">FreeCodeCamp Campsite Map (WIP)</a> by Alice (<a href="http://codepen.io/BecauseAlice">@BecauseAlice</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="//assets.codepen.io/assets/embed/ei.js"></script>

![](http://7xqg0a.com1.z0.glb.clouddn.com/fcc%20globe.jpeg)

A world map of Free Code Camp study groups using d3.js by Alice Jiang. You can zoom in and click on individual dots to bring up their Facebook groups.

这些小组通过脸书小组组织。平均每小组有40成员，甚至在像旧金山、伦敦、多伦多、德里这些主要城市，会有超过1000个成员的小组。

我与Alice Jiang, Aleksandar B,分析发现大约45%的注册学习小组都有预期的活动安排。

这里有一些其他社区的统计数据:

* 2016年7月，这里至少有430个人向freeCodeCamp**[代码仓库](https://github.com/freecodecamp/freecodecamp)** 提交了至少一次代码；
* Free Code Camp 是 Medium 上最受受欢迎的出版物的 **[第十二名](http://toppub.xyz/)** (原文：~~第十三名~~)；
* 在 **[YouTube频道](https://www.youtube.com/freecodecamp)** 上，有超过4万名关注者； 

我们最近开办了一个论坛，这个论坛现在有3万个用户，每天访问量1000。

我也分析了 Free Code Camp（免费程序猿训练营)222篇最近的推文:

> (‘code’, 44),
 	(‘freecodecamp’, 40),
 	(‘time’, 35),
 	(‘design’, 28),
 	(‘make’, 24),
 	(‘medium’, 24),
 	(‘trying’, 21),
 	(‘write’, 20),
 	(‘browser’, 20),
 	(‘history’, 19),
 	(‘future’, 19),
 	(‘developer’, 18),
 	(‘inspiration’, 17),
 	(‘programming’, 16),
 	(‘read’, 16),
 	(‘javascript’, 16),
 	(‘stories’, 13),
 	(‘coding’, 13),
 	(‘learn’, 12),
 	(‘spend’, 12),
 	(‘declarative’, 11),
 	(‘imperative’, 11),
 	(‘work’, 11),
 	(‘people’, 11),
 	(‘using’, 11),
 	(‘become’, 11),
 	(‘perfect’, 10),
 	(‘finding’, 10),
 	(‘better’, 10)

简而言之——编码，学习和努力工作。

写此文的目的是为了表达对每一个帮助了 [数据科学实验室](https://gitter.im/FreeCodeCamp/DataScience) 进行数据分析及可视化的小伙伴们的衷心感谢！
​
​小伙伴们，快乐编码，后会有期。

