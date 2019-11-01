

forEach 的return不会终止

注意，forEach（）无法在所有元素都传递给调用的函数之前终止遍历。也就是说，没有像for循环中使用的相应的break语句。如果要提前终止，必须把forEach（）方法放在一个try块中，并能抛出一个异常。如果forEach（）调用的函数抛出foreach.break异常，循环会提前终止：


https://www.cnblogs.com/PheonixHkbxoic/p/5708749.html

