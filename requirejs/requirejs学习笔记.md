

[Javascript模块化编程（三）：require.js的用法](http://www.ruanyifeng.com/blog/2012/11/require_js.html)

这样的写法有很大的缺点。首先，加载的时候，
浏览器会停止网页渲染，加载文件越多，
网页失去响应的时间就会越长；

其次，由于js文件之间存在依赖关系，
因此必须严格保证加载顺序（
比如上例的1.js要在2.js的前面），依赖性最大的模块一定要放到最后加载，当依赖关系很复杂的时候，代码的编写和维护都会变得困难。

require.js的诞生，就是为了解决这两个问题：

( 1）实现js文件的异步加载，避免网页失去响应；

（2）管理模块之间的依赖性，便于代码的编写和维护。


使用AMD规范定义的的require()函数。

```javascript
　require(['moduleA', 'moduleB', 'moduleC'], function (moduleA, moduleB, moduleC){

　　　　// some code here

　　});
```
回调函数内部


默认情况下，require.js假定这三个模块与main.js在同一个目录，文件名分别为jquery.js，underscore.js和backbone.js，然后自动加载。

使用require.config()方法，我们可以对模块的加载行为进行自定义。require.config()就写在主模块（main.js）的头部。参数就是一个对象，这个对象的paths属性指定各个模块的加载路径。

```javascript
require.config({

　　　　paths: {

　　　　　　"jquery": "jquery.min",
　　　　　　"underscore": "underscore.min",
　　　　　　"模块名": "路径"

　　　　}

　　});
```

```javascript
　require.config({

　　　　paths: {

　　　　　　"jquery": "lib/jquery.min",
　　　　　　"underscore": "lib/underscore.min",
　　　　　　"backbone": "lib/backbone.min"

　　　　}

　　});
```
或者
```
　require.config({

　　　　baseUrl: "js/lib",

　　　　paths: {

　　　　　　"jquery": "jquery.min",
　　　　　　"underscore": "underscore.min",
　　　　　　"backbone": "backbone.min"

　　　　}

　　});
```

或者
```javascript
require.config({

　　　　paths: {

　　　　　　"jquery": "https://ajax.googleapis.com/ajax/libs/jquery/1.7.2/jquery.min"

　　　　}

　　});
```

require.js要求，每个模块是一个单独的js文件。这样的话，如果加载多个模块，就会发出多次HTTP请求，会影响网页的加载速度。因此，require.js提供了一个优化工具，当模块部署完毕以后，可以用这个工具将多个模块合并在一个文件中，减少HTTP请求数。


模块必须按照AMD的规定来写。
具体来说，就是模块必须采用特定的define()函数来定义。如果一个模块不依赖其他模块，那么可以直接定义在define()函数之中。

```javascript
// math.js

　　define(function (){

　　　　var add = function (x,y){

　　　　　　return x+y;

　　　　};

　　　　return {

　　　　　　add: add
　　　　};

　　});
```
加载方法如下：

```javascript
// main.js

　　require(['math'], function (math){

　　　　alert(math.add(1,1));

　　});
```
　
如果这个模块还依赖其他模块，那么define()函数的第一个参数，必须是一个数组，指明该模块的依赖性。

```javascript
define(['myLib'], function(myLib){

　　　　function foo(){

　　　　　　myLib.doSomething();

　　　　}

　　　　return {

　　　　　　foo : foo

　　　　};

　　});
```
六、加载非规范的模块
举例来说，underscore和backbone这两个库，都没有采用AMD规范编写。如果要加载它们的话，必须先定义它们的特征。

```javascript
require.config({

　　　　shim: {

　　　　　　'underscore':{
　　　　　　　　exports: '_'
　　　　　　},

　　　　　　'backbone': {
　　　　　　　　deps: ['underscore', 'jquery'],
　　　　　　　　exports: 'Backbone'
　　　　　　}

　　　　}

　　});
```
require.config()接受一个配置对象，这个对象除了有前面说过的paths属性之外，还有一个shim属性，专门用来配置不兼容的模块。具体来说，每个模块要定义（1）exports值（输出的变量名），表明这个模块外部调用时的名称；（2）deps数组，表明该模块的依赖性。

比如，jQuery的插件可以这样定义：

```javascript
shim: {

　　　　'jquery.scroll': {

　　　　　　deps: ['jquery'],

　　　　　　exports: 'jQuery.fn.scroll'

　　　　}

　　}
```

七、require.js插件

require.js还提供一系列插件，实现一些特定的功能。

















