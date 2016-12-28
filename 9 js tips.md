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
这个方法会导致太多的中间件字符和连接操作，并且降低整体性能。
一个更好的实现方法是使用Array.join，这个方法会连接所有的数组元素到一个字符串里：
`var tmp = [];
for (/* each piece */) {
  tmp.push(piece);
}
str = tmp.join(''); // Specified an empty separator, thanks Jonathan
return str;`

此方法不受额外字符串对象的影响，而且执行速度更快。

###Binding Methods to Objects