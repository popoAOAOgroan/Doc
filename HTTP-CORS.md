##HTTP-CORS
OPTIONS请求也就是我们所知的跨域资源共享Cross-origin resource sharing（CORS）pre-flight请求。

如果你需要跨域请求资源，那他们是必不可少的。

这个pre-flight请求是一些浏览器为了确认请求是来自那些服务器可信任的站点以保障安全问题。意思是服务器明白这个方法，请求中的origin和headers可以被安全的接受和处理。

你的服务器不能忽略这些请求，而是处理这些请求无论你是否尝试跨域请求。

一个好的例子[http://enable-cors.org/]()

一个处理这些问题的方式是确保任何处理OPTIONS方法的服务器返回头：
`Access-Control-Allow-Origin: *`
这会告诉浏览器这个服务器很乐意对任何origin返回请求。
