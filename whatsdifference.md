`var uu1 = function(name,age){
	this.name = name;
	this.age = age;
	this.eatSomething = function(){
		console.log(this.name + 'eat something');
	}
}`
var uu = new uu1('aa','12');
uu.age;
//引用同一个内存区域，除非new一个新的
内部方法可以被读写

`
var uu2 = {
	name: '',
	age: '',
	eatSomething: function(){
		console.log(this.name + 'eat something');
	}
}`
//引用同一个内存区域
内部方法可以被读写


`
var uu3 = function(name,age){
	this.name = name;
	this.age = age;
}
uu3.prototype..eatSomething = function(){
	console.log(this.name + 'eat something');
}`
//同第一个

var uu4 = function(name,age){
	var man = {
		'name': name,
		'age': age
	}
	return function(){
		return man;
	}
}
//每次调用都创建一个新的内存区域。