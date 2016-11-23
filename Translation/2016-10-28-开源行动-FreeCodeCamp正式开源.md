# 开源行动：Free Code Camp 正式开源

> 原文链接：[Transparency in Action: Free Code Camp is Now Open Source](https://medium.freecodecamp.com/transparency-in-action-free-code-camp-is-now-open-source-9dae1985d925#.1zh20tm2o)
> 作者：[Free Code Camp](https://medium.freecodecamp.com/@FreeCodeCamp?source=post_header_lockup)
> 信息： 2014 年 11 月 29 日发布在 blog.freecodecamp.com
> 译者： [soyaine](http://github.com/soyaine)

我很高兴宣布 Free Code Camp（注：以下简称 FCC） 从此[完全开源](https://github.com/freecodecamp/freecodecamp)。现在你能 Fork 我们的代码，用来建立你自己的教育社区。如果你发现了 bug 或者对我们有优化的建议，请直接通过 Pull Request 来告诉我们。

## FCC 的前世今生
最初 FCC 用 Ruby on Rails 写成，这完全只是因为我用得比较熟，但如今看来， Javascript 是未来趋势这一点已经显露。类似 Node.js 和 Express.js 这些新工具，已经使纯 Javascript 全栈成为可能，现在已经有很多公司和学校开始这样做了。FCC 致力于开辟一方净土，以帮助繁忙的人们专注学习一系列的工具。既然我们要学的是全栈 Javascript，那没有一丁点 Javascript 的源码是没有指导意义的。所以我推翻原来 Rails 所写的应用，学了 Node.js 后又开始重建。
![我开发 FCC 0.1.0. 版时的办公场景掠影](http://ofjku7mlm.bkt.clouddn.com/16-10-24/70706423.jpg)
> 我开发 FCC 0.1.0. 版时的办公场景掠影

我考虑了 Meteor.js 和 Mean.js （在 Mean.io 出现之前是这个写法），甚至想过在 Google App 引擎的后端驱动下只选用 Angular.js。但最后，我决定使用 [Hackathon Starter App](https://github.com/sahat/hackathon-starter)，它有着验证套件和 API 集成，所以本身就可以看作是一个框架。几天之后， FCC 的初版诞生，尽管只有五个编程关卡和一个聊天室，但渐渐开始有人访问了，出人意料的是，大多数人还留了下来。

![10 周前 FCC 上线时它的样子](http://ofjku7mlm.bkt.clouddn.com/16-10-24/91741104.jpg)
> 10 周前 FCC 上线时的样子

 FCC 是我的第一个 Node.js 应用。当我向一个经验丰富的 JS 程序员展示代码的时候，他粗略一看便惊呼：“你脑子进水了吗！”不过黑客范的他承认，既然每天有上千的页面访问量也没出问题，那也不算太差，因此他觉得我应该继续做下去，然后开源。

所以我们用 Helmet.js 添加了安全支持，将 API 密钥移到 .env 文件，将之从 Git 历史清除。现在，你可以免费获取与 FCC 发布版几乎完全相同的代码了。

## FCC 的基础设施
之前我们一直只用了一个免费的 Heroku，但自从偶尔会超过 20 个并发数后，我们升级到了两个，每个月 35 美元。我们使用 [S3](https://www.wikiwand.com/en/Amazon_S3) 的云存储，并为聊天论坛建立了一个 AWS 小实例。此外，我们每年为 Vimeo Pro 帐户和 Screen Hero 帐户支付 240 美元，为单个 Google Apps for Business 团队帐户支付60美元。 这让我们每年基础设施的总成本在 2,000 美元以下。

## FCC 的志愿顾问
FCC 是一个帮助繁忙的人们学习编程的社区。在这里我们自称为“编程闯关者”，而这之中又有一些人因为志愿为社区付出而更忙。在社区里长期有编程顾问出没。我们尽全力迎接新人，然后回答各式各样的编程问题。FCC 唯一的目标是扩大同类人群，让他们通过 FCC 的编程关卡，构建项目，甚至找到一份开发的工作。

![我们中一些耐心而热情的志愿顾问](http://ofjku7mlm.bkt.clouddn.com/16-10-24/54833752.jpg)
> 我们中一些耐心而热情的志愿顾问

我们完全免费。如果有一天我们接受了资金或者通过职位广告版块来赚钱，我们会提供一个公平透明的渠道来分配股权或是支付薪酬给志愿者。成员间的交流大多通过聊天室或者定期的配对编程活动来进行。虽然我们的成员遍布各地，但在需要时也会见面。通常的流程是这样，先由顾问们提出关于新点子和内容的建议，讨论优先级和细节后，开始组队开发。正如你看到的这篇文章，也是由几个社区顾问协作完成的。

## FCC 的成长节奏
3 个月之内，我们的编程闯关者已经发展到了 5000 人的规模。但真正令人骄傲的不是成员的数量，而是他们的编程热情。一堆在职人士、学生、青年甚至[小孩子们](http://blog.freecodecamp.com/2014/11/I-am-a-Grandma-and-my-coding-career-is-just-getting-started.html)，正为编程学习投入他们宝贵的时间。

三周前我们更新了课程列表，从那时起，已有数以百计的人通过了长达一小时的闯关挑战。我们公开了这些指标，所以如果你有兴趣分析这些的（匿名）数据，或者帮助我们实现可视化，我们很乐意提供支持。

## FCC 的未来展望
不要期待 FCC 会有什么秘密行动，然后举行盛大揭幕仪式，实际上我们更乐于像互联网一样，在开放之中不断进化，而不是如原子弹一般，制造爆炸性的首次亮相。我们相信开源反对“bug 难逃众人法眼”（译者注：[Linux定律](https://www.wikiwand.com/zh/%E6%9E%97%E7%BA%B3%E6%96%AF%E5%AE%9A%E5%BE%8B)），所以对于任何人的提议，只要能让 FCC 变得更好，更有效地帮助繁忙的人们学习编程，我们都很欢迎。

最后我想将我们 FCC 的思想类比为乌班图（Ubuntu）。不是发行 Linux 的 Ubuntu，而是来自南非的一个同名词。[乌班图](https://zh.wikipedia.org/wiki/%E4%B9%8C%E7%8F%AD%E5%9B%BE)是一个祖鲁语中的词汇，可以直译为“我之所以为人，是因为我有归宿，我参与，我分享。”

![莱伊曼·古博薇（Leymah Gbowee）, 利比里亚的和平活动者，诺贝尔和平奖获得者，英文语义里被广泛接受的 Ubuntu 的典型代表。](http://ofjku7mlm.bkt.clouddn.com/16-10-24/36973040.jpg)
> 莱伊曼·古博薇（Leymah Gbowee）, 利比里亚的和平活动者，诺贝尔和平奖获得者，英文语义里被广泛接受的 Ubuntu 的典型代表。

FCC 之所以是 FCC，是因为我们编程闯关者的存在。在这里，工作繁忙的人们相互协助着学习编程，而这正是我们不断前行的原因。
