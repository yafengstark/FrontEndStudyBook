




利用原生JSON对象，将对象转为字符串
```javascript
var jsObj = {};
jsObj.testArray = [1,2,3,4,5];
jsObj.name = 'CSS3';
jsObj.date = '8 May, 2011';
var str = JSON.stringify(jsObj);
alert(str);

```



从JSON字符串转为对象
```javascript
var jsObj = {};
jsObj.testArray = [1,2,3,4,5];
jsObj.name = 'CSS3';
jsObj.date = '8 May, 2011';
var str = JSON.stringify(jsObj);
var str1 = JSON.parse(str);
alert(str1);
```

————————————————
版权声明：本文为CSDN博主「Rex_In」的原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/StarRexStar/article/details/8083259

