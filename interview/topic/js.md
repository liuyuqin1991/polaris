# 散装JS

## 实用移动端API

* **监听屏幕旋转变化接口: orientationchange**

定义：这个 API 可以将你手机是否横屏的情况暴露给需要知道的人知道，使用：

```
screenOrientation: function(){
    let self = this;
    let orientation = screen.orientation || screen.mozOrientation || screen.msOrientation;
    window.addEventListener("onorientationchange" in window ? "orientationchange" : "resize", function() {
        self.angle = orientation.angle;
    });
}
```

* **电池状态：navigator.getBattery()**

定义：这个 API 可以将你手机电池状态的情况暴露给需要知道的人知道。

> 这个 api 返回的是一个 promise 对象，会给出一个 BatteryManager 对象，对象中包含了以下信息：

|key|描述|备注|
|:-:|:-|:-|
|charging|是否在充电|可读属性|
|chargingTime|若在充电，还需充电时间|可读属性|
|dischargingTime|剩余电量|可读属性|
|level|剩余电量百分数|可读属性|
|onchargingchange|监听充电状态的改变|可监听事件|
|onchargingtimechange|监听充电时间的改变|可监听事件|
|ondischargingtimechange|监听电池可用时间的改变	|可监听事件|
|onlevelchange|监听剩余电量百分数的改变	|可监听事件|

使用：

```
getBatteryInfo: function(){
    let self = this;
    if(navigator.getBattery){
        navigator.getBattery().then(function(battery) {
            // 判断是否在充电
            self.batteryInfo = battery.charging ? `在充电 : 剩余 ${battery.level * 100}%` : `没充电 : 剩余 ${battery.level * 100}%`;
            // 电池充电状态改变事件
            battery.addEventListener('chargingchange', function(){
                self.batteryInfo = battery.charging ? `在充电 : 剩余 ${battery.level * 100}%` : `没充电 : 剩余 ${battery.level * 100}%`;
            });
        });
    }else{
        self.batteryInfo = '不支持电池状态接口';
    }
}
```

* **让你的手机震动: window.navigator.vibrate(200)**

定义：这个 API 可以让你的手机按你的想法震动。

使用：震动效果会在很多游戏使用。比如欢乐斗地主中，地主打完王炸后手机都会有震动的效果，以此来表达地主嘚瑟的心情也很是合理。

```
vibrateFun: function(){
    let self = this;
    if( navigator.vibrate ){
        navigator.vibrate([500, 500, 500, 500, 500, 500, 500, 500, 500, 500]);
    }else{
        self.vibrateInfo = "您的设备不支持震动";
    }
    <!--
    // 清除震动 
    navigator.vibrate(0);
    // 持续震动
    setInterval(function() {
        navigator.vibrate(200);
    }, 500);
    -->
}
```