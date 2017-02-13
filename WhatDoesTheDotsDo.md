What does the three dots in react do?
http://stackoverflow.com/questions/31048953/what-does-the-three-dots-in-react-do

这是一种JSX的扩展属性
var props = {};
props.foo = x;
props.bar = y;
var component = <Component {...props} />;
这个对象的属性们你可以直接通过...的方式拷贝到组件props中。
