#类

[https://segmentfault.com/a/1190000003798438]()
[https://github.com/getify/You-Dont-Know-JS/tree/master/this%20&%20object%20prototypes]()

类成员包括在{}里。类成员包括类构造器和类方法（包括静态方法和实例方法）。

`class Polygon {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
  
  get area() {
    return this.calcArea()
  }

  calcArea() {
    return this.height * this.width;
  }
}
const square = new Polygon(10, 10);

// 100
console.log(square.area);`

###静态方法
static 关键字用来定义类的静态方法。静态方法是指那些不需要对类进行实例化，使用类名就可以直接访问的方法，需要注意的是静态方法不能被实例化的对象调用。静态方法经常用来作为工具函数。

###原型链
原型链本质上只是建立对象之间的关联