#webpack
[https://github.com/webpack/docs/wiki/configuration]()

webpack 与gulp grunt不同之处在于webpack是一个模块构建工具，所有你项目中涉及到的文件都会包含，你所要做的就是给一个指定的处理它们的loader。

所以如果你写
`var myImage = require('./static/myImage.jpg');`
weibpack首先会试着把你require的内容解析成js。当然这肯定不会成功，所以你必须为你需要处理的文件给一个loader。比如file-或url-loader，并把给它们一个导出地址（output folder）然后将会返回一个对应文件的哈希url。
`var myImage = require("./static/myImage.jpg");`
`console.log(myImage); // '/build/12as7f9asfasgasg.jpg'`

##loaders
什么是loaders？它可以帮你处理（装换）你项目中的资源文件。它是nodejs写的方法，获取项目里资源文件并返回新的资源文件内容。

例如，你可以使用loaders告诉webpack来加载coffeeScript或者JSX文件。
