##简单解释什么是闭包##
link:http://stackoverflow.com/questions/12930272/javascript-closures-vs-anonymous-functions?rq=1

- 一个函数，称为F
- 列出F中所有的变量
- 变量的类型：
	- 本地变量（约束变量，已经声明的变量）
	- 非本地变量（自由变量，外部的变量）
- 如果F中没有自由变量，那他就无法称为闭包
- 如果F有自由变量（在父级作用域中定义的变量）：
	- F必须只有一个父作用域声明自由变量。
	- 如果F被父作用域的外部调用，自由变量便使之成为了闭包。
	- 自由变量被称为闭包F的上值（upvalue）

### 栗子1 ###
    for (var i = 0; i < 10; i++) {
	    (function f() {
		    var i2 = i;
		    setTimeout(function g() {
		    console.log(i2);
		    }, 1000);
	    })();
    }


**上面的程序里有2个函数：f和g。让我们看看他们是不是闭包：**
**先来看f:**

 - 列出变量
	- i2 是一个本地变量
	- i 是一个自由变量
	- setTimeout 是自由变量
	- g 是本地变量
	- console是自由变量
 - 来看看被父作用域声明的变量
	 - i 在全局中声明
	 - setTimeout在全局中声明
	 - console在全局中声明
 - 哪个作用域引用了F呢？全局
	 - 因此i没法让f称为闭包
	 - 因此setTimeout也没办法让f称为闭包
	 - 因此console也没办让f称为闭包

是的！函数f不是一个闭包。

**再来看g：**

- 列出变量
	- console是一个自由变量
- 	i2是一个自由变量
- 来看看被父作用域声明的变量
	- console在全局中声明
	- i2在f中声明
- 哪个作用域引用了g呢？setTimeout的作用域
	- 所以全局中声明的console没办法让g称为闭包
	- 而在f中声明的i2可以让g称为闭包

所以当setTimeout引用g时。函数g因为i2的存在称为了一个闭包（i2也因此称为g的上值）
