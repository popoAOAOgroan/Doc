
#A2 VS REACT
###angular2 is a framework,react is a library

> Choosing between Angular and React is like choosing between buying an off-the-shelf computer and building your own with off-the-shelf parts.
> 
> 在Angular与React中选择就好比你是选择买一台现成电脑用，还是买一堆零件自己组装一台用。
> 
https://medium.freecodecamp.com/angular-2-versus-react-there-will-be-blood-66595faafd51#.p2lkdsetd

##A2的优势
Low Decision Fatigue

A作为一个框架，它提供了更多更好的选择和功能。而R则需要添一些其他库才能构建一个APP。你可能需要一个库作为路由，还需要一个库来实现单向流，或执行webAPI，或是单元测试，依赖管理等等。最后项目依赖的库会非常庞大。这就是为什么R有那么多工具包。

A则提供了更多的选择空间，可以帮你更快的开始，而不需要考虑还需要增加什么库。而它一致性也帮助很多新手更快的掌握。在项目人员更替时也更容易交接。


###TypeScript=Clear Path 清晰的路径
当然，TS并不被所有人接受，但A2接受了它，它让js更具风味并取得了巨大的成功。在网上R的例子各种各样都有，几乎ES5与ES6各占一半，最近提供了3种不同的方式来定义组件。这对很多刚刚接触R的人造成了困惑。
然而A2不需要TS，A的核心团队接受他并在文档里使用TS。这意味着相关例子和开源项目更相似和一致。A已经提供清晰的例子来展示怎么利用TS编译。（虽然目前，并不是所有人都接受TS）这个一致性可以帮助到初学者在接触R时减少困惑和太多决策。

###Reduced Churn 降低流失率
2015是JS疲乏的一年。虽然R的发展非常迅速并带来了V15。R的系统正在快速成长，特别是在Flux和路由。因此，如果今天你的项目依赖了太多库，在未来可以都会过期，并需要重构。
所以A不像那些在发布后需要痛苦适应的框架。就像一个成熟的框架，当你选择A，你可以相信一个小团队就可以在未来完善好它。在R中，你必须去纠结选择不同的开源库到一个完整的项目中去，并协调在一起。这是一个令人沮丧和有无之境的工作。

###Broad Tooling Support 工具的广泛支持
我认为R JSX是一个巨大的成功。然而，你需要去选择一个支持JSX的工具。R非常受欢迎但支持工具却非常少。新的工具比如IDEs和linters并不能支持JSX。A2的模板存储在string或HTML文件，因此它不需要特别的工具支持。

###web Component Friendly 良好的web组件支持
A2的设计中包含了基础的web组件。在A2中创建的组件比较R的组件更容易转换成原生的web组件。当然，浏览器还不是完全支持，但这将会为以后打下基础

##R的优势

###JSX
JSX是一个用JS编译的类似HTML语法。标签和代码被写在同一个文件里，这意味着你完全可以自由引用你组件的方法和变量。相反，A的string模板有个缺点，在编辑器里没有代码提示，没有不支持代码补全，编译出错。通常只有可怜的错误消息提示。（虽然A团队已经创造了自己的模板编辑器来弥补这一点）
如果你不喜欢A的string模板，你可以把模板放在一个单独文件，但就像以前一样，同时在头部引入2个文件，没有错误提示和代码检查。直到你用R，它可以在一次编译中检查所以组件，这使得JSX如此特别。

###React Fails Fast and Explicitly R查错更快更明确
当你在R中写了个错误的JSX标签，它不会编译。是的！这意味着你会明确的知道哪行有错。明确的告诉你是否忘了关闭标签还是多加了个不存在的属性。事实上，JSX编译器指定错误发生的位置的行号。这种行为从根本上加速开发。
相反，当你在A2中错误地引用了变量。什么事都不会发生。A2用更快的编译时间来代替在编译时差错。当我加载APP时还要思考为什么我的数据没出现，并不有趣。

###React is JS-Centric

###React's JS-Centric design = simplicity

###Luxurious Development Experience

###Size Concerns

###React Embraces the Unix Philosophy

###Showdown Summary 总结
A2在1的基础上进了一大步。新的组件模块比起1代的directives简单。支持同构/同意渲染，它使用一个虚拟的DOM提升3-10倍的性能。这些改变使得A2更具竞争性。不可置否，功能齐全自然带来了显而易见的好处--减少“JS fatigue”。
然而，A2的大小和语法让我犹豫。A承诺，要以HTML为中心设计模块，而这比起R的以JS为中心的模块更复杂。在R中，你不需要学习HTML特性例如ngWHATEVER。完全可以把时间花在写原生JS上，而我相信这才是未来趋势。