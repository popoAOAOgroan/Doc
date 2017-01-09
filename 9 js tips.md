http://codetunnel.com/9-javascript-tips-you-may-not-know/


###Arrays的多用数据结构
虽然js第一眼看上去似乎在处理数据结构上能力有限。但Arrays比起其他程序语言（例如C++或Java）的数组类型来说可谓多才多艺。它通常以数组或联合数组的形式来使用，而这个例子会展示如何把Array当成堆栈,队列或是二进制输来使用。重用Array类代替数据结构可以带来2大好处：首先，时间不会浪费在重写已有的功能。第二，内置浏览器将比js counterpart更高效。

###Stack
一个堆栈遵循LIFO原则，一项内容被加在最后会被最先移出。Array类有2个方法可以提供堆栈功能。他们是push和pop。push会在数组最后增加一项，pop则是移除最后一项并返回数组。下面的代码演示了如何使用他们：

`var stack = [];
stack.push(2);       // stack is now [2]
stack.push(5);       // stack is now [2, 5]
var i = stack.pop(); // stack is now [2]
alert(i);            // displays 5`

###Queue
一个队列遵循FIFO原则：第一个增加的项目将会被第一个移除。一个数组可以被转为队列通过使用push和shift。push在数组后插入一项内容，shift移除第一项并返回数组。让我们看看代码：

`var queue = [];
queue.push(2);         // queue is now [2]
queue.push(5);         // queue is now [2, 5]
var i = queue.shift(); // queue is now [5]
alert(i);              // displays 2`

值得注意的是Array还有一个方法叫unshift。它可以在Array的开始增加项。所以一个堆栈可以通过unshift／shift模拟，一个队列可以通过unshift／pop模拟。

如果这些方法名让你觉得困惑，你也可以创造属于自己的别名。比如说，创造一个队列方法名叫add和remove：

`var queue = [];
queue.add = queue.push;
queue.remove = queue.shift;

queue.add(1);
var i = queue.remove();
alert(i);`

###Binary Tree
一个二叉树的数据形态就像一棵树的个个分支。每一个分支都有一个值和2个子分支（左一个右一个）。在C中，数据结构通常用构造和指针实现。在JS中可以通过对象和引用实现；然而，对于小型的二叉树来说，用数组实现是一个非常简单和快速的方式。数组第一项就是二叉树的头。左右子分支的索引可以通过下面的公式计算：
`leftChild(i) = 2i + 1
rightChild(i) = 2i + 2`
正如你所见，这样的方法在js中并不复杂，但当你处理一个小的数结构时这会非常有用。例如，你可以写一个帮助类来get和set节点或子节点，穿过树形结构，并且这个方法比起循环计算便捷。另一方面，这个方法的缺点是会随着数结构的增长而浪费空间。

###String Concatenation vs. Array.join
字符串链接和Array.join。
再怎么强调这个都不过分，多字符串连接的操作是非常影响性能的，当然这不难避免这种情况。例如你考虑构建一个由很多片组成的字符串，一个不怎么好的方式就是使用+好连接每一片到一个字符串里，一次一片：
`str = '';
for (/* each piece */) {
  str += piece; // bad for performance!
}
return str;`
这个方法会导致太多的中间件字符和连接操作，并且降低整体性能。（因为js中操作连接字符串的过程是，拿'a'+'b'举例，先创建2个字符的空间放入‘ab’，再把a和b消除掉）
一个更好的实现方法是使用Array.join，这个方法会连接所有的数组元素到一个字符串里：
`var tmp = [];
for (/* each piece */) {
  tmp.push(piece);
}
str = tmp.join(''); // Specified an empty separator, thanks Jonathan
return str;`

此方法不受额外字符串对象的影响，而且执行速度更快。

