export & export default

export用于暴露多个值（模块），当你import时，用相同的name即可引用相应的值。

export default则只用于暴露单一的值（模块），可以是一个函数，一个类，一个对象，或任何东西。考虑到这个值是唯一的出口，所以import时也一样是它。