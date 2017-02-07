BEM Naming Rules
[http://getbem.com/introduction/]()

众所周知，一个好的样式表能显著的提升开发和debug效率，展现代码的特性。可惜的是，大多数css框架并没有好的构造和命名规范。导致在大型团队里难以维护整套css框架。

BEM可以确保每个在开发中的人员都有一套单独的框架用统一的css语言。使用适当的命名规范可以确保在网站的设计变化时便于修改。

##Block
块，封装了一个独立的有一定意义的块结构。当块可以嵌套并相互作用时，语义上它们保持相等；没有优先级或层次结构。没有DOM显示需要的整个实体（如控制器或模型）可以被称为块。
###Naming

块名称可能由拉丁字母、数字和破折号。形成一个CSS类名，为命名空间添加一个短前缀：
.block

###HTML

任何DOM节点如果有一个className都可以被称为块。
<div class="block">...</div>

###CSS

1.只使用className选择器。
2.没有标签和ids
3.没有父级依赖
.block { color: #042; }

##Element
元素，一个块的部分元素，没有独立意义。任何元素在语义上和他的块共同存在。

###Naming

元素命名可以由拉丁字母，数字和破折号还有下划线组成。CSS类的格式以块名+2个下划线+元素名组成。
.block__elem

###HTML

任何块中的DOM节点可以是一个元素。在一个块下，所有的元素在语义上相等。
<div class="block">
  ...
  <span class="block__elem"></span>
</div>

###CSS

1.只使用className选择器。
2.没有标签和ids。
3.没有父级依赖
.block__elem { color: #042; }

##Modifier

可变内容。在块及元素上的状态旗帜。使用他们可以改变显示，行为，及状态。

###Naming

可变内容命名可以由拉丁字母，数字和破折号还有下划线组成。CSS类的格式以块或元素名+2个横线：
.block--mod .block__elem--mod
.block--color-black .block--color-red

###HTML
可变内容是一个加给已经存在的块或元素上的类。只有当块或元素需要修改时才加上可变类名，并且保证原始类名不变：
<div class="block block--mod">...</div>
	<div class="block block--size-big
		block--shadow-yes">...</div>
		
###CSS
使用可变类名作为选择器：
.block--hidden { }
根据块可变类修改元素：
.block--mod .block__elem { }
元素可变类：
.block__elem--mod { }


##Example
###HTML
`<form class="form form--theme-xmas form--simple">
  <input class="form__input" type="text" />
  <input
    class="form__submit form__submit--disabled"
    type="submit" />
</form>`
###CSS
`.form { }
.form--theme-xmas { }
.form--simple { }
.form__input { }
.form__submit { }
.form__submit--disabled { }`