###Binding Methods to Objects
在用JS时常常会遇到想分配一个对象方法到一个事件处理器上的情况。而问题是事件处理器只能背HTML元素调用，即使是原生绑定事件也是这样。为了克服这个，我用了一个方法来绑定一个方法到一个对象上；这里需要传入一个对象和一个对象方法，返回的一个函数永远会调用这个对象中的方法。这是我从Prototype中发现的小技巧，下面就是怎么在不使用prototype的情况下使用对象函数：
`function bind(obj, method) {
  return function() { return method.apply(obj, arguments); }
}
var obj = {
  msg: 'Name is',
  buildMessage: function (name) {
    return this.msg + ' ' + name;
  }
}
alert(obj.buildMessage('John')); // displays: Name is John

f = obj.buildMessage;
alert(f('Smith')); // displays: undefined Smith

g = bind(obj, obj.buildMessage);
alert(g('Smith')); // displays: Name is Smith
`
###Sorting With a Custom Comparison Function
排序是一个常用任务。js为数组提供一个排序的方法。然而，这个排序方法默认按字母排序。非字符串类型会在排序前被转成字符串，所以在排序数字时，结果可能与我们所期望不一样：

`var list = [5, 10, 2, 1];
list.sort()
// list is now: [1, 10, 2, 5]`

解释这种现象其实狠简单：数字被转成字符串后才被排序，所以10变成了‘10’，2变成了‘2’。js解析器会比较字符串中的第一个字符，如果str1小于str2的第一个字符，那就比str2小。在我们的例子里，‘1’比‘2’小，所以‘10’比‘2’小。

不幸的是，js提供一个方法去重写排序，这个方法定义如何排序内容，这需要比较2项间的参数，且返回：
1.如果a<b,值就比0小。
2.如果a==b就为0.
3.如果a>b，值就比0大。

这样一种为比较字符的程序微不足道：
`function cmp(a, b) {
  return a - b;
}`
现在我们就可以用我们自己的方法来排序数组：
`var list = [5, 10, 2, 1];
list.sort(cmp);
// list is now: [1, 2, 5, 10]`
Array.sort()的易用性在于它可以支持更复杂的排序方式，比如说你有一个论坛表单数组，每一个表单看起来就像这样：
`var post = {
  id: 1,
  author: '...',
  title: '...',
  body: '...'
}`
如果你想要通过表单的id判断，用下面的方法：
`function postCmp(a, b) {
  return a.id - b.id;
}`
有理由说，使用浏览器原生的排序方法可以比实施一个js排序方法更有效。当然，如果有可能，数据应当在服务端就被排序好，所以非必要下无需使用（例如，当你希望在一个页面里得到多个排序列表的话）。

###Assertion

###Static Local Variables

###null, undefined, and delete

###Deep Nesting of Objects
如果你需要对一个深度嵌套对象做多部操作，存储一个新的新的引用对象要比每次单纯引用它的临时变量要好。例如，假设你要对一个文本框做一个重要操作：
`document.forms[0].elements[0]`
这里推荐你存储一个文本框的新引用对象，并且使用这个变量代替上面的操作：
`var field = document.forms[0].elements[0];`
每一次对这个对象的检索都是一次操作，以检索一个属性，在一个循环中，这些操作做加起来就会爆炸，所以最好做一次，将对象存储在一个变量，并重新使用它。
###Using Firebug
Firefox又一个极好的js debug工具叫Firebug。
###$ and $$
`$('id')`
通过id搜索，并快速返回一个DOM id为输入值的元素。
`$$('css selector')`
通过css选择器搜索，并快速返回一个DOM元素。

###console.log(format, obj1, ...)
console对象提供方法用以显示condole的日志消息。这个比用alert有用的多。console.log()方法类似于c语言中的printf。可以传入一个格式化的string和其他参数，在控制台输出格式化后的字符串：
`var i = 1;
console.log('i value is %d', i);
// prints:
// i value is 3`
###console.trace()
此方法在执行的地方打印出堆栈，不需要任何参数。
###inspect(obj)

