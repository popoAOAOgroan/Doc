[http://jsrocks.org/cn/2014/10/arrow-functions-and-their-scope/
]()
这个箭头函数的作用域和其他函数有一些不同,如果不是严格模式，this关键字就是指向window，严格模式就是undefined，在构造函数里的this指向的是当前对象实例,如果this在一个对象的函数内则this指向的是这个对象，this有可能指向的是一个dom元素，例如当我们添加事件监听函数时,可能这个this的指向不是很直接，其实this（不止是this变量）变量的指向是根据一个规则来判断的：作用域流。
`
function Person () {

    let fullName = null;

    this.getName = function () {
        return fullName;
    };

    this.setName = function (name) {
        fullName = name;
        return this;
    };
}

let jon = new Person();
jon.setName("Jon Doe");
console.log(jon.getName()); // "Jon Doe"
//注：this关键字这里就不解释了，大家自己google,baidu吧。`

在这个例子中，如果我们让Person.setName函数返回Person对象本身，我们就可以这样用：

`
jon.setName("Jon Doe")
   .getName(); // "Jon Doe"   
`

但是当执行流(比如使用了setTimeout)和作用域变了的时候，this也会变。

`
function Student(data){

    this.name = data.name || "Jon Doe";
    this.age = data.age>=0 ? data.age : -1;

    this.getInfo = function () {
        return this.name + ", " + this.age;
    };

    this.sayHi = function () {
        window.setTimeout( function () {
            console.log( this );
        }, 100 );
    }

}

let mary = new Student({
    name: "Mary Lou",
    age: 13
});

console.log( mary.getInfo() ); // "Mary Lou, 13"
mary.sayHi();
// window`

当setTimeout函数改变了执行流的情况时，this的指向会变成全局对象,或者是在严格模式下就是undefine,这样在setTimeout函数里面我们使用其他的变量去指向this对象，比如self，that,当然不管你用什么变量，你首先应该在setTimeout访问之前，给self，that赋值，或者使用bind方法不然这些变量就是undefined。

这是后就是箭头函数登场的时候了，它可以保持作用域，this的指向就不会变了。

让我们看下上文起先的例子，在这里我们使用箭头函数：
`
function Student(data){

    this.name = data.name || "Jon Doe";
    this.age = data.age>=0 ? data.age : -1;

    this.getInfo = function () {
        return this.name + ", " + this.age;
    };

    this.sayHi = function () {
        window.setTimeout( ()=>{
            // the only difference is here
            console.log( this );
        }, 100 );
    }

}

let mary = new Student({
    name: "Mary Lou",
    age: 13
});

console.log( mary.getInfo() ); // "Mary Lou, 13"
mary.sayHi();
// Object { name: "Mary Lou", age: 13, ... }`

