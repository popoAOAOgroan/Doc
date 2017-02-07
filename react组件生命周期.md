[https://segmentfault.com/a/1190000003691119]()
[https://zhuanlan.zhihu.com/p/20328570]()

###componentWillMount：
在组件render之前执行，并且永远都只执行一次。由于这个方法始终只执行一次，所以如果在这里定义了setState方法之后，页面永远都只会在加载前更新一次。

###componentDidMount：
这个方法会在组件加载完毕之后立即执行。在这个时候之后组件已经生成了对应的DOM结构，可以通过this.getDOMNode()来进行访问。可以在这个方法中执行setTimeout, setInterval或者发送AJAX请求等操作(防止异部操作阻塞UI)。

###componentWillReceiveProps(object nextProps)：
在组件接收到一个新的prop时被执行。这个方法在初始化render时不会被调用。旧的props可以通过this.props来获取。在这个函数内调用this.setState()方法不会增加一次新的render.

###shouldComponentUpdate
返回一个布尔值。在组件接收到新的props或者state时被执行。在初始化时或者使用forceUpdate时不被执行。可以在你确认不需要更新组件时使用。

###componentWillUpdate
在组件接收到新的props或者state但还没有render时被执行。在初始化时不会被执行。一般用在组件发生更新之前。

###componentDidUpdate
在组件完成更新后立即执行。在初始化时不会被执行。一般会在组件完成更新后被使用。例如清除notification文字等操作。

###componentWillUnmount
该事件在组件即将被移除dom时会触发,主要用来执行一些必要的清理任务。例如清除setTimeout等函数，或者任意的在componentDidMount创建的DOM元素。


