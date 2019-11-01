一定要创建一个timer，然后调用延时之前先清除timer的延时

clearTimeout(this.timer);  //清除延迟执行 
 
this.timer = setTimeout(()=>{   //设置延迟执行
    console.log('ok');
},1000);

