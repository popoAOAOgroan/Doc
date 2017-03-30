redux 是js app中一个用来管理页面ui状态和数据状态的工具。它为了解决SPAs的状态复杂情况。他不是框架，而是一种数据流方式，他最初以react来设计，但它也可以在angular和jquery app中使用。

另外，它还设想了一种时间旅行的概念。稍后我们会聊到他。

在react中数据留是单线的，从父到子。

reducer 应该以纯函数的方式编写，什么是纯函数：
1.不做任何网络交互和数据库访问。
2.仅仅依据函数参数来返回值。
3.参数应该考虑到‘不可变性’，意味着你不能去改变它们。
4.当每次传入相同参数到纯函数时，都能返回相同值。

再来看看如何创建一个完整的store
1.通过reducer来创建store
2.reducer建立初始化的app state
3.dispatch通过发送action来改变store
4.reducer改变state并返回它以此改变store

