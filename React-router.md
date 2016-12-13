#Leveling Up With React: 
##React-Router - p1
[https://css-tricks.com/learning-react-router/]()

react-router:
react 不是一个框架而是一个插件。因此，他不能帮你解决一切app里会遇到的问题。它可以做到就是帮你快速创建一个组件并且提供系统的管理状态方式，但是如果要创建更为复杂的spa（single page application）将需要用到3方支持（supporting cast）。在这里我们需要讲的就是其中之一react router。

如果你曾经用过其他前端路由，其中很多都非常相似。但react-router和它们有很大的区别，它使用JSX，这可能在一开始会有点陌生。

下面是如何render一个简单的组件：
`var Home = React.createClass({
  render: function() {
    return (<h1>Welcome to the Home Page</h1>);
  }
});

ReactDOM.render((
  <Home />
), document.getElementById('root'));`

下面是Home组件是如何用React-router被渲染
`...

ReactDOM.render((
  <Router>
    <Route path="/" component={Home} />
  </Router>
), document.getElementById('root'));`

要注意<router>和<route>是2个不同的东西。它们是组件功能并不会真正的创建DOM。虽然看起来<Router>他自己被渲染进了root，但我们仅仅只是为app定义里一个路由规则。继续看，你会发现这个概念：组件有时候不会为自己创建DOM，而是让其他组件来做。

在这个例子例，<Route> 定义里一个规则，在浏览器里访问/时，会把home组件渲染进root。

##multiple routers
在之前的例子中可以看到，单个路由非常的简单。但这对我们来说没什么太大价值，因为我们完全可以不用route来实现这一切。

而react-router的强大之处在于，可以让我们定义多个路由。通过在浏览器访问当前路径来渲染对应的组件。
`ReactDOM.render((
  <Router>
    <Route path="/" component={Home} />
    <Route path="/users" component={Users} />
    <Route path="/widgets" component={Widgets} />
  </Router>
), document.getElementById('root'));`

每个<route>都会根据不同的url path来渲染对应的组件。在这3个组件里将只有一个被渲染进root。通过这种方式，我创建在root里的router会根据不同的路由切换。

##re-usable layout
现在我们开始学习SPA的简单搭建方式。然而，这还是没解决真正的问题。是的，我们可以构建3个组件来作为html page，但怎么做到重用？当然我们可以让3个组件用同一个公共组件例如header或sidebar。所以我们该怎么在这些组件里重复它们呢？
。。。
如果你需要做一些极其相似的事情，来利用模版系统，这将是基本策略。现在让我看看html部分。我们从静态html开始看。
。。。
记住，root元素必须在js初始化之前存在在html里。root比较恰当，因为我们的react app会被创建在里面。但这里没有绝对的正确名字或惯例。我选择root，所以我们继续使用它来创建这个例子。只要确保它在body里面，而不是直接在body里。

在创建完静态后我们把它改为react组件
。。。
不要太过纠结我把component称为layout。它们3个都是react组件。我仅仅把其中2个成为layouts因为规则上它们作为容器存在。

最终我们将用嵌套的方式把list放在layout中。但是首先，注意要使list在layou中，必须在layer中写上this.props.children。所有的组件都有this.props.children这个属性，但只有当组件中被包括在父组件中才会有效。如果组件没有父组件，那this.props.children将会是null。

##nested routes
所以我们该怎么去嵌套组件？当我们把routes嵌套时，router会帮我搞定这一切：
`ReactDOM.render((
  <Router>
    <Route component={MainLayout}>
      <Route component={SearchLayout}>
        <Route path="users" component={UserList} />
      </Route> 
    </Route>
  </Router>
), document.getElementById('root'));
`
组件会根据router的嵌套方式被组合在一起。当用户访问'/users'时，react router会把userlist填进来。最终结果就是'／users'会被3层组件嵌套放在root下。

##IndexRoutes
定义一个默认的index路径。


##user link not a
当创建一个路由基点时，你会需要用到link to来代替a href。但不用担心，但你用link组件，react router会最终给你一个普通的DOM锚点，使用link是react router的一个神奇的功能。

需要注意的是link的path必须的全路径，例如你route里定义的嵌套路径，在link to里必须写全部path。

如果你需要创建一个无路由路径，例如链接一个外部站点，使用普通的tag即可，

##Active links
link一个非常cool的特性是组件可以知道自己是否在选中状态。
`<Link to="/users" activeClassName="active">Users</Link>`
如果用户正在访问'/users'，路由会找出匹配的<link>并激活它的active class。

##browser history
为了防止混淆，我将一个重要的细节留到现在才说。<Router>需要知道使用什么样的追踪策略来解析history。react router文档中对于browserHistory的解释如下：
`var browserHistory = ReactRouter.browserHistory;

ReactDOM.render((
  <Router history={browserHistory}>
    ...
  </Router>
), document.getElementById('root'));`
在之前的react router版本中，history属性不需要被设置并且默认是用hashHistory。从字面理解就是使用#来管理前端SPA路由规则，类似Backbone.js的路由规则。

在hashHistory中，URLs看起来像这样：
example.com
example.com/#/user?_k=ckucup
example.com/#widgets?_k=ckuvup

在browserHistory中，看起来是这也：
example.com
example.com/users
example.com/widgets

这里有一个警告对服务器端，在前端使用brwserHistory时。如果用户访问example.com然后导航去了/users 和/widgets，react router会非常完美的处理这一切。然而，如果用户手动在浏览器中输入连接example.com/widgets，或者刷新了example.com/widgets这个界面，浏览器至少会请求一次服务器/widgets。如果服务器的没有路由，则会返回404.

要解决这个404问题。react router推荐在服务器端使用通配符路由。利用这个策略，无论向服务器端请求什么路由，服务器都将返回同一个html文件。因此当用户定向到example.com/widgets，即使返回相同的html文件，react router都可以聪明的加载正确的组件。

用户不会感觉到任何问题，但你需要考虑到服务器端处理同样的html文件。在例子中，这一系列讲会使用通配符策略，但这取决于你处理服务器端的方式。

react router可否在服务器端和客户端上使用的同样的方式？当然可以，但这超出了本教程的范围。

##redirect with browserHistory

browserHistory是一个单独对象你可以在任何文件中包含它。如果你需要通过代码来重定向你的用户访问，你可以使用push，方法如下：
`browserHistory.push('/some/path');`

##route matching
react router处理route matching 比其他的路由要简单：
`<Route path="users/:userId" component={UserProfile} />`
当用户访问任何开头是'users/'的路径，route都会匹配。不论是'/usera/1'还是'/users/143'或是'/users/abc'。
react router会把:userID作为一个prop给组件。在组件中通过'this.props.params.userId'来获取。


