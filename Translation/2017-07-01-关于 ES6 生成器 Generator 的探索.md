# 关于 ES6 生成器 Generator 的探索

原文链接：[https://medium.freecodecamp.org/lets-explore-es6-generators-5e58ed23b0f1](https://medium.freecodecamp.org/lets-explore-es6-generators-5e58ed23b0f1)  
作者：[Tiago Lopes Ferreia](https://medium.freecodecamp.org/@ferreiratiago?source=post_header_lockup)  
译者：[Soyaine](https://github.com/soyaine)  

![Generator](http://image.jiantuku.com/17-7-2/54822669.jpg?attname=1*clLJU6akoeiZuw0Vw9DC8w.png&e=1498980010&token=el7kgPgYzpJoB23jrChWJ2gV3HpRl0VCzFn8rKKv:aAAuUKDa6l-tKuFRU7ZOh1AFlvo=)

生成器（Generators）是可迭代协议（iterables）的一种实现。

它的最大特点在于，**它是可以在保持上下文状态的情况下暂停执行的函数**，当处理需要暂停的执行逻辑，但在恢复执行时需要之前的上下文时，这就起到了很重要的作用。看到这里有没有想到了异步编程？

## 语法
生成器的语法以 `function*` 作为开头的标识符（注意末尾的星号），同时穿插着 `yield` 来实现执行的暂停。下面以具体的代码演示这个过程。

```javascript
function* generator() {
    // 代码A
    yield 'foo'
    // 代码B
}
```

调用上面的 `generator` 函数时，将会创建一个新的生成器，我们可以通过 `next` 函数来用它控制程序逻辑。运行 `next` 将会执行这个生成器中代码，直到 `yield` 的语句。到这个点时，`yield` 语句中的 `value` 的值将被返回，同时 `generator` 的执行也被挂起。

```javascript
const g = generator()

g.next() // { value: 'foo', done: false }
// 生成器中的代码A 被执行，
// value 中的 'foo' 通过 yield 被返回，
// 然后，生成器的执行被挂起。

g.next() // { value: undefined, done: fales }
// 在这个阶段，剩下的代码（如代码B）继续被执行，
// 由于没有返回值，所以我得到 'undefined' 作为 value 的值，
// 同时这个迭代器（iterator）返回 true 以表示迭代结束。
```

### `yield`

`yield` 伴随着生成器出现，并且允许我们在执行的中途返回值，但只能在生成器内部这样做。如果我们试图在回调时返回一个值的话，就算在生成器中声明了，也会报错。

```javascript
function* generator() {
    ['foo', 'bar'].forEach(e => yield e) // SyntaxError 语法错误
    // 我们不能在一个非 generator 的函数中使用 yield
    //（译者注：此例子从 yield 被写在了 forEach 函数中）
}
```

### `yield*`

`yield*` 是用来在一个生成器中调用另一个生成器的。

```javascript
function* foo() {
    yield 'foo'
}

// 我们如何在 bar 生成器中调用 foo 生成器呢？
function* bar() {
    yield 'bar'
    foo()
    yield 'bar again'
}

const b = bar();

b.next() // { value: 'bar', done: false }
b.next() // { value: 'bar again', done: false }
b.next() // { value: undefined, done: true }
```

这里的 `b` 迭代器由 `bar` 生成器产生，但在调用 ‘foo’ 的时候并不会按照期待执行。这是因为，尽管运行 ‘foo’ 时产生了一个迭代器，但我们并不会迭代它。这就是 ES6 会带来 `yield*` 操作符的原因。

```javascript
function* foo() {
    yield 'foo'
}

function* bar() {
    yield 'bar'
    yield* foo()
    yield 'bar again'
}

const b = bar();

b.next() // { value: 'bar', done: false }
b.next() // { value: 'foo', done: false }
b.next() // { value: 'bar again', done: false }
b.next() // { value: undefined, done: true }
```

这对数据迭代也完美适用：

```javascript
function* foo() {
    yield 'foo'
}

function* bar() {
    yield 'bar'
    yield* foo()
    yield 'bar again'
}

for (let e of bar()) {
    console.log(e)
    // bar
    // foo
    // bar again
}

console.log([...bar()]) // [ 'bar', 'foo', 'bar again' ]
```

在 `yield*` 中遍历这个生成器中的所有元素，然后 `yield` 返回这个值。

```JavaScript
function* bar() {
    yield 'bar'
    for (let e of foo()) {
        yield e
    }
    yield 'bar again'
}
```

## 作为迭代器（Iterators）的生成器（Generators）

![Generators as Iterators](http://image.jiantuku.com/17-7-2/55735343.jpg?attname=1*p65T1aheR-c6JDSWRcUVhA.gif&e=1498981210&token=el7kgPgYzpJoB23jrChWJ2gV3HpRl0VCzFn8rKKv:g5ikMPJ5o1CRqAUMCLgD7NyrlrI=)

之所以说生成器是简单的迭代器，是因为它们同样遵循了可迭代协议（`iterable` protocol）和迭代器协议（`iterator` protocol）：
- 可迭代协议指出，一个可迭代的对象应该返回一个含有 key 为 `Symbol.iterator` 的迭代器。
     ```js
     const g = generator()

     typeof g[Symbol.iterator] // function
     ```
- 迭代器协议指出，迭代器对象应该是一个指向迭代函数（iteration）中下一个元素的对象，并且这个对象包含一个叫 `next` 的函数。
     ```
     const iterator = g[Symbol.iterator]()
     typeof iterator.next // function
     ```
- 由于生成器是可迭代对象，所以我们可以使用遍历方法来迭代循环其中的值，例如 `for-of`。
     ```js
     for (let e of iterator) {
          console.log(e)
          // 'foo'
     }
     ```

##  Return

我们可以在生成器中添加一个 `return` 语句，但由于生成器的数据处理规则是迭代，所以 `return` 的作用与平常有所区别。

```js
function* generatorWithReturn() {
    yield 'foo'
    yield 'bar'
    return 'done'
}

var g = generatorWithReturn()

g.next() // { value: 'foo', done: false }
g.next() // { value: 'bar', done: false }
g.next() // { value: 'done', done: true }
```

当手动执行这个迭代函数的时候，使用 `next`，我们得到的迭代器的最后一个 `value` 是 `return` 的返回值（如 `done`），此时 `done` 的标记值为 true。

但是在使用一个像 `for-of` 或者 `destructuring` 这样定义好的数据遍历操作时，返回值会被忽略。

```
for (let e of g) {
     console.log(e)
     // 'foo'
     // 'bar'
}

console.log([...g]) // ['foo', 'bar']
```

### yield*

我们知道 `yield*` 允许我们在一个生成器中调用另一个生成器，同时它也允许我们通过已执行的生成器来存储返回值。

```js
function* foo() {
     yield 'foo'
     return 'foo done'
}

function* bar() {
     yield 'bar'
     const result = yield* foo()
     yield result
}

for (let e of bar()) {
     console.log(e)
     // bar
     // foo
     // foo done
}
```

### Throw

我们可以在生成器内部使用 `throw`，`next` 会传递发生的异常。一旦抛出异常，迭代器的流程将会中断，状态被设置为 `done: true`，并无限保持。

```js
function* generatorWithThrow() {
     yield 'foo'
     throw new Error('Ups!')
     yield 'bar'
}

var g = generatorWithReturn()

g.next() // { value: 'foo', dxone: false }
g.next() // Error: Ups!
g.next() // { value: undefined, done: true }
```

## 用于数据遍历的生成器

生成器除了因 `yield` 而有了数据生成的作用，使用 `next` 它也可以遍历数据。

```js
function* generatorDataConsumer() {
     // A
     console.log('Ready to consume!')
     while (true) {
          const input = yield; // B
          console.log(`Got: ${input}`)
     }
}
```

这里也有一些有趣的点可以探索。（请看代码及之后的解释）

```js
// (1)
var g = generatorDataConsumer()

// (2)
g.next() // { value: undefined, done: false }
// Ready to consume!

// (3)
g.next('foo') // { value: undefined, done: false }
// Got: foo
```

### 创建生成器 (1)

在这一步创建了一个 `g` 生成器，程序会在 `A` 处停止执行。

### 第一个 next (2)

执行第一个 `next` 时，生成器会执行到第一个 `yield` 语句。第一次执行的时候，通过 `next` 传递的任何值都会被忽略，这是因为没有出现 `yield` 语句。所以执行过程会在 `B` 处暂停，等待 `yield` 被赋值。

### 下一个 next (3)

在下一次执行 `next` 时，生成器会运行代码至下一个 `yield`。在我们上面的例子中，它打印了通过 `yield` 得到的值（i.e. `Got: foo`），并且再次在 `yield` 处暂停。

## 应用例子

![Use Cases](http://image.jiantuku.com/17-7-2/11669803.jpg?attname=1*OiK88NOSMsbrlpWdDarvlg.gif&e=1498981210&token=el7kgPgYzpJoB23jrChWJ2gV3HpRl0VCzFn8rKKv:IO8hor2sBg6mwPBYE6ODgIOhopc=)

### 实现可迭代协议

因为生成器是可迭代协议的一种实现，所以当它被创建的时候我们也就得到了一个可迭代的对象，在这个对象中，`yield` 代表了每次迭代时传递出的值。这使得我们可以用生成器来创建迭代器。

下面这个例子展示了一个可迭代的生成器遍历数据并找出最大值的过程。因为我们的生成器会返回一个可迭代对象，所以我们可以用 `for-of` 来遍历这些值。

记住 `yield` 会暂停生成器的执行过程，每次迭代时，生成器会从之前暂停的地方重新开始。

```js
function* evenNumbersUntil() {
    for (let value = 0; value <= max; value += 2) {
        // 当 'value' 的值是偶数时，我们把它 'yield'
        // 并作为迭代过程中的下一个值
        if (value % 2 === 0) yield value;
    }
}

// 现在我们可以用 'for-of' 来迭代这些值了
for (let e of evenNumbersUntil(10)) {
    console.log(e)
    // 0
    // 2
    // 4
    // 6
    // 8
    // 10
}
```

### 异步的代码

我们可以用生成器来更好实现异步代码，比如 `promises`。这部分的例子很好的介绍了 ES8 中的新特性 `async/await` 。

下面要展示一个用 `promises` 来获取 JSON 文件的例子，我们将用 [Jake Archibald](https://twitter.com/jaffathecake) 的在 [developers.google.com](https://developers.google.com/web/fundamentals/getting-started/primers/promises) 上的例子。

为了让我们的代码看起来更像同步的风格，我们使用了 [co](https://github.com/tj/co) 库。至于 `async/await` 的话，我们的代码会有点像我们之前的版本。

## 结尾

这是 Axel Rauschmayer 在 Exploring ES6 上的图，向我们展示了生成器是如何与迭代器联系在一起的。

![Exploring ES6](http://image.jiantuku.com/17-7-2/82605719.jpg?attname=1*XBMTOSxCUQ6MloksmDYdJw.png&e=1498981210&token=el7kgPgYzpJoB23jrChWJ2gV3HpRl0VCzFn8rKKv:wG1f2oZviiqUHiDGl5YBr2SKM3w=)

生成器是可迭代协议的一种实现，且遵循可迭代协议和迭代器协议，因此它们都可以用于建立可迭代对象。

生成器最令人惊奇的点在于它可以在执行过程中暂停，为此 ES6 引入了 `yield` 的新特性。

然而在生成器中调用生成器并非像执行生成器函数那么简单，为了解决这个问题，ES6 中又有了 `yield*`。

> 生成器为让异步编程向同步风格的发展更近了一步。

## 致谢

- [Axel Rauschmayer](https://twitter.com/rauschma) 的 [Exploring ES6 — Generators](http://exploringjs.com/es6/ch_generators.html)
- [Nicolás Bevacqua](https://twitter.com/nzgb) 的 [PonyFoo — ES6 Generators in Depth](https://ponyfoo.com/articles/es6-generators-in-depth)
- [Jake Archibald](https://twitter.com/jaffathecake) 放在 [developers.google.com](https://developers.google.com/web/fundamentals/getting-started/primers/promises) 的 promise 的代码例子
- 感谢所有 [Regular Show](https://www.youtube.com/watch?v=n_OC-RAm7Qs) 的粉丝