模块化势在必行



模块化的发展情况~

> 无模块化-->CommonJS规范-->AMD规范-->CMD规范-->ES6模块化









在ES6中，我们可以使用 import 关键字引入模块，通过 exprot 关键字导出模块，功能较之于前几个方案更为强大，也是我们所推崇的，**但是由于ES6目前无法在浏览器中执行，所以，我们只能通过babel将不被支持的import编译为当前受到广泛支持的 require**。 



- vue 使用es6中的模块化方法，使用关键字import,export更强大，需要babel编译
- echarts test中为了直接运行，使用AMD写法，等加载完之后再执行
- echarts源码中使用es6的模块化处理方式



## links

这一次，我要弄懂javascript的模块化https://juejin.im/post/5b4420e7f265da0f4b7a7b27