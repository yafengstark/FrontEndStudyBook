
//2000毫秒后执行test()函数，只执行一次
```javascript
setTimeout("test()","2000");
```

```javascript
setInterval("test()","2000"); 
//每隔2000毫秒执行一次test()函数，执行无数次。
```


```javascript
created() {

            this.circleRun();
        },
        methods: {
            async getlunbotu() {

            },
            updateClock(){
                this.timestamp = new Date().getTime();
                console.log(this.timestamp)
            },
            circleRun() {
//                毫秒
                window.setInterval(this.updateClock,1000);
            }
        },
```

