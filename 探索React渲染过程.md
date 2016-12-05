#React 渲染过程

今天在用到css flex的时候发现react的渲染父组件和子组件时是有先后顺序的。

由于父组件包裹子组件的div样式是display:flex；子组件外层div上有样式flex：1，内部有div，position：relactive和 height，100%；另自组件有兄弟组件的height是父组件的10%左右。

照理说子占父组件90%，兄弟占10%。然而第一次渲染结果是子组件内部div，height100%撑满了整屏。因此猜测应该是先子后夫。

渲染时先更新了子组件css，其次再更新父组件css。导致一开始子的内部div height100%以父组件的height为准了。而且关键的一点是内部div的height是由iscroll加得可能是在一开始？或父组件未渲染前。