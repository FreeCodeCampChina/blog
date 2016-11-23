## FreeCodeCamp 的特别圣诞节：给开发数据一份大礼
>原文：[Free Code Camp Christmas Special: Giving the Gift of Open Data](https://medium.freecodecamp.com/free-code-camp-christmas-special-giving-the-gift-of-data-6ecbf0313d62#.j8rfmv1jt) 
作者：[Quincy Larson](https://medium.freecodecamp.com/@quincylarson)
翻译：[Laily](https://github.com/Laily123)
校对：[jhonny-me@fcc苏州](https://github.com/jhonny-me)

![](ogit74i74.bkt.clouddn.com/d7ec5f5ae4211041d1b9bf2810ba9ed9_image_0.jpeg)
在过去的几个月里，有数不清的研究人员和科学家们问起我们的系统数据，在这里，祝你们：圣诞节快乐！

自从14个月前启动了我们的开源社区，公开这些数据就作为我们的一个目标了。

今天，我们要兴奋的宣布我们已经公开了我们数据中的一大块－－我们成员的进度以及解决方案。

### 数据

数据集像下面这样：

```json
[
  {
    “name”: “Waypoint: Say Hello to HTML Elements”,
    “completedDate”: 1445854025698,
    “solution”: “<h1>Hello World</h1>\n”
  }
]
```

这是一个很大的 JSON 数组。

我们几个月前统计数据发现，在这个数组里有超过 100,000 个子数组。每条代表了一位至少完成过一个挑战的 fcc 成员。

每个子数组包含了一些 JavaScript 对象，表示一个独立的fcc成员完成的挑战。

每个这样的 JavaScript 对象包含挑战的名称，fcc 成员第一次完成挑战的时间（使用 Unix 时间戳表示）和他的答案。答案可能是一串代码也可能是一个链接到在 CodePen，Heroku 或者 GitHub 上的示例。

由于可以通过每个成员的答案分辨 fcc 用户，所有的这些信息都已经公开在成员的代码作品集里的。我们没有在这里包含任何私密的信息，只是让这些公开的信息更容易获取。

我们非常注重用户的隐私，不久前给用户添加了设置所有答案为私有的功能。为了防止我们社区（和雇主）能查看  fcc 用户的作品，我们禁止了他们的资格证书。令人庆幸的是，只有大约1000名成员选择设置他们的答案为私有。但是我们依然会注意不让这部分数据进入这个公开的数据集中。

### 来看看内部

作为开发者，在数据科学的又深又复杂的领域里我们很多还是初来乍到。但是即使用我们有限的理解，我们也能稍微窥探一下这个数据集的内部：

- 是否可以根据成员的完成挑战的表现，将成员进行分组
- 能否根据成员完成挑战的情况找到一个零界点，选拔出高效完成者和低效率者
- 有一些 FCC 成员会因为厌倦或者生活上的困扰暂时离开 FCC，在数月之后再回到这里，这里是否存在有意义的数据样本
- 有哪些成员按顺序完成挑战，哪些是跳跃式完成的
- 哪部分成员直接进入高难度的挑战，然后回到开始重新学习直到能成功完成挑战
- 有哪些挑战过于困难，比相类似的挑战明显需要花费更多的时间？
- 有哪些挑战不怎么受欢迎
- 那个挑战有最多的不同解决方法。
- FCC学员更喜欢面向对象编程还是函数式编程？

### 获取数据

你可以通过这个磁力链接 [Academic Torrents](http://academictorrents.com/details/030b10dad0846b5aecc3905692890fb02404adbf)使用 BT 下载工具下载这个数据集（一个 344MB 的 tar.gz 文件）。

注意这个数据集是使用的 [Open Database Commons Open Database License (ODbL)](http://opendatacommons.org/licenses/odbl/summary/) 协议。

![](ogit74i74.bkt.clouddn.com/d7ec5f5ae4211041d1b9bf2810ba9ed9_image_1.jpeg)

我们计划每个季度更新这个数据集，我们也计划以后尽可能多的公开我们的数据。

我们欢迎任何对我们数据有兴趣的人给我们反馈，如果你需要我们分享其他的数据，或者有什么可以更轻松的分析这些数据的建议，请在下面留言。
