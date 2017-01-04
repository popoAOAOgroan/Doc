`var uu1 = function(name,age){
	this.name = name;
	this.age = age;
	this.eatSomething = function(){
		console.log(this.name + 'eat something');
	}
}`
`
var uu2 = {
	name: '',
	age: '',
	eatSomething: function(){
		console.log(this.name + 'eat something');
	}
}`
`
var uu3 = function(name,age){
	this.name = name;
	this.age = age;
}
uu3.prototype..eatSomething = function(){
	console.log(this.name + 'eat something');
}`

