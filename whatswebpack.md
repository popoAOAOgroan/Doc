#Using React with Webpack 
link：https://blog.risingstack.com/using-react-with-webpack-tutorial/

##webpack核心思想

要明白webpack，首先要聊一聊Grunt和Gulp。相对于Grunt的任务和Gulp的管道来说input就像是文件路径（globs）的概念。匹配文件运行不同的进程，例如transpile, concat, minify等等。如果我们把Grunt和Gulp拿来做比较的话，webpack能处理你的项目，Grunt和Gulp能处理你的文件。

使用webpack时你只要给你一个文件路径。这个路径指向你项目的起点，典型的如index.js和main.js。webpack会检查你的app，弄清楚有多少require，import，图片静态文件地址等等。它为你的app创造了一个完整的依赖关系以便运行。所有这些你只需要一个起点文件路径。

一项资产就是一个文件。可以是一个图片，css，less，json，js，jsx，等等。这些node依赖文件由webpack创建依赖关系。

当webpack检查你的app，它会为依赖创建新的节点。当一个新的节点被发现，它会检查文件的延伸依赖。如果延伸依赖匹配你的webpack配置。会运行一个新的进程处理它们。这类进程就被称为loader。
