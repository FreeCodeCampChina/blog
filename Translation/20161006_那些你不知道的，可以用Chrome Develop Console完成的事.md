# 那些你不知道的，可以用Chrome's Developer Console完成的事

![题图](http://oekyukinw.bkt.clouddn.com/titu1.jpeg)

Chrome内嵌的开发者工具拥有很多特性，例如网页元素，网络，和安全。今天我们将全部注意力投入到它的JavaScript控制台。

我刚开始编程时，仅仅把JavaScript控制台当做服务器响应包的日志输出，或者输出变量的值。随后，在帮助文档的帮助下，我发现了控制台可以做的很多事情都是我未曾想象过的。

以下是非常有用的功能，如果你阅读这篇文章时使用的是Chrome浏览器，你甚至可以立即打开它的开发工具并尝试这些功能。

## 1. 选择DOM元素

如果你对jQuery比较熟悉，你一定知道$('.class')和$('#id')是非常重要的，它们可以利用和DOM元素相关联的id或class对元素进行选择。

即使当你不在jQuery和DOM环境中时，你仍然可以利用开发者控制台使用相同的功能操作DOM。

`$('tagName')、$('.class')、$('#id')、$('.class #id')`和`document.querySelector('')`等价，将返回所匹配元素列表的第一个元素。

你可以使用双美元符`$$('tagName')或$$('.class')`选择被匹配的所有DOM元素，这些元素将被放入一个数组中。更进一步，你可以通过指定数组中的一个下标从而选出其中特定元素。

例如，`$$('.className')`将返回包含类`className`的所有元素，`$$('.className')[0]`和`$$('.className')[1]`将分别返回其中的第一个和第二个元素。

![developer console](http://oekyukinw.bkt.clouddn.com/fy2.png)

## 2. 把你的浏览器变成一个编辑器

是否可以在浏览器中编辑文字？这个问题你想过多少次？答案是可以。你可以把你的浏览器变成一个编辑器，你可以在任意DOM中增加或删除文字。

你不再需要在HTML文件中编辑这个元素了，相反的，打开开发者控制台，并输入以下命令：

```
document.body.contentEditable=true
```

该命令将使页面可编辑，此时你几乎可以编辑DOM中的任何东西。

## 3. 查找DOM中和某个元素相关联的事件

Debug时，你应该对查找DOM中和某个元素绑定的事件监听者感兴趣。开发者控制台让这件事变得简单。

`getEventListeners($('selector'))`返回绑定在指定元素上的所有事件对象的一个数组，你可以展开该对象从而查看事件：

![getEventListeners](http://oekyukinw.bkt.clouddn.com/fy3.png)

你可以输入以下命令，从而输出监听器上的特定事件：

```
getEventListeners($(‘selector’)).eventName[0].listener 
```

该操作将展示监听器上绑定的特定事件，这里`eventName[0]`是一个列有特定事件的事件数组，例如：

```
getEventListeners($(‘firstName’)).click[0].listener 
```

...将展示与ID为`'firstName'`元素相关联的点击事件的监听者。

## 4. 监控事件

当你想监控DOM中某个元素执行中的事件，你也可以在开发者控制台中完成。以下是不同的监控这些事件的命令：

* `monitorEvents($('selector'))`：监控选择器指定元素所关联的所有事件，一旦事件触发，将日志记录到控制台。例如，`monitorEvents($('#firstName'))`将记录绑定在ID为'firstName'的元素上的所有事件。
* `monitorEvents($(‘selector’),’eventName’)`：将记录绑定在元素上的特定事件，你可以将事件名作为参数传递给该函数。例如，`monitorEvents($('#firstName'), 'click')`将记录所有绑定在ID为'firstName'的元素上的点击事件。
* `monitorEvents($(‘selector’),[‘eventName1’,’eventName3',….]) `：该命令将记录多个事件，具体数量取决于你的需求。区别是需要传递一组事件字符串数组作为参数，而不是单个事件名。例如`monitorEvents($('#firstName'), ['click', 'focus'])`将记录在ID为'firstName'元素上所绑定的点击和焦点事件。
* `unmonitorEvents($(‘selector’)) `：停止监控和记录控制台中的事件。

## 5. 查看某个代码块的执行时间

`console.time('labelName')`是JavaScript console的基本函数，它接受一个标签名作为参数，并开始计时。对应的，`console.timeEnd('labelName')`是另一个基本函数，它同样接受标签名作为参数，并结束标签名对应的时间。

例如：

```
console.time('myTime'); //Starts the timer with label - myTime
console.timeEnd('mytime'); //Ends the timer with Label - myTime

//Output: myTime:123.00 ms
```

上面代码的前两行将返回时间开始到时间结束之间的时间。

我们可以利用它来计算执行一段代码所消耗的时间。

例如，我们想知道执行一个循环所消耗的时间，可以这样做：

```javascript
console.time('myTime'); //Starts the timer with label - myTime

for(var i=0; i < 100000; i++){
  2+4+5;
}

console.timeEnd('mytime'); //Ends the timer with Label - myTime

//Output - myTime:12345.00 ms
```

## 6. 将变量的值排列到表格中

假设我们有一个数组变量看起来像这样：

```javascript
var myArray=[{a:1,b:2,c:3},{a:1,b:2,c:3,d:4},{k:11,f:22},{a:1,b:2,c:3}]
```

当我们在控制台敲入变量名，将会以数组对象的形式展示，这非常有帮助，你可以展开对象从而查看对象值。

但当属性数量增加时，是比较难理解的。因此，为了更清晰的展示变量数据，我们可以将它们放到表格中。

`console.table(variableName) `将变量及其属性以表格的结构展示。它们看起来像这样：

![console.table](http://oekyukinw.bkt.clouddn.com/fy4.png)

## 7. 检查DOM中的元素

在控制台中，你可以直接检查某个元素

* `inspect($('selector'))`将监视被匹配的元素，这个元素会被列在Chrome Developer Tool是的Elements标签栏。例如`inspect($('#firstName'))`将监视ID为'firstName'的元素；`inspect($('a'[3]))`将监视DOM中第4个<a>元素
* $0, $1, $2, 等等，可以帮你获取当前被监视的元素。例如$0返回最后一个被监视的元素，而$1返回倒数第二个。

## 8. 列出元素的属性

如果你想列出元素所有的属性，你也可以直接在控制台完成。

`dir($('selector'))`返回一个包含关联元素中所有属性的对象，你可以展开查看更多细节。	

## 9. 重新获取上一次结果的值

你可以把控制台当做一个计算器，当你这样做时，你可能需要在第二个算式中使用第一个算式的计算结果，以下是如何在内存中获取前一个计算结果的方式：

```javascript
$_
```

类似这样：

```javascript
2+3+4
9 //- The Answer of the SUM is 9

$_
9 // Gives the last Result

$_ * $_
81  // As the last Result was 9

Math.sqrt($_)
9 // As the last Result was 81

$_
9 // As the Last Result is 9
```

## 10. 清空控制台和内存

如果你想清空控制台和它的内存，只需要输入并回车：

```
clear()
```



这里只是Chrome的Javascript控制台的部分例子，我希望这些小技巧可以让你的工作更高效。

谢谢阅读，如果你喜欢这篇文章，你可以将它推荐给其他在Medium上的的网友，只需要点击红心按钮即可。你可以找到更多[我的文章](http://swagatswain.in/)，可以在[Facebook](https://www.facebook.com/swagat.swain1)，[Twitter](https://twitter.com/SwagatSwain_)以及[Medium](https://medium.com/@swagatswain)上关注我。

